# INSTALLAZIONE ROOT CERN versione 6.26.06 (LINUX UBUNTU 20 su WSL su WINDOWS)

Aprite il terminale (Ubuntu WSL) e copiate e incollate (in ordine) tutti i comandi della guida.

- [INSTALLAZIONE ROOT CERN versione 6.26.06 (LINUX UBUNTU 20 su WSL su WINDOWS](#installazione-root-cecrn-versione-6.26.06-linux-ubuntu-20-su-wsl-su-windows)
    - [0. Preparazione all'installazione](#preparazione-all'installazione)
    - [1. Rimozione della precedente installazione di ROOT (NECESSARIO per non avere conflitti tra le versioni)](#rimozione-della-precedente-installazione-di-root)
    - [2.	Scaricamento del file compresso della nuova versione di ROOT](scaricamento-del-file-compresso-della-nuova-versione-di-root)
    - [3. Installazione](installazione)
    - [4. Setup finale](setup-finale)


## 0. Preparazione all'installazione

Controllo della presenza di aggiornamenti:

``` bash
sudo apt update && sudo apt upgrade
```

Installazione delle librerie necessarie per ROOT:

``` bash
sudo apt-get install dpkg-dev cmake g++ gcc binutils libx11-dev libxpm-dev \
libxft-dev libxext-dev python libssl-dev
```

Installazione di altre librerie necessarie per ROOT:

``` bash
sudo apt-get install gfortran libpcre3-dev \
xlibmesa-glu-dev libglew1.5-dev libftgl-dev \
libmysqlclient-dev libfftw3-dev libcfitsio-dev \
graphviz-dev libavahi-compat-libdnssd-dev \
libldap2-dev python-dev libxml2-dev libkrb5-dev \
libgsl0-dev qtwebengine5-dev
```

## 1. Rimozione della precedente installazione di ROOT (NECESSARIO per non avere conflitti tra le versioni)

Salviamo prima le possibili macro presenti nella precedente installazione di ROOT

``` bash
cd ~
```

``` bash
mkdir macros
```

``` bash
cd ~
```

``` bash
mv -v ~/root/macros/* ~/macros/
```

Rimuoviamo la precedente installazione di ROOT

``` bash
cd ~
```

``` bash
rm -r root
```

``` bash
cd ~
```

## 2.	Scaricamento del file compresso della nuova versione di ROOT

``` bash
cd ~
```

``` bash
wget https://root.cern/download/root_v6.26.06.Linux-ubuntu20-x86_64-gcc9.4.tar.gz
```

## 3. Installazione

``` bash
cd ~
```

``` bash
tar -xzvf root_v6.26.06.Linux-ubuntu20-x86_64-gcc9.4.tar.gz
```

## 4. Setup finale

Rimettiamo le macro nella cartella di ROOT

``` bash
cd ~
```

``` bash
mv -v ~/macros/* ~/root/macros/
```

``` bash
cd ~
```

``` bash
rm -r ~/macros
```

Modifichiamo il file di avvio della bash in modo che il comando `root` invochi in automatico il software ROOT.

``` bash
code .bashrc
```

Aggiungere in fondo al file la seguente linea di codice (DOPO UNO SPAZIO VUOTO se non viene in automatico)

``` bash

source root/bin/thisroot.sh
```

Nel caso in cui sia già presente siete a posto!

Chiudete il terminale di Ubuntu WSL, riapritelo e scrivete

``` bash
root
```
Dovrebbe comparire scritto sul terminale qualcosa di questo tipo in cui è chiaro che avete installata la versione 6.26.06.

![bash ROOT v6.26.06](https://raw.githubusercontent.com/giopedro92/Guida_aggiornamento_ROOT_v6.26.06/main/bash_ROOT_v6.26.06.png)

Fate sapere nel caso di problemi.

>Giovanni Pedrelli