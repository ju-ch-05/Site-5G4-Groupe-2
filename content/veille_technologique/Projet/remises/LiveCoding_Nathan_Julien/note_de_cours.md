+++
title = "Notes de cours"
weight = 2
+++

## Définition du live coding
Le live coding est un concept de programmation qui consiste à écrire du code qui sera exécuter en temps réel. Le live coding est souvent vu comme étant une prestation musicale ou graphique auquel un public peut assister.

Le live coding est un art qui est improvisé. En effet, les performeurs vont créer leur arts en direct en n'ayant rien préparé d'avance. C'est d'ailleurs ce qui est recherché par le public, car cela permet de suivre le processus de création des artistes, notamment lorsqu'ils expérimentent et font des essais-erreurs en direct.

## Origines

Le live coding est s'est développé dans les années 2000 où il permettait de rassembler des artistes dans des prestations de programmation où on créait de la musique par exemple.

La Transnational Organisation for the Promotion of Live Algorithm Programming (TOPLAP) est une organisation qui a été créer en 2004 et qui a pour but de promouvoir le live coding.

Cette organisation a créer un **[manifeste](https://toplap.org/wiki/ManifestoDraft)** afin de définir le live coding ainsi que ses principes.
Les grandes lignes de ce manifeste sont les suivantes : 

+ Le code permet de voir les pensées de l'artiste.
+ Le code doit être public : Rien ne doit être caché au public.
+ Les algorithmes prévalent sur les outils utilisés.

## Technologie derrière le Live Coding

La technologie derrière le Live Coding est composé de plusieurs concepts et technologies qui travaillent ensemble pour nous donner la possibilité de faire du Live Coding. Pour la présentation des technologies utilisé, elle va être divisé en plusieurs plus petit volet qui chacun aborde un certain module qui compose l'intégrité du Live Conding. 

### REPL

Un **REPL** (Read–Eval–Print Loop) est un environnement interactif dans lequel le code est lu, exécuté, puis ses effets sont immédiatement renvoyés à l’utilisateur. En live coding, le REPL sert d’interface principale pour créer et transformer la musique ou les visuels en temps réel. L’artiste écrit ou modifie du code dans une zone d’édition, puis le REPL l’interprète instantanément : chaque changement déclenche une nouvelle exécution qui met à jour le comportement du programme sans interrompre la performance. Cela permet d’essayer des idées rapidement, d’ajuster des paramètres, de superposer des motifs, ou de réagir à l’ambiance du moment. En somme, le REPL est le cœur du processus de live coding, facilitant une boucle continue d’expérimentation, de création et de rétroaction immédiate entre le code et le résultat artistique. Strudel et Replit utilise un REPL pour leur platforme de live coding.

![Diagramme REPL](diagrammeREPL.png)

### Architecture Client-Serveur

L’architecture *client–serveur* appliquée au live coding repose sur une séparation entre l’environnement où l’on écrit le code (le client) et le moteur qui exécute les instructions en temps réel (le serveur). Dans SuperCollider, cette organisation se traduit par l’usage de **sclang** comme client interactif, chargé de lire et d’évaluer le code, et de **scsynth** comme serveur audio responsable de produire le son à partir de **UGens** (unit generators). Lorsqu’un·e artiste modifie un fragment de code, sclang interprète immédiatement ces changements et envoie de nouveaux messages au scsynth, qui ajuste instantanément les synthés, les patterns ou les paramètres actifs. Cette communication continue entre client et serveur permet une réponse sonore immédiate, faisant de SuperCollider un exemple clair et puissant de la manière dont l’architecture client–serveur soutient le live coding en offrant un flux créatif fluide et réactif.


## Comment ça fonctionne?
 Premièrement, la **transpilation** est un élément essentiels dans la plupart des technologies de live coding. Ce concept permet en réalité de traduire un langage de programmation de haut niveau veres un autre langage de haut niveau.
 Cela permet entre autre à Strudel REPL, qui utilise un librairie JavaScript pour faire créer du son, de permettre aux utilisateurs, qui sont généralement peu familiers avec les langages de programmation classiques, d'écrire du code beaucoup plus simplement. 

 La ligne : 
 ``` 'c3 [e3 g3]*2'; ```
 est transpiler en :
 ``` mini('c3 [e3 g3]*2').withMiniLocation([1, 0, 0], [1, 14, 14]); ``` 