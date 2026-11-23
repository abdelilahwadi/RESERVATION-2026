# Projet Réservations

Réservations est un projet d’intégration qui vise à centraliser le catalogue de spectacles et la réservation de places pour une société de production. Un spectacle peut avoir plusieurs représentations, à des dates ou dans des salles différentes. La réservation porte sur une représentation précise, avec un nombre de places et un tarif.

## Fonctionnalités prévues

| Public | Fonctionnalités |
| --- | --- |
| Visiteurs | Rechercher, filtrer et trier les spectacles, puis consulter les lieux et les prochaines représentations. |
| Membres | Réserver des places, consulter leurs réservations, modifier leur profil et publier un avis sur un spectacle auquel ils ont assisté. |
| Administrateurs | Gérer le catalogue dans une interface sécurisée, importer et exporter des données CSV et mettre à jour le catalogue depuis une API tierce. |
| Affiliés | Consulter les données du catalogue via une API authentifiée, selon leur niveau d’accès Free, Starter ou Premium. |
| Critiques de presse | Soumettre un article ou un lien pour publication. |
| Producteurs | Consulter les statistiques de vente de leurs spectacles et modérer les avis et les critiques associés. |

Le projet prévoit également un flux RSS consacré aux prochaines représentations.

## État du projet

Le dépôt contient la base technique du projet avec Laravel 12, SQLite, Blade, Tailwind CSS et Vite. La compilation des ressources front-end a été vérifiée. L’application affiche actuellement la page d’accueil de démarrage. La prochaine étape consiste à créer la liste des artistes et leurs fiches, avant de développer le catalogue et les réservations.

Le [plan de réalisation](PROJECT-CHECKLIST.md) détaille les itérations et les vérifications à effectuer avant la remise.

## Démarrage local

Le projet nécessite PHP 8 à partir de la version 8.2 avec l’extension `pdo_sqlite`, Composer et npm. Pour Node.js, utilisez la version 20 à partir de 20.19, ou la version 22.12 ou ultérieure. Les commandes suivantes s’exécutent dans PowerShell, à la racine du dépôt.

```powershell
composer install

if (-not (Test-Path .env)) {
    Copy-Item .env.example .env
    php artisan key:generate
}

if (-not (Test-Path database/database.sqlite)) {
    New-Item -ItemType File database/database.sqlite | Out-Null
}

php artisan migrate
npm ci
npm run build
php artisan serve
```

L’application est accessible à l’adresse [http://127.0.0.1:8000](http://127.0.0.1:8000). Pour lancer les tests, utilisez `php artisan test`.
