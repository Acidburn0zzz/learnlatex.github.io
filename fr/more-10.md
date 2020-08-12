---
title: "�crire les math�matiques:�pour aller plus loin"
---

## Plus d'alignements avec `amsmath`

En plus de l'environnement `align*` pr�sent� dans la le�on principale, `amsmath` propose plusieurs autres constructions pour les math�matiques � en exergue �, notamment `gather` pour les affichages multi-lignes qui ne n�cessitent pas d'alignement, et `multline` pour fractionner une grosse expression sur plusieurs lignes, en alignant la premi�re ligne � gauche, et la derni�re � droite. Dans tous les cas, la forme �toil�e (avec `*`) supprime la num�rotation des �quations.

```latex
\documentclass[a4paper]{article}
\usepackage[T1]{fontenc}

\usepackage{amsmath}

\begin{document}
Gather
\begin{gather}
  P(x)=ax^{5}+bx^{4}+cx^{3}+dx^{2}+ex +f\\
  x^2+x=10
\end{gather}

Multline
\begin{multline*}
   (a+b+c+d)x^{5}+(b+c+d+e)x^{4} \\
    +(c+d+e+f)x^{3}+(d+e+f+a)x^{2}+(e+f+a+b)x\\
    + (f+a+b+c)
\end{multline*}
\end{document}
```


### Les colonnes dans les alignements math�matiques

Les environnements d'alignement `amsmath` sont con�us pour prendre des paires de colonnes, la premi�re colonne de chaque paire �tant align�e � droite et la seconde � gauche. Cela permet d'afficher plusieurs �quations, chacune �tant align�e sur son symbole de relation.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{amsmath}
\begin{document}
Aligned equations
\begin{align*}
a &= b+1   &  c &= d+2  &  e &= f+3   \\
r &= s^{2} &  t &=u^{3} &  v &= w^{4}
\end{align*}

\end{document}
```


In addition there are variants of the display environments ending
in `ed` that make a subterm of a larger display for example, `aligned` and
`gathered`.

En outre, il existe des variantes des environnements math�matiques � en exergue � se terminant par `ed` qui font un sous-terme d'un affichage plus grand, par exemple, `aligned` et `gathered`. (_traduction en->fr � revoir_)

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{amsmath}
\begin{document}
Aligned:
\[
\left.\begin{aligned}
a&=b\\
c&=d
\end{aligned}\right\}
\Longrightarrow
\left\{\begin{aligned}
b&=a\\
d&=c
\end{aligned}\right.
\]
\end{document}
```

L'environnement `aligned` prend un argument optionnel similaire � `tabular`, utile pour aligner une formule math�matique sur sa ligne sup�rieure. Comparez par exemple les diff�rents �l�ments de la liste :

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{amsmath}
\begin{document}
\begin{itemize}
\item 
$\begin{aligned}[t]
a&=b\\
c&=d
\end{aligned}$
\item 
$\begin{aligned}
a&=b\\
c&=d
\end{aligned}$
\end{itemize}
\end{document}
```

## La gras en mode math�matique

En LaTeX standard, il y a deux fa�ons de mettre en gras des symboles math�matiques. Pour mettre une expression enti�re en gras, utilisez `\boldmath` avant l'expression. La commande `\mathbf`, elle, est faite pour mettre des lettres individuelles ou des mots en romain gras.

```latex
\documentclass[a4paper]{article}
\usepackage[T1]{fontenc}

\begin{document}


$(x+y)(x-y)=x^{2}-y^{2}$

{\boldmath $(x+y)(x-y)=x^{2}-y^{2}$ $\pi r^2$}

$(x+\mathbf{y})(x-\mathbf{y})=x^{2}-{\mathbf{y}}^{2}$
$\mathbf{\pi} r^2$ % bad use of \mathbf
\end{document}
```

Si vous souhaitez acc�der � des symboles en gras (comme le ferait `\boldmath`) dans une expression non-grasse, vous pouvez utiliser la commande `\bm` du paquet `bm`. La commande `\bm` fonctionne �galement avec des symboles tels que `=` et les lettres grecques (alors que `\mathbf` n'avait aucun effet sur `\pi` dans l'exemple ci-dessus).


```latex
\documentclass[a4paper]{article}
\usepackage[T1]{fontenc}
\usepackage{bm}

\begin{document}

$(x+\mathbf{y})(x-\mathbf{y})=x^{2}-{\mathbf{y}}^{2}$

$(x+\bm{y})(x-\bm{y}) \bm{=} x^{2}-{\bm{y}}^{2}$

$\alpha + \bm{\alpha} < \beta + \bm{\beta}$

\end{document}
```

## Le package `mathtools`

The package `mathtools` loads `amsmath` and adds several additional
features, such as variants of the `amsmath` matrix environments that
allow the column alignment to be specified.

Le paquet `mathtools` charge `amsmath` et ajoute des fonctionnalit�s suppl�mentaires, telles que des environnements pour les matrices, un peu comme ceux de `amsmath`, qui permettent de sp�cifier l'alignement des colonnes.

```latex
\documentclass[a4paper]{article}
\usepackage[T1]{fontenc}
\usepackage{mathtools}

\begin{document}

\[
\begin{pmatrix*}[r]
  10&11\\
   1&2\\
  -5&-6
\end{pmatrix*}
\]

\end{document}
```

## Math�matiques et Unicode

Comme nous le verrons dans [la le�on 14](lesson-14), il existe des variantes de moteurs TeX qui utilisent des polices OpenType. Par d�faut, ces moteurs utilisent toujours les polices math�matiques TeX classiques, mais vous pouvez utiliser le package `unicode-math` pour utiliser des polices math�matiques OpenType. Les d�tails de ce paquet ne sont pas couverts par ce cours et nous vous renvoyons [� sa documentation](https://texdoc.net/pkg/unicode-math). Cependant, voici un petit exemple:

```
% !TEX lualatex
\documentclass[a4paper]{article}
\usepackage{unicode-math}
\setmainfont{TeX Gyre Pagella}
\setmathfont{TeX Gyre Pagella Math}

\begin{document}

One two three
\[
\log \alpha + \log \beta = \log(\alpha\beta)
\]

Unicode Math Alphanumerics
\[A + \symfrak{A}+\symbf{A}+ \symcal{A} + \symscr{A}+ \symbb{A}\]

\end{document}
```
