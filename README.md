# Enroller by ViewPay

Ce guide a pour objectif de vous guider dans la mise en place du module JS Enroller de ViewPay dans votre site web.

## Chargement du Javascript
```html
<script type="text/javascript" src="https://cdn.jokerly.com/scripts/Enroller/VPEnroller.js?VPEnroller_init"></script>
```
Le fichier VPEnroller.js est le seul fichier nécessaire à appeler, celui-ci fera ensuite le travail afin d'appeler les éléments nécessaires pour un moment donné.
Ces fichiers sont installés sur notre CDN afin de vous garantir d'avoir toujours la dernière version.

Le paramètre VPEnroller_init (après le ?) réfère au nom de la fonction d'initialisation que vous allez définir plus bas.

NB: Il faut placer le script le plus haut possible dans la page afin d’optimiser son temps de chargement.

## Initialisation + Envoi de paramètres

Les fonctions JS vont permettre au paywall de s'afficher correctement et de faire le parcours nécessaire à celui-ci.
```html
<script>
                var enroller = null;
                function VPEnroller_init(){
                        enroller = new VPEnroller({
                                        site_id: '65b94a697eb8bcd1', //exemple
                                        zone : 'A6', //exemple
                                        source : 'SEO', //exemple
                                        frequence : 1 //exemple
                        });
                }
        </script>
```

Le paramètre site_id est celui de votre compte ViewPay. Si vous ne l'avez pas encore, veuillez nous contacter.

Le paramètre zone correspond au code région / département (?) / postal (?) de l'utilisateur.

Le paramètre source permet de transmettre à Enroller l'information de provenance de l'utilisateur : SEO/RS/Direct...

Le paramètre frequence permet de nous transmettre votre information de fréquence d'utilisation de l'utilisateur (nombre de jours actifs, nombre de sessions, etc).

## Div pour afficher le contenu du pied d'article + ViewPay

```html
<div id="VPEnroller">
</div>
<div id="cadreJokerlyADS">
</div>
```
Ce div doit être placé dans votre pied d'article. Il affichera en fonction des règles définies pour Enroller le bon scénario de pied d'article.
