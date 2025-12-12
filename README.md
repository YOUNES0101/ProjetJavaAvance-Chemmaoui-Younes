# 🛡️ Simulateur de Pare-feu (Firewall Simulator)
### Projet Java Avancé | Chemmaoui Younes

![Java](https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=java&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![Focus](https://img.shields.io/badge/Focus-Network%20Security-blue?style=for-the-badge)

## 📋 Présentation du Projet

Ce projet modélise un **système de sécurité réseau** complet conçu pour analyser le trafic entrant, identifier les menaces potentielles et bloquer les accès non autorisés. Il agit comme un filtre intelligent, laissant passer les communications légitimes tout en appliquant des règles de sécurité strictes.

---

## 🚀 Contexte et Objectifs

### Le Contexte
Dans un environnement réseau moderne, la sécurité dépend de la capacité à analyser rapidement des millions de requêtes. La latence n'est pas une option.

### L'Objectif
Développer une application Java haute performance simulant un **Pare-feu (Firewall)**.
* **Génération de trafic :** Simulation d'un flux massif de "Paquets Réseaux".
* **Moteur de règles :** Filtrage dynamique (Allow/Block/Drop).
* **Critères de filtrage :** Adresse IP source, Port de destination, Protocole (TCP/UDP), etc.

---

## 🛠️ Architecture et Conception

### Diagramme de Classes (Conceptuel)
Voici la structure logique des composants principaux du simulateur :

```mermaid
classDiagram
    class Packet {
        -String sourceIP
        -String destIP
        -int port
        -String protocol
        +toString()
    }

    class Rule {
        -String ipPattern
        -int port
        -Action action
        +matches(Packet p) boolean
    }

    class Firewall {
        -List~Rule~ rules
        +addRule(Rule r)
        +process(Packet p)
    }

    class NetworkSimulator {
        +generateTraffic()
        +startStream()
    }

    Firewall "1" o-- "*" Rule : contient
    Firewall ..> Packet : analyse
    NetworkSimulator ..> Firewall : envoie du trafic
