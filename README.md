# Chapitre 3 - PAGES STATIQUES - By Michael Hartl

Bien que Rails soit destiné à créer des sites web dynamiques avec base de données, il excèle aussi à faire ce genre de pages statiques que nous pouvons créer simplement par des fichiers de code HTML brut. En fait, utiliser Rails même pour des pages statiques produit un avantage certain : nous pouvons ajouter seulement une petite quantité de code dynamique. Nous verrons comment dans ce chapitre. Chemin faisant, nous aurons un avant-goût du testing automatique, qui nous aidera à nous sentir plus confiant en notre code. Plus loin encore, avoir une bonne suite de tests nous permettra de restructurer notre code en toute confiance, en changeant sa forme sans altérer sa fonction.

!>>>>>>>>>>>>>>>>> [Passe Les étapes préliminaires habituelles](#3.1) <<<<<<<<<<<<<<<<!

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

## <a name="3.1">3.1 Pages Statiques</a>
Rails propose deux principales manières de créer des pages web statiques. Primo, Rails peut utiliser des pages vraiment statiques contenant du code HTML brut. Secondo, Rails nous permet de définir des vues (views) contenant du HTML brut, que Rails peut rendre de telle sorte que les serveurs web puisse les envoyer au navigateur.<br/>
### <a name="3.1.1">3.1.1 Vraies pages statiques</a>

