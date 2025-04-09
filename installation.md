---
layout: default
title: Asentaminen
nav_order: 2
---
# SQLiten asennus

SQLite on helppo asentaa ja käyttää. Se on saatavilla useimmille käyttöjärjestelmille, mukaan lukien Windows, macOS ja Linux.

## SQLite eri käyttöjärjestelmissä

### Windows
1. Lataa SQLiten Windows-versio [täältä](https://www.sqlite.org/download.html).
2. Pura ladattu tiedosto ja siirrä `sqlite3.exe` haluamaasi kansioon.
3. Lisää kansio PATH-muuttujaan, jotta voit käyttää SQLitea komentoriviltä:
   - Avaa **Järjestelmäasetukset** > **Ympäristömuuttujat**.
   - Lisää kansio, jossa `sqlite3.exe` sijaitsee, PATH-muuttujaan.

### macOS
1. Tarkista, onko SQLite asennettu, kirjoittamalla `sqlite3` terminaaliin.
2. Jos SQLite ei ole asennettuna, asenna se Homebrew:n avulla:
   ```bash
   brew install sqlite
   ```

### Linux

1. Tarkista, onko SQLite asennettu, kirjoittamalla sqlite3 terminaaliin.
2. Jos SQLite ei ole asennettuna, asenna se jakelusi pakettienhallinnan avulla:

    ```bash
    # Ubuntu:
    sudo apt-get install sqlite3
    ``` 

    ```bash
    # Arch Linux:
    sudo pacman -S sqlite
    ``` 

## SQLite eri ohjelmointikielissä

SQLite on saatavilla myös useissa ohjelmointikielissä, joten voit käyttää sitä eri ympäristöissä. Tässä on esimerkkejä SQLiten käytöstä eri ohjelmointikielissä:

- **C**: SQLite on kirjoitettu C-kielellä, joten voit käyttää sitä suoraan C-ohjelmissa. Lataa SQLiten lähdekoodi [täältä](https://www.sqlite.org/download.html) ja käännä se omassa ympäristössäsi. Voit myös käyttää SQLiten esikäännettyjä kirjastoja.
- **C++**: SQLite on yhteensopiva C++:n kanssa, joten voit käyttää sitä C++-ohjelmissa samalla tavalla kuin C:ssä. Voit ladata SQLiten lähdekoodin ja kääntää sen C++-ympäristössäsi.
- **Python**: SQLite on sisäänrakennettu Pythonin standardikirjastoon, joten voit käyttää sitä ilman erillistä asennusta. Voit tarkistaa, onko SQLite käytettävissä Pythonissa kirjoittamalla `import sqlite3` Python-konsolissa.
- **Java**: SQLite on saatavilla myös Java-kirjastona. Voit ladata SQLiten JDBC-ajurin [täältä](https://bitbucket.org/xerial/sqlite-jdbc/downloads/). Lisää ladattu JAR-tiedosto projektisi riippuvuuksiin.
- **Node.js**: SQLite on saatavilla myös Node.js:lle. Voit asentaa SQLiten Node.js-kirjaston komennolla `npm install sqlite3`. Tämä asentaa SQLiten ja sen riippuvuudet projektiisi.
- **PHP**: SQLite on saatavilla myös PHP:lle. Voit tarkistaa, onko SQLite käytettävissä PHP:ssä kirjoittamalla `phpinfo()` ja etsimällä "SQLite" -osion. Jos se ei ole asennettuna, voit asentaa sen PHP:n laajennusten avulla.
- **Ruby**: SQLite on saatavilla myös Ruby:lle. Voit asentaa SQLiten RubyGemsin avulla komennolla `gem install sqlite3`. Tämä asentaa SQLiten ja sen riippuvuudet projektiisi.

## Harjoitus
1. Asenna SQLite omalle käyttöjärjestelmällesi.
2. Testaa että se toimii kirjoittamalla `sqlite3` komentoriville.