# MicroServices


# Prérequis:
* Windows 7
* Docker ToolBox installé

## Réalisé par: 
* **Ben Aissa Mohamed Khalil**
* **Derbali Chayma**
* **EL Waer Saifeddine**

## Étapes

**1. Géneration d'un fichier "Dockerfile" pour chaque Projet:**
	- **config-service**
	- **discovery-service**
	- **proxy-service**
	- **product-service**

Au niveau desquels on definit:  
	- L'image de base à partir de laquelle on va construire nos conteneurs. À l'aide de l'instruction "FROM".  
	- Le point de montage à créer. À l'aide de l'instruction "VOLUME".  
	- Le port réseau spécifié sur lequel le conteneur va rester en écoute. À l'aide de l'instruction "EXPOSE".  
	- Les fichiers, les répertoires ou les URLs des fichiers distante à ajouter au système de fichiers de l'image.. À l'aide de l'instruction "ADD".  
	- Les commandes Shell à excécuter pour executer nos conteneurs. À l'aide de l'instruction "CMD".  

**2. Géneration du "Docker Compose"; qui permet de définir et d'exécuter nos applications Docker multi-conteneurs:**

Au niveau desquels on definit:  
	- Nos services web en utilisant les images créées à partir ds Dockerfiles déja définis dans notre répertoire.   
	- Un réseau "mssample-network" de type **Bridge** pour nostre application. Chaque conteneur du service rejoint le réseau. I est accessible à la fois par d'autres conteneurs sur ce réseau.  
	- la dépendance des services au service "config-service" pour assusrer le démarrage des services dans l'ordre de dépendance et l'inclusion des dépendances au niveau des services.  

**3. Génenartion des fichiers de configuration "application.yml" pour notre service de configuration et "bootstrap.yml" pour les autres services:**

Au niveau du "application.yml", on définit:  
	- L'uri du repository de la configuration du serveur qui contient la ocnfiguration des autres services.  
```
	uri: https://github.com/khalilbenaissa10/myConfig
```

Au niveau du "bootstrap.yml", on définit:  
	- L'uri du service de configuration duquel notre service dépend.  
```
	uri: http://ms-sample-config-server:8888
```

**4. Lancement des conteneurs:**

au niveau de reperatoire on lance les commandes suivantes:  
```
docker-compose build
```
qui permet de construit nos conteneurs.  
```
docker-compose up
```
qui permet de lancer et connecter chaque conteneur au service en question.  

*Rq:*  
La commande **docker-compose up** permet aussi de faire un **build** avant de lancer les conteneurs.  
