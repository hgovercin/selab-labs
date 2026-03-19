# Cheat Sheet: System Engineering Lab (SELab)
**Student:** Hivda

## Basiscommando's

| Taak                                                   | Commando                         |
| :----------------------------------------------------- | :------------------------------- |
| Bekijk IP-adressen van alle netwerkadapters            | `ip a`                           |
| Bekijk de status van een service                       | `systemctl status SERVICE`       |
| Start een service                                      | `sudo systemctl start SERVICE`   |
| Stop een service                                       | `sudo systemctl stop SERVICE`    |
| Herstart een service                                   | `sudo systemctl restart SERVICE` |
| Update de package repositories (Ubuntu & Debian based) | `sudo apt update`                |
| Installeer een package (Ubuntu & Debian based)         | `sudo apt install PACKAGE`       |

## Git workflow

Simpele git workflow voor projecten met een enkele branch en zonder contributors.

| Task                                                               | Command                   |
| :----------------------------------------------------------------- | :------------------------ |
| Status van het huidige project                                     | `git status`              |
| Selecteer te committen bestanden                                   | `git add FILE...`         |
| Commit alle wijzigingen naar de lokale repository                  | `git commit -m 'MESSAGE'` |
| Push lokale wijzigingen naar de remote repository                  | `git push`                |
| Haal alle wijzigingen van de remote repository binnen in de lokale | `git pull`                |

## Checklist netwerkconfiguratie

1. Is het IP-adres correct? `ip a`
2. Is de router/default gateway correct? `ip r -n`
3. Is een DNS-server ingesteld? `cat /etc/resolv.conf`
# Labo 1 : Opdracht 1 - Package Management & Systeembeheer

## 1. APT Package Manager (Ubuntu Standaard)
Essentiële commando's voor het beheren van softwarepakketten.

| Taak | Commando |
| :--- | :--- |
| Update de pakketlijsten | `sudo apt update` |
| Installeer een nieuw pakket | `sudo apt install <pakketnaam>` |
| Verwijder een pakket | `sudo apt remove <pakketnaam>` |
| Upgrade alle geïnstalleerde pakketten | `sudo apt upgrade` |
| Zoek naar een specifiek pakket | `apt search <zoekterm>` |
| Verwijder onnodige afhankelijkheden | `sudo apt autoremove` |

## 2. Snap Package Manager
Voor het beheren van sandboxed applicaties.

| Taak | Commando |
| :--- | :--- |
| Installeer een snap pakket | `sudo snap install <pakketnaam>` |
| Bekijk een lijst van actieve snaps | `snap list` |
| Verwijder een snap pakket | `sudo snap remove <pakketnaam>` |

## 3. Netwerk & Systeem Informatie
Basiscommando's om de systeemstatus te controleren zoals vereist in het lab.

* **IP-adres controleren:** `ip a` (Toont alle netwerkadapters en hun IPv4/IPv6 adressen).
* **Default gateway bekijken:** `ip r -n`
* **DNS-instellingen controleren:** `cat /etc/resolv.conf`
* **Service status bekijken:** `systemctl status <service_naam>`
* **Service herstarten:** `sudo systemctl restart <service_naam>`

## 4. SSH & Remote Access
* **Inloggen op een remote server:** `ssh gebruiker@ip-adres`
* **Bestanden kopiëren via SCP:** `scp <bestand> gebruiker@ip-adres:/pad/naar/bestemming`

# Labo 2 Opdracht 2 MariaDB Server Installatie
**Student:** Hivda

## 1. Netwerk & Systeembeheer
| Taak | Commando |
| :--- | :--- |
| IP-adres controleren | `ip a` |
| Status van MariaDB bekijken | `systemctl status mariadb` |
| MariaDB herstarten | `sudo systemctl restart mariadb` |
| Configuratiebestand bewerken | `sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf` |

## 2. Remote Access (Bind-Address)
Om externe verbindingen toe te staan (vervangen van 127.0.0.1 naar 0.0.0.0):
bash
sudo sed -i 's/127.0.0.1/0.0.0.0/' /etc/mysql/mariadb.conf.d/50-server.cnf

## 3. MariaDB SQL 
sudo mariadb
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' IDENTIFIED BY 'letmein' WITH GRANT OPTION;
FLUSH PRIVILEGES;

## 4. Debugging 
- **Fout:** `Access denied for user 'admin'@'_gateway'`
- **Waarom:** Geen toestemming voor host toegang.
- **Oplossing:** Gebruiker defineren met `%` (wildcard) host.


## Labo 3 - Web Server Setup

### Belangrijke commando's Linux (Apache)

| Taak | Commando |
| :--- | :--- |
| De webserver status controleren | `sudo systemctl status apache2` |
| De webserver herstarten | `sudo systemctl restart apache2` |
| Een bestand bewerken met nano | `sudo nano [bestandsnaam]` |
| Rechten aanpassen (Permissions) | `sudo chmod 644 [bestandsnaam]` |
| Inhoud van een bestand tonen | `cat [bestandsnaam]` |
| De firewall uitschakelen | `sudo ufw disable` |
| IP-adres van de server opzoeken | `ip a` |

### Nano Editor Shortcuts
* **Opslaan:** `CTRL + O`
* **Afsluiten:** `CTRL + X`
