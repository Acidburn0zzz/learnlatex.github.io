---
title: "Inclure des images et les faire � flotter �"
---

## Inclure des images

Pour ins�rer des images provenant d'autres logiciels que LaTeX, utilisez le paquet `graphicx`, qui fournit la commande `\includegraphics`.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{graphicx}

\begin{document}
Cette image
\begin{center}
  \includegraphics[height=2cm]{example-image}
\end{center}
est un fichier PDF import�.
\end{document}
```

Vous pouvez inclure des fichiers EPS, PNG, JPG et PDF. Si vous ne donnez pas l'extension du nom de fichier, `graphicx` essaiera de la deviner. Mais si vous disposez de plusieurs versions d'une image, vous pouvez la pr�ciser, par exemple, `example-image.png`.

Vous pouvez remarquer que nous avons utilis� ici un nouvel environnement, `center`, pour centrer l'image horizontalement sur la page. [Un peu plus tard](lesson-11), nous parlerons plus en d�tail de l'espacement et du positionnement.


## Modifier l'apparence des images

La commande `\includegraphics` a de nombreuses options pour contr�ler la taille et la forme des images incluses et pour rogner l'image ins�r�e. Certaines de ces options sont tr�s utilis�es, il est donc important de les conna�tre.

Les choses les plus �videntes � d�finir sont la largeur de l'image (`width`) et sa hauteur (`height`), qui sont souvent donn�es par rapport � la largeur du texte (`\textwidth`) ou � sa hauteur (`\textheight`). LaTeX mettra automatiquement l'image � l'�chelle pour que son rapport hauteur/largeur reste correct.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{graphicx}

\begin{document}
\begin{center}
  \includegraphics[height = 0.5\textheight]{example-image}
\end{center}
Un peu de texte.
\begin{center}
  \includegraphics[width = 0.5\textwidth]{example-image}
\end{center}
\end{document}
```

Vous pouvez �galement mettre � l'�chelle les images avec `scale`, ou les faire pivoter avec `angle`. L'autre chose que vous pouvez faire est de d�couper (`clip`) ou de rogner (`trim`) une image.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{graphicx}

\begin{document}
\begin{center}
  \includegraphics[clip, trim = 0 0 50 50]{example-image}
\end{center}
\end{document}
```

## Faire � flotter � les images

Traditionnellement, dans la composition de documents, et en particulier pour les documents techniques, les images et les tableaux peuvent �tre d�plac�s une ou quelques pages plus loin dans le document, ou regroup�s � plusieurs sur une page, pour mieux utiliser l'espace disponible et ne pas laisser vides de grands morceaux de pages. Ce type d'image ou de tableau s'appelle un _flottant_.

```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{graphicx}
\usepackage{lipsum}  % Pour avoir du texte de remplissage

\begin{document}
\lipsum[1-4] % Quelques paragraphes de texte

Emplacement initial
\begin{figure}[ht]
  \centering
  \includegraphics[width=0.5\textwidth]{example-image-a.png}
  \caption{An example image}
\end{figure}

\lipsum[6-10] % Quelques paragraphes de texte
\end{document}
```

Si l'on n'utilisait pas le m�canisme des flottants, l'image appra�trait juste sous le texte `Emplacement initial`. Mais quand on permet � l'image de flotter, elle est positionn�e en haut de la deuxi�me page, car il n'y a pas de place pour elle au bas de la premi�re page. L'option `ht` influence l'endroit o� LaTeX peut placer le flottant ; ces deux lettres signifient qu'il peut aller l� o� il se trouve dans la source (donc � c�t� de `Emplacement initial`) ou en haut d'une page. Vous pouvez utiliser jusqu'� quatre sp�cificateurs de position :

- `h` : ici, si possible (_**h**ere_),
- `t` : en haut d'une page (_**t**op of a page_),
- `b` : en bas d'une page (_**b**ttom of a page_),
- `p` : sur une page r�serv�e pour les flottants (_**p**age_).

[Plus tard](lesson-09), nous verrons comment faire r�f�rence � des flottants dans votre texte, afin que le lecteur puisse les trouver facilement m�me s'ils sont �t� d�plac�s de quelques pages.

Vous avez sans doute remarqu� qu'ici nous avons centr� l'image en utilisant la commande `\centering` plut�t que l'environnement `center`. � l'int�rieur d'un flottant, vous devez utiliser cette commande pour centrer horizontalement le contenu ; cela �vitera que le flottant et l'environnement `center` n'ajoutent chacun un espace vertical suppl�mentaire disgracieux.


## Travaux pratiques

Essayez d'inclure une image que vous avez cr��e, en remplacement les images standards que nous avons utilis�es dans la d�monstration.

Explorez ce que vous pouvez faire en utilisant les options `height`, `width`, `angle` et `scale`.

Utilisez le package `lipsum` pour constuire un exemple assez long, puisplacez des flotteurs en utilisant les diff�rents sp�cificateurs de position. Comment les diff�rents sp�cificateurs interagissent-ils entre eux ?
