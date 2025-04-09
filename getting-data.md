---
layout: default
title: Tiedon hakeminen
nav_order: 5
---
# Tietojen hakeminen

Tietojen hakeminen tietokannasta. Tämä onnistuu SQL-kyselyiden avulla, jotka ovat tietokannan kyselykieltä. SQLite tukee monia SQL-käskyjä, mutta tässä keskitymme peruskäskyihin, joita tarvitset tietojen hakemiseen.

## Tietojen hakeminen SELECT-käskyllä

Tietojen hakeminen SQLite-tietokannasta tapahtuu pääasiassa `SELECT`-käskyllä. Tämä komento mahdollistaa tietojen valitsemisen ja hakemisen taulusta. Esimerkiksi seuraava komento hakee kaikki tiedot `users`-taulusta:

```sql
SELECT * FROM users;
```

Tässä esimerkissä `*` tarkoittaa, että kaikki sarakkeet valitaan. Voit myös valita vain tietyt sarakkeet seuraavasti:

```sql
SELECT name, email FROM users;
```

Tässä esimerkissä valitaan vain `name` ja `email` sarakkeet `users`-taulusta.
Voit myös lisätä ehtoja tietojen hakemiseen `WHERE`-lauseella. Esimerkiksi seuraava komento hakee kaikki käyttäjät, joiden ikä on yli 18 vuotta:

```sql
SELECT * FROM users WHERE age > 18;
```

Tässä esimerkissä `WHERE`-lause määrittää ehdon, jonka mukaan vain ne käyttäjät, joiden ikä on yli 18 vuotta, valitaan.
Voit myös käyttää `ORDER BY`-lausetta tietojen järjestämiseen. Esimerkiksi seuraava komento hakee kaikki käyttäjät ja järjestää ne nimen mukaan aakkosjärjestykseen:

```sql
SELECT * FROM users ORDER BY name ASC;
```

Tässä esimerkissä `ORDER BY`-lause järjestää tulokset nimen mukaan nousevassa järjestyksessä (`ASC` tarkoittaa "ascending", eli nouseva järjestys). Voit myös käyttää `DESC`-lausetta laskevan järjestyksen määrittämiseen:

```sql
SELECT * FROM users ORDER BY name DESC;
```

Tässä esimerkissä `DESC` tarkoittaa "descending", eli laskeva järjestys.
Voit myös rajoittaa tulosten määrää `LIMIT`-lauseella. Esimerkiksi seuraava komento hakee vain kolme ensimmäistä käyttäjää:

```sql
SELECT * FROM users LIMIT 3;
```

Tässä esimerkissä `LIMIT`-lause rajoittaa tulosten määrän kolmeen ensimmäiseen käyttäjään.
Voit myös yhdistää useita ehtoja `AND`- ja `OR`-lauseilla. Esimerkiksi seuraava komento hakee kaikki käyttäjät, joiden ikä on yli 18 vuotta ja jotka asuvat Helsingissä:

```sql
SELECT * FROM users WHERE age > 18 AND city = 'Helsinki';
```

Tässä esimerkissä `AND`-lause yhdistää kaksi ehtoa, jolloin vain ne käyttäjät, jotka täyttävät molemmat ehdot, valitaan.
Voit myös käyttää `OR`-lausetta, jos haluat valita käyttäjät, jotka täyttävät ainakin yhden ehdon:

```sql
SELECT * FROM users WHERE age > 18 OR city = 'Helsinki';
```

Tässä esimerkissä `OR`-lause yhdistää kaksi ehtoa, jolloin kaikki käyttäjät, jotka täyttävät ainakin yhden ehdon, valitaan.
Voit myös käyttää `LIKE`-lausetta osittaiseen vertailuun. Esimerkiksi seuraava komento hakee kaikki käyttäjät, joiden nimi alkaa kirjaimella "A":

```sql
SELECT * FROM users WHERE name LIKE 'A%';
```

Tässä esimerkissä `LIKE`-lause yhdistää osittaisen vertailun, jolloin kaikki käyttäjät, joiden nimi alkaa kirjaimella "A", valitaan. `%` tarkoittaa, että nimen jälkeen voi olla mitä tahansa merkkejä.
Voit myös käyttää `IN`-lausetta useiden arvojen vertailuun. Esimerkiksi seuraava komento hakee kaikki käyttäjät, joiden ikä on joko 18, 20 tai 25 vuotta:

```sql
SELECT * FROM users WHERE age IN (18, 20, 25);
```

Tässä esimerkissä `IN`-lause yhdistää useita arvoja, jolloin kaikki käyttäjät, joiden ikä on joko 18, 20 tai 25 vuotta, valitaan.
Voit myös käyttää `BETWEEN`-lausetta tietyn arvovälin valitsemiseen. Esimerkiksi seuraava komento hakee kaikki käyttäjät, joiden ikä on 18 ja 25 vuoden välillä:

```sql
SELECT * FROM users WHERE age BETWEEN 18 AND 25;
```

