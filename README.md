# Octocat Github Stats Generator ✨

<div  align="center">
  <img src="https://github.com/Foufou-exe/octocat/assets/76502393/90cdbee1-0139-48a3-8373-973d9c50d807" style="width: 50%">
</div>
<br>
The aim of this project is to generate commits statistics from a specific GitHub repository and present them as an SVG file. The statistics are updated daily using a GitHub Action to reflect the latest contributions.

## Table of contents 🌲

- [Fonctionnalités](#fonctionnalités)
- [Utilisation](#utilisation)
- [GitHub Action](#github-action)

## Features 🎈

- Generates an SVG chart of commit statistics for a GitHub repository.
- Automatically updates data every day using a GitHub Action.
- Easy customisation of the graph by modifying the parameters.

## Use 📌

Pour utiliser ce générateur de statistiques, suivez ces étapes simples :

1. `Fork a project `
2. `Adapter le Github action` :
  <img src="https://github.com/Foufou-exe/octocat/assets/76502393/a59e384c-77fe-418a-9c61-a69321787c77" style="width: 50%">
  </br>
  
3. `Put your { TOKEN and repo } values in the 'Secret and vairable ==> Action ' `
  
4. `After test a Github Action`

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
