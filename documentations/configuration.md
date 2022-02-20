<meta name="viewport" content="width=device-width, initial-scale=1">
<title>E-GEPADBAL</title>
<meta name="color-scheme" content="light dark">
<link rel="stylesheet" href="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/css/github-markdown-dark.css">
<style>
	.markdown-body {
		box-sizing: border-box;
		min-width: 200px;
		max-width: 980px;
		margin: 0 auto;
		padding: 45px;
	}
    @media (prefers-color-scheme: dark) {
            body {
                background-color: #0d1117;
            }
        }
	@media (max-width: 767px) {
		.markdown-body {
			padding: 15px;
		}
	}
</style>
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
    <h1>E-GEPADBAL - Configuration de l'application </h1>
    <div>
        <ul>
            <li><a href="#interface">Interface web</a></li>
            <li><a href="#generale">Configuration générale</a></li>
            <li><a href="#zimbra">Configuration Zimbra</a></li>
            <li><a href="#cron">Configuration des tâches planifiées</a></li>
            <li><a href="#fin">Finalisation</a></li>
        </ul>
    </div>
    La configuration de l'application se fait depuis une interface web dediée.
    <p id="interface"></p>
    <h4 style="color: #7ee787" > Accès à l'interface web:</h4>
    <p>Pour accéder à l'interface web de configuration, entrez dans un navigateur l'url que vous avez définit pour gepadbal</p>
    <p><code>ex: http(s)://gepadbal.mondomain.fr</code></p>
    <img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_01.png" alt="01"/>
    <div style="width: 70%; padding-left: 3em; padding-right: 3em;">
        <p>
            <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
            <div style="margin-left: 45px">L'url vers laquelle vous êtes redirigé ne sera accessible qu'après avoir installé l'application et jusqu'à ce que 
            l'installation soit terminée. Une fois l'installation effectuée, cette url ne sera plus accesible (authenfication par CAS). 
            Les administrateurs authentifiés auront ensuite accès à une interface de configuration en cas de besoin de modification.</div>
        </p>
        <p>
            <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
            <div style="margin-left: 45px">Trois grandes étapes de configuration sont à renseigner avec chacune d'elle plusieurs éléments. Vous pouvez naviger dans ces éléments avec les fléches allant de gauche à droite. Vous devez enregistrer vos modifications avant de changer d'élément:
                <p></p>
                <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_02.png" alt="02"/></p>
            </div>
        </p>
    </div>
