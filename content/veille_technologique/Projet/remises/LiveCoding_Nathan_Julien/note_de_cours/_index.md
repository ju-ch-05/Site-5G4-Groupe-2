+++
title = "Notes de cours"
weight = 2
+++

## Définition du live coding

Le live coding est un concept de programmation qui consiste à écrire du code qui sera exécuter en temps réel. Le live coding est souvent vu comme étant une prestation musicale ou graphique auquel un public peut assister.

Le live coding est un art qui est improvisé. En effet, les performeurs vont créer leur arts en direct en n'ayant rien préparé d'avance. C'est d'ailleurs ce qui est recherché par le public, car cela permet de suivre le processus de création des artistes, notamment lorsqu'ils expérimentent et font des essais-erreurs en direct.

## Différentes techniques de performances

### Participation du public

Dans les spectacles de musique traditionnels, la participation du public semle automatique. En effet, les fans vont chanter les paroles en choeur étant-donné qu'ils connaissent les chansons. Lors des algoraves, les performances musicales de live coding, il est plus difficile de faire participer le public, car l'artiste lui-même ne sait pas ce qu'il jouera.

L'article [*Live Coding the Audience Participation*](https://echolab.cs.vt.edu/wp-content/uploads/sites/105/2024/05/Lee-ICLC16-LiveCodingAudienceParticipation-s77n9n.pdf) propose un moyen pour faire parciciper le public directement dans la musique qui sera jouée. Pour ce faire, le public devra télécharger une application que l'artiste pourra, en quelque sorte contrôler. Le rôle de l'artiste serait de déterminer, par exemple : 
+ Les instruments auquels le public a accès
+ Le tempo du métronome
+ Avec le hasard, quels téléphones jouent aigu et lesquels jouent grave

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

## REPL

Un **REPL** (Read–Eval–Print Loop) est un environnement interactif dans lequel le code est lu, exécuté, puis ses effets sont immédiatement renvoyés à l’utilisateur. En live coding, le REPL sert d’interface principale pour créer et transformer la musique ou les visuels en temps réel. L’artiste écrit ou modifie du code dans une zone d’édition, puis le REPL l’interprète instantanément : chaque changement déclenche une nouvelle exécution qui met à jour le comportement du programme sans interrompre la performance. Cela permet d’essayer des idées rapidement, d’ajuster des paramètres, de superposer des motifs, ou de réagir à l’ambiance du moment. En somme, le REPL est le cœur du processus de live coding, facilitant une boucle continue d’expérimentation, de création et de rétroaction immédiate entre le code et le résultat artistique. Strudel et Replit utilise un REPL pour leur platforme de live coding.

![Diagramme REPL](diagrammeREPL.png)


## Architecture Client-Serveur

L’architecture *client–serveur* appliquée au live coding repose sur une séparation entre l’environnement où l’on écrit le code (le client) et le moteur qui exécute les instructions en temps réel (le serveur). Dans SuperCollider, cette organisation se traduit par l’usage de **sclang** comme client interactif, chargé de lire et d’évaluer le code, et de **scsynth** comme serveur audio responsable de produire le son à partir de **UGens** (unit generators). Lorsqu’un·e artiste modifie un fragment de code, sclang interprète immédiatement ces changements et envoie de nouveaux messages au scsynth, qui ajuste instantanément les synthés, les patterns ou les paramètres actifs. Cette communication continue entre client et serveur permet une réponse sonore immédiate, faisant de SuperCollider un exemple clair et puissant de la manière dont l’architecture client–serveur soutient le live coding en offrant un flux créatif fluide et réactif.

# Outil de Live Coding

## Strudel REPL

