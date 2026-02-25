# Besvarelse: SQL-Analyse

## Oppgave 1: Grunnleggende Spørringer
1.  `SELECT * FROM Vare;`
2.  `SELECT VNr, Betegnelse FROM Vare;`
3.  `SELECT DISTINCT KatNr FROM Vare;`
4.  `SELECT Fornavn, Etternavn, Stilling AS Jobbtittel FROM Ansatt;`

1.  **Forklaring:** Vises hele data fra Vare tabellen.

2.  **Forklaring:** Vises columner "VNr(primærnøkkel antagelig)" og "Betegnelse" fra Vare tabellen.

3.  **Forklaring:** Vises alle varer med unike KatNr

4.  **Forklaring:** Vises Fornavn, Etternavnm og Stilling med navnet "Jobbtittel" fra Ansatt tabellen.

## Oppgave 2: WHERE-klausulen
1.  `SELECT * FROM Vare WHERE Pris > 500;`
2.  `SELECT * FROM Ansatt WHERE Stilling = 'Salgssjef' AND Årslønn > 600000;`
3.  `SELECT Fornavn, Etternavn FROM Kunde WHERE PostNr = '0001' OR PostNr = '0002';`
4.  `SELECT Betegnelse FROM Vare WHERE NOT KatNr = 1;

1.  **Forklaring:** Vi trekker ut alle columner som ligger i Vare tabellen, men rader skulle bli sortert, og det viser varene som har pris 501 og mer

2.  **Forklaring:** Trekkes ut alle ansatt som er Salgsjeff, også årslønn er mer enn 600000

3.  **Forklaring:** Trekkes ut Fornavn, Etternavn av alle kunder som bor der hvor postNr er 0001 eller 0002

4.  **Forklaring:** Vises alle betegnelser av varer hvor KatNr er ikke 1.

## Oppgave 3: Gruppering og Sortering
1.  `SELECT * FROM Vare ORDER BY Pris DESC;`
2.  `SELECT KatNr, COUNT(*) FROM Vare GROUP BY KatNr;`
3.  `SELECT Stilling, AVG(Årslønn) FROM Ansatt GROUP BY Stilling;`
4.  `SELECT KatNr, SUM(Antall) FROM Vare GROUP BY KatNr HAVING SUM(Antall) > 500;`

1.  **Forklaring:** Vises hele dataen av varene som er dyreste i tabellen.

2.  **Forklaring:** Vises KatNr, og antall av alle varene fra Vare tabellen.

3.  **Forklaring:** Vises stilling og gjennomsnitt av årslønn av alle stillinger fra ansatt tabellen, uten duplikater av fordi Group by stilling.

4.  **Forklaring:** Vises Katnr og summ av alle varene hvor sum per katnr er større enn 500.

## Oppgave 4: Spørringer mot Flere Tabeller
1.  `SELECT V.Betegnelse, K.Navn FROM Vare V JOIN Kategori K ON V.KatNr = K.KatNr;`
2.  `SELECT O.OrdreNr, K.Fornavn, K.Etternavn FROM Ordre O LEFT JOIN Kunde K ON O.KNr = K.KNr;`
3.  `SELECT A1.Fornavn, A2.Fornavn FROM Ansatt A1, Ansatt A2 WHERE A1.PostNr = A2.PostNr AND A1.AnsNr < A2.AnsNr;`
4.  `SELECT V.Betegnelse FROM Vare V WHERE V.VNr NOT IN (SELECT VNr FROM Ordrelinje);`

1.  **Forklaring:** Vises Betegnelse, Navn fra Vare tabellen og data av kategori tabellen, og legger til Kategori tabellen hvor ktNr er lik.

2.  **Forklaring:** Vises OrdreNr, fra Ordre tabellen og Fornavn, Etternavn fra Kunde tabbelen, i tillegg ser vi alle ordre, til og meg hvis det er ikke data om kunden. I dette tilfelle blir det NULL i rader er Fornavn&Etternavn ikke eksisterer.

3.  **Forklaring:** Vises Fornavn og Etternavn fra to samme tabeller, men hvor de bor i samme postNr, men sletter duplikater fordi a1.ansNr< a2.ansnr.

4.  **Forklaring:** Vises alle begnelser fra Varer som ble ikke bestilte.

## Oppgave 5: NULL-verdier og Aggregeringsfunksjoner

Forklar hva følgende SQL-spørringer gjør, og hvorfor resultatene blir som de blir. Vær spesielt oppmerksom på hvordan `NULL` påvirker resultatet.

1.  **Spørring:**
    ```sql
    SELECT COUNT(*), COUNT(Bonus) FROM Ansatt;
    ```
    **Forklaring:**
    *   *... Skriv din forklaring her ...*

2.  **Spørring:**
    ```sql
    SELECT AVG(Bonus) FROM Ansatt;
    ```
    **Forklaring:**
    *   *... Skriv din forklaring her ...*

3.  **Spørring:**
    ```sql
    SELECT Fornavn, Etternavn, COALESCE(Bonus, 0) AS JustertBonus FROM Ansatt;
    ```
    **Forklaring:**
    *   *... Skriv din forklaring her ...*

4.  **Spørring:**
    ```sql
    SELECT Stilling, SUM(Årslønn + Bonus) FROM Ansatt GROUP BY Stilling;
    ```
    **Forklaring:**
    *   *... Skriv din forklaring her ...*

## Oppgave 6: Tre-verdi Logikk (TRUE, FALSE, UNKNOWN)

SQLs logikk er ikke bare `TRUE` eller `FALSE`. Når `NULL` er involvert, får vi en tredje tilstand: `UNKNOWN`. Denne oppgaven utforsker hvordan dette påvirker `WHERE`-klausuler.

### Del 1: Forklar SQL-spørringene

Forklar resultatet av følgende SQL-spørringer. Hvorfor returnerer de det de gjør?

1.  **Spørring:**
    ```sql
    SELECT COUNT(*) FROM Ordre WHERE ErBetalt = TRUE;
    ```
    **Forklaring:**
    *   *... Skriv din forklaring her ...*

2.  **Spørring:**
    ```sql
    SELECT COUNT(*) FROM Ordre WHERE ErBetalt = FALSE;
    ```
    **Forklaring:**
    *   *... Skriv din forklaring her ...*

3.  **Spørring:**
    ```sql
    SELECT COUNT(*) FROM Ordre WHERE ErBetalt = TRUE OR ErBetalt = FALSE;
    ```
    **Forklaring:**
    *   *... Skriv din forklaring her ...*

4.  **Spørring:**
    ```sql
    SELECT COUNT(*) FROM Ordre WHERE ErBetalt IS UNKNOWN;
    ```
    **Forklaring:**
    *   *... Skriv din forklaring her ...*
