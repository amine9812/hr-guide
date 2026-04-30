# GUIDE COMPLET.md — Comprendre et recréer la plateforme RH Spring Boot

Ce guide est écrit pour un vrai débutant. Il avance doucement, avec des images du quotidien, puis il montre comment ces images se traduisent dans ton projet réel.
Guide généré le 2026-04-29 23:26 UTC à partir des fichiers de `/home/shini/RH-nowjava`.

---

## PARTIE 0 — AVANT DE COMMENCER : COMPRENDRE L'ARCHITECTURE

### 0.1 — C'est quoi une application web ? (analogie : la commande de pizza)
Une application web est un programme que tu utilises avec un navigateur.
Le navigateur est comme le client qui commande une pizza.
Le serveur Spring Boot est la cuisine qui prépare la réponse.
HTTP est le livreur qui transporte la commande et la pizza.
Dans ce projet, quand tu tapes `/login`, `AuthController` prépare la page `auth/login.html`.

### 0.2 — C'est quoi Spring Boot ? (analogie : la cuisine d'un restaurant)
Spring Boot est le chef de cuisine qui organise tout.
Il démarre le serveur web, trouve les Controllers, connecte la base et prépare Thymeleaf.
Sans lui, tu devrais brancher chaque morceau à la main.
Ici, `GestionRhApplication.java` est le bouton qui démarre toute la cuisine.

### 0.3 — Les 5 couches du projet (analogie : le restaurant complet)
CLIENT : le navigateur, comme le client du restaurant.
CONTROLLER : le serveur qui prend la commande.
SERVICE : le chef qui applique la vraie règle métier.
REPOSITORY : la personne qui va chercher les ingrédients en réserve.
PostgreSQL : le garde-manger où les données sont rangées.
TEMPLATE Thymeleaf : l’assiette finale que le client voit.
Chemin : Navigateur → Controller → Service → Repository → PostgreSQL → Template HTML → Navigateur.

### 0.4 — C'est quoi Maven et le pom.xml ?
Maven est le livreur de courses.
`pom.xml` est la liste de courses.
Tu écris les bibliothèques nécessaires, Maven les télécharge.
Dans ce projet, Maven apporte Web, Thymeleaf, Security, JPA, PostgreSQL, Validation et Lombok.

### 0.5 — C'est quoi PostgreSQL ?
PostgreSQL est un classeur géant.
Chaque table est une feuille.
Chaque ligne est une fiche.
Chaque colonne est une case.
Dans ce projet, `employes`, `utilisateurs`, `demandes_conges` et `notifications` sont des feuilles du classeur.

---

## PARTIE 1 — LES FICHIERS QUE TU DOIS SAVOIR ÉCRIRE

> Ces fichiers contiennent la logique de l'application. Ce sont eux que tu devras recréer si tu refais le projet.

### Sous-section 1.1 — Les Entities (le modèle de données)

Une Entity est une fiche d’inscription : elle définit les cases de données.

#### 📄 DemandeAdministrative.java
📍 Emplacement : src/main/java/com/gestionrh/entity/DemandeAdministrative.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `DemandeAdministrative` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/DemandeAdministrative.java` contient 66 lignes. Il décrit une fiche de données `DemandeAdministrative` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/DemandeAdministrative.java
//
// CONCEPT SPRING BOOT : Cette Entity stocke les demandes administratives
// déposées par les employés et leur progression dans le workflow.
// @Entity : JPA gère cette classe comme une table.
@Entity
// @Table : nom SQL explicite.
@Table(name = "demandes_administratives")
// @Getter : génère les getters.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/DemandeAdministrative.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Cette Entity stocke les demandes administratives`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// déposées par les employés et leur progression dans le workflow.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `// @Entity : JPA gère cette classe comme une table.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `// @Table : nom SQL explicite.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `@Table(name = "demandes_administratives")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `// @Getter : génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `// @Setter : génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `public class DemandeAdministrative {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `// @Id : clé primaire.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 36 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `DemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DemandeAdministrative` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 DemandeConge.java
📍 Emplacement : src/main/java/com/gestionrh/entity/DemandeConge.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `DemandeConge` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/DemandeConge.java` contient 81 lignes. Il décrit une fiche de données `DemandeConge` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/DemandeConge.java
//
// CONCEPT SPRING BOOT : Cette Entity représente une demande de congé.
// Les champs enum modélisent le type de congé et l'état de validation.
// @Entity : cette classe est persistée dans PostgreSQL.
@Entity
// @Table : nom de la table des congés.
@Table(name = "demandes_conges")
// @Getter : génère les getters.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/DemandeConge.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Cette Entity représente une demande de congé.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Les champs enum modélisent le type de congé et l'état de validation.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `// @Entity : cette classe est persistée dans PostgreSQL.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `// @Table : nom de la table des congés.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `@Table(name = "demandes_conges")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `// @Getter : génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `// @Setter : génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 34 : `public class DemandeConge {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 36 : `// @Id : identifiant unique.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 37 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `DemandeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DemandeConge` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 Departement.java
📍 Emplacement : src/main/java/com/gestionrh/entity/Departement.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `Departement` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/Departement.java` contient 44 lignes. Il décrit une fiche de données `Departement` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/Departement.java
//
// CONCEPT SPRING BOOT : Cette Entity représente la table des départements.
// Un département regroupe des employés et aide à structurer l'organisation.
// @Entity : cette classe devient une table gérée par JPA.
@Entity
// @Table : nom SQL explicite pour éviter les surprises.
@Table(name = "departements")
// @Getter : Lombok génère les getters.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/Departement.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Cette Entity représente la table des départements.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Un département regroupe des employés et aide à structurer l'organisation.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `// @Entity : cette classe devient une table gérée par JPA.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `// @Table : nom SQL explicite pour éviter les surprises.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `@Table(name = "departements")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `// @Getter : Lombok génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `// @Setter : Lombok génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `public class Departement {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `// @Id : identifiant unique du département.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `Departement.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`Departement` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 Document.java
📍 Emplacement : src/main/java/com/gestionrh/entity/Document.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `Document` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/Document.java` contient 64 lignes. Il décrit une fiche de données `Document` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/Document.java
//
// CONCEPT SPRING BOOT : Cette Entity ne stocke pas le fichier lui-même en base.
// Elle stocke les métadonnées et le chemin du fichier enregistré dans uploads/.
// @Entity : JPA crée une table documents.
@Entity
// @Table : nom de table explicite.
@Table(name = "documents")
// @Getter : génère les getters.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/Document.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Cette Entity ne stocke pas le fichier lui-même en base.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Elle stocke les métadonnées et le chemin du fichier enregistré dans uploads/.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `// @Entity : JPA crée une table documents.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `// @Table : nom de table explicite.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `@Table(name = "documents")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `// @Getter : génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `// @Setter : génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `public class Document {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `// @Id : clé primaire du document.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `Document.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`Document` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 Employe.java
📍 Emplacement : src/main/java/com/gestionrh/entity/Employe.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `Employe` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/Employe.java` contient 105 lignes. Il décrit une fiche de données `Employe` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/Employe.java
//
// CONCEPT SPRING BOOT : Une Entity représente une table. Les relations
// @ManyToOne et @OneToOne permettent de relier les tables entre elles sans
// @Entity : JPA crée une table employes pour cette classe.
@Entity
// @Table : nom explicite de la table.
@Table(name = "employes")
// @Getter : génère les getters.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/Employe.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Une Entity représente une table. Les relations`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// @ManyToOne et @OneToOne permettent de relier les tables entre elles sans`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `// @Entity : JPA crée une table employes pour cette classe.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `// @Table : nom explicite de la table.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `@Table(name = "employes")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 34 : `// @Getter : génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 36 : `// @Setter : génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 37 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `public class Employe {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 40 : `// @Id : clé primaire.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 41 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `Employe.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`Employe` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 HistoriqueAction.java
📍 Emplacement : src/main/java/com/gestionrh/entity/HistoriqueAction.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `HistoriqueAction` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/HistoriqueAction.java` contient 51 lignes. Il décrit une fiche de données `HistoriqueAction` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/HistoriqueAction.java
//
// CONCEPT SPRING BOOT : Cette Entity garde une trace simple des actions importantes.
// C'est utile pour comprendre qui a validé, refusé ou modifié une demande.
// @Entity : JPA mappe cette classe vers une table.
@Entity
// @Table : nom SQL explicite.
@Table(name = "historique_actions")
// @Getter : génère les getters.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/HistoriqueAction.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Cette Entity garde une trace simple des actions importantes.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// C'est utile pour comprendre qui a validé, refusé ou modifié une demande.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `// @Entity : JPA mappe cette classe vers une table.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `// @Table : nom SQL explicite.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `@Table(name = "historique_actions")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `// @Getter : génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `// @Setter : génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `public class HistoriqueAction {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `// @Id : clé primaire.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `HistoriqueAction.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`HistoriqueAction` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 Notification.java
📍 Emplacement : src/main/java/com/gestionrh/entity/Notification.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `Notification` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/Notification.java` contient 55 lignes. Il décrit une fiche de données `Notification` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/Notification.java
//
// CONCEPT SPRING BOOT : Cette Entity stocke les messages internes envoyés
// à un utilisateur quand une demande change de statut.
// @Entity : JPA persiste les notifications.
@Entity
// @Table : nom de la table.
@Table(name = "notifications")
// @Getter : génère les getters.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/Notification.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Cette Entity stocke les messages internes envoyés`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// à un utilisateur quand une demande change de statut.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `// @Entity : JPA persiste les notifications.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `// @Table : nom de la table.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `@Table(name = "notifications")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `// @Getter : génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `// @Setter : génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `public class Notification {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `// @Id : clé primaire.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `Notification.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`Notification` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 Poste.java
📍 Emplacement : src/main/java/com/gestionrh/entity/Poste.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `Poste` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/Poste.java` contient 44 lignes. Il décrit une fiche de données `Poste` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/Poste.java
//
// CONCEPT SPRING BOOT : Cette Entity représente les postes occupés par les employés.
// Elle sera liée aux employés par une relation ManyToOne.
// @Entity : indique que Poste est persisté en base.
@Entity
// @Table : nom de la table PostgreSQL.
@Table(name = "postes")
// @Getter : génère les getters.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/Poste.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Cette Entity représente les postes occupés par les employés.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Elle sera liée aux employés par une relation ManyToOne.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `// @Entity : indique que Poste est persisté en base.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `// @Table : nom de la table PostgreSQL.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `@Table(name = "postes")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `// @Getter : génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `// @Setter : génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `public class Poste {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `// @Id : clé primaire.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `Poste.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`Poste` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 RoleUtilisateur.java
📍 Emplacement : src/main/java/com/gestionrh/entity/RoleUtilisateur.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `RoleUtilisateur` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/RoleUtilisateur.java` contient 16 lignes. Il décrit une fiche de données `RoleUtilisateur` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/RoleUtilisateur.java
//
// CONCEPT SPRING BOOT / JAVA : Un enum limite une valeur à une liste fermée.
// Ici, un utilisateur ne peut avoir qu'un des rôles prévus par l'application.
// enum : définit les rôles métier disponibles dans le MVP RH.
public enum RoleUtilisateur {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `RoleUtilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/RoleUtilisateur.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `RoleUtilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `RoleUtilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT / JAVA : Un enum limite une valeur à une liste fermée.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `RoleUtilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Ici, un utilisateur ne peut avoir qu'un des rôles prévus par l'application.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `RoleUtilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `// enum : définit les rôles métier disponibles dans le MVP RH.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `RoleUtilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `public enum RoleUtilisateur {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `RoleUtilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`RoleUtilisateur` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 Service.java
📍 Emplacement : src/main/java/com/gestionrh/entity/Service.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `Service` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/Service.java` contient 45 lignes. Il décrit une fiche de données `Service` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/Service.java
//
// CONCEPT SPRING BOOT : Cette Entity représente un service interne.
// Attention : elle s'appelle Service côté métier, à ne pas confondre avec
// l'annotation Spring @Service utilisée dans la couche logique métier.
// @Entity : JPA mappera cette classe vers une table.
@Entity
// @Table : nom de table explicite.
@Table(name = "services")
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/Service.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Cette Entity représente un service interne.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Attention : elle s'appelle Service côté métier, à ne pas confondre avec`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `// l'annotation Spring @Service utilisée dans la couche logique métier.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `// @Entity : JPA mappera cette classe vers une table.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `// @Table : nom de table explicite.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `@Table(name = "services")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `// @Getter : génère les getters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `// @Setter : génère les setters.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `public class Service {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `// @Id : clé primaire.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Service.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`Service` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.
- ⚠️ Ici `Service` est une Entity métier ; ne la confonds pas avec `@Service` de Spring.

