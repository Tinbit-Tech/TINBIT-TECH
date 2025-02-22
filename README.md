<img src="https://github.com/Tinbit-Tech/TINBIT-TECH/blob/main/1_J20ej4fVYltW8HU7skIQ0Q.jpg" width="125%">
<h1 align="center">Hi 👋, I'm Tinbit Tefera</h1>
<h3 align="center">A passionate Software Engineer from Ethiopia</h3>

<img align="right" alt="coding" width="400" src="https://user-images.githubusercontent.com/55389276/140866485-8fb1c876-9a8f-4d6a-98dc-08c4981eaf70.gif">

<p align="left"> <img src="https://komarev.com/ghpvc/?username=tinbit-tech&label=Profile%20views&color=0e75b6&style=flat" alt="tinbit-tech" /> </p>

- 👨‍💻 All of my projects are available at [https://linktr.ee/tinbit_tech](https://t.me/+FU574b8Zg7kxODI0)

- ⚡ Fun fact **I love exploring new technologies!**

<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://linkedin.com/in/tinbit/" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="tinbit-tech" height="30" width="40" /></a>
<a href="https://instagram.com/tinbito1" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="tinbit_tech" height="30" width="40" /></a>
<a href="https://www.youtube.com/c/tinbit_tech" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/youtube.svg" alt="tinbit_tech" height="30" width="40" /></a>
</p>

<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.cprogramming.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg" alt="c" width="40" height="40"/> </a> <a href="https://www.w3schools.com/cpp/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/cplusplus/cplusplus-original.svg" alt="cplusplus" width="40" height="40"/> </a> <a href="https://www.w3schools.com/css/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="css3" width="40" height="40"/> </a> <a href="https://www.w3.org/html/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="html5" width="40" height="40"/> </a> <a href="https://www.java.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="java" width="40" height="40"/> </a> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/> </a> <a href="https://www.mathworks.com/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png" alt="matlab" width="40" height="40"/> </a> <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a> <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> </a> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> </p>

name: Update README with Languages

on:
  schedule:
    - cron: '0 0 * * *' # Runs daily at midnight
  push:
    branches:
      - main

jobs:
  update-readme:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Fetch languages used in repositories
      run: |
        curl -s https://api.github.com/repos/Tinbit-Tech/registration/languages > registration-languages.json
        curl -s https://api.github.com/repos/Tinbit-Tech/victory-hotel-online-booking/languages > victory-hotel-online-booking-languages.json

    - name: Update README.md
      run: |
        LANGUAGES=$(jq -r 'keys | join(", ")' registration-languages.json)
        LANGUAGES="$LANGUAGES, $(jq -r 'keys | join(", ")' victory-hotel-online-booking-languages.json)"
        sed -i "/<h3 align=\"left\">Support:<\/h3>/,/<\/p>/c\\
        <h3 align=\"left\">Support:</h3>\\
        <p><a href=\"https://www.buymeacoffee.com/tinbittech\"> <img align=\"left\" src=\"https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png\" height=\"50\" width=\"210\" alt=\"tinbit tech\" /></a></p><br><br>\\
        <p>Languages used: $LANGUAGES</p>\\
        <p><img align=\"left\" src=\"https://github-readme-stats.vercel.app/api/top-langs?username=tinbit-tech&show_icons=true&locale=en&layout=compact\" alt=\"tinbit-tech\" /></p>\\
        <p>&nbsp;<img align=\"center\" src=\"https://github-readme-stats.vercel.app/api?username=tinbit-tech&show_icons=true&locale=en\" alt=\"tinbit-tech\" /></p>\\
        <p><img align=\"center\" src=\"https://github-readme-streak-stats.herokuapp.com/?user=tinbit-tech&\" alt=\"tinbit-tech\" /></p>" README.md

    - name: Commit changes
      run: |
        git config --global user.name 'github-actions[bot]'
        git config --global user.email 'github-actions[bot]@users.noreply.github.com'
        git add README.md
        git commit -m "Update README with languages"
        git push
