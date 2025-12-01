+++
title = "Notes de cours"
weight = 2
+++

## Définition du live coding
Le live coding est un concept de programmation qui consiste à écrire du code qui sera exécuter en temps réel. Le live coding est souvent vu comme étant une prestation musicale ou graphique auquel un public peut assister.

## Technologie derrière le Live Coding

La technologie derrière le Live Coding est composé de plusieurs concept et technologie qui travaille ensemble pour nous donner la possibilité de faire du live coding. Pour la présentation des technologies utilisé, elle va être divisé en plusieurs plus petit volet qui chacun aborde un certain module qui compose l'intégrité du Live Conding. 

### REPL

Un **REPL** (Read–Eval–Print Loop) est un environnement interactif dans lequel le code est lu, exécuté, puis ses effets sont immédiatement renvoyés à l’utilisateur. En live coding, le REPL sert d’interface principale pour créer et transformer la musique ou les visuels en temps réel. L’artiste écrit ou modifie du code dans une zone d’édition, puis le REPL l’interprète instantanément : chaque changement déclenche une nouvelle exécution qui met à jour le comportement du programme sans interrompre la performance. Cela permet d’essayer des idées rapidement, d’ajuster des paramètres, de superposer des motifs, ou de réagir à l’ambiance du moment. En somme, le REPL est le cœur du processus de live coding, facilitant une boucle continue d’expérimentation, de création et de rétroaction immédiate entre le code et le résultat artistique. Strudel et Replit utilise un REPL pour leur platforme de live coding.

![Diagramme REPL](diagrammeREPL.png)




## Comment ça fonctionne?
 Premièrement, la **transpilation** est un élément essentiels dans la plupart des technologies de live coding. Ce concept permet en réalité de traduire un langage de programmation de haut niveau veres un autre langage de haut niveau.
 Cela permet entre autre à Strudel REPL, qui utilise un librairie JavaScript pour faire créer du son, de permettre aux utilisateurs, qui sont généralement peu familiers avec les langages de programmation classiques, d'écrire du code beaucoup plus simplement. 

 La ligne : 
 ``` 'c3 [e3 g3]*2'; ```
 est transpiler en :
 ``` mini('c3 [e3 g3]*2').withMiniLocation([1, 0, 0], [1, 14, 14]); ``` 