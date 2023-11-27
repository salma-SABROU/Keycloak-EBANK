# Keycloak-EBANK
# TP Keycloak

## Partie 1: Configuration de Keycloak

#### 1. Télécharger Keycloak 19
Téléchargez Keycloak depuis le site officiel : Keycloak Téléchargement

#### 2. Démarrer Keycloak
Extrayez l'archive téléchargée et suivez les instructions de démarrage disponibles dans la documentation officielle de Keycloak.
![image](https://github.com/salma-SABROU/Keycloak_TP/assets/129564311/3f023c56-e8a1-4921-b57c-e6f99ae4080a)

#### 3. Créer un compte Admin
Accédez à l'interface d'administration de Keycloak (par défaut: http://localhost:8080/auth/admin). Créez un compte administrateur pour accéder à la console d'administration.
![image](https://github.com/salma-SABROU/Keycloak_TP/assets/129564311/2c33bff9-4019-4c44-a21f-125d50d7d969)


#### 4. Créer une Realm
Dans la console d'administration, créez une nouvelle "Realm" pour regrouper vos applications. Choisissez un nom significatif et appuyez sur "Create".
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/76764a7a-9636-48e3-ad69-9a1e0295aad1)

#### 5. Créer un client à sécuriser
Ajoutez un nouveau client dans votre Realm pour représenter votre application. Configurez les détails du client, y compris les URL de redirection et les paramètres appropriés.
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/549651b6-9624-4332-9418-fca64f80623c)


#### 6. Créer des utilisateurs
Ajoutez des utilisateurs à votre Realm à l'aide de la fonction "Users" dans la console d'administration. Attribuez-leur un nom d'utilisateur et un mot de passe.
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/fe31d5cd-ced5-4f34-a83d-54c5b103d6b9)

#### 7. Créer des rôles
Créez des rôles pour définir les autorisations des utilisateurs. Utilisez la fonction "Roles" dans la console d'administration pour définir des rôles significatifs.
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/4384699d-ac12-4055-971a-a58a134077cb)

#### 8. Affecter les rôles aux utilisateurs
Attribuez les rôles créés aux utilisateurs dans la section "Role Mappings" de chaque utilisateur.
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/a805c3c5-b1ac-4d55-a524-55a186a84935)
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/eea5b4c2-d4b4-43a4-91b5-c42247701b88)

#### 9. Tester avec Postman
Utilisez Postman pour effectuer les tests suivants :

 - Authentification avec le mot de passe.
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/7a36ffd0-9843-4bf9-b0ba-9d53e3b3a7b2)

 - Analyse des contenus des JWT Access Token et Refresh Token.
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/8fd52cb2-f667-491c-8461-96b4bb16c1df)


 - Authentification avec le Refresh Token.
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/117d56b6-abd0-4b46-9772-eab98e087586)


 - Authentification avec Client ID et Client Secret.
![image](https://github.com/salma-SABROU/Keycloak-EBANK/assets/129564311/2ee0c9ed-8bb9-424e-abf1-1018545d5575)

## Partie 2: Sécuriser les Applications
Dans cette partie, nous avons étendu l'utilisation de Keycloak pour sécuriser deux types d'applications : le frontend Products-App utilisant Thymeleaf et le microservice backend Supplier-service. Voici un résumé des étapes et des concepts clés :
![image](https://github.com/salma-SABROU/Keycloak_TP/assets/129564311/3c765b51-c4b2-452a-b130-a768e7d6457a)
![image](https://github.com/salma-SABROU/Keycloak_TP/assets/129564311/235ed0ed-de77-40aa-93d6-29506f274b6a)

### Pour Products-App (Frontend avec Thymeleaf) :
 
 1- Configuration du Client Keycloak :
  - Création d'un client Keycloak pour représenter Products-App.
  - Configuration des détails du client, y compris les URL de redirection et les paramètres nécessaires.

 2- Intégration de Keycloak dans l'Application :
  - Utilisation de la bibliothèque Keycloak Adapter for Spring Security dans l'application Spring Boot.
  - Configuration des propriétés dans le fichier application.properties pour spécifier le Realm, l'URL du serveur d'authentification, le client ID, etc.

 3- Sécurisation des Pages avec des Rôles :
  - Définition des rôles dans Keycloak reflétant les autorisations requises pour accéder aux pages de Products-App.
  - Utilisation d'annotations ou de configurations pour restreindre l'accès aux pages en fonction des rôles.


### Pour Supplier-service (Microservice Backend) :

 1- Configuration du Client Keycloak :
  - Création d'un nouveau client Keycloak pour représenter Supplier-service.
  - Configuration des détails du client, tels que les URL de redirection et les paramètres nécessaires.

 2- Intégration de Keycloak dans le Microservice :
  - Utilisation de la bibliothèque Keycloak Adapter pour Java dans le microservice.
  - Configuration du client dans le microservice pour communiquer avec le serveur Keycloak.

 3- Validation des Tokens JWT :
  - Configuration du microservice pour valider les tokens JWT émis par Keycloak, assurant que seules les demandes authentifiées avec un token valide sont autorisées.

 4 -Gestion de l'Authentification et de l'Autorisation :
  - Implémentation de la gestion de l'authentification et de l'autorisation dans le microservice en utilisant les informations extraites des tokens JWT.


