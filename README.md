🧑‍💻 Projet SOA – Gestion des Personnes
📌 Présentation du projet

Ce projet est une application web de gestion des personnes.
L’objectif principal est de consommer des services REST développés en Java afin de gérer des personnes, notamment :

l’ajout

la modification

la suppression

l’affichage des données

🏗️ Architecture du projet

Ce projet est composé de trois parties principales :

Frontend : React, HTML, CSS, JavaScript et Bootstrap

Backend : Java avec JAX-RS (Jersey)

Base de données : MySQL

Cette architecture permet une séparation claire des responsabilités entre l’interface utilisateur, la logique métier et la base de données.

⚙️ Backend – Java (JAX-RS / Jersey)

Le backend représente la partie serveur de l’application.
Il est organisé en plusieurs packages Java, afin de respecter une architecture en couches, ce qui rend le projet plus clair, structuré et maintenable.

📦 Package com.person.config

Ce package contient la configuration générale du backend.
Il inclut notamment un filtre CORS, qui permet au frontend React de communiquer avec le backend même si les deux applications utilisent des ports différents.

📦 Package com.person.model

Le package model contient les entités du projet.
La classe Person représente la table person dans la base de données.

Elle définit les attributs principaux :

nom

email

âge

téléphone

📦 Package com.person.dao

Le package DAO (Data Access Object) est responsable de l’accès à la base de données.
Il contient toutes les opérations CRUD :

findAll : récupérer toutes les personnes stockées dans la base de données

findById : récupérer une personne à partir de son identifiant

findByName : rechercher des personnes par leur nom

save : enregistrer une nouvelle personne

update : modifier une personne existante

delete : supprimer une personne à partir de son ID

📦 Package com.person.service

Ce package joue le rôle d’un intermédiaire entre le contrôleur REST et le DAO.
Il contient la logique métier de l’application et permet de mieux organiser le code.

📦 Package com.person.router

Ce package contient les services REST.
Il expose plusieurs endpoints HTTP permettant au frontend de communiquer avec le backend via des requêtes JSON.

Annotations principales :

@Path("/persons") : définit l’URL de base de l’API

@Consumes(MediaType.APPLICATION_JSON) : le backend reçoit des données JSON

@Produces(MediaType.APPLICATION_JSON) : le backend renvoie des données JSON

Fonctionnalités :

récupérer toutes les personnes

récupérer une personne par ID

rechercher une personne par nom

ajouter une personne

modifier une personne

supprimer une personne

🗄️ Base de données

La base de données utilisée dans ce projet est MySQL.

- Nom de la base de données : `person_db`
- SGBD : MySQL
- ORM utilisé : Hibernate (via JPA)

La connexion entre l’application Java et la base de données est configurée dans le fichier `persistence.xml`.  
Hibernate permet de gérer automatiquement les entités Java et de synchroniser la structure de la base de données avec les classes du projet.


🌐 Configuration Web

Le fichier web.xml est le fichier principal de configuration de l’application web.
Il permet :

de déclarer le servlet Jersey

de définir le mapping des services REST

d’activer le filtre CORS

Le filtre CORS autorise la communication entre le frontend React et le backend Java.

🎨 Frontend – React

Le frontend est développé avec React et permet à l’utilisateur d’interagir avec le backend REST.

🔹 Gestion des états

Deux états principaux sont utilisés :

persons : contient la liste des personnes récupérées depuis le backend

form : contient les données du formulaire pour l’ajout ou la modification

🔹 Chargement des données

Une requête GET est envoyée au backend afin de récupérer toutes les personnes et les afficher dans un tableau.

🔹 Communication avec le backend (Fetch API)

La communication entre le frontend React et le backend Java REST se fait à l’aide de Fetch API.
Fetch permet d’envoyer des requêtes HTTP vers les services REST et de récupérer les réponses au format JSON.

Les méthodes HTTP utilisées sont :

GET : pour récupérer la liste des personnes

POST : pour ajouter une nouvelle personne

PUT : pour modifier une personne existante

DELETE : pour supprimer une personne

🔹 Formulaire

Le formulaire permet d’ajouter ou de modifier une personne.
Les champs sont liés à l’état React et sont mis à jour automatiquement lors de la saisie.

🔹 Ajout et modification

Lors de la soumission du formulaire :

une requête POST est utilisée pour l’ajout

une requête PUT est utilisée pour la modification

Les données sont envoyées au backend au format JSON.

🔹 Suppression

Chaque personne peut être supprimée via un bouton.
Une confirmation est demandée avant l’envoi de la requête DELETE vers le backend.

🎨 Interface utilisateur

L’interface utilisateur est réalisée avec Bootstrap, ce qui permet :

un design simple et clair

une interface responsive

une meilleure organisation des formulaires et tableaux.