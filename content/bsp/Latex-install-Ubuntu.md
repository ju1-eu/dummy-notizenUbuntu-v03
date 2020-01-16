# Latex install unter Ubuntu
<!--letztes Update: 16-Jan-20-->
Quelle: Dr. Uwe Ziegenhagen - Anleitung zur TEX Live Installation

## TEX Live download

Download: <http://mirror.ctan.org/systems/texlive/tlnet>

~~~
  cd Downloads
  tar xvfz install-tl-unx.tar.gz
  cd install-tl-20200114
  perl install-tl
  perl install-tl -gui
~~~

## TeX Version

~~~
  tex --version
~~~

## TEX Live Installation

~~~
  sudo apt install texlive texlive-latex-recommended texlive-fonts-recommended texlive-latex-base texlive-base texlive-latex-extra texlive-lang-german

  # Verbesserte Schriftarten bei T1-Kodierung
  sudo apt-get install cm-super 
~~~

## Umgebungsvariablen für Unix

~~~
  vi ~/.profile
    # Datei 
    PATH=/usr/local/texlive/2019/bin/x86_64-linux:$PATH; export PATH
    MANPATH=/usr/local/texlive/2019/texmf-dist/doc/man:$MANPATH; export MANPATH
    INFOPATH=/usr/local/texlive/2019/texmf-dist/doc/info:$INFOPATH; export INFOPATH

  sudo vi /etc/manpath.config
    # Datei 
    MANPATH_MAP /usr/local/texlive/2019/bin/x86_64-linux \
      /usr/local/texlive/2019/texmf-dist/doc/man  
~~~