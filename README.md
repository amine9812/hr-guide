# GUIDE.md — Référence rapide du projet RH Spring Boot

Guide synthétique généré à partir du projet réel dans `/home/shini/RH-nowjava`.

## SECTION 1 — TECHNOLOGIES UTILISÉES

- `Spring Boot` — Framework Java qui démarre l'application et relie les briques entre elles. Utilisé pour lancer le serveur web, scanner les composants et configurer automatiquement le projet. Où : [GestionRhApplication.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/GestionRhApplication.java:15), [pom.xml](/home/shini/RH-nowjava/pom.xml:16).
- `Spring MVC / Web` — Partie de Spring qui gère les URLs, formulaires et réponses HTTP. Utilisée pour tous les `Controller` et les pages web. Où : [pom.xml](/home/shini/RH-nowjava/pom.xml:39), [EmployeController.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/controller/EmployeController.java:28).
- `PostgreSQL` — Base de données relationnelle. Utilisée pour stocker utilisateurs, employés, congés, demandes, documents et notifications. Où : [application.properties](/home/shini/RH-nowjava/src/main/resources/application.properties:10), [pom.xml](/home/shini/RH-nowjava/pom.xml:68).
- `Spring Data JPA` — Couche qui permet de manipuler la base via des interfaces Java au lieu d'écrire du SQL partout. Utilisée dans tous les `Repository`. Où : [pom.xml](/home/shini/RH-nowjava/pom.xml:62), [UtilisateurRepository.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/repository/UtilisateurRepository.java:16).
- `Hibernate` — Moteur JPA concret qui transforme les objets Java en requêtes SQL. Utilisé pour créer ou mettre à jour les tables et exécuter les requêtes JPA. Où : [application.properties](/home/shini/RH-nowjava/src/main/resources/application.properties:22), [application.properties](/home/shini/RH-nowjava/src/main/resources/application.properties:31).
- `Thymeleaf` — Moteur de templates HTML côté serveur. Utilisé pour afficher les pages avec les données venant du `Model`. Où : [pom.xml](/home/shini/RH-nowjava/pom.xml:45), [layout/base.html](/home/shini/RH-nowjava/src/main/resources/templates/layout/base.html:8).
- `Spring Security` — Système d'authentification et de rôles. Utilisé pour protéger les URLs, gérer `/login` et afficher certains boutons selon le rôle. Où : [pom.xml](/home/shini/RH-nowjava/pom.xml:51), [SecurityConfig.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/config/SecurityConfig.java:20), [conges/liste.html](/home/shini/RH-nowjava/src/main/resources/templates/conges/liste.html:11).
- `Thymeleaf Extras Spring Security` — Extension qui ajoute `sec:authorize` dans les templates. Utilisée pour montrer ou cacher des liens selon le rôle connecté. Où : [pom.xml](/home/shini/RH-nowjava/pom.xml:56), [layout/base.html](/home/shini/RH-nowjava/src/main/resources/templates/layout/base.html:25).
- `Bootstrap 5` — Bibliothèque CSS/JS prête à l'emploi. Utilisée pour la mise en page, les formulaires, les tableaux et la navbar. Où : [auth/login.html](/home/shini/RH-nowjava/src/main/resources/templates/auth/login.html:12), [layout/base.html](/home/shini/RH-nowjava/src/main/resources/templates/layout/base.html:13).
- `Lombok` — Outil qui génère automatiquement getters et setters. Utilisé pour alléger les `Entity`. Où : [pom.xml](/home/shini/RH-nowjava/pom.xml:81), [Utilisateur.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/entity/Utilisateur.java:26), [Employe.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/entity/Employe.java:35).
- `Validation Jakarta` — Validation de formulaires côté serveur. Utilisée avec `@Valid` et les erreurs `BindingResult`. Où : [pom.xml](/home/shini/RH-nowjava/pom.xml:75), [EmployeController.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/controller/EmployeController.java:88).
- `BCrypt` — Algorithme de hachage de mot de passe. Utilisé pour ne jamais stocker un mot de passe en clair. Où : [SecurityConfig.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/config/SecurityConfig.java:25), [UtilisateurService.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/service/UtilisateurService.java:63).
- `Maven` — Outil de build et de dépendances. Utilisé pour télécharger les bibliothèques et lancer le projet avec `mvn spring-boot:run`. Où : [pom.xml](/home/shini/RH-nowjava/pom.xml:1), [pom.xml](/home/shini/RH-nowjava/pom.xml:90).

