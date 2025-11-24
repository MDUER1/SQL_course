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

________

MANIPULATE/MODIFY YOUR DATA:
INDSÆT DATA I EN TABEL:
MEOTDE 1: INSERT INTO tabel navn (række_1, række_2, ...)    --- Det er optional at skrive kolonnerne, men SQL forventer ellers værdier for alle kolonner hvis de ikke skrives, så hvis du tilføjer en værdi til alle kolonner så lad vær med at skrive kolonnerne, hvis du skriver dem alle, du kan bare skippe det.
VALUE (value1, value2, osv.) --- VIGTIGT, antal kolonner og værdier angivet skal matche + De skal matche i rækkefølge + følg datatypereglerne sat og kravene

Note: Du kan insert multiple værdier, sådan her
VALUE (value1, value2, value3),
      (value1, value2, value3) ...

-- De kolonner som ikke vælges, de får angivet NULL automatisk som værdi når du inserter ny data og kun speficiferer et mindre antal kolonner som skal have givet værdier.

METODE 2:
Flyt data fra en tabel til en anden gennem SELECT

BENYT SELECT, og vælg de kolonner du skal bruge fra databasen du skal tage data fra. TIP: Åben databaens kolonne som du vil indsætte værdier ind i og tilpas select dertil så du kan se hvilke værdier du skal importere og hvilke der kan være null og ikke kan være null.

For at flytte data fra en tabel til en anden, så skriver du en query vha. select, og så benyter du INSERT INTO (tabel navn) for at kaste dataen ind i den tabels navn.

UPDATE ændrer/opdaterer den nuværende data i en tabel. --HUSK at benytte WHERE for at slippe for at opdatere hele databasen på en gang.

HER skal du ALTID benytte en WHERE claus for at sige hvilke rækker som skal have opdateret en kolonne. Ellers opdateres hele databasen.

TIP: Benyt en select quere med WHERE og så hvad du har sat where til i UPDATE funktionen for at se hvad for noget data der påvirkes inden du opdaterer.

For at slette data benytter du DELETE FROM (tabel navn) sammen med en WHERE condition, ALTID - eller sletter du alle kolonner.

Hvis du vil slette alt i en tabel, og du ved at det er det du vil, så benyt TRUNCATE TABLE i stedet for DELETE, da det er meget hurtigere. Den checker eller logger ingenting.

__________________________________________________ SQL BASCIS COMPLETE (Intro, QUERY DATA, DATA Definition, DATA Manipulation) _____________________________________________________________________________

5. FILTRERING AF DATA
WHERE:
Comparison operators - compare two things:

Strukturen er: Expressions | operator | Expression

fx 
column1 = column2 fx first_name = Last_name
column1 = value fx first_name = John
Function = Value fx UPPER(first_name) = "John"
Expression = value fx price*quantity = 1000
Subquery = value SELECT ... = Value

Comparison Operators
= - Lig med
!= - Ikke lig med
< - mindre end
> - større end
<= - mindre eller lig med
>= - større eller lig med

Logical operators
AND - All conditions must be true
OR - Atleast one conditiono must be true
NOT - REVERSE - tager den modsatte værdi

Range operator
Between - Tjekker om en værdi er inden for en range (slutpunkterne er inklusive), og benyttes sammen med AND: x between y and z
Benyt logiske operatorer i stedet, da du kan ændre boundaries, fx score >= 100 and score <= 500

Membership Operator
IN - tjekker om en række opfylder at være i en liste
Not in - tjekker om en række ikke opfylder at være i en liste
Notation: WHERE x (not) in (value, value)

Search Operator
LIKE - search for a pattern in text
Her handler det om at bygge et mønster som LIKE kan søge efter. Det gøres med % som betyder "alting" og _ som betyder 1 ting.
fx M% søger efter alt der starter med M, da alt efter accepteres af %, da den accepterer alt, selv ingenting.
%M søger efter alt som slutter med M, da den tilader alt foran M, så længe det slutter med M.
%M% søger efter alt med et M i sig. Da alt eller ingenting kan komme før eller efter.
_M søger efter 1 ting foran M og så med M efter.
M_ søger efter alt der starter med M og har en ting efter.
__b% søger efter alt med to ting foran b, og så alt eller intet efter b. fx godkendes kabfjdksfdks eller lab

Notation er: WHERE (kolonne_navn) LIKE (søg med % eller _ i '') 
fx WHERE first_name LIKE 'M%'



6. Combining Data

ALLE 9 Typer JOINS

Hvordan vælger du mellem alle de forskellige JOINS?

Hvis du vil lave en tabel hvor du joner flere tabeller hvor du kun er interesseret i det data som de matcher/begge har -> INNER JOIN
Hvis du vil se alle rækkker men én af tabellerne er vigtigere end den anden -> LEFT JOIN
Hvis du vil se alle rækker og alt er lige vigtigt -> FULL JOIN
Hvis du kun vil se hvad én tabel har som ikke matcher med andre tabeller -> LEFT ANTI JOIN
Hvis du kun vil se alt data som ikke matcher imellem tabellerne -> FULL ANTI JOIN.


Benyt eller lav en ER model for at se hvilke kolonner som der går igen hos de forskellige databaser, så du kan se hvilke du kan joine.

HUSK: JOINS samler kolonner ved siden af hinanden. SET OPERATORS tilføjer rækker under hinanden. For JOINS kræver det en nøgle-kolonne som går igen i alle tabeller du prøver at joine, og for SET OPERATORS er det at de har samme kolonner.

