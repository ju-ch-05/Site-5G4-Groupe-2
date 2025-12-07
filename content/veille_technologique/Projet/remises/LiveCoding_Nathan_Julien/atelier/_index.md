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

## 8. BONUS - Créer ses Propres Fonctions Personnalisées

Hydra utilise GLSL (un langage qui s'exécute directement sur la carte graphique) pour générer ses visuels. Chaque fonction JavaScript en Hydra correspond à un fragment de code GLSL. La magie, c'est que **vous pouvez créer vos propres fonctions** avec `setFunction()` !

### Pourquoi créer ses fonctions ?

- Réutiliser des effets complexes
- Créer des outils uniques et personnalisés
- Combiner plusieurs transformations en une seule
- Partager vos créations avec la communauté

### Anatomie de setFunction()

```javascript
setFunction({
  name: 'nomDeLaFonction',    // Nom que vous utiliserez dans Hydra
  type: 'src',                 // Type de fonction (voir ci-dessous)
  inputs: [                    // Paramètres de votre fonction
    { 
      name: 'speed',           // Nom du paramètre
      type: 'float',           // Type (float, vec2, vec3, vec4)
      default: 1.0             // Valeur par défaut
    }
  ],
  glsl: `                      // Code GLSL
    // Votre code ici
    return vec4(st.x, st.y, 0.0, 1.0);
  `
})

// Utilisation immédiate après définition :
nomDeLaFonction(2.0).out()
```

### Les 5 Types de Fonctions

Hydra utilise 5 types de fonctions qui correspondent à différentes étapes du pipeline graphique :

#### 1. **src** - Génère des visuels
Crée une nouvelle source visuelle à partir de rien.
- **Reçoit :** `vec2 _st` (coordonnées x,y de 0.0 à 1.0)
- **Retourne :** `vec4` (couleur RGBA)
- **Exemples Hydra :** `osc()`, `noise()`, `shape()`, `gradient()`

```javascript
// Cercles concentriques personnalisés
setFunction({
  name: 'circles',
  type: 'src',
  inputs: [
    { name: 'count', type: 'float', default: 5.0 },
    { name: 'thickness', type: 'float', default: 0.1 }
  ],
  glsl: `
    vec2 center = vec2(0.5, 0.5);
    float dist = distance(_st, center);
    float pattern = mod(dist * count, 1.0);
    float circles = smoothstep(thickness, thickness + 0.01, pattern);
    return vec4(vec3(circles), 1.0);
  `
})

// Utilisation comme n'importe quelle source
circles(10, 0.05).out()
circles(20, 0.02).color(1, 0.5, 0).out()
```

#### 2. **coord** - Transforme l'espace
Déforme les coordonnées avant d'appliquer la texture.
- **Reçoit :** `vec2 _st` (coordonnées)
- **Retourne :** `vec2` (nouvelles coordonnées)
- **Exemples Hydra :** `rotate()`, `scale()`, `pixelate()`, `kaleid()`

```javascript
// Coordonnées polaires
setFunction({
  name: 'polar',
  type: 'coord',
  inputs: [
    { name: 'zoom', type: 'float', default: 1.0 }
  ],
  glsl: `
    vec2 centered = _st - 0.5;
    float radius = length(centered) * zoom;
    float angle = atan(centered.y, centered.x);
    return vec2(radius, angle);
  `
})

// Utilisation : transforme n'importe quelle source
osc(10).polar(2.0).out()
gradient().polar(0.5).out()
```

#### 3. **color** - Modifie les couleurs
Transforme les couleurs d'une texture existante.
- **Reçoit :** `vec4 _c0` (couleur actuelle)
- **Retourne :** `vec4` (nouvelle couleur)
- **Exemples Hydra :** `invert()`, `contrast()`, `hue()`, `saturate()`

```javascript
// Filtre duotone (2 couleurs)
setFunction({
  name: 'duotone',
  type: 'color',
  inputs: [
    { name: 'hue1', type: 'float', default: 0.0 },
    { name: 'hue2', type: 'float', default: 0.5 }
  ],
  glsl: `
    // Calcul de la luminance
    float lum = (_c0.r + _c0.g + _c0.b) / 3.0;
    
    // Créer deux couleurs depuis les teintes
    vec3 color1 = vec3(
      cos(hue1 * 6.28), 
      sin(hue1 * 6.28), 
      0.5
    ) * 0.5 + 0.5;
    
    vec3 color2 = vec3(
      cos(hue2 * 6.28), 
      sin(hue2 * 6.28), 
      0.5
    ) * 0.5 + 0.5;
    
    // Mélanger selon la luminance
    vec3 result = mix(color1, color2, lum);
    return vec4(result, _c0.a);
  `
})

// Utilisation : s'applique après une source
noise(5).duotone(0.1, 0.6).out()
osc(20).duotone(0.8, 0.3).out()
```

#### 4. **combine** - Mélange deux textures
Combine deux sources visuelles ensemble.
- **Reçoit :** `vec4 _c0` (texture 1), `vec4 _c1` (texture 2)
- **Retourne :** `vec4` (couleur mélangée)
- **Exemples Hydra :** `add()`, `mult()`, `blend()`, `diff()`

```javascript
// Mélange en damier
setFunction({
  name: 'checkerBlend',
  type: 'combine',
  inputs: [
    { name: 'size', type: 'float', default: 10.0 }
  ],
  glsl: `
    float checker = mod(
      floor(_st.x * size) + floor(_st.y * size), 
      2.0
    );
    return mix(_c0, _c1, checker);
  `
})

// Utilisation : combine deux chaînes
osc(20).checkerBlend(noise(5), 15).out()
gradient().checkerBlend(shape(4), 8).out()
```

#### 5. **combineCoord** - Modulation spatiale
Utilise une texture pour déformer les coordonnées d'une autre.
- **Reçoit :** `vec2 _st` (coordonnées), `vec4 _c0` (texture modulante)
- **Retourne :** `vec2` (coordonnées déformées)
- **Exemples Hydra :** `modulate()`, `modulateScale()`, `modulateRotate()`

```javascript
// Distorsion personnalisée
setFunction({
  name: 'ripple',
  type: 'combineCoord',
  inputs: [
    { name: 'amount', type: 'float', default: 0.1 }
  ],
  glsl: `
    // Utiliser la luminance de c0 pour déformer
    float distortion = (_c0.r + _c0.g + _c0.b) / 3.0;
    _st.x += sin(_st.y * 10.0 + time) * distortion * amount;
    _st.y += cos(_st.x * 10.0 + time) * distortion * amount;
    return _st;
  `
})

// Utilisation : modulation avec une deuxième source
shape(4).ripple(noise(3), 0.3).out()
osc(10).ripple(gradient(), 0.5).out()
```

### Comment Utiliser vos Fonctions

Une fois définies avec `setFunction()`, vos fonctions personnalisées s'utilisent **exactement comme les fonctions Hydra natives** :

```javascript
// 1. Définir la fonction (une seule fois)
setFunction({
  name: 'myEffect',
  type: 'color',
  inputs: [{ name: 'intensity', type: 'float', default: 1.0 }],
  glsl: `return vec4(_c0.rgb * intensity, _c0.a);`
})

// 2. L'utiliser dans vos chaînes Hydra
osc(10).myEffect(2.0).out()
noise(5).myEffect(0.5).color(1, 0, 0).out()

// 3. Chaîner avec d'autres fonctions
shape(4)
  .myEffect(1.5)
  .rotate(0.5)
  .kaleid(6)
  .out()
```

**Ordre d'utilisation selon le type :**

```javascript
// TYPE 'src' : Début de chaîne (génère le visuel)
mySource(param1).rotate(0.5).out()

// TYPE 'coord' : Après une source (transforme l'espace)
osc(10).myCoord(param1).scale(2).out()

// TYPE 'color' : Après une source (modifie les couleurs)
noise(5).rotate(0.2).myColor(param1).out()

// TYPE 'combine' : Prend deux sources (mélange)
gradient().myCombine(shape(4), param1).out()

// TYPE 'combineCoord' : Modulation avec texture
shape(6).myCombineCoord(noise(3), param1).out()
```

### Exemples Avancés Prêts à l'Emploi

#### Grille de Points Animée
```javascript
setFunction({
  name: 'dots',
  type: 'src',
  inputs: [
    { name: 'size', type: 'float', default: 20.0 },
    { name: 'radius', type: 'float', default: 0.3 }
  ],
  glsl: `
    vec2 grid = fract(_st * size);
    vec2 center = vec2(0.5, 0.5);
    float dist = distance(grid, center);
    float dot = 1.0 - smoothstep(radius - 0.05, radius, dist);
    return vec4(vec3(dot), 1.0);
  `
})

dots(15, 0.2).color(1, 0.5, 0.8).out()
dots(20, ()=> Math.sin(time)*0.3+0.3).out()
```

#### Effet Tunnel Spatial
```javascript
setFunction({
  name: 'tunnel',
  type: 'coord',
  inputs: [
    { name: 'zoom', type: 'float', default: 2.0 },
    { name: 'twist', type: 'float', default: 1.0 }
  ],
  glsl: `
    vec2 centered = _st - 0.5;
    float r = length(centered);
    float angle = atan(centered.y, centered.x);
    
    r = zoom / r;  // Effet de profondeur
    angle += twist * r + time;  // Rotation progressive
    
    _st = vec2(r * cos(angle), r * sin(angle));
    return _st;
  `
})

osc(10, 0.1).tunnel(3, 0.5).out()
gradient().tunnel(2, 1).out()
```

#### Séparation RGB (Chromatic Aberration)
```javascript
setFunction({
  name: 'rgbSplit',
  type: 'color',
  inputs: [
    { name: 'amount', type: 'float', default: 0.02 }
  ],
  glsl: `
    vec2 offset = vec2(amount, 0.0);
    float r = texture2D(tex0, _st + offset).r;
    float g = _c0.g;
    float b = texture2D(tex0, _st - offset).b;
    return vec4(r, g, b, _c0.a);
  `
})

shape(4).repeat(3, 3).rgbSplit(0.05).out()
osc(20).kaleid(6).rgbSplit(()=> Math.sin(time)*0.03).out()
```

#### Effet Glitch Dynamique
```javascript
setFunction({
  name: 'glitch',
  type: 'color',
  inputs: [
    { name: 'amount', type: 'float', default: 0.5 }
  ],
  glsl: `
    // Ligne de glitch aléatoire
    float glitchLine = step(0.98, fract(_st.y * 20.0 + time * 5.0));
    vec4 offset = _c0;
    
    if(glitchLine > 0.0) {
      offset.r = texture2D(tex0, _st + vec2(amount * 0.1, 0.0)).r;
      offset.b = texture2D(tex0, _st - vec2(amount * 0.1, 0.0)).b;
    }
    
    return mix(_c0, offset, glitchLine);
  `
})

osc(20, 0.1, 1).glitch(0.8).out()
```

#### Effet Cristal/Facettes
```javascript
setFunction({
  name: 'crystal',
  type: 'coord',
  inputs: [
    { name: 'facets', type: 'float', default: 6.0 },
    { name: 'amount', type: 'float', default: 0.5 }
  ],
  glsl: `
    vec2 centered = _st - 0.5;
    float angle = atan(centered.y, centered.x);
    float radius = length(centered);
    
    // Créer des facettes angulaires
    float segment = 6.28318 / facets;
    angle = floor(angle / segment) * segment + segment * 0.5;
    
    _st = vec2(cos(angle), sin(angle)) * radius * amount + 0.5;
    return _st;
  `
})

gradient().crystal(8, 0.8).out()
noise(3).crystal(12, 1.2).colorama(0.5).out()
```

### Exercice BONUS
Créez votre propre fonction personnalisée qui combine au moins 2 transformations.

**Exemple de défi :**
```javascript
// Créez une fonction "neon" qui:
// 1. Détecte les contours
// 2. Ajoute une lueur colorée
// 3. Assombrit le fond

setFunction({
  name: 'neon',
  type: 'color',
  inputs: [
    { name: 'intensity', type: 'float', default: 2.0 },
    { name: 'glowColor', type: 'float', default: 0.5 }
  ],
  glsl: `
    // Détection de contours simple
    vec2 texelSize = vec2(1.0/1280.0, 1.0/720.0);
    float edge = 0.0;
    
    edge += length(texture2D(tex0, st + vec2(texelSize.x, 0.0)).rgb - c0.rgb);
    edge += length(texture2D(tex0, st - vec2(texelSize.x, 0.0)).rgb - c0.rgb);
    edge += length(texture2D(tex0, st + vec2(0.0, texelSize.y)).rgb - c0.rgb);
    edge += length(texture2D(tex0, st - vec2(0.0, texelSize.y)).rgb - c0.rgb);
    
    edge = smoothstep(0.0, 1.0, edge * intensity);
    
    // Couleur néon
    vec3 neonColor = vec3(
      cos(glowColor * 6.28) * 0.5 + 0.5,
      sin(glowColor * 6.28) * 0.5 + 0.5,
      1.0
    );
    
    // Mélange
    vec3 result = mix(c0.rgb * 0.2, neonColor, edge);
    return vec4(result, c0.a);
  `
})

// Test de la fonction neon
osc(20, 0.1)
  .kaleid(4)
  .neon(3.0, 0.3)
  .out()
```

### Variables GLSL Disponibles

Selon le type de fonction, différentes variables sont automatiquement disponibles :

```glsl
// DANS TOUTES LES FONCTIONS :
time         // float : temps écoulé en secondes
resolution   // vec2 : largeur et hauteur de l'écran

// SPÉCIFIQUES AU TYPE :
_st          // vec2 : coordonnées (x, y) de 0.0 à 1.0 [src, coord, combineCoord]
_c0          // vec4 : couleur de la texture actuelle [color, combine, combineCoord]
_c1          // vec4 : couleur de la 2ème texture [combine uniquement]
```

**Note importante :** Utilisez `_st` avec underscore (pas `st` seul) pour éviter des bugs !

### Fonctions GLSL Utilitaires Pré-définies

Hydra inclut des fonctions utiles que vous pouvez utiliser dans votre code GLSL :

```glsl
// Calculer la luminance d'une couleur RGB
float lum = _luminance(_c0.rgb);

// Convertir RGB vers HSV
vec3 hsv = _rgbToHsv(_c0.rgb);

// Convertir HSV vers RGB
vec3 rgb = _hsvToRgb(vec3(0.5, 1.0, 1.0));
```

### Astuces GLSL Essentielles

```glsl
// Distance entre deux points
float d = distance(_st, vec2(0.5, 0.5));

// Angle depuis le centre (coordonnées polaires)
vec2 centered = _st - 0.5;
float angle = atan(centered.y, centered.x);
float radius = length(centered);

// Répétition de coordonnées (tiling)
vec2 repeated = fract(_st * 5.0);  // Répète 5x5 fois

// Transition douce entre deux valeurs
float smooth = smoothstep(0.0, 1.0, value);

// Mélange linéaire entre deux valeurs/couleurs
float mixed = mix(valeur1, valeur2, 0.5);  // 50% de chaque
vec3 color = mix(color1, color2, amount);

// Modulo (pour créer des patterns répétés)
float pattern = mod(_st.x * 10.0, 1.0);

// Seuil binaire (0 ou 1)
float binary = step(0.5, value);  // 0 si value < 0.5, sinon 1

// Limiter une valeur entre min et max
float clamped = clamp(value, 0.0, 1.0);

// Arrondir
float rounded = floor(value);  // Arrondi inférieur
float ceiled = ceil(value);    // Arrondi supérieur
```

### Sauvegarde et Partage de vos Fonctions

#### Méthode 1 : Fichier JavaScript Externe

```javascript
// Créez un fichier "myHydraFunctions.js"
setFunction({
  name: 'dots',
  type: 'src',
  // ... votre fonction
})

setFunction({
  name: 'tunnel',
  type: 'coord',
  // ... votre fonction
})

// Dans Hydra, chargez vos fonctions :
await loadScript("chemin/vers/myHydraFunctions.js")

// Maintenant utilisez-les :
dots(20).tunnel(2).out()
```

#### Méthode 2 : Copier-Coller au Début

```javascript
// En haut de votre sketch Hydra, définissez toutes vos fonctions
setFunction({ name: 'dots', type: 'src', /* ... */ })
setFunction({ name: 'tunnel', type: 'coord', /* ... */ })
setFunction({ name: 'neon', type: 'color', /* ... */ })

// Puis utilisez-les dans votre code
dots(15)
  .tunnel(2, 0.5)
  .neon(3, 0.3)
  .out()
```

#### Méthode 3 : Extensions Hydra

Il existe des collections de fonctions custom prêtes à l'emploi :

```javascript
// Extra Shaders for Hydra (nombreux effets)
// https://gitlab.com/metagrowing/extra-shaders-for-hydra

// Hydra Blending Modes (modes de mélange avancés)
// https://github.com/ritchse/hydra-extensions
```

### Aller Plus Loin

**Extensions recommandées :**
- `hydra-glsl` : Écrire du GLSL directement dans vos patches
- `extra-shaders-for-hydra` : Collection d'effets prêts à l'emploi
- `hydra-blending-modes` : Modes de mélange Photoshop-like

**Ressources pour apprendre GLSL :**
- [The Book of Shaders](https://thebookofshaders.com/) - Tutorial GLSL interactif
- [Shadertoy](https://www.shadertoy.com/) - Plateforme de shaders GLSL
- [GLSL Functions Reference](https://www.khronos.org/opengl/wiki/OpenGL_Shading_Language) - Documentation officielle


---

## Ressources

- Documentation officielle: [hydra.ojack.xyz](https://hydra.ojack.xyz)
- Exemples: Appuyez sur les flèches dans l'éditeur Hydra
- Communauté: [Discord Hydra](https://discord.gg/hydra)

