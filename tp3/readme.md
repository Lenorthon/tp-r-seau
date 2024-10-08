# TP3 : 32°13'34"N 95°03'27"W

## I. ARP basics

### ☀️ Avant de continuer... 
```
PS C:\Users\david> ipconfig /all
 Adresse physique . . . . . . . . . . . : F8-FE-5E-18-12-DF

```
### ☀️ Affichez votre table ARP
```
PS C:\Users\david> arp -a

Interface : 192.168.56.1 --- 0x3
  Adresse Internet      Adresse physique      Type
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 10.33.74.229 --- 0xc
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.73.77           98-8d-46-c4-fa-e5     dynamique
  10.33.77.160          c8-94-02-f8-ab-97     dynamique
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique

```
### ☀️ Déterminez l'adresse MAC de la passerelle du réseau de l'école
```
PS C:\Users\david> arp -a
10.33.79.254   7c-5a-1c-d3-d8-76  dynamique
```
### ☀️ Supprimez la ligne qui concerne la passerelle
```
PS C:\Windows\system32> arp -d 10.33.79.254  7c-5a-1c-d3-d8-76     dynamique
```
### ☀️ Prouvez que vous avez supprimé la ligne dans la table ARP
```
  Adresse Internet      Adresse physique      Type
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```
### ☀️ Wireshark
voir arp1

## II. ARP dans un réseau local

## 1. Basics

### ☀️ Déterminer
```
PS C:\Windows\system32> ipconfig /all
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : F8-FE-5E-18-12-DF
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::a9b8:14ae:b7a6:3e3e%12(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.180.93(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Bail obtenu. . . . . . . . . . . . . . : mardi 8 octobre 2024 10:51:38
   Bail expirant. . . . . . . . . . . . . : mardi 8 octobre 2024 11:59:29
   Passerelle par défaut. . . . . . . . . : 192.168.180.29
   Serveur DHCP . . . . . . . . . . . . . : 192.168.180.29
   IAID DHCPv6 . . . . . . . . . . . : 167312990
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-96-0C-9A-00-EE-BC-DB-4B-42
   Serveurs DNS. . .  . . . . . . . . . . : 192.168.180.29
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```
### ☀️ DIY
```
PS C:\Windows\system32> ipconfig
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6. . . . . . . . . . . . . .: 2a02:8440:6141:2ff8:f277:4ae5:c012:811a
   Adresse IPv6 temporaire . . . . . . . .: 2a02:8440:6141:2ff8:3920:e808:5d15:179b
   Adresse IPv6 de liaison locale. . . . .: fe80::a9b8:14ae:b7a6:3e3e%12
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.180.18
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . : fe80::e0b6:7aff:fe88:2414%12
                                       192.168.180.29
```
### ☀️ Pingz!                                    
```
PS C:\Windows\system32> ping 192.168.180.182

Envoi d’une requête 'Ping'  192.168.180.182 avec 32 octets de données :
Réponse de 192.168.180.182 : octets=32 temps=62 ms TTL=128
Réponse de 192.168.180.182 : octets=32 temps=9 ms TTL=128
Réponse de 192.168.180.182 : octets=32 temps=51 ms TTL=128
Réponse de 192.168.180.182 : octets=32 temps=60 ms TTL=128

Statistiques Ping pour 192.168.180.182:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 9ms, Maximum = 62ms, Moyenne = 45ms
PS C:\Windows\system32> ping google.com

Envoi d’une requête 'ping' sur google.com [2a00:1450:4007:806::200e] avec 32 octets de données :
Réponse de 2a00:1450:4007:806::200e : temps=45 ms
Réponse de 2a00:1450:4007:806::200e : temps=98 ms
Réponse de 2a00:1450:4007:806::200e : temps=75 ms
Réponse de 2a00:1450:4007:806::200e : temps=59 ms

Statistiques Ping pour 2a00:1450:4007:806::200e:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 45ms, Maximum = 98ms, Moyenne = 69ms
```
## 2. ARP

### ☀️ Affichez votre table ARP !
```
PS C:\Windows\system32> arp -a

Interface : 192.168.56.1 --- 0x3
  Adresse Internet      Adresse physique      Type
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.180.91 --- 0xc
  Adresse Internet      Adresse physique      Type
  192.168.180.29        e2-b6-7a-88-24-14     dynamique
  192.168.180.182       e4-c7-67-81-d0-3f     dynamique
  192.168.180.255       ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```
### ➜ Wireshark that
```
voir arp2
```
### ☀️ Capture arp2.pcap

voir arp3