Tässä esimerkissä `BETWEEN`-lause yhdistää arvovälin, jolloin kaikki käyttäjät, joiden ikä on 18 ja 25 vuoden välillä, valitaan.
Voit myös käyttää `GROUP BY`-lausetta tietojen ryhmittelyyn. Esimerkiksi seuraava komento hakee käyttäjien määrän jokaisessa kaupungissa:

```sql
SELECT city, COUNT(*) FROM users GROUP BY city;
```

Tässä esimerkissä `GROUP BY`-lause ryhmittelee tulokset kaupungin mukaan, jolloin saadaan jokaisen kaupungin käyttäjien määrä.
Voit myös käyttää `HAVING`-lausetta ehtojen määrittämiseen ryhmitellyille tuloksille. Esimerkiksi seuraava komento hakee kaupungit, joissa on yli 10 käyttäjää:

```sql
SELECT city, COUNT(*) FROM users GROUP BY city HAVING COUNT(*) > 10;
```

Tässä esimerkissä `HAVING`-lause määrittää ehdon ryhmitellyille tuloksille, jolloin vain kaupungit, joissa on yli 10 käyttäjää, valitaan.
Voit myös käyttää `JOIN`-lausetta yhdistämään tietoja useista tauluista. Esimerkiksi seuraava komento hakee kaikki tilaukset ja niiden käyttäjät:

```sql
SELECT orders.*, users.name FROM orders
JOIN users ON orders.user_id = users.id;
```

Tässä esimerkissä `JOIN`-lause yhdistää `orders`- ja `users`-taulut käyttäjän ID:n perusteella, jolloin saadaan kaikki tilaukset ja niiden käyttäjät.
Voit myös käyttää `LEFT JOIN`-lausetta, jos haluat näyttää kaikki tilaukset, vaikka niillä ei olisi vastaavaa käyttäjää:

```sql
SELECT orders.*, users.name FROM orders
LEFT JOIN users ON orders.user_id = users.id;
```

Tässä esimerkissä `LEFT JOIN`-lause yhdistää `orders`- ja `users`-taulut käyttäjän ID:n perusteella, mutta näyttää myös kaikki tilaukset, vaikka niillä ei olisi vastaavaa käyttäjää.
Voit myös käyttää `RIGHT JOIN`-lausetta, jos haluat näyttää kaikki käyttäjät, vaikka heillä ei olisi tilauksia:

```sql
SELECT orders.*, users.name FROM orders
RIGHT JOIN users ON orders.user_id = users.id;
```

Tässä esimerkissä `RIGHT JOIN`-lause yhdistää `orders`- ja `users`-taulut käyttäjän ID:n perusteella, mutta näyttää myös kaikki käyttäjät, vaikka heillä ei olisi tilauksia.
Voit myös käyttää `FULL OUTER JOIN`-lausetta, jos haluat näyttää kaikki käyttäjät ja tilaukset, vaikka niillä ei olisi vastaavaa toisiaan:

```sql
SELECT orders.*, users.name FROM orders
FULL OUTER JOIN users ON orders.user_id = users.id;
```

Tässä esimerkissä `FULL OUTER JOIN`-lause yhdistää `orders`- ja `users`-taulut käyttäjän ID:n perusteella, mutta näyttää myös kaikki käyttäjät ja tilaukset, vaikka niillä ei olisi vastaavaa toisiaan.
Voit myös käyttää `UNION`-lausetta yhdistämään useita kyselyitä. Esimerkiksi seuraava komento hakee kaikki käyttäjät ja tilaukset:

```sql
SELECT name FROM users
UNION
SELECT product FROM orders;
```

Tässä esimerkissä `UNION`-lause yhdistää kaksi kyselyä, jolloin saadaan kaikki käyttäjät ja tilaukset.
Voit myös käyttää `INTERSECT`-lausetta yhdistämään useita kyselyitä, jolloin saadaan vain ne tulokset, jotka ovat molemmissa kyselyissä. Esimerkiksi seuraava komento hakee kaikki käyttäjät, jotka ovat myös tilanneet jotain:

```sql
SELECT name FROM users
INTERSECT
SELECT product FROM orders;
```

Tässä esimerkissä `INTERSECT`-lause yhdistää kaksi kyselyä, jolloin saadaan vain ne käyttäjät, jotka ovat myös tilanneet jotain.

Voit myös käyttää `EXCEPT`-lausetta yhdistämään useita kyselyitä, jolloin saadaan vain ne tulokset, jotka ovat ensimmäisessä kyselyssä, mutta eivät toisessa. Esimerkiksi seuraava komento hakee kaikki käyttäjät, jotka eivät ole tilanneet mitään:

```sql
SELECT name FROM users
EXCEPT
SELECT product FROM orders;
```

Tässä esimerkissä `EXCEPT`-lause yhdistää kaksi kyselyä, jolloin saadaan vain ne käyttäjät, jotka eivät ole tilanneet mitään.
