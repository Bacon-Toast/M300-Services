# M300 Dokumentation Teil 1
## Linux
![Tux](https://upload.wikimedia.org/wikipedia/commons/a/af/Tux.png)
---
### Theorie
Linux ist ein Kernel, welcher für andere Betriebssystemen zu Verfügung gestellt wird. Man kann den Kernel erweitern und optimieren, weil das ganze Open Source ist.

Meistens wird man auf Linux mit der Konsole arbeiten müssen. Da ist es gut wenn man wichtige Befehle kennt:

* chmod --> Berechtigungen wechseln
* chgroup --> 		Gruppe wechseln
* chown	-->	Owner wechseln

* mkdir	-->	Erstellt ein Verzeichnis
* mkdir/home/X -->	Erstellt ein Verzeichnis unter dem Pfad X
* mkdir –p X --> 		Erstellt ganzer verzeichnisbaum X
* cd --> Wechselt in ein (Unter)Verzeichnis
* cd –L	-->	cd folgt der logischen Verzeichnisstruktur (Standard)
* cd –P	-->	cd folgt der physischen Verzeichnisstruktur

* touch	-->	Zugriffs- und Änderungs-Zeitstempel von Dateien ändern

Mit diesen Befehlen kann man in Linux arbeiten. Weitre Infos zu Befehlen sind unter [Ubuntu Users](https://ubuntuusers.de/) zu finden...

---

## Virtualisierung
### Geschichte
Der Begriff Virtualisierung gibt es schon länger als 40 Jahre. Die IBM stellte ein OS für virtuelle Maschinen vor. Die Virtualisierung ermöglicht es, dass man mehrere OS parallel auf einem Client ausführen kann. Man benötigt also nicht mehr 1 Client pro OS sondern kann dieses Problem mit virtuellen Maschinen lösen.  Die Virtualisierung ermöglicht eine effiziente Ausnützung von Leistung der benötigten Hardware und es können sehr viele Kosten an Hardware eingespart werden.

### Virtuelle Maschine
Eine Virtuelle Maschine (VM) ist nichts anderes als ein Computer, mit dem Unterschied, dass sie keine eigene Hardware besitzt. Sie bezieht alle Ressourcen von ihrem physischen Host. Für diesen Austausch ist der sogenannte Hypervisor zuständig.
Der Hypervisor auch Virtual Machine Monitor (VMM) genannt, ist ein Vermittler zwischen VM und Host. Der VMM ist eine Software, welche wichtige Elemente, wie Arbeitsspeicher, Prozessor Netzwerkverbindungen und so weiter, an die VMs vermittelt. 
Dies ermöglicht, dass eine virtuelle Maschine ein Betriebssystem, unabhängig vom installierten Host-Betriebssystem beheimaten kann. Das heisst, dass man ein Linux OS auf einem Windows Client mittels Vmware oder HyperV laufen lassen und nutzen kann.

### Hypervisor
Der Hypervisor auch Virtual Machine Monitor (VMM) genannt, ist ein Vermittler zwischen VM und Host. Der VMM ist eine Software, welche wichtige Elemente, wie Arbeitsspeicher, Prozessor Netzwerkverbindungen und so weiter, an die VMs vermittelt. Davon gibt es zwei Arten:

#### Hypervisor Typ1
Der Hypervisor Typ1 setzt gleich auf der Hardware auf. Er ist das OS wie zum Beispiel ESX von VMware. Auf ihm laufen die VMs und man kann sie dann mit einem Konfigurationstool managen.

![Hypervisor Typ1](https://upload.wikimedia.org/wikipedia/commons/5/53/VMM-Type1.JPG) 


#### Hypervisor Typ2
Beim Hypervisor Typ 2 lauft eine Applikation auf einem OS, welche für die VMs zuständig ist. Hier wäre die VMware Workstation gemeint. Man kann diese Applikation auf Windows installieren, und über die Applikation die VMs erstellen, konfigurieren, etc…

![Hypervisor Typ1](https://upload.wikimedia.org/wikipedia/commons/1/1a/VMM-Type2.JPG)




---

## Vagrant
Vagrant ist ein Programm, welches effizient Virtuelle Maschinene erstellen kann. Anhand von einem Vagrantfile lassen sich Konfigurationen an den VMs und Informationen für die Hypervisoren anpassen. Mit den Commands, kann man dann die VMs steuern (starten, herunterfahren, lsöchen usw..)

Mehr Informationen sind unter folgendem Link zu finde.[Vagrant](https://www.vagrantup.com/) 

Hier sind einige wichtige Befehle, welche man kennen sollte, wenn man Vagrant braucht:

> <"vagrant Init">  -->    #Erstellt VM

> <"vagrant up">    -->    #Startet VM

> <"vagrant ssh">   -->    #Verbindet sich per SSH zur VM

> <"vagrant status"> -->   #Zeigt Status der VM an

> <"vagrant port">  -->    #Zeigt weitergeleitete Ports der VM an

> <"vagrant halt">  -->    #stoppt die VM

> <"vagrant destroy"> -->  #Zerstört / löscht die VM

---

## Git 
Git wurde von Linus Torvalds entwickelt und ist ein Versionorientiertes Programm. Es ermöglicht mehreren Benutzern gleichzeitig, eine Datei zu bearbeiten, ohne dass man sich Probleme macht, indem man Elemente der Datei überschreibt.

![](/Images/git-concept.jpg) 

Dadurch ergeben sich am Repo für Bearbeiter folgende Möglichkeiten:

* Die eigene Arbeit kann einfach wieder in die zentrale Basis integriert werden.

* Es kann zeitgleich weiterentwickelt werden, z.B. jeder an verschiedenen Features.

* Die Versionierung verhindert, dass bereits getätigte Arbeiten verloren gehen bzw. überschrieben werden.

* Bei Bedarf kann zu früheren Versionen zurückgekehrt werden oder simultan an verschiedenen Versionen gearbeitet werden (auch "Branches" genannt).

Git bietet aber noch viel mehr, welche Eigenschaften es anderen Systemen überlegen macht kann


---

## Mark Down
Markdown ist eine vereinfachte aufzeichnungssprache. Das Ziel ist es ein Format zu erstellen, dass man es ohne konvertierung lesen kann. 2004 wurde es entworfen. Diese Dokumentation wurde mit Markdown geschrieben. Man kann Markdown auf jedem Texteditor nutzen. 

---

## Systemsicherheit
Die Systemsicherheit ist ein wichtiger Bestandteil in der Informarik. Dies gilt auch für meine Umgebung. Ich werde im folgenden auf die Firewall und den Reverse Proxy genauer eingehen.

### Firewall
Die Firewall trennt das Netzwerk von anderen Netzwerken und bestimmt die Kommunikationswege. Sie entscheidet, ob ein Paket aus dem Netzwerk oder in das Netzwerk kommen kann. Anhand der Source, Destination, Port und Protokoll kann sie das umsetzen.

Man kann der Firewall auch gewisse Regeln zuweisen. Hier kommt die Konfiguration ins Spiel. Falls ein Proxy in die Firewall eingebaut ist, kann man ein Paketfilter einbauen. Viele Firewalls haben auch einen Stateful Packet Inspection (SPI) integriert. Dies ist eine Dynamische Paketfilterung (Layer 3) nach Verbindungszustand. Sämtliche Pakete ohne Verbindung werden verworfen. 

Folgende Firewall Typen gibt es auch noch:
* Application Layer Firewall (ALF) Layer 7 – Firewall: Filterung nach Daten-Inhalt → Proxy

* Personal Firewall Software Firewall, welche auf dem Host lokal die Kommunikation nach Regeln zulässt oder nicht (z.B. Windows Firewall, Comodo Firewall, Avira, Kaspersky ect. )

### Reverse Proxy
Der Reverseproxy ist ein Proxy, welcher Resourcen für einen Client von einem Servern holt. Es handelt sich um eine Kommunikationsschnittstelle im Netzwerk, die Anfragen entgegennimmt und stellvertretend an einen Zielrechner weiterleitet.

Ein Reverse Proxy-Server wird als zusätzliche Sicherheitskomponente vor einen oder mehrere Webserver geschaltet, um Anfragen aus dem Internet stellvertretend entgegenzunehmen und an einen Backend-Server im Hintergrund weiterzuleiten.

![](/Images/Sicherheit/Reverse_Proxy.JPG) 

---

### Benutzer & Rechte
In Linux gibt es wie auch in Windows User und ihre Zugriffsrechte. Folgende Standartusers sind meistens zu finden:

![](/Images/Linux/users.JPG)

Sämtliche Benutzer sind in der Datei: ~/etc/passwd zu finden. Die Passwörter befinden sich in der Datei ~/etc/shadow.

Das Berechtigungskonzept hat eine Idee dahinter. Jede Berechtigung ist mit einer Zahl versehen.

![](/Images/Linux/berechtigungen.JPG)

Je nach dem wie dann die Berechtigungen erteilt werden addiert man die Nummern. Folgender Command ist zu gebrauchen:

> chmod XXX

x=Zahl aus Tabelle






---

## Projekt Vagrant
### Einleitung
In diesem Projekt geht es darum, eine Vagrant VM aufzusetzen. Die Vagrant VM wird dann auf das Vagrantfile zurückgreifen und sämtliche Konfigurationen auslesen, und diese dann auch so umsetzen.

### Umgebung
Folgende Umgebung gilt es aufzubauen:

![](/Images/Plan/Visio.JPG)



#### Schritt 1
Als erstes muss man den Ordner erstellen, in welchem man arbeiten möchte. Hier wird dann die Konsole geöffnet und gearbeitet. Wichtig ist, dass man immer auf dem selben Pfad arbeitet, sonst gibt es ein Durcheinander...

#### Schritt 2
Sobald man sich im richtigen Ordner befindet muss man die VM erstellen. Dies ist mit folgendem Befehl zu machen:
> vagrant init ubuntu/trusty64

Danach wird das Vagrantfile erstellt, auf welchem man alle Konfigurationen machen kann. Das File ist in fünf Punkten gegliedert:

* config.vm.box 
* config.vm.provider
* config.vm.network
* config.vm.synced_folder
* config.vm.provision

1) Der erste Punkt definiert das Betriebssystem.
2) Der zweite Punkt definiert den Provider (Virtualbox, VMware usw..)
3) Beim dritten Punkt können sämtliche Netzwerk Konfigurationen gemacht werden (IP Adresse setzen usw..)
4) Der vierte Punkt sagt aus, wie man auf die Files der VM vom Computer aus zugreifen möchte.
5) Der fünfte Punkt definiert, was man automatisiert aufsetzen möchte.

