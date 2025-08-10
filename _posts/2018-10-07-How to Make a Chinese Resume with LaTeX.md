---
layout: post
title: How to Make a Chinese Resume with LaTeX 
subtitle: Series 1 of "LaTeX - From Getting Started to Giving Up"
date: 2018-10-07T86:00:00.000Z
author: yxy
header-img: img/post-bg-glass.jpg
catalog: true
tags:
  - latex
  - skill
---


> I've been job hunting recently. Since I'm looking for a job in China, I need to make a Chinese resume. So those nice English templates like the awesome template can't be used directly. But wouldn't it be great if I could learn to transform an English template into a Chinese one? Therefore, this article records the transformation process and the final effect.

# Effect Preview

![](/img/post-fig-vague.png)

# 1 Obtain a Basic Template for Transformation

## 1.1 Where to Find Templates

1. [Latex Templates](http://www.latextemplates.com/)
2. [overleaf](https://www.overleaf.com/gallery/tagged/cv) (It merged with OverLeaf recently. Since I'm used to TeX Live, I won't use Overleaf for now, but I'll consider using Atom later.)
3. Taking a template with a photo as an example, I used [this template](https://www.overleaf.com/latex/templates/1-dot-5-column-cv/rpcbqtrsgbxm). The initial effect is as follows: ![](https://429d5421843ead24b185-b347df14968347461fc7265222280b54.ssl.cf5.rackcdn.com/gallery-images/6e08cc48d800e2a5108a7d9893d959bb584f20f0.jpeg)

## 1.2 Preparation for Compiling the Template

- TeX Live 2017
- Compile until you see the effect. There shouldn't be any problems here.

# 2 Necessary TeX Packages to Include Before Transformation

Insert the following in the LaTeX macro definition section:

```latex
\usepackage{xeCJK}
\usepackage{fontspec}
```

After that, you can compile Chinese fonts. However, at this point, all Chinese titles will use LaTeX's default font, so further modification is needed.

# 3 Font Transformation

Here, I only modified the fonts without changing the colors, advocating **minimalism** and **decluttering**.

Before transformation:

```latex
% font families
\defaultfontfeatures{Ligatures=TeX}
\newfontfamily{\cvnamefont}{Roboto Medium}
\newfontfamily{\cvsectionfont}{Roboto Medium}
\newfontfamily{\cvtitlefont}{Roboto Regular}
\newfontfamily{\cvdurationfont}{Roboto Light Italic}
\newfontfamily{\cvheadingfont}{Roboto Regular}
\setmainfont{Roboto Light}
```

After transformation:

```latex
\defaultfontfeatures{Ligatures=TeX}
% Note that even though the fonts are redefined below, you still need to use custom commands when writing to apply the fonts
\newfontfamily\kai{STKaiti.ttf}          % KaiTi (regular script)
\newfontfamily\hei{SimHei}           % SimHei (boldface)
% Redefine fonts
\newfontfamily\cvnamefont[BoldFont]{STKaiti} % For name
\newfontfamily\cvsectionfont[BoldFont]{STKaiti}
\newfontfamily\cvtitlefont[ItalicFont]{SimHei}
\newfontfamily\cvdurationfont{Times New Roman} % Use the classic font for numbers
\newfontfamily\cvheadingfont[BoldFont]{SimSun}
\setmainfont{Times New Roman}
```

Usage in writing:

```latex
\cvpersonalinfo{
    % photo
    \includegraphics[height=43mm]{fig/myphoto.jpg}
}{
    % name
   \cvname{\textbf {\kai {Jiucai}}} % Note the \kai command here; when you need to use a non-system default font, you have to use a custom command
    }
}
```

After replacing the fonts, you can happily enrich the content. Wish everyone who reads this post can get an offer.