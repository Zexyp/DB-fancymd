# Remote Dependencies

- odkazy na objekty v jiné databázi

```sql
CREATE DATABASE LINK muj_db_link
CONNECT TO vzdalene_uzivatelske_jmeno IDENTIFIED BY vzdalene_heslo
USING 'nazev_vzdalene_databaze';

-- 

CREATE OR REPLACE mistni_procedura IS
BEGIN
    vzdalena_procedura@muj_db_link(...)
END;
```

> 📌 pokud vzdálená procedura není validní tak se to dozvíme až v době spuštění místní procedury

## Správa vzdálených závislostí

### Módy kontroly závislosí

- <span style="font-size: 1.5em;">`TIMESTAMP`</span> (výchozí)
    - každá změna objektu je automaticky zaznamenána
    - při změně místní procedury se místně ukládá i časová známka vzdálené procedury
    - nevýhoda &rarr; i když je vzdálená procedura validní, je potřeba překompilovat tu místní
    > 📌 příklad pro zjištění časové známky změny objektu
    > ```sql
    > SELECT timestamp FROM USER_OBJECTS; 
    > ```
    <span style="color: red;">>>> **přiklad na tabuly** <<<</span>

- <span style="font-size: 1.5em">`SIGNATURE`</span>
    - podle signatury metody
    - signatura vzdálené procedury se ukládá v místní proceduře
    > 📌 *připomenutí* - signaturu tvoří:
    > - název procedury
    > - datovými typy parametrů procedury
    > - módy parametrů procedury

nastavení pro aktuální relaci
```sql
ALTER SESSION SET REMOTE_DEPENDENCIES_MODE = {SIGNATURE | TIMESTAMP}
```

nastavení v celém systému
```sql
ALTER SYSTEM SET REMOTE_DEPENDENCIES_MODE = {SIGNATURE | TIMESTAMP}
```

## Opáčko
<span style="color: #8888;">už se mi to nechce překládat...</span>
- Remote dependency
- Signature mode
- Timestamp mode

---

<p align="center">
    <img style="width: 75%;" src="assets/img.webp"/>
</p>