## SECTION 2 — LES FICHIERS QUE TU CODES TOI-MÊME

### 1. Entities

- 📄 `DemandeAdministrative.java` — `src/main/java/com/gestionrh/entity/DemandeAdministrative.java` — Rôle : stocker une demande administrative. Fonctions : pas de méthode métier; décrit `employe`, `typeDemande`, `description`, `statut`, `dateSoumission`.
- 📄 `DemandeConge.java` — `src/main/java/com/gestionrh/entity/DemandeConge.java` — Rôle : stocker une demande de congé. Fonctions : pas de méthode métier; décrit `employe`, `typeConge`, dates, `motif`, `statut`, `traiteePar`.
- 📄 `Departement.java` — `src/main/java/com/gestionrh/entity/Departement.java` — Rôle : stocker un département. Fonctions : pas de méthode métier; décrit `libelle` et `description`.
- 📄 `Document.java` — `src/main/java/com/gestionrh/entity/Document.java` — Rôle : stocker les métadonnées d'un fichier uploadé. Fonctions : pas de méthode métier; décrit `nomFichier`, `chemin`, `categorie`, `employe`, `demandeAdministrative`.
- 📄 `Employe.java` — `src/main/java/com/gestionrh/entity/Employe.java` — Rôle : stocker une fiche employé. Fonctions : pas de méthode métier; décrit identité, email, date d'embauche, relations d'organisation, compte et statut.
- 📄 `HistoriqueAction.java` — `src/main/java/com/gestionrh/entity/HistoriqueAction.java` — Rôle : tracer les actions importantes. Fonctions : pas de méthode métier; décrit `utilisateur`, `action`, `dateAction`.
- 📄 `Notification.java` — `src/main/java/com/gestionrh/entity/Notification.java` — Rôle : stocker un message interne. Fonctions : pas de méthode métier; décrit `destinataire`, `message`, `dateEnvoi`, `lue`.
- 📄 `Poste.java` — `src/main/java/com/gestionrh/entity/Poste.java` — Rôle : stocker un poste. Fonctions : pas de méthode métier; décrit `libelle` et `description`.
- 📄 `RoleUtilisateur.java` — `src/main/java/com/gestionrh/entity/RoleUtilisateur.java` — Rôle : lister les rôles possibles. Fonctions : enum métier pour `ADMIN`, `RH`, `RESPONSABLE`, `EMPLOYE`.
- 📄 `Service.java` — `src/main/java/com/gestionrh/entity/Service.java` — Rôle : stocker un service interne. Fonctions : pas de méthode métier; décrit `libelle` et `description`.
- 📄 `StatutConge.java` — `src/main/java/com/gestionrh/entity/StatutConge.java` — Rôle : lister les statuts d'une demande de congé. Fonctions : enum de workflow.
- 📄 `StatutDemandeAdministrative.java` — `src/main/java/com/gestionrh/entity/StatutDemandeAdministrative.java` — Rôle : lister les statuts d'une demande administrative. Fonctions : enum de workflow.
- 📄 `StatutEmploye.java` — `src/main/java/com/gestionrh/entity/StatutEmploye.java` — Rôle : lister les statuts d'un employé. Fonctions : enum de dossier employé.
- 📄 `TypeConge.java` — `src/main/java/com/gestionrh/entity/TypeConge.java` — Rôle : lister les types de congés. Fonctions : enum utilisé par les formulaires et la base.
- 📄 `TypeDemandeAdministrative.java` — `src/main/java/com/gestionrh/entity/TypeDemandeAdministrative.java` — Rôle : lister les types de demandes administratives. Fonctions : enum utilisé par les formulaires et la base.
- 📄 `Utilisateur.java` — `src/main/java/com/gestionrh/entity/Utilisateur.java` — Rôle : stocker un compte de connexion. Fonctions : pas de méthode métier; décrit `login`, `motDePasse`, `role`, `actif`.

