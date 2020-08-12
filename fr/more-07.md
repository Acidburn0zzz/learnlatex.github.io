---
title: "Inclure des images et les faire � flotter �: pour aller plus loin"
---

## Nommer les fichiers d'images

LaTeX fonctionne sur de nombreuses plates-formes, les noms de fichiers m�ritent donc une r�flexion pour �tre portables d'un ordinateur � l'autre, surtout si vous collaborez avec d'autres personnes. Le plus s�r est de nommer vos graphiques simplement, en particulier sans espaces. Par exemple, si vous voulez organiser vos fichiers en conservant tous les graphiques dans un sous-r�pertoire, alors quelque chose comme `\includegraphics[width=30pt]{pics/mom.png}` est portable et devrait le rester dans le temps.

Les espaces dans les noms de fichiers sont souvent probl�matiques, m�me s'ils sont mieux pris en charge maintenant. De fa�on g�n�rale, si vous rencontrez des probl�mes et que vous avez des espaces dans un nom de fichier, commencez par supprimer ces espaces avant toute autre chose.

La prise en charge des caract�res accentu�s est quelque peu variable ; certains syst�mes, en particulier sous Windows, posent des probl�mes. Si vous rencontrez des probl�mes avec des noms de fichiers contenant des caract�res accentu�s, faites un test en utilisant uniquement des caract�res ASCII.


## Stocker les images dans un sous-r�pertoire

Une fa�on courante de ranger ses fichiers sources est de placer toutes les images dans un sous-r�pertoire. Vous pouvez alors les inclure par leur chemin relatif, comme illustr� ci-dessus ; notez que le caract�re `/` est utilis� pour s�parer des parties du chemin _m�me sous Windows_.

Si vous avez beaucoup d'images, vous souhaiterez peut-�tre d�finir � l'avance le sous-r�pertoire les contenant. Cela se fait en utilisant `\graphicspath`, qui n�cessite une entr�e (entre accolades `{...}`) pour chaque sous-r�pertoire. Par exemple, pour inclure les sous-r�pertoires `figs` et `pics`, on aurait :

<!-- {% raw %} -->
```latex
\graphicspath{{figs/}{pics/}}
```
<!-- {% endraw %} -->

Notez que les noms de r�pertoires doivent se terminer par un `/` final.


## Produire des graphiques

Comme nous l'avons vu, il est facile d'inclure dans un document LaTeX des images venant de la plupart des sources, y compris des graphiques de logiciels scientifiques. Dans ce cas, enregistrez-les plut�t au format PDF si vous le pouvez, car il s'agit d'un format p�renne et facile � manipuler (notamment, on peut le mettre � l'�chelle sans perte de qualit�). Si vous passez par des bitmaps, conservez une haute r�solution. Vous pouvez dessiner des images � la souris qui incluent des snippets LaTeX avec [Inkscape](https://inkscape.org/). Une alternative qui �tend ces techniques de dessin � trois dimensions est [Asymptote](https://www.ctan.org/pkg/asymptote). Ces deux logiciels produisent des fichiers que vous pourrez inclure dans votre document.

Vous pouvez �galement cr�er des dessins et graphiques parfaitement adapt�s � votre document LaTeX, utilisant la m�me police de caract�res, �ventuellement avec des formules math�matiques et des `\labels` auxquels avec vous pourrez vous r�f�rer en utilisant des packages LaTeX. Pour cela, vous pouvez dessiner directement � l'int�rieur de votre document, avec [Ti*k*Z](https://ctan.org/pkg/pgf) ou son alternative, [PSTricks](https://ctan.org/pkg/pstricks-base). Attention, c'est pratique et puissant, mais rend rapidement le code-source de vos documents plus complexe.


## Positionner des flottants

Le placement des flottants LaTeX est complexe, et parfois frustrant. La demande la plus courante consiste � placer l'image exactement l� o� elle se trouve dans le fichier d'entr�e. C'est ce que fait le package `float`.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{graphicx}
\usepackage{lipsum}  % Pour avoir du texte de remplissage
\usepackage{float}

\begin{document}
\lipsum[1-7]
\begin{figure}[H]
  \centering
  \includegraphics[width=0.5\textwidth]{example-image}
  \caption{Une image d'exemple}
\end{figure}
\lipsum[8-15]
\end{document}
```

Notez l'option `H`, qui met l'image � absolument ici � (_**h**ere_). Cependant, en r�gle g�n�rale, il est d�conseill� d'utiliser `H`, car �a a tendance � laisser de grands espaces vides dans votre document.


## D'autres types de flottants

Nous [allons bient�t voir](lesson-08) qu'on peut mettre des tableaux dans des flottants, dans un environnement `table`. Cependant, rien n'oblige � mettre les images dans des environnement `figures`, et les tableaux dans des environnements `tables` ; c'est juste une convention.

On peut d�finir d'autres types de flottants ; chaque type est ins�r� ind�pendamment. �a se fait avec le package [`trivfloat`](https://ctan.org/pkg/trivfloat), qui fournit une commande unique, `\trivfloat`, pour cr�er de nouveaux type d'environnements de flottants.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{graphicx}
\usepackage{lipsum}  % Pour avoir du texte de remplissage
\usepackage{trivfloat}
\trivfloat{image}

\begin{document}
\begin{image}
  \centering
  \includegraphics[width=0.5\textwidth]{example-image}
  \caption{Une image d'exemple}
\end{image}
\end{document}
```
