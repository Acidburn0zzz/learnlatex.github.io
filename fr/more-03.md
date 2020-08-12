---
title: "Votre premier document avec LaTeX: pour aller plus loin"
---

## Ex�cuter LaTeX

[Comme vu plus haut](lesson-02), les documents LaTeX sont simplement du texte en clair. Pour s'en rendre compte, essayez d'ouvrir votre premier document dans un simple �diteur de texte, par exemple sous Windows avec Notepad. Vous verrez le m�me texte que dans un �diteur LaTeX d�di�, mais sans aucune mise en couleur des mots-clefs.

Vous pouvez �galement compiler votre document LaTeX en PDF sans votre �diteur ; cela signifie utiliser l'invite de commande (dans le terminal), mais ne vous inqui�tez pas si vous n'�tes pas familier avec cela. Si vous *�tes familier*, vous pouvez naviguer jusqu'au r�pertoire contenant votre fichier source `.tex` et lancer 

`pdflatex first`

ou

`pdflatex first.tex`

pour compiler votre PDF. Notez que l'extension `.tex` est optionnelle : LaTeX supposera que les fichiers se terminent par `.tex`, sauf indication contraire de votre part.


## Caract�res sp�ciaux

If you need to type in a special character, most of the time you can simply
use a backslash in front of it, so for example `\{` is used to print a literal
`{`. There are a few cases where you need to use a longer command instead:

Si vous avez besoin de taper un caract�re sp�cial, la plupart du temps vous pouvez simplement utiliser une barre oblique invers�e devant ce caract�re, par exemple `\{` est utilis� pour imprimer un '{' litt�ral. Dans certains cas, vous devrez utiliser une commande plus longue :

| Symbole | Commande courte (maths et texte) | Commande longue (texte seulement) |
| `{`     | `\{`            | `\textbraceleft`   |
| `}`     | `\}`            | `\textbraceright`  |
| `$`     | `\$`            | `\textdollar`      |
| `%`     | `\%`            |                    |
| `&`     | `\&`            |                    |
| `#`     | `\#`            |                    |
| `_`     | `\_`            | `\textunderscore`  |
| ``\``   |                 | `\textbackslash`   |
| `^`     |                 | `\textasciicircum` |
| `~`     |                 | `\textasciitilde`  |

Pour les trois derniers symboles, il n'y a pas de commandes courtes disponibles, car `\\` est utilis� pour indiquer un retour � la ligne et `\~` et `\^` sont utilis�s pour produire des accents tilde et circonflexe lorsqu'on utilise uniquement des caract�res ASCII en entr�e.
