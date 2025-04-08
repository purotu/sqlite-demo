# Tietojen tuominen SQLite-tietokantaan

Voit tuoda tietoja SQLite-tietokantaan useilla eri tavoilla. Tässä on muutamia yleisimpiä menetelmiä:

## CSV-tiedostojen tuominen

### 1. **Valmistele CSV-tiedosto**

Varmista, että CSV-tiedostosi on oikein muotoiltu. Esimerkiksi:

```csv
id,name,email
1,Matti Meikäläinen,matti@example.com
2,Liisa Virtanen,liisa@example.com
```

### 2. **Avaa SQLite-komentotulkki**

Avaa SQLite-tietokanta tai luo uusi tietokanta:

```bash
sqlite3 tietokanta.db
```

### 3. **Luo taulu tietokantaan**

Luo taulu, johon CSV-tiedoston tiedot tuodaan. Esimerkiksi:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    email TEXT NOT NULL UNIQUE
);
```

### 4. **Ota käyttöön `.mode csv`**

Aseta SQLite käyttämään CSV-muotoa:

```sql
.mode csv
```

### 5. **Tuonti CSV-tiedostosta**

Käytä `.import`-komentoa tuodaksesi CSV-tiedoston tietokantaan:

```sql
.import /polku/tiedostoon.csv users
```

Korvaa `/polku/tiedostoon.csv` CSV-tiedostosi polulla ja `users` taulun nimellä.

### 6. **Varmista tuonti**

Tarkista, että tiedot on tuotu onnistuneesti:

```sql
SELECT * FROM users;
```

### 7. **Sulje SQLite**

Kun olet valmis, sulje SQLite:

```sql
.exit
```

Tämä tuo CSV-tiedoston tiedot SQLite-tietokantaan.

Kun tuot tietoja CSV-muodossa SQLite-tietokantaan, on hyvä huomioida seuraavat asiat:

### 1. **Sarakeotsikot**

Jos CSV-tiedostossa on sarakeotsikot, SQLite ei automaattisesti ohita niitä. Voit ohittaa ensimmäisen rivin (otsikot) käyttämällä `.mode csv` -tilan jälkeen komentoa:

```bash
.headers on
```

Tämä varmistaa, että SQLite käsittelee ensimmäistä riviä sarakeotsikoina eikä datana.

---

### 2. **Tietotyyppien yhteensopivuus**

Varmista, että CSV-tiedoston sarakkeiden tiedot vastaavat SQLite-taulun sarakkeiden tietotyyppejä. Esimerkiksi:

- Tekstikentät (`TEXT`) eivät saa sisältää ylimääräisiä lainausmerkkejä.
- Numerokentät (`INTEGER`, `REAL`) eivät saa sisältää kirjaimia tai muita ei-numeerisia merkkejä.

---

### 3. **Erotinmerkki**

Oletuksena SQLite käyttää pilkkua (`,`) CSV-tiedoston erottimena. Jos CSV-tiedostosi käyttää jotain muuta, kuten puolipistettä (`;`), voit vaihtaa erottimen seuraavalla komennolla ennen tuontia:

```bash
.separator ";"
```

---

### 4. **Puuttuvat arvot**

Jos CSV-tiedostossa on tyhjiä kenttiä, SQLite tulkitsee ne `NULL`-arvoiksi. Varmista, että tämä on haluttu käyttäytyminen, tai täytä puuttuvat arvot ennen tuontia.

---

### 5. **Erikoismerkit**

Jos CSV-tiedostossa on erikoismerkkejä, kuten lainausmerkkejä, pilkkuja tai uusia rivejä, varmista, että ne on asianmukaisesti escapettu. Esimerkiksi:

- Tekstikentät, joissa on pilkkuja, tulisi ympäröidä lainausmerkeillä: `"arvo, jossa on pilkku"`.
- Lainausmerkit tekstikentissä tulisi escapettaa kaksoislainauksilla: `"arvo ""lainausmerkeillä"""`.

---

### 6. **Tietojen validointi**

Tarkista tuodut tiedot tuonnin jälkeen varmistaaksesi, että kaikki tiedot on tuotu oikein:

```sql
SELECT * FROM my_table LIMIT 10;
```

---

### 7. **Indeksit ja rajoitteet**

Jos taulussa on indeksejä tai rajoitteita (esim. `UNIQUE` tai `FOREIGN KEY`), varmista, että CSV-tiedoston tiedot eivät riko näitä rajoitteita. Muuten tuonti voi epäonnistua.

---

### 8. **Suorituskyky**

Jos tuot suuria CSV-tiedostoja, suorituskykyä voi parantaa seuraavasti:

- Poista automaattiset transaktiot käytöstä tuonnin ajaksi:
  ```sql
  BEGIN TRANSACTION;
  .import data.csv my_table
  COMMIT;
  ```
- Poista indeksit käytöstä ennen tuontia ja luo ne uudelleen tuonnin jälkeen.

---

Näiden vinkkien avulla voit varmistaa, että CSV-tiedoston tuonti SQLite-tietokantaan sujuu ongelmitta.

## SQL-tiedostojen tuominen

Voit myös tuoda tietoja SQL-tiedostoista käyttämällä `sqlite3`-komentoa. Esimerkiksi seuraava komento tuo tietoja `data.sql`-tiedostosta:

```bash
sqlite3 my_database.db < data.sql
```

Tässä esimerkissä `data.sql` on tuomittava tiedosto, joka sisältää SQL-käskyjä tietojen lisäämiseksi tauluun.
