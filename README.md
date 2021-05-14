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

## Vagrant: Sinn und Zweck
Vagrant ist sehr gut geeignet, um schnell und unkompliziert Testumgebungen aufzubauen und, falls der Zweck erfüllt ist, diese auch wieder genau so schnell und unkompliziert zu löschen. In diesem Tutorial wirst Du ein **generelles Verständnis über die Funktionsweise von Vagrant** erhalten und auch schon die ersten "Hands-on"-Übungen durchführen. Falls Du nicht weiter weisst, hilft Dir **[Vagrant-Docs][20]** in allen Belangen weiter. Sämtliche Kommandos sind mit passenden Erklärungen versehen und für Anfänger und auch Fortgeschrittene eine sehr gute Quelle.


## Das folgende Dokument ist wie folgt strukturiert:
1. Der **ersten Abschnitt** **[Vagrant](#vagrant)** ist als Einstieg gedacht. Wir installieren einen Apache-Webserver und besprechen anschliessend die wichtigsten Vagrant-Kommandos. Nach Abschluss dieses Kapitels sollten Dir die gängigsten Vagrant-Befehle vertraut sein, und Du hast erfolgreich eine erste Vagrantbox aufgesetzt und zum Laufen gebracht  

2. Im **zweiten Abschnitt** **[NGINX-Webserver deklarativ aufsetzen](#nginx-webserver-deklarativ-aufsetzen)** setzen wir Schritt für Schritt einen NGINX-Webserver auf - und zwar so, dass diese Umgebung jederzeit gelöscht und wieder erstellt werden kann. Auch auf einer anderen Umgebung. Der Webseitencontent wird somit persistiert und es kann auch nach einem "Destroy" und einer Neuinstallation wieder auf diese Daten zurückgegriffen werden


---


## Preflight Checks ##
#### Commands 
Bevor wir loslegen checken wir, ob Vagrant, Virtualbox und SSH installiert ist.

> `$ vagrant -v ` _Checken, welche Vagrant-Version installiert ist_<br>
> `$ vboxmanage -v  ` _checken, welche Virtualbox-Version installiert ist_ <br>
> `$ ssh  ` _Checken, ob SSH installiert ist_ <br>

...kann in der GitBash ausgeführt werden (siehe folgendes Bild). Es spielt in diesem Fall noch keine Rolle, in welchem Verzeichnis man sich befindet. 

  ![Screenshot](images/01_vagrant-vb-ssh.jpg)

Falls das Kommando "vagrant" unter Windows nicht funktioniert, muss allenfalls noch die PATH-Variable angepasst werden (siehe folgendes Bild). Dasselbe gilt auch für "vboxmanage" (Virtualbox)

  ![Screenshot](images/02_Systemvariable-f-vagrant.jpg)


Mit folgenden Schritten das Verzeichnis für die erste mit Vagrant erstellte Ubuntu-VM vorbereiten

> `$ cd <Projekt-Mutterverzeichnis> ` _ins Mutterverzeichnis des vorgesehenen Projektes wechseln_<br>
> `$ pwd  ` _kontrolle, ob im richtigen Verzeichnis_ <br>
> `$ mkdir ubuntu  ` _Projektverzeichnis "ubuntu" anlegen_ 
> `$ cd ubuntu  ` _in's Verzeichnis wechseln_

Screenshot (Gitbash auf Windows)

  ![Screenshot](images/03_gitbash_ubuntu-verz_erstellen.png)


Mit folgendem Kommando wird im aktuellen Verzeichnis ein Vagrantfile erstellt:

```
$ vagrant init hashicorp/precise32
```
Screenshot (Gitbash auf Windows)
  ![Screenshot](images/11_gitbash_ubuntu-vagrantfile-erst.png)

> `$ ls -ali ` _überprüfen ob vorhanden_<br>

  ![Screenshot](images/11b_gitbash_ubuntu-vagrantfile-erst.png)

Config-file checken
> `$ vim Vagrantfile ` _Inhalt anschauen_<br>

  ![Screenshot](images/12_gitbash_ubuntu-vagrantfile-inhalt.png)
<br>


VM überprüfen
> `$ vagrant ssh ` _in die Ubuntu-VM "hüpfen"_<br>
> `$ uname -a  ` _Checken, ob Ubuntu_ <br>
> `$ df -h  ` _Diskfree Human-readable_ <br>

  ![Screenshot](images/13_gitbash_ubuntu-vm-mit Vagrant_inst.png)
<br>




# Viel Spass und viel Erfolg
- - -
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/3.0/ch/88x31.png" /></a><br />Dieses Werk ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/">Creative Commons Namensnennung - Nicht-kommerziell - Weitergabe unter gleichen Bedingungen 3.0 Schweiz Lizenz</a>

- - -

- Autor: Marcello Calisto
- Mail: marcello.calisto@tbz.ch
