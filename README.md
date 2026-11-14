# GitHub2 Lego for Typora — v2.0

基于 legoming 的 [GitHub2.css](https://github.com/legoming/macdown_theme_lego/blob/main/GitHub2.css) 转换并优化。两个主题均为独立 CSS，无外部字体或网络依赖。

## 主题选择

| 文件 | 主要特征 | 适合场景 |
| --- | --- | --- |
| `github2-lego-technical.css` | H1 居中、H2~H6 自动编号、960px 版心、技术表格和代码优先 | 技术设计、Android/AAOS 文档、测试/问题分析 |
| `github2-lego-reading.css` | H1 左对齐、不自动编号、880px 版心、宽松段落、温和色彩 | 长文、AI 输出、会议纪要、知识笔记 |

## 安装

1. Typora → Preferences/偏好设置 → Appearance/外观 → Open Theme Folder/打开主题文件夹。
2. 将两个 `.css` 文件复制到主题文件夹根目录（不要放到子文件夹）。
3. 完全退出并重新启动 Typora。
4. Themes/主题 菜单中选择 `Github2 Lego Technical` 或 `Github2 Lego Reading`。
5. 打开 `github2-lego-test.md` 测试长代码块、表格、Mermaid、公式以及提示框。

两个主题可同时安装、自由切换，原有的 `github2-lego.css` 不会被覆盖。

## 兼容性与改进

- **代码块一体化**：使用 `pre.md-fences` 作为外框，内部 CodeMirror 每一行不带单独边框、阴影、内边距。
- **减少滚动时视觉闪烁**：代码块在 `mock-cm` 初始化前后保持相同背景和默认字体、文字颜色，取消代码块内部过渡/动画。**Typora 内部延迟语法解析仍可能发生，CSS 无法彻底消除**。
- **语法高亮**：为 CodeMirror 的 `.cm-s-inner` 自定义关键词、字符串、注释等可读颜色。源码模式不受影响。
- **标准 Markdown 组件**：链接、任务列表、图片、引用、表格、目录、脚注、YAML front matter、公式与 Mermaid 容器均有基础适配。
- **GitHub Alerts**：`> [!NOTE]` / TIP / IMPORTANT / WARNING / CAUTION。请在 Typora Markdown 偏好设置中启用 `GitHub Style Alert`（Typora 1.8+）。
- **保留原有扩展**：`<note>`、`<warning>`、`<success>`、`<point>`、`<hlred>` 等自定义 HTML 样式及 `details` 折叠块。
- **打印**：保留彩色提示框和代码块背景；标题避免孤立；长表格按行尽量跨页显示。
- **无外部依赖**：字体采用操作系统回退，不引用原 CSS 作者电脑的本地 Font Awesome 路径。

## 已知限制

1. H2~H6 自动编号只在 Technical 主题中显示，由 CSS 计算，不会写回 Markdown 文件。TOC 内容或导出方式不同，目录中可能不包含自动编号。
2. 自定义 HTML 标签在 Typora 编辑模式、导出 HTML/PDF 以及其他 Markdown 阅读器中的兼容性可能不同。
3. 代码块滚动出现后再着色可能是 Typora/CodeMirror 的延迟初始化；主题已减少背景闪烁，无法通过 CSS 强制提前解析。
4. CSS 外观已用 Chromium 模拟 Typora DOM 检查，但没有在真实 Typora 应用中进行人工验收。

## 文件与维护

- `github2-lego-technical.css`, `github2-lego-reading.css`: 直接使用的主题。
- `github2-lego-test.md`: 样式和渲染验收文档。
- `technical-preview.png`, `reading-preview.png`: 基于模拟 Typora DOM 的预览。

如需针对其中一个主题进一步微调，可新建同名覆盖文件：例如 `github2-lego-technical.user.css`，Typora 会在主题 CSS 之后加载它。

官方资料：
- https://support.typora.io/About-Themes/
- https://support.typora.io/Add-Custom-CSS/
- https://support.typora.io/Code-Block-Styles/
- https://support.typora.io/What%27s-New-1.8/