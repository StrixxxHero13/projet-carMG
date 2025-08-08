# FleetManager - Guide d'Installation Complet

Ce guide vous aidera à installer le système de gestion de véhicules FleetManager sur votre ordinateur depuis le début. Suivez chaque étape attentivement, et vous aurez une application fonctionnelle à la fin.

## Ce que Vous Obtiendrez

Après avoir suivi ce guide, vous aurez :
- Un système complet de gestion de véhicules fonctionnant sur votre ordinateur
- Une interface web moderne pour gérer les véhicules, pièces et maintenance
- Système intelligent de validation du statut des véhicules
- Capacités avancées de recherche et filtrage
- Un assistant de chat pour aider avec la gestion de flotte
- Une base de données locale avec des données d'exemple pour commencer

## Prérequis

Vous devez avoir des connaissances de base sur :
- Comment ouvrir un terminal/invite de commande
- Comment copier et coller des commandes
- Comment télécharger des fichiers depuis internet

## Étape 1 : Installer Node.js

Node.js est l'environnement d'exécution qui alimente cette application.

### Pour Windows :
1. Allez sur https://nodejs.org/
2. Téléchargez la version "LTS" (recommandée pour la plupart des utilisateurs)
3. Lancez l'installateur et suivez l'assistant d'installation
4. Acceptez toutes les options par défaut

### Pour Mac :
1. Allez sur https://nodejs.org/
2. Téléchargez la version "LTS" pour macOS
3. Ouvrez le fichier .pkg téléchargé et suivez l'installateur
4. Acceptez toutes les options par défaut

### Pour Linux :
Ouvrez le terminal et exécutez :
```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Vérifier l'Installation :
Ouvrez le terminal/invite de commande et tapez :
```bash
node --version
npm --version
```

Vous devriez voir les numéros de version pour les deux commandes.

## Étape 2 : Installer la Base de Données PostgreSQL

PostgreSQL est le système de base de données qui stocke toutes vos données de véhicules.

### Pour Windows :
1. Allez sur https://www.postgresql.org/download/windows/
2. Téléchargez l'installateur pour Windows
3. Lancez l'installateur
4. **IMPORTANT** : Retenez le mot de passe que vous définissez pour l'utilisateur "postgres"
5. Acceptez le port par défaut (5432)
6. Acceptez le répertoire de données par défaut
7. Terminez l'installation

### Pour Mac :
1. Allez sur https://postgresapp.com/
2. Téléchargez Postgres.app
3. Déplacez-le dans le dossier Applications
4. Ouvrez Postgres.app
5. Cliquez sur "Initialize" pour créer un nouveau serveur

**Alternative pour Mac en utilisant Homebrew :**
```bash
brew install postgresql
brew services start postgresql
```

### Pour Linux (Ubuntu/Debian) :
```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

### Configurer la Base de Données :
Après l'installation, ouvrez le terminal et exécutez :

**Windows :**
```bash
# Ouvrir psql (vous serez invité à saisir le mot de passe que vous avez défini)
psql -U postgres -h localhost
```

**Mac/Linux :**
```bash
# Se connecter à PostgreSQL
sudo -u postgres psql
```

Une fois dans PostgreSQL, exécutez ces commandes :
```sql
-- Créer une base de données pour l'application
CREATE DATABASE fleetmanager;

-- Créer un utilisateur pour l'application
CREATE USER fleetuser WITH PASSWORD 'fleetpass123';

-- Accorder les permissions
GRANT ALL PRIVILEGES ON DATABASE fleetmanager TO fleetuser;

-- Quitter PostgreSQL
\q
```

## Étape 3 : Télécharger le Projet

Vous avez deux options :

### Option A : Télécharger le ZIP (Plus facile)
1. Allez sur la page GitHub de votre projet
2. Cliquez sur le bouton vert "Code"
3. Sélectionnez "Download ZIP"
4. Extrayez le fichier ZIP dans un dossier (par ex., Bureau/FleetManager)

### Option B : Cloner avec Git
Si vous avez Git installé :
```bash
git clone [URL_DE_VOTRE_PROJET]
cd [NOM_DU_DOSSIER_PROJET]
```

## Étape 4 : Configurer l'Application

1. Ouvrez le terminal/invite de commande
2. Naviguez vers votre dossier de projet :
```bash
cd chemin/vers/votre/dossier/FleetManager
```

3. Créez un fichier de configuration en copiant l'exemple :
```bash
# Windows
copy .env.example .env

# Mac/Linux
cp .env.example .env
```