#### Schritt 3
Nach dem man die Konfigurationen vorgenommen hat, kann man die VM starten. Hierzu benötigt man folgenden Command:

> vagrant up

#### Schritt 4 
Nun ist die VM aktiv. Mit SSH kann man auf sie zugegriffen werden. Hierzu benötigt man den folgenden Befehl:

> vagrant ssh


Die VM ist nun bereit und man kann mit ihr arbeiten.

---
### Testprotokoll
| Testfall                      | Check          |
| --------                      | -------------- |
| SSH Zugriff                   | positiv        |
| Programme installiert ?       | positiv        |
| Berechtigungen stimmen?       | positiv        |
| User erfolgreich erstellt ?   | positiv        |
| Firewall rules stimmen?       | positiv        |


   ---



## Projekt Systemsicherheit
### Einleitung
In diesem Projekt geht es darum, dass wir unsere Umgebung mit Sicherheitsaspekten absichern. Dazu gehören Firewalls und Reverse Proxys. Wir werden das Vagrant File so abändern, dass beide Kompnente automatisch mitinstalliert werden.

#### Schritt 1 
Zum erstellten Ordner mit der VM vom letzten Projekt navigieren. Dort das Vagrantfile in Visual Studio Code öffnen.

#### Schritt 2 
Wir werden den Bereich config.vm.provison bearbeiten. Hier drin müssen folgende Zeilen eingefügt werden:

![](/Images/Sicherheit/Systemsec_config.JPG)


## Sicherheitsmassnahmen
Bei diesem Projekt habe ich mir folgende Sicherheitsmassnahmen überlegt:

* Berechtigungen für Usergruppen auf Ordner
* Firewall rules eingerichtet
* Reverse Proxy eingerichtet (Webserverschutz)
* Benutzer Schulung
* Netzwerkdokumentation immer nachführen


---

## Kreativität für LB2
Ich habe ein Template für die VMs eingerichtet, welches Dienste installiert. Dieses wird zentral in Gihtub gespeichert. Da können alle darauf zugreifen.

---


## Vergleich Vorwissen & Wissenszuwachs
Zu Beginn kannte ich Virtual Box und setzte damit auch VMs auf. Die Konfiguration dieser einzelnen VMs nehmen viel Zeit in Anspruch. Als dann Vagrant ins Spiel kam, erkannte ich wie viel Zeit man sparen jedoch kann.

Alles was ich bisher in meiner Ausbildung lernte dokumentierte ich auf Word. Es ist meine aller Erste Dokumentation, welche ich mit Markdown und Gitlab zusammen mache. Die Situation war neu für mich. Ich muss sagen, dass mir die Sprache sehr gefällt und dass ich mit beiden noch weiterarbeiten werde.

