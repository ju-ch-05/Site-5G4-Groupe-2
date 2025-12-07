+++
title = "Atelier"
weight = 2
+++

## Atelier Hydra - Guide des Fonctions

Voici un lien vers la plateforme en ligne: [Hydra](https://hydra.ojack.xyz/)

## 1. Sources (Source)

Les sources sont le point de départ de toute création visuelle dans Hydra.

### Sources Génératives
```javascript
// Bruit aléatoire
noise(scale, offset)
noise(10, 0.1).out()

// Oscillateur (ondes)
osc(frequency, sync, offset)
osc(20, 0.1, 0).out()

// Formes géométriques
shape(sides, radius, smoothing)
shape(4, 0.3, 0.01).out()

// Diagramme de Voronoi
voronoi(scale, speed, blending)
voronoi(5, 0.3, 0.3).out()

// Dégradé
gradient(speed)
gradient(1).out()

// Couleur solide
solid(r, g, b, a)
solid(1, 0, 0.5, 1).out()
```

### Sources Externes
```javascript
// Source externe (src, prev, out)
s0.initCam()        // Initialiser la caméra
src(s0).out()       // Utiliser la caméra

s1.initImage("url") // Charger une image
src(s1).out()

// Utiliser le buffer précédent
prev().out()
```

### Exercice 1
Créez 3 visuels différents en utilisant `noise()`, `osc()` et `initImage()` Expérimentez avec les paramètres.

---

## 2. Géométrie (Geometry)

Transformations spatiales des visuels.

```javascript
// Rotation
rotate(angle, speed)
osc(20).rotate(0.5, 0.1).out()

// Échelle
scale(amount, xMult, yMult)
shape(4).scale(1.5).out()

// Pixelisation
pixelate(x, y)
noise().pixelate(20, 20).out()

// Répétition
repeat(repeatX, repeatY, offsetX, offsetY)
shape(3).repeat(3, 3).out()

repeatX(times, offset)
repeatY(times, offset)

// Kaléidoscope
kaleid(sides)
noise(3).kaleid(4).out()

// Défilement
scroll(scrollX, scrollY, speedX, speedY)
osc(10).scroll(0.5, 0.5).out()

scrollX(amount, speed)
scrollY(amount, speed)
```

### Exercice 2
Créez un kaléidoscope animé en combinant `noise()`, `kaleid()` et `rotate()`.

## 3. Couleur (Color)

Manipulation des couleurs et de la luminosité.

```javascript
// Postérisation (réduction des couleurs)
posterize(bins, gamma)
gradient().posterize(5).out()

// Décalage de couleur
shift(r, g, b, a)
osc(10).shift(0.5, 0.2, 0.1).out()

// Inversion des couleurs
invert(amount)
shape(4).invert(1).out()

// Contraste
contrast(amount)
noise().contrast(2).out()

// Luminosité
brightness(amount)
osc(20).brightness(0.5).out()

// Luma (noir et blanc)
luma(threshold, tolerance)
gradient().luma(0.5).out()

// Seuil (threshold)
thresh(threshold, tolerance)
noise().thresh(0.5, 0.1).out()

// Colorisation
color(r, g, b, a)
noise().color(1, 0, 0.5).out()

// Saturation
saturate(amount)
gradient().saturate(2).out()

// Teinte
hue(amount)
osc(10).hue(0.5).out()

// Colorama (rotation de teinte)
colorama(amount)
gradient().colorama(0.5).out()

// Canaux individuels
r(scale, offset)
g(scale, offset)
b(scale, offset)
a(scale, offset)
```

### Exercice 3
Prenez une source et appliquez au moins 4 transformations de couleur différentes.

## 4. Mélange (Blend)

Combinaison de plusieurs sources visuelles.

```javascript
// Addition
add(texture, amount)
osc(10).add(noise(3), 0.5).out()

// Soustraction
sub(texture, amount)
gradient().sub(shape(4), 0.5).out()

// Superposition
layer(texture)
solid(1, 0, 0).layer(osc(20, 0.1, 0)).out()

// Mélange
blend(texture, amount)
noise(5).blend(osc(10), 0.5).out()

// Multiplication
mult(texture, amount)
gradient().mult(shape(3), 1).out()

// Différence
diff(texture)
osc(20).diff(shape(4)).out()

// Masque
mask(texture)
noise(10).mask(shape(4, 0.5)).out()

// Somme (sum)
sum(texture)
osc(10, 0.1).sum(shape(4)).out()
```

### Exercice 4
Créez une composition en mélangeant au moins 3 sources différentes avec différentes techniques de blend.

## 5. Modulation (Modulate)

Les fonctions de modulation utilisent une texture pour déformer une autre texture.

```javascript
// Modulation de répétition
modulateRepeat(texture, repeatX, repeatY, offsetX, offsetY)
osc(10).modulateRepeat(noise(3), 3, 3).out()

modulateRepeatX(texture, times, offset)
modulateRepeatY(texture, times, offset)

// Modulation de kaléidoscope
modulateKaleid(texture, nSides)
noise(5).modulateKaleid(osc(10), 4).out()

// Modulation de défilement
modulateScrollX(texture, scrollX, speed)
modulateScrollY(texture, scrollY, speed)

// Modulation générale
modulate(texture, amount)
shape(4).modulate(noise(3), 0.5).out()

// Modulation d'échelle
modulateScale(texture, multiple, offset)
osc(10).modulateScale(noise(5), 2).out()

// Modulation de pixelisation
modulatePixelate(texture, multiple, offset)
gradient().modulatePixelate(noise(3), 10).out()

// Modulation de rotation
modulateRotate(texture, multiple, offset)
shape(3).modulateRotate(noise(2), 2).out()

// Modulation de teinte
modulateHue(texture, amount)
gradient().modulateHue(osc(10), 0.5).out()
```

### Exercice 5
Créez un effet de distorsion complexe en utilisant `modulate()` avec du bruit.

## 6. Paramètres Globaux (Synth Settings)

Contrôle de l'environnement Hydra.

```javascript
// Sortie vers un buffer
out(o0)  // Buffer principal
out(o1)  // Buffer secondaire
out(o2)
out(o3)

// Rendu
render(buffer)
render(o0)

// Résolution
setResolution(width, height)

// Arrêter tous les visuels
hush()

// Vitesse globale
speed = 2  // Double vitesse

// BPM (pour sync audio)
bpm = 120

// Variables temporelles
time      // Temps écoulé
mouse.x   // Position X de la souris
mouse.y   // Position Y de la souris

// Dimensions
width     // Largeur du canvas
height    // Hauteur du canvas
```

### Exercice 6
Créez une animation qui réagit à la position de la souris en utilisant `mouse.x` et `mouse.y`.

## 7. Projet Final - Composition Complète

Créez une composition visuelle qui utilise:
1. Au moins 2 sources différentes (Générative et Externe)
2. Des transformations géométriques (rotation, scale, kaleid, etc.)
3. Des modifications de couleur
4. Du blending entre sources
5. De la modulation pour créer des effets complexes
6. Des variables temporelles ou interactives

### Exemple de composition complexe:
```javascript
// Source 1: Oscillateur modulé
osc(20, 0.1, 1)
  .rotate(0.2, 0.1)
  .kaleid(4)
  .color(1, 0.5, 0.8)
  .modulate(noise(3), 0.3)
  
// Source 2: Formes répétées
.blend(
  shape(4, 0.3)
    .repeat(3, 3)
    .modulateScale(osc(8), 0.5)
  , 0.5)
  
.out(o0)
```

---


## Ressources

- Documentation officielle: [hydra.ojack.xyz](https://hydra.ojack.xyz)
- Exemples: Appuyez sur les flèches dans l'éditeur Hydra
- Communauté: [Discord Hydra](https://discord.gg/hydra)