**[Strudel](https://strudel.cc/)** est un environnement de **live coding musical** qui permet de créer et transformer des motifs sonores en temps réel directement dans le navigateur. Inspiré de Tidal Cycles mais entièrement basé sur JavaScript, il offre une manière simple et accessible d’explorer la composition algorithmique sans installation complexe ni connaissances préalables en programmation. En manipulant des « patterns » — des structures répétitives qui définissent rythmes, variations et textures — l’utilisateur peut improviser, expérimenter et construire des performances musicales vivantes. Strudel sert autant d’outil créatif pour les artistes que de plateforme d’apprentissage pour découvrir le live coding et ses possibilités expressives.

Strudel fonctionne grâce à un processus de **transpilation** qui transforme le code écrit par l’utilisateur en structures internes prêtes à être jouées. Lorsqu’on écrit un motif en mini-notation comme `"c3 [e3 g3]*2"`, celui-ci est converti en appels JavaScript, avec des informations de position permettant au REPL de surligner les notes jouées en temps réel pour devenir : ``` mini('c3 [e3 g3]*2').withMiniLocation([1, 0, 0], [1, 14, 14]); ```.

Le code source est d’abord analysé par **acorn** pour produire un **AST**, puis réécrit avec **escodegen** afin d’obtenir un JavaScript compréhensible par le moteur. La **mini-notation**, inspirée de Tidal, est gérée par un parseur **peggy** qui transforme les motifs en séquences Strudel (`seq`, `reify`, etc.). Chaque élément reçoit une localisation (`withLoc`) pour permettre le suivi visuel pendant l’exécution.

Une fois le `Pattern` généré, il est utilisé par un **scheduler** qui interroge régulièrement le motif pour déterminer quels événements doivent être joués. Grâce à la nature pure de `queryArc`, toute modification du code est prise en compte très rapidement, avec une faible latence.

Enfin, les événements sont envoyés à un **output**, généralement basé sur la Web Audio API, où les **control parameters** (note, forme d’onde, filtres…) définissent le rendu sonore. Ce système permet à Strudel d’offrir un environnement de live coding musical fluide, expressif et facile d’accès.

Voici un exemple de code Strudel REPL:

```
// "coastline" @by eddyflux
// @version 1.0
samples('github:eddyflux/crate')
setcps(.75)
let chords = chord("<Bbm9 Fm9>/4").dict('ireal')
stack(
  stack( // DRUMS
    s("bd").struct("<[x*<1 2> [~@3 x]] x>"),
    s("~ [rim, sd:<2 3>]").room("<0 .2>"),
    n("[0 <1 3>]*<2!3 4>").s("hh"),
    s("rd:<1!3 2>*2").mask("<0 0 1 1>/16").gain(.5)
  ).bank('crate')
  .mask("<[0 1] 1 1 1>/16".early(.5))
  , // CHORDS
  chords.offset(-1).voicing().s("gm_epiano1:1")
  .phaser(4).room(.5)
  , // MELODY
  n("<0!3 1*2>").set(chords).mode("root:g2")
  .voicing().s("gm_acoustic_bass"),
  chords.n("[0 <4 3 <2 5>>*2](<3 5>,8)")
  .anchor("D5").voicing()
  .segment(4).clip(rand.range(.4,.8))
  .room(.75).shape(.3).delay(.25)
  .fm(sine.range(3,8).slow(8))
  .lpf(sine.range(500,1000).slow(8)).lpq(5)
  .rarely(ply("2")).chunk(4, fast(2))
  .gain(perlin.range(.6, .9))
  .mask("<0 1 1 0>/16")
)
.late("[0 .01]*4").late("[0 .01]*2").size(4)
```

## Hydra

Hydra est un environnement de **live coding visuel** permettant de créer des compositions graphiques génératives en temps réel directement dans le navigateur. Inspiré des synthétiseurs vidéo modulaires, Hydra repose sur des flux visuels que l’on transforme, combine et module à l’aide de fonctions simples. Chaque instruction modifie instantanément l’image affichée, ce qui en fait un outil idéal pour le VJing, la performance audiovisuelle et l’exploration créative. Accessible, basé sur JavaScript et conçu pour encourager l’expérimentation, Hydra offre une approche intuitive de la synthèse visuelle, adaptée autant aux artistes numériques qu’aux curieux souhaitant découvrir l’art génératif.

Hydra s’appuie sur **GLSL** pour générer des visuels en temps réel, en transformant les fonctions JavaScript écrites par l’utilisateur en shaders exécutés directement sur la carte graphique. Ainsi, chaque commande comme `osc()`, `shape()` ou `noise()` correspond en réalité à un fragment de code GLSL qui sera combiné automatiquement pour former un shader complet. Ce fonctionnement rend Hydra à la fois performant et flexible, tout en conservant une interface simple côté utilisateur.

Le système de shaders d’Hydra repose sur cinq types de fonctions : les **sources**, qui génèrent les textures de base ; les **coord**, qui modifient les coordonnées ou la géométrie de l’image ; les **color**, qui ajustent ou transforment les couleurs ; les **combine**, qui permettent de mélanger plusieurs flux visuels ; et les **combineCoord**, qui introduisent des modulations plus complexes. En combinant ces blocs, Hydra construit un pipeline visuel dynamique où chaque transformation influence les suivantes.

Hydra offre également la possibilité d’étendre son langage visuel en créant ses propres fonctions GLSL grâce à `setFunction`. Cela permet aux utilisateurs avancés d’ajouter de nouveaux générateurs, effets ou opérations personnalisées, tout en continuant de profiter de l’architecture modulaire d’Hydra. Ce pont entre JavaScript et GLSL ouvre la porte à une grande expressivité visuelle, sans exiger la maîtrise complète des shaders dès le départ.

Voici un exemple de visuel possible avec Hydra:

```
// licensed with CC BY-NC-SA 4.0 https://creativecommons.org/licenses/by-nc-sa/4.0/
//trying to get closer
//by Ritchse
//instagram.com/ritchse
 
osc(60,-0.015,0.3).diff(osc(60,0.08).rotate(Math.PI/2))
	.modulateScale(noise(3.5,0.25).modulateScale(osc(15).rotate(()=>Math.sin(time/2))),0.6)
	.color(1,0.5,0.4).contrast(1.4)
	.add(src(o0).modulate(o0,.04),.6)
	.invert().brightness(0.1).contrast(1.2)
	.modulateScale(osc(2),-0.2)
  .out()
```
![Image Hydra](Hydra.png)
