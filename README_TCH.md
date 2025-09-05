[English](README.md) | 繁體中文

# 網頁流體重力模擬

## 線上預覽

* [fluid Simulator | JingShing blog](https://jingshing.com/fluidsim/)
* [Github page](https://jingshing.github.io/Fluid-Simulator-Online/)

## 如何使用

- `web-fluidsim.html` 下載後直接開啟

## 操控

**PC**

- 滑鼠拖曳 → 指向的方向變「重力方向」
- 方向鍵 `↑ ↓ ← →` → 調整重力
- 「重置粒子」/「暫停重力」按鈕 → 快速場景控制

**手機**

- 點「啟用手機感測器」取得權限(視情況不用)
- 可「重設基準」校正現在的裝置姿態為 0
- 可在設定中 **反轉 X/Y** 軸控制方向

##  設定

- **粒子數 / 半徑**：控制數量與大小
- **碰撞迭代 / 反彈係數**：迭代越多、越紮實；反彈越高、越有彈性
- **格子尺寸**：格子渲染密度（同時影響流體塊感）
- **重力倍率 / 阻尼**：場景重力強度、速度衰減
- **每格最多一顆（實驗）**：避免多粒子擠在同格（更硬派，較耗）
- **粒子顏色**：用色票選，系統自動推導泡沫/邊緣色
- **渲染模式**：格子 / 小球 切換
- **語言**：繁中 / English
- **側邊欄**：可收起；左上角按鈕可再打開

## 自訂預設值

**1) 改 HTML input 預設：**

```html
<input id="nRange"    value="700" />
<input id="rRange"    value="4"   />
<input id="iterRange" value="3"   />
<input id="restRange" value="0.50"/>
<input id="gridRange" value="56"  />
<input id="gRange"    value="1.0" />
<input id="dRange"    value="0.995"/>
<input id="colorPicker" type="color" value="#0078ff"/>
<select id="langSel">…</select>
```

**2) 改 JS fallback（無 localStorage 時的起始值）：**

```js
let lang = localStorage.getItem('lang') || 'zh';
let baseColor = localStorage.getItem('baseColor') || '#0078ff';
// 側邊欄是否預設收起
const collapsedSaved = (localStorage.getItem('sidebarCollapsed') ?? '0') === '1';
// 預設渲染模式
let renderMode = 'grid'; // 或 'balls'
```

> 注意：若曾經操作過 UI，瀏覽器會把你的設定存進 `localStorage`。要讓「新預設」生效，請清掉：

```js
['lang','baseColor','sidebarCollapsed','invX','invY'].forEach(k=>localStorage.removeItem(k));
```


## Roadmap

-  粒子半徑/顏色的雜訊分佈
-  WebGL 加速
-  匯出/載入設定 preset
- 自動偵測手機