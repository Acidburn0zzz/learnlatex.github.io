---
title: "Les tableaux"
---


## Tableaux simples

En LaTeX, un tableau se construit dans un environnement `tabular`. Cette le�on suppose que vous chargez le package `array`, qui ajoute des fonctionnalit�s aux tableaux LaTeX. Il n'est pas int�gr� dans le noyau LaTeX, mais c'est uniquement pour des raisons historiques et vous avez int�r�t � le charger d�s que vous utilisez des tableaux. Mettez donc ce qui suit dans votre pr�ambule et nous sommes pr�ts � commencer :

```latex
\usepackage{array}
```
{: .noedit :}

Pour composer un tableau dans un environnement `tabular`, nous devons indiquer � LaTeX combien de colonnes seront n�cessaires et comment elles doivent �tre align�es. Cela se fait dans un argument obligatoire de l'environnement &ndash; souvent appel� _pr�ambule_ du tableau &ndash; dans lequel vous sp�cifiez les colonnes en utilisant des noms � une lettre (les _preamble-tokens_). Les types de colonnes disponibles sont les suivants :

<!-- Don't line wrap this table, markdown seems to not support this. -->

| type       | description |
| ---        |:-- |
| `l`        | colonne align�e � gauche (_**l**eft_). |
| `c`        | colonne centr�e (_**c**entered_). |
| `r`        | colonne align�e � droite (_**r**ight_). |
| `p{width}` | colonne de largeur fix�e, �gale � `width`; le texte sera automatiquement justifi�, avec des saurs de lignes si n�cessaire. |
| `m{width}` | comme `p`, mais centr� verticalement par rapport au reste de la ligne. |
| `b{width}` | comme `p`, mais positionn� en bas par rapport au reste de la ligne. |
| `w{align}{width}` | fixe la largeur de la colonne � `width`, mais le contenu peut d�border s'il est trop grand. L'alignement horizontal `align` peut �tre `l`, `c`, or `r`, comme d�crit ci-dessus. |
| `W{align}{width}` | comme `w`, mais vous aurez un avertissement en ca de d�bordement. |


En outre, il existe quelques autres _preamble-tokens_ qui ne d�finissent pas une colonne mais s'av�rent utiles :

<!-- Don't line wrap this table, markdown seems to not support this. -->

| type | description |
| ---  | :-- |
| `*{num}{string}` | r�p�te `num`  fois la cha�ne `string` dans le pr�ambule. Permet de d�finir plusieurs colonnes identiques. |
| `>{decl}` | ajoute la cha�ne `decl` devant le contenu de chaque cellule de la colonne qui suit (permet par exemple de changer la police de cette colonne). |
| `<{decl}` | ajoute la cha�ne `decl` apr�s le contenu de chaque cellule de la colonne qui pr�c�de. |
| <span>`|`</span>  | trace un trait vertical. |
| `@{decl}` | remplace l'espace entre deux colonne par la cha�ne `decl`. |
| `!{decl}` | ajout la cha�ne `decl` au centre de l'espace entre deux colonnes. |

Ces deux tableaux r�pertorient tous les types de colonnes disponibles avec LaTeX et le package `array`. Quelques types de colonnes suppl�mentaires, provenant d'autres paquets, sont pr�sent�s [en approfondissement](more-08) de cette le�on.

Les colonnes `l`, `c` et `r` auront la largeur naturelle de la cellule la plus large. Chaque colonne doit �tre d�clar�e, donc si vous voulez trois colonnes centr�es, vous utiliserez `ccc` dans le pr�ambule du tableau. Les espaces sont ignor�es, donc `c c c` donne la m�me chose.

Dans le corps du tableau, les colonnes sont s�par�es par une esperluette `&` et une nouvelle ligne est commenc�e avec `\\`. Il n'y a pas besoin de d�clarer � l'avance le nombre de lignes du tableau.

Nous avons maintenant tout ce qu'il faut pour construire notre premi�re table. Dans le code suivant, les `&` et `\\` sont align�s. Ce n'est pas n�cessaire en LaTeX, mais �a aide � lire le code source et � trouver les erreurs �ventuelles.

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}

\begin{document}
\begin{tabular}{lll}
  Animal & Food  & Size   \\
  dog    & meat  & medium \\
  horse  & hay   & large  \\
  frog   & flies & small  \\
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->

Si une colonne de tableau contient beaucoup de texte, vous aurez du mal � avoir un beau r�sultat avec seulement `l`, `c` et `r`. Regardez l'exemple suivant :

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}

