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
                                        site_id: '65b94a697eb8bcd1', //votre ID ViewPay
                                        zone : '14', //numéro de département sur 2 caractères
                                        source : 'SEO', //source ou referrer
                                        frequence : 1 //fréquence de l'utilisateur
                        });
                }
</script>
```

Le paramètre site_id est celui de votre compte ViewPay. Si vous ne l'avez pas encore, veuillez nous contacter.

Le paramètre zone correspond au code département de l'utilisateur.

Le paramètre source permet de transmettre à Enroller l'information de provenance de l'utilisateur : SEO/RS/Direct...

Le paramètre frequence permet de nous transmettre votre information de fréquence d'utilisation de l'utilisateur (nombre de jours actifs, nombre de sessions, etc).

## Div pour afficher le contenu du pied d'article + ViewPay

```html
<div id="VPEnroller">
  </div>
<div id="VPmodal">
  <div id="cadreJokerlyADS">
  </div>
</div>
```
Ces div doivent être placés dans votre pied d'article. Le div VPEnroller affichera en fonction des règles définies pour Enroller le bon scénario de pied d'article, et le div cadreJokerlyADS est nécessaire pour l'affichage du module publicitaire ViewPay.

## CSS des éléments d'Enroller + ViewPay 

```css
#cadreJokerlyADS{
	margin: auto;
	top: 0;
	right: 0;
	left: 0;
	position: fixed;
	bottom: 0;
	width: 650px !important;
	height: 450px !important;
	z-index:999999 !important;
}

Le z-index est nécessaire à la visibilité de la publicité. Il est impératif de le monter si nécessaire si une frame/bannière/autre est au dessus du nôtre.
Ceci est obligatoire afin de garantir de CPM élevé.
```

Pour les sites Mobiles/Tablettes : exploiter le responsive

Pour votre site mobile, il est préférable d’utiliser tout l’espace vertical disponible en ouvrant l’iframe en 100% width et height, ou en spécifiant la taille maximale que vous pouvez nous offrir.

Les balises média suivantes seront à ajouter à votre page CSS pour permettre aux personnes sur mobile de profiter pleinement de l’interface ViewPay:

```css
@media screen and (max-width: 600px){
	#cadreJokerlyADS{
	width:100% !important;
	height:100% !important;
	margin-top:0;
	}
}
@media screen and ((min-width: 601px) and (max-width: 1024px)){
	#cadreJokerlyADS{
	width:100% !important;
	height:100% !important;
	margin-top:0;
	margin-left:0;
	}
}
```

Pour le fond noir :
```css
#VPmodal{
    width: 100%;
    height: 100%;
    display: none;
    position: fixed;
    background-color: rgba(0, 0, 0, 0.9);
    z-index: 1000;
}
```
