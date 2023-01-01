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

## Verknüpfe Git und Github über ssh
Über das Terminal gehe in das Verzeichnis deines neu angelegten Projektes, falls du dich nicht bereits darin befinden solltest. 
Für die Verknüpfung benötigst du ein ssh-keypair. Der öffentliche Key muss auf Github auf deinem Account hinterlegt sein. Falls sich noch kein ssh-keypair auf dem lokalen Rechner befindet, richte es ein und lege den Key in deinem Github.com-Account an. 

### Check ssh-keypair

#### Prüfe, ob ein ssh-keypair bereits angelegt ist. 
Gib in das Terminal folgende Aufforderung ein, um dir eine Liste mit vorhandenen Keys anzeigen zu lassen:

`ls -al ~/.ssh`

Prüfe, ob in der Ausgabe folgende mögliche öffentliche Keys vorhanden sind:

* id_rsa.pub
* id_ecdsa.pub
* id_ed25519.pub

> Achtung: Für die Öffentlichkeit sind stets nur die öffentlichen Keys mit der Endung .pub vorgesehen! Keys ohne Endung sind der private Key und müssen geheim gehalten werden.

#### Falls kein ssh-keypair vorhanden ist, generiere ein ssh-keypair

> Achtung: Bereits vorhandene keypairs werden überschrieben! Falls der öffentliche Key für eine Zugangsberechtigung hinterlegt ist, ist der Zugang per ssh nicht mehr möglich! Daher **immer erst prüfen**, pb ein ssh-keypair vorhanden ist, bevor man ein ssh-keypair generiert.

Gib in das Terminal folgende Aufforderung ein, um ein ssh-keypair zu erzeugen. Mit der Flag -C ergänzt du ein Comment als Label für deinen Key. In diesem Fall nutze die Email-Adresse, die mit deinem Github-Account verknüpft ist. Die Flag -t steht für type, also den Algorhytmus, mit dem das keypair erzeugt wird. 

`ssh-keygen -t ed25519 -C "<email-address>"`

>Falls der Ed25519-Algorhytmus auf dem lokalen System nicht zur Verfügung steht und eine Fehlermeldung ausgegeben wird, nutze RSA. Die Flag -b steht für bits:

>`ssh-keygen -t rsa -b 4096 -C "<email-address>"`

#### Hinterlege den öffentlichen ssh-key bei Github.com
Todo: Beschreibung 

#### Teste die Verbindung via ssh mit Github.com
Todo: Beschreibung

### Verbinde Git und Github via ssh

Verknüpfe jetzt dein lokales Git mit Github.com als remote repository:

`git remote add origin <ssh-verzeichnis github>`

Prüfe jetzt gern einmal den status deines lokalen repositorys:

`git status`