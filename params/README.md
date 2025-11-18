# Předávání parametrů

## Módy (slovo *modifikátory* v Oracle Corporation ještě nenašly)
- **IN** (výchozí)\
  chová se jako konstanta\
  lze předat cokoliv\
  může mít výchozí hodnotu
- **OUT**\
  nemá prvotní hodnotu\
  lze pouze předat proměnnou
- **IN OUT**\
  má prvotní hodnotu\
  lze pouze předat proměnnou

*OUT => prostě předávání referencí...*

## Deklarace
```sql
CREATE PROCEDURE procedura(param [mód] datový_typ) IS
```

### Výchozí hodnoty (yippee)
```sql
CREATE PROCEDURE procedura(param [mód] datový_typ DEFAULT hodnota) IS
```
nebo
```sql
CREATE PROCEDURE procedura(param [mód] datový_typ := hodnota) IS
```

lze pouze použít u `IN` parametru

## Pužití
```
procedura(hodnota/proměnná);
```

### Předávání parametrů
- pořadím
```sql
procedura(1, 2);
```
- názvem
```sql
procedura(p_a => 1, p_b => 2);
```
- kombinovaný - jak se člověku zachce (pozor nejdřív dle pořadí, pak názvem - jako klasicky)
```sql
procedura(1, p_b => 2);
```

## Recap
- **Combination Notation** - (kombinovaný zápis)
- **IN parameter** - (IN parametr)
- **IN OUT parameter** - (parametr IN OUT)
- **Named Notation** - (jmenný zápis)
- **OUT parameter** - (OUT parametr)
- **Positional Notation** - (zápis pořadím)

<center>
    <img src="./assets/giphy.gif">
</center>