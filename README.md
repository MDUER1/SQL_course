# SQL_course
SQL kursus af Baraa - Her ligges notes

_______

QUERY DATA:

Du kan skabe en "query" som vil sige at du beder om noget data, med disse kommandoer:

SELECT - vælger din data
FROM - Bestemmer hvor den kommer fra
WHERE - Filterer hvad du gerne vil se for nogle rækker ud  fra kolonne værdier
ORDER BY - Sorterer din data med asc eller desc, som kan kombiners med TOP for at se toppen eller bunden af noget data
GROUP BY - Her ligger du rækker sammen under én række som deler en specielt værdi du gruperer efter fx lande, så ryger alle lande og deres værdier under én række efter din definerede aggrerede funktion fx SUM
HAVING - Den sorterer igen efter du har kørt din aggrerede funktion i group by, her kan du fx have en betingelse at du kun vil se personer med en score på over 30.
DISTINCT - Den fjerner duplikater
TOP - Den viser kun de øverste x antal rækker (husk *)

De forskellige query-kommandoer ekseveres i følgende rækkefølge

1. FROM - Få data fra tabel
2. WHERE - Filtrer tabellen efter hvad du vil se
3. GROUP BY - Grupér din nye tabel + benyt en samlefunktion til at samle de grupperede værdier på din eftertragtede måde
4. HAVING - Filtrer din nye grupérede data
5. SELECT DISTINCT - Fjern evt. duplicater fx lande som går igen (beholder den øverste)
7. ORDERS BY - Bestem om dataene skal gå fra top til bund eller omvendt ud fra en specifik værdi
8. TOP - Vi nu blot de øvestre x antal rækker
_________

Definér strukturen af din database:


Benyt CREATE til at skabe en tabel i din database, og ALTER til at modificere den. ALTER vil altid tilføje din nye kolonne helt til sidst, hvis den skal stå i midten skal du starte fra scratch med at lave en ny tabel.
Benyt DROP for at fjerne en tabel fra din database.

ALTER tilføj benyt:
ALTER TABLE (navn)
ADD (kolonne navn) (datatype) (krav)

ALTER fjern benyt
ALTER TABLE (navn)
DROP COLUMN (navn) -- Husk dataen også slettes

DROP TABLE (database navn) -Fjerner hele databasen




