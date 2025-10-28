# EA113 – Conception d’un amplificateur audio

Projet réalisé dans le cadre du module **EA113 – Électronique analogique** en première année du département **Électronique** à l’**ENSEIRB-MATMECA**.

**Auteurs :**  
Mattéo BINET  
Alexandre BROMET  

**Professeur :**  
Jean-Michel VINASSA

**Date :** Avril 2025  

---

## 1. Introduction

Le projet d’électronique analogique EA113 a pour objectif la **conception et la réalisation d’un amplificateur audiofréquence de puissance**.  
Ce projet s’inscrit dans la continuité du module **EA108**, consacré aux fondamentaux des circuits électroniques.

L’objectif principal est de **mettre en pratique les connaissances théoriques** acquises pour concevoir un amplificateur audio répondant à des **spécifications précises**, tout en respectant les **contraintes d’alimentation, de bande passante et d’impédance**.

Le projet comprend plusieurs étapes : conception théorique, simulation, réalisation sur PCB et tests expérimentaux.  
Les simulations ont été réalisées à l’aide du logiciel **Proteus**, permettant de valider le comportement du circuit avant sa mise en œuvre physique.

---

## 2. Cahier des charges

- **Charge :** Haut-parleur de 8 Ω (remplacé par une résistance lors de l’étude)  
- **Tension d’entrée :** 100 mV_eff_ (niveau typique d’une sortie audio)  
- **Bande passante :** 40 Hz à 15 kHz  
- **Entrée :** Couplage par un passe-haut pour supprimer la composante continue  
- **Impédance d’entrée :** 47 kΩ  
- **Alimentation :** ±15 V  

---

## 3. Conception du circuit

Le circuit se compose de **deux étages principaux** :

1. **Premier étage :**  
   - Filtre passe-haut (R3, C3) pour supprimer la composante continue.  
   - Amplificateur opérationnel TL071 configuré en montage non inverseur.  
   - Gain en tension :  
     \\[ A_v = 1 + \\frac{R_2}{R_1} \\approx 100 \\]  
   - Résistances normalisées : R₁ = 1 kΩ, R₂ = 100 kΩ.

2. **Deuxième étage :**  
   - Étape de puissance en **push-pull complémentaire** à base de MOSFET (IRLIZ34N et IRLIB9343).  
   - Compensation de la **distorsion de croisement** par ajout de diodes et d’une diode Zener.  
   - Amélioration de la linéarité de la caractéristique de transfert.

Des **condensateurs de découplage** ont été ajoutés aux alimentations afin de limiter les perturbations et pertes inductives.  
Des **dissipateurs thermiques** sont fixés sur les transistors MOSFET pour garantir une dissipation thermique adéquate.

---

## 4. Simulation

Les simulations sous Proteus ont permis de vérifier :

- La **caractéristique de transfert** Vout(Vin) conforme au modèle théorique.  
- La **réduction de la distorsion de croisement** grâce aux diodes de polarisation.  
- Une **bande passante** conforme au cahier des charges.  
- Une **amplification correcte** sans saturation pour un signal sinusoïdal de 1 kHz.

---

## 5. Réalisation du circuit imprimé (PCB)

### 5.1 Conception du layout
- Réalisée sous **Proteus** à partir du schéma électrique.  
- Placement optimisé pour minimiser la longueur des pistes et les interférences.  
- Largeurs de pistes adaptées à l’intensité (5 A/mm²), avec T80 pour les alimentations et la masse.

### 5.2 Fabrication du PCB
- **Procédé utilisé :** gravure chimique au perchlorure de fer sur plaque FR4 photosensible.  
- **Étapes :** impression des typons, insolation UV, révélation, gravure, perçage et nettoyage.

### 5.3 Soudure des composants
- Montage manuel en commençant par les composants les plus fins.  
- Vérification systématique des soudures et des continuités électriques.

### 5.4 Vérification et tests
- Contrôle d’absence de courts-circuits avant mise sous tension.  
- Tests de continuité et de fonctionnement à vide.  
- Validation par mesure des tensions et signaux à l’oscilloscope.

---

## 6. Tests expérimentaux

- **Phase de test initiale :** vérification sans charge pour détecter d’éventuels défauts de câblage.  
- **Mesures en charge :** observation des tensions de sortie sous signal sinusoïdal.  
- **Validation qualitative :** écoute sur haut-parleur via signal audio d’un téléphone.

Le comportement du montage est conforme aux attentes, avec un **signal de sortie stable et amplifié** et **une restitution sonore satisfaisante**.

---

## 7. Résultats

| Paramètre | Valeur théorique | Valeur mesurée |
|------------|------------------|----------------|
| Gain en tension | 40 dB | ≈ 39 dB |
| Bande passante | 40 Hz – 15 kHz | Conforme |
| Impédance d’entrée | 47 kΩ | Conforme |
| Rendement du push-pull | ≈ 47 % | ≈ 44 % |
| Tension d’alim. | ±15 V | ±15 V |

Le circuit final présente une **bonne linéarité** et un **fonctionnement stable**, avec une **distorsion minimale** après correction par diodes.

---

## 8. Conclusion

Ce projet EA113 a permis de concevoir, simuler et réaliser un amplificateur audio répondant à un cahier des charges strict.  
L’ensemble des étapes – de la conception à la validation expérimentale – a permis de relier les aspects théoriques étudiés en cours à une mise en œuvre concrète.

Le travail a également permis d’aborder des notions clés telles que la **stabilité d’un montage analogique**, la **distorsion**, la **dissipation thermique** et la **fabrication de circuits imprimés**.

---

## 9. Contenu du dépôt GitHub

Le dépôt [EA113_-_Conception_dun_amplificateur_audio](https://github.com/matteob29/EA113_-_Conception_dun_amplificateur_audio) contient les éléments suivants :