#### 📄 StatutConge.java
📍 Emplacement : src/main/java/com/gestionrh/entity/StatutConge.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `StatutConge` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/StatutConge.java` contient 14 lignes. Il décrit une fiche de données `StatutConge` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/StatutConge.java
//
// CONCEPT JAVA : Les statuts de workflow sont modélisés par enum pour rester
// cohérents entre Java, Thymeleaf et PostgreSQL.
// enum : cycle simple d'une demande de congé.
public enum StatutConge {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/StatutConge.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT JAVA : Les statuts de workflow sont modélisés par enum pour rester`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// cohérents entre Java, Thymeleaf et PostgreSQL.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `// enum : cycle simple d'une demande de congé.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `public enum StatutConge {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `StatutConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`StatutConge` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 StatutDemandeAdministrative.java
📍 Emplacement : src/main/java/com/gestionrh/entity/StatutDemandeAdministrative.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `StatutDemandeAdministrative` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/StatutDemandeAdministrative.java` contient 15 lignes. Il décrit une fiche de données `StatutDemandeAdministrative` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/StatutDemandeAdministrative.java
//
// CONCEPT JAVA : Un enum décrit un workflow métier lisible et contrôlé.
// ============================================================
// enum : statuts demandés dans le cahier des charges.
public enum StatutDemandeAdministrative {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/StatutDemandeAdministrative.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT JAVA : Un enum décrit un workflow métier lisible et contrôlé.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 8 : `// enum : statuts demandés dans le cahier des charges.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `public enum StatutDemandeAdministrative {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `StatutDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`StatutDemandeAdministrative` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 StatutEmploye.java
📍 Emplacement : src/main/java/com/gestionrh/entity/StatutEmploye.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `StatutEmploye` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/StatutEmploye.java` contient 13 lignes. Il décrit une fiche de données `StatutEmploye` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/StatutEmploye.java
//
// CONCEPT JAVA : Cet enum évite d'écrire le statut d'un employé en texte libre.
// Cela empêche les fautes comme "actif", "Actif" ou "ACTIVE".
// enum : liste fermée des statuts possibles d'un dossier employé.
public enum StatutEmploye {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutEmploye.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/StatutEmploye.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutEmploye.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutEmploye.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT JAVA : Cet enum évite d'écrire le statut d'un employé en texte libre.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutEmploye.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Cela empêche les fautes comme "actif", "Actif" ou "ACTIVE".`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutEmploye.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `// enum : liste fermée des statuts possibles d'un dossier employé.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `StatutEmploye.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `public enum StatutEmploye {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `StatutEmploye.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`StatutEmploye` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 TypeConge.java
📍 Emplacement : src/main/java/com/gestionrh/entity/TypeConge.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `TypeConge` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/TypeConge.java` contient 15 lignes. Il décrit une fiche de données `TypeConge` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/TypeConge.java
//
// CONCEPT JAVA : Un enum est pratique pour afficher une liste déroulante fiable
// dans un formulaire Thymeleaf et stocker une valeur claire en base.
// enum : types de congés proposés dans le MVP.
public enum TypeConge {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/TypeConge.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT JAVA : Un enum est pratique pour afficher une liste déroulante fiable`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// dans un formulaire Thymeleaf et stocker une valeur claire en base.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `// enum : types de congés proposés dans le MVP.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `public enum TypeConge {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `TypeConge.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`TypeConge` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 TypeDemandeAdministrative.java
📍 Emplacement : src/main/java/com/gestionrh/entity/TypeDemandeAdministrative.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `TypeDemandeAdministrative` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/TypeDemandeAdministrative.java` contient 14 lignes. Il décrit une fiche de données `TypeDemandeAdministrative` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/TypeDemandeAdministrative.java
//
// CONCEPT JAVA : Cet enum représente les catégories de demandes administratives
// que l'employé peut choisir dans l'interface.
// enum : types de demandes administratives du MVP.
public enum TypeDemandeAdministrative {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/TypeDemandeAdministrative.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT JAVA : Cet enum représente les catégories de demandes administratives`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// que l'employé peut choisir dans l'interface.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `// enum : types de demandes administratives du MVP.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `TypeDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `public enum TypeDemandeAdministrative {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `TypeDemandeAdministrative.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`TypeDemandeAdministrative` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

#### 📄 Utilisateur.java
📍 Emplacement : src/main/java/com/gestionrh/entity/Utilisateur.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il décrit une fiche de données `Utilisateur` que PostgreSQL pourra ranger dans une table.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est une fiche d'inscription avec des cases. Si tu remplis une fiche pour un élève, tu as nom, prénom et classe. Ici, une Entity comme `Employe` a matricule, nom, email et liens vers département, service et poste.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/entity/Utilisateur.java` contient 58 lignes. Il décrit une fiche de données `Utilisateur` que PostgreSQL pourra ranger dans une table. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : entity/Utilisateur.java
//
// CONCEPT SPRING BOOT : Une Entity est une classe Java qui représente une table
// PostgreSQL. JPA traduit les objets Utilisateur en lignes SQL.
// @Entity : indique à JPA que cette classe correspond à une table PostgreSQL.
@Entity
// @Table : fixe le nom de la table en base de données.
@Table(name = "utilisateurs")
// @Getter : Lombok génère les méthodes getX() pour lire les champs.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : entity/Utilisateur.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Une Entity est une classe Java qui représente une table`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// PostgreSQL. JPA traduit les objets Utilisateur en lignes SQL.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `// @Entity : indique à JPA que cette classe correspond à une table PostgreSQL.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `@Entity`
  Explication : elle dit que la classe devient une table PostgreSQL.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `// @Table : fixe le nom de la table en base de données.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `@Table(name = "utilisateurs")`
  Explication : elle fixe le nom de la table.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `// @Getter : Lombok génère les méthodes getX() pour lire les champs.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `@Getter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `// @Setter : Lombok génère les méthodes setX() pour modifier les champs.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `@Setter`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `public class Utilisateur {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `// @Id : ce champ est la clé primaire de la table.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `@Id`
  Explication : elle marque la clé primaire, le numéro unique.
  Pourquoi : dans `Utilisateur.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`Utilisateur` est lu ou sauvegardé par un Repository, puis utilisé par les Services et parfois affiché dans les templates.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `entity/`.
2. Ajouter le bon `package`.
3. Ajouter les annotations JPA nécessaires.
4. Déclarer les champs.
5. Ajouter les relations si besoin.
6. Compiler puis lancer pour créer la table.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Entity`.
- Oublier `@Id`.
- Mal nommer une relation.

### Sous-section 1.2 — Les Repositories (l’accès aux données)

Un Repository est le bibliothécaire qui va chercher les fiches.

