# Readme
<!--letztes Update: 21-Dez-19-->
Erstellt Websiten & \LaTeX PDFs mit Markdown und Pandoc.

Sed passt die \LaTeX-Syntax an.

Versionsverwaltung: Git

## Hinweis

Projekt getestet unter Ubuntu 18.04.2 LTS.

## Projekt erstellen

Das Script "THEMA-umbenennen.sh" sucht und ersetzt THEMA.

ACHTUNG: Script außerhalb vom Projektordner ausführen.

~~~
  # Github Repository downloaden
  REPOSITORY="dummy-notizenUbuntu-v03"
  ADRESSE="https://github.com/ju1-eu"
  git clone $ADRESSE/$REPOSITORY.git 

  # Script anpassen
  vi THEMA-umbenennen.sh
    # file: THEMA - Suchen und Ersetzen
  ./THEMA-umbenennen.sh

  +++ Erste Schritte +++
  $ cd neue-Notiz/
  # files anpassen
  scripte/sed.sh
    - codelanguage:    HTML5, Python, Bash, C, C++, TeX
    - CMS Server Pfad: https://www.ju1.eu/#
    - Bildformat:      pdf, svg, png, jpg

  projekt.sh
    - Backupverzeichnis

  content/metadata.tex
    - Datum, Titel, Autor

  $ ./projekt.sh
    # Projekt erstellen"
~~~

## Software


Pandoc: <https://pandoc.org/installing.html>

LaTeX: <https://www.tug.org/texlive/acquire-netinstall.html>

Editor:

<https://code.visualstudio.com/download>

<https://atom.io/>

Git: <https://git-scm.com/downloads>

~~~
    # Shell $
    lsb_release -a
      # Ubuntu 18.04.3 LTS - Codename: bionic
    pandoc -v
      # pandoc 1.19.2.4
    tex -v
      # TeX 3.14159265 (TeX Live 2017/Debian)
    git --version
      # git version 2.17.1
~~~

kdiff3: <http://kdiff3.sourceforge.net/>

Imagemagick: <https://www.imagemagick.org/script/download.php#windows>


## Repository von Github downloaden

<https://github.com/ju1-eu>

**Repository Name** = dummy-notizenUbuntu-v03

~~~
  # Shell $

  # Github Repository downloaden
  REPOSITORY="dummy-notizenUbuntu-v03"
  ADRESSE="git@github.com:ju1-eu"
  git clone $ADRESSE/$REPOSITORY.git 

  # Backup Repository clonen
  repos_HD="/media/jan/virtuell/repos/notizenUbuntu"
  REPOSITORY="dummy-notizenUbuntu-v03"
  git clone $repos_HD/$REPOSITORY.git 

  repos_USB="/media/jan/usb/repos/notizenUbuntu"    
  REPOSITORY="dummy-notizenUbuntu-v03"
  git clone $repos_USB/$REPOSITORY.git 

  repos_RPI4="smb://rpi4.local/nas/repos/notizenUbuntu" 
  REPOSITORY="dummy-notizenUbuntu-v03"
  git clone $repos_RPI4/$REPOSITORY.git 
~~~

## Neues Repository auf Github anlegen

<https://github.com/ju1-eu>

**Repository Name** = dummy-notizenUbuntu-v03

