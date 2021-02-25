# Endpoint 1

Ce noeud est le noeud primaire que nous allons configurer.
Il dipose d'une base de donnée source PostGreSQL qui sera synchronisée par l'instance locale de Bucardo à travers les tunnels Wireguard routés par Bird2.

## Installation des logiciels

### Installation de PostGreSQL

- Debian x86

>apt install postgresql postgresql-client

### Installation de Bucardo

- Debian x86

>apt install bucardo

### Installation de Wireguard

- Debian x86

>apt install wireguard

### Installation de Bird2

- Debian x86
> echo "deb [trusted=yes] https://bird.network.cz/debian/ buster main" > /etc/apt/sources.list.d/bird.list
> apt install bird2 bird2-doc

## Configuration

### Configuration de Wireguard

### Configuration de Bird2

### Configuration sz PostGreSQL

### Configuration de Bucardo
