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
1. Im **ersten Abschnitt** **[Vagrant Einsteig](#vagrant-einstieg)** machen wir uns einwenig mit "Vagrant" vertraut. Wir installieren mit einem ersten einfachen deklarativen Script (Vagrantfile) eine Ubuntu-VM und setzen dabei gleich die ersten Vagrant-Kommandos "Hands-on" ein. Nach Abschluss dieses Kapitels sollten Dir die gängigsten Vagrant-Befehle vertraut sein, und Du hast erfolgreich eine erste Vagrantbox aufgesetzt, zum Laufen gebracht und wieder "zerstört" (gelöscht)

2. Im **zweiten Abschnitt** **[NGINX-Webserver deklarativ aufsetzen](#nginx-webserver-deklarativ-aufsetzen)** geht bereits ein erstes Mal zur Sache. Wir setzen Schritt für Schritt einen NGINX-Webserver auf - und zwar so, dass diese Umgebung jederzeit gelöscht und in kürzester Zeit wieder erstellt werden kann. Auch auf einer anderen Umgebung. Der Webseitencontent wird somit persistiert und es kann auch nach einem "Destroy" und einer Neuinstallation wieder auf den früher erstellten Content zugegriffen werden. 


---

## Vagrant Einstieg

### Preflight Checks

Bevor wir loslegen zuerst checken, ob Vagrant, Virtualbox und SSH installiert ist. Wir verwenden hier die "Gitbash" auf Windows. Es spielt im Moment noch keine Rolle, in welchem Verzeichnis wir uns befinden. 

> `$ vagrant -v ` _Checken, welche Vagrant-Version installiert ist_<br>
> `$ vboxmanage -v  ` _checken, welche Virtualbox-Version installiert ist_ <br>
> `$ ssh  ` _Checken, ob SSH installiert ist_<br>
  ![Screenshot](images/01_vagrant-vb-ssh.jpg) 


### PATH-Variable auf Host (Windows) anpassen + ergänzen (nur bei Bedarf)
Falls das Kommando "vagrant" unter Windows nicht funktioniert, muss allenfalls noch die PATH-Variable angepasst werden (siehe folgendes Bild). Dasselbe gilt auch für "vboxmanage" (Virtualbox)
  ![Screenshot](images/02_Systemvariable-f-vagrant.jpg)

### Setup erstes Projekt (Ubuntu-VM)
Mit folgenden Schritten das Verzeichnis für die erste mit Vagrant erstellte Ubuntu-VM vorbereiten

> `$ cd <Projekt-Mutterverzeichnis> ` _ins Mutterverzeichnis des vorgesehenen Projektes wechseln_<br>
> `$ pwd  ` _kontrolle, ob im richtigen Verzeichnis_ <br>
> `$ mkdir ubuntu  ` _Projektverzeichnis "ubuntu" anlegen_ <br> 
> `$ cd ubuntu  ` _in's Verzeichnis "ubuntu" wechseln_
  ![Screenshot](images/03_gitbash_ubuntu-verz_erstellen.png)


Im aktuellen Verzeichnis ein Vagrantfile (für das OS Ubuntu Precise32) erstellen:
> `$ vagrant init hashicorp/precise32 ` <br>
  ![Screenshot](images/11_gitbash_ubuntu-vagrantfile-erst.png)

Überprüfen ob das Vagrantfile vorhanden ist:
> `$ ls -ali `
  ![Screenshot](images/11b_gitbash_ubuntu-vagrantfile-erst.png)

Config-file mit Editor öffnen und ckecken
> `$ vim Vagrantfile ` _Inhalt anschauen_<br>
  ![Screenshot](images/12_gitbash_ubuntu-vagrantfile-inhalt.png)
<br>

### VM starten und überprüfen
Wenn soweit alles ok ist, können wir die VM wie folgt zum ersten Mal starten 
> `$ vagrant up ` _Virtualbox-VM mit Vagrant starten_<br>
  ![Screenshot](images/13_gitbash_ubuntu-vm-mit-Vagrant_inst.png)
<br>

In VM "hüpfen" und überprüfen
> `$ vagrant ssh ` _in die Ubuntu-VM "hüpfen"_<br>
> `$ uname -a  ` _Checken, ob Distro stimmt --> Ubuntu_ <br>
> `$ df -h ` _Diskfree Human-readable_ <br>
  ![Screenshot](images/14_gitbash_mit_ssh_auf_Ubuntu-VM.png)

VM vom Host aus überprüfen
> `$ exit ` _aus der VM zurück auf den Host_<br>
> `$ vboxmanage list runningvms  ` _checken, welche Virtualbox-VMs am Laufen sind_ <br>
  ![Screenshot](images/15_gitbash_Virtualbox_Ubuntu-VM.png)


### Erste Änderungen im Vagrantfile vornehmen
Standardmässig werden die Virtualbox-VMs „headless“ gestartet. Das heisst „ohne GUI" - nur mit der Kommandozeile. Man kann nun aber das Vagrantfile (Configfile) so anpassen, dass das GUI beim nächsten "` vagrant up `" gestartet
> `$ less Vangrantfile ` _schauen, wo das GUI auskommentiert ist_<br>
  ![Screenshot](images/16a_gitbash_Vagrantfile_anpassen.png)
> `$ vi Vangrantfile ` _entsprechende Zeilen auskommentieren_<br>
  ![Screenshot](images/16b_gitbash_Vagrantfile_anpassen.png)
<br>

Um die getätigten Änderungen im Vagrantfile zu aktivieren, muss dieses neu durchlaufen werden. Das kann mit einem der folgenden zwei Vorgehensweisen erfolgen 
> 1. `$ vagrant halt ` danach `$ vagrant up ` _Virtualbox-VM mit Vagrant stoppen und danach starten_<br>
> 2. `$ vagrant reload ` _Virtualbox-VM mit Vagrant quasi "rebooten"_<br>
  ![Screenshot](images/17_gitbash_reboot_mit_fenster.png)
<br>

Wenn das Virtualbox-Fenster erscheint, hier noch ein "Hint", wie man aus dem "Maus und Tastatur gefangen"-Modus (nächstes Bild) kommt ...

```
1. "Pfeil nach unten"-Taste gleichzeitig mit 
2. "Pfeil nach rechts"-Taste drücken
3.  Erst wenn die ersten beiden Tasten gedrückt sind, die 
	"Ctrl“-Taste drücken (alle drei Tasten zusammen)
```
  ![Screenshot](images/18_Maustaste_gefangen_loesen.png)


# Viel Spass und viel Erfolg
- - -
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/3.0/ch/88x31.png" /></a><br />Dieses Werk ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/">Creative Commons Namensnennung - Nicht-kommerziell - Weitergabe unter gleichen Bedingungen 3.0 Schweiz Lizenz</a>

- - -

- Autor: Marcello Calisto
- Mail: marcello.calisto@tbz.ch
