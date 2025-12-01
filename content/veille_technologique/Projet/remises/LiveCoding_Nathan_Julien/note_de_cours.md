+++
title = "Notes de cours"
weight = 2
+++

## Définition du live coding
Le live coding est un concept de programmation qui consiste à écrire du code qui sera exécuter en temps réel. Le live coding est souvent vu comme étant une prestation musicale ou graphique auquel un public peut assister.


## Comment ça fonctionne?
 Premièrement, la **transpilation** est un élément essentiels dans la plupart des technologies de live coding. Ce concept permet en réalité de traduire un langage de programmation de haut niveau veres un autre langage de haut niveau.
 Cela permet entre autre à Strudel REPL, qui utilise un librairie JavaScript pour faire créer du son, de permettre aux utilisateurs, qui sont généralement peu familiers avec les langages de programmation classiques, d'écrire du code beaucoup plus simplement. 

 La ligne : 
 ``` 'c3 [e3 g3]*2'; ```
 est transpiler en :
 ``` mini('c3 [e3 g3]*2').withMiniLocation([1, 0, 0], [1, 14, 14]); ``` 