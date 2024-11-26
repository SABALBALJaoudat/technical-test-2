# Technical test

## Introduction

Fabien just came back from a meeting with an incubator and told them we have a platform “up and running” to monitor people's activities and control the budget for their startups !

All others developers are busy and we need you to deliver the app for tomorrow.
Some bugs are left and we need you to fix those. Don't spend to much time on it.

We need you to follow these steps to understand the app and to fix the bug :

- Sign up to the app
- Create at least 2 others users on people page ( not with signup )
- Edit these profiles and add aditional information
- Create a project
- Input some information about the project
- Input some activities to track your work in the good project

Then, see what happens in the app and fix the bug you found doing that.

## Then

Time to be creative, and efficient. Do what you think would be the best for your product under a short period.

### The goal is to fix at least 3 bugs and implement 1 quick win feature than could help us sell the platform

## Setup api

- cd api
- Run `npm i`
- Run `npm run dev`

## Setup app

- cd app
- Run `npm i`
- Run `npm run dev`

## Finally

Send us the project and answer to those simple questions :

- What bugs did you find ? How did you solve these and why ?

  => Pour Sign In, le message "Wrong login" est toujours affiché.
  Cause : Le champ username n'était pas correct à cause d'une transformation en minuscules dans utils/auth.js.

  => Lors de la création d'un utilisateur dans Sign Up, aucune erreur n'est affichée si le mot de passe est invalide.
  Cause : return res.status(200) est utilisé au lieu de return res.status(400) dans utils/auth.js.

  => Lors de la création d'un utilisateur depuis la page People, le nom de l'utilisateur est toujours vide ("").
  Cause : Dans user/list.js, le champ name n'était pas initialisé dans le preview de la requete user. De plus, username était envoyé en paramètre dans values de user/list.js, alors que dans models/user.js, c'est le champ name qui était attendu. Par conséquent, username n'était pas pris en compte dans la requête.

  => Update d'un user ne donne rien.
  Cause : Dans user/view.js, le bouton update était onChange et pas onClick.

  => Bug de crash pour project.name dans project/view.js.
  Cause : Le champ project.name peut être undefined, ce qui provoque un crash. (ou sinon n'écrire que project.name est possible).

  => Quand on clique sur Edit pour un projet, un loading tourne à l'infini avec une erreur 500.
  Changer dans controllers/project.js find par findOne.

  => Quand on clique sur My account, on a toujours le menu déroulant ouvert.

- Which feature did you develop and why ?

  => Ajout d'un bouton pour retourner à la page de connexion.
  Raison : Il est nécessaire de pouvoir revenir à la page de connexion afin de créer un nouvel utilisateur.
  Dans mon cas, j'ai souvent eu besoin de faire des allers-retours entre les pages pour comprendre la cause des bugs de Sign In et Sign Up.

  => Possibilité de cliquer en dehors du menu déroulant de l'avatar pour le fermer.

- Do you have any feedback about the code / architecture of the project and what was the difficulty you encountered while doing it ?
  Très bien organisé, je me suis facilement retrouvé dans l'arborescence du projet et j'ai pu comprendre rapidement le fonctionnement de l'application.
  J'ai cependant rencontré quelques difficultés, car je n'utilise pas énormément le framework React et Node.js. J'ai donc eu besoin de prendre un peu de temps pour m'adapter.
