# Octocat Github Stats Generator ✨

<div  align="center">
  <img src="https://github.com/Foufou-exe/octocat/assets/76502393/90cdbee1-0139-48a3-8373-973d9c50d807" style="width: 50%">
</div>
<br>
Ce projet a pour objectif de générer des statistiques de commits à partir d'un référentiel GitHub spécifique et de les présenter sous forme de fichier SVG. Les statistiques sont mises à jour quotidiennement à l'aide d'une GitHub Action pour refléter les dernières contributions.

## Table des matières 🌲

- [Fonctionnalités](#fonctionnalités)
- [Utilisation](#utilisation)
- [GitHub Action](#github-action)

## Fonctionnalités 🎈

- Génère un graphique SVG des statistiques de commits pour un référentiel GitHub.
- Met à jour automatiquement les données chaque jour grâce à une GitHub Action.
- Personnalisation facile du graphique en modifiant les paramètres.

## Utilisation 📌

Pour utiliser ce générateur de statistiques, suivez ces étapes simples :

1. `Fork le projet `
2. `Adapter le Github action` :
  <img src="https://github.com/Foufou-exe/octocat/assets/76502393/a59e384c-77fe-418a-9c61-a69321787c77" style="width: 50%">
  </br>
  
3. `Mettre vos valeurs {  TOKEN et repo } dans le 'Secret et vairable ==> Action ' `
  
4. `Puis tester le Github Action`

## GitHub Action ⚙️
```yaml
name: GitHub-Profile-3D-Contrib

on:
  schedule: # 03:00 JST == 18:00 UTC
    - cron: "0 18 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-profile-3d-contrib
    steps:
      - uses: actions/checkout@v3
      - uses: yoshi389111/github-profile-3d-contrib@0.7.1
        env:
          GITHUB_TOKEN: ${{ secrets.TOKEN }}
          USERNAME: ${{ github.repository_owner }}
      - name: Commit & Push
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com
          git add -A .
          git commit -m "generated"
          git push
```









