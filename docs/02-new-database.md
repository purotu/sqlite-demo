# Uuden tietokannan luominen

SQLite-tietokannan luominen on helppoa ja nopeaa. Voit luoda uuden tietokannan yksinkertaisesti määrittämällä tietokannan nimen ja polun, johon se tallennetaan. SQLite käyttää tiedostopohjaista lähestymistapaa, joten voit luoda uuden tietokannan tiedoston avulla.

´´´bash
sqlite3 my_database.db
´´´
Tämä komento luo uuden SQLite-tietokannan nimeltä `my_database.db` nykyiseen työhakemistoon. Jos tiedosto on jo olemassa, SQLite avaa sen.
Voit myös määrittää tietokannan polun, jos haluat tallentaa sen eri hakemistoon. Esimerkiksi:
´´´bash
sqlite3 /path/to/my_database.db
´´´
Tämä komento luo uuden SQLite-tietokannan nimeltä `my_database.db` määritettyyn hakemistoon. Jos tiedosto on jo olemassa, SQLite avaa sen.
Kun olet luonut tietokannan, voit alkaa luoda tauluja ja lisätä tietoja siihen. SQLite tarjoaa monia komentoja ja toimintoja tietokannan hallintaan, kuten taulujen luominen, tietojen lisääminen, päivittäminen ja poistaminen.
