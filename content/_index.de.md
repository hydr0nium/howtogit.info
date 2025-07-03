+++
title = "Wie funktioniert Git"
+++

# Wie funktionert Git

Du bist wahrscheinlich hier weil einer deiner Arbeitskollegen oder Freunde dir diese Seite geschickt hast, als du ihnen erzählt hast, dass du nichts über git weißt. Für dich und jeden anderen, der diese Seite gefunden hat, ist dies der richtige Platz.

### Was ist git? [🔗](https://howtogit.info/de/#was-ist-git-link)

Git ist was man eine Version-Kontroll-Software nennt. Am einfachsten ist es sich git als einen Weg zu speichern 'was' und 'wer' etwas mit einer Datei gemacht hat. Git ist in erster Linie eine Kommandozeilenanwendungen, kann aber auch oft in deinem lieblings Codeeditor oder IDE wie VSCode benutzt werden. Es ist wichtig zwischen GitHub, GitLab und git zu unterscheiden, da diese 3 verschiedene Dinge sind, obwohl sie ähnliche Namen haben.

### Was ist GitHub / GitLab? [🔗](https://howtogit.info/de/#was-ist-github-gitlab-link)

GitHub und GitLab sind Speicherorte im Internet für deine git verwalteten Dateien. Sie bieten einige erweiterte Funktionen zu git welche Leuten helfen besser zusammen zu arbeiten, wie 'pull requests' oder 'CI pipelines'.

### Was sind repositories? [🔗](https://howtogit.info/de/#was-sind-repositories-link)

Ein repository, kurz repo, (deutsch: Lagerstätte oder Behälter) ist kurz und knapp nur ein Ordner in welchem deine Dateien verarbeitet werden. Du kannst dir das ganze als eine Box vorstellen wo deine Dateien drin 'leben'. Ein repo hat immer einen .git Ordner in sich.

### Wie erstelle ich ein repo? [🔗](https://howtogit.info/de/#wie-erstelle-ich-ein-repo-link)

Es gibt zwei Wege um ein git repo zu erstellen. Entweder auf GitHub / GitLab oder lokal. In beiden Fällen musst du beide verknüfen, falls du den Dienst von GitHub / GitLab benutzen willst.

### Ein Repo auf GitHub erstellen [🔗](https://howtogit.info/de/#ein-repo-auf-github-erstellen-link)

Um ein repo auf GitHub zu erstellen klickst du auf das '+' oben rechts und dann 'New repository'. Danach stellt GitHub dir einige Fragen wie zum Beispiel den Namen des repos oder ob dies öffentlich erreichbar sein soll.

### Wie erstelle ich ein lokales Repo? [🔗](https://howtogit.info/de/#wie-erstelle-ich-ein-lokales-repo-link)

Um ein lokales Repo zu erstellen navigiere zuerst in den Ordner in dem du dein repo anlegen willst. Dann führe folgenden Befehl in der Kommandozeile aus:
```bash
git init .
```

### Wie lade ich ein repo von GitHub / GitLab herunter? [🔗](https://howtogit.info/de/#wie-lade-ich-ein-repo-von-github-gitlab-herunter-link)

Du kannst ein repo von GitHub oder Gitlab ganz einfache mit dem clone Kommando herunterladen. Dies verbindet automatische deine lokale 'Kopie' mit der auf GitHub / GitLab gespeicherten. Um den clone Befehl ausführen zu können benötigtst du eine repo URL. Diese findest du auf GitHub in dem jeweiligen Repo bei dem blauen Knopf 'Code'. Du kannst hier SHH oder HTTPS auswählen. Bedenke jedoch, dass SSH einen SSH-Schlüssel benötigt und HTTPS nur lesen und nicht schreiben kann. 
```bash
git clone https://github.com/someuser/somerepo.git # Läd ein repo herunter
```

### Wie verbinde ich mein lokales Repo mit dem Repo auf GitHub? [🔗](https://howtogit.info/de/#wie-verbinde-ich-mein-lokales-repo-mit-dem-repo-auf-github-link)

