# Projet Web Scraping & Crawling

**Contexte du projet**
Une équipe data veut constituer un jeu de données à partir d'un site web. Vous collectez d'abord les données (liste des livres, puis fiche de chacun), puis vous découvrez pourquoi un script qui marche sur un site d'entraînement peut être refusé ou bloqué ailleurs, et comment le rendre respectueux des règles du site.

Ce dépôt contient l'ensemble de mes travaux pratiques sur l'extraction de données web (Web Scraping et Crawling) réalisés en Python. L'objectif de ces notebooks est de maîtriser la collecte de données, de la simple requête HTTP à l'automatisation éthique d'un pipeline d'extraction complet.

## Technologies et Librairies utilisées

- **Python 3**
- `requests` : Pour l'envoi de requêtes HTTP et le téléchargement du code source des pages.
- `BeautifulSoup` (bs4) : Pour le parsing du code HTML et l'extraction de données via des sélecteurs CSS.
- `pandas` : Pour la structuration des données collectées (DataFrames), le nettoyage, la fusion et l'export.
- `re` (Regex) : Pour le nettoyage de chaînes de caractères complexes.
- `urllib` : Pour la gestion des URL absolues/relatives et l'analyse des fichiers `robots.txt`.
- `time` : Pour la gestion des pauses (Rate Limiting).

## Contenu du dépôt

Ce projet est divisé en 3 notebooks progressifs :

### Notebook 1 : Scraping Classique (`books.toscrape.com`)

- **Objectif :** Extraire le catalogue complet d'une librairie en ligne (1 000 livres sur 50 pages).
- **Concepts clés :**
  - Inspection du DOM et utilisation des sélecteurs CSS (`.select`, `.select_one`).
  - Crawling horizontal (pagination via le bouton "Next").
  - Crawling vertical (visite des 1 000 fiches détaillées des livres).
  - Nettoyage des données et export au format CSV.

### Notebook 2 : Éthique, User-Agent et robots.txt

- **Objectif :** Comprendre les règles du jeu du web et créer un scraper "poli" capable de s'adapter aux restrictions d'un site réel comme Wikipédia.
- **Concepts clés :**
  - Personnalisation du `User-Agent` pour s'identifier de manière transparente.
  - Lecture et respect du fichier `robots.txt` via `RobotFileParser`.
  - Gestion des codes d'erreurs HTTP (403 Forbidden, 429 Too Many Requests, 503).
  - Création d'une fonction de requête robuste (`get_poli`) incluant un délai de pause et un mécanisme de _Backoff Exponentiel_.

### Notebook 3 : Mission d'adaptation (`quotes.toscrape.com`)

- **Objectif :** Adapter le code complet du premier notebook sur un tout nouveau site, sans code fourni, en appliquant les règles d'éthique du deuxième notebook.
- **Concepts clés :**
  - Adaptation des sélecteurs CSS à une nouvelle structure HTML.
  - Nettoyage avancé (retrait de guillemets typographiques) et extraction de listes (tags).
  - Optimisation des requêtes : utilisation de `.unique()` pour ne scraper la biographie de chaque auteur qu'une seule fois.
  - Analyses Pandas : Jointure de DataFrames (`pd.merge`) et comptage sur des listes dépliées (`explode`).

## Comment lancer le projet

1. Clonez le dépôt sur votre machine locale.
2. Créez un environnement virtuel (`.venv`).
3. Installez les dépendances requises :
   ```bash
   pip install requests beautifulsoup4 pandas
   ```
4. Ouvrez les notebooks dans Jupyter ou VS Code et exécutez les cellules étape par étape.

## Compétences validées

- [x] Naviguer dans l'arborescence HTML d'un site web.
- [x] Automatiser la collecte de données sur de multiples pages.
- [x] Mettre en place un scraping éthique (User-Agent, robots.txt, délais).
- [x] Nettoyer et structurer les données brutes pour l'analyse.
