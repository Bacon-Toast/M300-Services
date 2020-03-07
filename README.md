# M300 Dokumentation
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



## Projekt Systemsicherheit
### Einleitung
In diesem Projekt geht es darum, dass wir unsere Umgebung mit Sicherheitsaspekten absichern. Dazu gehören Firewalls und Reverse Proxys. Wir werden das Vagrant File so abändern, dass beide Kompnente automatisch mitinstalliert werden.

#### Schritt 1 
Zum erstellten Ordner mit der VM vom letzten Projekt navigieren. Dort das Vagrantfile in Visual Studio Code öffnen.

#### Schritt 2 
Wir werden den Bereich config.vm.provison bearbeiten. Hier drin müssen folgende Zeilen eingefügt werden:

![](/Images/Sicherheit/Systemsec_config.JPG)


## Sicherheitsmassnahmen


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