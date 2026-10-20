# ARMOIRE — Frontend du coffre-fort électronique

Interface web Angular du projet **ARMOIRE**, un prototype de coffre-fort électronique conçu pour la gestion de documents sensibles liés aux finances publiques maliennes.

Projet réalisé dans le cadre d’un stage en **cybersécurité et développement sécurisé chez ANKA Digital**.

## Objectif

L’interface permet aux utilisateurs d’interagir avec le coffre-fort : déposer des documents, consulter les fichiers auxquels ils ont accès et suivre leurs candidatures.

Elle propose également un espace d’administration pour la validation des utilisateurs et la gestion des offres.

## Architecture du projet

L’application repose sur trois composants :

| Composant | Rôle |
| --- | --- |
| Frontend Angular | Interface utilisateur et communication avec l’API |
| Backend Spring Boot | Logique métier, authentification, autorisations et opérations cryptographiques |
| PostgreSQL | Persistance des données gérées par le backend |

Le frontend et le backend sont maintenus dans deux dépôts distincts.

**Backend et documentation des mécanismes de sécurité :** [ARMOIRE-backend](https://github.com/sidiprograms11/ARMOIRE-backend)

## Technologies

- **Angular** : développement de l’application web.
- **TypeScript** : logique de l’interface et intégration des services.
- **HTML / CSS** : structure et présentation des pages.
- **API REST** : échanges avec le backend Spring Boot.
- **JWT** : intégration avec l’authentification fournie par le backend.

## Organisation fonctionnelle

### Authentification

- Inscription et connexion.
- Parcours de demande de validation d’identité.
- Accès aux espaces correspondant au profil de l’utilisateur.

### Espace utilisateur

- Accès au coffre personnel.
- Dépôt de documents.
- Consultation des documents autorisés.
- Consultation des offres et dépôt de candidatures.
- Suivi des candidatures.

### Espace administrateur

- Consultation des demandes d’inscription.
- Validation ou refus des demandes.
- Gestion des offres.
- Consultation des candidatures et des documents accessibles.

## Sécurité : rôle du frontend

Le frontend assure l’interaction avec les fonctionnalités de sécurité exposées par l’API.

L’affichage des pages et des actions selon le profil utilisateur facilite la navigation, mais **les autorisations doivent être vérifiées par le backend pour chaque opération sensible**.

Les responsabilités sont réparties ainsi :

| Frontend | Backend |
| --- | --- |
| Présenter les formulaires de connexion | Vérifier les identifiants |
| Transmettre les requêtes authentifiées | Valider les JWT et les permissions |
| Afficher les documents autorisés | Contrôler les accès avant restitution |
| Présenter les actions métier | Exécuter les traitements et les opérations cryptographiques |

Le chiffrement AES / RSA, la gestion des clés privées et la signature numérique relèvent du backend.

Aucun secret serveur ne doit être intégré au code Angular : les ressources livrées au navigateur sont accessibles à l’utilisateur.

## Contexte de réalisation

ARMOIRE s’inscrit dans la continuité d’une première application Angular / Spring Boot / PostgreSQL développée, sécurisée et déployée durant le stage.

L’évolution vers le coffre-fort a conduit à organiser l’interface autour des parcours d’authentification, d’administration et de gestion des documents.

## Statut et limites

Cette application est un **prototype réalisé en stage**.

- Le processus de vérification d’identité repose sur un service simulé dans le prototype.
- La sécurité des documents dépend des contrôles et des mécanismes mis en œuvre côté backend.
- Le projet ne revendique pas de certification ni de validation pour un usage en production.

## Améliorations envisagées

- Ajouter une démonstration visuelle avec des données fictives.
- Documenter le lancement local et la configuration de l’URL de l’API.
- Renforcer les tests des parcours de connexion, de dépôt et de consultation.
- Améliorer l’affichage des erreurs et la gestion de l’expiration de session.
- Vérifier l’accessibilité et l’adaptation aux différentes tailles d’écran.

## Compétences mobilisées

Développement Angular · TypeScript · Intégration d’API REST · Authentification JWT · Interfaces selon les rôles · Conception de parcours utilisateur · Collaboration frontend / backend
