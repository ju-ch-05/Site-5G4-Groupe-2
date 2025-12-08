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

Voici la liste des instruments les plus utilisés que l'on peut mettre dans la fonction `s()` : 

- `bd` : Grosse caisse (Bass Drum)
- `sd` : Caisse claire (Snare Drum)
- `hh` : Charley fermé (Hi-Hat)
- `oh` : Charley ouvert (Open Hat)
- `cp`: Clap

En séparant chaque instrument d'un espace, chaque instrument jouera à chaque temps. Voici un premier exemple que vous pouvez essayer à l'instant : `$: s("bd sd bd sd")`

## Séquences

Une séquence jouera en un cycle. On peut définir la durée d'un cycle avec la fonction `setcps(x)` où x est la durée d'un cycle en secondes.

### Modificateurs de séquences.

On peut décider du comportement d'une séquence avec certains caractères clés. En voici quelque uns : 
- `   `  (espace) : L'espace va faire en sorte de jouer tous les sons de la séquences en un cycle. Donc, plus il y en a, plus la séquence jouera rapidement. L'exemple de la section précédente montre l'utilisation de l'espace.
- `<>`: Dans un cycle, un seul élément entre crochets jouera à la fois. Donc, plus il y en a, plus il faudra de cycle pour terminer la séquence. Voici un exemple simple : `$: s("bd <bd sd> sd")`. Ici, ce qui est entre crochet jouera en alternance à chaque fois que la séquence est répétée.
- `[]`: Les crochets sont utilisés pour faire des sous-séquences. Elles auront le même comportement que les séquences, sauf qu'elles sont elles-même dans une séquence. Voici un exemple simple : `$: s("[bd sd] bd sd")`. Ce qui se trouve dans la sous-séquence jouera plus rapidement étant donné qu'un cycle pour la sous-séquence est équivalent à un temps de la séquence dans laquelle elle se trouve.
- `*x` où x représente l'incrément de rapidité. : Ce qui précède l'astérisque jouera x fois plus rapidement. Voici un exemple : `$: s("bd*2 sd bd sd")`. Ici, le premier son de la grosse caisse jouera 2 fois en un temps.
- `~` ou `-` :  Ces symboles agissent comme des instruments, sauf qu'ils produisent un silence. Voici un exemple : `$: s("bd sd ~ bd sd")`
- `,`: La virgule sert à faire jouer des sons parallèlement. Voici un exemple simple : `$: s("bd sd, hh oh")`. Ici, la grosse caisse et le charley fermé joueront en même temps et la caisse clair et le charley ouvert joueront ensemble par la suite.

Maintenant, essayez de créer une séquence qui utilise tous ces modificateurs. Vous êtes libre de décider comment cette dernière va sonner.

>[!info]- **Exemple**
>```
>setcps(2)
>$: s("bd*2 [~ sd] , <hh oh>")
>```