<h1 align="center">Hey 👋What's Up?</h1>

###

<div align="center">
  <a href="https://www.linkedin.com/in/felipe-levi-238ba1367/" target="_blank">
    <img src="https://raw.githubusercontent.com/maurodesouza/profile-readme-generator/master/src/assets/icons/social/linkedin/default.svg" width="52" height="40" alt="linkedin logo"  />
  </a>
  <a href="https://www.instagram.com/lev1sk8/" target="_blank">
    <img src="https://raw.githubusercontent.com/maurodesouza/profile-readme-generator/master/src/assets/icons/social/instagram/default.svg" width="52" height="40" alt="instagram logo"  />
  </a>
</div>

###

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=lev1developer&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=dracula&locale=en&hide_border=false&order=1" height="150" alt="stats graph"  />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=lev1developer&locale=en&hide_title=false&layout=compact&card_width=320&langs_count=5&theme=dracula&hide_border=false&order=2" height="150" alt="languages graph"  />
</div>

###

<div align="center">
  <img src="https://img.shields.io/badge/CSS-1572B6?logo=css&logoColor=white&style=for-the-badge" height="40" alt="css logo"  />
  <img width="12" />
  <img src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white&style=for-the-badge" height="40" alt="html5 logo"  />
</div>

###

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/lev1developer/lev1developer/output/pacman-contribution-graph-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/lev1developer/lev1developer/output/pacman-contribution-graph.svg">
  <img alt="pacman contribution graph" src="https://raw.githubusercontent.com/lev1developer/lev1developer/output/pacman-contribution-graph.svg">
</picture>

###

<div align="left">
  <img src="https://visitor-badge.laobi.icu/badge?page_id=lev1developer.lev1developer&"  />
</div>

###

<div align="center" style="width: 100%">
  <a target="_blank" href="https://github-readme-medium-recent-article.vercel.app/medium/@undefined/0">
    <img style="width: 100%" src="https://github-readme-medium-recent-article.vercel.app/medium/@undefined/0" alt="Medium post 1"  />
  </a>
  <a target="_blank" href="https://github-readme-medium-recent-article.vercel.app/medium/@undefined/1">
    <img style="width: 100%" src="https://github-readme-medium-recent-article.vercel.app/medium/@undefined/1" alt="Medium post 2"  />
  </a>
  <a target="_blank" href="https://github-readme-medium-recent-article.vercel.app/medium/@undefined/2">
    <img style="width: 100%" src="https://github-readme-medium-recent-article.vercel.app/medium/@undefined/2" alt="Medium post 3"  />
  </a>
</div>

###

name: Generate pacman animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate pacman-contribution-graph.svg
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}


      - name: push pacman-contribution-graph.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