Wenn du ein zuerst ein lokales repo und danach ein repo auf GitHub erstellst musst du diese beiden verbinden. Dein GitHub / GitLab repo sollte dir genaue Anweisungen nach erstellen geben um dies zu tun. Falls du jedoch mehr Informationen benötigst kannst du [diesem](https://docs.github.com/en/get-started/git-basics/managing-remote-repositories-link) Link folgen.

### Wie benutze ich einen SSH Schlüssel? [🔗](https://howtogit.info/de/#wie-benutze-ich-einen-ssh-schlüssel-link)

Ein SSH Schlüssel ist eine Möglichkeit den Servern von GitHub oder GitLab zu beweisen wer du bist. Dies benutzt eine kryptographische Methode welche man asymmetrische Kryptographie bzw "Public-Key-Kryptographie" nennt. Du Benutzung der public keys (öffentliche Schlüssel) ist unterschiedlich auf jeder Seite und wird hier am Beispiel von GitHub erklärt.

Um den SSH Schlüssel zu erstellen musst du zuerst in deinen .ssh Ordner mit der Kommandozeile, navigieren. Falls dieser nicht existiert musst du ihn erstellen. Er befindet sich in Windows unter C:/Nutzer/deinNutzername/ und /home/deinNutzername unter Linux. Um den Schlüssel nun zu erstellen benutzt du folgenden Befehl:
```bash
ssh-keygen # Erstellen des ssh Schlüssel Paars
```
Der Befehl frägt dich nun noch einige Fragen. Die erste ist der Name des Schlüsselpaars. Gib einen Namen (ohne Endung) an und drücke Enter. Du kannst dem Schlüssel auch ein Passwort geben jedoch wir benutzen hier kein Passwort. Nun sollten sich zwei neue Dateien in dem .ssh Ordner befinden. meinschlüssel (Privater Schlüssel) und meinschlüssel.pub (Öffentlicher Schlüssel).


Öffne nun die .pub datei (hier: meinschlüssel.pub) und kopiere den Inhalt. Gehe nun auf GitHub, Einstellungen, SSH und GPG Schlüssel und erstelle einen neuen SSH Schlüssel. Kopiere den Inhalt in das Schlüsselfeld und gib dem Eintrag einen Namen. Danach erstelle den Eintrag. Dies sollte deinen öffentlichen Schlüssel zu GitHub hinzugefügt haben.


Als letztes müssen wir eine ssh config für GitHub erstellen. Hierzu erstellen wir wieder im .ssh Ordner die Datei 'config' (ohne Endung). Nun musst du folgenden Inhalt hinzufügen:
```bash
Host github.com
    HostName github.com
    User git
    IdentityFile pfad_zur_pub_datei
    IdentitiesOnly yes
```
Nun sollte alles für die SSH Authentifizierung bei GitHub fertig sein. Solltest du jedoch immer noch Hilfe brauchen findest du diese [hier](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

### Wie benutze ich git? [🔗](https://howtogit.info/de/#wie-benutze-ich-git-link)

Um git zu benutzen musst du als aller erstes ein Repo erstellen. Alles was von hier an folgt, erfolgt in dem erstellten Repo in der Kommandozeile, kann jedoch auch über etwaige git Schnittstellen in Texteditoren oder IDEs benutzer werden. Nachdem du das Repo erstellt hast wird jede Änderung an Dateien von git überwacht. Du kannst die Änderungen mit folgendem Befehl sehen:
```bash
git status # Zeigt die Änderungen im Repo an
```
Dies zeigt dir wie, von wem und welche Dateien geändert wurden. Um die Änderungen zu speichern musst du diese erst in den Staging (szs. Sammlung) Bereich überführen. Diese kann in zwei Wegen passieren:
```bash
git add pfad_datei1 pfad_datei2 pfad_datei3 # Das fügt alle angegebenen Dateien in den Staging Bereich ein.
```
oder 
```bash
git add . # Fügt alle Änderungen in den Staging Bereich ein
```
Nun da alle gewünschten Dateien im Staging Bereich sind müssen diese committed (szs. gebunden, festgeschrieben) werden. Committing bedeutet, dass die jeweiligen Änderung an den jetzigen [Branch](https://howtogit.info/de/#was-ist-ein-branch-link) (Zweig) hinzugefügt werden. Beim Erstellen eines Commits müss außerdem eine Commit Nachricht angegeben werden:
```bash
git commit -m "Das hier ist eine Commit Nachricht" # Commited die Änderungen zum jetztigen Branch
```

<mark> WICHTIG: Jeder mit Zugriff auf ein Repo kann ALLE commits, inklusive commit Nachricht sehen. </mark>
Jetzt können die Änderungen zum online Repo geschickt werden, sofern du eines hinzugefügt hast:
```bash
git push # Sendet die Änderung zum online Repo
```
Möglicherweise müsst du einige Konfigurationen zu deinem git hinzufügen bevor du 'pushen' kannst. Git benötigt standartmäßig einen Namen und eine Email. Für mehr Informationen zum setzen der Konfiguration siehe [diesen](todo) Absatz.


Falls du mit mehreren Menschen an einem Projekt arbeitest kann es passieren, dass einige von ihnen 'pushen' und dir somit Änderungen fehlen. Um die Änderungen mit deinem lokalen Repo zu synchronisieren benutzt du einen 'pull':
```bash
git pull # Läd die Änderungen vom online Repo herunter
```
Dies kann zu einem 'merge conflict' (szs. Zusammenfügungsfehler). Du kannst mehr über merge conflicts [hier](todo) finden.

Der empfohlene Ablauf mit git ist der folgende:
1. Lade die Änderungen mit 'pull' herunter
2. Füge Änderungen hinzu
3. Benutze 'add' und 'commit' um deine Änderungen regelmäßig zu speichern
4. Lade die Änderungen mit 'push' hoch
5. Löse merge conflict falls welche entstehen.

### Was ist eine Branch? [🔗](https://howtogit.info/de/#was-ist-ein-branch-link)

Ein Branch (bzw. Pfad oder Zweig) ist wie eine andere Zeitline für deine Dateien. Wenn du einen Branch erstellst wird deine aktuelle 'Zeitlinie' in zwei geteilt. Von diesem Zeitpunkt an kannst du wählen auf welchen der zwei Pfade du weiter arbeitest. Um einen neuen Branch zu erstellen benutzt du folgenden Befehl:
```bash
git checkout -b neuer_branch_name # Erstelle einen neuen Branch
```
Du kannst außerdem Branches, mit diesem Befehl, wechseln:
```bash
git branch # Listet alle lokalen Branches auf
git branch -r # Listet alle online Branches auf
git branch -a # Listet alle Branches online und lokal auf
```

Branches können außerdem gemerged (zusammengeführt) werden. Das Mergen von Branches kann etwas verwirrent wirken. Für mehr über das Mergen von Branches kannst du [hier](https://howtogit.info/de/#merging-branches-link) klicken.

### Merging Branches [🔗](https://howtogit.info/de/#merging-branches-link)

Wenn Branches gemerged (zusammengeführt) werden versucht git den bestmöglichen Weg um Konflikte automatisch zu lösen. Jedoch scheitert auch git manchmal und so muss von menschlicher Hand der Konflikt gelöst werden. Um zwei Branches zu mergen benutzt du diesen Befehl:
```bash
git merge ein_branch_name # Merged ein_branch_name in den jetztigen Branch
```

Das Mergen von Branches kann wie oben besprochen zu sogenannten 'Merge Konflikten' führen. Diese Merge Konflikte siehen wie folgt aus:
```
<<<<<<< HEAD
Ich hasse git.
=======
Ich liebe git.
>>>>>>> mein_super_branch
```
Dies zeigt dir die jetzige 'Änderung' (HEAD - 'Ich hasse git.') und was die zu mergende Änderung (mein_super_branch - "Ich liebe git.") ist. Um einen Merge Konflikt zu lösen wählst du dir einen der beiden Änderungen aus und entfernst die andere, sowie alle Konflikt Markierungen.
```
Ich liebe git.
```

Nachdem alle Merge Konflikte gelöst sind, musst du die Änderungen wieder adden, committen und pushen.


Viele Merge Konflikte von Hand zu bearbeiten wird schnell eine Aufgabe des Unmöglichen, somit ist das Benutzen von einer guten IDE oder eines Codeeditor bei so etwas empfohlen. Merge Konflikte sind ein großes Thema in git und dies ist nur die Spitze des Eisberges. Falls du mehr Hilfe mit merge conflicts benötigt empfiehlt es sich [die git Dokumentation](https://git-scm.com/book/ms/v2/Git-Branching-Basic-Branching-and-Merging#_basic_merge_conflicts) zu lesen.

### Git Konfigurieren [🔗](https://howtogit.info/de/#git-konfigurieren-link) 

Git kann konfiguriert werden um viele verschiedene Dinge zu machen. Du kannst zum Beispiel deine eigenen git commands hinzufügen. Du weitverbreiteste Konfigurations um welche Leute sich kümmern müssen, ist die der Konfiguration von Name und Email, da git diese zum benutzen eines online Repos benötigt. Um einen Namen und eine Email zu einem Repo hinzuzufügen, kannst du folgendes (im Repo) benutzen:
```bash
git config user.name "Mein Name" # Setzt einen Name für ein Repo
git config user.email "meine_email@howtogit.info" # Setzt eine Email für ein Repo
```
Du kannst dies auch global für alle lokalen Repos auf deinem System machen:
```bash
git config --global user.name "Mein Name" # Setzt den Namen für alle lokallen Repos
git config --global user.email "meine_email@howtogit.info" # Setzt eine Email für alle lokalen Repos
```
<mark> WICHTIG: JEder mit Zugriff auf ein Repo kann die konfigurierte Email und den Namen sehen. </mark>


Git kann außerdem noch viel viel mehr konfigurieren mit einer .gitconfig. Hier ist als Beispiel meine:
```bash
[init]
	defaultBranch = main
[status]
	short = false
[user]
	email = 37932436+hydr0nium@users.noreply.github.com 
	name = hydr0nium
[merge]
	tool = nvimdiff2
[push]
	autoSetupRemote = true
[mergetool]
	keepBackup = false
[gpg]
	mode = ssh
	format = ssh
[filter "lfs"]
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
	process = git-lfs filter-process
	required = true
```

### Ich habe mein repo kaputt gemacht, HILFE [🔗](https://howtogit.info/de/#ich-habe-mein-repo-kaputt-gemacht-hilfe-link)

Das gute an git ist, dass es sehr schwer ist ein Repo entgültig komplett, ohne Reparaturmöglichkeit, kaputt zu machen. Als aller erstes solltest du ein Backup, von dem was du noch hast, machen. Du willst nicht noch mehr kaputt machen. Falls du keine wichtigen Änderung gemacht hast, kannst du das Repo einfach neu clonen. Das setzt das Repo nochmal zum Stand der online war zurück. Mit dem Backup kannst du auch jetzt falls nötig alle Änderungen wieder zurück einfügen. Falls du mehr Erfahrung mit git hast, kannst du außerdem einen neuen Branch erstellen, die Änderungen dort machen und den Branch dann mergen. Dies sollte 99% deiner Probleme lösen. Falls du immer noch Probleme hast ist Google und StackExchange eine gute Möglichkeit, Lösungen für dein Problem zu finden.

### Ich habe sensible Daten gepushed ... [🔗](https://howtogit.info/de/#ich-habe-sensible-daten-gepushed-link)

Du hast also sensible Daten, wie Passwört, API Schlüssel, deine Adresse etc. gepushed? Das ist sehr schlecht, denn git macht es dir sehr schwer bestimmte Daten, bzw. Informationen in einem Repo zu löschen, ohne das andere Inhalte mit gelöscht werden. Falls du etwas gepushed hast, wie ein Passwort oder API Schlüssel solltest du diesen so schnell wie möglich ändern. Falls es jedoch Daten sind, die du nicht schnell ändern kannst, wie deine Adresse ist der beste Weg, das Repo zu löschen und ein neues zu erstellen. Die Daten (ohne .git) kannst du einfach herrüber kopieren (ohne, die sensiblen Daten). Das sollte einen neuen Commitverlauf erstellen. Es gibt noch mehr Möglichkeiten, welche jedoch gute git Kenntnisse erfordern. [StackOverflow - How to remove a commit from GitHub](https://stackoverflow.com/questions/448919/how-can-i-remove-a-commit-on-github)

### Pull Requests [🔗](https://howtogit.info/de/#pull-requests-link)

Pull requests hören sich ähnlich wie pullen an sind aber zwei verschiedene Dinge. Eine pull requests ist keine git, sondern eine GitHub / GitLab etc. Funktion. Wenn du eine öffentliches Repo besuchst kannst du dieses 'forken'. Das bedeutet du kopierst, das Repo sodass du daran arbeiten kannst wie als wenn es deines wäre. Du kannst nun Änderungen vornehmen und "fragen" ob diese in das Original Repo germerged werden. Dies erlaubt es einfach zusammen zu arbeiten und Funktionen zu öffentlichen Repos hinzuzufügen, solange diese vom Besitzer angenommen werden. Pull requests müssen jedoch nicht durch forks entstehen. Bei der Zusammenarbeit an großen Projekten kann es passieren, dass du immer ienen neuen Branch pro Funktion erstellst und dieser mit einer Pull Request gemerged werden muss.

<mark> Es ist allgemein eine gute Idee auf "Feature / Funktions Branches" zu arbeiten und diese, egal ob man pull requests benutzt oder nicht zu mergen. </mark>

### Mehr Informationen [🔗](https://howtogit.info/de/#mehr-information-link)

Für mehr Informationen über das Thema, kannst du dir diese Quellen anschauen:

- [Git Documentation](https://git-scm.com/docs)
- [Git Book (Online/Free)](https://git-scm.com/book/en/v2)
- [GitHub Documentation](https://docs.github.com/en)
- [GitLab Documentation](https://docs.gitlab.com)

### Über mich & Mitwirken [🔗](https://howtogit.info/de/#über-mich-mitwirken-link)

Falls dir gefällt was du hier liest dann schau dir doch meinen anderen Kram auf [GitHub](https://github.com/hydr0nium) oder [Mastodon](https://infosec.exchange/@hydr0nium) an.

Falls du der Seite mehr zugänglich machen willst, kannst du helfen und diese mit Übersetzungen füllen. Um das zu tun gehe auf das [GitHub Repo](https://github.com/hydr0nium/howtogit.info), forke es und übersetze die _index.md im content Ordner. Du kannst dir eine Beispiel an den anderen Dateien dort nehmen wie zum Beispiel _index.de.md. Ich bin mir sicher du findest heraus wie es geht :)
