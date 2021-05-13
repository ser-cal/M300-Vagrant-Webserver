[10]: https://github.com
[20]: https://www.vagrantup.com/docs


# M300 Webserver mit Vagrant aufsetzen und einrichten

Ziel dieses Projektes (Tutorials) ist es, dass die Lernenden in das Thema **GIT** einsteigen können und beim Durcharbeiten gleichzeitig ein Repository mit einer Grundstruktur für das Modul 300 aufsetzen<br>

## Voraussetzungen:
- [Vagrant](https://www.vagrantup.com/) installiert
- [Virtualbox](https://www.virtualbox.org/wiki/Downloads) und Extension Pack (gleiche Version) installiert <br>_(Es kann auch ein anderer Provider wie z.B. VMware benutzt werden - Default ist Virtualbox)_
- [Github](https://github.com/) Account
- Windows: [GitBash](https://git-scm.com/downloads) auf dem lokalen Host installiert
- Mac oder Linux: (Bash bereits vorhanden, sonst ebenfalls auf [GitBash](https://git-scm.com/downloads)) verfügbar
- Editor: z.B: [Visual Studio Code](https://code.visualstudio.com/) , [Atom](https://atom.io/) oder [Sublime Text](https://www.sublimetext.com/) etc...

## Das folgende Dokument ist wie folgt strukturiert:
1. Der **ersten Abschnitt** **[Vagrant](#vagrant)** ist als Einstieg gedacht. Wir installieren einen Apache-Webserver und besprechen anschliessend die wichtigsten Vagrant-Kommandos. Nach Abschluss dieses Kapitels sollten Dir die gängigsten Vagrant-Befehle vertraut sein, und Du hast erfolgreich eine erste Vagrantbox aufgesetzt und zum Laufen gebracht  

2. Im **zweiten Abschnitt** **[NGINX-Webserver deklarativ aufsetzen](#nginx-webserver-deklarativ-aufsetzen)** setzen wir Schritt für Schritt einen NGINX-Webserver auf - und zwar so, dass diese Umgebung jederzeit gelöscht und wieder erstellt werden kann. Auch auf einer anderen Umgebung. Der Webseitencontent wird somit persistiert und es kann auch nach einem "Destroy" und einer Neuinstallation wieder auf diese Daten zurückgegriffen werden


Vagrant ist sehr gut geeignet, um schnell und unkompliziert Testumgebungen aufzubauen und, falls der Zweck erfüllt ist, diese auch wieder genau so schnell und unkompliziert zu löschen. In diesem Tutorial wirst Du ein **generelles Verständnis über die Funktionsweise von Vagrant** erhalten und auch schon die ersten "Hands-on"-Übungen durchführen. Falls Du nicht weiter weisst, hilft Dir **[Vagrant-Docs][20]** in allen Belangen weiter. Sämtliche Kommandos sind mit passenden Erklärungen versehen und für Anfänger und auch Fortgeschrittene eine sehr gute Quelle.

---


## Vagrant ##
#### Commands 
Bevor wir loslegen checken wir, ob Vagrant, Virtualbox und SSH installiert ist.

> `$ vagrant -v ` _Checken, welche Vagrant-Version installiert ist_<br>
> `$ vboxmanage -v  ` _checken, welche Virtualbox-Version installiert ist_ <br>
> `$ ssh  ` _Checken, ob SSH installiert ist_ <br>

...kann in der GitBash ausgeführt werden (siehe folgendes Bild). Es spielt in diesem Fall noch keine Rolle, in welchem Verzeichnis man sich befindet. 

  ![Commands](images/01_vagrant-vb-ssh.png)

Falls das Kommando "vagrant" unter Windows nicht funktioniert, muss allenfalls noch die PATH-Variable angepasst werden (siehe folgendes Bild). Dasselbe gilt auch für "vboxmanage" (Virtualbox)

  ![Variablen](images/01_Was-ist-GIT.jpg)


gehh








# Viel Spass und viel Erfolg
- - -
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/3.0/ch/88x31.png" /></a><br />Dieses Werk ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/">Creative Commons Namensnennung - Nicht-kommerziell - Weitergabe unter gleichen Bedingungen 3.0 Schweiz Lizenz</a>

- - -

- Autor: Marcello Calisto
- Mail: marcello.calisto@tbz.ch