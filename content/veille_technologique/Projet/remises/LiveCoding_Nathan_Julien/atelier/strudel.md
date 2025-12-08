+++
title = "Strudel REPL"
weight = 2
+++

>[!info]
>Voici le lien vers la plateforme [Strudel REPL](https://strudel.cc/)

## Patterns

Les patterns en Strudel REPL sont très importants. Ils permettent de produire des sons que nous avons modelé nous-même et de les faire jouer avec d'autres patterns.

Le mot clé pour faire un pattern est `$: `

## Sons et instrumments de batterie

Pour concevoir un son, il faut utiliser la fonction `s()`

Voici la liste des instruments que l'on peut mettre dans la fonction `s()` : 

- `bd` : Grosse caisse (Bass Drum)
- `sd` : Caisse claire (Snare Drum)
- `hh` : Charley fermé (Hi-Hat)
- `oh` : Charley ouvert (Open Hat)
- `cp`: Clap

En séparant chaque instrument d'un espace, chaque instrument jouera à chaque temps. Voici un premier exemple que vous pouvez essayer à l'instant : `$: s("bd sd bd sd")`