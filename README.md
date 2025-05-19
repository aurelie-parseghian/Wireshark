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

```bash
sudo apt-get update
sudo apt-get install wireshark
sudo dpkg-reconfigure wireshark-common  # Configure les droits d'accès
sudo adduser $USER wireshark            # Ajoute l'utilisateur au groupe wireshark

### Analyse réseau avec curl et Wireshark

Exemple d’utilisation de curl pour générer du trafic TCP :
sudo apt install curl
curl alcasar.laplateforme.io
