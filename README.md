# Analyse et Capture Réseau avec Wireshark et TShark

---

## Présentation

Wireshark est un logiciel open source d’analyse des protocoles réseau, créé en 1998 par Gerald Combs.  
Il est largement utilisé par des agences gouvernementales, des entreprises, des organisations à but non lucratif et des établissements pédagogiques pour diagnostiquer des problèmes réseau, analyser le trafic et réaliser des formations.

Wireshark permet de **capturer** et **analyser** les paquets échangés sur un réseau local.  
Il supporte plusieurs types de réseaux comme Ethernet, Bluetooth, réseaux sans fil (IEEE 802.11), Token Ring, Frame Relay, etc.

> **Note :** Un paquet est un message transporté par un protocole réseau (ex : TCP, DNS).

---

## Concepts clés

### Différence entre trame et paquet

- **Trame** : Bloc de données transmis sur la couche liaison (ex : Ethernet, ATM).  
- **Paquet** : Bloc de données transmis sur la couche réseau (ex : IP).

### Formats de fichiers de capture

- **PCAP** : Format classique pour enregistrer les captures réseau.  
- **PCAPNG** : Format amélioré utilisé par Wireshark, qui permet d’enregistrer plus d’informations (métadonnées, interfaces multiples, etc.).

---

## Installation sur Debian

Pour installer Wireshark et le configurer correctement pour un usage utilisateur :

```
sudo apt-get update
sudo apt-get install wireshark
sudo dpkg-reconfigure wireshark-common  # Configure les droits d'accès
sudo adduser $USER wireshark            # Ajoute l'utilisateur au groupe wireshark
```

<img src="/screen/1.png" alt="Capture d'écran"/>

---

### Analyse réseau avec curl et Wireshark

Exemple d’utilisation de curl pour générer du trafic TCP :
```
sudo apt install curl
curl alcasar.laplateforme.io
```
Cette commande permet d’envoyer des requêtes HTTP et d’observer le trafic TCP associé dans Wireshark.

---

### Diagramme

<img src="/screen/2.png" alt="Capture d'écran"/>

---

<img src="/screen/3.png" alt="Capture d'écran"/>
<img src="/screen/4.png" alt="Capture d'écran"/>
<img src="/screen/5.png" alt="Capture d'écran"/>
<img src="/screen/6.png" alt="Capture d'écran"/>
<img src="/screen/7.png" alt="Capture d'écran"/>
<img src="/screen/8.png" alt="Capture d'écran"/>
<img src="/screen/9.png" alt="Capture d'écran"/>
<img src="/screen/10.png" alt="Capture d'écran"/>
<img src="/screen/11.png" alt="Capture d'écran"/>
<img src="/screen/12.png" alt="Capture d'écran"/>

---

### Sécurité : FTP vs TLS
Lors de la capture :

FTP : Protocole non sécurisé, les informations sont visibles en clair dans la capture (identifiants, commandes, données).

TLS : Protocole sécurisé, les données sont chiffrées, rendant leur lecture impossible sans la clé de chiffrement.

<img src="/screen/13.png" alt="Capture d'écran"/>

<img src="/screen/14.png" alt="Capture d'écran"/>

---

## Utilisation de TShark (interface en ligne de commande de Wireshark)
### Installation
```
sudo apt install tshark
```
Capture d’un trafic spécifique (ex : FTP sur port 21)
```
sudo tshark -i ens33 -f "port 21" -w ftp_capture.pcapng
```

<img src="/screen/15.png" alt="Capture d'écran"/>

### Gestion du fichier de capture
La capture est enregistrée par défaut dans /root (car la commande est lancée avec sudo).

Pour déplacer le fichier vers votre dossier utilisateur :
```
sudo mv /root/ftp_capture.pcapng /home/aurelie/
```
Pour permettre l’ouverture du fichier par l’utilisateur :
```
sudo chown aurelie:aurelie /home/aurelie/ftp_capture.pcapng
```
### Limiter le nombre de paquets capturés
Pour capturer un nombre défini de paquets (par exemple 100) :
```
sudo tshark -i ens33 -f "port 21" -c 100 -w ftp_capture_limited.pcapng
```

<img src="/screen/16.png" alt="Capture d'écran"/>

---

## Remarques finales
Wireshark est un outil puissant pour comprendre et analyser le fonctionnement des réseaux.
Son utilisation demande une bonne connaissance des protocoles réseau et des bonnes pratiques pour garantir la sécurité des données capturées.
