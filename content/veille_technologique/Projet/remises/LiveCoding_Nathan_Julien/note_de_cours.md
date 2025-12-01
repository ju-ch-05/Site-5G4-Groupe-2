+++
title = "Notes de cours"
weight = 2
+++

## Définition du live coding
Le live coding est un concept de programmation qui consiste à écrire du code qui sera exécuter en temps réel. Le live coding est souvent vu comme étant une prestation musicale ou graphique auquel un public peut assister.

## Origines

Le live coding est s'est développé dans les années 2000 où il permettait de rassembler des artistes dans des prestations de programmation où on créait de la musique par exemple.

La Transnational Organisation for the Promotion of Live Algorithm Programming (TOPLAP) est une organisation qui a été créer en 2004 et qui a pour but de promouvoir le live coding.

Cette organisation a créer un **[manifeste](https://toplap.org/wiki/ManifestoDraft)** afin de définir le live coding ainsi que ses principes.
Les grandes lignes de ce manifeste sont les suivantes : 

+ Le code permet de voir les pensées de l'artiste.
+ Le code doit être public : Rien ne doit être caché au public.
+ Les algorithmes prévalent sur les outils utilisés.


## Comment ça fonctionne?
 Premièrement, la **transpilation** est un élément essentiels dans la plupart des technologies de live coding. Ce concept permet en réalité de traduire un langage de programmation de haut niveau veres un autre langage de haut niveau.
 Cela permet entre autre à Strudel REPL, qui utilise un librairie JavaScript pour faire créer du son, de permettre aux utilisateurs, qui sont généralement peu familiers avec les langages de programmation classiques, d'écrire du code beaucoup plus simplement. 

 La ligne : 
 ``` 'c3 [e3 g3]*2'; ```
 est transpiler en :
 ``` mini('c3 [e3 g3]*2').withMiniLocation([1, 0, 0], [1, 14, 14]); ``` 

