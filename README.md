# Datavisualization_Docker_Grafana
Utiliser un conteneur Grafana, grâce à Docker, pour faire de la Dataviz.

## 1.Contexte du projet

Afin de préparer une stack facilement déployable pour l'équipe de dev, les analystes data et le client, votre chef de projet vous demande de préparer des conteneurs pour des outils de Dataviz. Après discution avec la haute autorité de santé, votre client, les technologies retenues sont MySQL et GRAFANA. Le serveur est en Linux.

## 2. Préparation du container

### 2.1. Création du dossier 

Tout d'abord, il convient de créer un nouveau dossier de travail dans notre wsl2 (via la commande mdkir [nom_du_dossier]). 

On importe le fichier vaccination.sql dans notre dossier (soit avec la commande mv, soit en le passant dans le VSCode de notre wsl2), on se place dans le dossier (cd [nom_du_dossier])et on crée un fichier docker-compose.yaml (commande touch [nom_du_fichier]). On peut visualiser le tout avec la commande ls ou tree:

(base) natzer@DESKTOP-CF3Q9S7:~/Projet$ tree
.
├── database
├── docker-compose.yaml
└── vaccination.sql

### 2.2. Image 

Pour rappel, dans Docker, chaque conteneur est construit à partir d'une Image. Ici, nous aurons besoin de mysql ainsi que le logiciel de datavisualisation grafana. Pour se faire, on utilise la commande "docker pull". Ainsi, on a:

(base) natzer@DESKTOP-CF3Q9S7:~/Projet$ docker pull mysql
(base) natzer@DESKTOP-CF3Q9S7:~/Projet$ docker pull grafana/grafana

On a ainsi chargé nos images. 

### 2.3. Docker compose
Il va maintenant falloir remplir notre docker-compose.yaml pour définir nos containers ainsi que les relations que chacun entretien avec un autre. Pour plus de détails, se reporter au fichier compose.yaml intégré au repository. 

Une fois notre docker-compose finaliser, il n'y a plus qu'à le lancer avec la commande suivante:

(base) natzer@DESKTOP-CF3Q9S7:~/Projet$ docker-compose up -d

On peut observer grace au docker desktop si tout a bien été importé.  

![image](https://user-images.githubusercontent.com/95342035/161948932-e8369d90-3d3e-402e-8e79-d104b3857327.png)

Par la suite, il suffit de se connecter sur grafana via n'importe quel navigateur web, avec l'url suivant: localhost:3000/

## 3. Préparation du dashboard

La préparation du dashboard ne prend pas beaucoup de temps: 

1) On sélectionne "add data source", en choisissant MySQL
2) On effectue notre connexion 
3) Enfin, il ne reste plus qu'à faire les query.

*Exemple de query*

![image](https://user-images.githubusercontent.com/95342035/161949596-3d7caa19-b2fb-445d-8915-9c8830ec5d69.png)

![image](https://user-images.githubusercontent.com/95342035/161949621-afb0d479-05d7-4d78-9424-55157e0fbed0.png)

![image](https://user-images.githubusercontent.com/95342035/161962039-055da1cd-75f5-4a73-916d-e45f86e92079.png)



La magie d'internet. 
