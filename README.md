# presentations

Un dépot contenant toutes mes présentations.

Un workflow pour generer des presentations automatiquement depuis des fichiers markdown. Ce workflow est complètement basé sur celui [présenté dans cet article](https://blog.hanklu.tw/post/2021/use-reveal-md-to-generate-multiple-slides-and-host-them-on-github-page/).

## Pré-requis

- installer npm avec `sudo apt install npm`
- installer npm-run avec `npm install npm-run`
- creer un dépot local qui pointe sur un dépot remote sur Github

## Structure

A la racine du dépot creer cette architecture de dossiers

~~~bash
mkdir -p presentations presentations/attachments theme
~~~

- `presentations` : markdown files. Contient toutes les presentations
 - `attachments` : media (images, audio, video)
- `theme` : custom theme
- `docs` : the generated static site (avec github actions). Servira de DocumentRoot à GithubPages.

## Lancer une présentation



Ecrire un fichier `presentation-1.md` dans `presentations`. Il servira de présentation de test. Par exemple

~~~markdown
# Présentation 1

have fun : )

---

Slide 1


---

Slide 2
~~~

~~~bash
npm-run reveal-md presentations/ -w
~~~

On sert ici tout le contenu de `presentations` à présent visible sur `localhost:1948` et watché (se met à jour en live si les sources sont modifiées).

## Générer le contenu en static

~~~bash
npm-run reveal-md presentations/ --static docs/ --static-dirs=presentations/attachments
~~~

On retrouvera tout notre contenu static dans `docs`. Il n'y a plus qu'à lancer le `index.html` dans votre navigateur. Pas besoin de serveur le projet via un serveur local !

## Aller plus loin : servir les présentations sur un dépot Github avec Github Pages

Pousser tout ça sur le dépot remote en prenant garde d'avoir créer un `.gitignore` ignorant les `node_modules` avant.

Sur Github, aller sur votre dépot. `Settings/Page` puis choisissez /docs comme Source sur la branche main.

Sauvegarder et rendez-vous à l'url de votre GithubPage.

Vous verrez la liste de vos présentations, cliquez et voilà !

## Plusieurs présentations

Pour produire une autre présentation vous n'avez qu'à creer un fichier dans presentations, par exemple presentation2.md. Puis le servir pour tester

~~~bash
npm-run reveal-md presentation/ -w
~~~

Ecrivez vos slides en markdown.

Générez le contenu en static avec la même commande

~~~bash
npm-run reveal-md presentations/ --static docs/ --static-dirs=presentations/attachments
~~~

Poussez et allez visitez votre page Github associée au dépot. Vous devriez voir une liste de vos présentations

- presentation1.html
- presentation2.html

## Ressources

- [Use reveal-md to generate multiple slides and host them on GitHub Page](https://blog.hanklu.tw/post/2021/use-reveal-md-to-generate-multiple-slides-and-host-them-on-github-page/)
