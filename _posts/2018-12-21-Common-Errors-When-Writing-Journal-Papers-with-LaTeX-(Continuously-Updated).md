---
layout: post
title: A Collection of Troubles: Common Errors When Writing Journal Papers with LaTeX 
subtitle: Series 2 of "LaTeX- From Getting Started to Giving Up"
date: 2018-12-22T16:00:00.000Z
author: yxy
header-img: img/post-bg-clock.jpg
catalog: true
tags:
  - daily
  - tool
  - latex
  - skill
---

> This records the error issues encountered during the TeX writing process for journals I have submitted to, including Emerald, IEEE, ASME, Elsevier, Springer, and SPIE, all with attached solutions.

# Compilation Error Issues with .eps or .ps Images in Official Templates

Both SPIE and ASME provide templates containing .ps format images, but direct compilation will result in errors:

Original image code:

```latex
\begin{figure}
\centerline{{figure=figure/FMANU_MD_05_1107_11.ps,width=3.34in}}
\caption{Example taken from a paper that was held from production because the image quality is poor.  ASME sets figures captions in 8pt, Helvetica Bold.}
\label{fig_example1.ps}
\end{figure}
```

Error message:

![](https://pt.sjtu.edu.cn/picbucket/95136_154764087389.png)

Solution: Add packages for converting ps to pdf, then add `\psfig` before the figure path.

Corrected code:

```latex
\usepackage{epsfig}
\usepackage{auto-pst-pdf}

\begin{figure}
\centerline{\psfig{figure=figure/FMANU_MD_05_1107_11.ps,width=3.34in}}
\caption{Example taken from a paper that was held from production because the image quality is poor.  ASME sets figures captions in 8pt, Helvetica Bold.}
\label{fig_example1.ps}
\end{figure}
```

# BibTeX Compilation Error Issues

When .tex or .bbl files reference journals containing the `&` character, a warning will be triggered, such as "IEEE TRANS ON PATTERN ANALYSIS & MACHINE INTELLIGENCE" (TPAMI) and "COMPUTERS & GRAPHICS" (CG). You need to manually change `&` to `\&` in the .bbl file to resolve the error.

# Equation Alignment Issues

When needing to perform continuous equation derivations, alignment functions are usually used, and only one equation number is displayed in the typesetting. At this time, `\begin{equation}` and `\begin{aligned}` are used together. For example:

![](https://pt.sjtu.edu.cn/picbucket/95136_154763978918.png)

Code:

```latex
\begin{equation}
\begin{aligned}
\label{eq:warp3D}
\mathbf{x}_{\mathrm{c}\_i} & = W(\mathbf{x}_{\mathrm{t}\_i},\mathbf{p}_\mathrm{c}) \\
& = \mathcal{P}(\mathbf{X}_{t\_i},\mathbf{p}_0+\mathbf{p}_\mathrm{c}) \\
& = \mathbf{K}\mathbf{P}(\mathbf{p}_0)\mathbf{P}(\mathbf{p}_\mathrm{c})\mathbf{X}_{\mathrm{t}\_i}\\
& = \mathbf{K}\mathbf{P}_0\mathbf{P}_\mathrm{c}\mathbf{X}_{\mathrm{t}\_i}
\end{aligned}
\end{equation}
```

If you need to number each step of the derived equations consecutively, you should directly use `\begin{align}`. The effect and code are as follows:

![](https://pt.sjtu.edu.cn/picbucket/95136_154763995310.png)

```latex
\begin{align}
\label{eq:warp3D}
\mathbf{x}_{\mathrm{c}\_i} & = W(\mathbf{x}_{\mathrm{t}\_i},\mathbf{p}_\mathrm{c}) \\
& = \mathcal{P}(\mathbf{X}_{t\_i},\mathbf{p}_0+\mathbf{p}_\mathrm{c}) \\
& = \mathbf{K}\mathbf{P}(\mathbf{p}_0)\mathbf{P}(\mathbf{p}_\mathrm{c})\mathbf{X}_{\mathrm{t}\_i}\\
& = \mathbf{K}\mathbf{P}_0\mathbf{P}_\mathrm{c}\mathbf{X}_{\mathrm{t}\_i}
\end{align}
```

# Issues with Corresponding Author and Affiliation in Springer Journal Submissions

The Springer template does not provide code to distinguish between author affiliations and corresponding authors. Referring to the latest typesetting effect:

![](https://pt.sjtu.edu.cn/picbucket/95136_154744228829.jpg)

I wrote a version myself, with the source code and used packages as follows:

```latex
\usepackage[misc]{ifsym}

\author{XY Yin \textsuperscript{1}     \and
        Boss Fan  \textsuperscript{1,*} \and
        Xu Yang \textsuperscript{1}  \and
        Shiguang Qiu\textsuperscript{2}
}

\institute{
\Letter Boss Fan\\
\email{fan@sjtu.edu.cn}\\     
Tel.: +86-21-34206291\\     
\at
 {1} Institute of Intelligent Manufacturing and Information Engineering, Shanghai Jiao Tong University, Shanghai, 200240, China.
 \at
 {2} Chengdu Aircraft Industry (Group) Co. Ltd. of AVIC, Chengdu, 610092, China.\\
}
```

The effect is as follows: ![](https://pt.sjtu.edu.cn/picbucket/95136_154744275798.jpg)

![](https://pt.sjtu.edu.cn/picbucket/95136_154744278495.jpg)

# Issue of Converting LaTeX Equations to MathType

The thesis requires writing in `Word`, which is really frustrating. You can't write comments, can't automatically number, can't focus on content, can't compile beautiful PDFs in real-time, and dealing with equations and pseudocode is a hassle. Can't the school keep up with the times? Complaints aside, I still have to find a way. After struggling with `Pandoc` and `Aurora`, I found that **the converted TeX equations are all in the format of Word 2016's built-in equation editor**, which obviously can't pass the review. I had to struggle again with `MathType` to find a solution.

The solution is as follows: Open MathType -> Preferences -> Workspace Preferences, scroll to the bottom -> Check √ "Allow TeX language entry from keyboard".

After that, you can happily copy and paste equations from the LaTeX file:

![](https://pt.sjtu.edu.cn/picbucket/95136_154744934820.jpg)

# Typesetting Method for Cross-Column Images in Two-Column Papers

Here's the code directly; no need for diagrams. Those who use it will know. Use `*` to achieve this.

```latex
\begin{figure*}[ht] % The *实现跨栏的功能 (asterisk realizes the cross-column function); the same applies to tables.
\begin{center}
\begin{tabular}{c}
\includegraphics[width=16cm]{Graphicalabstract.jpg}
\end{tabular}
\end{center}
\end{figure*}
```

# Method to Fix Single-Column Figures and Tables

Here's the code directly; no need for diagrams. Those who use it will know. Use `[H]` to achieve this.

```latex
% Fixing a figure
\begin{figure}[H] % Achieved with [H]
\begin{center}
\begin{tabular}{c}
\includegraphics[width=7cm]{fig.png}
\end{tabular}
\end{center}
\caption
{ \label{fig:figref}
Caption of the figure. }
\end{figure}

% Fixing a table
\begin{table}[H]
\caption{\label{tab:tablabel}Caption of the table.}
\centering    
\begin{tabular}{|l|l|}
\hline
\rule[-1ex]{0pt}{3.5ex}  Parameters & Meaning  \\
\hline
\rule[-1ex]{0pt}{3.5ex} $[x_0,y_0]$ & Center of the ellipse in ICS  \\
\hline
\rule[-1ex]{0pt}{3.5ex} $a$ & Major axis length of the ellipse in ICS \\
\hline
\rule[-1ex]{0pt}{3.5ex} $b$ & Minor axis length of the ellipse in ICS\\
\hline
\rule[-1ex]{0pt}{3.5ex} $\gamma$ & Rotation angle of the ellipse in ICS\\
\hline
\end{tabular}
\end{table}
```

# Method to Fix Cross-Column Images in Two-Column Papers

Here's the code directly; no need for diagrams. Those who use it will know. Cross-column figures cannot use `[H]` as it will cause errors. Instead, use `[!htb]` to force the image to be fixed on the current page.

```latex
\begin{figure*}[!htb]
\begin{center}
\begin{tabular}{c}
\includegraphics[width=16cm]{test.jpg}
\end{tabular}
\end{center}
\caption
{ \label{fig:overflow}
Method overview.}
\end{figure*}
```