# 西南科技大学学位论文 LaTeX 模板

依据学校 2024 年版撰写规范及配套参考样式整理，支持专业硕士、学术硕士和学术博士。非官方模板。

## 使用

1. 在 `main.tex` 中选择模板，默认 `professional-master`（专业硕士）；另外两个值为 `academic-master`（学术硕士）、`academic-doctor`（学术博士）。
2. 在 `main.tex` 中填写题目、作者、导师、学位、专业及关键词等信息。
3. 在 `content/` 中撰写正文，在 `main.tex` 中增删章节。
4. 使用 TeX Live 或 MiKTeX，从项目根目录按 **XeLaTeX → BibTeX → XeLaTeX → XeLaTeX** 编译：

```sh
xelatex main.tex
bibtex main
xelatex main.tex
xelatex main.tex
```

版式和字体设置统一放在 `swust-thesis.sty`；`fonts/` 仅存放封面替代字体及其许可证。TeX 环境需包含 ctex、natbib、gbt7714、Fandol、TeX Gyre 等常用宏包和字体。

修改 `.bib` 后重新执行完整编译流程；也可使用 `latexmk -xelatex main.tex` 自动处理。

## 字体

正文优先使用本机宋体、黑体、楷体、Times New Roman 和 Arial；缺失时使用 TeX 发行版提供的 Fandol 和 TeX Gyre。

学校封面示例使用**方正粗宋简体**，本模板默认使用附带的**思源宋体 Heavy** 替代，两者字形不完全相同。如果本机已安装方正粗宋，在 `swust-thesis.sty` 中将：

```tex
\newCJKfontfamily\SWUSTCoverFont[Path=fonts/]{SourceHanSerifCN-Heavy.otf}
```

改为以下代码（字体名称以本机实际名称为准）：

```tex
\newCJKfontfamily\SWUSTCoverFont{方正粗宋简体}
```

使用已授权的字体文件时，也可直接指定文件路径。商业字体不随仓库分发。

## 说明

- `figures/swust-logo.png` 为封面使用的学校标识，其他论文图片也可放在 `figures/`。
- 示例包含图、三线表、公式、脚注与顺序编码引用。参考文献放在根目录 `references.bib`，采用 GB/T 7714 顺序编码样式，按首次引用顺序自动编号。正文使用 `\cite{swust2024}` 或 `\upcite{swust2024}` 上标引用，多篇用逗号分隔键名。未引用的条目不输出。
- 示例学位名称和正文均需按实际论文替换；长题目可使用 `main.tex` 中的封面分行设置。
- 替代字体可能改变分页，最终提交请依据学校及学院要求检查。

## 许可与来源

原创模板代码采用 MIT 许可，见 `LICENSE`。声明文字沿用学校提供的学位论文参考样式，其权利归原权利人，不包含在 MIT 授权范围内；学校标识来自所提供的学校模板，相关权利归原权利人，不包含在 MIT 授权范围内；本仓库不附带学校完整规范。

附带字体来自 [Adobe 思源宋体官方仓库](https://github.com/adobe-fonts/source-han-serif)，未修改，Copyright 2017–2022 Adobe，采用 SIL Open Font License 1.1，完整许可见 `fonts/OFL.txt`。方正粗宋可从[方正字库](https://www.foundertype.com/index.php/FontInfo/index/id/125)获取适用授权。
