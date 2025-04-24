## Olá! Eu sou o Gabriel

- 🔎 Procurando trabalho de Front-End React  
- 📖 Estudando React, Node.js  
- 😊 Pronome: ele/dele  
- 🎓 Graduando Ciência da Computação na Fiap Paulista   

<br/>

<p align="center">
  <!-- GitHub Stats -->
  <a href="https://github.com/anuraghazra/github-readme-stats">
    <img height="180em" src="https://github-readme-stats.vercel.app/api?username=gabrieljcoutinho&show_icons=true&theme=dracula&include_all_commits=true&count_private=true&cache_seconds=1800&v=11" alt="GitHub Stats"/>
  </a>
  
  <!-- Top Languages -->
  <a href="https://github.com/anuraghazra/github-readme-stats">
    <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=gabrieljcoutinho&layout=compact&theme=dracula&langs_count=8&v=1" alt="Top Languages"/>
  </a>
</p>

<br/>

<!-- Skills -->
<div style="display: inline_block;"><br>
    <img align="center" alt="Gabriel-HTML" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg">
    <img align="center" alt="Gabriel-CSS" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original.svg">
  <img align="center" alt="Gabriel-Js" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg">
  <img align="center" alt="Gabriel-React" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original.svg">
  <img align="center" alt="Gabriel-Python" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg">
  <img align="center" alt="Gabriel-Python" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/vscode/vscode-original.svg">

</div>

<br/><br/>

<!-- Social Media -->
<div>
  <a href="https://www.instagram.com/gabrieljorgecoutinho/" target="_blank">
    <img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" />
  </a>
  <a href="https://www.linkedin.com/in/gabriel-jorge-coutinho/" target="_blank">
    <img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
</div>

















# GitHub Action for generating a contribution graph with a snake eating your contributions.

# ![snake gif](https://github.com/your-user-name/your-user-name/blob/output/github-contribution-grid-snake.gif)

name: Generate Snake

# Controls when the action will run.
on:
  schedule:
      # every 12 hours
    - cron: "0 */12 * * *"

  # This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:
  
  # Also run on every push on the master branch
  push:
    branches:
    - main

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

 Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      - name: Clone repo
        uses: actions/checkout@v3
    
   - name: Generate the snake files in './dist/'
        uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |     
            dist/github-contribution-grid-snake.gif
            dist/github-contribution-grid-snake.svg
        env:
           GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      - name: Show build status
        run: git status

      - name: Push new files to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
          commit_message: Update snake animations
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}







