# TP2 : Hey yo tell a neighbor tell a friend

## 1. Quelques pings

### 🌞 Prouvez que votre configuration est effective

```
PS C:\Users\willi> Get-NetIPAddress -InterfaceAlias Ethernet


IPAddress         : fe80::ae57:56ef:302d:1e10%18
InterfaceIndex    : 18
InterfaceAlias    : Ethernet
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 10.1.1.3
InterfaceIndex    : 18
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore
```

### 🌞 Tester que votre LAN + votre adressage IP est fonctionnel
```

PS C:\Users\willi> ping 10.1.1.2

Envoi d’une requête 'Ping'  10.1.1.2 avec 32 octets de données :
Réponse de 10.1.1.2 : octets=32 temps<1ms TTL=128
Réponse de 10.1.1.2 : octets=32 temps<1ms TTL=128
Réponse de 10.1.1.2 : octets=32 temps<1ms TTL=128
Réponse de 10.1.1.2 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.1.1.2:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

### 🌞 Capture de ping
Voir Ping-1

# II. Utilisation des ports

## 1. Animal numérique

### 🌞 Sur le PC serveur
``` 
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> ./nc.exe 10.1.1.2 8888
```
 ### 🌞Sur le PC serveur toujours
 ```
  TCP    10.1.1.3:39230         10.1.1.2:8888          ESTABLISHED
 [nc.exe]
 ```
 ### 🌞 Sur le PC client
 ``` 
 PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> .\nc 10.1.1.3 8888
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11>
```
### 🌞 Echangez-vous des messages
```
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> ./nc.exe 10.1.1.2 8888
cc
ca va ?
salut
pas mal les bzez
````
### 🌞 Utilisez une commande qui permet de voir la connexion en cours
```
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> netstat

Connexions actives

  Proto  Adresse locale         Adresse distante       État
  TCP    10.33.77.148:38400     162.159.135.234:https  ESTABLISHED
  TCP    10.33.77.148:38572     par21s20-in-f3:http    ESTABLISHED
  TCP    10.33.77.148:38581     wf-in-f188:5228        ESTABLISHED
  TCP    10.33.77.148:38638     ec2-54-89-233-95:9339  ESTABLISHED
  TCP    10.33.77.148:38659     ae41dd3672a2e5b7b:https  ESTABLISHED
  TCP    10.33.77.148:38664     server-3-164-163-9:https  ESTABLISHED
  TCP    10.33.77.148:38916     ws-in-f188:5228        ESTABLISHED
```

### 🌞 Faites une capture Wireshark complète d'un échange
Voir Ping-e

### 🌞 Inversez les rôles

```
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> .\nc -lvp 8888
listening on [any] 8888 ...
DNS fwd/rev mismatch: DESKTOP-N8AD10N != DESKTOP-N8AD10N.local
connect to [10.1.1.3] from DESKTOP-N8AD10N [10.1.1.2] 47408
salut man
ca va ?
```
Voir ping-3

# III. Analyse de vos applications usuelles

## 1. Serveur web
### 🌞 Utilisez Wireshark pour capturer du trafic HTTP
Voir http.pcapng

