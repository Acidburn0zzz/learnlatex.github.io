---
title: "R�f�rences crois�es: pour aller plus loin"
---

## Transformer les r�f�rences crois�es en hyperliens

Vous pouvez transformer vos r�f�rences crois�es en hyperliens cliquables en utilisant le package `hyperref`. Dans la plupart des cas, `hyperref` doit �tre charg� apr�s tout autre package du pr�ambule de votre document.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage[hidelinks]{hyperref}
\begin{document}

\section{Introduction}
Some exciting text with a reference~\ref{sec:next}.

\section{Next thing}
\label{sec:next}

More text here.
\end{document}
```

Nous avons choisi de faire les liens de la m�me couleur que le texte normal ; enlevez l'option `hidelinks` pour comprendre pourquoi !     :)
