# 🎮 Taquin - Puzzle Game

Un jeu de Taquin (15-puzzle) classique développé en **C++** avec **Qt Framework**, offrant une interface graphique intuitive et le support multilingue.

## 📋 Table des matières

- [Caractéristiques](#-caractéristiques)
- [Prérequis](#-prérequis)
- [Installation](#-installation)
- [Utilisation](#-utilisation)
- [Structure du projet](#-structure-du-projet)
- [Commandes clés](#-commandes-clés)
- [Développement](#-développement)
- [Améliorations futures](#-améliorations-futures)
- [Contribution](#-contribution)

---

## 🎯 Caractéristiques

✅ **Jeu du Taquin classique** - Puzzle à 9 tuiles (grille 3×3)  
✅ **Interface graphique** - Interface moderne avec Qt Widgets  
✅ **Multilingue** - Support français et anglais avec détection automatique  
✅ **Sauvegarde/Chargement** - Sauvegardez votre partie et reprenez plus tard  
✅ **Compteur de coups** - Suivez le nombre de mouvements  
✅ **Thèmes personnalisés** - Plusieurs images de fond disponibles  
✅ **Raccourcis clavier** - Accès rapide aux fonctionnalités principales  

---

## 🛠️ Prérequis

Avant de compiler le projet, vous devez installer :

| Composant | Version | Description |
|-----------|---------|-------------|
| **C++** | 17 ou supérieur | Langage de programmation |
| **CMake** | 3.5+ | Système de build |
| **Qt Framework** | 5.15+ ou 6.0+ | Framework GUI |
| **Qt Creator** | 6.0+ | IDE recommandé (optionnel) |

### Installation des dépendances

#### Sur Ubuntu/Debian :
```bash
sudo apt-get update
sudo apt-get install build-essential cmake qt5-qmake qt5-default qtbase5-dev
# ou pour Qt6
sudo apt-get install build-essential cmake qt6-base-dev
```

#### Sur macOS (avec Homebrew) :
```bash
brew install cmake qt
```

#### Sur Windows :
- Téléchargez Qt depuis [qt.io](https://www.qt.io/download)
- Installez Qt Creator et Qt Framework (version 5 ou 6)

---

## 📥 Installation

### 1. Cloner le repository
```bash
git clone https://github.com/gihamos/projet.git
cd projet/projet_diga
```

### 2. Compiler avec CMake

#### Avec Qt Creator (recommandé) :
1. Ouvrez Qt Creator
2. Ouvrez le fichier `CMakeLists.txt` du dossier `projet_diga`
3. Configurez le kit (compiler et Qt version)
4. Cliquez sur **Build** (ou `Ctrl+B`)

#### Depuis la ligne de commande :
```bash
mkdir build
cd build
cmake ..
make
```

### 3. Lancer l'application
```bash
./projet_diga
```

---

## 🎮 Utilisation

### Commandes principales

| Action | Raccourci | Description |
|--------|-----------|-------------|
| **Nouvelle partie** | `Ctrl+N` | Démarre une nouvelle partie |
| **Sauvegarder** | `Ctrl+S` | Sauvegarde la partie en cours |
| **Charger** | `Ctrl+O` | Charge une partie sauvegardée |
| **Quitter** | `Ctrl+Q` | Ferme l'application |

### Jouer

1. **Cliquez sur une tuile** adjacente à l'espace vide pour la déplacer
2. **Réorganisez** toutes les tuiles dans l'ordre numérique (1-8 avec l'espace vide à la fin)
3. **Gagnez** quand toutes les tuiles sont dans le bon ordre
4. Le **compteur de coups** affiche votre nombre de mouvements

### Thèmes disponibles

Sélectionnez une image de fond dans le menu pour personnaliser votre jeu :
- 🌳 Arbre
- 🕸️ Réseau
- 🏢 Organisation
- 🌲 Forêt

---

## 📂 Structure du projet

```
projet_diga/
├── CMakeLists.txt                    # Configuration de build
├── main.cpp                          # Point d'entrée de l'application
├── mainwindow.h / mainwindow.cpp     # Fenêtre principale et logique du jeu
├── mainwindow.ui                     # Interface graphique (Qt Designer)
├── saisietaille.h / saisietaille.cpp # Dialog de saisie de la taille
├── saisietaille.ui                   # Interface du dialog
├── ressource.qrc                     # Fichiers ressources (images, icônes)
├── projet_diga_fr_FR.ts              # Traductions français
└── projet_diga_en_US.ts              # Traductions anglais
```

### Composants clés

**MainWindow** : Contrôle central du jeu
- Gestion de la grille de tuiles (3×3 par défaut)
- Détection des mouvements valides
- Logique de victoire
- Sauvegarde/chargement des parties en fichier

**Saisie de Taille** : Dialog pour configurer la partie
- Permet de choisir les paramètres du puzzle

**Traductions** : Support multilingue automatique
- Détecte la langue du système
- Fichiers .ts pour localisation

**Ressources** : Fichier qrc contenant
- Icônes de l'application
- Images de thème

---

## 💻 Développement

### Architecture du code

#### Fonctions principales (mainwindow.cpp)

```cpp
void MainWindow::generermatricejeux();      // Génère un puzzle aléatoire
bool MainWindow::partiegagner() const;       // Vérifie si le puzzle est résolu
void MainWindow::move();                      // Gère un clic sur une tuile
void MainWindow::sauver_partie();            // Sauvegarde l'état du jeu
void MainWindow::charger_partie();           // Récupère une sauvegarde
void MainWindow::trietuiles();              // Organise les tuiles en grille
```

#### Flux du jeu

1. **Initialisation** : MainWindow crée une grille 3×3 avec 8 tuiles numérotées
2. **Génération** : `generermatricejeux()` crée un puzzle aléatoire
3. **Interaction** : L'utilisateur clique sur les tuiles, `move()` valide le mouvement
4. **Vérification** : `partiegagner()` détecte quand le puzzle est résolu
5. **Sauvegarde** : État du jeu peut être sauvegardé/chargé

### Ajouter une nouvelle fonctionnalité

1. **Modifiez le fichier .ui** dans Qt Designer (accessible depuis Qt Creator)
2. **Implémentez la logique** dans `mainwindow.cpp`
3. **Déclarez les slots/signaux** dans `mainwindow.h`
4. **Compilez** avec `cmake .. && make`
5. **Testez** la nouvelle fonctionnalité

### Ajouter une traduction

1. Mettez à jour les fichiers `.ts` (Linguist)
2. Exécutez : `lupdate` pour extraire les textes
3. Compilez avec `lrelease` pour générer les fichiers `.qm`

---

## 🚀 Améliorations futures

- [ ] Grilles de tailles variables (4×4, 5×5, etc.)
- [ ] Système de score et classement
- [ ] Mode chronométré
- [ ] Animation fluide des déplacements
- [ ] Fonction Undo/Redo
- [ ] Statistiques de jeu
- [ ] Thèmes supplémentaires
- [ ] Son et effets sonores

---

## 🤝 Contribution

Les contributions sont bienvenues ! Pour contribuer :

1. Fork le projet
2. Créez une branche (`git checkout -b feature/AmazingFeature`)
3. Commitez vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Pushez vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

---

## 📝 Licence

Ce projet est librement utilisable à des fins éducatives.

---

## 🆘 Support & Aide

- 📖 [Documentation Qt](https://doc.qt.io/)
- 🐛 Signalez les bugs via les [Issues](https://github.com/gihamos/projet/issues)
- 💬 Posez des questions dans les [Discussions](https://github.com/gihamos/projet/discussions)

---

## 👤 À propos

Développé comme projet d'étude pour le cours de programmation C++/Qt en Licence 3 Informatique.

**Auteur** : [@gihamos](https://github.com/gihamos)  
**Dernière mise à jour** : Avril 2026