2. Autres services
### 🌞 Pour les 5 applications 
```
Voicie la commande  netstat pour voir les connexions actives sur le système.


PS C:\Windows\system32> netstat -a -b -n

Connexions actives

  Proto  Adresse locale         Adresse distante       État
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  RpcSs
 [svchost.exe]
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:5040           0.0.0.0:0              LISTENING
  CDPSvc
 [svchost.exe]
  TCP    0.0.0.0:7680           0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:27036          0.0.0.0:0              LISTENING
 [steam.exe]
  TCP    0.0.0.0:49664          0.0.0.0:0              LISTENING
 [lsass.exe]
  TCP    0.0.0.0:49665          0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:49668          0.0.0.0:0              LISTENING
  Schedule
 [svchost.exe]
  TCP    0.0.0.0:49669          0.0.0.0:0              LISTENING
  EventLog
 [svchost.exe]
  TCP    0.0.0.0:49672          0.0.0.0:0              LISTENING
 [spoolsv.exe]
  TCP    0.0.0.0:49691          0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    10.33.74.229:139       0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    10.33.74.229:49454     20.199.120.151:443     ESTABLISHED
  WpnService
 [svchost.exe]
  TCP    10.33.74.229:57574     52.123.200.65:443      ESTABLISHED
 [ms-teams.exe]
  TCP    10.33.74.229:57602     20.199.120.151:443     ESTABLISHED
 [OneDrive.exe]
  TCP    10.33.74.229:57609     52.123.139.78:443      ESTABLISHED
 [msedgewebview2.exe]
  TCP    10.33.74.229:57615     162.159.130.234:443    ESTABLISHED
 [Discord.exe]
  TCP    10.33.74.229:57635     185.25.182.20:27021    ESTABLISHED
 [steam.exe]
  TCP    10.33.74.229:57718     54.146.56.54:443       ESTABLISHED
 [EpicGamesLauncher.exe]
  TCP    10.33.74.229:57725     20.199.120.151:443     ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:57765     192.229.221.95:80      CLOSE_WAIT
 [HxTsr.exe]
  TCP    10.33.74.229:57843     20.250.77.142:443      ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:57858     3.64.143.176:443       ESTABLISHED
 Impossible d’obtenir les informations de propriétaire
  TCP    10.33.74.229:57898     52.97.201.210:443      ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.74.229:57905     13.107.246.254:443     CLOSE_WAIT
 [SearchHost.exe]
  TCP    10.33.74.229:57912     172.65.251.78:443      ESTABLISHED
 [chrome.exe]
  TCP    10.33.74.229:58085     185.199.111.154:443    ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58090     13.89.178.26:443       ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58092     185.199.111.154:443    ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58093     185.199.111.133:443    ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58095     140.82.113.26:443      ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58102     34.120.22.49:443       TIME_WAIT
  TCP    10.33.74.229:58108     40.126.49.152:443      TIME_WAIT
  TCP    10.33.74.229:58109     3.211.157.115:443      ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58112     104.18.86.42:443       ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58118     54.204.178.109:443     ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58119     54.170.196.176:443     ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58121     54.84.54.3:443         ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58122     3.211.157.115:443      ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58126     54.84.54.3:443         ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58127     3.211.157.115:443      ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58128     3.211.157.115:443      ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58137     86.64.231.167:443      CLOSE_WAIT
 [msedge.exe]
  TCP    10.33.74.229:58154     20.189.173.12:443      TIME_WAIT
  TCP    10.33.74.229:58156     104.18.86.42:443       TIME_WAIT
  TCP    10.33.74.229:58158     20.189.173.7:443       ESTABLISHED
 Impossible d’obtenir les informations de propriétaire
  TCP    10.33.74.229:58160     52.203.66.187:443      CLOSE_WAIT
 [EpicGamesLauncher.exe]
  TCP    10.33.74.229:58161     45.57.91.1:443         ESTABLISHED
 [msedge.exe]
  TCP    10.33.74.229:58162     23.217.238.254:443     ESTABLISHED
 [steamwebhelper.exe]
  TCP    10.33.74.229:58164     44.220.113.135:443     CLOSE_WAIT
 [EpicGamesLauncher.exe]
  TCP    10.33.74.229:58165     20.42.65.93:443        ESTABLISHED
 [Microsoft.SharePoint.exe]
  TCP    10.33.74.229:58166     34.120.22.49:443       ESTABLISHED
 [chrome.exe]
  TCP    10.33.74.229:58167     34.236.219.197:443     ESTABLISHED
 [chrome.exe]
  TCP    127.0.0.1:6463         0.0.0.0:0              LISTENING
 [Discord.exe]
  TCP    127.0.0.1:9222         0.0.0.0:0              LISTENING
 [msedgewebview2.exe]
  TCP    127.0.0.1:27060        0.0.0.0:0              LISTENING
 [steam.exe]
  TCP    127.0.0.1:49678        127.0.0.1:49679        ESTABLISHED
 [WUDFHost.exe]
  TCP    127.0.0.1:49679        127.0.0.1:49678        ESTABLISHED
 [WUDFHost.exe]
  TCP    127.0.0.1:49853        0.0.0.0:0              LISTENING
 [steam.exe]
  TCP    127.0.0.1:49853        127.0.0.1:49859        ESTABLISHED
 [steam.exe]
  TCP    127.0.0.1:49854        0.0.0.0:0              LISTENING
 [steam.exe]
  TCP    127.0.0.1:49854        127.0.0.1:49858        ESTABLISHED
 [steam.exe]
  TCP    127.0.0.1:49858        127.0.0.1:49854        ESTABLISHED
 [steamwebhelper.exe]
  TCP    127.0.0.1:49859        127.0.0.1:49853        ESTABLISHED
 [steamwebhelper.exe]
  TCP    127.0.0.1:55403        127.0.0.1:55404        ESTABLISHED
 [WUDFHost.exe]
  TCP    127.0.0.1:55404        127.0.0.1:55403        ESTABLISHED
 [WUDFHost.exe]
  TCP    127.0.0.1:56039        127.0.0.1:56040        ESTABLISHED
 [ipfsvc.exe]
  TCP    127.0.0.1:56040        127.0.0.1:56039        ESTABLISHED
 [ipfsvc.exe]
  TCP    127.0.0.1:56296        0.0.0.0:0              LISTENING
 [RiotClientServices.exe]
  TCP    192.168.56.1:139       0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:135               [::]:0                 LISTENING
  RpcSs
 [svchost.exe]
  TCP    [::]:445               [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:7680              [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:49664             [::]:0                 LISTENING
 [lsass.exe]
  TCP    [::]:49665             [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:49668             [::]:0                 LISTENING
  Schedule
 [svchost.exe]
  TCP    [::]:49669             [::]:0                 LISTENING
  EventLog
 [svchost.exe]
  TCP    [::]:49672             [::]:0                 LISTENING
 [spoolsv.exe]
  TCP    [::]:49691             [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::1]:42050            [::]:0                 LISTENING
 [Microsoft.SharePoint.exe]
  TCP    [::1]:49673            [::]:0                 LISTENING
 [jhi_service.exe]
  UDP    0.0.0.0:500            *:*
  IKEEXT
 [svchost.exe]
  UDP    0.0.0.0:4500           *:*
  IKEEXT
 [svchost.exe]
  UDP    0.0.0.0:5050           *:*
  CDPSvc
 [svchost.exe]
  UDP    0.0.0.0:5353           *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5355           *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:6666           *:*
 [EpicGamesLauncher.exe]
  UDP    0.0.0.0:27036          *:*
 [steam.exe]
  UDP    0.0.0.0:50060          34.120.22.49:443
 [chrome.exe]
  UDP    0.0.0.0:50081          *:*
 [ms-teams.exe]
  UDP    0.0.0.0:52821          *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:54517          8.8.4.4:443
 [msedge.exe]
  UDP    0.0.0.0:60872          8.8.8.8:443
 [chrome.exe]
  UDP    0.0.0.0:61282          *:*
 [EpicGamesLauncher.exe]
  UDP    0.0.0.0:64938          *:*
 [ms-teams.exe]
  UDP    10.33.74.229:137       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    10.33.74.229:138       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    10.33.74.229:1900      *:*
  SSDPSRV
 [svchost.exe]
  UDP    10.33.74.229:2177      *:*
  QWAVE
 [svchost.exe]
  UDP    10.33.74.229:51970     *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:1900         *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:51971        *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:57990        127.0.0.1:57990
  iphlpsvc
 [svchost.exe]
  UDP    192.168.56.1:137       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.56.1:138       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.56.1:1900      *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.56.1:2177      *:*
  QWAVE
 [svchost.exe]
  UDP    192.168.56.1:54383     *:*
  SSDPSRV
 [svchost.exe]
  UDP    [::]:500               *:*
  IKEEXT
 [svchost.exe]
  UDP    [::]:4500              *:*
  IKEEXT
 [svchost.exe]
  UDP    [::]:5353              *:*
 [chrome.exe]
  UDP    [::]:5353              *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:5353              *:*
 [msedge.exe]
  UDP    [::]:5353              *:*
 [chrome.exe]
  UDP    [::]:5353              *:*
 [msedge.exe]
  UDP    [::]:5355              *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:50081             *:*
 [ms-teams.exe]
  UDP    [::]:52821             *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:64938             *:*
 [ms-teams.exe]
  UDP    [::1]:1900             *:*
  SSDPSRV
 [svchost.exe]
  UDP    [::1]:54382            *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::a9b8:14ae:b7a6:3e3e%12]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::a9b8:14ae:b7a6:3e3e%12]:2177  *:*
  QWAVE
 [svchost.exe]
  UDP    [fe80::a9b8:14ae:b7a6:3e3e%12]:54381  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::e495:f205:63dd:cedf%3]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::e495:f205:63dd:cedf%3]:2177  *:*
  QWAVE
 [svchost.exe]
  UDP    [fe80::e495:f205:63dd:cedf%3]:54380  *:*
  SSDPSRV
 [svchost.exe]
```