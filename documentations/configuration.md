[pathDocumentation]: https://raw.githubusercontent.com/viduc/gepadbal/main/
<link rel="stylesheet" type="text/css" media="all" href="../assets/styles/material/material-dashboard.css" />

<div class="card">
    <div class="card-header card-header-info">
        <div class="d-flex justify-content-between">
            <h5 class="card-title text-break">GEPADBAL</h5>
            <span class="m-0 ml-2 text-danger">
		 Configuration de l'application
            </span>
        </div>
    </div>
    <div class="card-body">
	<table class="table" style="border: 0px">
		<tr>
			<td style width="160px">
				<a href="https://www.univ-grenoble-alpes.fr/" class="simple-text">
					<img src="https://www.univ-grenoble-alpes.fr/uas/SITEUI/UGA_LOGO_ACCUEIL/logo+bleu.svg" style="width:150px">
				</a>
			</td>
			<td style width="500px">
				<p class="">GEPADBAL ©UGA - pôle développement</p>
				<p><A HREF="mailto:tristan.fleury@univ-grenoble-alpes.fr">tristan.fleury@univ-grenoble-alpes.fr</A></p>
				<p>Licence: <a href="../LICENSE">Apache 2.0</a></p>
			</td>
			<td>
				<ul class="nav flex-column pl-5">
					<li class="nav-item">
						<a class="nav-link" href="#interface">Interface web</a>
					</li>
					<li class="nav-item">
						<a class="nav-link" href="#generale">Configuration générale</a>
					</li>
					<li class="nav-item">
						<a class="nav-link" href="#zimbra">Configuration Zimbra</a>
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
			</td>
		</tr>
	</table>
    </div>
</div>

La configuration de l'application se fait depuis une interface web dediée.

<p id="interface"></p>
### Accès à l'interface web:

Pour accéder à l'interface web de configuration, entrez dans un navigateur l'url que vous avez définit pour gepadbal

ex: http(s)://gepadbal.mondomain.fr

<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_01.png" alt="01"/>

>> <img src="./images/warning.png" alt="warning" style="width:40px;"/> L'url vers laquelle vous êtes redirigé ne sera accessible qu'après avoir installé l'application et jusqu'à ce que l'installation soit terminée. Une fois l'installation effectuée, cette url ne sera plus accesible (authenfication par CAS). Les administrateurs authentifiés auront ensuite accès à une interface de configuration en cas de besoin de modification.
>>

>> <img src="./images/warning.png" alt="warning" style="width:40px;"/> Sur la droite de cette interface se trouve les sous éléments des grandes étapes à effectuer. Vous pouvez naviger dans ces sous étapes avec les fléches allant à gauche ou à droite. Vous devez également enregistrer avant de changer de sous étapes si vous avez modifier une valeur:
>> <img src="./images/interface_02.png" alt="02"/>
>>

<p id="generale"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Configuration générale:

La première étape consiste à configuration les informations générales:

