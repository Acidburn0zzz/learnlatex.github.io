---
title: "Mise en forme du texte: fontes et espacements"
---

## Espacement des paragraphes

Nous avons d�j� vu qu'une ligne blanche dans votre saisie g�n�rera un nouveau paragraphe en LaTeX. Conform�ment aux usages typographiques, ce nouveau paragraphe commence par une indentation (ou retrait de paragraphe). Un autre style possible est de ne pas avoir d'indentations pour les paragraphes, mais plut�t d'avoir une � ligne blanche � entre eux. On peut obtenir ce r�sultat en utilisant le package `parskip`.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage[parfill]{parskip}
\usepackage{lipsum} % Pour avoir du texte de remplissage

\begin{document}
\lipsum
\end{document}
```

## Ins�rer un saut de ligne

La plupart du temps, il ne faut pas ajouter de force une coupure de ligne dans LaTeX : en fait, c'est presque toujours d'un nouveau paragraphe dont vous avez besoin, ou bien du package `parskip` pour appara�tre une � ligne blanche � entre les paragraphes, comme vu ci-dessus. 

Il y a seulement quelques endroits o� l'usage de `\\` est conseill� pour commencer une nouvelle ligne sans commencer un nouveau paragraphe :

- � la fin des lignes d'un tableau,
- Dans l'environnement `center`,
- En po�sie (dans un environnement `verse`).

Presque toujours, si vous n'�tes pas dans un de ces cas particuliers, **vous ne devriez pas** utiliser `\\`.


## Ins�rer une espace

On peut ins�rer une espace fine (d'environ la moiti� de la largeur normale) en utilisant `\,`. En mode math�matique, il y a aussi d'autres commandes : `\.`, `\:` et `\;`, et une pour l'espace n�gative : `\!`.

Tr�s rarement, par exemple lors de la cr�ation d'une page de titre, on a avoir besoin d'ajouter un espace horizontal ou vertical explicite. Les commandes `\hspace` and `\vspace` sont faite pour �a:

```latex
\documentclass{article}
\usepackage[T1]{fontenc}

\begin{document}
Un peu de texte \hspace{1cm} encore du texte.

\vspace{10cm}

Et encore davantage de texte.
\end{document}
```


## Mettre en forme le texte de fa�on explicite

Nous avons vu [il y a quelque temps](lesson-03) que le plus souvent, il est pr�f�rable de s'appuyer sur la structure logique du document. Mais il arrive parfois que l'on veuille mettre le texte en gras, en italique, en interligne simple, etc. Il existe deux types de commandes pour cela : une pour les textes courts, et une pour le texte � courant �.

Pour les petits fragments de texte, nous utilisons les commandes `\textbf`, `\textit`, `\textrm`, `\textsf`, `\texttt` et `\textsc`.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}

\begin{document}
Let's have some font fun: \textbf{bold}, \textit{italic}, \textrm{roman},
\textsf{sans serif}, \texttt{monospaced} and \textsc{small caps}.
\end{document}
```

Pour le texte courant, on utilise des commandes qui changent la police en cours ; les commandes ici sont par exemple `\bfseries` et `\itshape`. Comme l'effet de ces commandes n'a pas de fin pr�d�finie, on doit les placer dans un _groupe_ si on veut �viter qu'elles ne s'appliquent pas � l'ensemble du document. Les environnements LaTeX sont des groupes, tout comme les cellules des tableaux, ou bien on peut simplement utiliser les accolades `{...}` pour cr�er un groupe explicite.


```latex
\documentclass{article}
\usepackage[T1]{fontenc}

\begin{document}
Un peu de texte normal.

{\itshape

� partir d'ici, le texte est en italique.

Vous voyez: l'effet n'est pas limit� � un paragraphe.

}
\end{document}
```

On peut r�gler la taille des caract�res de la m�me mani�re, avec des commandes qui s'appliquent � � partir d'ici �. Elles d�finissent des tailles relatives par rapport � la taille de base: les plus courantes sont `\huge`, `\large`, `\normalsize`, `\small` et `\footnotesize`. Il est important de terminer le paragraphe _avant_ de modifier la taille de la police de caract�res � nouveau ; regardez comment nous ajoutons un `\par` explicite (coupure de paragraphe) ici:

```latex
\documentclass{article}
\usepackage[T1]{fontenc}

\begin{document}
Du texte  normal.

\begin{center}
{\itshape\large Du texte mis en forme\par}
Normal � nouveau
{\bfseries\small Enfin du texte plus petit\par}
\end{center}

\end{document}
```


## Travaux pratiques

Exp�rimentez le formatage manuel : cr�ez un environnement `titlepage`, pour une page de titre et essayez d'ins�rer diff�rents espaces et de modifier la police. Que se passe-t-il lorsque vous combinez des changements de police ? En quoi est-ce diff�rent du mode math�matique ?

Que se passe-t-il si vous changez la taille de la police d'un grand paragraphe (essayez avec `\tiny` puis avec `\huge`) mais que vous n'�mettez pas de `\par` final avant de fermer le groupe ?
