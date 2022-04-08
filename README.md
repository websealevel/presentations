# presentations

Un dépot contenant toutes mes présentations.

Un workflow pour generer des presentations automatiquement depuis des fichiers markdown. Ce workflow est complètement basé sur celui [présenté dans cet article](https://blog.hanklu.tw/post/2021/use-reveal-md-to-generate-multiple-slides-and-host-them-on-github-page/).

## Pré-requis

- installer npm avec `sudo apt install npm`
- installer npm-run avec `npm install npm-run`

## Structure

- `presentation-1` : markdown files
 - `attachments` : media (images, audio, video)
- `theme` : custom theme
- `docs` : the generated static site (avec github actions)

## Lancer une présentation

~~~bash
npm-run reveal-md presentation-1/ -w
~~~

On sert ici tout le contenu de `presentation-1` à présent visible sur `localhost:1948` et watché (se met à jour en live si les sources sont modifiées).

## Générer le contenu en static

~~~bash
npm-run reveal-md presentation-1/ --static docs/ --static-dirs=presentation-1/attachments
~~~

On retrouvera tout notre contenu static dans `docs/presentation-1`. Il n'y a plus qu'à lancer le `index.html` dans votre navigateur. Pas besoin de serveur le projet via un serveur local !

## Aller plus loin : servir les présentations sur un dépot Github avec Github Pages

- creer un dépot sur Github dédié a heberger les présentations compilées (pas les sources)
- 



## Ressources

- [Use reveal-md to generate multiple slides and host them on GitHub Page](https://blog.hanklu.tw/post/2021/use-reveal-md-to-generate-multiple-slides-and-host-them-on-github-page/)
