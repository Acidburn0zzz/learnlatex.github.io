---
title: "Utiliser les classes de documents pour changer l'apparence: pour aller plus loin"
---

## Classes sp�cifiques d'un journal

De nombreuses journaux scientifiques proposent leur classe LaTeX pour les soumissions d'articles. Celle-ci donne g�n�ralement une mise en page proche de celle du journal final, bien que cela d�pende de l'utilisation des polices de caract�res, etc. ; parfois, la mise en forme reste g�n�rique, mais l'utilisation de la classe du journal facilite l'import de votre article dans leur cha�ne de traitement. Si une classe est disponible, elle est normalement mise � disposition directement par l'�diteur du journal (sur son site web), qui doit donner les d�tails n�cessaires � son utilisation. Nombre d'entre elles sont �galement disponibles sur CTAN et dans des distributions TeX standards.


## Classes pour les diaporamas

Un domaine tr�s particulier est la cr�ation de diaporamas (pr�sentations type Microsoft Powerpoint). La classe `slides` avait �t� con�ue pour la production de diapositives 24x36mm et n'est pas vraiment faite pour les pr�sentations destin�es � un vid�o-projecteur. Deux classes ont �t� d�velopp�es � cet effet et sont largement utilis�es : `beamer` et `powerdot`. Actuellement, `beamer` est le plus largement utilis�, voici donc un exemple de son fonctionnement :

```latex
\documentclass{beamer}
\usepackage[T1]{fontenc}
\begin{document}

\begin{frame}{Premi�re diapositive}
  Un peu de texte
\end{frame}

\begin{frame}{Deuxi�me diapositive}
  Autre texte
  \begin{itemize}
    \item<1-> Premier item,
    \item<2-> Second item.
  \end{itemize}
\end{frame}

\end{document}
```

Cela montre deux choses importantes. Premi�rement, `beamer` divise un document en `frames` (� cadres �), chacun d'eux pouvant donner plus d'une diapositive. Deuxi�mement, `beamer` ajoute des possibilit�s � la syntaxe LaTeX normale pour permettre � certaines parties du document d'appara�tre petit � petit, formant des animations. C'est un outil puissant, mais plus compliqu� que ce que nous pouvons couvrir ici : [consultez cet article de blog](https://www.texdev.net/2014/01/17/the-beamer-slide-overlay-concept/) pour en savoir plus.


## Classe pour produire des images

Parfois vous devez composer une image (qui peut avoir un code-source tr�s long) avec LaTeX. Dans ce cas, souvent, vous ne voulez rien d'autre que l'image dans le PDF final, sans le reste de la page. Le plus simple est d'utiliser la classe [`standalone`](https://ctan.org/pkg/standalone). Elle d�finit automatiquement la taille de la page pour qu'elle entoure le contenu imprim�.


```latex
\documentclass{standalone}
\usepackage[T1]{fontenc}
\begin{document}
Un document tr�s simple: il va tenir dans une toute petite bo�te!
\end{document}
```
