а# C# – kompletní zápisky

> Stručný přehled všech témat z dodaného materiálu. U každého tématu jsou základní pojmy, důležitá syntaxe a nejčastější chyby.

## Obsah

### 1. Základy jazyka a práce s konzolí
1. [Vstupy a výstupy](#1-vstupy-a-výstupy)
2. [Proměnné a datové typy](#2-proměnné-a-datové-typy)
3. [Operátory a výpočty](#3-operátory-a-výpočty)
4. [Podmínky – if, else, else if](#4-Podmínky-if-else-else-if)
5. [Podmínka switch](#5-podmínka-switch) 
6. [Cyklus for](#6-cyklus-for)
7. [Cykly while a do-while](#7-cykly-while-a-do-while)
8. [Generování náhodných čísel](#8-generování-náhodných-čísel)
9. [Funkce](#9-funkce)
10. [Procedury](#10-procedury)
11. [Řetězce a práce s textem](#11-řetězce-a-práce-s-textem)
12. [Jednorozměrná pole](#12-jednorozměrná-pole)
13. [Textové soubory](#13-textové-soubory)
14. [Vícerozměrná pole – matice](#14-vícerozměrná-pole-matice)
15. [Struktury – struct](#15-struktury-struct)
16. [Výčtový typ – enum](#16-výčtový-typ-enum)
17. [Datum a čas](#17-datum-a-čas)

### 2. Objektově orientované programování
18. [Třída](#18-třída)
19. [Objekt a reference](#19-objekt-a-reference)
20. [Datové členy třídy](#20-datové-členy-třídy)
21. [Vlastnosti a zapouzdření](#21-vlastnosti-a-zapouzdření)
22. [Metody třídy](#22-metody-třídy)
23. [Konstruktory](#23-konstruktory)
24. [Destruktory, GC a IDisposable](#24-destruktory-gc-a-idisposable)
25. [Přístupové modifikátory](#25-přístupové-modifikátory)
26. [Statické členy – static](#26-statické-členy-static)
27. [Výjimky – try/catch](#27-výjimky-trycatch)
28. [Abstrakce objektů a UML](#28-abstrakce-objektů-a-uml)
29. [Dědičnost](#29-dědičnost)
30. [Polymorfismus](#30-polymorfismus)
31. [Přetěžování operátorů](#31-přetěžování-operátorů)
32. [Rozhraní – interface](#32-rozhraní-interface)
33. [Delegáti, lambda výrazy a události](#33-delegáti-lambda-výrazy-a-události)

### 3. Kolekce a pokročilejší témata
34. [Seznam – List a ArrayList](#34-seznam-list-a-arraylist)
35. [Slovník – Dictionary](#35-slovník-dictionary)
36. [Další datové struktury](#36-další-datové-struktury)
37. [Genericita a generické metody](#37-genericita-a-generické-metody)

---

# 1. Vstupy a výstupy

## Základní pojmy
- **Programovací jazyk** – prostředek pro zápis algoritmů, které počítač provádí.
- **Zdrojový kód** – čitelné příkazy napsané programátorem.
- **Strojový kód** – binární instrukce vykonávané procesorem.
- **Překlad kódu** – převod zdrojového kódu na strojový (kompilace nebo interpretace).
- **IDE** – vývojové prostředí s nástroji pro tvorbu programu.

## Základní konzolové příkazy

```csharp
Console.WriteLine("Text");  // vypíše text a přejde na nový řádek
Console.Write("Text");      // vypíše text bez přechodu na nový řádek
string vstup = Console.ReadLine(); // načte řádek textu od uživatele
Console.ReadLine();          // může také počkat na Enter
```

`Console.ReadLine()` vrací vždy text (`string`), i když uživatel zadá číslo.

## Řídicí (escape) sekvence
Zapisují se pomocí zpětného lomítka `\`:

| Zápis | Význam | Příklad |
|---|---|---|
| `\n` | nový řádek | `"Ahoj\nsvěte"` |
| `\t` | tabulátor | `"Jméno:\tKarel"` |
| `\\` | zpětné lomítko | `"C:\\Skola"` |
| `\"` | uvozovka uvnitř textu | `"Řekl: \"Ahoj\""` |

Doslovný řetězec s `@` bere zpětná lomítka doslova: `@"C:\Skola\Programovani"`.

## Výpis proměnných
Text lze spojovat operátorem `+`:

```csharp
Console.WriteLine("Ahoj " + jmeno + "!");
```

Přehlednější je **interpolace** – před uvozovky se napíše `$` a proměnné se vloží do `{ }`:

```csharp
Console.WriteLine($"Ahoj {jmeno}!");
```

> **Pozor:** C# rozlišuje velká a malá písmena. Piš `Console.WriteLine`, ne `console.writeline`. Příkaz ukonči středníkem. Bez `$` se `{jmeno}` vypíše doslova.
Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/operators/arithmetic-operators).

---

# 2. Proměnné a datové typy

## Základní pojmy
- **Proměnná** – pojmenované místo v paměti, jehož hodnota se může měnit.
- **Datový typ** – určuje, jaké hodnoty proměnná uchovává.
- **Deklarace** – vytvoření proměnné, např. `int vek;`.
- **Inicializace** – první přiřazení hodnoty, např. `int vek = 17;`.
- **Přiřazení** – uložení nové hodnoty pomocí `=`, např. `vek = 18;`.
- **Literál** – hodnota zapsaná přímo v kódu, např. `17`, `3.14`, `'A'`, `"Ahoj"`, `true`.
- **Konstanta** – hodnota, kterou po deklaraci nelze změnit (`const`).

## Základní datové typy

| Typ | Co uchovává | Příklad |
|---|---|---|
| `int` | celé číslo (přibližně ±2,1 miliardy) | `int pocet = 28;` |
| `long` | velké celé číslo | `long obyvatel = 8100000000;` |
| `double` | desetinné číslo (asi 15–16 platných číslic) | `double vyska = 1.82;` |
| `decimal` | přesnější desetinné číslo, vhodné pro peníze | `decimal cena = 199.90m;` |
| `bool` | `true` nebo `false` | `bool aktivni = true;` |
| `char` | jeden znak v apostrofech | `char skupina = 'A';` |
| `string` | text v uvozovkách | `string jmeno = "Petra";` |

Desetinná čísla se v kódu píší s **tečkou**. V českém nastavení Windows uživatel obvykle zadává desetinná čísla s **čárkou**. Literál `decimal` potřebuje příponu `m`.

## Názvy proměnných
- Mohou obsahovat písmena, číslice a `_`, nesmí začínat číslicí.
- Nesmí jít o klíčové slovo (`int`, `class` apod.).
- `vek` a `Vek` jsou dvě různé proměnné.
- Používej výstižné názvy ve stylu **camelCase**: `cenaCelkem`, `pocetZaku`. Bez diakritiky.

## `var` a `const`

```csharp
var mesto = "Kroměříž"; // překladač odvodí string
var pocet = 25;         // překladač odvodí int

const double DPH = 0.21;
const int MaxPocetZaku = 30;
```

`var` musí být hned inicializováno. `const` má neměnnou hodnotu známou už při překladu; názvy konstant se často píší PascalCase nebo velkými písmeny u zkratek.

## Načtení čísla a převody

```csharp
string text = Console.ReadLine();
int vek = int.Parse(text);
double vyska = double.Parse(text);
int pocet = Convert.ToInt32(text);
```

| Převod | Výsledek / význam |
|---|---|
| `double d = cele;` | automatický převod `int` → `double` |
| `(int)7.9` | `7` – desetinná část se odsekne směrem k nule |
| `Math.Round(7.9)` | `8` – zaokrouhlení |
| `Convert.ToInt32(7.9)` | `8` – zaokrouhlení |
| `vek.ToString()` | převede hodnotu na text |

`Math.Round()` a `Convert.ToInt32()` při přesné polovině (např. `6.5`) standardně zaokrouhlují k nejbližšímu sudému číslu. Školní zaokrouhlení zajistí:

```csharp
Math.Round(cislo, MidpointRounding.AwayFromZero);
```

> **Časté chyby:** `Console.ReadLine()` není číslo, musí se převést. `char` používá apostrofy (`'A'`), `string` uvozovky (`"A"`). `"5" + 5` vytvoří text `"55"`, nikoli součet. `decimal cena = 19.90;` je chyba – správně `19.90m`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/builtin-types/built-in-types).

---

# 3. Operátory a výpočty

## Aritmetické operátory

| Operátor | Význam | Příklad |
|---|---|---|
| `+` | sčítání; u textů spojování | `7 + 2` → `9` |
| `-` | odčítání | `7 - 2` → `5` |
| `*` | násobení | `7 * 2` → `14` |
| `/` | dělení | `7 / 2` → `3` |
| `%` | zbytek po celočíselném dělení | `7 % 2` → `1` |

## Celočíselné a desetinné dělení
- Dva celočíselné operandy → celočíselný výsledek: `7 / 2` je `3`, `1 / 3` je `0`.
- Alespoň jeden desetinný operand → desetinné dělení: `7 / 2.0` je `3.5`.
- Pro desetinný průměr přetypuj alespoň jeden operand: `(double)soucet / pocet`.

Operátor `%` vrací zbytek. Použití: sudé číslo `x % 2 == 0`, poslední číslice `x % 10`, převod minut na hodiny a minuty.

```csharp
int celkemMinut = 200;
int hodiny = celkemMinut / 60; // 3
int minuty = celkemMinut % 60; // 20
```

## Zkrácené zápisy

| Zápis | Ekvivalent |
|---|---|
| `x++` | `x = x + 1` |
| `x--` | `x = x - 1` |
| `x += 5` | `x = x + 5` |
| `x -= 5` | `x = x - 5` |
| `x *= 2` | `x = x * 2` |
| `x /= 2` | `x = x / 2` |
| `x %= 3` | `x = x % 3` |

`a++` nejprve vrátí původní hodnotu a potom zvýší `a`; `++a` nejprve zvýší a vrátí novou hodnotu. Rozdíl se projeví ve větším výrazu.

## Priorita operátorů
1. Závorky `( )`
2. Unární operátory (`++`, `--`, `-x`, `(int)x`)
3. `*`, `/`, `%`
4. `+`, `-`
5. Přiřazení (`=`, `+=`, `-=` …)

Operátory stejné priority se vyhodnocují zleva doprava. Používej závorky, když si nejsi jistý.

## Třída `Math`

| Metoda / konstanta | Význam |
|---|---|
| `Math.Pow(x, y)` | mocnina `x` na `y` |
| `Math.Sqrt(x)` | druhá odmocnina |
| `Math.Abs(x)` | absolutní hodnota |
| `Math.Round(x, n)` | zaokrouhlení na `n` desetinných míst |
| `Math.Floor(x)` | zaokrouhlení dolů |
| `Math.Ceiling(x)` | zaokrouhlení nahoru |
| `Math.Max(a, b)` / `Math.Min(a, b)` | větší / menší číslo |
| `Math.PI` | konstanta π |

Metody `Pow`, `Sqrt`, `Floor` a `Ceiling` vracejí `double`.

## Formátování výstupu
- `{x:F2}` – vždy dvě desetinná místa, např. `5.00`.
- `{x:F0}`, `{x:F1}`, `{x:F3}` – jiné počty desetinných míst.
- `{x:D2}` – celé číslo doplněné zleva nulami, např. `7` → `07`.

Formátování mění pouze výpis, nikoli hodnotu proměnné.

> **Pozor:** `^` není mocnina. Pro mocninu použij `Math.Pow(x, 2)` nebo `x * x`. Záměna `x += 5` a `x =+ 5` je častá chyba; druhý zápis přiřadí kladnou pětku.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/operators/arithmetic-operators).

---

# 4. Podmínky if, else, else if

**Podmínka** je logický výraz s výsledkem `true` nebo `false`. Podle výsledku program zvolí, který blok kódu provede.

## Porovnávací operátory

| Operátor | Význam |
|---|---|
| `==` | rovná se |
| `!=` | nerovná se |
| `<`, `>` | menší, větší |
| `<=`, `>=` | menší nebo rovno, větší nebo rovno |

## Logické operátory

| Operátor | Význam | Kdy je výsledek `true` |
|---|---|---|
| `&&` | AND – a zároveň | platí obě podmínky |
| `\|\|` | OR – nebo | platí alespoň jedna |
| `!` | NOT – negace | podmínka neplatí |

## Zápis

```csharp
if (vek >= 18)
{
    Console.WriteLine("Jste plnoletý.");
}
else
{
    Console.WriteLine("Nejste plnoletý.");
}
```

Více možností:

```csharp
if (teplota < 0)
{
    Console.WriteLine("Mrzne.");
}
else if (teplota < 20)
{
    Console.WriteLine("Je chladno.");
}
else
{
    Console.WriteLine("Je teplo.");
}
```

Podmínky `else if` se kontrolují shora dolů a provede se první splněná větev. Nejdříve proto testuj přísnější podmínky.

> **Pozor:** `=` přiřazuje, `==` porovnává. Za `if (podminka)` nepiš středník. Rozsah 1 až 5 zapiš `x >= 1 && x <= 5`, nikoli `1 <= x <= 5`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/statements/selection-statements).

---

# 5. Podmínka switch

`switch` je vícenásobné větvení podle jedné hodnoty. Hodí se pro menu, dny v týdnu, měsíce nebo typ operace.

- `case` – konkrétní hodnota.
- `break` – ukončí aktuální větev `switch`.
- `default` – provede se, pokud neodpovídá žádný `case` (obdoba `else`).

```csharp
switch (volba)
{
    case 1:
        Console.WriteLine("Káva");
        break;
    case 2:
        Console.WriteLine("Čaj");
        break;
    default:
        Console.WriteLine("Neplatná volba");
        break;
}
```

- Výraz může být `int`, `char`, `string`, `bool` nebo výčtový typ.
- Každá větev musí skončit `break`, `return` nebo jiným ukončením větve.
- Více hodnot lze seskupit několika `case` pod sebou.
- Text rozlišuje velká a malá písmena (`"A"` není `"a"`).

## Switch výraz (C# 8+)
Používá se pro výběr hodnoty. Větve se zapisují `hodnota => výsledek`, oddělují se čárkou a výchozí větev je `_`.

```csharp
string obdobi = mesic switch
{
    12 or 1 or 2 => "zima",
    3 or 4 or 5 => "jaro",
    6 or 7 or 8 => "léto",
    9 or 10 or 11 => "podzim",
    _ => "neplatný měsíc"
};
```

> **Pozor:** V běžném `switch` se píše `case 1:` (dvojtečka), ve switch výrazu se větve oddělují čárkami. Nezapomeň na středník za ukončovací závorkou switch výrazu.

Více informací: [Microsoft Learn (if, switch)](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/statements/selection-statements), [Microsoft Learn (switch)](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/operators/switch-expression).
Více informací: [Microsoft Learn]().

---

# 6. Cyklus for

**Cyklus** opakovaně provádí blok příkazů. `for` se používá, když je počet opakování známý nebo ho lze určit předem.

```csharp
for (int i = 1; i <= 5; i++)
{
    Console.Write(i + " "); // 1 2 3 4 5
}
```

Hlavička má tři části:
1. **Inicializace** – provede se jednou na začátku (`int i = 1`).
2. **Podmínka** – kontroluje se před každým průchodem (`i <= 5`).
3. **Změna** – provede se po průchodu (`i++`).

## Varianty

```csharp
for (int i = 5; i >= 1; i--)  // sestupně
    Console.Write(i + " ");

for (int i = 1; i <= 9; i += 2) // lichá čísla
    Console.Write(i + " ");

for (int i = 0; i < n; i++) // přesně n opakování
    Console.WriteLine("Ahoj!");
```

## Součet a počítadlo
Součet a počet nastav před cyklem na nulu:

```csharp
int soucet = 0;
int pocet = 0;
for (int i = 1; i <= 100; i++)
{
    soucet += i;
    if (i % 7 == 0)
        pocet++;
}
```

## Vnořené cykly
Vnitřní cyklus proběhne celý při každém průchodu vnějšího. Vnější cyklus obvykle řídí řádky, vnitřní sloupce.

```csharp
for (int radek = 1; radek <= 3; radek++)
{
    for (int sloupec = 1; sloupec <= 4; sloupec++)
        Console.Write("# ");
    Console.WriteLine();
}
```

> **Pozor:** Středník hned za hlavičkou `for` vytvoří prázdný cyklus. Dávej pozor na `i < n` versus `i <= n`, na směr změny a na to, aby se součet nevynuloval uvnitř cyklu.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/statements/iteration-statements).

---

# 7. Cykly while a do-while

Používají se, když předem neznáme počet opakování.

| Cyklus | Kdy testuje podmínku | Použití |
|---|---|---|
| `for` | před každým průchodem | počet opakování známe |
| `while` | na začátku | tělo může proběhnout 0× |
| `do-while` | na konci | tělo proběhne alespoň 1× |

## while

```csharp
int cislo = 1;
while (cislo <= 100)
{
    Console.Write(cislo + " ");
    cislo *= 2; // změna řídicí proměnné
}
```

## do-while

```csharp
string odpoved;
do
{
    Console.Write("Pokračovat? (A/N): ");
    odpoved = Console.ReadLine();
} while (odpoved != "A" && odpoved != "N");
```

Za podmínkou `while (...)` v konstrukci `do-while` musí být středník.

## break a continue
- `break` – okamžitě ukončí celý cyklus.
- `continue` – přeskočí zbytek aktuálního průchodu a pokračuje dalším testem podmínky.

`break` uvnitř `switch` ukončí pouze `switch`, ne okolní cyklus.

## Bezpečný převod – TryParse

```csharp
Console.Write("Zadejte věk: ");
string vstup = Console.ReadLine();
if (int.TryParse(vstup, out int vek))
    Console.WriteLine($"Příští rok vám bude {vek + 1}.");
else
    Console.WriteLine("To není celé číslo!");
```

`TryParse` vrátí `true` nebo `false`; převedenou hodnotu uloží do proměnné za `out`. Při neúspěchu program nespadne.

> **Nekonečný cyklus:** Pokud se v těle nemění proměnná, která ovlivňuje podmínku, cyklus nemusí skončit. Pozor také na `continue` umístěné před zvýšení řídicí proměnné.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/statements/iteration-statements).

---

# 8. Generování náhodných čísel

Počítač vytváří **pseudonáhodná čísla** – posloupnost počítá algoritmus, ale vypadá náhodně. Generátor je objekt třídy `Random`.

```csharp
Random rnd = new Random(); // vytvoř jednou, mimo cyklus
int hod = rnd.Next(1, 7);   // celé číslo 1 až 6
```

| Zápis | Výsledek |
|---|---|
| `rnd.Next()` | nezáporné celé číslo |
| `rnd.Next(10)` | `0` až `9` |
| `rnd.Next(1, 7)` | `1` až `6` |
| `rnd.Next(-5, 6)` | `-5` až `5` |
| `rnd.NextDouble()` | desetinné číslo od `0` včetně do `1` bez `1` |
| `10 + rnd.NextDouble() * 20` | od `10` včetně do `30` bez `30` |

**Důležité:** U `Next(min, max)` je dolní mez zahrnuta, horní nikoli. Pro celé číslo od `min` do `max` včetně použij `Next(min, max + 1)`.

```csharp
Random testovaci = new Random(42); // stejné semínko = stejná posloupnost
int hod = Random.Shared.Next(1, 7); // sdílený generátor (.NET 6+)
```

`NextDouble() < 0.3` nastane přibližně ve 30 % případů.

> **Pozor:** `rnd.Next(1, 6)` nikdy nevrátí šestku. Nevytvářej nový `Random` pro každé číslo uvnitř cyklu. `NextDouble() * 6` není hod kostkou – vrací desetinné číslo.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/api/system.random).

---

# 9. Funkce

**Funkce** je pojmenovaná část programu, která provede výpočet a **vrátí výsledek**.

- **Parametr** – proměnná v hlavičce funkce, přes kterou přijímá vstup.
- **Argument** – konkrétní hodnota předaná při volání.
- **Návratový typ** – typ výsledku (`int`, `double`, `bool`, `string` …).
- **`return`** – ukončí funkci a vrátí hodnotu.
- **Lokální proměnná** – existuje jen uvnitř funkce.

## Syntaxe a použití

```csharp
static double ObvodKruhu(double r)
{
    return 2 * Math.PI * r;
}

double obvod = ObvodKruhu(2.5); // 2.5 je argument
Console.WriteLine($"Obvod: {obvod:F2}");
```

Funkci lze volat ve výrazu, podmínce, výpisu nebo přiřazení.

```csharp
static int Vetsi(int a, int b)
{
    if (a > b)
        return a;
    return b;
}

static bool JeSude(int n)
{
    return n % 2 == 0;
}
```

Funkce vracející `bool` se hodí do podmínky: `if (JeSude(cislo)) { ... }`.

## Rekurze
Rekurze = funkce volá sama sebe. **Musí mít ukončovací podmínku**, jinak skončí chybou `StackOverflowException`.

```csharp
static long Faktorial(int n)
{
    if (n <= 1)
        return 1;
    return n * Faktorial(n - 1);
}
```

Rekurze bývá elegantní, ale jednoduché úlohy lze často řešit rychleji a bezpečněji cyklem.

> **Pozor:** Každá možná cesta funkcí musí vrátit hodnotu. Kód za `return` se už neprovede. Statická lokální funkce nevidí proměnné hlavního programu – předej jí je jako argumenty.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/classes-and-structs/local-functions).

---

# 10. Procedury

**Procedura** provede činnost, ale nevrací hodnotu. Její návratový typ je `void`.

```csharp
static void VypisNadpis(string text)
{
    Console.WriteLine("=== " + text + " ===");
}

VypisNadpis("Rozvrh hodin");
```

Proceduru lze předčasně ukončit příkazem `return;` bez hodnoty.

## Předání parametru

| Způsob | Hlavička / volání | Předem musí mít hodnotu? | Musí procedura přiřadit? | Změní se původní proměnná? |
|---|---|---:|---:|---:|
| hodnotou | `int x` / `Proc(a)` | ano | ne | ne |
| odkazem | `ref int x` / `Proc(ref a)` | ano | ne | ano |
| výstupem | `out int x` / `Proc(out a)` | ne | ano | ano |

### `ref` – změna původní proměnné

```csharp
int body = 10;
PridejBonus(ref body);

static void PridejBonus(ref int b)
{
    b += 5;
}
```

### `out` – vrácení více výsledků

```csharp
Vydel(17, 5, out int podil, out int zbytek);

static void Vydel(int a, int b, out int podil, out int zbytek)
{
    podil = a / b;
    zbytek = a % b;
}
```

Každému parametru `out` musí procedura přiřadit hodnotu.

### Volitelné parametry
Parametr s výchozí hodnotou lze při volání vynechat. Volitelné parametry musí být až za povinnými.

```csharp
static void VykresliCaru(int delka = 20, char znak = '-')
{
    for (int i = 0; i < delka; i++)
        Console.Write(znak);
    Console.WriteLine();
}

VykresliCaru();       // 20 pomlček
VykresliCaru(5);      // 5 pomlček
VykresliCaru(5, '*'); // 5 hvězdiček
```

> **Pozor:** `ref` a `out` musí být v hlavičce i při volání. Proměnná pro `ref` musí být předem inicializovaná. Procedura `void` nic nevrací, její výsledek nelze uložit do proměnné.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/keywords/method-parameters).

---

# 11. Řetězce a práce s textem

**Řetězec (`string`)** je posloupnost znaků `char`. Text se píše do uvozovek, jeden znak do apostrofů. Indexy začínají nulou.

- První znak: `text[0]`.
- Poslední znak: `text[text.Length - 1]`.
- Délka: `text.Length`.
- Prázdný řetězec: `""`.
- Řetězce jsou **neměnné** – metody vracejí nový text, který je potřeba uložit.

## Nejdůležitější vlastnosti a metody
Příklad: `string text = "Ahoj světe";`

| Zápis | Význam |
|---|---|
| `text.Length` | počet znaků |
| `text[0]` | znak na indexu 0 |
| `text.ToUpper()` / `ToLower()` | velká / malá písmena |
| `text.Contains("svět")` | obsahuje podřetězec? |
| `text.StartsWith("Ah")` / `EndsWith(...)` | začíná / končí textem? |
| `text.IndexOf('s')` | index prvního výskytu; `-1`, pokud nenalezen |
| `text.Replace("světe", "Brno")` | nahradí výskyty |
| `text.Substring(5)` | část od indexu 5 do konce |
| `text.Substring(0, 4)` | část od indexu 0 o délce 4 |
| `text.Trim()` | odstraní mezery na začátku a konci |
| `text.Split(' ')` | rozdělí text na části |
| `string.Join(", ", pole)` | spojí části oddělovačem |

## Práce se znaky

```csharp
foreach (char znak in slovo)
    Console.Write(znak);

for (int i = slovo.Length - 1; i >= 0; i--)
    Console.Write(slovo[i]); // pozpátku
```

Metody `char`:
- `char.IsLetter(z)` – je písmeno?
- `char.IsDigit(z)` – je číslice?
- `char.IsWhiteSpace(z)` – je bílý znak / mezera?
- `char.IsUpper(z)` / `char.IsLower(z)` – je velké / malé?
- `char.ToUpper(z)` / `char.ToLower(z)` – převede velikost písmena.

## Rozdělení textu

```csharp
string veta = "Jan   Amos Komenský";
string[] slova = veta.Split(' ', StringSplitOptions.RemoveEmptyEntries);
Console.WriteLine(slova.Length);             // 3
Console.WriteLine(string.Join(", ", slova)); // Jan, Amos, Komenský
```

`RemoveEmptyEntries` vynechá prázdné části vzniklé více oddělovači za sebou.

## StringBuilder
Pro skládání dlouhého textu v cyklu je `StringBuilder` efektivnější než opakované `+=`, protože nevytváří při každém přidání nový řetězec. Je potřeba `using System.Text;`.

```csharp
using System.Text;
StringBuilder sb = new StringBuilder();
sb.Append("Ahoj");
sb.Append(' ');
sb.Append("světe");
string vysledek = sb.ToString();
```

> **Pozor:** `text.ToUpper();` samo o sobě text nezmění – ulož `text = text.ToUpper();`. Index posledního znaku je `Length - 1`. U `Substring(start, delka)` je druhý parametr délka, nikoli koncový index. Rozlišuj `'a'` a `"a"`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/strings/).

---

# 12. Jednorozměrná pole

**Pole** uchovává více hodnot stejného datového typu pod jedním názvem.
- Indexy začínají od `0`.
- Počet prvků zjistíš pomocí `Length`.
- Velikost pole je po vytvoření pevná.
- Výchozí prvky: čísla `0`, `bool` `false`, referenční typy (např. `string`) `null`.

## Vytvoření pole

```csharp
int[] znamky = new int[5];
double[] ceny = { 19.90, 45.50, 12.00 };
string[] dny = { "Po", "Út", "St", "Čt", "Pá" };

int n = int.Parse(Console.ReadLine());
int[] cisla = new int[n];
```

## Práce s prvky

```csharp
znamky[0] = 1;                 // první prvek
znamky[4] = 3;                 // pátý prvek
Console.WriteLine(dny[1]);     // Út
Console.WriteLine(dny.Length); // 5
Console.WriteLine(dny[dny.Length - 1]); // poslední prvek
```

## Procházení
- `for` – máš index, prvky lze číst i měnit.
- `foreach` – projde všechny prvky bez indexu; proměnná cyklu se používá pro čtení.

```csharp
int soucet = 0;
for (int i = 0; i < znamky.Length; i++)
    soucet += znamky[i];

foreach (int z in znamky)
    Console.WriteLine(z);
```

## Typické algoritmy

**Maximum:**

```csharp
int max = cisla[0];
for (int i = 1; i < cisla.Length; i++)
    if (cisla[i] > max)
        max = cisla[i];
```

**Lineární hledání:**

```csharp
int index = -1;
for (int i = 0; i < cisla.Length; i++)
{
    if (cisla[i] == hledane)
    {
        index = i;
        break;
    }
}
```

`-1` znamená, že hodnota nebyla nalezena.

**Prohození dvou prvků:**

```csharp
int pomocna = pole[i];
pole[i] = pole[i + 1];
pole[i + 1] = pomocna;
```

**Bublinkové řazení:** porovnává sousední prvky a prohazuje je, jsou-li ve špatném pořadí. Po každém kole se největší prvek dostane na konec.

```csharp
for (int kolo = 0; kolo < pole.Length - 1; kolo++)
    for (int i = 0; i < pole.Length - 1 - kolo; i++)
        if (pole[i] > pole[i + 1])
        {
            int pom = pole[i];
            pole[i] = pole[i + 1];
            pole[i + 1] = pom;
        }
```

## Hotové metody
- `Array.Sort(pole)` – seřadí vzestupně.
- `Array.Reverse(pole)` – obrátí pořadí.
- `Array.IndexOf(pole, hodnota)` – najde index, nebo vrátí `-1`.
- `string.Join(", ", pole)` – vypíše prvky jako text.

Pole je **referenční typ**. Předání pole do metody zpřístupní stejné pole, takže změny jeho prvků se projeví i mimo metodu.

> **Pozor:** Používej `i < pole.Length`, nikoli `i <= pole.Length`. První index je 0, poslední `Length - 1`. `Length` nemá závorky. `Console.WriteLine(pole)` nevypíše jednotlivé prvky; použij cyklus nebo `string.Join`. Průměr počítej desetinně: `(double)soucet / pole.Length`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/builtin-types/arrays).

---

# 13. Textové soubory

**Soubor** uchovává data na disku, takže zůstanou i po ukončení programu.
- **Textový soubor** obsahuje čitelné znaky (`.txt`, `.csv`, `.html`, `.cs`).
- **Binární soubor** obsahuje bajty, např. obrázek, hudbu nebo `.exe`.
- **Kódování** převádí znaky na bajty. Doporučené je UTF-8, které podporuje i českou diakritiku.
- **Absolutní cesta** začíná od kořene disku (`C:\data\soubor.txt`).
- **Relativní cesta** je vzhledem k pracovní složce programu (`data\soubor.txt`).

## Cesty k souborům

```csharp
string cesta1 = "C:\\data\\soubor.txt"; // zdvojená lomítka
string cesta2 = @"C:\data\soubor.txt";    // doslovný řetězec
string cesta3 = Path.Combine("data", "soubor.txt");
```

Při spuštění z Visual Studia bývá pracovní složkou například `bin\Debug\net8.0`. Zjistíš ji takto:

```csharp
Console.WriteLine(Directory.GetCurrentDirectory());
```

## Třída File – celý soubor najednou

| Metoda | Význam |
|---|---|
| `File.WriteAllText(cesta, text)` | zapíše text; existující soubor přepíše |
| `File.AppendAllText(cesta, text)` | připíše text na konec |
| `File.ReadAllText(cesta)` | načte celý soubor jako řetězec |
| `File.WriteAllLines(cesta, pole)` | zapíše každý prvek pole na řádek |
| `File.ReadAllLines(cesta)` | načte řádky do pole řetězců |
| `File.Exists(cesta)` | ověří existenci souboru |

```csharp
File.WriteAllText("pozdrav.txt", "Ahoj světe!");
File.AppendAllText("pozdrav.txt", Environment.NewLine + "Druhý řádek");
string obsah = File.ReadAllText("pozdrav.txt");
```

`Environment.NewLine` vloží konec řádku podle operačního systému.

## StreamReader a StreamWriter
Používají se pro postupné čtení a zápis, například po řádcích. Blok `using` soubor automaticky zavře i při chybě.

```csharp
using (StreamWriter zapisovac = new StreamWriter("ctverce.txt"))
{
    for (int i = 1; i <= 5; i++)
        zapisovac.WriteLine(i * i);
}

using (StreamReader ctenar = new StreamReader("ctverce.txt"))
{
    while (!ctenar.EndOfStream)
    {
        string radek = ctenar.ReadLine();
        Console.WriteLine(radek);
    }
}
```

`new StreamWriter(cesta)` soubor přepíše; `new StreamWriter(cesta, true)` připisuje na konec. `ReadLine()` na konci souboru vrátí `null`.

## Ošetření chyb při práci se soubory

```csharp
try
{
    string text = File.ReadAllText("data.txt");
}
catch (FileNotFoundException)
{
    Console.WriteLine("Soubor neexistuje.");
}
catch (UnauthorizedAccessException)
{
    Console.WriteLine("Nemáte přístupová práva.");
}
catch (IOException ex)
{
    Console.WriteLine($"Chyba souboru: {ex.Message}");
}
```

Časté výjimky: `FileNotFoundException` – soubor neexistuje; `DirectoryNotFoundException` – chybí složka; `UnauthorizedAccessException` – chybí oprávnění; `IOException` – obecná chyba vstupu/výstupu.

> **Pozor:** `WriteAllText` přepíše původní obsah; pro připsání použij `AppendAllText`. Nezapomeň na konec řádku při přidávání. U `StreamWriter` a `StreamReader` používej `using`. Relativní cesta se nehledá vedle `Program.cs`, ale v pracovní složce programu.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/standard/io/).

---

# 14. Vícerozměrná pole – matice

**Matice** je pole s více indexy, nejčastěji dvourozměrná tabulka.
- Prvek se zapisuje `[radek, sloupec]`.
- Indexy začínají od nuly.
- `GetLength(0)` vrací počet řádků.
- `GetLength(1)` vrací počet sloupců.
- `Length` vrací celkový počet všech prvků.

## Vytvoření a práce s maticí

```csharp
int[,] matice = new int[2, 3];
int[,] hodnoty =
{
    { 1, 2, 3 },
    { 4, 5, 6 }
};

Console.WriteLine(hodnoty[0, 1]); // 2
hodnoty[1, 2] = 60;
Console.WriteLine(hodnoty.GetLength(0)); // 2 řádky
Console.WriteLine(hodnoty.GetLength(1)); // 3 sloupce
```

## Procházení vnořenými cykly
Vnější cyklus prochází řádky, vnitřní sloupce.

```csharp
for (int r = 0; r < matice.GetLength(0); r++)
{
    for (int s = 0; s < matice.GetLength(1); s++)
        Console.Write($"{matice[r, s],4}");
    Console.WriteLine();
}
```

Zápis `{hodnota,4}` zarovná hodnotu doprava na šířku 4 znaků; `{text,-10}` zarovná doleva.

## Typické úlohy
- Součet řádku: cyklus přes sloupce, `soucet += m[r, s]`.
- Součet sloupce: cyklus přes řádky.
- Hlavní diagonála čtvercové matice: prvky `m[i, i]`.
- Transpozice: řádky se změní na sloupce; nová matice má rozměry `[sloupce, řádky]` a platí `t[s, r] = m[r, s]`.
- `foreach (int x in m)` projde všechny prvky po řádcích, ale bez indexů.

## Zubaté pole `int[][]`
Je to pole samostatných polí; každý řádek může mít jinou délku. Přístup je `z[i][j]`, délka řádku `z[i].Length`.

```csharp
int[][] znamky = new int[3][];
znamky[0] = new int[] { 1, 2 };
znamky[1] = new int[] { 3, 1, 1, 2 };
znamky[2] = new int[] { 2 };
```

> **Pozor:** Matice `int[,]` používá `m[r, s]`; zubaté pole `int[][]` používá `z[r][s]`. Nezaměň `GetLength(0)` a `GetLength(1)`. `Length` u matice není počet řádků.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/builtin-types/arrays).


---

# 15. Struktury – struct

**Struktura (`struct`)** je vlastní datový typ, který seskupuje související hodnoty, např. bod `(x, y)` nebo zboží (název, cena, počet).

- Datové položky se uvnitř struktury označí `public`, pokud mají být dostupné zvenku.
- Struktura je **hodnotový typ** – při přiřazení nebo předání parametru vznikne kopie.
- `int`, `double`, `bool`, `char`, `DateTime` jsou také hodnotové typy.
- Pole a třídy jsou referenční typy – proměnná uchovává odkaz.

## Deklarace a použití

```csharp
struct Bod
{
    public double X;
    public double Y;
}

Bod a = new Bod();
a.X = 3;
a.Y = 4;
Console.WriteLine($"[{a.X}; {a.Y}]");
```

V programu s příkazy nejvyšší úrovně se deklarace `struct` píše až za hlavní kód a lokální funkce.

## Struktura jako parametr a návratová hodnota

Při běžném předání dostane funkce kopii. Původní proměnnou lze změnit přes `ref` nebo vrátit upravenou strukturu:

```csharp
static Bod Posun(Bod p, double o)
{
    p.X += o;
    p.Y += o;
    return p;
}
```

## Pole struktur

```csharp
Zbozi[] kosik = new Zbozi[3];
kosik[0].Nazev = "Sešit";

struct Zbozi
{
    public string Nazev;
    public int Cena;
    public int Pocet;
}
```

**Struktura vs. třída:** `struct` se hodí pro malé jednoduché skupiny hodnot; složitější objekty se popisují třídou (`class`).

> **Pozor:** Změna kopie struktury nezmění původní hodnotu. Pro změnu původní proměnné použij `ref`, nebo vrať novou strukturu. Při použití struktury bez `new` musíš přiřadit hodnotu všem položkám.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/builtin-types/struct).

---

# 16. Výčtový typ – enum

**Výčtový typ (`enum`)** omezuje proměnnou na předem vyjmenované pojmenované hodnoty. Zvyšuje přehlednost oproti „magickým číslům“.

```csharp
Den dnes = Den.Streda;
Console.WriteLine(dnes);      // Streda
Console.WriteLine((int)dnes); // číselná hodnota

enum Den
{
    Pondeli = 1,
    Utery,
    Streda,
    Ctvrtek,
    Patek,
    Sobota,
    Nedele
}
```

- Standardní číselné hodnoty začínají od 0; první lze nastavit ručně.
- Převod na číslo: `(int)Den.Patek`.
- Převod čísla na výčet: `(Den)6`.
- Převod na text: `den.ToString()`.
- Ověření platnosti: `Enum.IsDefined(typeof(Den), 9)`.
- S výčtem lze pracovat v `switch`.

> **Pozor:** Přetypování čísla na enum samo nekontroluje, zda člen existuje. Použij `Enum.IsDefined`. Při převodu enum → int je nutné explicitní přetypování.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/builtin-types/enum).

---

# 17. Datum a čas

## Základní typy
- `DateTime` – datum a čas; je hodnotovým typem.
- `TimeSpan` – časový interval, např. 14 dní nebo 1 hodina 30 minut.
- `DateTime.Now` – aktuální datum a čas.
- `DateTime.Today` – dnešní datum s časem 00:00:00.
- `Stopwatch` – měření doby běhu programu.

## Vytvoření a načtení data

```csharp
DateTime vanoce = new DateTime(2026, 12, 24);
DateTime zvoneni = new DateTime(2026, 9, 1, 8, 0, 0);
DateTime ted = DateTime.Now;
DateTime dnes = DateTime.Today;
DateTime narozeni = DateTime.Parse(Console.ReadLine());
```

`DateTime.Parse` čte datum podle místního nastavení. Bezpečnější je `DateTime.TryParse(text, out DateTime datum)`.

## Části data a úpravy

| Zápis | Význam |
|---|---|
| `datum.Year`, `.Month`, `.Day` | rok, měsíc, den |
| `datum.Hour`, `.Minute`, `.Second` | hodina, minuta, sekunda |
| `datum.DayOfWeek` | den v týdnu (`DayOfWeek`) |
| `datum.DayOfYear` | pořadí dne v roce |
| `datum.AddDays(7)` | datum posunuté o 7 dní |
| `datum.AddMonths(1)` / `AddYears(-1)` | posun o měsíce / roky |
| `DateTime.DaysInMonth(2024, 2)` | počet dní v měsíci |
| `DateTime.IsLeapYear(2024)` | je rok přestupný? |

`DateTime` je neměnný – metody `Add...` vracejí nové datum. Výsledek ulož: `datum = datum.AddDays(1);`.

`DayOfWeek` má hodnoty `Sunday` (0) až `Saturday` (6). Víkend ověříš např. takto:

```csharp
if (datum.DayOfWeek == DayOfWeek.Saturday ||
    datum.DayOfWeek == DayOfWeek.Sunday)
{
    Console.WriteLine("Je víkend!");
}
```

## TimeSpan – rozdíl dat

```csharp
TimeSpan rozdil = navrat - odjezd;
Console.WriteLine(rozdil.Days);       // celé dny
Console.WriteLine(rozdil.TotalDays);  // celá doba ve dnech jako desetinné číslo
Console.WriteLine(rozdil.TotalHours);
```

`Days` a `Hours` jsou části intervalu; `TotalDays` a `TotalHours` vyjadřují celou dobu.

## Formátování data

| Značka | Význam |
|---|---|
| `d`, `dd` | den, případně s nulou |
| `ddd`, `dddd` | zkratka / celý den v týdnu |
| `M`, `MM`, `MMMM` | měsíc číslem / s nulou / názvem |
| `yyyy` | rok |
| `H`, `HH` | hodina 0–23 |
| `mm` | minuty |
| `ss` | sekundy |

```csharp
Console.WriteLine(datum.ToString("dd.MM.yyyy"));
Console.WriteLine(datum.ToString("dddd"));
Console.WriteLine(datum.ToString("HH:mm"));
Console.WriteLine($"Dnes je {datum:dddd d. M. yyyy}");
```

Názvy dnů a měsíců se řídí jazykem Windows. `DayOfWeek.ToString()` vypisuje anglický název; formát `dddd` zobrazí lokalizovaný název.

## Stopwatch – měření času

```csharp
using System.Diagnostics;

Stopwatch stopky = Stopwatch.StartNew();
// měřená část programu
stopky.Stop();
Console.WriteLine($"Trvalo to {stopky.ElapsedMilliseconds} ms");
Console.WriteLine($"Trvalo to {stopky.Elapsed.TotalSeconds:F2} s");
```

> **Pozor:** Nezapomeň ukládat výsledek `AddDays()` a podobných metod. `MM` znamená měsíc, `mm` minuty; `HH` je hodina 0–23. Rozlišuj `Days` a `TotalDays`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/standard/base-types/custom-date-and-time-format-strings).

---

# 18. Třída

**Třída (`class`)** je šablona, která popisuje, jaká data a metody budou mít objekty. **Objekt** je konkrétní instance třídy vytvořená pomocí `new`.

- **OOP** – programování skládáním objektů, které mají data a chování.
- **Datový člen** – proměnná uvnitř třídy, uchovává stav objektu.
- **Metoda** – funkce nebo procedura uvnitř třídy, popisuje chování objektu.
- **`new`** – vytvoří nový objekt.

## Deklarace třídy

```csharp
class Pes
{
    public string Jmeno = "";
    public string Rasa = "";
    public int Vek;

    public void Stekej()
    {
        Console.WriteLine($"{Jmeno}: Haf haf!");
    }

    public int VekVLidskychLetech()
    {
        return Vek * 7;
    }
}
```

Název třídy se píše stylem **PascalCase**. `public` zpřístupňuje člen i mimo třídu. Metody, které patří konkrétním objektům, se píší bez `static`.

## Vytvoření objektu

```csharp
Pes pes1 = new Pes();
pes1.Jmeno = "Rex";
pes1.Vek = 4;
pes1.Stekej();
```

Každý objekt má vlastní hodnoty datových členů. Metoda zavolaná na `pes1` pracuje s daty objektu `pes1`.

## Kam třídu napsat
V programu s příkazy nejvyšší úrovně se deklarace třídy píše až za hlavní program a lokální funkce, obvykle na konec `Program.cs`. Ve větším projektu má každá třída vlastní soubor, například `Pes.cs` (Visual Studio → Přidat → Třída).

> **Pozor:** `Pes pes;` pouze deklaruje proměnnou. Objekt vytvoří až `new Pes()`. Bez `public` nemusí být člen přístupný z hlavního programu. Metodu objektu volej přes instanci, např. `pes1.Stekej();`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/fundamentals/types/classes).

---

# 19. Objekt a reference

**Reference** je odkaz na objekt uložený v paměti. Proměnná typu třída obsahuje odkaz, ne samotný objekt.

- **Referenční typy:** třídy, pole, `string`.
- **Hodnotové typy:** `int`, `double`, `bool`, `struct`, `enum`, `DateTime`.
- **`null`** – proměnná neodkazuje na žádný objekt.
- **Garbage collector (GC)** – automaticky uvolňuje paměť objektů, na které už nevede žádný odkaz.
- **`NullReferenceException`** – vznikne při použití členu nebo metody přes `null`.

## Přiřazení reference

```csharp
Auto a = new Auto();
a.Nazev = "Škoda";
Auto b = a;              // zkopíruje se pouze odkaz
b.Nazev = "Tesla";
Console.WriteLine(a.Nazev); // Tesla – a i b ukazují na stejný objekt

Auto c = new Auto();     // nový samostatný objekt
```

`a == b` u objektů porovnává, zda jde o stejný objekt (stejnou referenci), nikoli zda mají stejné hodnoty.

## Pole objektů

```csharp
Auto[] auta = new Auto[3]; // pole tří odkazů, všechny jsou zatím null
for (int i = 0; i < auta.Length; i++)
{
    auta[i] = new Auto();  // vytvoření každého objektu zvlášť
}
```

`new Auto[3]` vytvoří pouze pole, nikoli tři auta.

## Hodnota null

```csharp
Auto? auto = null;
if (auto == null)
    Console.WriteLine("Žádné auto.");

auto = new Auto();
```

`Auto?` říká, že proměnná může obsahovat `null`. Před použitím jejího členu ověř, že není `null`.

## Objekt jako parametr
Metoda dostane kopii reference, ale obě reference ukazují na tentýž objekt. Změny jeho datových členů se proto projeví i mimo metodu.

```csharp
static void Vylepsi(Auto auto, int oKolik)
{
    auto.MaxRychlost += oKolik;
}
```

| Vlastnost | `class` | `struct` |
|---|---|---|
| Druh typu | referenční | hodnotový |
| Přiřazení `b = a` | kopie odkazu, jeden objekt | kopie dat, dva nezávislé údaje |
| Může být `null` | ano | běžně ne |
| Předání metodě | metoda může měnit původní objekt | metoda pracuje s kopií |

> **Pozor:** `Auto[] auta = new Auto[3]` obsahuje zpočátku tři hodnoty `null`. `b = a` nevytváří kopii objektu. Před použitím objektu, který může být `null`, proveď kontrolu.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/fundamentals/object-oriented/objects).

---

# 20. Datové členy třídy

**Datový člen (field)** je proměnná deklarovaná přímo ve třídě, mimo metody. Uchovává stav objektu po celou dobu jeho existence. Každý objekt má vlastní hodnoty.

**Lokální proměnná** je deklarovaná uvnitř metody a existuje pouze během jejího provádění.

## Výchozí hodnoty datových členů

| Typ | Výchozí hodnota |
|---|---|
| `int`, `long`, `double`, `decimal` | `0` |
| `bool` | `false` |
| `char` | znak `\0` |
| `DateTime` | 1. 1. 0001 00:00:00 |
| `enum` | hodnota s číslem 0 |
| `string`, pole, objekty | `null` |

Výchozí hodnotu dostávají datové členy a prvky pole. Lokální proměnnou nelze použít, dokud jí nepřiřadíš hodnotu. Textové datové členy je vhodné inicializovat `= ""`.

## const a readonly

```csharp
class Objednavka
{
    public const int MaxPolozek = 30; // společná konstanta třídy
    public readonly DateTime Vytvoreno = DateTime.Now; // hodnota konkrétního objektu
}
```

| Vlastnost | `const` | `readonly` |
|---|---|---|
| Kdy se hodnota určí | při překladu | při vytvoření objektu |
| Typy | čísla, znaky, text, bool | libovolný typ |
| Komu patří | celé třídě | každému objektu zvlášť |
| Kde ji lze nastavit | pouze v deklaraci | v deklaraci nebo konstruktoru |

Konstanta se používá přes název třídy, např. `Objednavka.MaxPolozek`. U `readonly` pole nelze vyměnit celé pole, ale jeho jednotlivé prvky měnit lze.

## Pole jako datový člen a počítadlo
Pole má pevnou kapacitu. Další datový člen si proto může pamatovat počet skutečně obsazených míst.

```csharp
class Kasicka
{
    public const int Kapacita = 100;
    public int[] Mince = new int[Kapacita];
    public int PocetMinci;

    public void Vhod(int hodnota)
    {
        if (PocetMinci < Kapacita)
        {
            Mince[PocetMinci] = hodnota;
            PocetMinci++;
        }
    }
}
```

Při výpočtech a výpisu procházej jen prvky od `0` do `PocetMinci - 1`, ne celé `Mince.Length`.

> **Pozor:** Co si má objekt pamatovat, patří do datového členu, ne do lokální proměnné metody. Nepoužívej `null` text bez kontroly. Konstantu přistupuj přes třídu, nikoli objekt.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/classes-and-structs/fields).

---

# 21. Vlastnosti a zapouzdření

**Zapouzdření** skrývá vnitřní data objektu a dovoluje je číst nebo měnit pouze kontrolovaným způsobem.

**Vlastnost (property)** se používá podobně jako proměnná (`osoba.Vek = 16`), ale může obsahovat přístupové metody:
- `get` – čtení hodnoty.
- `set` – nastavení hodnoty.
- `value` – hodnota, kterou se právě přiřazuje.

## Vlastnost s kontrolou

```csharp
class Osoba
{
    private int _vek;

    public int Vek
    {
        get { return _vek; }
        set
        {
            if (value >= 0)
                _vek = value;
        }
    }
}
```

## Automatické a vypočítané vlastnosti

```csharp
class Obdelnik
{
    public double A { get; set; }                 // čtení i zápis
    public double B { get; set; }
    public double Obsah { get { return A * B; } } // pouze čtení, vypočítaná
    public string Nazev { get; private set; } = "obdélník";
}
```

| Zápis | Čtení zvenku | Zápis zvenku |
|---|---:|---:|
| `{ get; set; }` | ano | ano |
| `{ get; private set; }` | ano | ne |
| `{ get; }` | ano | ne |

> **Pozor:** V `set` musíš přiřazovat do datového členu (`_vek = value`), ne znovu do vlastnosti (`Vek = value`) – vznikla by nekonečná rekurze. Vlastnosti se pojmenovávají PascalCase, soukromé datové členy obvykle `_camelCase`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/classes-and-structs/properties).

---

# 22. Metody třídy

**Metoda** je funkce nebo procedura, která patří třídě. **Instanční metoda** se volá na konkrétním objektu a pracuje s jeho daty.

- Metoda s návratovou hodnotou vrací výsledek přes `return`.
- Procedura má návratový typ `void`.
- **Signatura** = název metody + počet, typy a pořadí parametrů.
- **Přetěžování (overloading)** = více metod se stejným názvem, ale jinými parametry.
- `ToString()` vrací textovou podobu objektu; lze ji přepsat.

```csharp
class Obdelnik
{
    public double A { get; set; }
    public double B { get; set; }

    public double Obsah()
    {
        return A * B;
    }

    public void Zvetsi(double koeficient)
    {
        A *= koeficient;
        B *= koeficient;
    }

    public override string ToString()
    {
        return $"Obdélník {A} x {B}";
    }
}
```

## Přetěžování metod

```csharp
class Plochy
{
    public double Plocha(double strana) { return strana * strana; }
    public double Plocha(double a, double b) { return a * b; }
    public int Plocha(int a, int b) { return a * b; }
}
```

Metody se musí lišit parametry. Pouze jiný návratový typ nestačí.

> **Pozor:** Při volání metody nezapomeň na závorky: `o.Obsah()`. Bez přepsání `ToString()` výpis objektu zobrazí název typu. Funkce s návratovou hodnotou musí vracet hodnotu ve všech možných větvích.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/classes-and-structs/methods).

---

# 23. Konstruktory

**Konstruktor** je speciální metoda, která se automaticky zavolá při vytvoření objektu pomocí `new`. Nastaví počáteční stav objektu.

- Má stejný název jako třída.
- Nemá návratový typ (nepíše se ani `void`).
- **Výchozí konstruktor** nemá parametry. Pokud nenapíšeš žádný konstruktor, vytvoří ho překladač.
- Jakmile napíšeš vlastní konstruktor, automatický výchozí konstruktor zmizí.

```csharp
class Osoba
{
    public string Jmeno { get; set; }
    public int Vek { get; set; }

    public Osoba(string jmeno, int vek)
    {
        Jmeno = jmeno;
        Vek = vek;
    }
}

Osoba eva = new Osoba("Eva", 17);
```

## Klíčové slovo this
`this` označuje aktuální objekt. Používá se k odlišení datového členu od parametru se stejným názvem.

```csharp
class Bod
{
    private int x;
    public Bod(int x)
    {
        this.x = x;
    }
}
```

## Přetěžování a řetězení konstruktorů
Konstruktor může volat jiný konstruktor stejné třídy pomocí `: this(...)`. Společný kód se tak píše pouze jednou.

```csharp
class Hrac
{
    public string Jmeno { get; set; }
    public int Zivoty { get; set; }

    public Hrac(string jmeno, int zivoty)
    {
        Jmeno = jmeno;
        Zivoty = zivoty;
    }

    public Hrac(string jmeno) : this(jmeno, 3) { }
    public Hrac() : this("Neznámý") { }
}
```

## Inicializátor objektu
Nejprve se zavolá konstruktor, poté se nastaví uvedené vlastnosti:

```csharp
Hrac h = new Hrac { Jmeno = "Cyril", Zivoty = 5 };
Hrac h2 = new Hrac("Dana") { Zivoty = 10 };
```

Vlastnost pouze s `get` lze nastavit v konstruktoru, ale po vytvoření objektu už ne.

> **Pozor:** Konstruktor nesmí mít návratový typ. Po přidání konstruktoru s parametry je nutné napsat i bezparametrický konstruktor, pokud ho chceš používat. Při shodě názvu parametru a členu používej `this.clen = clen`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/classes-and-structs/constructors).

---

# 24. Destruktory, GC a IDisposable

V C# se o uvolnění spravované paměti stará **garbage collector (GC)**. Objekt se stane kandidátem na odstranění, když na něj už nevede žádný odkaz; GC ho uklidí automaticky, nikoli v přesně předvídatelném okamžiku.

- **Spravované prostředky** – běžné objekty v paměti, uklízí GC.
- **Nespravované prostředky** – například otevřené soubory, síťová nebo databázová připojení; je třeba je uvolnit včas.
- **Finalizér** (`~Trida()`) – zavolá ho GC před uvolněním objektu, ale nevíme kdy.
- **`IDisposable`** – rozhraní s metodou `Dispose()` pro řízené uvolnění prostředků.
- **`using`** – zajistí automatické zavolání `Dispose()` na konci bloku.

## Finalizér

```csharp
class Docasny
{
    ~Docasny()
    {
        Console.WriteLine("Objekt se uvolňuje z paměti.");
    }
}
```

Finalizér nelze volat ručně. V C# se používá výjimečně – nevíme, kdy poběží, běží v nezaručeném pořadí a zpomaluje práci GC.

## IDisposable a using

```csharp
class Pripojeni : IDisposable
{
    public void Dispose()
    {
        Console.WriteLine("Připojení uzavřeno.");
    }
}

using (Pripojeni db = new Pripojeni())
{
    // práce s připojením
} // automaticky se zavolá db.Dispose()
```

Lze použít i kratší zápis:

```csharp
using Pripojeni db = new Pripojeni();
```

`GC.Collect()` a `GC.WaitForPendingFinalizers()` slouží hlavně k pokusům a ladění, ne k běžnému používání.

> **Pozor:** Přiřazení `null` objekt ihned neodstraní – pouze zruší odkaz. Nespoléhej na finalizér pro včasné zavření souboru; používej `using` / `Dispose()`. Po zavolání `Dispose()` s prostředkem dál nepracuj.

Více informací: [Microsoft Learn (finalizéry)](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/classes-and-structs/finalizers), [Microsoft Learn (příkaz using)](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/statements/using).

---

# 25. Přístupové modifikátory

**Přístupový modifikátor** určuje, odkud je třída nebo její člen dostupný. Souvisí se zapouzdřením – data mají být skrytá a okolí má používat veřejné metody a vlastnosti.

| Modifikátor | Dostupnost | Typické použití |
|---|---|---|
| `public` | odkudkoli | veřejné metody a vlastnosti |
| `private` | pouze uvnitř stejné třídy | datové členy a pomocné metody |
| `protected` | ve třídě a jejích potomcích | členy určené pro dědění |
| `internal` | v rámci stejného projektu (assembly) | třídy a členy neveřejné mimo projekt |

Výchozí přístup: člen třídy je `private`, třída je `internal`.

```csharp
class BankovniUcet
{
    private decimal _zustatek;
    public string Majitel { get; }

    public BankovniUcet(string majitel)
    {
        Majitel = majitel;
    }

    public void Vlozit(decimal castka)
    {
        if (castka > 0)
            _zustatek += castka;
    }
}
```

Vlastnost může mít různé modifikátory pro čtení a zápis: `public int Body { get; private set; }` – číst může kdokoli, měnit pouze třída.

**`public` vs. `internal`:** `public` je dostupné i z jiných projektů, `internal` pouze uvnitř stejného projektu. V jednom malém projektu se často chovají podobně.

> **Pozor:** Neřeš chybu nepřístupného členu tím, že uděláš všechno `public`. Raději nabídni veřejnou metodu nebo vlastnost s kontrolou hodnoty. Chyba CS0122 znamená, že člen není přístupný.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).

---

# 26. Statické členy – static

- **Instanční člen** patří konkrétnímu objektu. Používá se přes proměnnou objektu: `hrac.Jmeno`.
- **Statický člen** patří třídě jako celku, existuje jen jednou a sdílejí ho všechny objekty. Používá se přes název třídy: `Hrac.Rekord`.
- **Statická metoda** se volá bez vytváření objektu, např. `Math.Sqrt()`, `int.Parse()`.
- **Statická třída** nemůže mít instance a obsahuje pouze statické členy.

```csharp
class Kalkulacka
{
    public static int Vetsi(int a, int b)
    {
        return a > b ? a : b;
    }
}

int vysledek = Kalkulacka.Vetsi(7, 12);
```

## Statická třída

```csharp
static class Geometrie
{
    public static double ObsahKruhu(double r)
    {
        return Math.PI * r * r;
    }
}
```

## Co smí statická metoda používat
- Instanční metoda může používat instanční i statické členy.
- Statická metoda nemá konkrétní objekt, proto může přímo používat pouze statické členy.

> **Pozor:** Statický člen volej přes třídu, ne přes objekt (`Hrac.Rekord`). Statická metoda nemůže přímo přistupovat k instančnímu členu – chyba CS0120. Statická třída se nevytváří přes `new`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members).

---
# 27. Výjimky – try/catch

**Výjimka (`exception`)** je objekt popisující chybu za běhu programu. Pokud ji nikdo nezachytí, program skončí chybou. Výjimka může „probublat“ z volané metody do místa, které ji zavolalo.

## Časté typy výjimek

| Výjimka | Příčina |
|---|---|
| `FormatException` | text nelze převést na číslo |
| `OverflowException` | hodnota je mimo rozsah typu |
| `DivideByZeroException` | celočíselné dělení nulou |
| `IndexOutOfRangeException` | index mimo pole |
| `NullReferenceException` | použití objektu s hodnotou `null` |
| `FileNotFoundException` | soubor neexistuje |
| `ArgumentException` | metodě byla předána neplatná hodnota |

Dělení nulou u `double` nevyhodí výjimku; může vrátit nekonečno (`∞`) nebo `NaN`.

## try – catch – finally

```csharp
try
{
    int cislo = int.Parse(Console.ReadLine());
}
catch (FormatException)
{
    Console.WriteLine("Nezadali jste celé číslo.");
}
catch (Exception ex)
{
    Console.WriteLine("Neočekávaná chyba: " + ex.Message);
}
finally
{
    Console.WriteLine("Tento blok se provede vždy.");
}
```

- `try` – kód, ve kterém může vzniknout chyba.
- `catch` – reakce na zachycenou výjimku; lze mít více bloků.
- `finally` – provede se vždy, i po chybě nebo `return`.
- `Exception` – základní třída všech výjimek; `Message` obsahuje popis.

Bloky `catch` řaď od nejkonkrétnějšího po nejobecnější. `catch (Exception)` musí být poslední. Lze vynechat `catch` nebo `finally`, ne však oba.

## Vyhození vlastní výjimky

```csharp
if (vek < 0)
    throw new ArgumentException("Věk nesmí být záporný.");
```

Vlastní výjimka dědí z `Exception`:

```csharp
class NeplatnaZnamkaException : Exception
{
    public NeplatnaZnamkaException(string zprava) : base(zprava)
    {
    }
}
```

Výjimky používej pro chybové situace. Co lze jednoduše ověřit předem, zkontroluj podmínkou nebo pomocí `TryParse`.

> **Pozor:** Neschovávej chybu prázdným `catch { }`. Konkrétní výjimky musí být před obecným `Exception`. Proměnná vytvořená uvnitř `try` není vidět v `catch` ani za blokem. Systémové `Message` bývá technické a uživateli nemusí být srozumitelné.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/statements/exception-handling-statements).

---

# 28. Abstrakce objektů a UML

**Abstrakce** znamená vybrat z reálného objektu jen vlastnosti a činnosti podstatné pro konkrétní program. Model třídy tedy neobsahuje všechno, co reálný objekt má, ale jen to, co aplikace potřebuje.

- **Model** – třída popisující vybranou část skutečnosti.
- **Skrývání složitosti** – uživatel volá jednoduché veřejné metody a neřeší jejich vnitřní provedení.
- **Veřejné rozhraní třídy** – všechny členy `public`.
- **UML** – grafický jazyk pro návrh programu; diagram tříd ukazuje třídy, členy, metody a vztahy.

## Čtyři pilíře OOP

| Pilíř | Význam |
|---|---|
| **Abstrakce** | modelujeme jen podstatné vlastnosti a chování |
| **Zapouzdření** | data jsou skrytá a mění se kontrolovaně přes vlastnosti a metody |
| **Dědičnost** | nová třída převezme a rozšíří členy existující třídy |
| **Polymorfismus** | stejné volání metody se u různých objektů chová různě |

Abstrakce rozhoduje, co třída nabízí navenek; zapouzdření hlídá přístup k jejím vnitřním datům.

## UML diagram tříd
Třída se kreslí jako obdélník se třemi částmi: název, datové členy a metody.

| Značka UML | Význam | C# |
|---|---|---|
| `+` | veřejný člen | `public` |
| `-` | soukromý člen | `private` |
| `#` | chráněný člen | `protected` |

V UML se typ píše za název a dvojtečku: `cena : decimal`. V C# se typ píše před název: `decimal cena;`. Návratový typ metody je v UML za závorkou.

## Návrh tříd ze zadání
1. Podstatná jména jsou kandidáti na třídy a datové členy.
2. Slovesa jsou kandidáti na metody.
3. Vyber jen to, co program potřebuje.
4. Data skryj (`private`), navenek nabídni potřebné vlastnosti a metody.
5. Navrhni diagram tříd a teprve potom programuj.

Vztahy mezi třídami mohou mít násobnost, např. jeden košík obsahuje `0..*` produktů.

> **Pozor:** Nedělej jednu obří třídu, která zajišťuje vše. Rozděl odpovědnosti mezi objekty. Nepodstatné vlastnosti reálné věci do modelu nezařazuj.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/fundamentals/tutorials/oop).

---

# 29. Dědičnost

**Dědičnost** umožňuje vytvořit novou třídu (potomka), která převezme členy jiné třídy (předka) a může je rozšířit.

- **Předek / bázová třída** – obecnější třída.
- **Potomek / odvozená třída** – konkrétnější třída.
- Používej vztah **„je“**: Student je Osoba.
- Vztah **„má“** řeš datovým členem: Auto má Motor, proto `Auto : Motor` není vhodné.
- Třída může mít pouze jednoho přímého předka.
- Všechny třídy dědí z `object`.

## Základní zápis

```csharp
class Student : Osoba
{
    // nové členy potomka
}
```

Konstruktory se nedědí. Konstruktor potomka může zavolat konstruktor předka pomocí `: base(...)`:

```csharp
public Student(string jmeno, int vek, string skola)
    : base(jmeno, vek)
{
    Skola = skola;
}
```

Metodu předka lze zavolat přes `base.Metoda()`.

## Přístup v dědičnosti

| Modifikátor | Ve třídě | V potomkovi | V hlavním programu |
|---|---:|---:|---:|
| `private` | ano | ne | ne |
| `protected` | ano | ano | ne |
| `public` | ano | ano | ano |

Potomek soukromý člen předka obsahuje, ale nemůže k němu přímo přistupovat.

## Abstraktní třída a metoda
- `abstract class` – nelze z ní vytvořit objekt; slouží jako obecný předek.
- `abstract` metoda – nemá tělo a potomek ji musí doplnit pomocí `override`.

```csharp
abstract class Figurka
{
    public abstract string Pohyb();
}

class Vez : Figurka
{
    public override string Pohyb()
    {
        return "rovně o libovolný počet polí";
    }
}
```

> **Pozor:** Pokud předek nemá bezparametrický konstruktor, potomek musí zavolat správný konstruktor přes `base(...)`. `private` člen předka není dostupný potomkovi. Z abstraktní třídy nelze vytvořit objekt. C# nepovoluje dědění z více tříd.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/fundamentals/object-oriented/inheritance).

---

# 30. Polymorfismus

**Polymorfismus (mnohotvarost)** znamená, že stejné volání metody může mít různé chování podle skutečného typu objektu.

- Proměnná typu předka může obsahovat objekt kteréhokoli potomka.
- Přes referenci předka lze volat jen členy, které má předek.
- `virtual` – metoda předka, kterou lze přepsat.
- `override` – potomek dodá vlastní verzi virtuální metody.
- `new` – potomek metodu předka skryje, nikoli přepíše.

```csharp
class Nastroj
{
    public virtual string Zahraj() { return "..."; }
}

class Kytara : Nastroj
{
    public override string Zahraj() { return "brnk brnk"; }
}

class Buben : Nastroj
{
    public override string Zahraj() { return "bum bum"; }
}

Nastroj[] kapela = { new Kytara(), new Buben() };
foreach (Nastroj n in kapela)
    Console.WriteLine(n.Zahraj()); // podle skutečného objektu
```

## Operátory is a as

| Zápis | Význam |
|---|---|
| `obj is Kytara` | test, zda jde o kytaru nebo jejího potomka |
| `obj is Kytara k` | test a současné uložení do proměnné `k` |
| `obj as Kytara` | pokus o převod; při neúspěchu vrátí `null` |
| `(Kytara)obj` | přetypování; při neúspěchu vyhodí `InvalidCastException` |

## override vs. new

| | `override` | `new` |
|---|---|---|
| Metoda předka | musí být `virtual`, `abstract` nebo `override` | nemusí být virtuální |
| Volání přes typ potomka | metoda potomka | metoda potomka |
| Volání přes typ předka | přepsaná metoda potomka | metoda předka |

`new` pro skrytí metody se používá výjimečně; obvykle je vhodné `override`.

> **Pozor:** Bez `virtual` v předkovi nelze metodu přepsat. Metodu existující pouze v potomkovi nelze zavolat přes referenci předka bez ověření typu. Výsledek `as` vždy kontroluj na `null`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/fundamentals/object-oriented/polymorphism).

---

# 31. Přetěžování operátorů

**Přetěžování operátorů** umožňuje určit, co znamená například `a + b`, když `a` a `b` jsou objekty vlastní třídy (např. vektory nebo zlomky).

- Operátor se definuje jako veřejná statická metoda s klíčovým slovem `operator`.
- Alespoň jeden parametr musí být typu dané třídy.
- Operátory `==` a `!=` se přetěžují v páru; stejně tak `<` a `>`.
- K `==` je vhodné doplnit `Equals()` a `GetHashCode()`.

```csharp
class Vektor
{
    public double X { get; }
    public double Y { get; }

    public Vektor(double x, double y)
    {
        X = x;
        Y = y;
    }

    public static Vektor operator +(Vektor a, Vektor b)
    {
        return new Vektor(a.X + b.X, a.Y + b.Y);
    }
}
```

Přetížení má smysl, když je význam operátoru přirozený (např. sčítání vektorů). Nemá smysl používat `+` pro nesouvisející operaci.

> **Pozor:** Operátor musí být `public static`. `==` a `!=` se definují společně. Operátor obvykle vrací nový objekt, nemění původní. Pro `v * 2` a `2 * v` může být potřeba definovat obě pořadí operandů.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/operators/operator-overloading).

---

# 32. Rozhraní – interface

**Rozhraní (`interface`)** je smlouva – stanoví, jaké metody a vlastnosti musí třída nabídnout, ale neurčuje jejich vnitřní provedení.

- Název rozhraní obvykle začíná `I` (`IZvire`, `IComparable`).
- Třída rozhraní implementuje a doplní všechny jeho členy jako `public`.
- Z rozhraní nelze vytvořit objekt, ale lze ho použít jako typ proměnné nebo pole.
- Třída může dědit z jedné třídy a implementovat více rozhraní.

```csharp
interface IZvire
{
    string Zvuk();
}

class Pes : IZvire
{
    public string Zvuk() { return "Haf"; }
}

class Kocka : IZvire
{
    public string Zvuk() { return "Mňau"; }
}

IZvire[] zvirata = { new Pes(), new Kocka() };
foreach (IZvire z in zvirata)
    Console.WriteLine(z.Zvuk());
```

Při dědění a implementaci rozhraní se nejprve uvádí předek a potom rozhraní:

```csharp
class Kachna : Ptak, ILetajici, IPlavajici { }
```

## IComparable<T> – řazení vlastních objektů
Implementací `IComparable<T>` získá objekt pravidlo porovnání pomocí `CompareTo()`:

```csharp
class Student : IComparable<Student>
{
    public double Prumer { get; set; }

    public int CompareTo(Student other)
    {
        return Prumer.CompareTo(other.Prumer);
    }
}
```

`CompareTo()` vrací záporné číslo (tento objekt je před), `0` (rovnost) nebo kladné číslo (tento objekt je za). Potom lze použít `Array.Sort()`.

> **Pozor:** Implementované metody musí být `public`. Nezapomeň doplnit všechny členy rozhraní. Třídu předka uváděj před rozhraními.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/fundamentals/types/interfaces).

---

# 33. Delegáti, lambda výrazy a události

**Delegát** je datový typ, jehož proměnná uchovává odkaz na metodu. Umožňuje uložit metodu do proměnné, předat ji jiné metodě nebo ji zavolat později.

- **Signatura** – návratový typ a počet a typy parametrů.
- **Lambda výraz** – anonymní funkce zapsaná např. `(a, b) => a + b`.
- **Vícenásobný delegát** – může obsahovat více metod přidaných přes `+=`.
- **Událost (`event`)** – oznámení, které objekt vyšle přihlášeným metodám, když se něco stane.

## Vlastní delegát

```csharp
delegate double Operace(double a, double b);

static double Secti(double a, double b) => a + b;
static double Vynasob(double a, double b) => a * b;

Operace op = Secti;          // bez závorek – uloží se metoda
Console.WriteLine(op(5, 3)); // zavolání přes delegát
op = Vynasob;
```

Metoda předaná do delegátu musí mít stejnou signaturu.

## Vestavěné delegáty

| Delegát | Co uchovává | Příklad |
|---|---|---|
| `Action` / `Action<T...>` | metoda bez návratové hodnoty (`void`) | `Action<string> pozdrav = s => Console.WriteLine(s);` |
| `Func<T..., TResult>` | metoda vracející hodnotu; poslední typ je návratový | `Func<int, int, int> soucet = (a, b) => a + b;` |
| `Predicate<T>` | metoda s jedním parametrem, vrací `bool` | `Predicate<int> sude = x => x % 2 == 0;` |

Příklady lambda výrazů:

```csharp
Func<double, double> naDruhou = x => x * x;
Func<int, int, int> soucet = (a, b) => a + b;
Action cara = () => Console.WriteLine("-----");
```

Lambda s blokem `{ }`, která vrací hodnotu, musí použít `return`.

## Metody pole přijímající podmínku / delegát

| Metoda | Výsledek |
|---|---|
| `Array.FindAll(pole, podminka)` | nové pole všech vyhovujících prvků |
| `Array.Find(pole, podminka)` | první vyhovující prvek, jinak výchozí hodnota |
| `Array.FindIndex(pole, podminka)` | index prvního vyhovujícího, jinak `-1` |
| `Array.Exists(pole, podminka)` | `true`, pokud vyhovuje alespoň jeden |
| `Array.TrueForAll(pole, podminka)` | `true`, pokud vyhovují všechny |
| `Array.ForEach(pole, akce)` | provede akci pro každý prvek |
| `Array.Sort(pole, porovnani)` | řazení podle vlastního porovnání |

## Události
Událost je delegát označený `event`. Odběratel se přihlásí přes `+=`, odhlásí přes `-=`. Vyvolat ji může třída, ve které je deklarována.

```csharp
class Tlacitko
{
    public event Action? Kliknuti;

    public void Klikni()
    {
        Kliknuti?.Invoke(); // vyvolá se pouze, pokud má odběratele
    }
}

Tlacitko tlacitko = new Tlacitko();
tlacitko.Kliknuti += () => Console.WriteLine("Ahoj!");
tlacitko.Klikni();
```

Událost nemá-li odběratele obsahuje `null`; proto se používá `?.Invoke()`.

> **Pozor:** Při přiřazení metody do delegátu se nepíší závorky (`op = Secti`, nikoli `op = Secti()`). U `Func` je poslední typový parametr návratový typ. `=` přepíše dosavadní metody, `+=` přidá další. Událost vyvolávej přes `?.Invoke()`.

Více informací: [Microsoft Learn (delegati)](https://learn.microsoft.com/cs-cz/dotnet/csharp/programming-guide/delegates/), [Microsoft Learn (lambda)](https://learn.microsoft.com/cs-cz/dotnet/csharp/language-reference/operators/lambda-expressions).

---

# 34. Seznam – List a ArrayList

**Abstraktní datový typ (ADT)** popisuje, jaké operace lze s datovou strukturou provádět (přidat, odebrat, najít…), bez ohledu na její vnitřní provedení.

**Seznam** je uspořádaná posloupnost s indexy od nuly. Na rozdíl od pole může za běhu růst a zmenšovat se.

| Vlastnost | Pole `int[]` | Seznam `List<int>` |
|---|---|---|
| Velikost | pevná | mění se |
| Počet prvků | `Length` | `Count` |
| Přidání / odebrání | nelze přímo | `Add`, `Insert`, `Remove`, `RemoveAt` |
| Přístup | `pole[i]` | `seznam[i]` |

## Vytvoření seznamu

```csharp
List<string> nakup = new List<string>();
List<int> cisla = new List<int> { 5, 3, 8 };
var znamky = new List<int>();
```

`List<T>` je generický typ – `T` určuje typ prvků, např. `List<int>`, `List<string>`, `List<Zak>`.

## Nejdůležitější metody a vlastnosti

| Zápis | Význam |
|---|---|
| `Add(x)` | přidá na konec |
| `Insert(i, x)` | vloží na index a posune další prvky |
| `Remove(x)` | odebere první výskyt hodnoty; vrací `bool` |
| `RemoveAt(i)` | odebere prvek na indexu |
| `Clear()` | smaže všechny prvky |
| `Count` | počet prvků |
| `seznam[i]` | čtení nebo změna prvku |
| `Contains(x)` | obsahuje hodnotu? |
| `IndexOf(x)` | index prvního výskytu, jinak `-1` |
| `Sort()` / `Reverse()` | seřadí / obrátí pořadí |

Procházení: `foreach`, pokud nepotřebuješ index; `for`, pokud ho potřebuješ nebo měníš prvky.

## Seznam objektů a vyhledávání
Metody `Find`, `FindAll`, `FindIndex`, `Exists` a `RemoveAll` přijímají podmínku, často jako lambda výraz:

```csharp
List<Zak> zaci = new List<Zak>();
List<Zak> dobri = zaci.FindAll(z => z.Prumer < 2);
int index = zaci.FindIndex(z => z.Jmeno == "Petr");
int odebrano = zaci.RemoveAll(z => z.Prumer > 2.5);
```

## ArrayList vs. List<T>
`ArrayList` je starší negenerický seznam, který ukládá vše jako `object`. U hodnotových typů dochází k **boxingu** (zabalení do `object`) a při čtení k **unboxingu** (přetypování zpět).

`List<T>` je vhodnější, protože:
- hlídá typ prvků už při překladu;
- není nutné přetypovávat načtené hodnoty;
- vyhne se zbytečnému boxingu hodnotových typů.

`ArrayList` vyžaduje `using System.Collections;`. Pro běžný nový kód používej `List<T>`.

> **Pozor:** U seznamu je `Count`, nikoli `Length`. `Remove(3)` odebere hodnotu 3; `RemoveAt(3)` odebere prvek na indexu 3. Při průchodu `foreach` seznam neměň. Indexy jsou `0` až `Count - 1`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/api/system.collections.generic.list-1).

---

# 35. Slovník – Dictionary

**Slovník** (mapa, asociativní pole) uchovává dvojice **klíč → hodnota**. Hodnotu hledáme podle klíče, nikoli podle indexu.

- **Klíč** je jedinečný – v jednom slovníku smí být pouze jednou.
- **Hodnota** se opakovat může.
- **`KeyValuePair<TKey, TValue>`** představuje jednu dvojici s vlastnostmi `Key` a `Value`.
- `Dictionary` využívá hashovací tabulku – hledání podle klíče je velmi rychlé.

## Vytvoření

```csharp
Dictionary<string, string> telefony = new Dictionary<string, string>();

Dictionary<string, decimal> cenik = new Dictionary<string, decimal>
{
    { "rohlík", 3.90m },
    { "mléko", 24.90m }
};
```

První typový parametr je typ klíče, druhý typ hodnoty.

## Metody a vlastnosti

| Zápis | Význam |
|---|---|
| `Add(klic, hodnota)` | přidá dvojici; existující klíč způsobí `ArgumentException` |
| `slovnik[klic] = hodnota` | přidá nový nebo přepíše existující klíč |
| `slovnik[klic]` | přečte hodnotu; chybějící klíč způsobí `KeyNotFoundException` |
| `ContainsKey(klic)` | ověří existenci klíče |
| `TryGetValue(klic, out hodnota)` | bezpečně načte hodnotu; vrátí `true` / `false` |
| `Remove(klic)` | odebere dvojici |
| `Count` | počet dvojic |
| `Keys`, `Values` | kolekce klíčů / hodnot |
| `ContainsValue(hodnota)` | ověří, zda se hodnota vyskytuje (prochází dvojice) |

## Procházení slovníku

```csharp
foreach (KeyValuePair<string, decimal> polozka in cenik)
    Console.WriteLine($"{polozka.Key}: {polozka.Value:F2} Kč");

foreach (string klic in cenik.Keys)
    Console.WriteLine(klic);
```

Pořadí dvojic není zaručeno. Pokud potřebuješ seřazený výpis, zkopíruj klíče do seznamu a seřaď je:

```csharp
List<string> jmena = new List<string>(telefony.Keys);
jmena.Sort();
```

## Typické použití – počítání četnosti

```csharp
Dictionary<char, int> pocty = new Dictionary<char, int>();
foreach (char znak in "abrakadabra")
{
    if (pocty.ContainsKey(znak))
        pocty[znak]++;
    else
        pocty.Add(znak, 1);
}
```

> **Pozor:** `Add` selže, pokud klíč už existuje. Před čtením ověř klíč přes `ContainsKey` nebo použij `TryGetValue`. Textové klíče rozlišují velikost písmen (`"Praha"` a `"praha"`). Slovník neměň během `foreach`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/api/system.collections.generic.dictionary-2).

---

# 36. Další datové struktury

## Přehled

| Kolekce | Princip | Vložení | Odebrání | Nahlédnutí |
|---|---|---|---|---|
| `Queue<T>` | fronta FIFO | `Enqueue(x)` | `Dequeue()` | `Peek()` |
| `Stack<T>` | zásobník LIFO | `Push(x)` | `Pop()` | `Peek()` |
| `PriorityQueue<TElement, TPriority>` | prioritní fronta / halda | `Enqueue(x, priorita)` | `Dequeue()` | `Peek()` |
| `HashSet<T>` | množina bez duplicit | `Add(x)` | `Remove(x)` | `Contains(x)` |
| `Dictionary<TKey, TValue>` | klíč → hodnota | `Add(k, v)` | `Remove(k)` | `[k]` |
| `List<T>` | dynamické pole / seznam | `Add`, `Insert` | `Remove`, `RemoveAt` | `[i]` |

Všechny uvedené kolekce mají `Count`, `Clear()` a lze je procházet pomocí `foreach`.

## Fronta – Queue<T>
**FIFO (First In, First Out)** – první vložený prvek jde první ven. Použití: zákazníci u pokladny, tiskové úlohy, požadavky.

```csharp
Queue<string> fronta = new Queue<string>();
fronta.Enqueue("Adam");
fronta.Enqueue("Bára");
string prvni = fronta.Dequeue(); // Adam
string dalsi = fronta.Peek();   // Bára – zůstane ve frontě
```

## Zásobník – Stack<T>
**LIFO (Last In, First Out)** – poslední vložený prvek jde ven jako první. Použití: Zpět v editoru/prohlížeči, historie kroků, párování závorek.

```csharp
Stack<string> historie = new Stack<string>();
historie.Push("první");
historie.Push("druhý");
string posledni = historie.Pop(); // druhý
string nahled = historie.Peek();  // první – zůstane
```

## Prioritní fronta – PriorityQueue<TElement, TPriority>
Prvek se ukládá společně s prioritou. `Dequeue()` vrací prvek s **nejmenší hodnotou priority** (např. 1 = nejdůležitější).

```csharp
PriorityQueue<string, int> pacienti = new PriorityQueue<string, int>();
pacienti.Enqueue("rýma", 5);
pacienti.Enqueue("bezvědomí", 1);
string pacient = pacienti.Dequeue(); // bezvědomí
```

Pro bezpečné odebírání z prázdné fronty lze použít `TryDequeue(..., out ...)`.

## Množina – HashSet<T>
Množina neobsahuje duplicity a nezaručuje pořadí. `Add` vrací `false`, pokud prvek už existuje.

| Operace | Metoda | Výsledek v množině A |
|---|---|---|
| sjednocení A ∪ B | `A.UnionWith(B)` | prvky alespoň v jedné množině |
| průnik A ∩ B | `A.IntersectWith(B)` | prvky v obou množinách |
| rozdíl A \ B | `A.ExceptWith(B)` | prvky z A, které nejsou v B |
| symetrický rozdíl | `A.SymmetricExceptWith(B)` | prvky právě v jedné množině |

Další testy bez změny množiny: `IsSubsetOf`, `Overlaps`, `SetEquals`.

## Hashovací tabulka – Hashtable
`Hashtable` je starší negenerická kolekce z `System.Collections`. Klíče i hodnoty ukládá jako `object`, proto je nutné přetypování a typy nejsou kontrolovány překladačem. Pro nový kód používej `Dictionary<TKey, TValue>`.

| | `Hashtable` | `Dictionary<TKey, TValue>` |
|---|---|---|
| Typy | `object`, přetypování | určené typy, kontroluje překladač |
| Chybějící klíč při čtení | vrátí `null` | vyhodí `KeyNotFoundException` |
| Použití | starší kód | nové programy |

## Vektor – dynamické pole (`List<T>`)
`List<T>` má uvnitř obyčejné pole:
- `Count` – počet skutečně uložených prvků.
- `Capacity` – velikost vnitřního pole.
- Když se pole zaplní, vytvoří se větší pole a data se zkopírují.
- Přidávání na konec je v průměru rychlé; vkládání na začátek je pomalejší, protože se posouvají další prvky.
- Předem známou kapacitu lze zadat: `new List<int>(1000)`.

## Jak vybrat kolekci

| Potřebuji… | Použiji |
|---|---|
| zpracovat prvky v pořadí příchodu | `Queue<T>` |
| vrátit poslední krok / historii | `Stack<T>` |
| vždy odebrat prvek s nejlepší prioritou | `PriorityQueue<TElement, TPriority>` |
| unikátní hodnoty a množinové operace | `HashSet<T>` |
| vyhledávat hodnotu podle klíče | `Dictionary<TKey, TValue>` |
| seznam s indexy a proměnlivou délkou | `List<T>` |

> **Pozor:** `Dequeue()`, `Pop()` a `Peek()` na prázdné kolekci vyhodí `InvalidOperationException`. `HashSet` nemá indexy a jeho pořadí není zaručeno. Metody `UnionWith`, `IntersectWith` a `ExceptWith` mění původní množinu – chceš-li zachovat originál, vytvoř kopii. Během `foreach` kolekci neměň. Prioritní fronta při shodné prioritě nezaručuje pořadí vložení.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/standard/collections/).

---

# 37. Genericita a generické metody

**Genericita** umožňuje vytvářet metody a třídy, které fungují pro různé datové typy. Konkrétní typ se doplní až při použití.

- **Typový parametr** – zástupné jméno typu v lomených závorkách, obvykle `T`.
- **Generická metoda** – metoda s parametrem typu, např. `VypisPole<T>()`.
- **Generická třída** – třída s parametrem typu, např. `Krabice<T>`.
- **Omezení (`where`)** – požadavek na vlastnosti typu, který dosadíme.
- **Typová bezpečnost** – překladač kontroluje, zda se používají správné typy.

Genericita dovoluje napsat kód jednou pro více typů a vyhnout se `object`, ručnímu přetypování a boxingu jako u `ArrayList`.

## Generická metoda

```csharp
static void VypisPole<T>(T[] pole)
{
    foreach (T prvek in pole)
        Console.Write(prvek + " ");
}

static T Posledni<T>(T[] pole)
{
    return pole[pole.Length - 1];
}
```

Volání lze zapsat s typem (`VypisPole<int>(cisla)`) nebo ho překladač obvykle odvodí (`VypisPole(cisla)`).

## Generická třída

```csharp
class Krabice<T>
{
    public T Obsah { get; set; }

    public Krabice(T obsah)
    {
        Obsah = obsah;
    }
}

Krabice<int> kostka = new Krabice<int>(6);
Krabice<string> darek = new Krabice<string>("plyšový medvěd");
```

Třída může mít více typových parametrů: `Dvojice<T1, T2>`. Typ objektu se určí při vytvoření. `default(T)` vrátí výchozí hodnotu daného typu.

## Omezení typu – where
U obecného `T` nevíme, zda podporuje operace `<`, `>` nebo `+`. Pomocí `where` stanovíme, co musí dosazený typ umět.

```csharp
static T Vetsi<T>(T a, T b) where T : IComparable<T>
{
    if (a.CompareTo(b) > 0)
        return a;
    return b;
}
```

| Omezení | Požadavek na typ `T` |
|---|---|
| `where T : IComparable<T>` | implementuje porovnání přes `CompareTo` |
| `where T : Zvire` | je třída `Zvire` nebo její potomek |
| `where T : class` | je referenční typ |
| `where T : struct` | je hodnotový typ |
| `where T : new()` | má konstruktor bez parametrů |

Omezení lze kombinovat, např. `where T : class, new()`. U generické třídy se `where` píše za hlavičku třídy.

U neomezeného `T` nelze obecně použít `==`; pro porovnání hodnot lze použít `Equals()`.

> **Pozor:** Typový parametr patří za název metody (`VypisPole<T>`). Omezení `where` patří za seznam parametrů a před tělo metody. Pro porovnávání použij `IComparable<T>` a `CompareTo()`.

Více informací: [Microsoft Learn](https://learn.microsoft.com/cs-cz/dotnet/csharp/fundamentals/types/generics).

---

## Rychlé opakování – nejdůležitější rozdíly

| Co si neplést | Rozdíl |
|---|---|
| `=` × `==` | přiřazení × porovnání |
| `Write()` × `WriteLine()` | bez nového řádku × s novým řádkem |
| `char` × `string` | jeden znak v `' '` × text v `" "` |
| `int` dělení × `double` dělení | celočíselný výsledek × desetinný výsledek |
| `if` × `switch` | složené podmínky/rozsahy × konkrétní hodnoty jedné proměnné |
| `for` × `while` | známý počet opakování × počet není známý |
| `while` × `do-while` | podmínka na začátku × podmínka na konci |
| funkce × procedura | vrací hodnotu × `void`, nic nevrací |
| `ref` × `out` | vstupní proměnná už má hodnotu × hodnota se musí přiřadit uvnitř |
| pole × `List<T>` | pevná délka × měnitelný počet prvků |
| `int[,]` × `int[][]` | matice s pevnými rozměry × pole polí, řádky mohou mít jinou délku |
| `struct` × `class` | hodnotový typ × referenční typ |
| `const` × `readonly` | hodnota při překladu × hodnota nastavená při vytvoření objektu |
| instanční × statický člen | patří objektu × patří třídě |
| `override` × `new` | přepsání virtuální metody × skrytí metody předka |
| `Queue` × `Stack` | FIFO × LIFO |
| `List` × `Dictionary` | index prvku × klíč → hodnota |

## Základní pravidla pro psaní C#
- C# rozlišuje velká a malá písmena.
- Každý běžný příkaz ukonči středníkem `;`.
- Bloky kódu zapisuj do složených závorek `{ }`.
- Proměnné pojmenovávej výstižně; běžné proměnné camelCase, třídy a veřejné členy PascalCase.
- Než použiješ vstup od uživatele jako číslo, převeď ho (`Parse`) nebo bezpečně ověř (`TryParse`).
- U polí a řetězců pamatuj, že indexování začíná od nuly.
- Kontroluj hranice indexů, prázdné kolekce a možné hodnoty `null`.
- Data objektu běžně skrývej pomocí `private` a zpřístupňuj je přes vlastnosti a metody.
