# Taulujen käsittely

Taulujen käsittely SQLite-tietokannassa on tärkeä osa tietokannan hallintaa. Taulut ovat tietokannan perusyksiköitä, ja ne sisältävät tietoja, jotka on järjestetty riveihin ja sarakkeisiin. Tässä osassa käsitellään taulujen luomista, muokkaamista ja poistamista SQLite-tietokannassa.

## Taulujen luominen

Taulujen luominen SQLite-tietokannassa tapahtuu SQL-käskyjen avulla. Voit määrittää taulun nimen, sarakkeet ja niiden tietotyypit. Esimerkiksi seuraava komento luo taulun nimeltä `users`, jossa on kolme saraketta: `id`, `name` ja `email`:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    email TEXT NOT NULL UNIQUE
);
```

Tässä esimerkissä `id`-sarakkeen tietotyyppi on `INTEGER`, ja se toimii ensisijaisena avaimena. `name`- ja `email`-sarakkeiden tietotyyppi on `TEXT`, ja ne eivät saa olla tyhjät (`NOT NULL`). Lisäksi `email`-sarakkeessa on määritetty, että sen arvojen on oltava ainutlaatuisia (`UNIQUE`).
Voit luoda useita tauluja samalla komennolla erottamalla ne puolipisteellä. Esimerkiksi:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    email TEXT NOT NULL UNIQUE
);
CREATE TABLE orders (
    id INTEGER PRIMARY KEY,
    user_id INTEGER NOT NULL,
    product TEXT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

Tässä esimerkissä luodaan kaksi taulua: `users` ja `orders`. `orders`-taulussa on viittaus `users`-tauluun, mikä tarkoittaa, että jokaisella tilauksella on liittyvä käyttäjä.

Kun haluat katsoa luomasi taulut, voit käyttää seuraavaa komentoa:

```sql
SELECT name FROM sqlite_master WHERE type='table';
```

Tämä komento palauttaa luettelon kaikista tietokannan tauluista.

## Taulujen muokkaaminen

Taulujen muokkaaminen SQLite-tietokannassa voidaan tehdä useilla tavoilla. Voit lisätä uusia sarakkeita, muuttaa olemassa olevien sarakkeiden tietotyyppejä tai poistaa sarakkeita. Esimerkiksi seuraava komento lisää uuden sarakkeen `age` tauluun `users`:

```sql
ALTER TABLE users ADD COLUMN age INTEGER;
```

Tässä esimerkissä lisätään uusi sarake `age`, jonka tietotyyppi on `INTEGER`. Voit myös muuttaa olemassa olevan sarakkeen tietotyyppiä seuraavalla komennolla:

```sql
ALTER TABLE users RENAME COLUMN name TO full_name;
```

Tässä esimerkissä sarakkeen `name` nimi muutetaan `full_name`:ksi. Huomaa, että sarakkeen tietotyyppiä ei voi muuttaa suoraan SQLite-tietokannassa, mutta voit luoda uuden sarakkeen haluamallasi tietotyypillä ja siirtää tiedot vanhasta sarakkeesta uuteen.

## Taulujen poistaminen

Taulujen poistaminen SQLite-tietokannasta tapahtuu `DROP TABLE` -komennolla. Esimerkiksi seuraava komento poistaa `users`-taulun:

```sql
DROP TABLE users;
```

Tässä esimerkissä `users`-taulu poistetaan tietokannasta. Huomaa, että tämä komento poistaa kaikki tiedot ja rakenteen taulusta, joten käytä sitä varoen.

## Taulujen tarkastelu

Voit tarkastella tietokannan tauluja ja niiden rakennetta käyttämällä `PRAGMA`-komentoa. Esimerkiksi seuraava komento näyttää kaikki tietokannan taulut:

```sql
PRAGMA table_info(users);
```

Tässä esimerkissä `table_info` näyttää taulun `users` sarakkeet ja niiden tietotyypit. Voit myös tarkastella kaikkia tietokannan tauluja seuraavalla komennolla:

```sql
SELECT name FROM sqlite_master WHERE type='table';
```

Tässä esimerkissä `sqlite_master`-taulusta haetaan kaikki taulut, jotka ovat tyyppiä `table`. Tämä komento palauttaa luettelon kaikista tietokannan tauluista.

## Yhteenveto

SQLite-tietokannan taulujen käsittely on tärkeä osa tietokannan hallintaa. Voit luoda, muokata ja poistaa tauluja SQL-käskyjen avulla. Taulut ovat tietokannan perusyksiköitä, ja niiden avulla voit järjestää ja hallita tietoja tehokkaasti. Muista käyttää varovaisuutta taulujen poistamisessa, sillä se poistaa kaikki tiedot ja rakenteen taulustSELECT name FROM sqlite_master WHERE type='table';a.
