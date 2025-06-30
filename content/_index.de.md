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

Es gibt zwei Wege um ein git repo zu erstellen. Entweder auf GitHub / GitLab oder lokal. In beiden Fällen musst du beiden verknüfen, falls du den Dienste von GitHub / GitLab benutzen willst.

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
git clone https://github.com/someuser/somerepo.git
```

### Wie verbinde ich mein lokales Repo mit dem Repo auf GitHub? [🔗](https://howtogit.info/de/#wie-verbinde-ich-mein-lokales-repo-mit-dem-repo-auf-github-link)

Wenn du ein zuerst ein lokales repo und danach ein repo auf GitHub erstellst musst du diese beiden verbinden. Dein GitHub / GitLab repo sollte dir genaue Anweisungen nach erstellen geben um dies zu tun. Falls du jedoch mehr Informationen benötigst kannst du [diesem](https://docs.github.com/en/get-started/git-basics/managing-remote-repositories-link) Link folgen.


