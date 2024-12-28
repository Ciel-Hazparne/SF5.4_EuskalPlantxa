<h2 align="center">Projet Euskal Plantxa 2023</h2>
<h3 align="center">Partie d'Antoine (Site Web). Ilyas étant chargé de la partie C++/Arduino</h3>

<p align="center">
symfony server:start
 website to remotely manage a camping pantxa
</p>


![Language](https://img.shields.io/badge/language-php-797db2.svg?style=flat)
![Language](https://img.shields.io/badge/language-symfony-000000.svg?style=flat)
![Language](https://img.shields.io/badge/language-twig-bccf28.svg?style=flat)
![Language](https://img.shields.io/badge/language-javascript-efd81d.svg?style=flat)

## Install & Run Project

   ```sh
    $ git clone [ssh]
    $ composer install && npm install && npm run build
    $ // edit db url in .env and create database
    $ symfony console doctrine:migration:migrate // create all tables
    $ symfony console doctrine:fixtures:load // execute seeders
    $ symfony server:start
   ```
# Présentation du projet Euskal Plantxa


## 1.1 Présentation de l’entreprise

L’entreprise **Euskal Plantxa** vend ou loue des plantxas dans différents campings pendant la saison estivale.  
Dans certains campings haut de gamme, chaque mobil-home a sa propre plantxa.  

---

## 1.2 Analyse de l’existant

Actuellement :  
- L’utilisation de la plantxa n’est pas facturée, ou un forfait est inclus dans le prix de la location.  
- Dans les campings, l'utilisation des plantxas est possible grâce à un forfait inclus dans le prix de la location, permettant de créditer un temps de cuisson particulier.  
- Les clients sont obligés de passer à l'accueil s’ils veulent modifier leur forfait plantxa.  

---

## 1.3 Expression des besoins

Le système actuel présente plusieurs limites :  
- Aucun suivi possible de l’utilisation, ni indication de panne (ex. fin de gaz).  
- Pas de facturation de l’utilisation.  
- Facturation uniquement au forfait, ce qui renchérit le prix de base.  

### Objectif :  
Mettre en place un système avec les caractéristiques suivantes :  

1. **Gestion initiale** :  
   - À l’attribution d’un emplacement à un nouveau client, son crédit temps plantxa est mis à zéro.  

2. **Déclenchement et utilisation** :  
   - Le client peut lancer une cuisson en appuyant sur un bouton-poussoir (BP) relié à un microcontrôleur embarqué dans ou à côté de la plantxa.  
   - L’électrovanne gaz de la plantxa est ouverte pour autoriser la cuisson.  
   - Le crédit temps est compté.  

3. **Surveillance du temps de cuisson** :  
   - Le client peut surveiller le temps :  
     - Soit sur un afficheur à proximité de la plantxa.  
     - Soit grâce à son téléphone portable en scannant un QR Code affiché près de la plantxa (*option*).  

4. **Fin de cuisson** :  
   - Le client appuie sur un bouton-poussoir pour fermer l’électrovanne de gaz.  
   - Le temps de cuisson est envoyé à la base de données (BDD) et cumulé au temps précédemment consommé.  

5. **Facturation** :  
   - En fin de séjour, le client est facturé pour sa consommation réelle.  

6. **Analyse des données** :  
   - Une base de données centrale permet d’analyser les données d’utilisation des plantxas.  
   - Différents graphiques seront disponibles pour analyser les données.  