4. Ouvrez le fichier `.env` dans un éditeur de texte et ajoutez :
```
DATABASE_URL=postgresql://fleetuser:fleetpass123@localhost:5432/fleetmanager
NODE_ENV=development
PORT=5000
```

**Note** : Si vous avez utilisé des identifiants différents à l'Étape 2, mettez à jour le DATABASE_URL en conséquence.

## Étape 5 : Installer les Dépendances du Projet

Dans votre terminal, assurez-vous d'être dans le dossier du projet et exécutez :

```bash
npm install
```

Cela téléchargera tous les packages nécessaires. Cela peut prendre quelques minutes.

## Étape 6 : Configurer les Tables de Base de Données

Exécutez cette commande pour créer toutes les tables nécessaires :

```bash
npm run db:push
```

Vous devriez voir un message de succès indiquant "Changes applied".

## Étape 7 : Démarrer l'Application

Maintenant vous pouvez démarrer l'application :

```bash
npm run dev
```

Vous devriez voir des messages comme :
```
serving on port 5000
```

## Étape 8 : Accéder à l'Application

1. Ouvrez votre navigateur web
2. Allez sur : http://localhost:5000
3. Vous devriez voir le tableau de bord FleetManager

## Ce que Vous Pouvez Faire

L'application inclut :

### Tableau de Bord
- Vue d'ensemble de tous les véhicules et leur statut
- Alertes de maintenance récentes
- Résumé de l'inventaire des pièces

### Section Véhicules
- Voir tous les véhicules de votre flotte
- Ajouter de nouveaux véhicules
- Mettre à jour les informations des véhicules
- Suivre le statut des véhicules (opérationnel, maintenance due, en réparation)

### Section Maintenance
- Planifier la maintenance des véhicules
- Voir l'historique de maintenance
- Suivre les coûts et la durée
- Assigner les techniciens

### Inventaire des Pièces
- Gérer le stock de pièces de rechange
- Suivre les articles en stock faible
- Ajouter de nouvelles pièces à l'inventaire
- Surveiller l'utilisation des pièces

### Système de Validation
- Évaluation intelligente du statut des véhicules
- Interface en liste de tâches - les véhicules validés disparaissent
- Analyse complète du statut basée sur l'historique de maintenance
- Opérations de validation en lot

### Assistant de Chat
- Poser des questions sur votre flotte
- Obtenir des mises à jour rapides du statut des véhicules
- Vérifier les alertes de maintenance
- S'enquérir de l'inventaire des pièces
- Réponses intelligentes de secours

## Données d'Exemple

L'application vient avec des données d'exemple :
- 3 véhicules d'exemple (Renault Master, Peugeot Partner, Ford Transit)
- Inventaire de pièces avec différents niveaux de stock
- Enregistrements de maintenance et alertes

## Dépannage

### "Échec de connexion à la base de données"
- Assurez-vous que PostgreSQL fonctionne
- Vérifiez votre DATABASE_URL dans le fichier .env
- Vérifiez vos identifiants de base de données

### "Le port 5000 est déjà utilisé"
- Changez le PORT dans votre fichier .env vers un numéro différent (par ex., 3000)
- Ou arrêtez toute autre application utilisant le port 5000

### "commande npm introuvable"
- Assurez-vous que Node.js est correctement installé
- Redémarrez votre terminal
- Essayez : `node --version` pour vérifier l'installation

### L'application ne démarre pas
- Assurez-vous d'être dans le bon dossier de projet
- Essayez : `npm install` à nouveau
- Vérifiez les messages d'erreur

### Les tables de base de données n'existent pas
- Exécutez : `npm run db:push` à nouveau
- Assurez-vous que votre connexion à la base de données fonctionne

## Obtenir de l'Aide

Si vous rencontrez des problèmes :
1. Vérifiez la section dépannage ci-dessus
2. Assurez-vous que tous les prérequis sont correctement installés
3. Vérifiez que toutes les commandes ont été exécutées dans le bon ordre
4. Vérifiez que la base de données fonctionne et est accessible

## Arrêter l'Application

Pour arrêter l'application :
- Appuyez sur `Ctrl + C` dans le terminal où elle fonctionne

Pour redémarrer :
- Exécutez `npm run dev` à nouveau

## Prochaines Étapes

Une fois que tout fonctionne :
1. Effacez les données d'exemple et ajoutez vos propres véhicules
2. Configurez votre inventaire de pièces
3. Commencez à planifier la maintenance de votre flotte
4. Explorez les fonctionnalités de l'assistant de chat

Votre FleetManager est maintenant prêt à être utilisé !