- Authentification cas
  L'authentification se fait exclusivement depuis un serveurv<a href="https://www.single-sign-on.info/cas-sso-de-quoi-sagit-il/">CAS (sso)</a>. Vous devez donc renseigner votre serveur d'authentification dans cette partie:
  <img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_03.png" alt="03"/>
  Entrez l'url de votre serveur cas ainsi que l'url de déconnexion

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- LDAP
Vous devez disposer d'un serveur ldap pour la gestion des accès utilisateurs.
Dans le premier champ renseignez le nom (ou ip⁾) de votre serveur LDAP. Préciser également le port. Définissez le protocol à utiliser avec le bouton switch entre LDAP et LDAPS.
Renseignez ensuite de DN général du serveur (par ex: OU=monOu,dc=mondc,dc=org).
Ensuite dans le champ ou people, renseignez l'OU qui contient vos utilisateurs (ex: ou=people). De même pour l'ou groupe, renseignez l'OU qui contient vos groupes.
Pour l'authentification, reseignez le compte ayant droit d'accéder et son mot de passe (ex (cn=monlogin,ou=ouadmin).
Enfin vous devez renseigner trois attributs particulier à savoir le nom de *objectClassGroup*, le nom de l'*uid* et le nom du *memberof*
Vous disposez d'un bouton pour tester votre connexion avec les informations reseignées (vous devez enregistrer avant de tester).
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_04.png" alt="04"/>
Vous devez ensuite renseigner les groupes administrateurs et assistance:
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_04_1.png" alt="04_1"/>
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/> Les membres du groupe admin auront tout les droits dans l'application (Partage + configuration).
Les membres assistances pourront partager les bals sans restrictions. Ils ont accès à toutes les fonctionnalités sauf la configuration.

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- API
Le chargement de la liste des boîtes institutionnelles peut se faire de deux façons différentes. Vous pouvez créer une api depuis votre référentiel ou charger un fichier csv.
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_05.png" alt="05"/>

>> <i>Chargement depuis une api</i>
>> Votre api devra retourner une collection d'objet selon ce format:
>> a définir
>> L'url qui sera appelée devra être au format suivant:
>> https://login:motdepasse@serveurdomain.fr/requete
>>

>> <i>Chargement depuis un fichier</i>
>> <img src="./images/interface_06.png" alt="06"/>
>> Vous devrez créer un fichier csv selon le modèle suivant téléchargeable depuis l'interface (fichier enregistré).
>> Il vous faudra recharger ce fichier (dans la page de configuration plus tard) à chaque fois que vous aurez des mises à jours de boîtes institutionnelles à effectuer.
>> <img src="./images/warning.png" alt="warning" style="width:40px;"/> Le lien "fichier des erreurs" permet de récupérer les bals qui n'ont pas pu être chargées depuis votre fichier.
>> Si une erreur est trouvée dans une ligne, elle ne sera pas chargée et sera enregistrée dans ce fichier.
>>

>> <i>Sous structure</i>
>> Le chargement de la liste des sous structures (d'une structure) se fait selon le même principe.
>> Le format de l'api devra être:
>> https://login:motdepasse@serveurdomain.fr/requete.
>> Vous devrez également rajouter [idstructure] dans l'url que vous renseignez. Cette partie sera ensuite remplacée par l'id du la structure lors de l'appel à votre api.
>> Vous pouvez donc construire l'url de votre api selon vos besoins et renseignant au bon endroit ce pattern.
>> Le modèle de fichier est à récupérer comme pour le fichier des bals
>>

>> <img src="./images/warning.png" alt="warning" style="width:40px;"/> Le chargement des bals et des sous structures est indépendant.
>> Vous pouvez utiliser l'api dans un des cas et le chargement par fichier pour l'autre cas.
>>

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- Logs
Déterminer le nombre de logs d'actions qui seront sauvegardés par bal. Chaque action réalisée sur une bal est enregistrée dans un fichier.
Lorsque le nombre d'actions maximum est enregistrés dans le fichier, la plus ancienne des actions est supprimer de ce fichier.
Par défaut il est conseillé de mettre ce champ à 10.
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_07.png" alt="07"/>

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- SMTP
Il est necessaire de configurer un serveur smtp pour l'envoi des mails
Enregistrer l'url du serveur smtp dans el premier champ. ex: smtp://login:motdepasse@smtps.dmoain.fr:587
Renseigner l'adresse qui sera ajouter au from lors de l'envoie.
Vous pouvez tester l'envoie de mail depuis cette interface en entrant une adresse valide dans le dernier champ et en cliquant sur "Envoyer un courriel" (il faut avoir sauvegarder la configuration)
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_08.png" alt="08"/>

<p id="zimbra"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Configuration zimbra:
Dans cette partié nous allons configurer toutes les informations relatives à zimbra.

- WSDL
  L'application GEPADBAL utilise le mode <a href="https://www.w3.org/TR/wsdl.html">wdsl</a> pour communiquer avec le serveur zimbra.
  Vous devrez donc avoir activer cette fonctionnalité sur votre instance et fournir l'url de connexion.
  <img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_09.png" alt="09"/>
  Vous devez également fournir le login et mot de passe de connexion d'un compte ayant des droits de lecture et écriture pour ce mode.

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- COS et Domaine
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_10.png" alt="10"/>
Renseignez le cos (Class of Service) de vos bals partagées et votre domaine de mail

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- Règles de partages
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_11.png" alt="11"/>
Vous devez définir le nombre de partages maximum autorisé par bal.
Cette Limitation sera indicative dans l'interface de partage des bals.

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- Dossiers
Cette partie permet de mapper les dossiers système de zimbra des bals institutionnelles vers des noms de dossiers que vous aurez choisi pour les utilisateurs qui recevront les partages.
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_12.png" alt="12"/>
Dans la partie 1 modifier le nom de chaque dossier si besoin.
La partie 2 concerne le dossier qui sera rajouter au dossiers système (1) et dont les utilisateurs pourront se servir pour créer leur sous-dossiers (ils n'auraont pas le droit de créer des dossiers à la racine du partage).
La partie 3 sera le nom du dossier dans lequel tout les point de montage (partage) seront réalisés pour chauqe utilisateur.
Les partages ne sont pas montés directement à la racine de l'utilisateur mais bien dans ce dossier pour plus de clarté.

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- Calendrier
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_13.png" alt="13"/>
Ici vous pouvez renseigner le préfix qui sera ajouter au point de montage des calendriers.

<p id="cron"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Configuration des tâches planifiées:

Deux tâches planifiées peuvent être activées.

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- Envoie des rapports structures
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_15.png" alt="15"/>
Cette tâche planfiée va générer un récapitulatif des partages de chaque bal regroupées par structure. Le rapport est ensuite envoyé au responsable de la structure.
Pour activer cette tâche cliquez sur le switch on/off. Une fois activé, vous pouvez définir le crons comme vous souhaitez et cliquez sur Modifier le cron"
Il est conseillé de faire tournéer cette tâche une fois par semaine en pleine nuit.

<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
- Génération du rapport général des bals
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_16.png" alt="16"/>
Cette tâche planfiée va générer un rapport complet pour toutes les bals. Il sera ensuite visible depuis le Tableau de Bord.
Pour activer cette tâche cliquez sur le switch on/off. Une fois activé, vous pouvez définir le crons comme vous souhaitez et cliquez sur Modifier le cron"
Il est conseillé de faire tourner cette tâche toute les nuits

<p id="fin"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
### Finalisation:

Une fois toute la configuration terminée, vous pouvez cliquer sur Terminer
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_17.png" alt="17"/>
Vous serez alors rediriger vers votre serveur cas pour l'authentification.
En tant qu'administrateur de l'application vous aurez accès à la partie configuration directement depuis l'application:
<img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_18.png" alt="18"/>

Si besoin Vous pourrez modifier directement la configuration. Il est possible d'ajouter votre logo (qui remplacera l'image en haut à gauche). Vous pouvez également renseigner les mentions légales (qui seront accessible depuis un lien dans le pied de page) et ajouter une information pour l'assistance (texte, lien..., visible également dans le pied de page)