### 2. Repositories

- 📄 `DemandeAdministrativeRepository.java` — `src/main/java/com/gestionrh/repository/DemandeAdministrativeRepository.java` — Rôle : accès base pour les demandes administratives. Fonctions : `findByEmployeOrderByDateSoumissionDesc()` liste celles d'un employé; `findByStatutOrderByDateSoumissionDesc()` filtre par statut; `countByStatut()` compte les demandes d'un statut.
- 📄 `DemandeCongeRepository.java` — `src/main/java/com/gestionrh/repository/DemandeCongeRepository.java` — Rôle : accès base pour les congés. Fonctions : `findByEmployeOrderByDateSoumissionDesc()` liste celles d'un employé; `findByStatutOrderByDateSoumissionDesc()` filtre par statut; `countByStatut()` compte les congés d'un statut.
- 📄 `DepartementRepository.java` — `src/main/java/com/gestionrh/repository/DepartementRepository.java` — Rôle : CRUD des départements. Fonctions : héritées de `JpaRepository`.
- 📄 `DocumentRepository.java` — `src/main/java/com/gestionrh/repository/DocumentRepository.java` — Rôle : accès base pour les documents. Fonctions : `findByEmployeOrderByDateAjoutDesc()` liste les documents d'un employé; `findByDemandeAdministrativeOrderByDateAjoutDesc()` liste ceux d'une demande.
- 📄 `EmployeRepository.java` — `src/main/java/com/gestionrh/repository/EmployeRepository.java` — Rôle : accès base pour les employés. Fonctions : `findByNomContainingIgnoreCaseOrPrenomContainingIgnoreCaseOrDepartementLibelleContainingIgnoreCase()` fait la recherche; `findByUtilisateur()` retrouve la fiche liée à un compte; `countByStatut()` compte les actifs.
- 📄 `HistoriqueActionRepository.java` — `src/main/java/com/gestionrh/repository/HistoriqueActionRepository.java` — Rôle : enregistrer les traces d'audit. Fonctions : héritées de `JpaRepository`.
- 📄 `NotificationRepository.java` — `src/main/java/com/gestionrh/repository/NotificationRepository.java` — Rôle : accès base pour les notifications. Fonctions : `findByDestinataireOrderByDateEnvoiDesc()` liste celles d'un utilisateur; `countByDestinataireAndLueFalse()` compte les non lues.
- 📄 `PosteRepository.java` — `src/main/java/com/gestionrh/repository/PosteRepository.java` — Rôle : CRUD des postes. Fonctions : héritées de `JpaRepository`.
- 📄 `ServiceRepository.java` — `src/main/java/com/gestionrh/repository/ServiceRepository.java` — Rôle : CRUD des services internes. Fonctions : héritées de `JpaRepository`.
- 📄 `UtilisateurRepository.java` — `src/main/java/com/gestionrh/repository/UtilisateurRepository.java` — Rôle : accès base pour les comptes. Fonctions : `findByLogin()` charge un compte par login; `findByRole()` filtre par rôle; `existsByLogin()` évite les doublons.

### 3. Services

