# Cloud Pool Manager — Documentation

**Cloud Pool Manager** déploie et gère des **pools de machines virtuelles pour l'enseignement** :
un enseignant crée un pool pour son cours, la plateforme provisionne une flotte de VMs identiques
sur un cloud OpenStack, et chaque étudiant ouvre **JupyterLab**, **VS Code** ou un terminal
directement dans son navigateur.

Cette documentation décrit le fonctionnement interne, composant par composant.

## Sommaire

- [Architecture générale](01-architecture.md) — les trois tiers, gRPC, les deux projets OpenStack
- [Authentification & connexion](02-authentification.md) — OIDC, GitHub, SSH, sessions
- [Création des pools](03-creation-pools.md)
- [Provisionnement & réconciliation](04-provisionnement-reconciliation.md) — file de jobs, boucle auto-cicatrisante
- [Attribution d'une VM à un étudiant](05-attribution-etudiants.md)
- [Accès aux VMs](06-acces-vm.md) — reverse-proxy, JupyterLab, VS Code, terminal
- [Notation nbgrader](07-nbgrader-notation.md)
- [Snapshots & images](08-snapshots-images.md) — golden images
- [Développement & exploitation](09-developpement-exploitation.md)
- [Observabilité](10-observabilite.md) — Prometheus, Loki, Grafana, OpenTelemetry
- [Intégration Moodle](11-moodle.md)

!!! note "Code source"
    La plateforme vit dans le dépôt [vm-pool-managers](https://github.com/cloud-pool-managers/vm-pool-managers).
