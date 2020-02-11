---
layout: page
title: Une journée de web scraping en Python
permalink: webscraping-00-student
---

### WORKSHOP WEB SCRAPING EN PYTHON
![python-web-scraping-tutorial](https://www.dataquest.io/wp-content/uploads/2016/11/python-web-scraping-beautifulsoup-tutorial-1040x520.jpg "python-web-scraping-tutorial")

Ce workshop est une introduction au *web scraping* ou
**extraction astucieuse de données** en français. Le terme anglais sera
utilisé comme si c'était un terme français tout au long
de ce document : web scraping.

Définition :
> Le scraping définit de façon générale une technique permettant d'extraire du contenu (des informations) d'un ou de plusieurs sites web de manière totalement automatique. Ce sont des scripts, des programmes informatiques, qui sont chargés d'extraire ces informations.

> Le scraping, web scraping ou encore harvesting, a plusieurs utilités. Il permet d'abord de réutiliser des contenus présents sur un site web pour l'afficher sur un autre site web, et ainsi multiplier sans effort le nombre de pages disposant d'un même contenu. Cette technique, assimilée à du pillage ou pompage de contenu, participe à un meilleur référencement d'un site web, sauf lorsqu'elle est détectée par les algorithmes des moteurs de recherche (qui la sanctionnent sévèrement). 

> Le scraping peut également être utilisé comme un outil de surveillance des concurrents (on récupère automatiquement les tarifs pratiqués par un site de commerce en ligne concurrent et l'on détecte leurs variations) ou comme outil de veille concurrentielle.


Dans les exercices suivants nous vous demanderont de toucher à plusieurs langages qui vous seront utiles afin de réaliser une boucle de scraping, soit extraire de l'html à partir de python.

## Exercice 00 : Les prérequis

Les modules à installer:
```
sudo apt-instal python3.7

pip3 install lxml

pip3 install regex

pip3 install selenium

pip3 install urllib
```
## Exercice 01 : Les xpath 

Cette exercice consite en l'obtention du chemin vers une partie d'un document xml.

La doc: [clique ici](https://openclassrooms.com/fr/courses/1766341-structurez-vos-donnees-avec-xml/1769083-xpath-localiser-les-donnees)

Les exercices sont [ici](http://learn.onion.net/language=en/35426/w3c-xpath).

## Exercice 02 : Les xpath II

Voici un cas pratique du web scraping.
Il vous faudra déterminer un chemin Xpath pour obtenir le prix, le titre, l'image du premier livre en vente affiché sur la page suivante: [Harry Potter livres](https://www.fnac.com/SearchResult/ResultList.aspx?SCat=0%211&Search=harry+potter&sft=1&sa=0)

## Exercice 03 : Les xpath III

Déterminez deux autres chemins xpath différents pour le titre de manière à ce que ces chemins xpath mènent à la même partie du document xml mais en utilisant d'autres procédés (chil/node/ancestor etc...).

Vous devrez maintenant déterminer lequel des trois chemins xpath pour le titre est le plus simple, le plus court, et en même temps le plus unique. De manière à ce qu'il puisse mener uniquement à la partie du document xml désirée et qu'il soit facilement réutilisable dans un programme.

Puis répéter l'exercice pour le prix et l'image.

## Exercice 04 : Les Regex

Cette exercice consiste en l'obtention d'une chaîne de caractère spécifique qui va apparaître régulièrement dans un texte. Le but est par la suite d'extraire la chaîne de caractère désirée de manière automatisée grâce aux regex (expressions régulières) au sein d'un programme vaste de web scraping.

La doc: [clique ici](https://www.w3schools.com/python/python_regex.asp)

Les exercices sont [ici](https://www.w3resource.com/python-exercises/re/)


## Exercice 05 : Selenium I

Selenium chromedriver est le framework que nous utiliserons pour simuler le comportement humain sur une page web de manière automatisée.

Attention à ne pas générer un traffic trop important avec votre webdriver sinon vous risquez de surcharger les serveurs du site visé ce qui n'est en aucun cas souhaitable.

La doc: [clique ici](https://chromedriver.chromium.org/getting-started)

Réalisez un programme qui permet de:
1) localiser un élément par ce qu'il affiche.
2) localiser un élément par son `ID`.
3) localiser un élément par `Linktext`.
4) localiser un élément par `Linktext partiel`.
5) localiser un élément par `Xpath`.
6) localiser un élément par `CSS selector`.
7) localiser un élément par `Tagname`.
8) localiser un élément par `Classname`.


## Exercice 06 : Selenium II

Réalisez un programme qui permet de:

1) cliquer sur le bouton `j'ai de la chance` de google.
2) ouvrir `plusieurs onglets` et de `changer le focus` du webdriver d'un onglet à l'autre.
3) `se connecter à un compte` avec identifiant et mot de passe (par exemple un compte Facebook).

## Exercice 07 : Selenium III

Votre tâche consiste en le scraping du site [jd](https://www.jdsports.fr/promo/).

Vous allez pouvoir vous aider de la lib [lxml](https://lxml.de/tutorial.html).

Vous allez dans un premier temps télécharger la page web jd indiquée.

Puis vous aller récupérer un document xml grâce aux fonctions de la lib lxml à partir de la page web téléchargée.

Vous allez `parser en boucle` le document xml obtenu. Grâce aux chemins Xpath vers le prix, l'image et le titre de chaque item, vous pourrez récupérer les informations désirées.

Enfin il vous faudra `stocker ces informations` dans un dictionnaire.

Il se peut que les informations obtenues via les chemins Xpaths soient mếlées avec d'autres informations parasyte. Pour ne garder que l'essentiel vous pouvez `filtrer` cela grâce aux regex.

Recommencez avec le site [nike](https://www.nike.com/fr/w/hommes-chaussures-nik1zy7ok) maintenant. 

Vous ne devriez avoir besoin de changer que les chemins Xpath pour que le même programme fonctionne sur chacun des deux sites.

## Exercice 08 : Selenium IV

Votre tâche consiste en le scraping complet des spiritueux du site [argonaut](https://www.argonautliquor.com/) dans le but de récupérer les informations (nom du produit, volume, prix brut, prix promo, url de l'image, url de redirection vers la page produit) des spiritueux du groupe [LVMH](https://www.lvmh.fr/les-maisons/vins-spiritueux/).

1) Vous devrez dans un premier temps scraper les spiritueux par `catégorie`. 
Il faudra scraper les dix premières pages de chaque `catégorie` (vodka, sparkling, cognac, champagne, still wines, whisky, gin, tequila, red wine, white wine, rum, liquor, brandy, mezcal).

2) Puis il faudra scraper les spiritueux par `mot clef` en utilisant le moteur de recherche du site argonaut. Choisissez les mots clefs les plus pertinants pour obtenir des informations similaires à celles obtenues via le scraping par catégorie. 
Le but étant de croiser l'information pour ne pas rater d'items. Encore une fois, scrapez les dix premières pages de chaque recherche par `mot clef`.

3) Enfin, lors du scraping par catégorie et par mot clef, vous devrez récupérer l'url de la `page produit` des spiritueux du groupe [LVMH](https://www.lvmh.fr/les-maisons/vins-spiritueux/) et les stocker pour réaliser une troisième et dernière boucle de scraping. Elle consiste en le scraping de toutes les `pages produits` à partir des url précédemment obtenus.

## Exercice 09 : Selenium V

Une fois le programme fonctionnel, répétez l'opération avec un site similaire comme [Millesima](https://www.millesima.fr/) et perfectionnez le programme pour le rendre `adaptable` à n'importe quel site e-commerce.