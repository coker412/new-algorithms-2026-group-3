# 第三组统一报告模板

排版要求以 [合作规范](../../CONTRIBUTING.md#报告统一方式) 为准，`main.tex` 实现对应设置。中文正文使用 Fandol 宋体，标题使用 Fandol 黑体，英文使用 Latin Modern，数学沿用 LaTeX 默认的 Computer Modern 与 AMS 数学字体；所有字体均来自 TeX Live，不依赖个人电脑上的宋体或 Times New Roman。

直接查看 [模板 PDF 预览](_build/main.pdf)。

## 使用

1. 将本目录的 `main.tex`、`references.bib` 和 `.latexmkrc` 复制到合作规范指定的报告目录，不复制 `_build/`。
2. 填写标题和实际作者，保留第三组署名与空日期。五项章节用于组内候选题讨论；其他材料按合作规范中的章节表调整。
3. 修改正文，不单独更换导言区的字体、间距或编号规则。共同设置需要调整时，修改本模板并同步在用报告。
4. 有引用时将真实条目填入 `references.bib`，在正文使用 `\cite{键}`，取消文末两行书目命令的注释。没有引用时保持两行注释，不生成空参考文献表。

公开出题说明与课程审核补充说明分别编译，AI 试解和参考解答放在审核补充说明中。

## 编译

需要安装带有中文支持的 TeX Live、XeLaTeX 和 latexmk。也可在 Overleaf 上传这三个文件并选择 XeLaTeX 编译。

在报告目录运行：

```bash
latexmk -g -xelatex -outdir=_build main.tex
```

输出为 `_build/main.pdf`。`.latexmkrc` 使省略输出参数时仍写入 `_build/`；构建输出默认不进入 Git，仅本模板的预览 PDF 随仓库提供。发送课程材料时按合作规范重命名 PDF，并附在固定版本提交中。

## 常用写法

公式使用 `equation`、`align`，不编号时使用带星号的对应环境；交叉引用用 `\eqref{eq:名称}`。命题等使用 `theorem`、`lemma`、`proposition`、`definition`，证明使用 `proof`；引用用 `\ref{thm:名称}`。

图表使用 `figure` 或 `table`，加 `\centering`。图片用 `\includegraphics[width=0.8\linewidth]{figures/文件名.pdf}`。图的 `\caption` 写在图片下方，表的 `\caption` 写在表格上方，`\label` 紧接对应的 `\caption`。三线表用 `\toprule`、`\midrule`、`\bottomrule`。

提交前检查编译日志中的错误、缺失引用、重复标签、字体警告和越界，再检查 PDF 的分页、图表及公式。模板中的填写提示须替换为实际内容。
