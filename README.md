# Chapitre 3 - PAGES STATIQUES - By Michael Hartl

Bien que Rails soit destiné à créer des sites web dynamiques avec base de données, il excèle aussi à faire ce genre de pages statiques que nous pouvons créer simplement par des fichiers de code HTML brut. En fait, utiliser Rails même pour des pages statiques produit un avantage certain : nous pouvons ajouter seulement une petite quantité de code dynamique. Nous verrons comment dans ce chapitre. Chemin faisant, nous aurons un avant-goût du testing automatique, qui nous aidera à nous sentir plus confiant en notre code. Plus loin encore, avoir une bonne suite de tests nous permettra de restructurer notre code en toute confiance, en changeant sa forme sans altérer sa fonction.

Comme au [chapitre 2](https://github.com/Zouz84/demo_app), avant de commencer nous avons besoin de créer un nouveau projet Rails, cette fois appelé **sample_app** (Application Exemple) :<br/>
```Ruby
$ cd ~/rails_projects
$ rails new sample_app -T
$ cd sample_app
```
Notre prochaine étape consiste à utiliser un éditeur de texte pour actualiser le fichier [Gemfile](https://github.com/Zouz84/Chapter3/blob/master/Gemfile) avec les gems nécessaires à notre application.<br/>
<br/>
Ceci fait, il ne nous reste plus qu'à initialiser le repository Git :<br/>
```Ruby
$ git init
$ git add .
$ git commit -m "Met ce que tu veux, on est en Amérique ! Ah, non? Pas grave."
```
Initialise un nouveau repository:<br/>
```Ruby
$ git remote add origin git@github.com:<username>/sample_app.git
$ git push origin master
```
Et on déploie direct sur Heroku. C'est plus safe:<br/>
```Ruby
$ heroku create
$ git push heroku master
```

***

## 3.1.1 Initialisation