\begin{document}
\begin{tabular}{cl}
  Animal & Description \\
  Chien  & Le chien est un membre du genre Canis, qui fait partie des Canid�s
           proches du loup, et est le carnivore terrestre le plus
           r�pandu. \\
  Cat    & Le chat est une esp�ce domestique de petit mammif�re carnivore. C'est
           la seule esp�ce domestiqu�e de la famille des F�lins et on l'appelle
           souvent le chat domestique pour le distinguer des autres membres de la
           famille, tous sauvages. \\
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->

Le probl�me est qu'une colonne de type `l` d�roule son contenu sur une seule ligne, et prend sa largeur naturelle, m�me si la page n'est pas assez large. Pour r�soudre ce probl�me, vous pouvez utiliser une colonne de type `p`. Celle-ci met son contenu sous forme de paragraphes avec la largeur que vous sp�cifiez, et aligne ces paragraphe verticalement en haut et en bas. Comparez le r�sultat de ce nouvel exemple avec le pr�c�dent :

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}

\begin{document}
\begin{tabular}{cp{9cm}}
  Animal & Description \\
  Chien  & Le chien est un membre du genre Canis, qui fait partie des Canid�s
           proches du loup, et est le carnivore terrestre le plus
           r�pandu. \\
  Chat   & Le chat est une esp�ce domestique de petit mammif�re carnivore. C'est
           la seule esp�ce domestiqu�e de la famille des F�lins et on l'appelle
           souvent le chat domestique pour le distinguer des autres membres de la
           famille, tous sauvages. \\
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->

Si votre tableau comporte de nombreuses colonnes du m�me type, vous pouvez vous faciliter la viee en utilisant `*{nombre}{cha�ne}`, qui r�p�te `nombre` de fois la `cha�ne`. Ainsi, `*{6}{c}` est �quivalent � `cccccc`. Pour vous montrer que cela fonctionne, voici le premier tableau de cette le�on avec cette nouvelle syntaxe :

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}

\begin{document}
\begin{tabular}{*{3}{l}}
  Animal & Food  & Size   \\
  dog    & meat  & medium \\
  horse  & hay   & large  \\
  frog   & flies & small  \\
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->


## Tirer des traits entre les lignes

Un conseil avant de parler des traits : ceux-ci doivent �tre utilis�s parcimonieusement dans les tableaux, et de fa�on g�n�rale, les traits verticaux donnent un rendu peu professionnel. En fait, pour obtenir des  tableaux au look professionnel, il vaut mieux se passer des traits fournis en standard par LaTeX, et utiliser � la place le package `booktabs`. C'est pourquoi nous en parlons en premier lieu. Par souci d'exhaustivit�, les lignes standards sont [pr�sent�es en approfondissement](more-08).

`booktabs` provides four different types of lines. Each of those commands has to
be used as the first thing in a row or following another rule.
Three of the rule commands are: `\toprule`, `\midrule`, and
`\bottomrule`. From their names the intended place of use should be clear:

Le package `booktabs` propose quatre types de traits diff�rents. Chacune de ces commandes doit �tre utilis�e au d�but d'une ligne, ou juste apr�s un autre trait. Les trois principales commandes sont : `\toprule` (pour le haut du tableau), `\midrule` (pour le corps du tableau) et `\bottomrule` (pour le bas du tableau) :

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}
\usepackage{booktabs}

\begin{document}
\begin{tabular}{lll}
  \toprule
  Animal & Food  & Size   \\
  \midrule
  dog    & meat  & medium \\
  horse  & hay   & large  \\
  frog   & flies & small  \\
  \bottomrule
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->

La quatri�me commande fournie par `booktabs` pour tracer des traits est `\cmidrule`. Elle peut �tre utilis�e pour tirer un trait qui ne couvre pas toute la largeur du tableau mais seulement une plage de colonnes sp�cifi�e. La plage de colonnes est entr�e comme une plage de num�ros de colonnes : `{`_num�ro_`-`_num�ro_`}`. M�me si vous ne voulez dessiner le trait que pour une seule colonne, vous devez la sp�cifier comme une plage (avec deux num�ros identiques: `{2-2}`).

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}
\usepackage{booktabs}

\begin{document}
\begin{tabular}{lll}
  \toprule
  Animal & Food  & Size   \\
  \midrule
  dog    & meat  & medium \\
  \cmidrule{1-2}
  horse  & hay   & large  \\
  \cmidrule{1-1}
  \cmidrule{3-3}
  frog   & flies & small  \\
  \bottomrule
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->


