---
name: xtx-coding-conventions
description: Project coding conventions for this repo. Use when writing or editing HTML CSS or JS files. All identifiers must start with xtx_, HTML needs header comment, use vanilla tech stack with iconfont icons and fetch API, no third-party libs or CDN.
---

# 项目编码规范（许桐欣）

本项目所有代码必须遵循以下硬规则，无论新建文件还是修改已有文件。

## 规则一：命名前缀 `xtx_`

以下标识符必须以 `xtx_` 开头（小写，下划线后接语义名）：

- **CSS 类名**（class）：`xtx_container`、`xtx_slide`、`xtx_btn-primary`
- **CSS ID**：`xtx_header`、`xtx_main-box`
- **JS 变量 / 函数 / 常量**：`xtx_userName`、`xtx_initSlider()`、`XTX_CONFIG`

禁止使用无前缀通用名（如 `.box`、`.grid`、`myVar`、`header`），避免与第三方库或后续扩展冲突。

## 规则二：HTML 页面头部注释

每个 HTML 文件 `<body>` 标签之后的第一行必须包含以下格式的注释：

```html
<!-- 姓名：许桐欣 建立时间：YYYY-MM-DD 使用大模型：<模型名> 功能名称：<简短描述> -->
```

四个字段缺一不可：

- **姓名**：固定为 许桐欣
- **建立时间**：文件创建日期（YYYY-MM-DD）
- **使用大模型**：实际生成该文件所用的 AI 模型名称（如 GLM-5.3-Flash）
- **功能名称**：用 4-12 个汉字概括页面用途

示例：
```html
<!-- 姓名：许桐欣 建立时间：2026-10-26 使用大模型：GLM-5.3-Flash 功能名称：逢7过游戏 -->
```

## 规则三：技术栈原生化

前端实现严格使用原生 **HTML + CSS + JavaScript**，禁止引入任何第三方库或 CDN 资源：

- ❌ 禁止：jQuery、Bootstrap、Vue、React、Tailwind、Lodash、Font Awesome（CDN 版）等
- ❌ 禁止：从 `<link>` 或 `<script src="https://...">` 加载任何外部 CDN
- ✅ 允许：仅使用浏览器原生 API（DOM、Fetch、Canvas、Web Storage 等）

## 规则四：图标统一用项目内 iconfont

图标必须使用项目自带的 iconfont 字体文件，目录为 `font_5244722_v0q45bpmzfi/`：

```html
<!-- 在 <head> 中引入 iconfont 样式 -->
<link rel="stylesheet" href="font_5244722_v0q45bpmzfi/iconfont.css">
```

页面中使用：
```html
<i class="iconfont icon-xxx"></i>
```

禁止使用 Font Awesome、Lucide、Material Icons 等任何其他图标方案。

## 规则五：数据获取统一用 Fetch API

与服务器端数据交互时，必须使用浏览器原生 **`fetch`** API，禁止使用 jQuery `$.ajax`、Axios 等第三方请求库：

```javascript
fetch("/api/data")
    .then(function(res) { return res.json(); })
    .then(function(data) { /* 处理数据 */ })
    .catch(function(err) { /* 错误处理 */ });
```

## 检查清单

每次生成或修改代码前，自问：

- [ ] 所有 class / id 是否都以 `xtx_` 开头？
- [ ] 所有 JS 变量和函数是否都以 `xtx_` 开头？
- [ ] HTML 头部注释是否齐全（姓名 / 建立时间 / 使用大模型 / 功能名称）？
- [ ] 是否未引入任何第三方库或 CDN？
- [ ] 图标是否用的是项目内 `font_5244722_v0q45bpmzfi/iconfont.css`？
- [ ] 数据请求是否使用原生 `fetch` 而非 Axios / jQuery 等？
