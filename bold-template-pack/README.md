# Algorithm-Driven Culture Presentation

本仓库用于存放英语课展示 slides：

**Algorithm-Driven Culture: How TikTok and RED Reshape Global Social Media**

本项目使用 `frontend-slides` 制作。它不是传统的 `.pptx` 文件，而是一个基于 HTML/CSS 的网页幻灯片项目。
可编辑源文件是 HTML，最终提交版本可以导出为 PDF。

---

## 文件说明

### `algorithm-driven-culture.pdf`

这是目前导出的最终 PDF 版本。

可用于：

* 直接预览最终效果
* 提交作业
* 上台展示

---

### `algorithm-driven-culture.html`

这是 slides 的主要源文件。

如果需要修改 slides，主要编辑这个文件，例如：

* 修改文字
* 调整排版
* 更换图片
* 修改视觉元素
* 重新导出 PDF

建议使用 VS Code 打开并编辑。

---

### `assets/slide06/`

这个文件夹存放第 6 页使用的图片素材。

请不要随意删除或重命名里面的图片。
如果修改了图片文件名，也需要同步修改 `algorithm-driven-culture.html` 中对应的图片路径，否则图片可能无法正常显示。

---

### `my-presentation-brief.md`

这是最初制作 slides 时的需求文档。

里面包含：

* 展示主题
* 核心观点
* 页面结构
* 风格要求
* 整体设计思路

如果后续需要理解这份 slides 的逻辑，可以先看这个文件。

---

## 如何查看 slides

如果只是查看最终版本，直接打开：

```text
algorithm-driven-culture.pdf
```

如果要查看或编辑源文件，打开：

```text
algorithm-driven-culture.html
```

HTML 文件可以直接用浏览器打开预览。

---

## 如何修改 slides

推荐流程：

1. Clone 本仓库到本地。
2. 用 VS Code 打开项目文件夹。
3. 修改 `algorithm-driven-culture.html`。
4. 用浏览器打开 HTML 文件，检查页面效果。
5. 确认文字、图片和排版没有问题。
6. 重新导出 PDF。

---

## 如何导出 PDF

不要直接使用浏览器的 `Ctrl + P` 打印功能，因为这样可能导致页面比例不正确。

请使用 `frontend-slides` 提供的导出脚本。

首先确保电脑已经安装 Node.js。

在项目根目录下运行：

```bash
bash scripts/export-pdf.sh ./algorithm-driven-culture.html ./algorithm-driven-culture.pdf
```

如果第一次导出时提示缺少 Playwright / Chromium，可以先运行：

```bash
npx playwright install chromium
```

然后再次运行导出命令：

```bash
bash scripts/export-pdf.sh ./algorithm-driven-culture.html ./algorithm-driven-culture.pdf
```

导出的 PDF 会保持正确的 16:9 页面比例。

---

## 注意事项

* 不要把这个项目当作普通 PPTX 文件处理。
* 可编辑源文件是 `algorithm-driven-culture.html`。
* 最终提交文件是 `algorithm-driven-culture.pdf`。
* 图片素材应放在 `assets/` 文件夹下。
* 修改后一定要重新导出 PDF，并手动检查效果。
* 检查是否存在文字溢出、图片丢失、比例错误等问题。
* `.frontend-slides/` 等临时文件夹一般不需要修改或提交。

---

## 推荐工作流

```text
修改 HTML → 浏览器预览 → 导出 PDF → 检查 PDF → 提交
```

---

## 后续修改建议

修改时尽量保持当前整体风格一致：

* 蓝白科技风
* 干净简洁的排版
* 大字号标题
* 低密度页面文字
* 突出 TikTok 与 RED 的对比
* 保持 16:9 页面比例
* 确保适合导出 PDF

不要在单页中加入过多文字。
这份 slides 是为口头展示设计的，页面应该保持视觉化、简洁、有重点。

# Bold Template Pack

This pack brings the `beautiful-html-templates` design systems into the
`frontend-slides` skill without making them the default for every deck.

## What To Read

1. Read `bold-template-pack/selection-index.json` first.
2. Shortlist candidates from metadata only:
   - `mood`
   - `tone`
   - `best_for`
   - `avoid_for`
   - `formality`
   - `density`
   - `scheme`
3. For title-slide previews, read only the relevant candidate `preview.md`
   files.
4. After the user chooses a bold template, read exactly that one template's
   full `design.md`.
5. Do not read every `design.md` in the pack.
6. Do not read or copy `template.html` from the source template library unless a
   selected `design.md` is missing a critical implementation detail.

The full source metadata index is not bundled in the user-facing skill. Normal
generation should use `selection-index.json` only.

## How To Use In Frontend Slides

Preview mix:

- 1 safe option from `STYLE_PRESETS.md`
- at least 1 bold option from this pack
- 1 wildcard option, which may be another bold template from this pack or a
  self-generated custom design

Adjust the tone inside that default mix:

- For board, legal, regulatory, healthcare, investor-update, or highly formal
  internal decks, make the safe option very restrained and choose calmer,
  higher-formality bold templates. The wildcard should feel authoritative and
  specific, not merely decorative.
- For bold, editorial, expressive, experimental, or highly designed decks, keep
  the safe option as a readable fallback, choose one strong bold template, and
  use the wildcard for either a second adventurous template or a custom design
  that better matches the user's occasion and vibe.

If the wildcard is custom, it must follow Frontend Slides' no-slop aesthetics:
distinctive typography, a committed palette, a recognizable layout system, a
context-specific visual idea, fixed 16:9 stage behavior, and no visible process
labels such as "custom", "wildcard", "template", or "preview".

## Implementation Contract

`design.md` is the design-system reference. Treat it as a style recipe, not as
content to copy. `preview.md` is only a lightweight style card for generating
the three title-slide options.

Preview slides must be real title slides for the user's deck. Do not render
template names, option labels, file names, paths, `preview.md`, "generated
from", or user requirement notes on the slide itself.

When generating final slides:

- Keep `frontend-slides` output as one self-contained HTML file.
- Include the full contents of `viewport-base.css`.
- Generate every deck as a fixed 1920×1080 stage scaled uniformly to the
  viewport. This applies even if the source template was originally
  viewport-fluid.
- Treat `vw`, `vh`, and `clamp()` values in a source `design.md` as design
  proportions to translate into fixed 1920×1080 stage coordinates.
- Preserve the selected template's fonts, palette, decorative vocabulary,
  spacing rhythm, and component grammar.
- Keep the user's actual slide content primary. The template style should shape
  presentation, not override message or structure.
- Verify rendered output for both text overflow and panel overlap. A card can
  pass `scrollHeight` checks while still being covered by another grid panel.
