# Simple Web App

## Description
Cette application web simple utilise HTML, CSS et JavaScript. Elle affiche une page web avec un bouton qui déclenche une alerte lorsqu'il est cliqué.

## Fonctionnalités
- Affiche un message de bienvenue.
- Un bouton qui, lorsqu'il est cliqué, affiche une alerte "Bouton cliqué!".

## Structure du Projet
- `index.html` : La page HTML principale.
- `styles.css` : La feuille de style CSS pour la mise en page.
- `app.js` : Le fichier JavaScript pour les interactions.
- `Dockerfile` : Le fichier pour construire l'image Docker.
- `.github/workflows/ci-cd.yml` : Le workflow GitHub Actions pour le CI/CD.
- `app.test.js` : Le fichier de tests pour le JavaScript.
- `package.json` : Le fichier de configuration du projet Node.js et Jest.

## Prérequis
- Node.js installé
- Docker installé

## Installation
1. Cloner le repository :
    ```bash
    git clone https://github.com/darryl000/web-app.git
    cd simple-web-app
    ```

2. Installer les dépendances Node.js :
    ```bash
    npm install
    ```

## Exécution de l'Application
1. Ouvrir `index.html` dans un navigateur pour voir l'application.

## Exécution des Tests
1. Exécuter les tests avec Jest :
    ```bash
    npm test
    ```

## Construction de l'Image Docker
1. Construire l'image Docker :
    ```bash
    docker build -t web-app .
    ```

2. Exécuter l'image Docker :
    ```bash
    docker run -p 8081:80 web-app
    ```

3. Accéder à l'application :
    - Ouvrir un navigateur et aller à l'adresse suivante :
      ```
      http://localhost:8081
      ```

## Déploiement de l'Application

### Déploiement avec Docker Hub
1. Se connecter à Docker Hub :
    ```bash
    docker login
    ```

2. Taguer l'image Docker :
    ```bash
    docker tag web-app darryl443/web-app
    ```

3. Pousser l'image vers Docker Hub :
    ```bash
    docker push darryl443/web-app
    ```

4. Tirer et exécuter l'image depuis Docker Hub :
    ```bash
    docker pull darryl/web-app
    docker run -p 8081:80 darryl443/web-app
    ```

### Déploiement avec Docker Compose
1. Créer un fichier `docker-compose.yml` :
    ```yaml
    version: '3'
    services:
      web:
        image: simple-web-app
        ports:
          - "8081:80"
    ```

2. Démarrer le conteneur avec Docker Compose :
    ```bash
    docker-compose up
    ```

3. Accéder à l'application :
    - Ouvrir un navigateur et aller à l'adresse suivante :
      ```
      http://localhost:8081
      ```

## Pipeline CI/CD avec GitHub Actions
1. Le fichier de workflow GitHub Actions est situé dans `.github/workflows/ci-cd.yml`.
2. Le workflow est déclenché à chaque push sur la branche `main`.
3. Le pipeline CI/CD effectue les étapes suivantes :
    - Exécute les tests.
    - Construit l'image Docker.
    - Pousse l'image sur Docker Hub.

## Résolution des Problèmes
### Erreur de Port
Si vous rencontrez l'erreur suivante :
```text
docker: Error response from daemon: Ports are not available: exposing port TCP 0.0.0.0:8080 -> 0.0.0.0:0: listen tcp 0.0.0.0:8080: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.
