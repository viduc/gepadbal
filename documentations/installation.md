span

<div class="markdown-body">
    <table class="table" style="border: 0; width: 100%">
        <tr>
            <td style="width:20%; background-color: #fff6f8">
                <a href="https://www.univ-grenoble-alpes.fr/" class="simple-text">
                    <img src="https://www.univ-grenoble-alpes.fr/uas/SITEUI/UGA_LOGO_ACCUEIL/logo+bleu.svg" style="width:150px" alt="">
                </a>
            </td>
            <td style="width:60%; text-align:center">
                <H3>E-GEPADBAL ©UGA - pôle développement</H3>
                <p><A HREF="mailto:tristan.fleury@univ-grenoble-alpes.fr">tristan.fleury@univ-grenoble-alpes.fr</A></p>
                <p>Licence: <a href="../LICENSE">Apache 2.0</a></p>
            </td>
            <td style="width:20%; background-color: #fff6f8">
                <a href="https://www.esup-portail.org/" class="simple-text">
                    <img src="https://www.esup-portail.org/sites/default/files/logo-esupportail_1.png" style="width:150px" alt="">
                </a>
            </td>
        </tr>
    </table>
    <h1>E-GEPADBAL - Installation de l'application </h1>
    <div>
        <ul>
            <li class="nav-item">
                <a class="nav-link" href="#serveur-web-configuration">Configuration minimum</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#serveur-web-sources">Récupération des sources</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#serveur-web-dependances">Installation des dépendances</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#serveur-web-compilation">Compilation</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#serveur-web-droits">Modification des droits</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#nofile">Modification de la variable nofile</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#serveur-web-vhost">Configuration du virtual host</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#installation-auto">Installation automatisée</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#docker">Image Docker</a>
            </li>
        </ul>
    </div>

L'application E-GEPADBAL peut être installée de deux façons différentes, soit depuis une image docker, soit sirectement sur un serveur web.

<p id="serveur-web"></p>
<h2>Installation sur un serveur web:</h2>
<p id="serveur-web-configuration"></p>
<h3> Configuration du serveur web:</h3>

<ul>
<li> serveur linux 64 bits</li>
<li> apache + php 7.4</li>
<li> node js + npm (sudo apt install nodejs npm) + yarn (sudo npm install --global yarn)</li>
<li> git</li>
<li> composer</li>
<li> ext-soap (sudo apt install php-soap)</li>
<li> ext-zip (sudo apt install php-zip)</li>
<li> ext-curl (sudo apt install php-curl)</li>
<li> ext-dom (sudo apt install php-dom)</li>
<li> ext-xml (sudo apt install php-xml)</li>
<li> ext-ldap (sudo apt install php-ldap)</li>
<li> ext-mbstring (sudo apt install php-mbstring) (phpunit)</li>
</ul>

Dans une console, naviguez dans le dossier web de votre serveur (par exemple ./var/www) puis cloner le dépot:

```
git clone https://ledepot gepadbal
```

<p id="serveur-web-dependances"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h3> Installation des dépendances:</h3>
<p>Dans une console, entrez dans le dossier et lancer composer:</p>

```
    cd gepadbal
    composer install (ou php composer.phar install)
```

<div style="width: 70%; padding-left: 3em; padding-right: 3em;">
    <p>
        <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
        <div style="margin-left: 45px">Si vous rencontrez des difficultés lors de l'installation des dépendances avec composer liées à des limites php, vous pouvez utilisez la commande suivante:
 php -d memory_limit=-1 composer.phar install</div>
    </p>
</div>

<div style="width: 70%; padding-left: 3em; padding-right: 3em;">
    <p>
        <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
        <div style="margin-left: 45px">Lors de l'installation il vous sera demandé si vous souhaitez exécuter certaines recipes (symfony flex), accepter les recettes:
        <p></p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/recipe.png" alt="recipe" style="width:800px;"/></p></div>
    </p>
</div>

<p id="serveur-web-compilation"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h3>Compilation:</h3>

A la suite de l'installation des dépendances (via composer), un script (gepadbal.sh) sera exécuté automatiquement pour installer et compiler les autres dépendances javascript.

<div style="width: 70%; padding-left: 3em; padding-right: 3em;">
    <p>
        <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
        <div style="margin-left: 45px">Si ce script échoue (npm, node ou yarn non installé), vous pourrez le relancer directement ce script vai la console:</div>
    </p>
</div>

```
sh gepadbal.sh
```

<div style="width: 70%; padding-left: 3em; padding-right: 3em;">
    <p>
        <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
        <div style="margin-left: 45px">Si vous rencontrez des difficultés lors de la compilation suite à un problème de droits, lancez la commande en sudo:</div>
    </p>
</div>

```
sudo sh gepadbal.sh
```

<p id="serveur-web-droits"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h3>Modification des droits:</h3>

Vous devez ajouter l'utilisateur apache aux droits du dossier par exemple:

