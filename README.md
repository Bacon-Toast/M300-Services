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