#### 📄 DemandeAdministrativeRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/DemandeAdministrativeRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `DemandeAdministrative` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/DemandeAdministrativeRepository.java` contient 26 lignes. Il sert à retrouver, enregistrer ou compter les données de `DemandeAdministrative` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/DemandeAdministrativeRepository.java
//
// CONCEPT SPRING BOOT : Les méthodes déclarées ici deviennent des requêtes
// pour suivre les demandes administratives par employé ou statut.
public interface DemandeAdministrativeRepository extends JpaRepository<DemandeAdministrative, Long> {
    List<DemandeAdministrative> findByEmployeOrderByDateSoumissionDesc(Employe employe);
    List<DemandeAdministrative> findByStatutOrderByDateSoumissionDesc(StatutDemandeAdministrative statut);
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/DemandeAdministrativeRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Les méthodes déclarées ici deviennent des requêtes`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// pour suivre les demandes administratives par employé ou statut.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `public interface DemandeAdministrativeRepository extends JpaRepository<DemandeAdministrative, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `List<DemandeAdministrative> findByEmployeOrderByDateSoumissionDesc(Employe employe);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `DemandeAdministrativeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `List<DemandeAdministrative> findByStatutOrderByDateSoumissionDesc(StatutDemandeAdministrative statut);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `DemandeAdministrativeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DemandeAdministrativeRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 DemandeCongeRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/DemandeCongeRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `DemandeConge` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/DemandeCongeRepository.java` contient 25 lignes. Il sert à retrouver, enregistrer ou compter les données de `DemandeConge` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/DemandeCongeRepository.java
//
// CONCEPT SPRING BOOT : Ce Repository gère les demandes de congés et leurs filtres.
// ============================================================
public interface DemandeCongeRepository extends JpaRepository<DemandeConge, Long> {
    List<DemandeConge> findByEmployeOrderByDateSoumissionDesc(Employe employe);
    List<DemandeConge> findByStatutOrderByDateSoumissionDesc(StatutConge statut);
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeCongeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/DemandeCongeRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeCongeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeCongeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Repository gère les demandes de congés et leurs filtres.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeCongeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeCongeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `public interface DemandeCongeRepository extends JpaRepository<DemandeConge, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeCongeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `List<DemandeConge> findByEmployeOrderByDateSoumissionDesc(Employe employe);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `DemandeCongeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `List<DemandeConge> findByStatutOrderByDateSoumissionDesc(StatutConge statut);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `DemandeCongeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DemandeCongeRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 DepartementRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/DepartementRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `Departement` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/DepartementRepository.java` contient 13 lignes. Il sert à retrouver, enregistrer ou compter les données de `Departement` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/DepartementRepository.java
//
// CONCEPT SPRING BOOT : Ce Repository donne accès aux départements sans écrire de SQL.
// ============================================================
public interface DepartementRepository extends JpaRepository<Departement, Long> {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DepartementRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/DepartementRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DepartementRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DepartementRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Repository donne accès aux départements sans écrire de SQL.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DepartementRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DepartementRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `public interface DepartementRepository extends JpaRepository<Departement, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DepartementRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DepartementRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 DocumentRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/DocumentRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `Document` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/DocumentRepository.java` contient 19 lignes. Il sert à retrouver, enregistrer ou compter les données de `Document` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/DocumentRepository.java
//
// CONCEPT SPRING BOOT : Ce Repository permet de retrouver les documents
// associés à un employé ou à une demande administrative.
public interface DocumentRepository extends JpaRepository<Document, Long> {
    List<Document> findByEmployeOrderByDateAjoutDesc(Employe employe);
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/DocumentRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Repository permet de retrouver les documents`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// associés à un employé ou à une demande administrative.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `public interface DocumentRepository extends JpaRepository<Document, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `List<Document> findByEmployeOrderByDateAjoutDesc(Employe employe);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `DocumentRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DocumentRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 EmployeRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/EmployeRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `Employe` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/EmployeRepository.java` contient 27 lignes. Il sert à retrouver, enregistrer ou compter les données de `Employe` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/EmployeRepository.java
//
// CONCEPT SPRING BOOT : Les noms de méthodes deviennent des requêtes SQL.
// Ici, Spring comprend les propriétés imbriquées comme departement.libelle.
public interface EmployeRepository extends JpaRepository<Employe, Long> {
    List<Employe> findByNomContainingIgnoreCaseOrPrenomContainingIgnoreCaseOrDepartementLibelleContainingIgnoreCase(String nom, String prenom, String departement);
    Optional<Employe> findByUtilisateur(Utilisateur utilisateur);
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/EmployeRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Les noms de méthodes deviennent des requêtes SQL.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Ici, Spring comprend les propriétés imbriquées comme departement.libelle.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `public interface EmployeRepository extends JpaRepository<Employe, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `List<Employe> findByNomContainingIgnoreCaseOrPrenomContainingIgnoreCaseOrDepartementLibelleContainingIgnoreCase(String nom, String prenom, String departement);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `EmployeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `Optional<Employe> findByUtilisateur(Utilisateur utilisateur);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `EmployeRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`EmployeRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 HistoriqueActionRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/HistoriqueActionRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `HistoriqueAction` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/HistoriqueActionRepository.java` contient 13 lignes. Il sert à retrouver, enregistrer ou compter les données de `HistoriqueAction` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/HistoriqueActionRepository.java
//
// CONCEPT SPRING BOOT : Ce Repository enregistre les traces d'actions métier.
// ============================================================
public interface HistoriqueActionRepository extends JpaRepository<HistoriqueAction, Long> {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueActionRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/HistoriqueActionRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueActionRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueActionRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Repository enregistre les traces d'actions métier.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueActionRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueActionRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `public interface HistoriqueActionRepository extends JpaRepository<HistoriqueAction, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `HistoriqueActionRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`HistoriqueActionRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 NotificationRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/NotificationRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `Notification` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/NotificationRepository.java` contient 22 lignes. Il sert à retrouver, enregistrer ou compter les données de `Notification` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/NotificationRepository.java
//
// CONCEPT SPRING BOOT : Ce Repository sert à afficher et compter les messages
// internes d'un utilisateur connecté.
public interface NotificationRepository extends JpaRepository<Notification, Long> {
    List<Notification> findByDestinataireOrderByDateEnvoiDesc(Utilisateur destinataire);
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/NotificationRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Repository sert à afficher et compter les messages`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// internes d'un utilisateur connecté.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `public interface NotificationRepository extends JpaRepository<Notification, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `List<Notification> findByDestinataireOrderByDateEnvoiDesc(Utilisateur destinataire);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `NotificationRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`NotificationRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 PosteRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/PosteRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `Poste` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/PosteRepository.java` contient 13 lignes. Il sert à retrouver, enregistrer ou compter les données de `Poste` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/PosteRepository.java
//
// CONCEPT SPRING BOOT : Ce Repository donne les opérations CRUD pour les postes.
// ============================================================
public interface PosteRepository extends JpaRepository<Poste, Long> {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `PosteRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/PosteRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `PosteRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `PosteRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Repository donne les opérations CRUD pour les postes.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `PosteRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `PosteRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `public interface PosteRepository extends JpaRepository<Poste, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `PosteRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`PosteRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 ServiceRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/ServiceRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `Service` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/ServiceRepository.java` contient 13 lignes. Il sert à retrouver, enregistrer ou compter les données de `Service` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/ServiceRepository.java
//
// CONCEPT SPRING BOOT : Ce Repository manipule l'Entity métier Service.
// ============================================================
public interface ServiceRepository extends JpaRepository<Service, Long> {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `ServiceRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/ServiceRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `ServiceRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `ServiceRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Repository manipule l'Entity métier Service.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `ServiceRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `ServiceRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `public interface ServiceRepository extends JpaRepository<Service, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `ServiceRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`ServiceRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

#### 📄 UtilisateurRepository.java
📍 Emplacement : src/main/java/com/gestionrh/repository/UtilisateurRepository.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il sert à retrouver, enregistrer ou compter les données de `Utilisateur` sans écrire de SQL à la main.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un bibliothécaire. Tu ne vas pas fouiller toutes les étagères toi-même : tu demandes un livre, il sait où chercher. Ici, le Repository sait interroger PostgreSQL.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/repository/UtilisateurRepository.java` contient 26 lignes. Il sert à retrouver, enregistrer ou compter les données de `Utilisateur` sans écrire de SQL à la main. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : repository/UtilisateurRepository.java
//
// CONCEPT SPRING BOOT : Un Repository est une interface d'accès aux données.
// Spring Data JPA génère automatiquement les requêtes SQL à partir des méthodes.
// JpaRepository<Utilisateur, Long> fournit save, findById, findAll et delete.
public interface UtilisateurRepository extends JpaRepository<Utilisateur, Long> {
    // findByLogin : Spring génère SELECT ... WHERE login = ?.
    Optional<Utilisateur> findByLogin(String login);
    // findByRole : Spring génère SELECT ... WHERE role = ?.
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : repository/UtilisateurRepository.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Un Repository est une interface d'accès aux données.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Spring Data JPA génère automatiquement les requêtes SQL à partir des méthodes.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `// JpaRepository<Utilisateur, Long> fournit save, findById, findAll et delete.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `public interface UtilisateurRepository extends JpaRepository<Utilisateur, Long> {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `// findByLogin : Spring génère SELECT ... WHERE login = ?.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `Optional<Utilisateur> findByLogin(String login);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `// findByRole : Spring génère SELECT ... WHERE role = ?.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `List<Utilisateur> findByRole(RoleUtilisateur role);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `UtilisateurRepository.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`UtilisateurRepository` parle à PostgreSQL pour une Entity, et il est appelé depuis un Service.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer une interface dans `repository/`.
2. Étendre `JpaRepository<Entity, Long>`.
3. Ajouter les méthodes `findBy...` utiles.
4. Injecter le Repository dans un Service.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Se tromper dans `findBy...`.
- Mettre un mauvais type d’id.
- Oublier `JpaRepository`.

### Sous-section 1.3 — Les Services (la logique métier)

Un Service est le chef de projet qui sait quoi faire avec les fiches.

#### 📄 CongeService.java
📍 Emplacement : src/main/java/com/gestionrh/service/CongeService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `Conge`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/CongeService.java` contient 75 lignes. Il contient les règles métier de `Conge`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/CongeService.java
//
// CONCEPT SPRING BOOT : Ce Service gère le workflow des congés :
// dépôt par l'employé, validation ou refus par un responsable.
// @Service : logique métier des congés.
@Service
public class CongeService {
    private final DemandeCongeRepository demandeCongeRepository;
    private final NotificationService notificationService;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/CongeService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Service gère le workflow des congés :`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// dépôt par l'employé, validation ou refus par un responsable.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `// @Service : logique métier des congés.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `@Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `public class CongeService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `private final DemandeCongeRepository demandeCongeRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `private final NotificationService notificationService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `private final HistoriqueService historiqueService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `public CongeService(DemandeCongeRepository demandeCongeRepository, NotificationService notificationService, HistoriqueService historiqueService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `public List<DemandeConge> findAll() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `return demandeCongeRepository.findAll();`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 43 : `public List<DemandeConge> findForEmploye(Employe employe) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 44 : `return demandeCongeRepository.findByEmployeOrderByDateSoumissionDesc(employe);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `CongeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`CongeService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

#### 📄 DashboardService.java
📍 Emplacement : src/main/java/com/gestionrh/service/DashboardService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `Dashboard`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/DashboardService.java` contient 47 lignes. Il contient les règles métier de `Dashboard`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/DashboardService.java
//
// CONCEPT SPRING BOOT : Ce Service regroupe les compteurs du tableau de bord.
// Le Controller n'a pas à connaître les détails des requêtes JPA.
// @Service : composant Spring injectable.
@Service
public class DashboardService {
    private final EmployeService employeService;
    private final CongeService congeService;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/DashboardService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Service regroupe les compteurs du tableau de bord.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Le Controller n'a pas à connaître les détails des requêtes JPA.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 14 : `// @Service : composant Spring injectable.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `@Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `public class DashboardService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `private final EmployeService employeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `private final CongeService congeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `private final DemandeAdministrativeService demandeAdministrativeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `private final NotificationService notificationService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `public DashboardService(EmployeService employeService, CongeService congeService, DemandeAdministrativeService demandeAdministrativeService, NotificationService notificationService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `public Map<String, Long> buildCounters(Utilisateur utilisateur) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 45 : `return counters;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DashboardService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

#### 📄 DemandeAdministrativeService.java
📍 Emplacement : src/main/java/com/gestionrh/service/DemandeAdministrativeService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `DemandeAdministrative`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/DemandeAdministrativeService.java` contient 73 lignes. Il contient les règles métier de `DemandeAdministrative`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/DemandeAdministrativeService.java
//
// CONCEPT SPRING BOOT : Ce Service gère le workflow des demandes administratives.
// ============================================================
// @Service : logique métier des demandes administratives.
@Service
public class DemandeAdministrativeService {
    private final DemandeAdministrativeRepository demandeAdministrativeRepository;
    private final NotificationService notificationService;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/DemandeAdministrativeService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Service gère le workflow des demandes administratives.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `// @Service : logique métier des demandes administratives.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `@Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `public class DemandeAdministrativeService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `private final DemandeAdministrativeRepository demandeAdministrativeRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `private final NotificationService notificationService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `private final HistoriqueService historiqueService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `public DemandeAdministrativeService(DemandeAdministrativeRepository demandeAdministrativeRepository, NotificationService notificationService, HistoriqueService historiqueService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 37 : `public List<DemandeAdministrative> findAll() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `return demandeAdministrativeRepository.findAll();`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 42 : `public List<DemandeAdministrative> findForEmploye(Employe employe) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 43 : `return demandeAdministrativeRepository.findByEmployeOrderByDateSoumissionDesc(employe);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `DemandeAdministrativeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DemandeAdministrativeService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

#### 📄 DocumentService.java
📍 Emplacement : src/main/java/com/gestionrh/service/DocumentService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `Document`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/DocumentService.java` contient 76 lignes. Il contient les règles métier de `Document`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/DocumentService.java
//
// CONCEPT SPRING BOOT : Ce Service gère l'upload de fichiers MultipartFile,
// l'écriture dans le dossier uploads/ et l'enregistrement des métadonnées.
// @Service : logique métier des documents.
@Service
public class DocumentService {
    private final Path uploadDir = Path.of("uploads");
    private final DocumentRepository documentRepository;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/DocumentService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Service gère l'upload de fichiers MultipartFile,`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// l'écriture dans le dossier uploads/ et l'enregistrement des métadonnées.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `// @Service : logique métier des documents.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `@Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `public class DocumentService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `private final Path uploadDir = Path.of("uploads");`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `private final DocumentRepository documentRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `private final EmployeRepository employeRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `public DocumentService(DocumentRepository documentRepository, EmployeRepository employeRepository) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 44 : `public List<Document> findAll() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 45 : `return documentRepository.findAll();`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 48 : `// findById : retrouve un document.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 49 : `public Document findById(Long id) {`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `DocumentService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DocumentService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

#### 📄 EmployeService.java
📍 Emplacement : src/main/java/com/gestionrh/service/EmployeService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `Employe`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/EmployeService.java` contient 100 lignes. Il contient les règles métier de `Employe`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/EmployeService.java
//
// CONCEPT SPRING BOOT : Ce Service gère les dossiers employés.
// Il assemble les choix de formulaire avec les objets JPA reliés.
// @Service : classe de logique métier injectable.
@Service
public class EmployeService {
    private final EmployeRepository employeRepository;
    private final DepartementRepository departementRepository;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/EmployeService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Service gère les dossiers employés.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Il assemble les choix de formulaire avec les objets JPA reliés.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `// @Service : classe de logique métier injectable.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `@Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `public class EmployeService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `private final EmployeRepository employeRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `private final DepartementRepository departementRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `private final ServiceRepository serviceRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `private final PosteRepository posteRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `private final UtilisateurRepository utilisateurRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 41 : `public EmployeService(EmployeRepository employeRepository, DepartementRepository departementRepository, ServiceRepository serviceRepository, PosteRepository posteRepository, UtilisateurRepository utilisateurRepository) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 50 : `public List<Employe> findAll() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 51 : `return employeRepository.findAll();`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`EmployeService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

#### 📄 HistoriqueService.java
📍 Emplacement : src/main/java/com/gestionrh/service/HistoriqueService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `Historique`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/HistoriqueService.java` contient 33 lignes. Il contient les règles métier de `Historique`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/HistoriqueService.java
//
// CONCEPT SPRING BOOT : Ce Service isole l'écriture d'audit pour garder
// les autres Services lisibles.
// @Service : composant Spring injectable.
@Service
public class HistoriqueService {
    private final HistoriqueActionRepository historiqueActionRepository;
    public HistoriqueService(HistoriqueActionRepository historiqueActionRepository) {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/HistoriqueService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Service isole l'écriture d'audit pour garder`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// les autres Services lisibles.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 14 : `// @Service : composant Spring injectable.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `@Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `public class HistoriqueService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `private final HistoriqueActionRepository historiqueActionRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `public HistoriqueService(HistoriqueActionRepository historiqueActionRepository) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `public void tracer(Utilisateur utilisateur, String action) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `historiqueActionRepository.save(historiqueAction);`
  Explication : elle enregistre une donnée en base.
  Pourquoi : dans `HistoriqueService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`HistoriqueService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

#### 📄 NotificationService.java
📍 Emplacement : src/main/java/com/gestionrh/service/NotificationService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `Notification`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/NotificationService.java` contient 54 lignes. Il contient les règles métier de `Notification`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/NotificationService.java
//
// CONCEPT SPRING BOOT : Ce Service centralise la création et la lecture
// des notifications internes.
// @Service : rend la classe injectable dans les autres Services.
@Service
public class NotificationService {
    private final NotificationRepository notificationRepository;
    public NotificationService(NotificationRepository notificationRepository) {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/NotificationService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Service centralise la création et la lecture`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// des notifications internes.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `// @Service : rend la classe injectable dans les autres Services.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `@Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `public class NotificationService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `private final NotificationRepository notificationRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `public NotificationService(NotificationRepository notificationRepository) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `public void creerNotification(Utilisateur destinataire, String message) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `notificationRepository.save(notification);`
  Explication : elle enregistre une donnée en base.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `public List<Notification> findForUser(Utilisateur utilisateur) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 40 : `return notificationRepository.findByDestinataireOrderByDateEnvoiDesc(utilisateur);`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 44 : `public long countUnread(Utilisateur utilisateur) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 45 : `return notificationRepository.countByDestinataireAndLueFalse(utilisateur);`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`NotificationService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

#### 📄 OrganisationService.java
📍 Emplacement : src/main/java/com/gestionrh/service/OrganisationService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `Organisation`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/OrganisationService.java` contient 95 lignes. Il contient les règles métier de `Organisation`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/OrganisationService.java
//
// CONCEPT SPRING BOOT : Ce Service regroupe la logique CRUD de l'organisation :
// départements, services et postes. Le Controller reste ainsi très simple.
// @org.springframework.stereotype.Service : annotation Spring écrite en nom complet pour éviter le conflit avec l'Entity Service.
@org.springframework.stereotype.Service
public class OrganisationService {
    private final DepartementRepository departementRepository;
    private final ServiceRepository serviceRepository;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/OrganisationService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Service regroupe la logique CRUD de l'organisation :`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// départements, services et postes. Le Controller reste ainsi très simple.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `// @org.springframework.stereotype.Service : annotation Spring écrite en nom complet pour éviter le conflit avec l'Entity Service.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `@org.springframework.stereotype.Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `public class OrganisationService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `private final DepartementRepository departementRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `private final ServiceRepository serviceRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `private final PosteRepository posteRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `public OrganisationService(DepartementRepository departementRepository, ServiceRepository serviceRepository, PosteRepository posteRepository) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 37 : `public List<Departement> findAllDepartements() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `return departementRepository.findAll();`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 42 : `public Departement saveDepartement(Departement departement) {`
  Explication : elle enregistre une donnée en base.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 43 : `return departementRepository.save(departement);`
  Explication : elle enregistre une donnée en base.
  Pourquoi : dans `OrganisationService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`OrganisationService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

#### 📄 UtilisateurService.java
📍 Emplacement : src/main/java/com/gestionrh/service/UtilisateurService.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il contient les règles métier de `Utilisateur`.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le chef cuisinier. Le serveur prend la commande, mais le chef sait préparer le plat. Ici, le Service sait encoder un mot de passe, archiver un employé ou valider un congé.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/service/UtilisateurService.java` contient 77 lignes. Il contient les règles métier de `Utilisateur`. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : service/UtilisateurService.java
//
// CONCEPT SPRING BOOT : Un Service contient la logique métier.
// Ici, il charge les utilisateurs pour Spring Security et encode les mots de passe.
// @Service : Spring crée automatiquement une instance injectable de cette classe.
@Service
public class UtilisateurService implements UserDetailsService {
    private final UtilisateurRepository utilisateurRepository;
    private final PasswordEncoder passwordEncoder;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : service/UtilisateurService.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Un Service contient la logique métier.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Ici, il charge les utilisateurs pour Spring Security et encode les mots de passe.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `// @Service : Spring crée automatiquement une instance injectable de cette classe.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `@Service`
  Explication : elle dit que la classe contient de la logique métier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `public class UtilisateurService implements UserDetailsService {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `private final UtilisateurRepository utilisateurRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `private final PasswordEncoder passwordEncoder;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `public UtilisateurService(UtilisateurRepository utilisateurRepository, PasswordEncoder passwordEncoder) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 37 : `@Override`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `Utilisateur utilisateur = utilisateurRepository.findByLogin(username)`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 41 : `return new User(`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 53 : `public List<Utilisateur> findAll() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `UtilisateurService.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`UtilisateurService` est appelé par un Controller et appelle un ou plusieurs Repositories.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `service/`.
2. Ajouter `@Service`.
3. Déclarer les dépendances en `private final`.
4. Créer le constructeur.
5. Écrire les méthodes métier.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Oublier `@Service`.
- Mettre toute la logique dans le Controller.
- Créer les dépendances avec `new`.

### Sous-section 1.4 — Les Controllers (le routage HTTP)

Un Controller est le réceptionniste qui reçoit les URLs.

#### 📄 AdminController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/AdminController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `Admin` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/AdminController.java` contient 65 lignes. Il reçoit les adresses web liées à `Admin` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/AdminController.java
//
// CONCEPT SPRING BOOT : Ce Controller est réservé à ROLE_ADMIN par SecurityConfig.
// Il crée des comptes utilisateurs et leur assigne un rôle Spring Security.
// @Controller : gestion web de l'administration.
@Controller
// @RequestMapping : préfixe /admin.
@RequestMapping("/admin")
public class AdminController {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/AdminController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Controller est réservé à ROLE_ADMIN par SecurityConfig.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Il crée des comptes utilisateurs et leur assigne un rôle Spring Security.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `// @Controller : gestion web de l'administration.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `// @RequestMapping : préfixe /admin.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `@RequestMapping("/admin")`
  Explication : elle donne le préfixe commun des URLs.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `public class AdminController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `private final UtilisateurService utilisateurService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `public AdminController(UtilisateurService utilisateurService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 37 : `@GetMapping("/utilisateurs")`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `public String utilisateurs(Model model) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `model.addAttribute("utilisateurs", utilisateurService.findAll());`
  Explication : elle met une donnée dans le Model pour Thymeleaf.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 40 : `return "admin/utilisateurs";`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `AdminController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`AdminController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

#### 📄 AuthController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/AuthController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `Auth` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/AuthController.java` contient 22 lignes. Il reçoit les adresses web liées à `Auth` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/AuthController.java
//
// CONCEPT SPRING BOOT : Un Controller reçoit une requête HTTP et retourne
// le nom d'une page Thymeleaf. Ici, il affiche la page de connexion.
// @Controller : indique à Spring que cette classe gère des pages web.
@Controller
public class AuthController {
    // @GetMapping : répond à une requête HTTP GET sur /login.
    @GetMapping("/login")
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/AuthController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Un Controller reçoit une requête HTTP et retourne`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// le nom d'une page Thymeleaf. Ici, il affiche la page de connexion.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `// @Controller : indique à Spring que cette classe gère des pages web.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 13 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 14 : `public class AuthController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `// @GetMapping : répond à une requête HTTP GET sur /login.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `@GetMapping("/login")`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `public String login() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `return "auth/login";`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `AuthController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`AuthController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

#### 📄 CongeController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/CongeController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `Conge` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/CongeController.java` contient 100 lignes. Il reçoit les adresses web liées à `Conge` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/CongeController.java
//
// CONCEPT SPRING BOOT : Ce Controller gère les pages de congés et utilise
// Principal pour connaître le login de l'utilisateur connecté.
// @Controller : gestion web des congés.
@Controller
// @RequestMapping : préfixe /conges.
@RequestMapping("/conges")
public class CongeController {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/CongeController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Controller gère les pages de congés et utilise`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Principal pour connaître le login de l'utilisateur connecté.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `// @Controller : gestion web des congés.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 34 : `// @RequestMapping : préfixe /conges.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `@RequestMapping("/conges")`
  Explication : elle donne le préfixe commun des URLs.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 36 : `public class CongeController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `private final CongeService congeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 42 : `private final EmployeService employeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 45 : `private final UtilisateurService utilisateurService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 48 : `public CongeController(CongeService congeService, EmployeService employeService, UtilisateurService utilisateurService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 55 : `@GetMapping`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 56 : `public String liste(Model model, Principal principal) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `CongeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`CongeController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

#### 📄 DashboardController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/DashboardController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `Dashboard` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/DashboardController.java` contient 47 lignes. Il reçoit les adresses web liées à `Dashboard` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/DashboardController.java
//
// CONCEPT SPRING BOOT : Ce Controller prépare le tableau de bord après connexion.
// Le Model transporte les compteurs Java vers le template Thymeleaf.
// @Controller : classe web Spring MVC.
@Controller
public class DashboardController {
    private final UtilisateurService utilisateurService;
    private final DashboardService dashboardService;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/DashboardController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Controller prépare le tableau de bord après connexion.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Le Model transporte les compteurs Java vers le template Thymeleaf.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `// @Controller : classe web Spring MVC.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `public class DashboardController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `private final UtilisateurService utilisateurService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `private final DashboardService dashboardService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `public DashboardController(UtilisateurService utilisateurService, DashboardService dashboardService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 34 : `@GetMapping("/")`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `public String home() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 36 : `return "redirect:/dashboard";`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 40 : `@GetMapping("/dashboard")`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 41 : `public String dashboard(Model model, Principal principal) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DashboardController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DashboardController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

#### 📄 DemandeAdministrativeController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/DemandeAdministrativeController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `DemandeAdministrative` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/DemandeAdministrativeController.java` contient 101 lignes. Il reçoit les adresses web liées à `DemandeAdministrative` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/DemandeAdministrativeController.java
//
// CONCEPT SPRING BOOT : Ce Controller suit le même cycle MVC que les congés,
// mais avec le workflow administratif EN_ATTENTE -> EN_COURS -> VALIDEE...
// @Controller : gestion web des demandes administratives.
@Controller
// @RequestMapping : préfixe /demandes.
@RequestMapping("/demandes")
public class DemandeAdministrativeController {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/DemandeAdministrativeController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Controller suit le même cycle MVC que les congés,`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// mais avec le workflow administratif EN_ATTENTE -> EN_COURS -> VALIDEE...`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `// @Controller : gestion web des demandes administratives.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 34 : `// @RequestMapping : préfixe /demandes.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `@RequestMapping("/demandes")`
  Explication : elle donne le préfixe commun des URLs.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 36 : `public class DemandeAdministrativeController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `private final DemandeAdministrativeService demandeAdministrativeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 42 : `private final EmployeService employeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 45 : `private final UtilisateurService utilisateurService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 48 : `public DemandeAdministrativeController(DemandeAdministrativeService demandeAdministrativeService, EmployeService employeService, UtilisateurService utilisateurService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 55 : `@GetMapping`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 56 : `public String liste(Model model, Principal principal) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DemandeAdministrativeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DemandeAdministrativeController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

#### 📄 DocumentController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/DocumentController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `Document` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/DocumentController.java` contient 77 lignes. Il reçoit les adresses web liées à `Document` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/DocumentController.java
//
// CONCEPT SPRING BOOT : MultipartFile représente un fichier envoyé par formulaire.
// Le Controller le transmet au Service, puis propose le téléchargement.
// @Controller : gestion web des documents.
@Controller
// @RequestMapping : préfixe /documents.
@RequestMapping("/documents")
public class DocumentController {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/DocumentController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : MultipartFile représente un fichier envoyé par formulaire.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// Le Controller le transmet au Service, puis propose le téléchargement.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `// @Controller : gestion web des documents.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `// @RequestMapping : préfixe /documents.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `@RequestMapping("/documents")`
  Explication : elle donne le préfixe commun des URLs.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `public class DocumentController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `private final DocumentService documentService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 36 : `private final EmployeService employeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `public DocumentController(DocumentService documentService, EmployeService employeService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 45 : `@GetMapping`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 46 : `public String liste(Model model) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 47 : `model.addAttribute("documents", documentService.findAll());`
  Explication : elle met une donnée dans le Model pour Thymeleaf.
  Pourquoi : dans `DocumentController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`DocumentController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

#### 📄 EmployeController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/EmployeController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `Employe` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/EmployeController.java` contient 105 lignes. Il reçoit les adresses web liées à `Employe` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/EmployeController.java
//
// CONCEPT SPRING BOOT : Ce Controller gère les fiches employés.
// @Valid déclenche la validation, BindingResult contient les erreurs de formulaire.
// @Controller : gestion des pages employés.
@Controller
// @RequestMapping : préfixe commun /employes.
@RequestMapping("/employes")
public class EmployeController {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/EmployeController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Controller gère les fiches employés.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// @Valid déclenche la validation, BindingResult contient les erreurs de formulaire.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `// @Controller : gestion des pages employés.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `// @RequestMapping : préfixe commun /employes.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `@RequestMapping("/employes")`
  Explication : elle donne le préfixe commun des URLs.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `public class EmployeController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `private final EmployeService employeService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 35 : `private final OrganisationService organisationService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `private final UtilisateurService utilisateurService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 41 : `public EmployeController(EmployeService employeService, OrganisationService organisationService, UtilisateurService utilisateurService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 49 : `model.addAttribute("departements", organisationService.findAllDepartements());`
  Explication : elle met une donnée dans le Model pour Thymeleaf.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 50 : `model.addAttribute("services", organisationService.findAllServices());`
  Explication : elle met une donnée dans le Model pour Thymeleaf.
  Pourquoi : dans `EmployeController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`EmployeController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

#### 📄 NotificationController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/NotificationController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `Notification` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/NotificationController.java` contient 54 lignes. Il reçoit les adresses web liées à `Notification` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/NotificationController.java
//
// CONCEPT SPRING BOOT : Ce Controller affiche les notifications de l'utilisateur
// connecté et permet de les marquer comme lues.
// @Controller : gestion web des notifications.
@Controller
// @RequestMapping : préfixe /notifications.
@RequestMapping("/notifications")
public class NotificationController {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/NotificationController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Controller affiche les notifications de l'utilisateur`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// connecté et permet de les marquer comme lues.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `// @Controller : gestion web des notifications.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `// @RequestMapping : préfixe /notifications.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `@RequestMapping("/notifications")`
  Explication : elle donne le préfixe commun des URLs.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `public class NotificationController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `private final NotificationService notificationService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `private final UtilisateurService utilisateurService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `public NotificationController(NotificationService notificationService, UtilisateurService utilisateurService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `@GetMapping`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 40 : `public String liste(Model model, Principal principal) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 41 : `Utilisateur utilisateur = utilisateurService.findByLogin(principal.getName());`
  Explication : elle déclenche une recherche en base.
  Pourquoi : dans `NotificationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`NotificationController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

#### 📄 OrganisationController.java
📍 Emplacement : src/main/java/com/gestionrh/controller/OrganisationController.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il reçoit les adresses web liées à `Organisation` et choisit la page à afficher.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le réceptionniste d'un hôtel. Il écoute ce que veut la personne et l'envoie vers la bonne chambre. Ici, le Controller reçoit `/employes`, `/conges` ou `/login`.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/controller/OrganisationController.java` contient 144 lignes. Il reçoit les adresses web liées à `Organisation` et choisit la page à afficher. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : controller/OrganisationController.java
//
// CONCEPT SPRING BOOT : Ce Controller montre le cycle CRUD complet :
// formulaire HTML -> POST -> Controller -> Service -> Repository -> PostgreSQL.
// @Controller : cette classe répond à des URLs web.
@Controller
// @RequestMapping : toutes les URLs commencent par /organisation.
@RequestMapping("/organisation")
public class OrganisationController {
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : controller/OrganisationController.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Ce Controller montre le cycle CRUD complet :`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// formulaire HTML -> POST -> Controller -> Service -> Repository -> PostgreSQL.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `// @Controller : cette classe répond à des URLs web.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `@Controller`
  Explication : elle dit que la classe reçoit des requêtes web.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `// @RequestMapping : toutes les URLs commencent par /organisation.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `@RequestMapping("/organisation")`
  Explication : elle donne le préfixe commun des URLs.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `public class OrganisationController {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `private final OrganisationService organisationService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `public OrganisationController(OrganisationService organisationService) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 38 : `@GetMapping`
  Explication : elle répond à une visite de page.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 39 : `public String index(Model model) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 40 : `model.addAttribute("departements", organisationService.findAllDepartements());`
  Explication : elle met une donnée dans le Model pour Thymeleaf.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 41 : `model.addAttribute("services", organisationService.findAllServices());`
  Explication : elle met une donnée dans le Model pour Thymeleaf.
  Pourquoi : dans `OrganisationController.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
`OrganisationController` reçoit une URL, appelle un Service, remplit `Model`, puis retourne un template.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer la classe dans `controller/`.
2. Ajouter `@Controller`.
3. Ajouter les mappings GET/POST.
4. Appeler le Service.
5. Retourner le nom du template.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Retourner un mauvais nom de template.
- Oublier une donnée dans `Model`.
- Utiliser GET pour modifier des données.

### Sous-section 1.5 — La configuration Spring Security

Spring Security est le vigile avec liste VIP.

#### 📄 SecurityConfig.java
📍 Emplacement : src/main/java/com/gestionrh/config/SecurityConfig.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il protège les pages avec les rôles et configure la connexion.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le vigile avec une liste VIP. Il vérifie si tu es connecté et si ton rôle t'autorise à entrer.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/config/SecurityConfig.java` contient 78 lignes. Il protège les pages avec les rôles et configure la connexion. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : config/SecurityConfig.java
//
// CONCEPT SPRING BOOT : Spring Security intercepte chaque requête HTTP avant
// les Controllers. Cette configuration définit qui peut accéder à quelles URLs,
// @Configuration : indique que cette classe déclare des objets Spring de configuration.
@Configuration
public class SecurityConfig {
    // @Bean : expose PasswordEncoder dans le contexte Spring pour pouvoir l'injecter ailleurs.
    @Bean
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : config/SecurityConfig.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : Spring Security intercepte chaque requête HTTP avant`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// les Controllers. Cette configuration définit qui peut accéder à quelles URLs,`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `// @Configuration : indique que cette classe déclare des objets Spring de configuration.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `@Configuration`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `public class SecurityConfig {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `// @Bean : expose PasswordEncoder dans le contexte Spring pour pouvoir l'injecter ailleurs.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `@Bean`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `public PasswordEncoder passwordEncoder() {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `return new BCryptPasswordEncoder();`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `// @Bean : configure la chaîne de filtres de sécurité HTTP.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `@Bean`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 32 : `public SecurityFilterChain securityFilterChain(HttpSecurity http, UtilisateurService utilisateurService) throws Exception {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 33 : `return http`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `SecurityConfig.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Il parle à `UtilisateurService` et influence tous les Controllers.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer `SecurityConfig`.
2. Déclarer `PasswordEncoder`.
3. Déclarer `SecurityFilterChain`.
4. Configurer login, logout et rôles.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Bloquer `/login`.
- Oublier BCrypt.
- Confondre rôle `ADMIN` et autorité `ROLE_ADMIN`.

### Sous-section 1.6 — Les Templates Thymeleaf (le frontend)

Thymeleaf est un document Word avec des champs à remplir.
Syntaxe : `th:text` remplit un texte, `th:each` répète, `th:if` conditionne, `th:href` crée un lien, `th:action` crée une adresse de formulaire, `sec:authorize` affiche selon le rôle.

#### 📄 utilisateur-form.html
📍 Emplacement : src/main/resources/templates/admin/utilisateur-form.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/admin/utilisateur-form.html` contient 17 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/admin/utilisateur-form.html
  CONCEPT THYMELEAF : ce formulaire crée un compte, le Service encodera ensuite le mot de passe.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <form th:action="@{/admin/utilisateurs}" th:object="${utilisateur}" method="post" class="card card-body">
        <div class="mb-3"><label class="form-label">Login</label><input class="form-control" th:field="*{login}"><div class="text-danger small" th:errors="*{login}"></div></div>
        <div class="mb-3"><label class="form-label">Mot de passe</label><input class="form-control" type="password" th:field="*{motDePasse}"><div class="text-danger small" th:errors="*{motDePasse}"></div></div>
        <div class="mb-3"><label class="form-label">Rôle</label><select class="form-select" th:field="*{role}"><option th:each="r : ${roles}" th:value="${r}" th:text="${r}"></option></select></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/admin/utilisateur-form.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : ce formulaire crée un compte, le Service encodera ensuite le mot de passe.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<form th:action="@{/admin/utilisateurs}" th:object="${utilisateur}" method="post" class="card card-body">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<div class="mb-3"><label class="form-label">Login</label><input class="form-control" th:field="*{login}"><div class="text-danger small" th:errors="*{login}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<div class="mb-3"><label class="form-label">Mot de passe</label><input class="form-control" type="password" th:field="*{motDePasse}"><div class="text-danger small" th:errors="*{motDePasse}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<div class="mb-3"><label class="form-label">Rôle</label><select class="form-select" th:field="*{role}"><option th:each="r : ${roles}" th:value="${r}" th:text="${r}"></option></select></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 13 : `<div class="form-check mb-3"><input class="form-check-input" type="checkbox" th:field="*{actif}"><label class="form-check-label">Actif</label></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateur-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 utilisateurs.html
📍 Emplacement : src/main/resources/templates/admin/utilisateurs.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/admin/utilisateurs.html` contient 11 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/admin/utilisateurs.html
  CONCEPT SPRING SECURITY : cette page est protégée par /admin/** dans SecurityConfig.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Comptes utilisateurs</h1><a class="btn btn-primary" th:href="@{/admin/utilisateurs/nouveau}">Créer un compte</a></div>
    <table class="table table-striped bg-white"><thead><tr><th>Login</th><th>Rôle</th><th>Actif</th></tr></thead><tbody><tr th:each="u : ${utilisateurs}"><td th:text="${u.login}"></td><td th:text="${u.role}"></td><td th:text="${u.actif}"></td></tr></tbody></table>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `utilisateurs.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/admin/utilisateurs.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `utilisateurs.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT SPRING SECURITY : cette page est protégée par /admin/** dans SecurityConfig.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `utilisateurs.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `utilisateurs.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `utilisateurs.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateurs.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 8 : `<div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Comptes utilisateurs</h1><a class="btn btn-primary" th:href="@{/admin/utilisateurs/nouveau}">Créer un compte</a></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateurs.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<table class="table table-striped bg-white"><thead><tr><th>Login</th><th>Rôle</th><th>Actif</th></tr></thead><tbody><tr th:each="u : ${utilisateurs}"><td th:text="${u.login}"></td><td th:text="${u.role}"></td><td th:text="${u.actif}"></td></tr></tbody></table>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `utilisateurs.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 login.html
📍 Emplacement : src/main/resources/templates/auth/login.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/auth/login.html` contient 41 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/auth/login.html
  CONCEPT THYMELEAF : Cette page affiche un formulaire HTML classique.
  Spring Security intercepte le POST /login et vérifie le compte en base.
-->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
                    <div th:if="${param.error}" class="alert alert-danger">Login ou mot de passe incorrect.</div>
                    <div th:if="${param.logout}" class="alert alert-success">Vous êtes déconnecté.</div>
                    <form th:action="@{/login}" method="post">
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/auth/login.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : Cette page affiche un formulaire HTML classique.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `Spring Security intercepte le POST /login et vérifie le compte en base.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 21 : `<div th:if="${param.error}" class="alert alert-danger">Login ou mot de passe incorrect.</div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 22 : `<div th:if="${param.logout}" class="alert alert-success">Vous êtes déconnecté.</div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `<form th:action="@{/login}" method="post">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `login.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 form.html
📍 Emplacement : src/main/resources/templates/conges/form.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/conges/form.html` contient 19 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/conges/form.html
  CONCEPT THYMELEAF : th:each crée les options depuis l'enum TypeConge.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <form th:action="@{/conges}" th:object="${demandeConge}" method="post" class="card card-body">
            <div class="col-md-4"><label class="form-label">Type</label><select class="form-select" th:field="*{typeConge}"><option th:each="t : ${types}" th:value="${t}" th:text="${t}"></option></select></div>
            <div class="col-md-4"><label class="form-label">Date début</label><input class="form-control" type="date" th:field="*{dateDebut}"></div>
            <div class="col-md-4"><label class="form-label">Date fin</label><input class="form-control" type="date" th:field="*{dateFin}"></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/conges/form.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : th:each crée les options depuis l'enum TypeConge.`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<form th:action="@{/conges}" th:object="${demandeConge}" method="post" class="card card-body">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<div class="col-md-4"><label class="form-label">Type</label><select class="form-select" th:field="*{typeConge}"><option th:each="t : ${types}" th:value="${t}" th:text="${t}"></option></select></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<div class="col-md-4"><label class="form-label">Date début</label><input class="form-control" type="date" th:field="*{dateDebut}"></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 13 : `<div class="col-md-4"><label class="form-label">Date fin</label><input class="form-control" type="date" th:field="*{dateFin}"></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 14 : `<div class="col-12"><label class="form-label">Motif</label><textarea class="form-control" th:field="*{motif}"></textarea></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 liste.html
📍 Emplacement : src/main/resources/templates/conges/liste.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/conges/liste.html` contient 14 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/conges/liste.html
  CONCEPT THYMELEAF + SECURITY : sec:authorize affiche des boutons seulement aux rôles autorisés.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" xmlns:sec="https://www.thymeleaf.org/extras/spring-security" th:replace="~{layout/base :: page(~{::main})}">
    <div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Congés</h1><a class="btn btn-primary" th:href="@{/conges/nouveau}">Nouvelle demande</a></div>
    <table class="table table-striped bg-white">
        <tbody><tr th:each="d : ${demandes}"><td th:text="${d.employe.prenom + ' ' + d.employe.nom}"></td><td th:text="${d.typeConge}"></td><td th:text="${d.dateDebut}"></td><td th:text="${d.dateFin}"></td><td th:text="${d.statut}"></td><td sec:authorize="hasAnyRole('ADMIN','RH','RESPONSABLE')" class="text-end"><form class="d-inline" th:action="@{/conges/traiter/{id}(id=${d.id})}" method="post"><input type="hidden" name="statut" value="VALIDEE"><button class="btn btn-sm btn-success">Valider</button></form> <form class="d-inline" th:action="@{/conges/traiter/{id}(id=${d.id})}" method="post"><input type="hidden" name="statut" value="REFUSEE"><button class="btn btn-sm btn-danger">Refuser</button></form></td></tr></tbody>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/conges/liste.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF + SECURITY : sec:authorize affiche des boutons seulement aux rôles autorisés.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" xmlns:sec="https://www.thymeleaf.org/extras/spring-security" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 8 : `<div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Congés</h1><a class="btn btn-primary" th:href="@{/conges/nouveau}">Nouvelle demande</a></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<table class="table table-striped bg-white">`
  Explication : c'est un tableau visible dans la page.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<tbody><tr th:each="d : ${demandes}"><td th:text="${d.employe.prenom + ' ' + d.employe.nom}"></td><td th:text="${d.typeConge}"></td><td th:text="${d.dateDebut}"></td><td th:text="${d.dateFin}"></td><td th:text="${d.statut}"></td><td sec:authorize="hasAnyRole('ADMIN','RH','RESPONSABLE')" class="text-end"><form class="d-inline" th:action="@{/conges/traiter/{id}(id=${d.id})}" method="post"><input type="hidden" name="statut" value="VALIDEE"><button class="btn btn-sm btn-success">Valider</button></form> <form class="d-inline" th:action="@{/conges/traiter/{id}(id=${d.id})}" method="post"><input type="hidden" name="statut" value="REFUSEE"><button class="btn btn-sm btn-danger">Refuser</button></form></td></tr></tbody>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 index.html
📍 Emplacement : src/main/resources/templates/dashboard/index.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/dashboard/index.html` contient 18 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/dashboard/index.html
  CONCEPT THYMELEAF : Le template lit les attributs "utilisateur" et "counters"
  ajoutés au Model par DashboardController.
-->
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <p class="text-muted">Connecté en tant que <strong th:text="${utilisateur.login}"></strong> avec le rôle <strong th:text="${utilisateur.role}"></strong>.</p>
        <div class="col-md-3"><div class="card"><div class="card-body"><div class="text-muted">Employés actifs</div><div class="display-6" th:text="${counters.employesActifs}">0</div></div></div></div>
        <div class="col-md-3"><div class="card"><div class="card-body"><div class="text-muted">Congés en attente</div><div class="display-6" th:text="${counters.congesEnAttente}">0</div></div></div></div>
        <div class="col-md-3"><div class="card"><div class="card-body"><div class="text-muted">Demandes en attente</div><div class="display-6" th:text="${counters.demandesEnAttente}">0</div></div></div></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/dashboard/index.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : Le template lit les attributs "utilisateur" et "counters"`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `ajoutés au Model par DashboardController.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 7 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<p class="text-muted">Connecté en tant que <strong th:text="${utilisateur.login}"></strong> avec le rôle <strong th:text="${utilisateur.role}"></strong>.</p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<div class="col-md-3"><div class="card"><div class="card-body"><div class="text-muted">Employés actifs</div><div class="display-6" th:text="${counters.employesActifs}">0</div></div></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 13 : `<div class="col-md-3"><div class="card"><div class="card-body"><div class="text-muted">Congés en attente</div><div class="display-6" th:text="${counters.congesEnAttente}">0</div></div></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 14 : `<div class="col-md-3"><div class="card"><div class="card-body"><div class="text-muted">Demandes en attente</div><div class="display-6" th:text="${counters.demandesEnAttente}">0</div></div></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `<div class="col-md-3"><div class="card"><div class="card-body"><div class="text-muted">Notifications non lues</div><div class="display-6" th:text="${counters.notificationsNonLues}">0</div></div></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 form.html
📍 Emplacement : src/main/resources/templates/demandes/form.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/demandes/form.html` contient 15 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/demandes/form.html
  CONCEPT THYMELEAF : th:field garde les valeurs saisies si la validation échoue.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <form th:action="@{/demandes}" th:object="${demandeAdministrative}" method="post" class="card card-body">
        <div class="mb-3"><label class="form-label">Type</label><select class="form-select" th:field="*{typeDemande}"><option th:each="t : ${types}" th:value="${t}" th:text="${t}"></option></select></div>
        <div class="mb-3"><label class="form-label">Description</label><textarea class="form-control" th:field="*{description}"></textarea></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/demandes/form.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : th:field garde les valeurs saisies si la validation échoue.`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<form th:action="@{/demandes}" th:object="${demandeAdministrative}" method="post" class="card card-body">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<div class="mb-3"><label class="form-label">Type</label><select class="form-select" th:field="*{typeDemande}"><option th:each="t : ${types}" th:value="${t}" th:text="${t}"></option></select></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<div class="mb-3"><label class="form-label">Description</label><textarea class="form-control" th:field="*{description}"></textarea></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 liste.html
📍 Emplacement : src/main/resources/templates/demandes/liste.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/demandes/liste.html` contient 14 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/demandes/liste.html
  CONCEPT THYMELEAF : un formulaire POST peut changer le statut d'une ligne.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" xmlns:sec="https://www.thymeleaf.org/extras/spring-security" th:replace="~{layout/base :: page(~{::main})}">
    <div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Demandes administratives</h1><a class="btn btn-primary" th:href="@{/demandes/nouveau}">Nouvelle demande</a></div>
    <table class="table table-striped bg-white">
        <tbody><tr th:each="d : ${demandes}"><td th:text="${d.employe.prenom + ' ' + d.employe.nom}"></td><td th:text="${d.typeDemande}"></td><td th:text="${d.description}"></td><td th:text="${d.statut}"></td><td sec:authorize="hasAnyRole('ADMIN','RH')" class="text-end"><form th:action="@{/demandes/statut/{id}(id=${d.id})}" method="post" class="d-flex gap-2"><select class="form-select form-select-sm" name="statut"><option th:each="s : ${statuts}" th:value="${s}" th:text="${s}"></option></select><button class="btn btn-sm btn-primary">Mettre à jour</button></form></td></tr></tbody>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/demandes/liste.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : un formulaire POST peut changer le statut d'une ligne.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" xmlns:sec="https://www.thymeleaf.org/extras/spring-security" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 8 : `<div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Demandes administratives</h1><a class="btn btn-primary" th:href="@{/demandes/nouveau}">Nouvelle demande</a></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<table class="table table-striped bg-white">`
  Explication : c'est un tableau visible dans la page.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<tbody><tr th:each="d : ${demandes}"><td th:text="${d.employe.prenom + ' ' + d.employe.nom}"></td><td th:text="${d.typeDemande}"></td><td th:text="${d.description}"></td><td th:text="${d.statut}"></td><td sec:authorize="hasAnyRole('ADMIN','RH')" class="text-end"><form th:action="@{/demandes/statut/{id}(id=${d.id})}" method="post" class="d-flex gap-2"><select class="form-select form-select-sm" name="statut"><option th:each="s : ${statuts}" th:value="${s}" th:text="${s}"></option></select><button class="btn btn-sm btn-primary">Mettre à jour</button></form></td></tr></tbody>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 liste.html
📍 Emplacement : src/main/resources/templates/documents/liste.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/documents/liste.html` contient 19 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/documents/liste.html
  CONCEPT SPRING MVC : enctype multipart/form-data permet d'envoyer un fichier.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <form th:action="@{/documents/upload}" method="post" enctype="multipart/form-data" class="card card-body mb-3">
            <div class="col-md-3"><label class="form-label">Employé</label><select class="form-select" name="employeId"><option value="">-</option><option th:each="e : ${employes}" th:value="${e.id}" th:text="${e.prenom + ' ' + e.nom}"></option></select></div>
    <table class="table table-striped bg-white"><thead><tr><th>Nom</th><th>Catégorie</th><th>Employé</th><th>Date</th><th></th></tr></thead><tbody><tr th:each="d : ${documents}"><td th:text="${d.nomFichier}"></td><td th:text="${d.categorie}"></td><td th:text="${d.employe != null ? d.employe.prenom + ' ' + d.employe.nom : '-'}"></td><td th:text="${d.dateAjout}"></td><td class="text-end"><a class="btn btn-sm btn-outline-primary" th:href="@{/documents/{id}/telecharger(id=${d.id})}">Télécharger</a></td></tr></tbody></table>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/documents/liste.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT SPRING MVC : enctype multipart/form-data permet d'envoyer un fichier.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<form th:action="@{/documents/upload}" method="post" enctype="multipart/form-data" class="card card-body mb-3">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 13 : `<div class="col-md-3"><label class="form-label">Employé</label><select class="form-select" name="employeId"><option value="">-</option><option th:each="e : ${employes}" th:value="${e.id}" th:text="${e.prenom + ' ' + e.nom}"></option></select></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `<table class="table table-striped bg-white"><thead><tr><th>Nom</th><th>Catégorie</th><th>Employé</th><th>Date</th><th></th></tr></thead><tbody><tr th:each="d : ${documents}"><td th:text="${d.nomFichier}"></td><td th:text="${d.categorie}"></td><td th:text="${d.employe != null ? d.employe.prenom + ' ' + d.employe.nom : '-'}"></td><td th:text="${d.dateAjout}"></td><td class="text-end"><a class="btn btn-sm btn-outline-primary" th:href="@{/documents/{id}/telecharger(id=${d.id})}">Télécharger</a></td></tr></tbody></table>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 detail.html
📍 Emplacement : src/main/resources/templates/employes/detail.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/employes/detail.html` contient 21 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/employes/detail.html
  CONCEPT THYMELEAF : th:text remplace le contenu HTML par la valeur Java.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <h1 class="h3 mb-3" th:text="${employe.prenom + ' ' + employe.nom}">Employé</h1>
        <p><strong>Matricule :</strong> <span th:text="${employe.matricule}"></span></p>
        <p><strong>Email :</strong> <span th:text="${employe.email}"></span></p>
        <p><strong>Date d'embauche :</strong> <span th:text="${employe.dateEmbauche}"></span></p>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/employes/detail.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : th:text remplace le contenu HTML par la valeur Java.`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 8 : `<h1 class="h3 mb-3" th:text="${employe.prenom + ' ' + employe.nom}">Employé</h1>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<p><strong>Matricule :</strong> <span th:text="${employe.matricule}"></span></p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<p><strong>Email :</strong> <span th:text="${employe.email}"></span></p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<p><strong>Date d'embauche :</strong> <span th:text="${employe.dateEmbauche}"></span></p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 13 : `<p><strong>Département :</strong> <span th:text="${employe.departement != null ? employe.departement.libelle : '-'}"></span></p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 14 : `<p><strong>Service :</strong> <span th:text="${employe.service != null ? employe.service.libelle : '-'}"></span></p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `<p><strong>Poste :</strong> <span th:text="${employe.poste != null ? employe.poste.libelle : '-'}"></span></p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `<p><strong>Compte :</strong> <span th:text="${employe.utilisateur != null ? employe.utilisateur.login : '-'}"></span></p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `<p><strong>Statut :</strong> <span th:text="${employe.statut}"></span></p>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `<form th:action="@{/employes/{id}/archiver(id=${employe.id})}" method="post"><button class="btn btn-warning" type="submit">Archiver</button></form>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `detail.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 form.html
📍 Emplacement : src/main/resources/templates/employes/form.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/employes/form.html` contient 26 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/employes/form.html
  CONCEPT THYMELEAF : les listes déroulantes envoient les ids, puis le Controller
  demande au Service de retrouver les objets JPA correspondants.
-->
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <form th:action="@{/employes}" th:object="${employe}" method="post" class="card card-body">
        <input type="hidden" th:field="*{id}">
            <div class="col-md-4"><label class="form-label">Matricule</label><input class="form-control" th:field="*{matricule}"><div class="text-danger small" th:errors="*{matricule}"></div></div>
            <div class="col-md-4"><label class="form-label">Nom</label><input class="form-control" th:field="*{nom}"><div class="text-danger small" th:errors="*{nom}"></div></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/employes/form.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : les listes déroulantes envoient les ids, puis le Controller`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `demande au Service de retrouver les objets JPA correspondants.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 7 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<form th:action="@{/employes}" th:object="${employe}" method="post" class="card card-body">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<input type="hidden" th:field="*{id}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 13 : `<div class="col-md-4"><label class="form-label">Matricule</label><input class="form-control" th:field="*{matricule}"><div class="text-danger small" th:errors="*{matricule}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 14 : `<div class="col-md-4"><label class="form-label">Nom</label><input class="form-control" th:field="*{nom}"><div class="text-danger small" th:errors="*{nom}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `<div class="col-md-4"><label class="form-label">Prénom</label><input class="form-control" th:field="*{prenom}"><div class="text-danger small" th:errors="*{prenom}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `<div class="col-md-6"><label class="form-label">Email</label><input class="form-control" th:field="*{email}"><div class="text-danger small" th:errors="*{email}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 17 : `<div class="col-md-6"><label class="form-label">Date d'embauche</label><input class="form-control" type="date" th:field="*{dateEmbauche}"><div class="text-danger small" th:errors="*{dateEmbauche}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `<div class="col-md-4"><label class="form-label">Département</label><select class="form-select" name="departementId"><option value="">-</option><option th:each="d : ${departements}" th:value="${d.id}" th:selected="${employe.departement != null and employe.departement.id == d.id}" th:text="${d.libelle}"></option></select></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `<div class="col-md-4"><label class="form-label">Service</label><select class="form-select" name="serviceId"><option value="">-</option><option th:each="s : ${services}" th:value="${s.id}" th:selected="${employe.service != null and employe.service.id == s.id}" th:text="${s.libelle}"></option></select></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `<div class="col-md-4"><label class="form-label">Poste</label><select class="form-select" name="posteId"><option value="">-</option><option th:each="p : ${postes}" th:value="${p.id}" th:selected="${employe.poste != null and employe.poste.id == p.id}" th:text="${p.libelle}"></option></select></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 liste.html
📍 Emplacement : src/main/resources/templates/employes/liste.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/employes/liste.html` contient 15 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/employes/liste.html
  CONCEPT THYMELEAF : th:href construit des URLs Spring MVC avec paramètres.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Employés</h1><a class="btn btn-primary" th:href="@{/employes/nouveau}">Nouvel employé</a></div>
    <form class="row g-2 mb-3" method="get" th:action="@{/employes}"><div class="col-md-10"><input class="form-control" name="keyword" th:value="${keyword}" placeholder="Rechercher par nom, prénom ou département"></div><div class="col-md-2"><button class="btn btn-outline-primary w-100">Rechercher</button></div></form>
    <table class="table table-striped bg-white">
        <tbody><tr th:each="e : ${employes}"><td th:text="${e.matricule}"></td><td th:text="${e.prenom + ' ' + e.nom}"></td><td th:text="${e.email}"></td><td th:text="${e.departement != null ? e.departement.libelle : '-'}"></td><td th:text="${e.statut}"></td><td class="text-end"><a class="btn btn-sm btn-outline-secondary" th:href="@{/employes/{id}(id=${e.id})}">Voir</a> <a class="btn btn-sm btn-outline-primary" th:href="@{/employes/{id}/modifier(id=${e.id})}">Modifier</a></td></tr></tbody>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/employes/liste.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : th:href construit des URLs Spring MVC avec paramètres.`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 8 : `<div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Employés</h1><a class="btn btn-primary" th:href="@{/employes/nouveau}">Nouvel employé</a></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<form class="row g-2 mb-3" method="get" th:action="@{/employes}"><div class="col-md-10"><input class="form-control" name="keyword" th:value="${keyword}" placeholder="Rechercher par nom, prénom ou département"></div><div class="col-md-2"><button class="btn btn-outline-primary w-100">Rechercher</button></div></form>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<table class="table table-striped bg-white">`
  Explication : c'est un tableau visible dans la page.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<tbody><tr th:each="e : ${employes}"><td th:text="${e.matricule}"></td><td th:text="${e.prenom + ' ' + e.nom}"></td><td th:text="${e.email}"></td><td th:text="${e.departement != null ? e.departement.libelle : '-'}"></td><td th:text="${e.statut}"></td><td class="text-end"><a class="btn btn-sm btn-outline-secondary" th:href="@{/employes/{id}(id=${e.id})}">Voir</a> <a class="btn btn-sm btn-outline-primary" th:href="@{/employes/{id}/modifier(id=${e.id})}">Modifier</a></td></tr></tbody>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 base.html
📍 Emplacement : src/main/resources/templates/layout/base.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/layout/base.html` contient 47 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/layout/base.html
  CONCEPT THYMELEAF : Ce layout est le squelette commun des pages.
  Les autres templates injectent leur contenu dans le fragment "page".
  Bootstrap 5 est chargé par CDN pour éviter tout fichier CSS custom.
<html lang="fr" xmlns:th="http://www.thymeleaf.org" xmlns:sec="https://www.thymeleaf.org/extras/spring-security" th:fragment="page(content)">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
        <a class="navbar-brand" th:href="@{/dashboard}">Plateforme RH</a>
                <li class="nav-item"><a class="nav-link" th:href="@{/dashboard}">Dashboard</a></li>
                <li class="nav-item" sec:authorize="hasAnyRole('ADMIN','RH')"><a class="nav-link" th:href="@{/employes}">Employés</a></li>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/layout/base.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : Ce layout est le squelette commun des pages.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `Les autres templates injectent leur contenu dans le fragment "page".`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `Bootstrap 5 est chargé par CDN pour éviter tout fichier CSS custom.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 8 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" xmlns:sec="https://www.thymeleaf.org/extras/spring-security" th:fragment="page(content)">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 13 : `<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 18 : `<a class="navbar-brand" th:href="@{/dashboard}">Plateforme RH</a>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `<li class="nav-item"><a class="nav-link" th:href="@{/dashboard}">Dashboard</a></li>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `<li class="nav-item" sec:authorize="hasAnyRole('ADMIN','RH')"><a class="nav-link" th:href="@{/employes}">Employés</a></li>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 26 : `<li class="nav-item" sec:authorize="hasAnyRole('ADMIN','RH')"><a class="nav-link" th:href="@{/organisation}">Organisation</a></li>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 27 : `<li class="nav-item"><a class="nav-link" th:href="@{/conges}">Congés</a></li>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 28 : `<li class="nav-item"><a class="nav-link" th:href="@{/demandes}">Demandes</a></li>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 29 : `<li class="nav-item" sec:authorize="hasAnyRole('ADMIN','RH','RESPONSABLE')"><a class="nav-link" th:href="@{/documents}">Documents</a></li>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 30 : `<li class="nav-item"><a class="nav-link" th:href="@{/notifications}">Notifications</a></li>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `<li class="nav-item" sec:authorize="hasRole('ADMIN')"><a class="nav-link" th:href="@{/admin/utilisateurs}">Comptes</a></li>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `base.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 liste.html
📍 Emplacement : src/main/resources/templates/notifications/liste.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/notifications/liste.html` contient 11 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/notifications/liste.html
  CONCEPT THYMELEAF : th:if affiche une classe visuelle selon une condition.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Mes notifications</h1><form th:action="@{/notifications/lire}" method="post"><button class="btn btn-outline-primary">Tout marquer comme lu</button></form></div>
    <div class="list-group"><div th:each="n : ${notifications}" class="list-group-item" th:classappend="${!n.lue} ? ' list-group-item-warning'"><div th:text="${n.message}"></div><small class="text-muted" th:text="${n.dateEnvoi}"></small></div></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/notifications/liste.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : th:if affiche une classe visuelle selon une condition.`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 8 : `<div class="d-flex justify-content-between align-items-center mb-3"><h1 class="h3">Mes notifications</h1><form th:action="@{/notifications/lire}" method="post"><button class="btn btn-outline-primary">Tout marquer comme lu</button></form></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<div class="list-group"><div th:each="n : ${notifications}" class="list-group-item" th:classappend="${!n.lue} ? ' list-group-item-warning'"><div th:text="${n.message}"></div><small class="text-muted" th:text="${n.dateEnvoi}"></small></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `liste.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 departement-form.html
📍 Emplacement : src/main/resources/templates/organisation/departement-form.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/organisation/departement-form.html` contient 16 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/organisation/departement-form.html
  CONCEPT THYMELEAF : th:field lie les champs HTML aux propriétés Java.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <form th:action="@{/organisation/departements}" th:object="${departement}" method="post" class="card card-body">
        <input type="hidden" th:field="*{id}">
        <div class="mb-3"><label class="form-label">Libellé</label><input class="form-control" th:field="*{libelle}"><div class="text-danger small" th:errors="*{libelle}"></div></div>
        <div class="mb-3"><label class="form-label">Description</label><textarea class="form-control" th:field="*{description}"></textarea></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/organisation/departement-form.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : th:field lie les champs HTML aux propriétés Java.`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<form th:action="@{/organisation/departements}" th:object="${departement}" method="post" class="card card-body">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<input type="hidden" th:field="*{id}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<div class="mb-3"><label class="form-label">Libellé</label><input class="form-control" th:field="*{libelle}"><div class="text-danger small" th:errors="*{libelle}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<div class="mb-3"><label class="form-label">Description</label><textarea class="form-control" th:field="*{description}"></textarea></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `departement-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 index.html
📍 Emplacement : src/main/resources/templates/organisation/index.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/organisation/index.html` contient 24 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/organisation/index.html
  CONCEPT THYMELEAF : th:each parcourt les listes Java envoyées par le Controller.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
            <div class="d-flex justify-content-between align-items-center mb-2"><h2 class="h5">Départements</h2><a class="btn btn-sm btn-primary" th:href="@{/organisation/departements/nouveau}">Ajouter</a></div>
            <table class="table table-sm table-striped bg-white"><tbody><tr th:each="d : ${departements}"><td th:text="${d.libelle}"></td><td class="text-end"><a class="btn btn-sm btn-outline-secondary" th:href="@{/organisation/departements/{id}/modifier(id=${d.id})}">Modifier</a></td></tr></tbody></table>
            <div class="d-flex justify-content-between align-items-center mb-2"><h2 class="h5">Services</h2><a class="btn btn-sm btn-primary" th:href="@{/organisation/services/nouveau}">Ajouter</a></div>
            <table class="table table-sm table-striped bg-white"><tbody><tr th:each="s : ${services}"><td th:text="${s.libelle}"></td><td class="text-end"><a class="btn btn-sm btn-outline-secondary" th:href="@{/organisation/services/{id}/modifier(id=${s.id})}">Modifier</a></td></tr></tbody></table>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/organisation/index.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : th:each parcourt les listes Java envoyées par le Controller.`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<div class="d-flex justify-content-between align-items-center mb-2"><h2 class="h5">Départements</h2><a class="btn btn-sm btn-primary" th:href="@{/organisation/departements/nouveau}">Ajouter</a></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<table class="table table-sm table-striped bg-white"><tbody><tr th:each="d : ${departements}"><td th:text="${d.libelle}"></td><td class="text-end"><a class="btn btn-sm btn-outline-secondary" th:href="@{/organisation/departements/{id}/modifier(id=${d.id})}">Modifier</a></td></tr></tbody></table>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 15 : `<div class="d-flex justify-content-between align-items-center mb-2"><h2 class="h5">Services</h2><a class="btn btn-sm btn-primary" th:href="@{/organisation/services/nouveau}">Ajouter</a></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 16 : `<table class="table table-sm table-striped bg-white"><tbody><tr th:each="s : ${services}"><td th:text="${s.libelle}"></td><td class="text-end"><a class="btn btn-sm btn-outline-secondary" th:href="@{/organisation/services/{id}/modifier(id=${s.id})}">Modifier</a></td></tr></tbody></table>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 19 : `<div class="d-flex justify-content-between align-items-center mb-2"><h2 class="h5">Postes</h2><a class="btn btn-sm btn-primary" th:href="@{/organisation/postes/nouveau}">Ajouter</a></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 20 : `<table class="table table-sm table-striped bg-white"><tbody><tr th:each="p : ${postes}"><td th:text="${p.libelle}"></td><td class="text-end"><a class="btn btn-sm btn-outline-secondary" th:href="@{/organisation/postes/{id}/modifier(id=${p.id})}">Modifier</a></td></tr></tbody></table>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `index.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 poste-form.html
📍 Emplacement : src/main/resources/templates/organisation/poste-form.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/organisation/poste-form.html` contient 16 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/organisation/poste-form.html
  CONCEPT THYMELEAF : le même formulaire sert à créer ou modifier grâce au champ id caché.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <form th:action="@{/organisation/postes}" th:object="${poste}" method="post" class="card card-body">
        <input type="hidden" th:field="*{id}">
        <div class="mb-3"><label class="form-label">Libellé</label><input class="form-control" th:field="*{libelle}"><div class="text-danger small" th:errors="*{libelle}"></div></div>
        <div class="mb-3"><label class="form-label">Description</label><textarea class="form-control" th:field="*{description}"></textarea></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/organisation/poste-form.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : le même formulaire sert à créer ou modifier grâce au champ id caché.`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<form th:action="@{/organisation/postes}" th:object="${poste}" method="post" class="card card-body">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<input type="hidden" th:field="*{id}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<div class="mb-3"><label class="form-label">Libellé</label><input class="form-control" th:field="*{libelle}"><div class="text-danger small" th:errors="*{libelle}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<div class="mb-3"><label class="form-label">Description</label><textarea class="form-control" th:field="*{description}"></textarea></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `poste-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

#### 📄 service-form.html
📍 Emplacement : src/main/resources/templates/organisation/service-form.html

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il construit une page HTML visible par l'utilisateur.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est un document Word avec des trous à remplir. Thymeleaf remplace les trous par de vraies données Java, puis le navigateur voit du HTML normal.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/resources/templates/organisation/service-form.html` contient 16 lignes. Il construit une page HTML visible par l'utilisateur. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```html
<!--
  FICHIER : templates/organisation/service-form.html
  CONCEPT THYMELEAF : th:object définit l'objet de formulaire courant.
-->
<!doctype html>
<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">
    <form th:action="@{/organisation/services}" th:object="${serviceRh}" method="post" class="card card-body">
        <input type="hidden" th:field="*{id}">
        <div class="mb-3"><label class="form-label">Libellé</label><input class="form-control" th:field="*{libelle}"><div class="text-danger small" th:errors="*{libelle}"></div></div>
        <div class="mb-3"><label class="form-label">Description</label><textarea class="form-control" th:field="*{description}"></textarea></div>
```
Lecture guidée :
- Ligne 1 : `<!--`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `FICHIER : templates/organisation/service-form.html`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `CONCEPT THYMELEAF : th:object définit l'objet de formulaire courant.`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `-->`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `<!doctype html>`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 6 : `<html lang="fr" xmlns:th="http://www.thymeleaf.org" th:replace="~{layout/base :: page(~{::main})}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 9 : `<form th:action="@{/organisation/services}" th:object="${serviceRh}" method="post" class="card card-body">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 10 : `<input type="hidden" th:field="*{id}">`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 11 : `<div class="mb-3"><label class="form-label">Libellé</label><input class="form-control" th:field="*{libelle}"><div class="text-danger small" th:errors="*{libelle}"></div></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 12 : `<div class="mb-3"><label class="form-label">Description</label><textarea class="form-control" th:field="*{description}"></textarea></div>`
  Explication : Thymeleaf remplacera cette partie côté serveur.
  Pourquoi : dans `service-form.html`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Ce template reçoit les variables envoyées par un Controller via `Model`.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer le fichier dans `templates/`.
2. Écrire le HTML.
3. Ajouter les `th:` nécessaires.
4. Vérifier que le Controller retourne ce chemin.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Utiliser une variable absente du Model.
- Écrire un mauvais `th:href`.
- Oublier `th:object` avec `th:field`.

### Sous-section 1.7 — Le DataInitializer

CommandLineRunner est le technicien qui prépare la salle avant ouverture.

#### 📄 DataInitializer.java
📍 Emplacement : src/main/java/com/gestionrh/config/DataInitializer.java

🎯 À QUOI ÇA SERT EN UNE PHRASE SIMPLE ?
Il crée les données de départ au démarrage.

🏠 ANALOGIE DE LA VIE RÉELLE
C'est le technicien qui prépare la salle avant l'arrivée du public. Il pose le compte admin et quelques données de départ.

🔍 CE QUE LE FICHIER FAIT DANS LE PROJET
Le fichier `src/main/java/com/gestionrh/config/DataInitializer.java` contient 89 lignes. Il crée les données de départ au démarrage. Il participe au chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template selon son rôle.

📝 EXPLICATION DU CODE LIGNE PAR LIGNE
Extraits exacts importants du fichier réel :
```java
// ============================================================
// FICHIER : config/DataInitializer.java
//
// CONCEPT SPRING BOOT : CommandLineRunner exécute du code automatiquement
// après le démarrage de l'application. Ici, on crée les premières données.
// @Component : Spring crée ce composant automatiquement au démarrage.
@Component
public class DataInitializer implements CommandLineRunner {
    private final UtilisateurRepository utilisateurRepository;
    private final UtilisateurService utilisateurService;
```
Lecture guidée :
- Ligne 1 : `// ============================================================`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 2 : `// FICHIER : config/DataInitializer.java`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 3 : `//`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 4 : `// CONCEPT SPRING BOOT : CommandLineRunner exécute du code automatiquement`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 5 : `// après le démarrage de l'application. Ici, on crée les premières données.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 23 : `// @Component : Spring crée ce composant automatiquement au démarrage.`
  Explication : c'est un commentaire pour expliquer aux humains.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 24 : `@Component`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 25 : `public class DataInitializer implements CommandLineRunner {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 31 : `private final UtilisateurRepository utilisateurRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 34 : `private final UtilisateurService utilisateurService;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 37 : `private final DepartementRepository departementRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 40 : `private final ServiceRepository serviceRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 43 : `private final PosteRepository posteRepository;`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 46 : `public DataInitializer(UtilisateurRepository utilisateurRepository, UtilisateurService utilisateurService, DepartementRepository departementRepository, ServiceRepository serviceRepository, PosteRepository posteRepository) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 55 : `@Override`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.
- Ligne 56 : `public void run(String... args) {`
  Explication : elle participe au comportement principal du fichier.
  Pourquoi : dans `DataInitializer.java`, cette ligne aide le fichier à remplir son rôle dans le projet réel.

🔗 COMMENT CE FICHIER EST LIÉ AUX AUTRES ?
Il parle aux Repositories et à `UtilisateurService` au démarrage.

🛠️ COMMENT LE RECRÉER DE ZÉRO ?
1. Créer `DataInitializer`.
2. Implémenter `CommandLineRunner`.
3. Vérifier si les données existent.
4. Créer admin et données exemple.

⚠️ LES ERREURS FRÉQUENTES À ÉVITER
- Créer les données en double.
- Oublier d’encoder le mot de passe.
- Démarrer sans PostgreSQL.

---

## PARTIE 2 — LES FICHIERS QUE TU N'AS PAS À ÉCRIRE MAIS QUI DOIVENT EXISTER

> Ces fichiers sont soit générés automatiquement, soit des fichiers standard que tu copies-colles.

#### ⚙️ GestionRhApplication.java

🎯 POURQUOI IL EXISTE
Il démarre l’application.

🏠 ANALOGIE
Interrupteur principal de la maison.

✅ CE QUE TU DOIS SAVOIR FAIRE AVEC LUI
Le laisser presque tel quel.

🚫 CE QUE TU N'AS PAS BESOIN DE COMPRENDRE EN DÉTAIL
Spring scanne automatiquement les composants.

#### ⚙️ pom.xml

🎯 POURQUOI IL EXISTE
Il déclare les dépendances Maven.

🏠 ANALOGIE
Liste de courses.

✅ CE QUE TU DOIS SAVOIR FAIRE AVEC LUI
Modifier les dépendances si besoin.

🚫 CE QUE TU N'AS PAS BESOIN DE COMPRENDRE EN DÉTAIL
Maven gère les téléchargements et versions.

#### ⚙️ application.properties

🎯 POURQUOI IL EXISTE
Il configure PostgreSQL, JPA, Thymeleaf, uploads et le port.

🏠 ANALOGIE
Panneau de réglage du four.

✅ CE QUE TU DOIS SAVOIR FAIRE AVEC LUI
Changer surtout URL, username, password.

🚫 CE QUE TU N'AS PAS BESOIN DE COMPRENDRE EN DÉTAIL
Spring Boot lit tout seul les propriétés.

#### ⚙️ target/

🎯 POURQUOI IL EXISTE
Il contient les fichiers compilés.

🏠 ANALOGIE
Fichiers temporaires d’un micro-ondes.

✅ CE QUE TU DOIS SAVOIR FAIRE AVEC LUI
Ne pas toucher ; supprimer avec `mvn clean` si besoin.

🚫 CE QUE TU N'AS PAS BESOIN DE COMPRENDRE EN DÉTAIL
Maven le reconstruit automatiquement.

#### ⚙️ .mvn/ et mvnw

🎯 POURQUOI IL EXISTE
Ils permettent de lancer Maven sans installation globale.

🏠 ANALOGIE
Mode d’emploi livré avec l’appareil.

✅ CE QUE TU DOIS SAVOIR FAIRE AVEC LUI
Les copier depuis Spring Initializr si tu veux.

🚫 CE QUE TU N'AS PAS BESOIN DE COMPRENDRE EN DÉTAIL
Le wrapper télécharge Maven lui-même.

---

## PARTIE 3 — LE CHEMIN COMPLET D'UNE REQUÊTE (DE A À Z)

### Scénario 1 — Un employé se connecte
1. L’employé tape `http://localhost:8080/login`.
Le navigateur demande la page de connexion.
2. Fichier reçu : `AuthController.java`.
```java
@GetMapping("/login")
public String login() {
    return "auth/login";
}
```
3. Spring Security intervient dans `SecurityConfig.java`.
```java
.requestMatchers("/login", "/css/**", "/js/**").permitAll()
.formLogin(form -> form.loginPage("/login"))
```
4. Table interrogée : `utilisateurs`.
```sql
select * from utilisateurs where login = ?;
```
5. Template retourné : `templates/auth/login.html`.
```html
<form th:action="@{/login}" method="post"> ... </form>
```
6. À l’écran.
Deux champs apparaissent : login et mot de passe. Si tout est bon, redirection vers `/dashboard`.

### Scénario 2 — Un employé soumet une demande de congé
1. L’employé clique sur Soumettre.
Le formulaire `templates/conges/form.html` envoie un POST vers `/conges`.
2. Le Controller reçoit.
```java
@PostMapping
public String soumettre(@Valid @ModelAttribute DemandeConge demandeConge, ...)
```
3. Le compte connecté est lu.
```java
Utilisateur utilisateur = utilisateurService.findByLogin(principal.getName());
```
4. La fiche employé est retrouvée.
```java
Employe employe = employeService.findByUtilisateur(utilisateur).orElse(null);
```
5. Le Service enregistre.
```java
demandeConge.setStatut(StatutConge.EN_ATTENTE);
demandeCongeRepository.save(demandeConge);
```
6. SQL équivalent.
```sql
insert into demandes_conges (...) values (..., 'EN_ATTENTE', ...);
```
7. Note réelle.
Le projet trace l’historique ; la notification automatique se fait lors du changement de statut, car aucun responsable d’équipe précis n’est modélisé.

### Scénario 3 — Le responsable valide une demande
1. Le responsable clique sur Valider.
Le bouton existe dans `templates/conges/liste.html`.
2. Le formulaire envoie `VALIDEE`.
```html
<input type="hidden" name="statut" value="VALIDEE">
```
3. Le Controller reçoit.
```java
@PostMapping("/traiter/{id}")
public String traiter(@PathVariable Long id, @RequestParam StatutConge statut, ...)
```
4. Le Service modifie.
```java
demande.setStatut(statut);
demande.setTraiteePar(responsable);
demandeCongeRepository.save(demande);
```
5. Notification créée.
```java
notificationService.creerNotification(demande.getEmploye().getUtilisateur(), "Votre demande de congé #" + id + " est maintenant " + statut);
```
6. Tables touchées.
`demandes_conges` est mise à jour et `notifications` reçoit une nouvelle ligne.

---

## PARTIE 4 — LA BASE DE DONNÉES EXPLIQUÉE

### 4.1 — Le schéma complet
- `utilisateurs` : `id`, `login`, `mot_de_passe`, `role`, `actif`.
- `employes` : `id`, `matricule`, `nom`, `prenom`, `email`, `date_embauche`, `departement_id`, `service_id`, `poste_id`, `utilisateur_id`, `statut`.
- `departements` : `id`, `libelle`, `description`.
- `services` : `id`, `libelle`, `description`.
- `postes` : `id`, `libelle`, `description`.
- `demandes_conges` : `id`, `employe_id`, `type_conge`, `date_debut`, `date_fin`, `motif`, `statut`, `date_soumission`, `traitee_par_id`.
- `demandes_administratives` : `id`, `employe_id`, `type_demande`, `description`, `statut`, `date_soumission`.
- `documents` : `id`, `nom_fichier`, `chemin`, `categorie`, `date_ajout`, `employe_id`, `demande_administrative_id`.
- `notifications` : `id`, `destinataire_id`, `message`, `date_envoi`, `lue`.
- `historique_actions` : `id`, `utilisateur_id`, `action`, `date_action`.
OneToMany : un département peut avoir plusieurs employés, comme une école a plusieurs élèves. ManyToOne : chaque employé appartient à un département, comme chaque élève est dans une classe. OneToOne : chaque employé a au plus un compte utilisateur, comme une personne a un passeport.

### 4.2 — Ce que fait Hibernate automatiquement
Hibernate lit les annotations et fabrique du SQL. Exemple réel : `UtilisateurRepository.findByLogin` devient environ :
```sql
select * from utilisateurs where login = ?;
```
`EmployeRepository.countByStatut(StatutEmploye.ACTIF)` devient environ :
```sql
select count(*) from employes where statut = 'ACTIF';
```

### 4.3 — Les migrations : `spring.jpa.hibernate.ddl-auto=update`
`update` demande à Hibernate d’adapter les tables au code. Analogie : un technicien réarrange la salle selon le nouveau plan. En développement, c’est pratique. En production, il faut préférer des migrations contrôlées, car les vraies données sont précieuses.

---

## PARTIE 5 — GLOSSAIRE COMPLET

**@Autowired**
Définition simple : `@Autowired` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Autowired` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Bean**
Définition simple : `@Bean` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Bean` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Column**
Définition simple : `@Column` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Column` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Component**
Définition simple : `@Component` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Component` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Controller**
Définition simple : `@Controller` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Controller` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Entity**
Définition simple : `@Entity` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Entity` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@GetMapping**
Définition simple : `@GetMapping` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@GetMapping` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Id**
Définition simple : `@Id` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Id` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@ManyToOne**
Définition simple : `@ManyToOne` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@ManyToOne` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@NotBlank**
Définition simple : `@NotBlank` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@NotBlank` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@OneToMany**
Définition simple : `@OneToMany` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@OneToMany` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@OneToOne**
Définition simple : `@OneToOne` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@OneToOne` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@PostMapping**
Définition simple : `@PostMapping` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@PostMapping` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Repository**
Définition simple : `@Repository` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Repository` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@RequestMapping**
Définition simple : `@RequestMapping` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@RequestMapping` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@RequestParam**
Définition simple : `@RequestParam` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@RequestParam` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Service**
Définition simple : `@Service` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Service` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**@Table**
Définition simple : `@Table` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `@Table` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**BCrypt**
Définition simple : `BCrypt` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `BCrypt` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Bootstrap**
Définition simple : `Bootstrap` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Bootstrap` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**CRUD**
Définition simple : `CRUD` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `CRUD` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**CommandLineRunner**
Définition simple : `CommandLineRunner` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `CommandLineRunner` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**DTO**
Définition simple : `DTO` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `DTO` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Entity**
Définition simple : `Entity` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Entity` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**ForeignKey**
Définition simple : `ForeignKey` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `ForeignKey` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**GET**
Définition simple : `GET` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `GET` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**HTML**
Définition simple : `HTML` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `HTML` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**HTTP**
Définition simple : `HTTP` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `HTTP` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**HTTPS**
Définition simple : `HTTPS` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `HTTPS` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Hibernate**
Définition simple : `Hibernate` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Hibernate` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**JPA**
Définition simple : `JPA` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `JPA` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**JSON**
Définition simple : `JSON` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `JSON` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**MVC**
Définition simple : `MVC` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `MVC` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Maven**
Définition simple : `Maven` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Maven` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Model**
Définition simple : `Model` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Model` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**ORM**
Définition simple : `ORM` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `ORM` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**POST**
Définition simple : `POST` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `POST` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**PostgreSQL**
Définition simple : `PostgreSQL` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `PostgreSQL` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**PrimaryKey**
Définition simple : `PrimaryKey` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `PrimaryKey` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**REST**
Définition simple : `REST` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `REST` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Repository**
Définition simple : `Repository` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Repository` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Service**
Définition simple : `Service` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Service` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Spring Boot**
Définition simple : `Spring Boot` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Spring Boot` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Spring Security**
Définition simple : `Spring Security` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Spring Security` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**Thymeleaf**
Définition simple : `Thymeleaf` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `Thymeleaf` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**URL**
Définition simple : `URL` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `URL` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**UserDetails**
Définition simple : `UserDetails` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `UserDetails` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**UserDetailsService**
Définition simple : `UserDetailsService` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `UserDetailsService` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**th:each**
Définition simple : `th:each` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `th:each` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**th:if**
Définition simple : `th:if` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `th:if` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

**th:text**
Définition simple : `th:text` est un mot du projet qui aide Spring Boot à organiser, afficher, protéger ou enregistrer les données.
Analogie : pense à un outil dans une boîte à outils ; chaque outil a une mission simple.
Dans ce projet : `th:text` apparaît dans le code, les templates ou la configuration selon son rôle. Regarde les sections précédentes pour voir les fichiers exacts liés.

---

## PARTIE 6 — GUIDE DE RECRÉATION DU PROJET (FEUILLE DE ROUTE)

## Étape 1 — Créer le projet Spring Boot
[ ] Aller sur https://start.spring.io
[ ] Choisir Maven, Java 17, Spring Boot 3.x
[ ] Ajouter Web, Thymeleaf, Security, Data JPA, PostgreSQL, Validation, Lombok
[ ] Télécharger et extraire le ZIP
Temps estimé : 5 minutes

## Étape 2 — Configurer PostgreSQL
[ ] Créer `gestion_rh_db`
[ ] Modifier `application.properties`
[ ] Tester la connexion
Temps estimé : 10 minutes

## Étape 3 — Créer les Entities
[ ] Créer les enums
[ ] Créer Departement, Service, Poste
[ ] Créer Utilisateur
[ ] Créer Employe
[ ] Créer demandes, documents, notifications, historique
Temps estimé : 45 minutes

## Étape 4 — Créer les Repositories
[ ] Un fichier par Entity
[ ] Étendre JpaRepository
[ ] Ajouter findBy et countBy
Temps estimé : 20 minutes

## Étape 5 — Créer les Services
[ ] UtilisateurService
[ ] OrganisationService
[ ] EmployeService
[ ] CongeService
[ ] DemandeAdministrativeService
[ ] DocumentService
[ ] NotificationService
[ ] DashboardService
Temps estimé : 60 minutes

## Étape 6 — Créer SecurityConfig
[ ] BCrypt
[ ] URL autorisées
[ ] Login/logout
[ ] Rôles
Temps estimé : 35 minutes

## Étape 7 — Créer les Controllers
[ ] Auth
[ ] Dashboard
[ ] Organisation
[ ] Employe
[ ] Conges
[ ] Demandes
[ ] Documents
[ ] Notifications
[ ] Admin
Temps estimé : 90 minutes

## Étape 8 — Créer les Templates
[ ] base
[ ] login
[ ] dashboard
[ ] CRUD organisation
[ ] CRUD employés
[ ] congés
[ ] demandes
[ ] documents
[ ] notifications
[ ] admin
Temps estimé : 120 minutes

## Étape 9 — Tester
[ ] mvn compile
[ ] mvn spring-boot:run
[ ] Login admin
[ ] Créer un compte
[ ] Créer une fiche employé
[ ] Tester congé et notification
Temps estimé : 60 minutes

---

## PARTIE 7 — LES ERREURS FRÉQUENTES ET COMMENT LES RÉSOUDRE

### Failed to configure a DataSource
Ce que ça veut dire : PostgreSQL n’est pas démarré ou la configuration est mauvaise.
Comment résoudre :
- Démarrer PostgreSQL
- Créer la base
- Vérifier username/password

### WhiteLabel Error Page
Ce que ça veut dire : Spring ne trouve pas de page adaptée.
Comment résoudre :
- Vérifier URL
- Vérifier Controller
- Vérifier template

### Circular dependency
Ce que ça veut dire : Deux Services s’appellent en boucle.
Comment résoudre :
- Créer un troisième Service
- Retirer une dépendance
- Compiler

### detached entity passed to persist
Ce que ça veut dire : JPA reçoit un objet relationnel mal attaché.
Comment résoudre :
- Recharger avec findById
- Éviter les objets juste avec id
- Sauvegarder depuis Service

### No mapping for GET /...
Ce que ça veut dire : Aucune méthode Controller pour cette URL.
Comment résoudre :
- Ajouter @GetMapping
- Vérifier @RequestMapping
- Corriger th:href

### Access Denied
Ce que ça veut dire : Le rôle ne permet pas d’entrer.
Comment résoudre :
- Vérifier SecurityConfig
- Vérifier rôle du compte
- Se connecter avec bon utilisateur

### TemplateInputException
Ce que ça veut dire : Thymeleaf ne trouve pas ou ne comprend pas le template.
Comment résoudre :
- Vérifier chemin
- Vérifier syntaxe th:
- Vérifier Model

### Could not extract ResultSet
Ce que ça veut dire : La requête SQL échoue, souvent table ou colonne absente.
Comment résoudre :
- Vérifier ddl-auto
- Lire les logs SQL
- Recréer la base en développement

---

## PARTIE 8 — COMMENT LANCER LE PROJET (RAPPEL FINAL)

```bash
# 1. Démarrer PostgreSQL (selon ton système)
# 2. Créer la base si elle n'existe pas
createdb gestion_rh_db

# 3. Compiler et lancer
mvn spring-boot:run

# 4. Ouvrir dans le navigateur
http://localhost:8080/login

# 5. Se connecter
Login : admin
Mot de passe : admin123
```

Fin du guide : si tu comprends le chemin Navigateur → Controller → Service → Repository → PostgreSQL → Template, tu tiens la clé du projet.