- 📄 `CongeService.java` — `src/main/java/com/gestionrh/service/CongeService.java` — Rôle : logique métier des congés. Fonctions : `findAll()` liste tout; `findForEmploye()` filtre par employé; `findById()` charge une demande; `soumettre()` crée une demande en `EN_ATTENTE`; `traiter()` valide/refuse et crée historique + notification; `countEnAttente()` alimente le dashboard.
- 📄 `DashboardService.java` — `src/main/java/com/gestionrh/service/DashboardService.java` — Rôle : fabriquer les compteurs du tableau de bord. Fonctions : `buildCounters()` assemble employés actifs, congés en attente, demandes en attente et notifications non lues.
- 📄 `DemandeAdministrativeService.java` — `src/main/java/com/gestionrh/service/DemandeAdministrativeService.java` — Rôle : logique métier des demandes administratives. Fonctions : `findAll()`, `findForEmploye()`, `findById()`, `soumettre()`, `changerStatut()`, `countEnAttente()`.
- 📄 `DocumentService.java` — `src/main/java/com/gestionrh/service/DocumentService.java` — Rôle : gérer l'upload et le téléchargement de fichiers. Fonctions : `findAll()` liste; `findById()` charge; `upload()` écrit dans `uploads/` puis sauvegarde les métadonnées; `loadResource()` prépare le téléchargement.
- 📄 `EmployeService.java` — `src/main/java/com/gestionrh/service/EmployeService.java` — Rôle : logique métier des fiches employés. Fonctions : `findAll()`, `search()`, `findById()`, `findByUtilisateur()`, `saveWithRelations()` rattache département/service/poste/compte avant sauvegarde, `archiver()`, `countActifs()`.
- 📄 `HistoriqueService.java` — `src/main/java/com/gestionrh/service/HistoriqueService.java` — Rôle : centraliser l'écriture d'audit. Fonctions : `tracer()` enregistre une action et sa date.
- 📄 `NotificationService.java` — `src/main/java/com/gestionrh/service/NotificationService.java` — Rôle : créer et lire les notifications. Fonctions : `creerNotification()`, `findForUser()`, `countUnread()`, `markAllRead()`.
- 📄 `OrganisationService.java` — `src/main/java/com/gestionrh/service/OrganisationService.java` — Rôle : CRUD des départements, services et postes. Fonctions : `findAllDepartements()/saveDepartement()/findDepartement()/deleteDepartement()`, `findAllServices()/saveService()/findService()/deleteService()`, `findAllPostes()/savePoste()/findPoste()/deletePoste()`.
- 📄 `UtilisateurService.java` — `src/main/java/com/gestionrh/service/UtilisateurService.java` — Rôle : logique métier des comptes et pont avec Spring Security. Fonctions : `loadUserByUsername()` charge un compte pour le login; `findAll()`; `findByLogin()`; `saveWithEncodedPassword()` encode le mot de passe; `save()`; `existsByLogin()`.

### 4. Controllers

- 📄 `AdminController.java` — `src/main/java/com/gestionrh/controller/AdminController.java` — Rôle : gérer les comptes côté admin. Fonctions : `utilisateurs()` affiche la liste; `nouveau()` ouvre le formulaire; `creer()` valide et crée un compte.
- 📄 `AuthController.java` — `src/main/java/com/gestionrh/controller/AuthController.java` — Rôle : afficher la page de connexion. Fonctions : `login()` retourne `auth/login`.
- 📄 `CongeController.java` — `src/main/java/com/gestionrh/controller/CongeController.java` — Rôle : pages web des congés. Fonctions : `liste()` affiche les demandes; `nouveau()` ouvre le formulaire; `soumettre()` crée une demande; `traiter()` change le statut.
- 📄 `DashboardController.java` — `src/main/java/com/gestionrh/controller/DashboardController.java` — Rôle : page d'accueil après connexion. Fonctions : `home()` redirige `/` vers `/dashboard`; `dashboard()` remplit le `Model` avec l'utilisateur et les compteurs.
- 📄 `DemandeAdministrativeController.java` — `src/main/java/com/gestionrh/controller/DemandeAdministrativeController.java` — Rôle : pages web des demandes administratives. Fonctions : `liste()`, `nouveau()`, `soumettre()`, `changerStatut()`.
- 📄 `DocumentController.java` — `src/main/java/com/gestionrh/controller/DocumentController.java` — Rôle : pages et actions des documents. Fonctions : `liste()` affiche la page; `upload()` reçoit le fichier; `telecharger()` renvoie le document en HTTP.
- 📄 `EmployeController.java` — `src/main/java/com/gestionrh/controller/EmployeController.java` — Rôle : pages des employés. Fonctions : `liste()` recherche/affiche; `nouveau()` ouvre le formulaire; `detail()` montre une fiche; `modifier()` recharge la fiche; `sauvegarder()` crée ou modifie; `archiver()` passe le statut en archivé.
- 📄 `NotificationController.java` — `src/main/java/com/gestionrh/controller/NotificationController.java` — Rôle : pages des notifications. Fonctions : `liste()` affiche celles du connecté; `lire()` marque tout comme lu.
- 📄 `OrganisationController.java` — `src/main/java/com/gestionrh/controller/OrganisationController.java` — Rôle : pages CRUD d'organisation. Fonctions : `index()` affiche les 3 listes; `nouveau*/modifier*()/sauvegarder*()/supprimer*()` gèrent départements, services et postes.

