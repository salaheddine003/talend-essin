# 🚀 Projet Talend ESSIN — Gestion de Livres et Auteurs

## 🧩 Description du projet
Ce projet a été réalisé dans le cadre du module **ETL / Data Integration** à l’ESSIN.  
Il vise à illustrer les étapes d’un **processus d’intégration de données** (ETL) complet à l’aide de **Talend Open Studio** et de **Docker**.

L’objectif principal est de :
- Extraire les données brutes depuis des fichiers CSV.
- Transformer ces données (nettoyage, jointure, enrichissement).
- Charger les données finales dans un **Data Warehouse** MySQL.

---

## 🧱 Architecture du projet

```
talend-essin/
│
├── .vscode/                  # Configuration VS Code
├── Talend/
│   ├── docker-compose.yml    # Conteneur MySQL
│   ├── bookdb_init.sql       # Script d'initialisation base source
│   ├── dwh_init.sql          # Script d'initialisation Data Warehouse
│   ├── gestion_livres_init.sql # Schéma de gestion des livres
│   ├── LivresAuteur.csv      # Données sources (livres/auteurs)
│   ├── LivresAuteur2.csv     # Deuxième fichier source
│   ├── Extraire_Auteur.zip   # Job Talend : extraction des auteurs
│   ├── Transformation_Auteur.zip # Job Talend : transformation des données
│   ├── Load_DWH_Auteur.zip   # Job Talend : chargement dans le DWH
│   └── Join_Export_Tables_CSV.zip # Job Talend : jointure et export final
│
└── README.md
```

---

## 🐳 Lancer le projet avec Docker

### 1️⃣ Démarrer MySQL
```bash
docker-compose up -d
```

Cela va créer un conteneur MySQL avec les bases nécessaires :
- `bookdb`
- `dwh`
- `gestion_livres`

### 2️⃣ Vérifier la base
```bash
docker ps
docker exec -it mysql_gestion bash
mysql -u root -p
SHOW DATABASES;
```

---

## ⚙️ Exécution des Jobs Talend

Importer les jobs `.zip` dans **Talend Open Studio for Data Integration** :

1. Ouvrir Talend → `File` → `Import Items`
2. Sélectionner le répertoire `Talend/`
3. Choisir les jobs à importer :
   - `Extraire_Auteur`
   - `Transformation_Auteur`
   - `Load_DWH_Auteur`
   - `Join_Export_Tables_CSV`
4. Exécuter les jobs dans l’ordre pour observer le pipeline complet.

---

## 📊 Résultat attendu

À la fin de l’exécution :
- Les données des fichiers CSV sont nettoyées et intégrées dans le Data Warehouse.
- Les tables sont jointes pour obtenir une **vue consolidée** des auteurs et de leurs livres.
- Les résultats peuvent être exportés sous format CSV pour reporting.

---

## 👨‍💻 Auteur
**Salaheddine Abbar**  
🎓 Étudiant en Master data engineer&cloud — ESSIN Paris  
💡 Projet réalisé dans le cadre du module Data / Talend

