<h1 align="center">Rakib Hasan</h1>

<div align="center">
<img src="https://www.bing.com/th/id/OGC.e1f3413bf5036045713341394f617225?pid=1.7&rurl=http%3a%2f%2fjavanrayan.com%2fimages%2f1397%2f08%2f17%2fprogrammer.gif&ehk=SSyT4%2faf8JThO%2boBBzorrPrIZY4y6gBsmpYphb%2fgDdo%3d" width="350">
</div>

<p align="justify">Rakib Hasan is currently pursuing a Bachelor of Science degree in Computer Science and Engineering at Daffodil International University. He is competent in several programming languages, such as C, Java, Python, Assembly, and Dart, and is also skilled in data structure, algorithms, object-oriented programming, data mining, and machine learning. He has completed some projects using those languages. His strengths are that he is self-motivated, hardworking, disciplined, and a quick learner. His short-term plan is to complete his graduation with a high grade, and his long-term goal is to attain an honest position wherever he will build his career as well as serve his nation.</p>

- 💬 Ask me about **C, Python, Assembly, Dart, Data Structure, Algorithms, Object-Oriented Programming, Data Mining, and Machine Learning**


<p><img align="left" src="https://github-readme-stats.vercel.app/api/top-langs?username=engrrakibhasan&show_icons=true&locale=en&layout=compact" alt="engrrakibhasan" /></p>

<p>&nbsp;<img align="center" src="https://github-readme-stats.vercel.app/api?username=engrrakibhasan&show_icons=true&locale=en" alt="engrrakibhasan" /></p>

<p><img align="center" src="https://github-readme-streak-stats.herokuapp.com/?user=engrrakibhasan&" alt="engrrakibhasan" /></p>



# GitHub Action for generating a contribution graph with a snake eating your contributions.

name: Generate Snake

# Controls when the action will run. This action runs every 6 hours.

on:
  schedule:
      # every 6 hours
    - cron: "0 */6 * * *"

# This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Generates the snake  
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: engrrakibhasan
          # these next 2 lines generate the files on a branch called "output". This keeps the main branch from cluttering up.
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

     # show the status of the build. Makes it easier for debugging (if there's any issues).
      - run: git status

      # Push the changes
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
