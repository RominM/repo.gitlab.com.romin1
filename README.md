# Repo GitLab to GitHub Import

Ce référentiel contient les étapes et les informations sur l'importation des commits depuis un référentiel GitLab vers un référentiel GitHub.

## Objectif

L'objectif de ce processus est de transférer tous les commits d'un projet GitLab vers un nouveau projet GitHub.

## Étapes

1. **Installation de l'outil d'importation :** Tout d'abord, installez l'outil d'importation en exécutant la commande suivante :

```sh
go install github.com/alexandear/import-gitlab-commits@latest
```
   
2. **Configuration des variables d'environnement :** Configurez les variables d'environnement requises pour l'outil d'importation :
  
  ```js
  $env:GITLAB_BASE_URL = "https://gitlab.com/"
  $env:GITLAB_TOKEN = "YOUR_GITLAB_TOKEN"
  $env:COMMITTER_NAME = "Your Name"
  $env:COMMITTER_EMAIL = "your.email@example.com"
  ```

3. **Exécution de l'importation :** Exécutez la commande pour importer les commits depuis GitLab :

  ```sh
  import-gitlab-commits
  // cette commande crée automatiquement un dossier du projet GitLab qui contiendra votre historique
  ```

4. **Création d'un nouveau référentiel sur GitHub :** Ensuite, créez un nouveau référentiel vide sur GitHub portant le même nom que le projet GitLab.

5. **Initialisation du référentiel local :** L'outil d'importation a créé un dossier contenant un dépôt Git initial avec l'historique des commits provenant de GitLab. J'ai ensuite navigué vers ce dossier et initialisé un nouveau dépôt Git local :
  ```sh
  cd nom_du_dossier_importé
  git remote add origin git@github.com:username/nom_du_referentiel_github.git
  git push -u origin main
  ```

Ces étapes ont permis de transférer avec succès les commits du projet GitLab vers le référentiel GitHub, en créant un nouveau référentiel sur GitHub et en poussant les modifications depuis le dépôt local. Assurez-vous de personnaliser les informations telles que "YOUR_GITLAB_TOKEN", "Your Name", "your.email@example.com", "nom_du_dossier_importé", "username" et "nom_du_referentiel_github" en fonction de votre configuration et de votre nom de projet.

