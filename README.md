# Analyse Réseau avec Wireshark et TShark

## Introduction

**Wireshark** est un logiciel open source d’analyse des protocoles réseau créé par Gerald Combs en 1998. Il est utilisé par des agences gouvernementales, de grandes entreprises, des organisations à but non lucratif et des établissements pédagogiques pour résoudre des problèmes réseau et former à l’analyse réseau.

Wireshark est un outil de **capture et d’analyse de paquets**. Il permet de capturer le trafic réseau local et d’analyser les données collectées hors ligne. Il supporte de nombreux types de trafic, tels que :
- Ethernet
- Bluetooth
- Réseaux sans fil (IEEE 802.11)
- Token Ring
- Frame Relay
- Et bien plus encore

> **Remarque** : un « paquet » est un message d’un protocole réseau (ex. : TCP, DNS, etc.)

---

## Concepts Clés

### Trame vs Paquet

- **Trame** : bloc de données transmis sur la **liaison de données** (ex. : Ethernet, ATM).
- **Paquet** : bloc de données transmis sur la **couche réseau** (ex. : IP).

### Formats de fichiers : PCAP et PCAPNG

- **PCAP (Packet CAPture)** : format de capture de paquets utilisé pour analyser et diagnostiquer les réseaux.
- **PCAPNG (PCAP Next Generation)** : format plus évolué principalement utilisé par Wireshark, qui permet d’enregistrer des captures réseau avec plus de détails et de flexibilité.

---

## Installation de Wireshark sur Debian

```bash
sudo apt-get install wireshark
sudo dpkg-reconfigure wireshark-common  # pour configurer les privilèges utilisateurs
sudo adduser $USER wireshark            # ajouter l’utilisateur au groupe Wireshark