### 5. Config

- 📄 `GestionRhApplication.java` — `src/main/java/com/gestionrh/GestionRhApplication.java` — Rôle : point d'entrée de l'application. Fonctions : `main()` démarre Spring Boot.
- 📄 `SecurityConfig.java` — `src/main/java/com/gestionrh/config/SecurityConfig.java` — Rôle : sécurité du site. Fonctions : `passwordEncoder()` fournit BCrypt; `securityFilterChain()` protège les URLs, configure login et logout; `authenticationSuccessHandler()` redirige après connexion.

### 6. Templates HTML (Thymeleaf)

- 📄 `admin/utilisateur-form.html` — `src/main/resources/templates/admin/utilisateur-form.html` — Rôle : formulaire de création de compte. Blocs clés : `th:object="${utilisateur}"`, `th:field` pour login/mot de passe/rôle/actif.
- 📄 `admin/utilisateurs.html` — `src/main/resources/templates/admin/utilisateurs.html` — Rôle : liste des comptes. Blocs clés : bouton de création et tableau `th:each="u : ${utilisateurs}"`.
- 📄 `auth/login.html` — `src/main/resources/templates/auth/login.html` — Rôle : page de connexion. Blocs clés : alertes `param.error` et `param.logout`, formulaire POST vers `/login`.
- 📄 `conges/form.html` — `src/main/resources/templates/conges/form.html` — Rôle : formulaire de demande de congé. Blocs clés : `th:object="${demandeConge}"`, choix du `TypeConge`, dates, motif.
- 📄 `conges/liste.html` — `src/main/resources/templates/conges/liste.html` — Rôle : liste des congés. Blocs clés : tableau des demandes, boutons Valider/Refuser visibles avec `sec:authorize`.
- 📄 `dashboard/index.html` — `src/main/resources/templates/dashboard/index.html` — Rôle : tableau de bord. Blocs clés : affichage du login/role et des compteurs.
- 📄 `demandes/form.html` — `src/main/resources/templates/demandes/form.html` — Rôle : formulaire de demande administrative. Blocs clés : choix du type et zone description.
- 📄 `demandes/liste.html` — `src/main/resources/templates/demandes/liste.html` — Rôle : liste des demandes administratives. Blocs clés : tableau des demandes et formulaire de changement de statut pour `ADMIN`/`RH`.
- 📄 `documents/liste.html` — `src/main/resources/templates/documents/liste.html` — Rôle : upload et liste des documents. Blocs clés : formulaire multipart, liste des employés, lien de téléchargement.
- 📄 `employes/detail.html` — `src/main/resources/templates/employes/detail.html` — Rôle : fiche détail d'un employé. Blocs clés : affichage des infos et bouton Archiver.
- 📄 `employes/form.html` — `src/main/resources/templates/employes/form.html` — Rôle : formulaire employé. Blocs clés : champs identité + listes déroulantes pour département/service/poste/compte.
- 📄 `employes/liste.html` — `src/main/resources/templates/employes/liste.html` — Rôle : liste et recherche d'employés. Blocs clés : formulaire GET de recherche et liens Voir/Modifier.
- 📄 `layout/base.html` — `src/main/resources/templates/layout/base.html` — Rôle : squelette commun des pages. Blocs clés : navbar, `sec:authorize`, fragment `page(content)`, bouton logout.
- 📄 `notifications/liste.html` — `src/main/resources/templates/notifications/liste.html` — Rôle : liste des notifications. Blocs clés : bouton "Tout marquer comme lu", surbrillance des non lues.
- 📄 `organisation/departement-form.html` — `src/main/resources/templates/organisation/departement-form.html` — Rôle : formulaire département. Blocs clés : `id` caché, `libelle`, `description`.
- 📄 `organisation/index.html` — `src/main/resources/templates/organisation/index.html` — Rôle : page centrale de l'organisation. Blocs clés : 3 tableaux pour départements, services et postes.
- 📄 `organisation/poste-form.html` — `src/main/resources/templates/organisation/poste-form.html` — Rôle : formulaire poste. Blocs clés : `id` caché, `libelle`, `description`.
- 📄 `organisation/service-form.html` — `src/main/resources/templates/organisation/service-form.html` — Rôle : formulaire service. Blocs clés : `th:object="${serviceRh}"`, `id`, `libelle`, `description`.