```
chown -R www-data:www-data gepadbal
chmod 555 -R gepadbal
```

entrez ensuite dans le dossier:

```
cd gepadbal
```

ajouter les droits d'écriture aux dossiers logs public et var:

```
chmod 775 -R ./logs ./public ./var ./config/gepadbal
```

<p id="nofile"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h3> Modification de la variable nofile</h3>
Il est nécessaire de modifier la variable nofile pour l'utilisateur apache. Ouvrez une console et entrez la commande suivante:

```
sudo echo "www-data  -   nofile  16384" > /etc/security/limits.conf
```

<p id="serveur-web-vhost"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h3> Configuration du virtual host</h3>

Votre virtual host devra pointer vers le répertoire public du dossier d'installation:

```
#<VirtualHost *:443>
<VirtualHost *:80>
ServerName gepadbal

ServerAdmin webmaster@localhost
DocumentRoot /var/www/gepadbal/public

<Directory /var/www/gepadbal/public/>
DirectoryIndex index.php
FallbackResource /index.php
Options FollowSymLinks
AllowOverride All
Require all granted
<ifModule mod_rewrite.c>
RewriteEngine On
</ifModule>
</Directory>

ErrorLog ${APACHE_LOG_DIR}/error-gepadbal.log
CustomLog ${APACHE_LOG_DIR}/access-gepadbal.log combined
</VirtualHost>
```

Une fois configuré votre dns, vous pourrez ouvrir votre navigateur et vous rendre sur l'url:

```
http(s)://monserveur/gepadbal
```

<p id="installation-auto"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h3> Installation automatisée</h3>
<p>Toutes les opérations précédentes peuvent être réalisées depuis un script bash d'installation.</p>
<p>Une fois les sources récupérées, ouvrez une console et entrez dans le dossier gepadbal:</p>

```
cd gepadbal
sudo sh installation.sh
```

<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_0.png" alt="script" style="width:400px;"/>

<div style="width: 70%; padding-left: 3em; padding-right: 3em;">
    <p>
        <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
        <div style="margin-left: 45px">Il est impératif de lancer cette commande avec un compte root</div>
    </p>
</div>

</br>
<p>Vous serez ensuite guidé dans le processus de configuration du serveur (dépendances) puis dans l'installation de l'application via composer</p>
<p>Le script vous demandera si vous souhaitez lancer la configuration, répondez oui</p>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_1.png" alt="script" style="width:800px;"/>
<p></p><p>L'installation se lancera automatiquent</p>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_2.png" alt="script" style="width:800px;"/>
<div style="width: 70%; padding-left: 3em; padding-right: 3em;">
    <p>
        <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
        <div style="margin-left: 45px">Si votre version de php n'est pas en 7.4, le script vous en informera et s'arrêtera</div>
    </p>
</div></br></br>
<p>Une fois votre système configuré, le script vous demandera si vous souhaitez lancer l'installation de E-Gepadbal, répondez oui</p>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_3.png" alt="script" style="width:800px;"/></br></br>
<p>Comme vous êtes connecté en tant que ROOT, composer vous le signalera et vous demandera si vous souhaitez continuer, appuyez sur entrer</p>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_4.png" alt="script" style="width:400px;"/></br></br>
<p>Ensuite symfony/flex vous demandera si vous souhaitez installer différentes recettes, dites y à chaque fois</p>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_5.png" alt="script" style="width:800px;"/></br></br>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_6.png" alt="script" style="width:800px;"/></br></br>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_7.png" alt="script" style="width:800px;"/></br></br>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/script_installation_8.png" alt="script" style="width:800px;"/></br></br>
<p>Les dépendances Php et Javascript seront installées. Le système se chargera également de compiler la partie VueJs/Node</p>
<p>Une fois le script terminé vous pouvez vous connecter à l'url que vous avez déterminé pour l'application et faire le paramètrage.</p>

<p id="docker"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h2>Image Docker</h2>

Vous devez avoir préalablement installé :

<h3> Installation sur poste client (dev, test)</h3>

* [Docker Desktop](https://www.docker.com/products/docker-desktop)
* [Docker Compose](https://docs.docker.com/compose/install/#install-compose) : *Déjà intégré à Docker Desktop sur Windows*

<h3> Installation serveur :</h3>

* [Docker Engine](https://docs.docker.com/engine/install/)
* [Docker Compose](https://docs.docker.com/compose/install/#install-compose) : *Déjà intégré à Docker Desktop sur Windows*

<h3> Démarrer le conteneur</h3>

<p>Se placer à la racine du projet et lancer</p>

```
docker-compose up
```

<p>Pour démarrer en mode daemon vous pouvez ajouter l'option `-d`</p>

```
docker-compose up -d
```

<h3> Arreter le conteneur</h3>

<p>Se placer à la racine du projet et lancer</p>

```
docker-compose down
```

</div>
