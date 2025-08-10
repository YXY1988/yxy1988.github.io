---
layout: post
title: General Typesetting Tutorial for LaTeX Journals and Conferences
subtitle: Series 3 of "LaTeX - From Getting Started to Giving Up"
date: 2019-01-13T16:00:00.000Z
author: yxy
header-img: img/post-bg-coffee.jpg
catalog: true
tags:
  - daily
  - tool
  - latex
  - skill
---

> As a coder and PhD candidate, Markdown and TeX are basic skills. Unless the client insists on Word documents, I always use .md/.tex to get things done. The original templates provided by various publishers for journals and conferences include cover patterns and other elements that go without saying. This article records the tools involved in typesetting figures, tables, literature citations, pseudocodes, and equations. This blog will be continuously updated, serving as a way to relieve stress during thesis writing.

# Hyperref
My favorite feature, so I'll put it first! Hyperlinks are satisfying to use, and the more you use them, the more satisfying they are~~ Code:

```latex
\usepackage{hyperref}
\usepackage{url}
\usepackage{xcolor}
```

Effect:

![](https://pt.sjtu.edu.cn/picbucket/95136_154752494908.png)

![](https://pt.sjtu.edu.cn/picbucket/95136_154752503783.png)

![](https://pt.sjtu.edu.cn/picbucket/95136_154752511482.png)

# Sections & Subsections
The structure of sections, subsections, and acknowledgements is the same across different journals. You can directly copy them when submitting to another journal. Code:

```latex
\section{Introduction} % Section 1
\label{sec:intro}
Your text comes here.

\section{Related work} % Automatically formatted as Section 2
\label{sec:rw}

\subsection{Subsection title} % Automatically formatted as Subsection
\label{sec:sub1}
Here's an example of section citation (see Section.~\ref{sec:intro}).

\begin{acknowledgements}
If you'd like to thank anyone.
\end{acknowledgements}
```

Effect:

![](https://pt.sjtu.edu.cn/picbucket/95136_154752553572.png)

# Single Figure
```latex
\begin{figure}[H]
\label{fig:example}
\centering
\includegraphics[height=5.5cm]{fig/example.jpg}
\caption{Figure title.}
\end{figure}
```

The caption and label can also be written separately.

~~There should be a figure here, but I'm too lazy, so no guarantee of an update~~

# Multi Figures
```latex
\begin{figure}[th]
\centering
\subfigure[Title]{\includegraphics[height=3cm]{imgFilePath}}
% Use \\ to control line breaks; set height or width according to the layout width, calculate the number of figures to insert, and then compute the size yourself.
\caption{Assembly process simulation}
\label{fig:SimpleBright}
\end{figure}
```

~~There should be a figure here, but I'm too lazy, so no guarantee of an update~~

# Equations
LaTeX uses [MathJax](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference) syntax. Codes for special characters can be obtained through handwritten recognition on [detexify](http://detexify.kirelabs.org/classify.html). The code for the main part of an equation is as follows:

```latex
\begin{equation}
\label{eq:eqlabel}
\end{equation}
```

It's worth noting that:
- Number fields are represented using hollow fonts: `\mathbb{R}` $\mathbb{R}$
- Vectors and matrices use bold fonts: `\mathbf{p}` $\mathbf{p}$
- Images, data, and sets use script fonts, e.g.: `\mathcal{I}` $\mathcal{I}$
- Non-variable subscripts that describe meanings should be in roman font instead of the default italic. For example, the image captured by a camera, $\mathcal{I}$, is written as `\mathcal{I}_\mathrm{c}` $\mathcal{I}_\mathrm{c}$

~~There should be a figure here, but I'm too lazy, so no guarantee of an update~~

# Tables

# Algorithms (Pseudocode) (Updated on January 26, 2021)
## English-only: algorithm + algorithmic
## Chinese pseudocode: algorithm + algorithmic + ctex
## Embedding pseudocode in Word with Aurora (English-only, cannot use ctex)

# References of all types of materials
Cite and hyperlink the above materials in the article