### 7. DataInitializer

- 📄 `DataInitializer.java` — `src/main/java/com/gestionrh/config/DataInitializer.java` — Rôle : créer les données de départ au lancement. Fonctions : `run()` crée le compte `admin/admin123`, des départements, un service et un poste si la base est vide.

## SECTION 3 — LES FICHIERS QUE TU NE CODES PAS

- ⚙️ `pom.xml` — Rôle : définir les dépendances et le build Maven. À faire : modifier surtout les dépendances ou versions si besoin.
- ⚙️ `src/main/resources/application.properties` — Rôle : configurer PostgreSQL, JPA, Thymeleaf, upload et port. À faire : adapter surtout URL, username, password et éventuellement le port.
- ⚙️ `GestionRhApplication.java` — Rôle : démarrer l'application Spring Boot. À faire : presque ne pas toucher.
- ⚙️ `.gitignore` — Rôle : dire à Git quels fichiers ignorer. À faire : ajuster seulement si tu veux ignorer d'autres fichiers locaux.
- ⚙️ `target/` — Rôle : contenir les fichiers compilés générés par Maven. À faire : ne pas modifier à la main.
- ⚙️ `uploads/` — Rôle : contenir les fichiers téléversés par les utilisateurs. À faire : laisser l'application l'alimenter.
- ⚙️ `mvnw` / `mvnw.cmd` — Rôle : wrapper Maven. À faire : non présents dans ce dépôt; si tu recrées le projet, tu peux les générer depuis Spring Initializr.

## SECTION 4 — COMMENT TOUT S'ENCHAÎNE

Exemple réel : un employé soumet une demande de congé.

1. Le navigateur envoie le formulaire de [conges/form.html](/home/shini/RH-nowjava/src/main/resources/templates/conges/form.html:9) vers l'URL `/conges`.
2. [CongeController.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/controller/CongeController.java:76) reçoit le POST dans `soumettre(...)`.
3. Le controller récupère l'utilisateur connecté avec [UtilisateurService.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/service/UtilisateurService.java:58), puis retrouve sa fiche employé avec [EmployeService.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/service/EmployeService.java:68).
4. Il appelle [CongeService.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/service/CongeService.java:53) dans `soumettre(...)`.
5. Le service met le statut à `EN_ATTENTE`, pose la date de soumission, puis appelle [DemandeCongeRepository.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/repository/DemandeCongeRepository.java:15).
6. JPA/Hibernate traduit cela en `INSERT` dans PostgreSQL grâce à la config de [application.properties](/home/shini/RH-nowjava/src/main/resources/application.properties:22).
7. Après redirection, [CongeController.java](/home/shini/RH-nowjava/src/main/java/com/gestionrh/controller/CongeController.java:56) recharge la liste.
8. La réponse repart vers [conges/liste.html](/home/shini/RH-nowjava/src/main/resources/templates/conges/liste.html:6), puis revient au navigateur en HTML.

✅ GUIDE.md généré
