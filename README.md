# Notes Paris Web 2015

## Le dev front à mach 1 au quotidien

[Présentation de la conférence](http://www.paris-web.fr/2015/conferences/le-dev-front-a-mach-1-au-quotidien.php) - [Slides](http://tdd.github.io/parisweb-2015-talk/#/)

* Se documenter sur les devtools du navigateur qu'on utilise, voire sur les devtools de tous les navigateurs
* Ne pas hésiter à utiliser le live coding intégré dans les devtools, ils permettent souvent de sauvegarder les modifications maintenant
* Utiliser BrowserSync pour appliquer automatiquement les modifications qu'on fait dans un éditeur hors devtools
* Utiliser Gulp ou Webpack, les deux sont bons mais Webpack a le vent en poupe en ce moment
* Se mettre à ES6 et au système de modules qu'il propose

## La crypto pour les devs : petit état des lieux des outils d'aujourd'hui et des techniques de demain

[Présentation de la conférence](http://www.paris-web.fr/2015/conferences/la-crypto-pour-les-devs-petit-etat-des-lieux-des-outils-daujourdhui-et-des-techniques-de-demain.php) - [Slides](http://talks.m4dz.net/crypto-pour-les-devs/#/)

* Le plus important c'est la clé, l'algo on s'en fout
* Ne pas utiliser des combinaisons de fonctions de hashage (ie. `md5(sha1($password))`), c'est pas plus sécurisé qu'une seule fonction de hashage
* Utiliser un sel unique (en utilisant des vraies techniques de génération de chaînes aléatoires)
* Le sel doit être unique PAR MOT DE PASSE sinon ça sert à rien, puisque en appliquant le même sel sur le même mot de passe pour 2 utilisateurs, on crée une répétition, et donc une faille
* Le chiffrement synchrone c'est un peu pourrit car la même clé chiffre et déchiffre, donc si on se la fait voler, le mec fait ce qu'il veut
* Il faut utiliser le chiffrement asynchrone (RSA)
* Clé privée : déchiffrement / Clé publique : chiffrement
* La signature est le fait de chiffrer avec sa clé privée. On peut donc déchiffrer avec la clé publique. Il n'y a pas de sécurité, mais ça permet d'identifier de manière certaine l'auteur
* L'initiative [Let's Encrypt](https://letsencrypt.org/) va permettre d'obtenir des certificats gratuitement
* Dans le navigateur, il existe l'API WebCrypto
* C'est un Working Draft, et la doc est très obscure
* `window.crypto` / `window.crypto.subtle`
* `window.crypto.subtle.encrypt` + nom de l'algo, clé publique, data
* Manipule uniquement des données binaires, il faut donc passer son temps à convertir de et vers du binaire
* Tous les algos de chiffrement ne sont pas implémentés dans tous les navigateurs, c'est autant la misère que pour les codec pour les API Audio/Video

## Il est beau il est frais mon RGAA 3

[Présentation de la conférence](http://www.paris-web.fr/2015/conferences/il-est-beau-il-est-frais-mon-rgaa-3.php) - [Slides](#)

* Référentiel Général d'Accessibilité pour les Administrations : [spécification](https://references.modernisation.gouv.fr/rgaa-3-0)
* `role="group"` sur `<figure>` pour lier la légende (`<figcaption>`) à l'image (`<img>`) il faut que le `alt` de l'`<img>` soit la même chose que le contenu du `<figcaption>`
* `<svg>` décoratif ou porteur de sens
* Pour un `<svg>` porteur de sens, `<text>` dans le <svg> avec une opacity à 0. Les autres éléments en `aria-hidden="true"`
* Pour un `<svg>` décoratif, `aria-hidden="true"` directement sur le `<svg>`
* Pour les médias, alternative à l'extérieur de `<object>` car les lecteurs d'écrans ne savent pas aller voir à l'intérieur de `<object>` pour récupérer l'alternative
* Pour l'audio, Able Player et MFP video player sont les plus compatibles RGAA, mais ils posent plein d'autres soucis (pas responsive)
* JS : plus obligé d'avoir des alternatives
* Tester la restitution dans les lecteurs d'écrans (NVDA, Jaws...)
* Il faut respecter les [design pattern ARIA](http://www.w3.org/TR/wai-aria-practices/) (modal, accordion...)
* Utiliser les éléments sémantiques HTML et y ajouter les roles ARIA
* Ajouter des liens d'accès rapide à la tabulation au clavier
* Ajout des roles `heading`, `list`, `listitem` pour les cas où ces concepts ne seraient pas représentées par la balise adaptée semantiquement (`<hx>`, `<(u|o)l>`, `<li>`)
* Plus le droit d'utiliser le px pour le font-size
* Pas d'attribut `title` vide ou identique à l'intitulé des liens
* Indiquer "erreur de saisie" dans le `<title>` de la page
* Pas d'attribut `summary` sur les table, mettre le résumé dans le `<caption>`
