<h1 align="center">Rakib Hasan</h1>

<div align="center">
<img src="https://www.bing.com/th/id/OGC.8190a1dce0daf6e56c705dba6e07d27f?pid=1.7&rurl=https%3a%2f%2fcdn.dribbble.com%2fusers%2f5690231%2fscreenshots%2f16191500%2fmedia%2f4fbd0ec22f13a3521bb37cc5fe8b1cb3.gif&ehk=EG0DMGOyUJ3le8SNjdlo%2bLxxSje3wP1E7qT5TKymyW0%3d" width="350">
</div>

<p align="justify">Rakib Hasan is currently pursuing a Bachelor of Science degree in Computer Science and Engineering at Daffodil International University. He is competent in several programming languages, such as C, Java, Python, Assembly, and Dart, and is also skilled in data structure, algorithms, object-oriented programming, data mining, and machine learning. He has completed some projects using those languages. His strengths are that he is self-motivated, hardworking, disciplined, and a quick learner. His short-term plan is to complete his graduation with a high grade, and his long-term goal is to attain an honest position wherever he will build his career as well as serve his nation.</p>

- 💬 Ask me about **C, Python, Assembly, Dart, Data Structure, Algorithms, Object-Oriented Programming, Data Mining, and Machine Learning**


# GitHub Action for generating a contribution graph with a snake eating your contributions.
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

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      - name: Clone repo
        uses: actions/checkout@v3
    
      - name: Generate the snake files in './dist/'
        uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
            dist/github-contribution-grid-snake.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
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
