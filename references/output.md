# 八字命理 · HTML 命书输出规范

> **读取时机**：需要生成 HTML 命书时读取。包含完整的 CSS 变量系统、页面基础结构和命盘模板。

---

## 一、页面基础结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <title>命书 · [命主代号]</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@400;700&family=Noto+Sans+SC:wght@300;400;700&display=swap');

    :root {
      --bg-dark:    #0d0d0d;
      --bg-card:    #1a1a1a;
      --gold:       #c9a962;
      --gold-dim:   #8b7355;
      --vermilion:  #8b3a3a;
      --text:       #e8e4d9;
      --text-dim:   #9a9590;
      --wood:       #4a7c59;
      --fire:       #c94040;
      --earth:      #b8860b;
      --metal:      #a8a8a8;
      --water:      #3a6ea8;
    }

    body {
      font-family: 'Noto Sans SC', sans-serif;
      background: var(--bg-dark);
      color: var(--text);
      line-height: 1.8;
    }
    h1, h2, h3 { font-family: 'Noto Serif SC', serif; }
    .container  { max-width: 900px; margin: 0 auto; padding: 40px 20px; }
    .card       { background: var(--bg-card); border: 1px solid var(--gold-dim); border-radius: 8px; padding: 30px; margin-bottom: 30px; }
    .card-title { color: var(--gold); font-size: 1.4em; border-bottom: 1px solid var(--gold-dim); padding-bottom: 10px; margin-bottom: 20px; }

    table   { width: 100%; border-collapse: collapse; margin: 15px 0; }
    th, td  { padding: 10px 15px; border: 1px solid var(--gold-dim); text-align: center; }
    th      { background: rgba(201,169,98,0.1); color: var(--gold); }

    /* 五行徽章 */
    .badge        { display: inline-block; padding: 2px 8px; border-radius: 4px; font-size: 0.85em; font-weight: 700; }
    .badge-wood   { background: var(--wood);   color: #fff; }
    .badge-fire   { background: var(--fire);   color: #fff; }
    .badge-earth  { background: var(--earth);  color: #fff; }
    .badge-metal  { background: var(--metal);  color: #000; }
    .badge-water  { background: var(--water);  color: #fff; }

    /* 大运时间轴 */
    .dayun-track  { display: flex; gap: 8px; flex-wrap: wrap; margin: 16px 0; }
    .dayun-item   { border: 1px solid var(--gold-dim); border-radius: 6px; padding: 10px 14px; min-width: 70px; text-align: center; background: rgba(255,255,255,0.03); }
    .dayun-active { border-color: var(--gold); background: rgba(201,169,98,0.08); }
  </style>
</head>
<body>
  <div class="container">
    <!-- MODULE 0~6 内容 -->
  </div>
</body>
</html>
```

---

## 二、命盘表格模板（MODULE 0）

```html
<div class="card">
  <div class="card-title">四柱命盘</div>
  <table id="bazi-plate">
    <thead>
      <tr><th></th><th>年柱</th><th>月柱</th><th>日柱</th><th>时柱</th></tr>
    </thead>
    <tbody>
      <tr><td>天干</td><td>甲</td><td>丙</td><td>戊</td><td>壬</td></tr>
      <tr><td>地支</td><td>子</td><td>寅</td><td>辰</td><td>午</td></tr>
      <tr><td>藏干</td><td>癸</td><td>甲丙戊</td><td>乙戊癸</td><td>丁己</td></tr>
      <tr><td>十神</td><td>正印</td><td>比肩食神</td><td>日主偏财正印</td><td>伤官正印</td></tr>
    </tbody>
  </table>
</div>
```

---

## 三、五神标注模板（MODULE 2）

```html
<div class="card">
  <div class="card-title">日主能量 · 喜用神</div>
  <p>日主：<strong>戊土</strong>，能量等级：<strong>身强</strong></p>
  <table>
    <tr><th>五神</th><th>五行</th><th>原则</th></tr>
    <tr><td>用神</td><td><span class="badge badge-wood">木</span></td><td>克泄耗，疏土为用</td></tr>
    <tr><td>喜神</td><td><span class="badge badge-water">水</span></td><td>生木，间接助用</td></tr>
    <tr><td>忌神</td><td><span class="badge badge-earth">土</span> <span class="badge badge-fire">火</span></td><td>同类助旺，壅塞</td></tr>
    <tr><td>仇神</td><td><span class="badge badge-metal">金</span></td><td>泄木（用神），间接助忌</td></tr>
    <tr><td>闲神</td><td>—</td><td>无显著影响</td></tr>
  </table>
</div>
```

---

## 四、大运时间轴模板（MODULE 5）

```html
<div class="card">
  <div class="card-title">大运流年</div>
  <p>起运岁数：<strong>X岁</strong>（顺/逆行）</p>
  <div class="dayun-track">
    <div class="dayun-item">
      <div style="color:var(--gold)">甲子</div>
      <div style="font-size:0.8em;color:var(--text-dim)">X~X岁</div>
    </div>
    <div class="dayun-item dayun-active">
      <div style="color:var(--gold)">乙丑</div>
      <div style="font-size:0.8em;color:var(--text-dim)">X~X岁 ◀ 当前</div>
    </div>
    <!-- 其余大运 -->
  </div>
  <!-- 当前大运流年分析 -->
</div>
```

---

## 五、色彩系统参考

| 元素 | 色值 | 用途 |
|---|---|---|
| 背景 | `#0d0d0d` | page background |
| 卡片背景 | `#1a1a1a` | .card |
| 主色（金） | `#c9a962` | 标题、强调、边框 |
| 暗金 | `#8b7355` | 次级边框、dim 元素 |
| 强调（朱） | `#8b3a3a` | 警示、凶神标注 |
| 正文 | `#e8e4d9` | body text |
| 辅助文字 | `#9a9590` | 注释、dim |
| 木绿 | `#4a7c59` | 木五行徽章 |
| 火赤 | `#c94040` | 火五行徽章 |
| 土黄 | `#b8860b` | 土五行徽章 |
| 金银 | `#a8a8a8` | 金五行徽章 |
| 水蓝 | `#3a6ea8` | 水五行徽章 |

---

## 六、输出检查

- [ ] HTML 文件无外部 CSS/JS 依赖（Google Fonts 除外）
- [ ] 五行徽章色彩使用 CSS 变量系统，不硬编码色值
- [ ] 大运时间轴标注当前大运
- [ ] 命盘表格天干地支对应正确
- [ ] 所有模块 MODULE 0~6 均已输出
