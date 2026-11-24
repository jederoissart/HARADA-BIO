# HARADA-BIO (v6.0)

Application web autonome (*single-file*, **100 % locale**) dédiée au suivi physiologique, à la programmation sportive et au pilotage d'objectifs par la **méthode Harada**.

Conçue pour fonctionner sans serveur, sans compte utilisateur et sans base de données distante : tout tourne directement dans le navigateur.

---

## Confidentialité & Architecture *Local-First*

* **Zéro cloud, zéro tracking :** Ce dépôt contient uniquement le code source neutre de l'application.
* **Données 100 % locales :** Chaque utilisateur stocke son profil, ses séances et sa grille dans le `localStorage` de son propre appareil. Personne (pas même l'auteur du dépôt) n'a accès aux données saisies par un autre utilisateur.
* **Portabilité totale :** Export et import complet de l'historique en un clic via fichier `.json` (sauvegarde manuelle ou transfert PC ↔ téléphone).

---

## Démarrage rapide

1. Ouvre l'application via le lien **GitHub Pages** du dépôt (ou télécharge simplement `index.html` et ouvre-le dans ton navigateur).
2. Au premier lancement, l'**assistant d'accueil (4 étapes)** te permet de configurer :
   * **Profil & biométrie** (mode complet avec fréquence cardiaque ou mode simplifié sans FC, ou import direct d'un `.json` existant).
   * **Thème visuel** parmi 5 palettes : *Cyber Cyan*, *Tactique Olive*, *Obsidienne & Or*, *Clair Minimaliste* et **Nuit Rouge** (monochrome rouge pur sans canal bleu ni vert).
   * **Modèle sportif** : *Calisthénie & Lest*, *Musculation Fonte*, *Endurance & Sports Collectifs* ou *Vierge*.
   * **Objectif & Grille Harada** : *Équilibre Global*, *Performance Athlétique* ou *Vierge* (avec générateur de prompt IA intégré pour bâtir ta propre grille en 1 minute).

> **Astuce mobile :** Depuis le navigateur de ton téléphone, utilise *« Ajouter à l'écran d'accueil »* pour accéder à l'outil comme une application dédiée. Pense à exporter ton fichier `.json` régulièrement pour ne jamais perdre ton historique en cas de vidage de cache.

---

## Fonctionnalités principales

### Suivi quotidien (`Jour`)
* **Sommeil & Récupération :** Saisie du coucher/lever (sommeil continu + éveils nocturnes, latence d'endormissement `SOL`, `WASO`, sieste), fréquence cardiaque au coucher et au réveil, *dipping* nocturne et indice de récupération.
* **Sport modulaire :** Suivi RPT avec micro-surcharges, suivi unilatéral D/G (alerte d'asymétrie), pyramides, EMOM et RPE.
* **Interrupteur `⚡ Express 20'` :** Réduit automatiquement les blocs RPT de 3 à 2 séries en conservant **100 % de la charge** pour préserver les acquis de force les jours contraints⁵.
* **Rituels & Complémentation :** Suivi des habitudes journalières.

### Matrice Harada & Archives (`Harada`)
* **Grille complète :** 1 objectif central, 8 piliers, 64 actions et 192 sous-actions personnalisables.
* **Archives mensuelles & Radar comparatif :** Sauvegarde d'instantanés mensuels avec superposition graphique ($M$ vs $M-1$) et deltas par pilier.
* **Simulateur temporel :** Test visuel de l'érosion des acquis sans modifier la date réelle.

### Analyses & Outils (`Courbes`, `Prog`, `Données`)
* **Modélisation de charge :** Courbes de forme/fatigue, suivi de l'équilibre musculaire et calcul des charges biomécaniques ($M_0$).
* **Mode Nuit Rouge :** Bascule instantanée de l'interface et des graphiques en monochrome rouge sombre pour éviter l'exposition à la lumière bleue le soir.
* **Fiche papier A5 imprimable :** Génération d'une feuille hebdomadaire prête à imprimer au format A5 (charges de la semaine + cases vierges FC/sommeil pour un suivi matinal sans écran).

---

## Fondements mathématiques & scientifiques

Pour éviter l'effet de progression artificielle rapide, la matrice Harada et le module sportif reposent sur des modèles quantitatifs issus de la littérature :

* **Saturation par courbe de Hill ($\gamma = 1,5$) :** Inspirée des modèles d'entraînement à effet de seuil¹, la progression présente une forte inertie initiale et exige **au minimum 5 mois pleins ($\ge 150$ unités)** pour atteindre 100 % sur les routines quotidiennes.
* **Décroissance temporelle ($\Delta t$) selon 3 moteurs :**
  * `Lally` (habitudes) : tolérance de 2 jours sans perte, puis érosion exponentielle douce ($u_{\text{eff}} = u \cdot e^{-(\Delta t - 2)/45}$)².
  * `Physique` (force / conditionnement) : fenêtre de récupération protégée jusqu'à 72 h, puis désentraînement selon la constante de temps $\tau_1 = 21,5\text{ j}$³.
  * `ACT-R` (compétences / apprentissage) : bonus d'espacement optimal (+25 %) entre 2 et 7 jours, puis déclin mnésique en loi de puissance⁴.
* **Maintien de la force sous volume réduit :** Le mode *Express 20'* applique le principe de dose minimale efficace : réduire le volume de 33 % à 60 % tout en maintenant l'intensité maximale préserve les performances de force⁵, ⁶.

---

## Feuille de route (Évolutions en cours de réflexion)

* [ ] **Passage en PWA complète** (`manifest.json` + *Service Worker*) pour un fonctionnement 100 % hors-ligne garanti.
* [ ] **Couplage automatique `Jour` ↔ `Harada`** pour supprimer la double saisie.
* [ ] **Module Second Cerveau / Drill & RETEX** : rappel actif sous chrono couplé au moteur `ACT-R` et journal de retours d'expérience ultra-courts.
* [ ] **Portage Android natif (APK)** avec raccourci / widget sans déverrouillage sur écran verrouillé pour capture éclair.

---

## Références scientifiques

* **¹ Hellard, P., Avalos, M., Millet, G., Lacoste, L., Barale, F., & Chatard, J. C.** (2005). *Modeling the residual effects and threshold saturation of training: a case study of Olympic swimmers.* Journal of Strength and Conditioning Research, 19(1), 67-75.
* **² Lally, P., van Jaarsveld, C. H. M., Potts, H. W. W., & Wardle, J.** (2010). *How are habits formed: Modelling habit formation in the real world.* European Journal of Social Psychology, 40(6), 998-1009.
* **³ Bouzigues, T.** (2024). *Modélisation des effets de l'entraînement sur les performances et les blessures : effets du niveau de jeu, de l'âge et du genre.* Thèse de doctorat en Sciences du Sport, ENS de Rennes / Université Rennes 2.
* **⁴ Pavlik, P. I., Jr., & Anderson, J. R.** (2008). *Using a model to compute the optimal schedule of practice.* Journal of Experimental Psychology: Applied, 14(2), 101-117.
* **⁵ Spiering, B. A., Mujika, I., Sharp, M. A., & Foulis, S. A.** (2021). *Maintaining Physical Performance: The Minimal Dose of Exercise Needed to Preserve Endurance and Strength Over Time.* Journal of Strength and Conditioning Research, 35(5), 1449-1458.
* **⁶ Bosquet, L., Montpetit, J., Arvisais, D., & Mujika, I.** (2007). *Effects of tapering on performance: a meta-analysis.* Medicine & Science in Sports & Exercise, 39(8), 1358-1365.