Vor diesem Modul hatte ich ein Raspberry Pi Modul, in welchem ich mich hart mit Linux befasste. Deshalb kannte ich bereits die Basics (Ordnerstruktur, Befehle usw...). Modul 300 gab mir einen guten Einblick in die Systemsicherheit (Firewall / Reverse proxy). Schliesslich habe ich noch nie damit auf Linux gearbeitet.

---

## Reflexion
Die Lernbeurteilung 2 war eine sehr gute Übung für mich. Ich habe sehr viel davon profitiert. Schliesslich habe ich noch nie in einer Github Umgebung gearbeitet. Ich konnte einige wichtige Basics zum Thema Infarstucture lernen. Die Zukunft in der Informatik besteht aus Automatisierung. Dieses Modul zeigt wie einfach man sich das Leben machen kann und wie viel Geld man sparen kann, wenn man diese Methoden in der Arbeitswelt einsetzt.
Zudem deckte es Themen wie Netzwerksicherheit und Virtualisierung. Diese beiden Themen haben auch eine sehr wichtige Bedeutung in Zukunft. 

---

# Modul 300 Dokumentation Teil 2
## Containerisierung
Bei der Containerisierung handelt es sich um eine Art Virtualisierung auf Anwendungsebene, bei der mehrere isolierte Maschinen auf einem einzelnen Kernel ausgeführt werden können. Diese Maschinen werden Container genannt.

Container bieten eine Standardmethode um Anwendungscode, Laufzeitumgebung, Systemwerkzeugen, Systembibliotheken und Konfigurationen in einer Maschine zusammenzufassen. Im Gegensatz zu VMS, die alle ihren eigenen "Kernel" haben, teilen sich Container einen Kernel (Betriebssystem), der auf der Hardware installiert ist.

Folgendes Bild zeigt den Unterschied zwischen Container und Virtuellen Maschinen:

![](/Images/Container/difference.JPG)

Die Vorteile der Containerisierung sind:

* Resourcenbedarf (weniger Resourcen als VMs)
  
* Effizient (Container nutzen Serverresourcen sehr dynamisch  aus )
  
* Performance (Container haben bringen mehr Leistung, als VMs, weil das Gastbetriebssystem auch seine eigenen Speicheranforderungen erfüllen und wertvollen Arbeitsspeicher des Hosts belegen muss)

---

