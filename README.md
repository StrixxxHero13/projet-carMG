# FleetManager - Système de Gestion de Véhicules

Un système complet de gestion de flotte de véhicules construit avec React, Node.js et PostgreSQL. Cette application aide à gérer les flottes de véhicules, suivre les calendriers de maintenance, surveiller l'inventaire des pièces, fournit des alertes automatisées pour la maintenance préventive, et inclut une validation intelligente du statut des véhicules.

## 🚗 Fonctionnalités

### Gestion des Véhicules
- Suivre tous les véhicules de votre flotte
- **Validation Intelligente du Statut** : Évaluation automatique du statut opérationnel des véhicules
- Surveiller le statut des véhicules (opérationnel, maintenance due, en réparation)
- Stocker les informations détaillées des véhicules (plaque, modèle, marque, année, kilométrage)
- Mises à jour en temps réel basées sur l'historique de maintenance et les alertes
- Détails complets des véhicules avec statistiques de maintenance

### Planification de Maintenance
- Planifier et suivre les activités de maintenance
- Historique complet de maintenance pour chaque véhicule
- Suivi des coûts et de la durée
- Attribution des techniciens
- Rappels automatisés de maintenance

### Inventaire des Pièces
- Catalogue complet des pièces
- Surveillance des niveaux de stock
- Alertes de stock faible
- Suivi de l'utilisation des pièces à travers les activités de maintenance
- Gestion des coûts

### Alertes Intelligentes
- Notifications automatisées de maintenance due
- Avertissements de maintenance en retard
- Alertes de stock faible pour les pièces
- Système d'alertes basé sur les priorités

### Assistant de Chat Interactif
- Poser des questions sur votre flotte
- Obtenir des mises à jour instantanées du statut des véhicules
- Vérifier les calendriers de maintenance
- Consulter l'inventaire des pièces
- Statistiques rapides de la flotte
- Réponses intelligentes avec suggestions de secours

### Recherche et Filtrage Avancés
- **Recherche Intelligente de Véhicules** : Recherche en direct avec navigation vers les pages pertinentes, résultats détaillés et indices visuels clairs
- **Filtrage Complet de l'Historique** : Filtrer par véhicule, type de maintenance et plages de dates
- **Validation en Liste de Tâches** : Les véhicules disparaissent de la liste de validation une fois opérationnels
- **Fonctionnalité de Réinitialisation** : Effacement rapide des filtres

### Vue d'Ensemble du Tableau de Bord
- Statistiques de la flotte en un coup d'œil
- Alertes et notifications récentes
- Vue d'ensemble du calendrier de maintenance
- Résumé de l'inventaire des pièces

## 🛠 Stack Technique

- **Frontend** : React 18, TypeScript, Tailwind CSS, composants Radix UI
- **Backend** : Node.js, Express.js, TypeScript
- **Base de Données** : PostgreSQL avec Drizzle ORM
- **Outils de Build** : Vite pour le développement et la production
- **Framework UI** : bibliothèque de composants shadcn/ui
- **Gestion d'État** : TanStack Query pour l'état serveur

## 🚀 Démarrage Rapide

**Important** : Ce projet nécessite une configuration technique. Suivez le guide complet dans `SETUP_GUIDE.md` pour des instructions détaillées.

### Prérequis
- Node.js (version LTS)
- Base de données PostgreSQL
- Git (optionnel)

### Installation
1. Téléchargez ou clonez ce dépôt
2. Ouvrez le fichier `SETUP_GUIDE.md`
3. Suivez exactement les instructions étape par étape
4. Le guide couvre tout, de l'installation des dépendances au lancement de l'application

## 📁 Structure du Projet

```
FleetManager/
├── client/                 # Application frontend React
│   ├── src/
│   │   ├── components/     # Composants UI réutilisables
│   │   ├── pages/          # Pages de l'application
│   │   ├── lib/           # Utilitaires et configurations
│   │   └── hooks/         # Hooks React personnalisés
├── server/                # Backend Express.js
│   ├── routes.ts          # Définitions des routes API
│   ├── storage.ts         # Opérations de base de données
│   └── db.ts             # Connexion à la base de données
├── shared/                # Types TypeScript partagés
│   └── schema.ts          # Schéma et types de base de données
├── SETUP_GUIDE.md        # Instructions complètes d'installation
└── package.json          # Dépendances et scripts
```

## 🎯 Utilisation

Après l'installation, l'application fournit :

1. **Tableau de Bord** - Vue d'ensemble de votre flotte entière avec statistiques en temps réel
2. **Véhicules** - Gérer les véhicules individuels et leur statut avec vues détaillées
3. **Maintenance** - Planifier et suivre les activités de maintenance avec suivi des coûts
4. **Pièces** - Surveiller l'inventaire et les niveaux de stock avec alertes automatisées
5. **Historique** - Historique complet de maintenance avec filtrage avancé
6. **Validation** - Validation dédiée du statut des véhicules avec interface en liste de tâches
7. **Chat** - Assistant interactif pour les requêtes rapides de gestion de flotte

## 📊 Données d'Exemple

L'application inclut des données d'exemple pour démontrer les fonctionnalités :
- 3 véhicules d'exemple (différentes marques et statuts)
- Inventaire de pièces avec divers niveaux de stock
- Enregistrements et historique de maintenance
- Alertes et notifications actives

## 🔧 Configuration

L'application utilise des variables d'environnement pour la configuration. Voir `.env.example` pour les paramètres requis :

- `DATABASE_URL` - Chaîne de connexion PostgreSQL
- `NODE_ENV` - Environnement (development/production)
- `PORT` - Port de l'application (par défaut : 5000)

## 📖 Documentation

- `SETUP_GUIDE.md` - Instructions complètes d'installation pour n'importe quel ordinateur
- `GITHUB_UPLOAD_GUIDE.md` - Instructions pour partager ce projet
- `replit.md` - Documentation de l'architecture technique

## 🆘 Dépannage

Les problèmes courants et leurs solutions sont couverts dans le fichier `SETUP_GUIDE.md`. La plupart des problèmes sont liés à :
- Problèmes de connexion à la base de données
- Dépendances manquantes
- Conflits de ports
- Configuration d'environnement

## 🎓 Projet Éducatif

Ce projet a été créé comme un devoir scolaire et démontre :
- Développement web full-stack
- Conception et gestion de base de données
- Développement d'API RESTful
- Patterns React modernes
- Utilisation de TypeScript partout
- Organisation professionnelle du code

Parfait pour apprendre les pratiques modernes de développement web !

## 📄 Licence

Ce projet est créé à des fins éducatives.