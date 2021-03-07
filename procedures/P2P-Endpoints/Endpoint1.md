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

> sudo sh -c "echo 'deb http://deb.debian.org/debian buster-backports main contrib non-free' > /etc/apt/sources.list.d/buster-backports.list"
> apt update
>apt install wireguard

### Installation de Bird2

- Debian x86
> echo "deb [trusted=yes] https://bird.network.cz/debian/ buster main" > /etc/apt/sources.list.d/bird.list
>
> apt install bird2 bird2-doc

## Configuration

### Configuration réseau

Nous utilisons des IPs de liens locaux pou que les différentes machines du réseau puissent se joindre.

Dans le fichier /etc/network/interfaces, nous rajoutons cette ligne :

> iface lo:10 inet6 static
> 	address [IPv6 unique locale]/128

Pour cette exemple nous prenons [IPv6 unique locale] = fd00:10ca:1:1452::1/128

### Configuration de Wireguard

#### Avant-Propos

Wireguard se configure grâce à des fichiers nommés /etc/wireguard/wg[XX].conf, où [xx] correspond au numéro du tunnel désiré. Nous devons créer autant de fichiers que de tunnel souhaités.

Une fois une configuration rédigée, elle peut être démarrée par systemd. Il sufft d'ajouter le service souhaité de la manière suivante :
> sudo systemctl enable wg-quick@wg[xx].service
> sudo systemctl daemon-reload

Où [xx] correspond au numéro du tunnel (et donc qui fait référence au fichier de configuration rédigé).
Ensuite, il suffit de démarrer le tunnel :

> sudo systemctl start wg-quick@wg0

Et d'en afficher son statut :

> systemctl status wg-quick@wg0

Il est possible de voir l'état de tous les tunnels configurés :

> wg show

### Configuration de Bird2

### Configuration sz PostGreSQL

### Configuration de Bucardo