## Docker
### Erklärung
![](https://upload.wikimedia.org/wikipedia/commons/4/4e/Docker_%28container_engine%29_logo.svg)

Docker ist eine Software zur Isolierung von Anwendungen mit Containervirtualisierung. Die Software benötigt keine Lizenzen.

Docker nahm damals die bestehende Linux-Containertechnologie auf und verpackte und erweiterte sie in vielerlei Hinsicht – vor allem durch portable Images und eine benutzerfreundliche Schnittstelle.

### Architektur
Im Folgenden sind alle Elemnte und ihre Aufgaben aufgelistet:

#### Docker Deamon 
* Erstellen, Ausführen und Überwachen der Container
* Bauen und Speichern von Images.

#### Docker Client

* Docker wird über die Kommandozeile (CLI) mittels des Docker Clients bedient
* Kommuniziert per HTTP REST mit dem Docker Daemon

#### Images
* Images sind gebuildete Umgebungen welche als Container gestartet werden können
* Images sind nicht veränderbar, sondern können nur neu gebuildet werden.
* Images bestehen aus Namen und Version (TAG), z.B. ubuntu:16.04. 

#### Container
* Container sind die ausgeführten Images
* Ein Image kann beliebig oft als Container ausgeführt werden
* Container bzw. deren Inhalte können verändert werden, dazu werden sogenannte Union File Systems verwendet, welche nur die Änderungen zum original Image speichern.

#### Docker Registry 
* In Docker Registries werden Images abgelegt und verteilt

## Microservices
Microservices sind ein Architekturkonzept der Anwendungsentwicklung. 
Ein Microservice ist also eine Kernfunktion einer Anwendung und er wird unabhängig von anderen Services ausgeführt. 

Jede Funktion kann unabhängig entwickelt und implementiert werden.

Folgende Grafik zeigt der Aufbau von Microservices auf:
![](/Images/Container/microservice.JPG)

## Docker Projekt Container
### Einleitung

In diesem Projekt geht es darum, Docker besser kennen zu lernen. Ich werde Container erstellen, diese Kombinieren und managen. Ausserdem werde ich noch mit Images Arbeiten.

### Umgebung
So wird meine Umgebung am Schluss des Moduls etwa aussehen:

![](/Images/Plan/Visio-docker.JPG)

### Docker download
Als Erstes geht es darum Docker zu installieren. Ich arbeite auf einer Ubuntu VM.

Hierzu habe ich die Anleitung von Docker [Docker Anleitung Download](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

Nach der Installation kann man die Funktionsfähigkeit von Docker mit dem folgenden Command testen:

> run 'Hello-world'

![](/Images/docker/holamundo.JPG)

Falls dieses Bild erscheint kann man mit den Container & Images fortfahren.

### Docker Container & Images
Ein Container beinhaltet Services, ohne dass man diese installieren. Das Konzept dahinter basiert auf Dockerfiles. Mit diesen kann man Images erstellen.

Images kann man auch von Dockerhub herunterladen. Jedoch muss man sich dort einlogen.

Ich werde im folgenden mit den Apache und mysql Images arbeiten.

Apache werde ich als Backend installieren und mysql als frontend.

![](/Images/docker/docker-container.JPG)

Mit folgenden Command lässt sich der Apache Container installieren: 

> docker container run -d -p 8081:80 --name MyApache httpd


> docker container run -it -p 8082:80 mysql 

Nun sind die Container installiert und laufen. Für den Test kann man im Browser: http://localhost:(port) eingeben. Wenn die Webserver ersichtlich sind dann hat es geklappt.

Beim erstellen eines Containers, für welches ein neues Image gebraucht wird, beziehungsweise ein Image benötigt wird, welches nicht lokal vorhanden ist, wird ein Pull Request von docker hub ausgeführt, damit es lokal downgeloaded ist.

![](/Images/docker/pull-image.JPG)

Hier sind noch weitere Docker commands:

Alle laufende Container anzeigen:
> docker ps

Alle Container anzeigen
> docker container ls -a

Alle Images anzeigen
> docker images

Image herunterladen
> pull (Imagename)

Image erstellen
> docker image build -t

Container stoppen
> docker container stop [ID]

den Container "betreten"
> docker container exec -it "containername" bash

## Image erstellen 
Man kann auch Images erstellen. Für das habe ich ein bestehendes Image genommen (nginx) und habe darauf meine Webseite gemacht. Das Image habe ich im Anschluss auf Dockerhub gepushed.

Als erstes erstellt man den Container mit dem Image und mapped den Ordner im Image drin, welchen man bearbeiten will in einen Ordner auf dem Hostsystem:
> docker container run -d -p 8080:80 nginx -v $(pwd):/usr/share/nginx/html --name nginx-website-m300 nginx

Ich habe mir einen Test Ordner erstellt, welchen ich gemappt habe. Im Command ist das "$(pwd)" zu finden, und das ist dafür da, dass dieser Ordner in dem man sich gerade befindet, gemeint ist. 

Im Testordner habe ich nun ein index.html file erstellt, welches das Original überschreibt. Diese Änderungen geschehen allem im Container.

![](/Images/docker/docker-testdir.JPG)

Hier kann man nun ein Image erstellen. Dies ist mit dem Docker File zu machen. Hierzu habe ich in der SELBEN Direcotory ein Dockerfile erstellt.

![](/Images/docker/docker-file.JPG)

Im Dockerfile habe ich definiert, mit welchem Image ich arbeite, wo meine Workdirectory ist und, dass das Image alle Inhalte von der Workdirectory in mein Image kopieren soll.

Als nächstes geht es darum, das Image zu "bauen". Dies macht man mit folgendem Command:
> docker image build -t seanm300/nginx-website-m300 . 

Docker image build -t würde das Image lokal abspeichern. Da ich es jedoch nachher noch auf mein Dockerhub pushen möchte habe ich noch mein Username von Dockerhub und den namen der Webseite festgelegt. Der Punkt am Schluss bezieht sich auf das Dokerfile in der Directory.

Nun ist das Image lokal verfügbar, und man kann bereits mit dem einen Container erstellen. Jedoch möchte ich, dass ich das von jedem Computer aus machen kann. Also pushe ich das noch von meinem Dockerhub Account.

Der Command dazu wäre:
> Docker push seanm300/nginx-website-m300

![](/Images/docker/push-docker-image.JPG)

Wichtig: Man muss sich natürlich zuerst noch authentifizieren. Hierzu einfach folgenden Command eingeben:
> Docker login

Danach kann man sich auf Dockerhub mit Username und Passwort einloggen.

![](/Images/docker/dockerhub.JPG)

## Testprotokoll
| Testfall                      | Check          |
| --------                      | -------------- |
| Container wird angezeigt      | positiv        |
| Webseite erreichbar           | positiv        |
| Applikation erreichbar        | positiv        |
| Ports sind nicht besetzt      | positiv        |
| Image funktioniert            | positiv        |
| Image Dockerhub erreichbar    | positiv        |


Als nächstes werde ich meine Container mit Sicherheitselementen beschmücken.

## Docker Projekt Sicherheit
Im letzten Projekt habe ich meine Container erstellt und verwaltet. Nun geht es darum diese Container abzusichern. Es ist wichtig, dass Logging und Mitteilungen aktiviert sind. Das System muss dem Administrator behilflich sein. Im Ernstfall müssen Warnungen gesendet werden.

### Meldungen an den Admin
Eine gute Monitoring-Lösung sollte auf einen Blick den Zustand des Systems zeigen und rechtzeitig warnen, wenn Ressourcen knapp werden.
Docker Tools cAdvisor von Google ist das am häufigsten eingesetzte Monitoring-Tool für Docker.

Dieses Programm ist als Container verfügbar und man kann darauf zugreifen. Der folgende Command muss dazu aktiviert werden:
>docker run -d --name cadvisor -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys:ro -v /var/lib/docker/:/var/lib/docker:ro -p 8080:8080 google/cadvisor:latest

### Weitere Sicherheitsaspekte
Ich habe folgende weitere Sicherheitsaspekte für meine Container realisiert:

#### Speicher
Wenn man den Speicher schützt, kann man die Chancen von DDos Attacken minimieren. Dies ist wichtig, da der Speicher nicht "aufgefressen" werden darf. Hier wäre der Command dazu:

> docker run -m 128m --memory-swap 128m amouat/stress stress --vm 1 --vm-bytes 127m -t 5s

![](/Images/docker/RAM-protection.JPG)

#### Neustarts begrenzen
Ein Neustart verhindert Zeitverluste und Ressorcenverluste von einem sterbenden Container. Auch hier kann eine DDos Attacke verhindert werden. Der Command dazu wäre:

> docker run -d --restart=on-failure:10 my-flaky-image

![](/Images/docker/Restart-protection.JPG)

#### Ressourcenbeschränken
Der Kernel definiert Ressourcenbeschränkungen, die für Prozesse gesetzt werden können. Diese lassen sich auch auf Docker-Container anwenden. Hierzu wäre der Command:

> docker run --ulimit cpu=12:14 amouat/stress stress --cpu 1

![](/Images/docker/Ressource-protection.JPG)

#### Capabilities einschränken 
Der Linux-Kernel definiert eine Reihe von Berechtigungen, welche Prozessen zugewiesen werden können, um ihnen einen erweiterten Zugriff auf das System zu gestatten.

Die Capabilities decken einen grossen Funktionsbereich ab, vom Ändern der Systemzeit bis hin zum Öffnen von Netzwerk-Sockets. Der Command dazu ist:

> docker run --cap-drop all --cap-add CHOWN ubuntu chown 100 /tmp
 
![](/Images/docker/Capabilities-protection.JPG)

## Docker Projekt Node & Mongo DB
Für mein letztes Projekt habe ich zwei Dockercontainer miteinander verbunden. Eine App erstellt eine Einkaufsliste. Die Elemente werden in einer Datenbank abgespeichert. Hierzu habe ich Node und Mongo DB verwendet.

## Wissenszuwachs
In den letzten Jahren habe ich stets mit VMs gearbeitet. Container waren mir nicht bekannt. Ich habe die Services immer installieren müssen und konfigurieren müssen. Mit Docker erspart man sich da viel Arbeit. 

Ich habe mit intensiv mit Docker befasst und viele nützliche Dinge kennengelernt, welche mir auf meinem weiteren Weg nützlich sein werden.

## Reflexion
In dieser zweiten Arbeit von diesem Modul habe ich einen guten Einblick in die Welt der Container erhalten. Ich weiss jetzt wie man mit Docker sehr schnell Services zum laufen bringt und diese auch verwalten kann. Ich habe sehr viel Freude an diesem Bereich erhalten und kann mir vorstellen in Zukunft damit zu arbeiten.