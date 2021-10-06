<link rel="stylesheet" type="text/css" media="all" href="../assets/styles/material/material-dashboard.css" />

<div class="card">
    <div class="card-header card-header-info">
        <div class="d-flex justify-content-between">
            <h5 class="card-title text-break">GEPADBAL</h5>
            <span class="m-0 ml-2 text-danger">
		 Installation de l'application
            </span>
        </div>
    </div>
    <div class="card-body">
	<table class="table" style="border: 0px">
		<tr>
			<td style width="160px">
				<a href="https://www.univ-grenoble-alpes.fr/" class="simple-text">
					<img src="http://www.sciencespo-grenoble.fr/wp-content/uploads/2019/11/logo-uga.jpeg" style="width:150px">
				</a>
			</td>
			<td style width="500px">
				<p class="">GEPADBAL ©UGA - pôle développement</p>
				<p><A HREF="mailto:tristan.fleury@univ-grenoble-alpes.fr">tristan.fleury@univ-grenoble-alpes.fr</A></p>
				<p>Licence: <a href="../LICENSE">Apache 2.0</a></p>
			</td>
			<td>
				<ul class="nav flex-column">
					<li class="nav-item">
						<a class="nav-link active" href="#serveur-web">Installation serveur web</a>
						<ul class="nav flex-column pl-5">
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
								<a class="nav-link" href="#serveur-web-vhost">Configuration du virtual host</a>
							</li>
						</ul>
			  		</li>
				  	<li class="nav-item">
				   		<a class="nav-link active" href="#serveur-web">Installation Docker</a>
						<ul class="nav flex-column pl-5">
							<li class="nav-item">
								<a class="nav-link" href="javascript:;">Link</a>
							</li>
						</ul>
				  	</li>
				</ul>
			</td>
		</tr>
	</table>
    </div>
</div>

L'application GEPADBAL peut être installée de deux façons différentes, soit depuis une image docker, soit sirectement sur un serveur web.
<p id="serveur-web"></p>
<div class="alert alert-primary">
  <h2>Installation sur un serveur web:</h2>
</div>

<p id="serveur-web-configuration"></p>
### Configuration du serveur web:

* serveur linux 64 bits
* apache + php 7
* node js + npm (sudo apt install nodejs npm) + yarn (sudo npm install --global yarn)
* git
* composer
* ext-soap (sudo apt install php-soap)
* ext-zip (sudo apt install php-zip)
* ext-curl (sudo apt install php-curl)
* ext-dom (sudo apt install php-dom)
* ext-xml (sudo apt install php-xml)
* ext-ldap (sudo apt install php-ldap)
* ext-mbstring (sudo apt install php-mbstring) (phpunit)

<p id="serveur-web-sources"><a href="#top"><img src="./images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Récuparation des sources:

Dans une console, naviguez dans le dossier web de votre serveur (par exemple ./var/www) puis cloner le dépot:

	git clone https://ledepot gepadbal
<p id="serveur-web-dependances"><a href="#top"><img src="./images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Installation des dépendances:

Dans une console, entrez dans le dossier et lancer composer:

	cd gepadbal 
	
	composer install

><img src="./images/warning.png" alt="warning" style="width:40px;"/> Si vous rencontrez des difficultés lors de l'installation des dépendances avec composer liées à des limites php, vous pouvez utilisez un fichier [composer.phar](https://getcomposer.org/download/latest-stable/composer.phar) puis dans une commande:
>
>	php -d memory_limit=-1 composer.phar install

Lors de l'installation il vous sera demandé si vous souhaité exécuter un recipe (symfony), accepter la recette:

<img src="./images/recipe.png" alt="recipe" style="width:800px;"/>

<p id="serveur-web-compilation"><a href="#top"><img src="./images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Compilation:

A la suite de l'installation des dépendances (via composer), un script sera exécuté automatiquement pour installer  et compiler les autres dépendances javascript.

><img src="./images/warning.png" alt="warning" style="width:40px;"/> Si ce script échoue (npm, node ou yarn non installé), vous pourrez le relancer directement ce script vai la console:
>
	sh gepadbal.sh

><img src="./images/warning.png" alt="warning" style="width:40px;"/> Si vous rencontrez des difficultés lors de la compilation suite à un problème de droits, lancez la commande en sudo:
>
	sudo sh gepadbal.sh
	
<p id="serveur-web-droits"><a href="#top"><img src="./images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Modification des droits:

Vous devez ajouter l'utilisateur apache aux droits du dossier par exemple:

	chown -R www-data:www-data gepadbal
	chmod 555 -R gepadbal

entrez ensuite dans le dossier:

	cd gepadbal

ajouter les droits d'écriture aux dossiers logs public et var:

	chmod 775 -R ./logs ./public ./var ./config/gepadbal
<p id="serveur-web-vhost"><a href="#top"><img src="./images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Configuration du virtual host:

Votre virtual host devra pointer vers le répertoire public du dossier d'installation:

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
	
	        Header set Access-Control-Allow-Origin "*"
	
	#       SSLEngine on
	#       SSLCertificateFile /etc/apache2/server.crt
	#       SSLCertificateKeyFile /etc/apache2/server.key
	</VirtualHost>
	
Une fois configuré votre dns, vous pourrez ouvrir votre navigateur et vous rendre sur l'url:

	http(s)://monserveur/gepadbal
	
<a href="#top"><img src="./images/up.png" alt="up" style="width:40px;"/> HAUT</a> 

<a href="./configuration.md"><img src="./images/next.png" alt="next" style="width:40px;"/>  Configuration</a>