~~~
  # lokales Repository: HEAD -> master
  git init # rm -rf .git
  git add .
  git commit -m"Projekt init"

  # Github Repository: origin/master
      # anpassen    
  REPOSITORY="dummy-notizenUbuntu-v03"
  ADRESSE="git@github.com:ju1-eu"
  git remote add origin $ADRESSE/$REPOSITORY.git
  git push --set-upstream origin master

  # backup Repository: backupUSB/master
      # anpassen
  repos_USB="/media/jan/usb/repos/notizenUbuntu"    
  REPOSITORY="dummy-notizenUbuntu-v03"
  LESEZEICHEN="backupUSB"
  git clone --no-hardlinks --bare . $repos_USB/$REPOSITORY.git 
  git remote add $LESEZEICHEN $repos_USB/$REPOSITORY.git 
  git push --all $LESEZEICHEN

  # backup Repository: backupRPI4/master
      # anpassen
  repos_RPI4="smb://rpi4/nas/repos/notizenUbuntu" 
  REPOSITORY="dummy-notizenUbuntu-v03"
  LESEZEICHEN="backupRPI4"
  git clone --no-hardlinks --bare . $repos_RPI4/$REPOSITORY.git 
  git remote add $LESEZEICHEN $repos_RPI4/$REPOSITORY.git 
  git push --all $LESEZEICHEN

  # Backup Repository: backupHD/master
  repos_HD="/media/jan/virtuell/repos/notizenUbuntu"
  REPOSITORY="dummy-notizenUbuntu-v03"
  LESEZEICHEN="backupHD"
  git clone --no-hardlinks --bare . $repos_HD/$REPOSITORY.git 
  git remote add $LESEZEICHEN $repos_HD/$REPOSITORY.git 
  git push --all $LESEZEICHEN
~~~

Git Befehle

~~~
  # Shell $
  #
  # ".gitconfig", ".gitignore" erstellen und konfigurieren
  #
  # git versionieren
  git add .
  git commit -a # Editorauswahl: sudo update-alternatives --config editor
  git status
  git log --graph --oneline 
  git lg > git.log

  # Github Repository
  git pull
  git push

  # Backup Repository
  git remote -v
  git push --all backupHD # sichern
  git push --all backupUSB
  git push --all backupRPI4

  # Branch erstellen
  git checkout -b feature/a1
  git checkout feature/a1
  # projekt bearbeiten
  git checkout master
  git merge feature/a1

  git status
  git log
  git lg
  git log --graph --oneline # beenden q
  git log --graph --pretty=format:";  %cn;  %h;  %ad;  %s" --date=relative > git.log
~~~

## Markdown Dokumente - Notizen verfassen

Markdown Dokumente / Notizen im Ordner "md/neu.md" erstellen.

