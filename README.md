# 山东大学实验报告 XeLaTeX 模板

从用户提供的实验报告提炼版式，保留校徽封面、中文正文、摘要、目录、分级标题、三线表、代码块、流程图、参考文献及页码规则。适用于不同课程的个人或小组实验报告。

## 快速使用

1. 下载或克隆整个仓库，保留目录结构。
2. 修改 `report-info.tex`：课程、题目、副标题、班级、成员、实验日期和 PDF 作者信息。
3. 修改 `main.tex` 中的摘要、关键词、AI 使用情况声明和参考文献。
4. 将实验正文写入 `sections/body.tex`，截图放入 `figures/`。
5. 使用 **XeLaTeX** 编译。Overleaf 可上传整个仓库 ZIP，选择 XeLaTeX，并将 `main.tex` 设为主文件。

本地推荐使用 TeX Live（包含中文支持、Fandol 字体、TikZ、listings、latexmk 等常用组件），从仓库根目录运行：

```sh
latexmk -xelatex -interaction=nonstopmode -halt-on-error -outdir=build main.tex
```

输出位于 `build/main.pdf`。若没有 latexmk，运行以下命令两次，使目录和交叉引用生效：

```sh
xelatex -interaction=nonstopmode -halt-on-error main.tex
xelatex -interaction=nonstopmode -halt-on-error main.tex
```

## 文件结构

| 文件 | 用途 |
| --- | --- |
| `main.tex` | 报告入口、摘要、关键词、声明、参考文献 |
| `report-info.tex` | 每次报告需要填写的封面信息 |
| `sdu-lab-report.sty` | 集中管理版式，通常无需改动 |
| `sections/body.tex` | 通用章节、表格、公式、代码、流程图和截图示例 |
| `assets/sdu-logo.png` | 用户提供的原始校徽图片，未经改动 |
| `figures/` | 每次实验的真实截图 |
| `preview/` | 模板 PDF 与封面、正文预览 |

## 与原报告的版式关系

- 文档：`ctexart`、A4、12pt；页边距上/下 2.45 cm，左/右 2.55 cm。
- 正文：首行缩进 2 字符，行距因子 1.35；保留 ctex 默认章节层级。
- 封面：校徽宽度为正文宽度的 82%；课程标题黑体二号，实验题目黑体一号，副标题四号；信息表行高因子 1.7。
- 前置部分使用大写罗马页码，正文从阿拉伯数字 1 开始。
- 图表标题使用小号字，图表编号与题注间以空格分隔；保留原三线表和浅灰带行号代码块样式。
- 封面的固定 7 cm 空白改为弹性间距，以适应不同标题长度和成员数；信息表行高设置限制在封面内部。
- 为便于跨平台复用，默认显式使用 TeX Live 自带的 Fandol 中文字体。若要使用原报告在 Windows 上的自动系统字体选择，删除 `main.tex` 文档类选项中的 `fontset=fandol`。这会改变字体字形和部分换行。

## 常用写法

```tex
\section{一级标题}
\subsection{二级标题}
\subsubsection{三级标题}
\reportfigure{figures/result.png}{实际运行结果}
```

普通文本中的 `_`、`%`、`&`、`#` 应分别写成 `\_`、`\%`、`\&`、`\#`。代码放入 `lstlisting` 环境；建议中文解释写在代码块外。

个人报告可在 `report-info.tex` 中将成员标签改为“姓名”，并只保留一位成员。没有副标题时将 `\ReportSubtitle` 设为空。封面字段特别长或成员特别多时，应编译检查封面是否仍为一页。

## 给 AI 生成报告时使用的提示

> 请使用本仓库的 XeLaTeX 模板生成实验报告。保持 `sdu-lab-report.sty` 的版式；填写 `report-info.tex`，将正文写入 `sections/body.tex`，并更新 `main.tex` 的摘要、关键词、声明和参考文献。仅根据我提供的实验要求、实际操作记录、截图及数据描述结果；缺失信息标为待补充，不编造测试通过、性能数据、成员贡献或引用。使用 XeLaTeX 编译并检查封面、目录、图表和代码排版。

## 素材与内容

原报告只作为版式参考，未将原报告正文、姓名、学号、实验数据和截图上传。示例中的说明文字与“待填写”均为模板占位内容。

校徽图片由用户提供，原样收录；山东大学校名及校徽权益归相关权利人所有，本仓库不代表学校官方模板。仓库未附加覆盖校徽或原报告权利的开源许可。
