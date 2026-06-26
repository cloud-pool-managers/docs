# CloudPoolManager — présentation

CloudPoolManager permet à un **enseignant** de provisionner automatiquement, en quelques clics,
des **machines virtuelles de TP** (sur l'infrastructure OpenStack de l'X) et de les **attribuer
à ses étudiants**, avec un environnement **JupyterLab** prêt à l'emploi et la **correction
automatisée** des rendus (nbgrader).

## Ce que ça fait

- **Pools de VMs par cours** : l'enseignant crée un « pool » (image, taille, nombre de machines) ;
  les VMs sont provisionnées et maintenues automatiquement.
- **Accès étudiant simple** : l'étudiant se connecte (GitHub, ou compte Moodle/établissement),
  rejoint son cours et obtient une VM avec **JupyterLab** dans le navigateur + un **terminal web**
  (Guacamole). Aucune installation locale.
- **Notation (nbgrader)** : distribution des sujets, collecte des copies, **notation automatique**,
  correction manuelle, export CSV des notes.
- **Suivi temps réel** : l'enseignant voit qui est connecté sur quelle machine.

## Le besoin vis-à-vis de Moodle / de la base de synchro

L'objectif est d'**éviter la double saisie** : récupérer la **liste des étudiants** d'un cours pour
les inscrire automatiquement aux VMs, et proposer la connexion via leur compte établissement.

**Accès souhaité : LECTURE SEULE.** Données nécessaires, limitées aux cours de l'**X** :

- la **liste des cours** ;
- les **inscriptions** à ces cours (enseignants + élèves) : identité minimale (**nom, email/login**) ;
- (optionnel) les **groupes** et inscriptions aux groupes.

Aucune écriture n'est requise. *(La remontée des notes vers Moodle existe mais reste optionnelle et
nécessiterait un accès en écriture ; à défaut, l'enseignant exporte un CSV et l'importe lui-même.)*

## Architecture (résumé)

Frontend web (SvelteKit) → Control Center (Go) → Microservice OpenStack (Go) → VMs.
Identité par OIDC (SSO), GitHub, ou Moodle. Code et documentation détaillée disponibles
(dossier `doc/`).