~~~
  # Markdown
  <!--ju - Letztes Update: 6-Apr-19  -->

  # Überschrift
  ## Überschrift 2
  ### Überschrift 3

  ## Bild

  Bilder in pdf speichern, empfehlenswert für \LaTeX.

  ![Logo](images/bildname-001.pdf)

  ![Bild](https://cdn.pixabay.com/photo/2019/04/02/04/32/masala-4096891_960_720.jpg)

  ## Tabelle

  |**Nr.**|**Begriffe**|**Erklärung**|
  |------:|:-----------|:------------|
  | 1     | a1         | a2		       |
  | 2     | b1         | b2		       |
  | 3     | c1         | c2		       |
~~~

**Erste Schritte**

scripteBash "projekt.sh", "scripteBash/sed.sh" u. content/metadata.tex anpassen.

~~~
  # Shell $
  cd neue-Notiz
    # scripteBash anpassen

  vi scripteBash/sed.sh
    # codelanguage: HTML5, Python, Bash, C, C++, TeX
    # CMS Server Pfad: https://www.ju1.eu/*
    #  Bildformat: pdf -> \LaTeX; svg, png, jpg -> web

  vi projekt.sh
      #------------------------------------------------------
      # anpassen
      THEMA="dummy-notizenUbuntu-v03"

      backup_USB="/media/jan/usb/backup/notizenUbuntu"    
      #backup_RPI4="smb://rpi4.local/nas/backup/notizenUbuntu" 
      backup_HD="/media/jan/virtuell/backup/notizenUbuntu"

      archiv_USB="/media/jan/usb/archiv/notizenUbuntu"    
      #archiv_RPI4="smb://rpi4.local/nas/archiv/notizenUbuntu" 
      archiv_HD="/media/jan/virtuell/archiv/notizenUbuntu"

      repos_USB="/media/jan/usb/repos/notizenUbuntu"    
      #repos_RPI4="smb://rpi4.local/nas/repos/notizenUbuntu" 
      repos_HD="/media/jan/virtuell/repos/notizenUbuntu"
      #------------------------------------------------------

  vi content/metadata.tex
    # Datum, Titel, Autor
~~~

**Script ausfuehren**

~~~
  # Shell $
  cd neue-Notiz
  ./projekt.sh

  Projekt: Web & \LaTeX Dokumente erstellen unter Ubuntu

  1) Markdown in (tex, html5) - sed (Suchen/Ersetzen)
  2) Kopie tex (Pandoc) - tex (Handarbeit)
  3) Kapitel erstellen, Scripte ausführen
  4) Beamer
  5) TEST: Artikel-PDFs erstellen mit latexmk (x_*.pdf)
  6) PDFs erstellen (book-, print-, artikel.pdf) - Archiv (tex)
  7) Projekt aufräumen
  8) Git-Version erstellen
  9) git status und git log --graph --oneline
 10) git init
 11) Fotos optimieren (Web, Latex)
 12) book-pdf-Version erstellen
 13) Backup (archiv/*.zip & *.tar.gz) & (/media/jan/virtuell/backup)
 14) www
 15) Beenden?

 Eingabe Zahl >_
~~~

## Bilder optimieren

**JPG Bilder** in den Ordner "img-in/" kopieren.

optimiert Fotos für das Web und die PDF Datei.

## Backup

~~~
  # Shell $
  cd neue-Notiz
  tar cvzf ../neue-Notiz.tar.gz .
~~~

# Schnellstart
<!--update: 20-12-19-->
**Befehle**

- Git: download <https://git-scm.com/download/win>
- GitHub: Projekt anlegen <https://github.com/ju1-eu/>
- pwd 
- git clone "Repository_name"
- code "file" 
- git add "file" oder git add .git remote rm 
- git status
- git log oder git lg
- git stash
- git reset 

## Git konfigurieren

~~~
  # Git konfigurieren
  #----------------------
  git version

  # gitconfig anpassen
  git config --global user.name "jan_lap"
  git config --global user.email "esel573@gmail.com"
  
  # gitconfig ansehen
  git config --global --list
    .gitconfig
    .gitattributes
    .gitignore
~~~

## Projekt mit GitHub einrichten

Auf GitHub ein Repository erstellen: <https://github.com/ju1-eu/>

- **Repository_name**: "prj-dummy"  
- **Clone with HTTPS**: https://github.com/ju1-eu/prj-dummy.git
- weiter mit "Projekt von GitHub downloaden"
- oder
- weiter mit "Projekt lokal einrichten"

## Projekt von GitHub downloaden

~~~
  pwd

  $THEMA="prj-dummy"
  rm $THEMA -Recurse -Force
  git clone https://github.com/ju1-eu/$THEMA.git
  #git clone https://github.com/ju1-eu/$THEMA.git prj1

  # weiter mit ...
  # Git Workflow / PROJEKT bearbeiten
~~~

## Projekt lokal einrichten

~~~
  pwd 

  # lokales Repository: master
  $THEMA="prj-dummy" # Repository_name auf Github erstellen
  #rm $THEMA -Recurse -Force
  mkdir $THEMA
  cd $THEMA
  # Repository anlegen
  git init # rm -rf .git oder rm .git -Recurse -Force
  echo "# prj-dummy" > README.md 
  git add .
  git commit -m"init"
  git status
  git remote add origin https://github.com/ju1-eu/$THEMA.git
  git push --set-upstream origin master

  # weiter mit ...
  # Git Workflow / PROJEKT bearbeiten
~~~

## Git Workflow


### Arbeitsverzeichnis 
~~~
  pwd
    # /c/daten/projekte/git/git-kurs/prj
    # C:\daten\projekte\git\git-kurs\prj
~~~

### PROJEKT bearbeiten

~~~
  git status

  # README.md erstellen
  echo "# prj-dummy" > README.md 
  echo "<!-- update: 20-Dez-19 -->" >> README.md
  cat README.md
  
  # .gitignore erstellen
  echo "# ju update: 20-Dez-19 .gitignore" > .gitignore
  echo "!.gitignore" >> .gitignore
  cat .gitignore
~~~

### git add - Arbeitsverzeichnis  => Stagingbereich 

~~~
  git add .
  git add README.md
~~~

### git commit - Stagingbereich => Repository

~~~
  git commit -m"projekt init"
  git commit
  git commit -a
~~~

### git push - Repository => Github Repository

~~~
  # Voraussetzung
  $THEMA="prj-dummy" # Repository_name auf Github erstellen
  git remote add origin https://github.com/ju1-eu/$THEMA.git
  git push --set-upstream origin master

  git status
  git push
  git pull
~~~

### git status - sauberes Arbeitsverzeichnis prüfen!

~~~
  git status
    On branch master
    Your branch is up to date with 'origin/master'.

    nothing to commit, working tree clean
~~~

##  git log - history

~~~
  git status
  git log
  git log --abbrev-commit --pretty=oneline --graph
  git lg
~~~

## Branch neu erstellen - PROJEKT bearbeiten

~~~
  # sauberes Arbeitsverzeichnis prüfen!
  git checkout master
  git status
  # wenn lokale Änderungen vorliegen, wird der Merge abgebrochen
  git pull --ff-only

  git branch
  # Branch neu erstellen
  git checkout -b feature/a1
  # Feature-Branch zentral sichern
  git push --set-upstream origin feature/a1
  # Änderungen können zukünftig gesichert werden
  git push

  # PROJEKT bearbeiten
  code README.md
  git add .
  git commit
  
  # Branch wechseln
  git status 
  git branch
  git checkout master

  # Branch zusammenführen
  git merge feature/a1

  git branch
  # nutzlosen Branch löschen
  git push -d origin feature/a1
  git branch -d feature/a1
 
  # sauberes Arbeitsverzeichnis prüfen!
  git status
~~~

## git tag - Version erstellen

~~~
  # sauberes Arbeitsverzeichnis prüfen!
  git status

  git tag
  git tag -a v1.0
    # stabile Version

  git checkout v1.0
  git checkout master
~~~

## git blame - Wer hat was und wann geändert?

~~~
  git blame README.md
~~~

## Datei umbenennen o. löschen - .git löschen

~~~
  git mv file_alt file_neu
  git commit -am"Datei umbenannt"
  git rm file_neu
  git commit -am"Datei gelöscht"
  git status

  # .git löschen
  rm -rf .git 
  rm .git -Recurse -Force
~~~

## Versionskonflikt lösen

~~~
  # sauberes Arbeitsverzeichnis prüfen!
  git status

  git branch -a

  # Voraussetzung: Branch muss vorhanden sein
  # siehe Branch neu erstellen
  git checkout feature/a1

  # PROJEKT bearbeiten auf feature/a1 Branch
  code README.md
    # file: README.md bearbeiten
  git commit -am"README.md bearbeitet"
  git push
  git diff master feature/a1

  git checkout master

  # PROJEKT bearbeiten auf master Branch
  code README.md
    # file: README.md bearbeiten
  git commit -am"README.md bearbeitet master"
  git push
  git status

  # zusammenführen mit master-Branch 
  git merge feature/a1
    # Fehler, weil auf unterschiedlichen Branches gearbeitet wurde
    #----------------------
    Auto-merging README.md
    CONFLICT (content): Merge conflict in README.md
    Automatic merge failed; fix conflicts and then commit the result.
    #----------------------
  # Konflikt bearbeiten
  code README.md
    # file bereinigen: <<<<<<<, ======= und >>>>>>>
  
  git commit -am"Konflikt behoben"
  git push
  
  git branch -a
  git push -d origin feature/a1
  git branch -d feature/a1

  # sauberes Arbeitsverzeichnis prüfen!
  git status
~~~

## Lokales Wiederherstellen

~~~
  # Änderungen zwischenspeichern
  git stash --include-untracked
  # Letzte gespeicherte Änderungen zurückholen
  git stash pop
~~~


~~~
  pwd

  # PROJEKT bearbeiten
  echo "neu" > file.txt
  git add .
  git commit -m"neu" 
  echo "Fehler" >> file.txt
  # Achtung: noch kein git commit!
  git status

  # Möglichkeit 1
  git log
  cat .\file.txt
  git checkout HEAD file.txt
  cat .\file.txt
  git status

  # Möglichkeit 2
  git log
  cat .\file.txt
  git reset --hard HEAD
  cat .\file.txt
  git status
~~~

## Repository Wiederherstellen 

~~~
  pwd

  # PROJEKT bearbeiten
  echo "Fehler 2" >> file.txt
  git commit -am"Fehler provoziert" 
  # Achtung: noch kein git push!
  git status

  # Möglichkeit 1
  git log
  git reset --hard d446456
  git log
  git status

  # Möglichkeit 2
  git log
  git revert c3b6fab
  git log
  git status

  git push
  git status
~~~

## Git Backup - Repository ohne einen Workspace

Backup auf USB-Stick

~~~
  pwd

  # backup Repository: backup_wlap/master
    # anpassen
  $PFAD="E:/backup-Repos/notizenWin10"
  $THEMA="prj-dummy"
  $REPO="backup_wlap"

  #cd $THEMA
  git clone --no-hardlinks --bare . $PFAD/$THEMA.git 
  git remote add $REPO $PFAD/$THEMA.git 
  # gelegentlich sichern
  git status
  git push --all $REPO

  # löschen
  rm -rf $PFAD/$THEMA
  rm $PFAD/$THEMA -Recurse -Force
~~~

Backup auf Raspberry Pi

~~~
  pwd

  # backup Repository: backup_rpi4/master
    # anpassen
  $PFAD="\\RPI4\usbstick\backup-Repos\notizenWin10"
  $THEMA="prj-dummy"
  $REPO="backup_rpi4"

  #cd $THEMA
  git clone --no-hardlinks --bare . $PFAD/$THEMA.git 
  git remote add $REPO $PFAD/$THEMA.git 
  # gelegentlich sichern
  git status
  git push --all $REPO

  # löschen
  rm -rf $PFAD/$THEMA
  rm $PFAD/$THEMA -Recurse -Force
~~~

## lokales Repository clonen

~~~
  pwd
  cd C:\daten\projekte\git\git-kurs\prj

  # löschen
  rm -rf $THEMA
  rm $THEMA -Recurse -Force

  $PFAD="E:/backup-Repos/notizenWin10"
  $THEMA="prj-dummy"
  $REPO="backup_wlap"

  git clone $PFAD/$THEMA.git
  cd $THEMA
    
  # oder

  $PFAD="\\RPI4\usbstick\backup-Repos\notizenWin10"
  $THEMA="prj-dummy"
  $REPO="backup_rpi4"
  git clone $PFAD/$THEMA.git 
  cd $THEMA
~~~

# Git Workflow - Bereiche

- Datei bearbeiten
- Datei hinzufügen
- Datei Umbenennen
- Datei löschen

~~~
                     Lokal                             Remote Server 
  <----------------------------------------------->|<---------------->
  Arbeitsverzeichnis | Stagingbereich | Repository | Github Repository
      bearbeiten
                  git add
                  git mv
                  git rm                       
                                  git commit
                                                git push
  <----------------------------------------------->|<---------------->         
~~~


# Wiederherstellen

## Ordner für Experimente erstellen - löschen

~~~
  # Shell $
  cd projekt
  mkdir -p repoWork repoNeu repoAlt
  # löschen
  rm -rf repoWork repoNeu repoAlt
~~~

## bestehendes Repository clonen

~~~
  cd neue-Notiz # ? Repository
  git clone . ../repoWork
~~~

## Arbeitsverzeichnis bearbeiten

**File bearbeiten 1**

~~~
  # Shell $
  cd repoWork
  vi test.md
    # file
    Basis

  # git versionieren
  git add .
  git commit -a
  git status
~~~

**File bearbeiten 2**

~~~
  # Shell $
  vi test.md
    # file
    Basis
    2) Version

  # git versionieren
  git commit -a
  git status
~~~

**File bearbeiten 3**

~~~
  # Shell $
  vi test.md
    # file
    Basis
    2) Version
    3) Version

  # git versionieren
  git commit -a
  git status
  git log --graph --oneline
~~~

##  Wiederherstellen: Repository in ein temp. Verzeichnis klonen

~~~
  # Shell $
  cd repoWork
  git clone . ../repoNeu
  git clone . ../repoAlt
~~~

## Wechsel auf den gewünschten Git-Branch

~~~
  # Shell $
  cd ../repoNeu/
  git stash
  git log --graph --oneline
  * 85f27a3 (HEAD -> master) version 3
  * 22355e7 Vesion 2
  * 23e67c4 Version 1
  * 5c1d6a7 (origin/master, origin/HEAD) aufgeräumt
  * 138684a prj
  * 2af6ca2 Projekt init
  # version2
  git reset --hard 22355e7
~~~

## Verschiebe .git in den Workspace der alten Versionsverwaltung

~~~
  # Shell $
  git archive master | tar -x -C ../repoAlt/
~~~

## Ergebnis prüfen

~~~
  # Shell $
  cd projekt
  kdiff3 repoAlt/ repoNeu/Repository 
~~~

# Repository Versionen vergleichen

## Ordner für Experimente erstellen - löschen

~~~
  # Shell $
  cd projekt
  mkdir -p vers_Lokal vers_Github vers_backupHD vers_backupUSB vers_backupRPI4
  # löschen
  rm -rf vers_Lokal vers_Github vers_backupHD vers_backupUSB vers_backupRPI4
~~~

## lokales Repository

~~~
  # Shell $
  # repository clonen
  cd repoWork
  VERZ="vers_Lokal"
  git clone . ../$VERZ

  # build - Versionen erstellen
  VERZ="vers_Lokal"
  #tar cvzf ../$VERZ.tgz .
  ID=$(git rev-parse --short HEAD) # git commit (hashwert)
  timestamp=$(date +"%d%m%y") # Datum: 260619
  # 260619_Verz_v0b61478.tgz
  archiv=$timestamp'_'$VERZ'_v'$ID
  tar cvzf ../$archiv.tgz .
  cd ..
~~~

## Github Repository

origin/master

~~~
  # Shell $
  # Github repository clonen
  REPOSITORY="dummy-notizenUbuntu-v03"
  ADRESSE="https://github.com/ju1-eu"
  cd $REPOSITORY
  git clone $ADRESSE/$REPOSITORY.git .
    # oder
  REPOSITORY="dummy-notizenUbuntu-v03"
  ADRESSE="git@github.com:ju1-eu"
  cd $REPOSITORY
  git clone $ADRESSE/$REPOSITORY.git .

  # build - Versionen erstellen
  VERZ="vers_Github"
  #tar cvzf ../$VERZ.tgz .
  ID=$(git rev-parse --short HEAD) # git commit (hashwert)
  timestamp=$(date +"%d%m%y") # Datum: 260619
  # 260619_Verz_v0b61478.tgz
  archiv=$timestamp'_'$VERZ'_v'$ID
  tar cvzf ../$archiv.tgz .
  cd ..
~~~


## Backup Repository

~~~
  # Shell $
  # Backup Repository: backupHD/master
  HD="/media/jan/virtuell/repos/notizenUbuntu"
  REPOSITORY="dummy-notizenUbuntu-v03"
  LESEZEICHEN="backupHD"
  git clone --no-hardlinks --bare . $HD/$REPOSITORY.git 
  git remote add $LESEZEICHEN $HD/$REPOSITORY.git 
  git push --all $LESEZEICHEN

  # build - Versionen erstellen
  VERZ="vers_backupHD"
  #tar cvzf ../$VERZ.tgz .
  ID=$(git rev-parse --short HEAD) # git commit (hashwert)
  timestamp=$(date +"%d%m%y") # Datum: 260619
  # 260619_Verz_v0b61478.tgz
  archiv=$timestamp'_'$VERZ'_v'$ID
  tar cvzf ../$archiv.tgz .
  cd ..

  # backup Repository: backupUSB/master
      # anpassen
  USB="E:/repos/notizenUbuntu"
  REPOSITORY="dummy-notizenUbuntu-v03"
  LESEZEICHEN="backupUSB"
  git clone --no-hardlinks --bare . $USB/$REPOSITORY.git 
  git remote add $LESEZEICHEN $USB/$REPOSITORY.git 
  git push --all $LESEZEICHEN

  # build - Versionen erstellen
  VERZ="vers_backupUSB"
  #tar cvzf ../$VERZ.tgz .
  ID=$(git rev-parse --short HEAD) # git commit (hashwert)
  timestamp=$(date +"%d%m%y") # Datum: 260619
  # 260619_Verz_v0b61478.tgz
  archiv=$timestamp'_'$VERZ'_v'$ID
  tar cvzf ../$archiv.tgz .
  cd ..

  # backup Repository: backupRPI4/master
      # anpassen
  RPI4="\\RPI4\nas\repos\notizenUbuntu"
  REPOSITORY="dummy-notizenUbuntu-v03"
  LESEZEICHEN="backupRPI4"
  git clone --no-hardlinks --bare . $RPI4/$REPOSITORY.git 
  git remote add $LESEZEICHEN $RPI4/$REPOSITORY.git 
  git push --all $LESEZEICHEN

  # build - Versionen erstellen
  VERZ="vers_backupRPI4"
  #tar cvzf ../$VERZ.tgz .
  ID=$(git rev-parse --short HEAD) # git commit (hashwert)
  timestamp=$(date +"%d%m%y") # Datum: 260619
  # 260619_Verz_v0b61478.tgz
  archiv=$timestamp'_'$VERZ'_v'$ID
  tar cvzf ../$archiv.tgz .
  cd ..
~~~


## Ergebnis prüfen

~~~
  # Shell $
  cd projekt
  # Verzeichnisse vergleichen
  # vers_Lokal vers_Github vers_backupHD vers_backupUSB vers_backupRPI4
  kdiff3 vers_Lokal/ vers_Github/ 
  kdiff3 vers_Lokal/ vers_backupHD
  kdiff3 vers_backupHD vers_backupUSB vers_backupRPI4
  # files vergleichen
  kdiff3 vers_Lokal/Readme.md vers_Github/Readme.md
~~~


## Projekt Inhalt

~~~
  # Shell $
  cd projekt
  ls -lh *gz
    # Inhalt
    260619_vers_Github_v5c1d6a7.tgz
    260619_vers_Lokal_v5c1d6a7.tgz
~~~

## build - Versionen erstellen

~~~
  # Shell $
  file="MD5-Hash.txt"
  printf "# --------------------------------\n"               >  $file
  printf "# build - Versionen\n"                              >> $file
  printf "# MD5-Hash:  Datum_Verzeichnis_vGit-Hashwert.tgz\n" >> $file
  printf "# --------------------------------\n\n"             >> $file

  # hashwert erstellen
  md5sum  260619_vers_Github_v5c1d6a7.tgz  >> $file
  md5sum  260619_vers_Lokal_v5c1d6a7.tgz   >> $file

  # build - Versionen
  vi MD5-Hash.txt
~~~