Il existe une autre fonctionnalit� de `\cmidrule` qui contribue � un rendu de qualit�: on peut raccourcir le trait � chaque extr�mit� avec un argument optionnel entre parenth�ses :

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}
\usepackage{booktabs}

\begin{document}
\begin{tabular}{lll}
  \toprule
  Animal & Food  & Size   \\
  \midrule
  dog    & meat  & medium \\
  \cmidrule{1-2}
  horse  & hay   & large  \\
  \cmidrule(r){1-1}
  \cmidrule(rl){2-2}
  \cmidrule(l){3-3}
  frog   & flies & small  \\
  \bottomrule
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->

Vous avez sans doute devin� que `r` et `l` signifient que le trait est raccourci � son extr�mit� droite (_**r**ight_) et  gauche (_**l**eft_), respectivement.

Parfois, un trait serait une s�paration trop forte entre deux lignes, mais vous souhaitez quand m�me ajouter une forme de s�paration pour aider � la lecture du tableau. Dans ce cas, vous pouvez utiliser `\addlinespace` pour ins�rer un petit peu plus d'espace entre les lignes.

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}
\usepackage{booktabs}

\begin{document}
\begin{tabular}{cp{9cm}}
  \toprule
  Animal & Description \\
  \midrule
  Chien  & Le chien est un membre du genre Canis, qui fait partie des Canid�s
           proches du loup, et est le carnivore terrestre le plus
           r�pandu. \\
  \addlinespace
  Chat   & Le chat est une esp�ce domestique de petit mammif�re carnivore. C'est
           la seule esp�ce domestiqu�e de la famille des F�lins et on l'appelle
           souvent le chat domestique pour le distinguer des autres membres de la
           famille, tous sauvages. \\
  \bottomrule
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->


## Fusionner des cellules

En LaTeX, vous pouvez fusionner des cellules horizontalement en utilisant la commande `\multicolumn`. Elle doit appara�tre en premier dans une cellule. `\multicolumn` prend trois arguments :

1. Le nombre de cellules � fusionner,
2. L'alignement de la cellule r�sultante,
3. Le contenu de la cellule r�sultante.

L'alignement peut contenir tout ce qui est autoris� dans le pr�ambule d'un tableau, mais _seulement un seul type de colonne_:

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}
\usepackage{booktabs}

\begin{document}
\begin{tabular}{lll}
  \toprule
  Animal & Food  & Size   \\
  \midrule
  dog    & meat  & medium \\
  horse  & hay   & large  \\
  frog   & flies & small  \\
  fuath  & \multicolumn{2}{c}{unknown} \\
  \bottomrule
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->


Vous pouvez �galement utiliser `\multicolumn` sur une seule cellule pour emp�cher l'application de ce que vous avez d�fini dans le pr�ambule du tableau pour la colonne actuelle.  L'exemple suivant utilise cette m�thode pour centrer la ligne d'en-t�te du tableau :

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}
\usepackage{booktabs}

\begin{document}
\begin{tabular}{lll}
  \toprule
  \multicolumn{1}{c}{Animal} & \multicolumn{1}{c}{Food} & \multicolumn{1}{c}{Size} \\
  \midrule
  dog    & meat  & medium \\
  horse  & hay   & large  \\
  frog   & flies & small  \\
  fuath  & \multicolumn{2}{c}{unknown} \\
  \bottomrule
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->


La fusion verticale des cellules n'est pas prise en charge par LaTeX. En g�n�ral, il suffit de laisser les cellules vides pour donner au lecteur une id�e correcte de ce que l'on veut dire, sans que les cellules s'�tendent r�ellement sur plusieurs lignes.

<!-- {% raw %} -->
```latex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{array}
\usepackage{booktabs}

\begin{document}
\begin{tabular}{lll}
  \toprule
  Group     & Animal & Size   \\
  \midrule
  herbivore & horse  & large  \\
            & deer   & medium \\
            & rabbit & small  \\
  \addlinespace
  carnivore & dog    & medium \\
            & cat    & small  \\
            & lion   & large  \\
  \addlinespace
  omnivore  & crow   & small  \\
            & bear   & large  \\
            & pig    & medium \\
  \bottomrule
\end{tabular}
\end{document}
```
<!-- {% endraw %} -->


## Travaux pratiques

Utilisez le premier exemple ci-dessus pour exp�rimenter avec les tableaux. Essayez diff�rents alignements en utilisant les types de colonnes `l`, `c` et `r`. Que se passe-t-il si vous avez trop peu d'�l�ments dans une ligne de tableau ? Et si vous en avez trop ? Essayez la commande `\multicolumn` pour �tendre le contenu sur plusieurs colonnes.
