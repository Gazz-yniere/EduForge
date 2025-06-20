# Apprentium 

## Description
Apprentium est une application de bureau développée en Python avec une interface graphique conviviale (basée sur PyQt6). Elle est conçue pour aider à la création de cahiers d'exercices personnalisés pour les élèves, couvrant un large éventail de matières. L'application permet de générer ces fiches d'exercices aux formats PDF et Word.

Les utilisateurs peuvent finement ajuster les paramètres de chaque type d'exercice (nombre d'items, difficulté, options spécifiques) directement depuis l'interface. Ces configurations sont automatiquement sauvegardées dans un fichier `config.json` pour une réutilisation facile. Le contenu pédagogique de base, tel que les listes de verbes, les phrases pour les exercices de grammaire, les homophones, les énoncés de petits problèmes mathématiques, les phrases en anglais et les mots à relier, est stocké dans des fichiers JSON dédiés. Cela permet une personnalisation et une extension aisées du matériel pédagogique par l'utilisateur. Les matières couvertes incluent les calculs (additions, soustractions, multiplications, divisions, énumération de nombres, petits problèmes), les mesures (conversions d'unités, rangement de nombres, encadrement), la conjugaison, la grammaire (types de phrases, transformations), l'orthographe (homophones) et l'anglais (phrases à compléter, jeux de mots à relier).


## Structure du projet
```
Apprentium/
├── src/
│   ├── Apprentium.py                  # Point d'entrée de l'application (interface graphique)
│   ├── pdf_generator.py             # Logique de génération des fichiers PDF
│   ├── word_generator.py            # Logique de génération des fichiers Word
│   ├── grammar_generator.py         # Module pour générer les exercices de grammaire (utilise json/phrases_grammaire.json)
│   ├── conjugation_generator.py     # Module pour générer les exercices de conjugaison (utilise json/verbes.json)
│   ├── mesures_generator.py         # Module pour générer les exercices de mesures et conversions
│   ├── anglais_generator.py         # Module pour générer les exercices d'anglais (utilise json/phrases_anglais_*.json, json/mots_a_relier.json)
│   ├── exercise_data_builder.py     # Assemble les données d'exercices pour les générateurs de documents
│   ├── calculs_generator.py         # Module pour générer les exercices de calculs (opérations, problèmes, etc. utilise json/problemes_maths.json pour les problèmes)
│   ├── json/                        # Dossier contenant les données JSON personnalisables
│   │   ├── phrases_grammaire.json
│   │   ├── homophones.json
│   │   ├── mots_a_relier.json
│   │   ├── phrases_anglais_complexe.json
│   │   ├── phrases_anglais_simple.json
│   │   ├── verbes.json
│   │   ├── problemes_math.json
│   │   └── levels_config.json       # Configuration des exercices disponibles par niveau
│   ├── img/                         # Dossier contenant les images utilisées pour les en-têtes de section dans les PDF
│   │   ├── calculs.png    
│   │   ├── mesures.png    
│   │   ├── conjugaison.png    
│   │   ├── grammaire.png    
│   │   ├── orthographe.png    
│   │   └── anglais.png    
│   ├── config.json                  # Fichier de configuration utilisateur sauvegardé (généré au premier lancement si absent)
│   └── Apprentium.ico                 # Icône de l'application
├── requirements.txt                 # Liste des dépendances Python nécessaires
└── README.md                        # Ce fichier.
```

## Installation
Installez les dépendances nécessaires avec :

```
pip install -r requirements.txt
```

## Utilisation (mode Python)
1. Exécutez `Apprentium.py` pour lancer l'application :
   ```
   python src/Apprentium.py
   ```
2. Personnalisez les paramètres (calculs, conjugaison, grammaire, etc.).
3. Cliquez sur "Générer PDF" ou "Générer Word" pour créer la fiche.
4. Le PDF ou le Word est enregistré dans le dossier output.

## Utilisation (exécutable Windows autonome)
1. Compilez avec PyInstaller (logo et dossier JSON à côté de l'exe) :
   ```
   pyinstaller --onefile --noconsole --icon=src/Apprentium.ico --add-data "src/json;json" --add-data "src/img;img" --add-data "src/Apprentium.ico;." --add-data "src/config.json;." src/Apprentium.py
   ```
2. Dans le dossier `dist/`, copiez `Apprentium.exe`, `config.json`, `Apprentium.ico`, et le dossier `json`.
3. Copiez également le dossier `img` dans `dist/` si vous souhaitez que les images des sections PDF soient incluses.
4. Lancez `Apprentium.exe` sur n'importe quel PC Windows (aucune installation Python requise).
5. Les fichiers JSON sont modifiables à côté de l'exe pour personnaliser verbes, phrases, et la configuration des niveaux.
 

## Personnalisation
- **Verbes** : éditez `verbes.json` pour ajouter/supprimer des verbes par groupe.
- **Phrases de grammaire** : éditez `phrases_grammaire.json` pour enrichir les exercices.
- **Phrases en anglais** : éditez `phrases_anglais_complexe.json` et `phrases_anglais_simple.json`
- **mots à relier** : éditez `mots_a_relier.json`
- **homophones** : éditez `homophones.json`
- **Petits Problèmes (Maths)** : éditez `problemes_math.json` pour ajouter ou modifier les énoncés des problèmes.
- **Configuration des Niveaux** : Éditez `levels_config.json` pour définir quels types d'exercices sont disponibles pour chaque niveau scolaire (CP, CE1, etc.). 
- **Apparence des PDF**: Modifiez ou remplacez les images dans le dossier src/img/ (ex: calculs.png, mesures.png) pour changer les illustrations des sections dans les documents PDF générés. 

## Contribuer
Les contributions sont les bienvenues ! N'hésitez pas à proposer des améliorations ou signaler des bugs.