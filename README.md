# Dokumentation M347

---

# Inhalt

- [Dokumentation M347](#dokumentation-m347)
- [Inhalt](#inhalt)
- [Handlungsziele](#handlungsziele)
- [Basics](#basics)
- [Erste Schritte](#erste-schritte)
  - [Installation](#installation)
  - [Erstellung eines Dockers](#erstellung-eines-dockers)
- [Visual Code mit Docker Extension](#visual-code-mit-docker-extension)
  - [Terminal Befehle](#terminal-befehle)
  - [Anpassung im Visual Studio Code](#anpassung-im-visual-studio-code)
- [Let's begin with Docker](#lets-begin-with-docker)
  - [Grundwissen](#grundwissen)
  - [Commandos](#commandos)

---

# Handlungsziele

> o Identifiziert Auswirkungen von Virtualisierung auf den beruflichen Alltag.
>
> o Wählt eine geeignete Containerkomposition (Architektur) situationsbezogen aus.
>
> o Wählt geeignete Containerdienstleister gemäss Anforderungen aus.
>
> o Virtualisiert eine Applikation mit der gewählten Containerkomposition sowohl zu Entwicklungszwecken als auch für Auslieferung/Betrieb.
>
> o Plant Methoden zur Qualitätskontrolle und setzt diese um.

---

# Basics

---

# Erste Schritte

## Installation

Mit dem Folgendem Befehl kann man schauen ob man Docker installiert hat und ob man schon welche habt:
![[Pasted image 20230403104012.png]]

Und falls man keinen Docker Installiert habt kann man die Folgenden Befehle in die Commandozeile einfügen:

```
sudo su

apt update

apt install apt-transport-https ca-certificates curl gpg

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \ gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 \ signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \ https://download.docker.com/linux/ubuntu \ $(lsb_release -cs) stable" > \ /etc/apt/sources.list.d/docker.list

apt update

apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

und wenn man nun einen User Hinzufügen will, kann man wie im folgendem eispiel dies machen:

```
usermod -aG docker vmadmin
```

## Erstellung eines Dockers

Mit dem nächsten Befehl erstellen wir nun einen hello-World Docker.

```
docker run hello-world:latest
```

---

# Visual Code mit Docker Extension

## Terminal Befehle

1. Download the key:

```
curl -L https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /usr/share/keyrings/microsoft-archive-keyring.gpg >/dev/null
```

2. Hinzufügen des MS Repository:

```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft-archive-keyring.gpg] https://packages.microsoft.com/repos/vscode stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
```

3. Updaten & Installieren:

```
apt update apt install code
```

## Anpassung im Visual Studio Code

1. Installation von Docker Extetion in VS Code:
   ![[Pasted image 20230403111818.png]]
2. Danach kann man dies auch im Visual Studio Code Benutzen. Für weiter Informationen kann man bei [https://code.visualstudio.com/docs/containers/overview](https://code.visualstudio.com/docs/containers/overview) sich hineinlesen.

---

# Let's begin with Docker

## Grundwissen

> Um die Grundbefehle durchzuführen, wurde im diesem beispiel  das Basisimage ubuntu:latest verwendet.

## Commandos

1. Image Herunterladen

Aufbau = Basisbefehl + Basismage

```
docker pull ubuntu:latest
```

2. Images anzeigen

```
docker images
```

![[Pasted image 20230403113255.png]]

Man verwendet diesen Befehl meistens wenn man die Images, die man besitzt anzeigen möchte.

3. Container Starten

Aufbau = Basisbefehl + Spezifitzierung

Example:

```
docker run -it --name my-ubuntu-container ubuntu:latest
```

| Cmmando      | Bedeutung                                   |
| ------------ | ------------------------------------------- |
| -lt          |  interaktiv                                 |
| docker ps -a | Überprüfen, welche Container gestartet sind |
| docker start | Starten des Conteiner                       |

3. Container stoppen

```
docker stop my-ubuntu-container
```

Dies ist ein Beispiel, wie man einen laufenden Docker stoppen kann.

4. Container löschen

```
docker rm my-ubuntu-container
```

Dieses Beispielbefehl löscht mittels `rm ` den Docker.

5. Image löschen

```
docker rmi ubuntu:latest
```

Der Schlüsselwort bei diesem Beispiel ist `rmi`.

6. Image Namen setzen
   Um den Image namen zu setzen muss man verstehen, dass dies aus den folgenden Befehlsstruktur besteht:

```
source/imagename:tag
```

| Commando  | Bedeutung                                                                                |
| --------- | ---------------------------------------------------------------------------------------- |
| source    | gibt den Namen der Organisatio (oder Person) an, die das Image erstellt hat, z.B. docker |
| imagename | Name des Images                                                                          |
| tag       | Versionsnummer                                                                           |
