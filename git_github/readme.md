Änderung remote

# Git und Github für Python-Project "Projektname" einrichten
## Verzeichnis anlegen
Lege im Terminal einen Ordner für das Projekt an und wechsle in das Verzeichnis.

`mkdir <Projektname>`

`cd <Projektname>`

## Installiere Git und richte es ein

### Installation

Falls Git nicht installiert ist, muss es zuerst installiert und eingerichtet werden.

Prüfe, ob Git installiert ist:

`which git`

Dies sollte als Ausgabe folgendes liefern:

/usr/bin/git

Gegebenenfalls prüfe die Version:

`git --version`

Du solltest etwas in der Art als Asugabe erhalten:

git version 2.34.1

Falls du keine Ausgaben erhältst, ist git nicht installiert. Installiere Git über den apt-Packetmanager:

`sudo apt install git -y`

### Einrichtung

#### Username und Email-adresse

Hinterlege deinen Usernamen deine Emailadresse, die du auch auf Github benutzt.

`git config --global user.name "<username>"`

`git config --global user.email "<email-address>"`

### Lege als defaultBranch 'main' fest

Der Name des Branches, welchen Git per default vergibt ist 'master'. Github verwendet als defaultBranch 'main'. Um Konflikte und unnötige Merges zu vermeiden, lege den defaultBranch als 'main' für Git fest:

`git config --global init.defaultBranch main`

Deine Änderungen werden in .gitconfig gespeichert. Du kannst dir die Datei im Terminal aúsgeben lassen:

`cat ~/.gitconfig`

Du solltest eine solche Ausgabe erhalten:

```
# This is Git's per-user configuration file.
[user]
    email = <email-address>
    name = <username>
# Please adapt and uncomment the following lines:
#    email = <email-address>
#    name = <username>
[init]
	defaultBranch = main
```

Damit ist die grundlegende Einrichtung abgeschlossen.

## Initiiere Git

`git init`

## Lege ein Repository in Github an 
Gehe auf deinen Account bei Github.com und lege ein Repository mit dem Namen "Projektname" an. Während des Prozesses füge ein Readme und ein .gitignore für Python hinzu.
Wenn das Repository angelegt ist, kopiere dir das Verzeichnis, indem du über den Button Code das SSH-Verzeichnis in die Zwischenablage kopierst.  

## Verknüpfe Git und Github
Über das Terminal gehe in das Verzeichnis deines neu angelegten Projektes, falls du dich nicht bereits darin befinden solltest. 

