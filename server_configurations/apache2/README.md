## Configuration apache
Plusieurs configurations sont disponibles :

### Cas 1


Le backend et le frontend fonctionnent sur le même port avec la commande ``python3 dispatcher.py``
La configuration apache permet de proxyfier les url disponibles sur le port applicatif vers le port 80 du serveur :

 * localhost:5000/admin --> localhost/admin
 * localhost:5000/mreport --> localhost/admin
 * localhost:5000/api --> localhost/api

Utiliser la configuration apache **mreport_conf1.conf** et l'inclure dans la configuration du virtualhost apache2 eg:

Adapter tous  les chemins  pointant vers le dossier report de votre installation exemple :

``Include /home/mreport/server_configurations/apache2/mreport_conf1.conf``

Cette configuration inclue les configurations nécessaires dans conf/common et conf/flask.


### Cas 2

Le backend est lancé sur le port applicatif via gunicorn ou la commande ``export FLASK_APP=backend && flask run``
Le frontend est uniquement servi par apache

Utiliser la configuration apache **mreport_conf2.conf** et l'inclure dans la configuration du virtualhost apache2 eg:

Adapter tous  les chemins  pointant vers le dossier report de votre installation exemple :

``Include /home/mreport/server_configurations/apache2/mreport_conf2.conf``

Cette configuration inclue les configurations nécessaires dans conf/common et conf/noflask.