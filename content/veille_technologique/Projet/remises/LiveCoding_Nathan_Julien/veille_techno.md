+++
title = "Veille technologique"
weight = 1
+++

# Veille Technologique

## Premier Prompt

### LLM: ChatGPT

### Prompt:

On souhaite créer une veille technologique au sujet du live coding (musical et graphique). Pourrais-tu nous fournir une variété de langages/plateformes qui pourraient être intéressantes et expliquer leurs particularités distinctes ?

### Réponse: 

>Voici une sélection de langages, environnements et plateformes de live coding utilisés dans les pratiques musicales, audiovisuelles et visuelles. La liste couvre aussi bien les outils spécialisés que les approches plus hybrides. Pour chacun, je mets en évidence les particularités, philosophies et contextes d’usage.
>________________________________________
>🎶 Live Coding Musical
>1. TidalCycles
>•	Langage : DSL (Domain-Specific Language) basée sur Haskell
>•	Particularités :
>o	Très orienté pattern-based, permet de décrire des structures rythmiques et mélodiques complexes de manière concise.
>o	Paradigme déclaratif : on “décrit” des patterns plutôt que programmer pas à pas.
>o	Très populaire dans la communauté algorave.
>o	Intégration commune avec SuperDirt (moteur audio SuperCollider).
>•	Points forts : expressivité énorme, patterns polymétriques et évolutifs.
>________________________________________
>2. SuperCollider
>•	Langage : Langage dédié à la synthèse et au traitement audio
>•	Particularités :
>o	Moteur audio temps réel très performant.
>o	Langage SC qui permet autant de la synthèse que du live coding, via l’interpréteur sc-lang.
>o	Très flexible : peut servir de backend pour d’autres environnements (TidalCycles, Sonic Pi, FoxDot…).
>•	Points forts : profondeur sonore, possibilités de conception sonore avancées.
>________________________________________
>3. Sonic Pi
>•	Langage : Ruby simplifié
>•	Particularités :
>o	Conçu pour l’éducation et le live coding performant.
>o	Syntaxe très simple, accessible aux débutants, mais suffisamment riche pour des performances avancées.
>o	Intègre un moteur SuperCollider.
>•	Points forts : pédagogique, cross-platform, communauté très active.
>________________________________________
>4. FoxDot
>•	Langage : Python
>•	Particularités :
>o	Interface Python dédiée à la création musicale en live.
>o	Basé sur SuperCollider comme backend audio.
>o	Syntaxe simple et immédiate, inspirée de TidalCycles mais plus accessible.
>•	Points forts : bon compromis entre expressivité et facilité.
>________________________________________
>5. Overtone
>•	Langage : Clojure
>•	Particularités :
>o	Fonctionne sur la JVM, avec SuperCollider comme moteur audio.
>o	Permet de combiner live coding et manipulation algorithmique avancée (puisque Clojure ≈ Lisp).
>•	Points forts : puissance du functional programming + flexibilité musicale.
>________________________________________
>🎨 Live Coding Visuel / Graphique
>6. Hydra
>•	Langage : DSL JavaScript
>•	Particularités :
>o	Pensé pour le live coding vidéo interactif, inspiré des synthétiseurs vidéo analogiques.
>o	Fonctionne directement dans le navigateur ou dans des outils comme Atom/VS Code.
>o	Chaînes d’effets visuels, feedback, oscillateurs visuels.
>•	Points forts : immédiat, visuel, modulaire, parfait pour performances VJ.
>________________________________________
>7. TouchDesigner (via Python)
>•	Langage : Nodes + Python
>•	Particularités :
>o	Pas un langage de live coding pur, mais énormément utilisé en VJing et performance visuelle.
>o	Python permet de coder des scènes dynamiques en temps réel.
>o	Intègre shaders GLSL en live.
>•	Points forts : pipeline visuel professionnel, intégration hardware.
>________________________________________
>8. GLSL Live Coding (Shadertoy, Bonzomatic, etc.)
>•	Langage : GLSL
>•	Particularités :
>o	Live coding de shaders fragmentaires/vertex en temps réel.
>o	Approche mathématique et algorithmique très minute.
>o	Utilisé pour des performances visuelles ultra-réactives et abstraites.
>•	Points forts : extrêmement puissant pour des visuels génératifs spectaculaires.
>________________________________________
>9. P5.js + Live Coding Tools
>•	Langage : JavaScript
>•	Particularités :
>o	p5.js (wrapper Processing en JS) sert de base à des setups live (ex. p5live, ml5.js + p5 pour LLM/IA).
>o	Très accessible, fonctionne dans le navigateur.
>•	Points forts : apprentissage fluide, riche écosystème JS.
>________________________________________
>🎵🎨 Outils Hybrides (Audio + Visuel)
>10. Gibber / Gibberwocky
>•	Langage : JavaScript
>•	Particularités :
>o	Live coding intégré au navigateur, audio + visuel.
>o	Permet la synchronisation musique/graphisme.
>o	Interface très adaptée au live : code affiché en superposition, sliders interactifs…
>•	Points forts : très fluide pour performance AV unifiée.
>________________________________________
>11. Estuary
>•	Langage : Multi-langages (TidalCycles, Punctual, etc.)
>•	Particularités :
>o	Plateforme en ligne collaborative pour live coding audiovisuel.
>o	Permet de coder ensemble à distance.
>o	Supporte plusieurs langages et moteurs audio/visuels.
>•	Points forts : collaboration, accessibilité en ligne.
>________________________________________
>12. Max/MSP + Live Coding Extensions
>•	Langage : Patchs + GenExpr (inspiré C)
>•	Particularités :
>o	Pas du live-coding traditionnel, mais combos patching + code.
>o	Extensions pour live editing et création/démontage de patchs en performance.
>o	Forte communauté audiovisuelle.
>•	Points forts : versatile, audio/visuel/interaction.
>________________________________________
>📦 Plateformes plus expérimentales / alternatives
>13. Impromptu / Extempore
>•	Langages : Lisp-like + low-level xtlang
>•	Particularités :
>o	Permet du live coding audio, visuel et computationnel.
>o	Intéressant pour la compilation JIT en temps réel.
>•	Points forts : très bas niveau, très performant.
>________________________________________
>14. ChucK
>•	Langage : ChucK
>•	Particularités :
>o	Conçu pour le timing précis et l’audio en temps réel.
>o	Syntaxe particulière centrée sur le temps ("=> now").
>o	Permet l'exécution concurrente de processus audio.
>•	Points forts : contrôle temporel exceptionnel.
>________________________________________
>🧭 En résumé
>Outil	Domaine	Particularité clé
>TidalCycles	Audio	Patterns déclaratifs très puissants
>SuperCollider	Audio	Synthèse sonore avancée, flexible
>Sonic Pi	Audio	Très accessible, pédagogique
>FoxDot	Audio	Python + simplicité
>Overtone	Audio	Programmation fonctionnelle (Clojure)
>Hydra	Visuel	Feedback vidéo inspiré analogique
>GLSL Live	Visuel	Rend rendu GPU extrême en temps réel
>p5.js	Visuel	Accessibilité + Web
>Gibber	Audio/Visuel	Live coding AV unifié
>Estuary	Audio/Visuel	Plateforme collaborative
>Extempore	AV/Compute	Compilation JIT + low-level
>ChucK	Audio	Contrôle temporel unique
>________________________________________
>Si tu veux, je peux aussi t’aider à :
>🔹 construire une veille technologique formelle (format tableau, fiches, critères)
>🔹 proposer une sélection des plus pertinents selon ton public
>🔹 comparer les outils selon critères (facilité, maturité, esthétique sonore/visuelle)
>🔹 créer un document PDF structuré utilisable en classe ou en conférence
>Souhaites-tu approfondir un point ou produire un livrable ?

### Sources sélectionnées pour nos recherches

Pour les sources que nous avons sélectionnés, nous allons principalement utilisés la documentation des outils présenté ( Strudel, Hydra et **Outil Mix à déterminer** ).

[Strudel (Audio)](https://strudel.cc/workshop/getting-started/)
[Hydra (Graphique)](https://hydra.ojack.xyz/docs/)
[**Outil Mix**]()

Nous allons aussi nous inspirer des 2 créateurs sités un peu plus bas.

### Articles sur le "Live Coding"

[Article de Mirakl Tech Blog (2025)](https://mirakl.tech/beats-bytes-and-basslines-an-introduction-to-live-coding-with-strudel-cc-4d378e86d5b7)

[Article de WIRED(2019)](https://www.wired.com/story/algoraves-live-coding-djs/)

[Article de Medium(2022)](https://medium.com/@royce.taylor789/live-coding-6ac7ead9dbcf)

### Chaine Youtube sur le live Coding

### Live Coding Audio:

[Switch Angel (Strudel)](https://www.youtube.com/@Switch-Angel)

### Live Coding Graphique:

[Naoto Hieda (Hydra)](https://www.youtube.com/@NaotoHieda)