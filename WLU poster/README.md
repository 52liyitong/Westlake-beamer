# 西湖大学会议海报模板
这是一个为西湖大学（Westlake University）设计的非官方会议海报模板。它基于 `beamerposter` 包构建，提供了现代化的海报设计风格。
## 项目文件结构

```
WLU poster/
├── assets/                    # 资源文件夹
│   ├── background.png        # 背景图片
│   ├── line.png             # 装饰线条
│   ├── wlu-logo-en-alt.png  # 英文版西湖大学logo
│   ├── wlu-logo-faculty.png # 学院logo
│   ├── xi.png               # 小西
│   └── xi2.png              # 小西
├── beamercolorthemewluposter.sty  # 颜色主题文件
├── beamerthemewluposter.sty       # 主主题文件
├── template.tex                    # 模板示例文件
├── template.pdf                    # 生成的PDF示例
├── template.bib                    # 参考文献文件
├── justfile                        # 构建脚本
├── LICENSE                         # 许可证文件
└── README.md                       # 项目说明
```

## 效果预览

[完整PDF](template.pdf)
![template](assets/template.png "template")

## 如何使用

1. 复制以下文件到您的工作目录：
   - `beamerthemewluposter.sty` - 主主题文件
   - `beamercolorthemewluposter.sty` - 颜色主题文件
   - `template.tex` - 模板示例文件
   - `assets/` 文件夹中的相关logo

2. 修改 `template.tex` 文件以适应您的需求

3. 使用 `PDFLaTeX`（或 `XeLaTeX`、`LuaLaTeX`）编译

该海报基于 [beamerposter](https://github.com/deselaers/latex-beamerposter) 和包构建，可以使用标准的 Beamer 宏进行自定义（例如 `\setbeamercolor` 和 `\setbeamertemplate`）。
在https://github.com/alexfikl/uvt-poster的基础上进行了修改

## 主题选项

该包定义了以下选项，可通过 `\usetheme[opts]{wluposter}` 使用：

| 选项 | 描述 |
| :- | :- |
| `language` | `english`  |
| `nomyriadpro` | 不加载 *Myriad Pro* 字体（默认加载，如果可用） |
| `showframe` | 显示页面元素周围的框架（边距等） |
| `layoutgrid` | 添加调试网格以检查对齐 |
| `size=aN` | 设置纸张大小 |
| `orientation=name` | 设置方向为 "landscape" 或 "portrait" |
| 其他 | 其他选项传递给 `beamerposter` |

## 颜色方案

标准品牌颜色如下：

| 颜色 | RGB值 |
| :- | :- |
| `WLULightBlue` | ![#00008B](https://placehold.co/15x15/00008B/00008B.png) `(0, 0, 139)` |
| `WLUDarkBlue` | ![#00008B](https://placehold.co/15x15/00008B/00008B.png) `(0, 0, 139)` |
| `WLUYellow` | ![#FFA500](https://placehold.co/15x15/FFA500/FFA500.png) `(255, 165, 0)` |
| `WLUTextYellow` | ![#CC8400](https://placehold.co/15x15/CC8400/CC8400.png) `(204, 132, 0)` |

`WLUTextYellow` 颜色应该用于文本中，在需要更高对比度的地方使用。

## 辅助宏

以下辅助宏为一些标准功能而定义：

| 宏 | 描述 |
| :- | :- |
| `\footername` | 部门名称、演讲者姓名等（左侧） |
| `\footerlocation` | 海报展示位置（中间） |
| `\footeremail` | 联系邮箱（右侧） |
| `\heading` | 在块内添加小标题的宏 |
| `\separatorcolumn` | 在列之间添加标准化间距 |
| `\headerlogoleft` | 标题中的左侧logo |
| `\headerlogoright` | 标题中的右侧logo |

## Logo处理

标题中的logo已经过修改以获得更好的间距和对比度。您可以使用以下命令获得类似效果（使用 `imagemagick`）：

```bash
magick logo.png -trim +repage logo-trimmed.png
magick logo-trimmed.png -fuzz 10% -channel RGB -fill '#FFFFFF' -opaque '#306BB3' logo.png
```

第一个命令移除任何填充，第二个命令将logo中使用的标准蓝色替换为白色。

## 字体

默认情况下，此模板使用 [Myriad Pro](https://fonts.adobe.com/fonts/myriad) 字体。此字体通常不是免费的，但可以从 Adobe 或[经销商](https://www.fontspring.com/fonts/adobe/myriad-pro)购买。OTF 字体可以直接由 `XeLaTeX` 或 `LuaLaTeX` 引擎加载。

如果您无法获得该字体（或安装因某种原因不起作用），可以使用 `nomyriadpro` 选项禁用它。当找不到字体时，类会回退到使用 `\usepackage{helvet}`，这会加载一个名为 Nimbus Sans L 的 Helvetica 替代品。

如果您使用 `XeLaTeX` 或 `LuaLaTeX`，还有许多其他不错的字体可以考虑，例如：Carlito（Calibri 克隆）、Caladea（Cambria 克隆）、Montserrat（受 Gotham 启发）、Adobe Source Sans 等等。

## 构建工具

项目包含一个 `justfile` 构建脚本，提供以下命令：

- `just build` - 构建模板示例
- `just assets` - 为示例编译资源
- `just clean` - 删除临时编译文件
- `just purge` - 删除所有生成的文件

## 致谢

此主题基于 [Gemini](https://github.com/anishathalye/gemini/) 主题，但主要保留了其中的标题和页脚部分。如果您需要更通用的主题，Gemini 非常棒！
此主题基于 [UVTposter](https://github.com/alexfikl/uvt-poster/）主题，主要修改了配色和配图。