SET OPERATORS:

For set operators, sætte du dem mellem to SELECTs. Her på ORDER BY kun benyttes én gang og det er til aller sidst.

DU SKAL have det samme antal rækker som du viser i hver query som forbindes med en SET operator. Ellers duer det ikke.

DATATYPERNE for hver kolonne i hver query skal være compatible. Altså det skal være de samme datatyper.

RÆKKEFØLGEN SKAL være den samme under SLECET i hver query.

Den første QUERY navngiver kolonnerne i outputtet. Så hvis du vil give aliases for output kolonnerne, så skal du blot give et alias til den første query.

Husk at tjekke om din rækkefølge af kolonner er rigtig under hver query er ens, da datatyperne godt kan matche og så give det forkerte resultat uden en error, da datatyperne matcher. Fx hvis du bytter om på rækkefølgen af første og sidste navn i to queries forbundet med en SET OPERATOR.

SET OPERATOR: UNION
Returnerer alle rækker fra all queries og fjerner duplikater.

Husk du skal vælge de rækker som går igen i begge tabeller, du kan ikke bare kombinere hele tabellerne.

SET OPERATOR: UNION ALL
Returnerer alle rækker, men fjerner ikke duplikater.

Union ALL er hurtigere end Union, så hvis du ved at der ikke er duplikater, så benyt ikke UNION, da den er langsommere da den udfører flere beregninger da den tjekker for duplikater. Bare benyt UNION ALL.
Du kan også benytte UNION ALL hvis du gerne vil tjekke om der er duplikater i to tabeller.

SET OPERATOR: EXCEPT (minus)
Den returnerer alle distinkte (ingen dups) rækker fra den første query, som ikke er fundet i den næste query. Derfor er rækkefølgen af queries vigtig her, og den minder om LEFT JOIN lowkey.

SET OPERATOR: INTERSECT
Returnerer kun de rækker som går igen i begge queries, og fjerner duplikater. Minder om INNER JOIN

BRUGER GUIDE: 
Kombiner ligende data fra flere tabeller ind til 'en tabel, og så kør en query på den nye tabel - Her benyt UNION ALL eller UNION hvis du vil være sten sikker på der er ingen duplikater.

De benyttes typisk til at samle data i én tabel, og så behandle det med én query, i stedet for at behandle dem hver især, for at undgå problemer og gøre det nemmere.

For gode kodningvaner, så benyt ikke * men indsæt hver kolonne. Kopier dem fra TOP 1000 som du kan se under columns og så højreklik på tabellen.

Det er også gode kodningvaser at tilføje en ny kolonne helt i starten som siger "navnet på tabellen" og så under aliaset "SourceTable", for at se hvilke rækker kommer fra hvilke tabeller.

EXCEPT bliver typisk brugt til at udtrække ny data fra gammel data, så du kan identificere ny data som kommer fra den source, ved at benytte except på forrig data og så din nye data for at se hvilket data skiller sig ud, som må være det nye. Dette data kan så tilføjes til din database.

EXCEPT bliver også brugt meget til at teste for "data completenes", hvilket er når du fx transportere en tabel af data fra én database til en anden, for så at se om alle rækker kom med. Her kan du benytte EXCEPT til at se om der stadig er data tilbage i database A som ikke er kommet frem til database b. Hvis den er tom betyder at at alt er kommet over. Derefter gør du det den modsatte vej, og får empty hver gang, så er begge tabeller identiske.

____________________

ROW-LEVEL FUNCTIONS

En funktion i SQL er noget kode som accepterer en værdi, bearbejder den og returnerer et output.

Du har to main kategorier - single row function fx lower() eller LEFT() og multiple row functions fx SUM()

Du har også nested functions hvor du kan sætte functioner efter hinanden fx LEFT(LOWER(xxx)) og så kan du bare fortsætte sådan med fx LEN() udenpå, hvor den inderste eksekveres først og derefter arbejder den sig ud af som normalt.


SINGLE-ROW Functions:
String, Numeric, Date & Time, NULL - dataengineers

MULTI-ROW
Simple Aggregate (samle) funktioner, Window functions (advanced) - bliver typisk brugt af dataanalyst

STRING FUNCTIONS:
Manipulation:
Concat = kombinerer flere strings ind til én  string. CONCAT(xxx, xxx, ...) AS (alias)
UPPER() = Gør alle karrakterer til versaler, UPPER(xxx) AS (alias)
LOWER() = Gør at til små bogstaver, LOWER(xx,xxx) AS (alias/nyt kolonnenavn)
TRIM() = Fjerner mellemrum før og efter en string
Replace() = Erstatter en karakter, hvor du giver den "gammel værdi" og "ny værdi". Du kan også benytte den til at fjerne mellemrum, ved at erstatte med ingenting '', REPLACE('værdi.txt', 'hvad der skal erstattes', 'hvad det erstattes med')

Calculation:
LEN() = Returnerer længden på din string

String Extraction:
LEFT() Udtager et specifikt nummer af karakterer fra en string fra venstre side af.
RIGHT() Denne gør hvad LEFT() gør bare fra højre side af.
SUBSTRING() Denne udtager en del af en string fra en givet position. SUBSTRING(Value/kolonnenavn, start, length)

NUMBER FUNCTIONS: 









