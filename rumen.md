# 一些入门内容和环境配置
Here are some of my initial LaTeX application files. The source links for LaTeX related configurations in VS Code that I used are as follows:

- [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
- [latex-utilities][https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile](https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile)
- [latex-utilities][https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile#latex-workshoplatexbuildforcerecipeusage](https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile#latex-workshoplatexbuildforcerecipeusage)
- [CSDN][https://blog.csdn.net/qq_44089921/article/details/107719981](https://blog.csdn.net/qq_44089921/article/details/107719981)
- [Overleaf][https://cn.overleaf.com/latex/templates](https://cn.overleaf.com/latex/templates)?

## 上述内容来源于我的GitHub
- https://github.com/CarterYin/tex_allin/blob/main/README.md

# 一些进阶使用内容

- 【使用 Circuitikz 宏包绘制 LaTeX 文档的电路图】https://www.bilibili.com/video/BV1U54y167KB?vd_source=4fd6c4265e65c0785c912874692a3971
- 【LaTeX 直播之六 - TiKZ 绘图基础入门】https://www.bilibili.com/video/BV1UV41127gC?vd_source=4fd6c4265e65c0785c912874692a3971
- 【博士汪倾力整理！全网最强大的LaTeX+Sublime Text写作环境-第一集 功能展示（一定要看完再决定要不要安装！）】https://www.bilibili.com/video/BV1wY4y1W7sj?vd_source=4fd6c4265e65c0785c912874692a3971



# 复制粘贴一些内容
 [Latex 定理和证明类环境的配置（amsthm） - 知乎](https://zhuanlan.zhihu.com/p/133244838)
## 定理类环境

需要宏包：`\usepacakge{[amsthm](https://zhida.zhihu.com/search?content_id=117741425&content_type=Article&match_order=1&q=amsthm&zhida_source=entity)}`

新定义定理环境：`\newtheorem{name}[counter]{text}[section]`

- name：标识这个环境的关键字（用于编程）
- text：真正在文档中打印出来的定理环境的名字
- counter：计数器；一般新定义的定理环境会自己用一个新的计数器，但是可以在 counter 中传入其他的定理环境，表示和这个环境共用计数器。
- section：定理编号依赖于某个章节层次（比如：定理1.1）

例如，定义一个 “定理” 环境：

```tex
\newtheorem{theorem}{定理}
```

调用定理环境：

```tex
\begin{theorem}[勾股定理]
    若 $a,b$ 为直角三角形的两条直角边，$c$ 为斜边，那么 $a^2 + b^2 + c^2.$
\end{theorem}
```

其中方括号传入的参数是定理名字，这样子生成的 PDF 中会显示为：

> **定理1(勾股定理).** 若 a,b 为直角三角形的两条直角边， c 为斜边，那么 a2+b2=c2

## 证明类环境

amsthm 宏包已经提供了用于写证明的 proof 环境，不需要再自行定义，默认样式是引导词 “Proof” 为斜体，环境里的内容是正体，结尾会自动添加证毕符号 " ◻ "

需要注意的是，定理类环境（定理、引理、命题、推论等）和证明类环境（证明、解）的样式是不一样的，定理类环境里的内容是斜体，引导词是加粗。所以最好不要用 `\newtheorem` 定义一个定理类环境来写证明，这样子会有很长一段斜体，并且还要手工添加证毕符号

对于中文文档，可以用下面的命令把引导词 ”proof“ 改成 "证明"：

```tex
\renewcommand{\proofname}{\indent\bf 证明}
```

如果需要修改证毕符号，可以重新定义 `\qedsymbol` 命令：

```tex
\renewcommand{\qedsymbol}{$\blacksquare$}    % 证毕符号改成黑色的正方形
```

如果证明是以行间公式结束的，默认证毕符号会在行间公式的下一行出现，比较丑，可以用 `\qedhere` 命令解决

```tex
\begin{proof}
    ...
    所以：
    \[
        G(x, y) = G(y, x).  \qedhere
    \]
\end{proof}
```

有时候还需要一个 [solution](https://zhida.zhihu.com/search?content_id=117741425&content_type=Article&match_order=1&q=solution&zhida_source=entity) 环境（引导词是 “解”），希望它和 proof 环境有相同的样式，可以直接调用 proof 环境来改造：

```tex
\newenvironment{solution}{\begin{proof}[\indent\bf 解]}{\end{proof}}

% 新定义环境的命令：\newenvironment{env-name}[num-of-args]{before}{after}
% 把一段代码放到新定义的环境里，相当于自动在前面加上 before 的内容，在后面加上 after 的内容
% Proof 环境可以传参，改变引导词
```

## 定理环境的样式

可以用 `\theoremstyle{style}` 命令修改定理环境的样式，Latex 内置的样式（style参数）有三种：

1. plain（默认样式）：定理名称是正体，定理内容是斜体
2. definition：定理名称和定理内容都是正体
3. remark： 定理名称是斜体，定理内容是正体

在 `\theoremstyle{}` 语句之后的定理都会采用这种样式，直到下一次改变样式。例如：

```tex
\theoremstyle{plain}
\newtheorem{theorem}{Theorem}[section]
\newtheorem{lemma}[theorem]{Lemma}    % theorem 和 lemma 环境是 plain 样式
\theoremstyle{definition}
\newtheorem{example}{Example}[section]     % example 环境是 definition 样式
```

## 附：懒人代码

```tex
% 中文定理环境
% \indent 为了段前空两格
\newtheorem{theorem}{\indent 定理}[section]
\newtheorem{lemma}[theorem]{\indent 引理}
\newtheorem{proposition}[theorem]{\indent 命题}
\newtheorem{corollary}[theorem]{\indent 推论}
\newtheorem{definition}{\indent 定义}[section]
\newtheorem{example}{\indent 例}[section]
\newtheorem{remark}{\indent 注}[section]
\newenvironment{solution}{\begin{proof}[\indent\bf 解]}{\end{proof}}
\renewcommand{\proofname}{\indent\bf 证明}

% % English theorem environment
% \newtheorem{theorem}{Theorem}[section]
% \newtheorem{lemma}[theorem]{Lemma}
% \newtheorem{proposition}[theorem]{Proposition}
% \newtheorem{corollary}[theorem]{Corollary}
% \newtheorem{definition}{Definition}[section]
% \newtheorem{remark}{Remark}[section]
% \newtheorem{example}{Example}[section]
% \newenvironment{solution}{\begin{proof}[Solution]}{\end{proof}}
```

直接拷贝来用就行了，如果需要的话可以自行调整
