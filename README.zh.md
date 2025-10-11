````markdown
# AssetHub — 静态资源仓库

此仓库用于集中存放项目使用的静态资源，便于在不同项目/页面中复用和管理。资源类型包括：SVG、图片（jpg、png、avif 等）、字体（woff/woff2/ttf）以及 CodePen 示例资源。

## 目的

- 提供一个结构化的位置来保存可复用的视觉资源。
- 保持命名规范与使用示例，方便快速引用与集成。
- 提供简单的贡献与提交规范（采用 Conventional Commits）。

## 顶级目录说明

项目中存在的主要目录（示例）：

- `cats/` — 单独主题或示例文件夹（可按主题组织图片）
- `fonts/` — 字体文件和对应的 CSS/说明
- `portfolio/` — 作品或示例图片
- `svg/` — 所有 SVG 资源，按子项目或主题分类。例如：`svg/codepen_demo/spooky-clock/`

> 注：以上目录为仓库中已存在的示例结构。可以按需新增子目录来存放新的主题或组件资源。

## 使用示例

在 HTML 中直接引用图片：

```powershell
<!-- 相对路径示例（视引用文件的位置而定） -->
<img src="./svg/codepen_demo/spooky-clock/jack-o'-lantern.svg" alt="jack o'lantern"> 
```

将 SVG 作为背景图或 CSS 引用：

```css
.header-logo {
  background-image: url("../svg/codepen_demo/spooky-clock/midnight.svg");
  background-size: contain;
  background-repeat: no-repeat;
}
```

内联 SVG（可更灵活地控制样式与动画）：

```html
<!-- 复制 svg 文件的 <svg> 内容并粘贴到 HTML 中 -->
<div class="icon">
  <!-- <svg ...> ... </svg> -->
</div>
```

使用自托管字体（示例放在 `fonts/` 下）：

```css
@font-face {
  font-family: 'MyAssetFont';
  src: url('./fonts/MyAssetFont.woff2') format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

## 线上引用（GitHub Raw / CDN）

如果你在其他项目中直接通过线上地址引用这些资源（例如使用 GitHub 的 raw 链接或 CDN），可以按下面方式使用：

- 直接使用 raw.githubusercontent.com 地址（示例）：

```html
<!-- 注意：文件名中包含特殊字符（如单引号）时，URL 会被编码 -->
<img src="https://raw.githubusercontent.com/ooBean/AssetHub/main/svg/codepen_demo/spooky-clock/jack-o%27-lantern.svg" alt="jack o'lantern">
```

- 使用 jsDelivr 作为 CDN（更稳定的缓存与速度）：

```html
<img src="https://cdn.jsdelivr.net/gh/ooBean/AssetHub@main/svg/codepen_demo/spooky-clock/jack-o%27-lantern.svg" alt="jack o'lantern">
```

注意事项：
- 为了避免线上资源被后续改动破坏，推荐使用 tag 或 commit hash 固定版本（例如 `@v1.0.0` 或 `@<commit-hash>`）而不是 `@main`。
- URL 中的特殊字符必须正确 URL 编码（例如 `'` → `%27`，空格 → `%20`）。
- GitHub raw 链接通常不会设置跨域 CORS 头（视具体用途可能导致字体或跨域请求问题），如果遇到 CORS 限制可以考虑使用 jsDelivr 等 CDN 作为替代。
- 注意缓存与缓存失效：使用 CDN + 指定版本号可以避免缓存中出现不同版本的资源。
- 检查资源许可（License）和隐私/合规要求，确保允许线上直接引用。
````