<p id="generale"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h4 style="color: #7ee787" >Configuration générale:</h4>
La première étape consiste à configurer les informations générales:
<ul>
    <li>
        <h5>LDAP</h5>
        <p>Vous devez disposer d'un serveur <a href="https://fr.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol">ldap</a> pour la gestion des accès utilisateurs.</p>
        <p class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="checked" disabled="disabled">
            Dans le premier champ renseignez le nom (ou ip) de votre serveur LDAP. Précisez également le port.
        </p>
        <p class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="checked" disabled="disabled">
            Définissez le protocol à utiliser avec le bouton switch entre LDAP et LDAPS.
        </p>
        <p class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="checked" disabled="disabled">
            Renseignez ensuite de DN général du serveur (par ex: OU=monOu,dc=mondc,dc=org).
        </p>
        <p class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="checked" disabled="disabled">
            Ensuite dans le champ ou people, renseignez l'OU qui contient vos utilisateurs (ex: ou=people).
        </p>  
        <p class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="checked" disabled="disabled">
            De même pour l'ou groupe, renseignez l'OU qui contient vos groupes.
        </p>  
        <p class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="checked" disabled="disabled">
            Pour l'authentification, reseignez le compte ayant droit d'accéder et son mot de passe (ex (cn=monlogin,ou=ouadmin).
        </p>   
        <p class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="checked" disabled="disabled">
            Enfin vous devez renseigner trois attributs particulier à savoir le nom de *objectClassGroup*, le nom de l'*uid* et le nom du *memberof*
        </p>
        <p>
            <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
            <div style="margin-left: 45px">Vous disposez d'un bouton pour tester votre connexion avec les informations reseignées (vous devez enregistrer avant de tester).</div>
        </p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_04.png" alt="04"/></p>
        <p class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="checked" disabled="disabled">
            Vous devez ensuite renseigner les groupes administrateurs et assistance:
        </p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_04_1.png" alt="04_1"/></p>
        <div style="width: 70%; padding-left: 3em; padding-right: 3em;">
            <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
            <div style="margin-left: 45px">
                <p>Les membres du groupe admin auront tout les droits dans l'application (Partage + configuration).</p>
                Les membres assistances pourront partager les bals sans restrictions. Ils ont accès à toutes les fonctionnalités sauf la configuration.
            </div>
        </div>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>Authentification</h5>
        <p>L'authentification peut être faite soit depuis le serveur ldap, soit depuis
        un serveur <a href="https://www.single-sign-on.info/cas-sso-de-quoi-sagit-il/">CAS (sso)</a>.
        Choisissez le mode d'authentification qui vous convient avec le bouton switch:</p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_03.png" alt="04"/></p>
        <p>Si vous sélectionnez le serveur ldap, vous n'avez pas de configuration supplémentaire à effectuer.
        Si vous souhaitez utiliser une authentification cas, il vous faudra configurer le serveur:</p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_03_1.png" alt="03_1"/></p>
        <p>Entrez l'url de votre serveur cas ainsi que l'url de déconnexion</p>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>API</h5>
        <p>Le chargement de la liste des boîtes institutionnelles peut se faire de deux façons différentes.
        Vous pouvez créer une api depuis votre référentiel ou charger un fichier csv.</p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_05.png" alt="05"/></p>
        <div style="margin-left: 10%; background-color: #8b949e; width: 60%; color: #0a3069">
            <h6 style="color: #bf1e58">Chargement depuis une api</h6>
            <p>Votre api devra retourner une collection d'objet selon ce format:</p>
                <p><div class="highlight"><pre>
{
    "success":true,
    "message":"",
    "total":1,
    "data":[
        {
            "compte":"login", <span style="color: #3b2300"><i>le login de la boîte institutionnelle</i></span>
            "nom":"LA BAL", <span style="color: #3b2300"><i>le nom affiché de la boîte institutionnelle</i></span>
            "mail_prefere":"la.bal@mon-domain.fr", <span style="color: #3b2300"><i>l'adresse mail de la boîte institutionnelle</i></span>
            "structure":"LA STRUCTURE", <span style="color: #3b2300"><i>le nom de la structure associée de la boîte institutionnelle</i></span>
            "structureId":"1234", <span style="color: #3b2300"><i>l'id de la structure de la boîte institutionnelle</i></span>
            "mail_bal_archive_associee":null, <span style="color: #3b2300"><i>configuration non utilisée, mettre la valeur null</i></span>
            "compte_responsable":"loginDuResponsable" <span style="color: #3b2300"><i>le login du responsable de la boîte institutionnelle</i></span>
        },
    ]
}
            </pre></div></p>
             <p>L'url qui sera appelée devra être au format suivant:
             https://login:motdepasse@serveurdomain.fr/requete</p>
        </div>
        <div style="margin-left: 10%; background-color: #8b949e; width: 60%; color: #0a3069">
            <h6 style="color: #bf1e58">Chargement depuis un fichier</h6>
            <p style="margin-left: 1em; margin-right: 1em"><img src="./images/interface_06.png" alt="06"/></p>
            <p>Vous devrez créer un fichier csv selon le modèle suivant téléchargeable depuis l'interface (fichier enregistré).</p>
            <p>Il vous faudra recharger ce fichier (dans la page de configuration plus tard)
            à chaque fois que vous aurez des mises à jours de boîtes institutionnelles à effectuer.</p>
            <div style="width: 70%; padding-left: 3em; padding-right: 3em;">
                <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
                <div style="margin-left: 45px">
                    <p>Le lien "fichier des erreurs" permet de récupérer les bals qui n'ont pas pu être chargées depuis votre fichier.</p>
                </div>
            </div><p></p>
            <div style="width: 70%; padding-left: 3em; padding-right: 3em;">
                <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
                <div style="margin-left: 45px">
                    <p>Si une erreur est trouvée dans une ligne, elle ne sera pas chargée et sera enregistrée dans ce fichier.</p>
                </div>
            </div><p></p>
        </div>
        <div style="margin-left: 10%; background-color: #8b949e; width: 60%; color: #0a3069">
            <h6 style="color: #bf1e58">Sous structure</h6>
            <p>L'application vérifiera pour chaque structure si elle possède des sous structures et pourra le cas échéant proposer l'affichage (mail + partages) de celles ci.</p>
            <p>Le chargement de la liste des sous structures se fait selon le même principe que précédemment. Le retour de l'API se fera sous cette forme:.</p>
<p><div class="highlight"><pre>
{
    "success":true,
    "message":"",
    "total":1,
    "data":[
        {
            "id":"1234", <span style="color: #3b2300"><i>l'id du service</i></span>
            "lc_structure":"Libellé court", <span style="color: #3b2300"><i>le libéllé court de la structure</i></span>
            "ll_structure":"Libellé long", <span style="color: #3b2300"><i>le libellé long de la structure</i></span>
        },
    ]
}
            </pre></div></p>
            <p>Le format de l'api devra être: https://login:motdepasse@serveurdomain.fr/requete.</p>
            <p>Vous devrez également rajouter [idstructure] dans l'url que vous renseignez. </p>
            <p>Cette partie sera ensuite remplacée par l'id du la structure lors de l'appel à votre api.</p>
            <p>Vous pouvez donc construire l'url de votre api selon vos besoins et renseignant au bon endroit ce pattern.</p>
            <p>Si vous souhaitez utiliser le chargement par fichier csv, récupérer l'exemple comme pour le fichier des bals</p>
            <p></p><div style="width: 70%; padding-left: 3em; padding-right: 3em;">
                <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
                <div style="margin-left: 45px">
                    <p>Le chargement des bals et des sous structures est indépendant.
                    Vous pouvez utiliser l'api dans un des cas et le chargement par fichier pour l'autre cas.</p>
                </div>
            </div><p></p>
        </div>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>Logs</h5>
        <p>Choisissez le nombre de logs d'actions qui seront sauvegardés par bal. Chaque action réalisée sur une bal est enregistrée dans un fichier.</p>
        <p>Lorsque le nombre d'actions maximum est enregistrés dans le fichier, la plus ancienne des actions est supprimée de ce fichier.</p>
        <p>Par défaut il est conseillé de mettre ce champ à 10.</p>
        <img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_07.png" alt="07"/>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>SMTP</h5>
        <p>Il est necessaire de configurer un serveur smtp pour l'envoi des mails</p>
        <p>Enregistrez l'url du serveur smtp dans le premier champ. ex: smtp://login:motdepasse@smtps.dmoain.fr:587</p>
        <p>Renseignez l'adresse qui sera ajouter au from lors de l'envoie.</p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_08.png" alt="08"/></p>
        <p></p><div style="width: 70%; padding-left: 3em; padding-right: 3em;">
            <div style="float: left"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/warning.png" alt="warning" style="width:40px;"/></div>
            <div style="margin-left: 45px">
                <p>Vous pouvez tester l'envoie de mail depuis cette interface en entrant une 
                adresse valide dans le dernier champ et en cliquant sur "Envoyer un courriel"
                (il faut avoir sauvegarder la configuration)</p>
            </div>
        </div><p></p>
    </li>
</ul>
<p id="zimbra"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h4 style="color: #7ee787" >Configuration zimbra:</h4>
<p>Dans cette partié nous allons configurer toutes les informations relatives à zimbra.</p>
<ul>
    <li>
        <h5>WSDL</h5>
        <p>L'application GEPADBAL utilise le mode <a href="https://www.w3.org/TR/wsdl.html">wdsl</a> pour communiquer avec le serveur zimbra.</p>
        <p>Vous devrez donc avoir activer cette fonctionnalité sur votre instance et fournir l'url de connexion.</p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_09.png" alt="09"/></p>
        <p>Vous devez également fournir le login et mot de passe de connexion d'un compte ayant des droits de lecture et écriture pour ce mode.</p>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>COS et Domaine</h5>
        <p>Renseignez le cos (Class of Service) de vos bals partagées et votre domaine de mail</p>
        <img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_10.png" alt="10"/>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>Règles de partages</h5>
        <p>Vous devez définir le nombre de partages maximum autorisé par bal.</p>
        <p>Cette Limitation sera indicative dans l'interface de partage des bals pour les administrateurs et assistance.
        Elle sera limitative pour les gestionnaires (délégation)</p>
        <img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_11.png" alt="11"/>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>Dossiers</h5>
        <p>Cette partie permet de mapper les dossiers système de zimbra des bals 
        institutionnelles vers des noms de dossiers que vous aurez choisi pour les utilisateurs qui recevront les partages.</p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_12.png" alt="12"/></p>
        <p>Dans la partie 1 modifier le nom de chaque dossier si besoin.</p>
        <p>La partie 2 concerne le dossier qui sera rajouter au dossiers système 
        (1) et dont les utilisateurs pourront se servir pour créer leur sous-dossiers 
        (ils n'auraont pas le droit de créer des dossiers à la racine du partage).</p>
        <p>La partie 3 sera le nom du dossier dans lequel tout les point de montage (partage) seront réalisés pour chauqe utilisateur.</p>
        <p>Les partages ne sont pas montés directement à la racine de l'utilisateur mais bien dans ce dossier pour plus de clarté.</p>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>Calendrier</h5>
        <p>Ici vous pouvez renseigner le préfix qui sera ajouter au point de montage des calendriers.</p>
        <img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_13.png" alt="13"/>
    </li>
</ul>
<p id="cron"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h4 style="color: #7ee787" >Configuration des tâches planifiées:</h4>
<p>Deux tâches planifiées peuvent être activées.</p>
<ul>
    <li>
        <h5>Envoie des rapports structures</h5>
        <p>Cette tâche planfiée va générer un récapitulatif des partages de chaque bal regroupées par structure. 
        Le rapport est ensuite envoyé au responsable de la structure.</p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_15.png" alt="15"/></p>
        <p>Pour activer cette tâche cliquez sur le switch on/off. Une fois activé, vous pouvez définir le crons comme vous souhaitez et cliquez sur Modifier le cron"
        Il est conseillé de faire tournéer cette tâche une fois par semaine en pleine nuit.</p>
    </li>
</ul>
<p><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<ul>
    <li>
        <h5>Génération du rapport général des bals</h5>
        <p>Cette tâche planfiée va générer un rapport complet pour toutes les bals. Il sera ensuite visible depuis le Tableau de Bord.</p>
        <p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_16.png" alt="16"/></p>
        <p>Pour activer cette tâche cliquez sur le switch on/off. Une fois activé, vous pouvez définir le crons comme vous souhaitez et cliquez sur Modifier le cron"
        Il est conseillé de faire tourner cette tâche toute les nuits</p>
    </li>
</ul>
<p id="fin"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h4 style="color: #7ee787" >Finalisation:</h4>
<p>Une fois toute la configuration terminée, vous pouvez cliquer sur Terminer</p>
<p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_17.png" alt="17"/></p>
<p>Vous serez alors rediriger vers votre serveur cas pour l'authentification.</p>
<p>En tant qu'administrateur de l'application vous aurez accès à la partie configuration directement depuis l'application:</p>
<p><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/interface_18.png" alt="18"/></p>
<p>Si besoin Vous pourrez modifier directement la configuration. Il est possible 
d'ajouter votre logo (qui remplacera l'image en haut à gauche). Vous pouvez également 
renseigner les mentions légales (qui seront accessible depuis un lien dans le pied de page) 
et ajouter une information pour l'assistance (texte, lien..., visible également dans le pied de page)</p>
</div>
