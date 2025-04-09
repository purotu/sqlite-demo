---
layout: default
title: Uuden tietokannan luominen
nav_order: 3
---
# Uuden tietokannan luominen

SQLite-tietokannan luominen on helppoa ja nopeaa. Voit luoda uuden tietokannan yksinkertaisesti määrittämällä tietokannan nimen ja polun, johon se tallennetaan. SQLite käyttää tiedostopohjaista lähestymistapaa, mikä tarkoittaa, että tietokanta tallennetaan yksittäiseen tiedostoon.

Seuraava komento luo uuden SQLite-tietokannan nimeltä `my_database.db` nykyiseen työhakemistoon. Jos tiedosto on jo olemassa, SQLite avaa sen.

```bash
$ sqlite3 my_database.db
SQLite version 3.39.2 2025-04-08 12:00:00
Enter ".help" for usage hints.
sqlite>
```  

Kunt tietokanta on luotu pitäisi hakemistossa olla kyseinen tiedosto (esim. my_database.db). Komennon jälkeen olet sqlite-kehotteessa, jossa voit myös tarkistaa, että uusi tietokanta on tyhjä, kirjoittamalla komennon:

```bash
sqlite> .tables
```

Komennon antamisen jälkeen ei pitäisi näkyä mitään taluluja. Voit myös poistua sqlite-kehotteesta kirjoittamalla komennon:

```bash
sqlite> .exit
``` 

Voit avata uudelleen tietokannan kirjoittamalla komennon:

```bash
$ sqlite3 my_database.db
``` 

Tämä jälkeen voit luoda testitaulun varmistaaksesi, että tietokanta toimii. 

```bash
sqlite> CREATE TABLE test(id INTEGER PRIMARY KEY, name TEXT);
sqlite> .tables
```

Komento näyttää nyt taulun test, jos tietokanta toimii oikein.

## Tietokannan poistaminen

Tietokanta poistetaan poistamalla tiedosto.

## Vinkkejä ja parhaita käytäntöjä

### Tietokannan sijainti

On suositeltavaa tallentaa tietokanta hakemistoon, johon on helppo pääsy, mutta joka on suojattu luvattomalta käytöltä.

### Varmuuskopiointi

Koska SQLite-tietokanta on yksittäinen tiedosto, sen varmuuskopiointi on helppoa. Kopioi vain tiedosto turvalliseen paikkaan.

## Seuraavat vaiheet

Kun olet luonut tietokannan, voit alkaa luoda tauluja ja lisätä tietoja siihen. SQLite tarjoaa monia komentoja ja toimintoja tietokannan hallintaan, kuten taulujen luominen, tietojen lisääminen, päivittäminen ja poistaminen.