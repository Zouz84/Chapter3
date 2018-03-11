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
En gros on nous explique que localhost:3000 et localhost:3000/index ne sont qu'une seule et même page, et que tout ce qui apparaitra dans votre dossier "public" s'affichera en ligne sur la page d'accueil. Mais j'ai pas l'habitude de fonctionner comme ça, alors on va pas y rester 100 ans.
### <a name ="3.1.2">3.1.2 LEs pages statiques avec Rails </a>
Dans cette section, nous ferons un premier pas vers la création de pages dynamiques en créant un jeu d'actions Rails, qui sont une façon plus puissante de définir des URLs que les fichiers statiques.<br/>
Rails est fourni avec un script pour créer des contrôleurs, appelé generate ; tout ce dont il a besoin pour faire son tour de magie, c'est le nom du contrôleur. Puisque nous créons ce contrôleur pour traiter les pages statiques (courantes), nous l'appellerons simplement le contrôleurs Pages, et planifierons de faire des actions pour la page d'accueil, la page de contact et la page « À Propos ». Le script generate prend une liste optionnelle d'actions, donc nous incluerons certaines de ces actions initiales directement en ligne de commande :<br/>
`$ rails generate controller Pages home contact`.
Concrètement, nous venons de demander à Rails de créer un **controller** "Pages" qui possède 2 actions: **_home_** et **_contact_**.<br/>
<br/>
Si l'on se rend dans notre fichier **routes.rb**, on peut voir que *Rails* a généré 2 routes:<br/>
```Ruby
Rails.application.routes.draw do
  get 'pages/home'

  get 'pages/contact'

  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
end
```
Si vous ouvrez votre app en serveur local, vous allez tomber sur le fameux "*Yay! You're on rails!*". Si vous aller à l'adresse: http://localhost:3000/pages/home, vous tomberez sur le **views** "home", que l'on verra plus tard. L'important ici, c'est de voir que la route fonctionne. Merci Rails.<br/>
En utilisant get nous nous arrangeons pour que la route réponde à la requête GET, qui est un des verbes HTTP fondamentaux supporté par le Hypertext Transfer Protocol (Box 3.1). Dans notre cas, cela signifie que lorsque nous générons une action home à l'intérieur du contrôleur Pages nous atteignons automatiquement une page à l'adresse /pages/home. <br/>
<br/>
Si l'on se rend maintenant dans le controller *Pages*, voici ce que nous y verrons:
```Ruby
class PagesController < ApplicationController

  def home
  end

  def contact
  end
end
```
On y remarque que ce controlleur Pages hérite (**<**) directement de l'ApplicationController, qui elle même hérite de l'[ActionController::Base](https://github.com/Zouz84/demo_app#235-hi%C3%A9rarchie-des-h%C3%A9ritages).<br/>
Parce qu'elle hérite de la classe ApplicationController le comportement de ses méthodes est spécifique à Rails : en visitant l'URL **/pages/home**, Rails consulte le **contrôleur Pages** et exécute le code de l'**action home**, et rend alors la vue (le caractère « **V** » de [MVC](https://github.com/Zouz84/demo_app#222-mvc-en-action)) correspondant à l'action.<br/>
Dans le cas présent, l'action home est vide, donc tous les appels à **/pages/home** rendent simplement la vue. Donc, à quoi ressemble une vue, et où la trouvons-nous ?<br/>
Réponse: **_app/views/pages/home.html.erb_**



