span

<p id="zimbra"><a href="#top"><img src="https://raw.githubusercontent.com/viduc/gepadbal/main/documentations/images/up.png" alt="up" style="width:40px;"/> HAUT</a></p>
<h4 style="color: #7ee787" >Configuration du serveur ZIMBRA:</h4>
<p>Il est nécessaire d'apporter quelques modifications au serveur zimbra.</p>
<p>Voici les valeurs qu'il faut modifier sur la plateforme zimbra afin de réaliser des requêtes soap "en masse"

```
DoSFilter Delay (milliseconds) :
zimbraHttpDosFilterDelayMillis: 0
```

<p>DoSFilter Maximum Requests Per Second :
Maximum number of requests from a connection per second. Requests in excess of this are throttled. The default is 30 and the minimum is 1.</p>

```
zimbraHttpDosFilterMaxRequestsPerSec: 1000
zimbraHttpThrottleSafeIPs: <@ip du serveur qui va interroger faire des requêtes soap>
```

<p>Pour mettre ces valeurs il a y deux façons de procéder:</p>
<ul>
    <li>soit de façon globale :

```zmprov mcf zimbraHttpDosFilterDelayMillis 0
            zmprov mcf zimbraHttpDosFilterMaxRequestsPerSec 1000
            mprov mcf zimbraHttpThrottleSafeIPs 1.2.3.4
```

</li>
<li>soit local au serveur sur lequel sera executé les requêtes

```
        zmrpov ms `zmhostname` zimbraHttpDosFilterDelayMillis 0
        zmrpov ms `zmhostname` zimbraHttpDosFilterMaxRequestsPerSec 1000
        zmrpov ms `zmhostname` zimbraHttpThrottleSafeIPs 1.2.3.4
```

</li></ul>
<p>Pour le wsdl une nouvelle variable a été introduite (Patch 25) dans le zmlocalconfig wsdl_use_public_service_hostname par défaut à true
cela signifie que l'on va utiliser le nom publique de la plateforme zimbra (https://zimbra.univ-grenoble-alpes.fr)pour pouvoir faire les requêtes soap</p>
<p>Il faudra donc ouvrir sur les proxys le port 9071 pour pouvoir faire des requêtes en relation avec les méthode admin (que l'on voit dan le fichier https://zimbra.univ-grenoble-alpes.fr/service/wsdl/ZimbraAdminService.wsdl)
mais également le port 7071</p>
<p>Si la variable zmlocalconfig wsdl_use_public_service_hostname est à false il faudra ouvrir les port 7071 et 9071 sur le serveur qui prendra les requêtes</p>
<p>Le plus simple reste de donner l'accès ip à la machine qui fera les requêtes soap qui recevra les requêtes.</p>

</div>
