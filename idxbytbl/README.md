# Indexování tabulek záznamů
`INDEX BY` tabulka je [kolekce](#kolekce) \*tečka\*

## Kolekce
- druh kompozitní proměné
- stejný druh dat uložených jako proměnná
- oložená v paměti

## Deklarace
deklarace
```sql
TYPE název_typu IS TABLE OF DATOVÝ_TYP
INDEX BY DATOVÝ_TYP_PRIMÁRNÍHO_KLÍČE;
```

klasické použití
```sql
identifikátor název_typu;
```

plnění
```sql
DECLARE
    TYPE název_typu IS TABLE OF DATOVÝ_TYP
    INDEX BY DATOVÝ_TYP_PRIMÁRNÍHO_KLÍČE;
    -- opice sem v originálu nedaly vynechaný řádek takže se to nedalo číst
    identifikátor název_typu;
BEGIN
    FOR záznam IN (SELECT sloupec FROM tabulka) LOOP
        -- povšimněte si jak podivně v Oracle Corporation zapisují hranaté závorky
        identifikátor(primární_klíč) := záznam.sloupec;
    END LOOP;
END;
```

## Metody
**ne** všechny se volání jsou *se závorkami*\
<span style="font-size: 2em;">🤔😳</span>

EXISTS
COUNT
FIRST
LAST

PRIOR
NEXT
DELETE
TRIM

ps: just f*cking kill me

## Opáčko
- coe kolekce
- coe INDEX BY tabulka
- coe INDEX BY tabulka záznamů

## Memísek
<center>
    <img src="./assets/i2p4hwibee771.webp"/>
</center>