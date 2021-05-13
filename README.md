[10]: https://github.com
[20]: https://git-scm.com/
[21]: https://git-scm.com/book/en/v2


# M300 Webserver mit Vagrant aufsetzen und einrichten

Ziel dieses Projektes (Tutorials) ist es, dass die Lernenden in das Thema **GIT** einsteigen können und beim Durcharbeiten gleichzeitig ein Repository mit einer Grundstruktur für das Modul 300 aufsetzen<br>

## Voraussetzungen:
- [Github](https://github.com/) Account
- Windows: [GitBash](https://git-scm.com/downloads) auf dem lokalen Host installiert
- Mac oder Linux: (Bash bereits vorhanden, sonst ebenfalls auf [GitBash](https://git-scm.com/downloads)) verfügbar
- Editor: z.B: [Visual Studio Code](https://code.visualstudio.com/) , [Atom](https://atom.io/) oder [Sublime Text](https://www.sublimetext.com/) etc...

## Das folgende Dokument ist wie folgt strukturiert:
1. Der **ersten Abschnitt** **[Vagrant](#vagrant)** ist als Einstieg gedacht. Wir gehen kurz auf die Installation und die Dependencies ein und besprechen anschliessend die wichtigsten Vagrant-Kommandos. Nach Abschluss dieses Kapitels sollte Vagrant funktionstüchtig sein und Du kennst die wichtigsten Befehle, um damit zu arbeiten.  

2. Im **zweiten Abschnitt** **[NGINX-Webserver deklarativ aufsetzen](#nginx-webserver-deklarativ-aufsetzen)** setzen wir Schritt für Schritt einen NGINX-Webserver auf - und zwar so, dass diese Umgebung jederzeit gelöscht und wieder erstellt werden kann. Auch auf einer anderen Umgebung. 


Git ist sehr umfangreich. Für den täglichen Gebrauch reichen aber wenige Kommandos und ein **generelles Verständnis über die Funktionsweise von Git**. Diese sind im **[Pro Git book][21]** (Kapitel 1 und 2) sehr gut beschrieben.  Alle in diesem Dokument verwendeten Kommandos finden sie ebefalls in diesen beiden Kapiteln wieder.

---


## Vagrantfile ##
