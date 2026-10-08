# Ukládání a čtení souborů v C#

## Navigace

- [Základní teorie](#1-základní-teorie)
- [Typy souborů](#2-typy-souborů)
- [Způsoby práce se soubory v C#](#3-způsoby-práce-se-soubory-v-c)
- [Třída `File`](#4-třída-file)
- [Direktiva `using`](#5-using)
- [`StreamWriter`](#6-streamwriter)
- [`StreamReader`](#7-streamreader)
- [Třída `Path`](#8-třída-path)
- [Výjimky (`Exception`)](#9-výjimky-exception)
- [ Ošetření výjimek `try` / `catch`](#10-try--catch)
- [ Nejčastější výjimky](#11-nejčastější-výjimky)
- [ NEJDŮLEŽITĚJŠÍ KÓD](#12-nejdůležitější-kód)
- [ Celkový přehled](#13-celkový-přehled)

##  1. Základní teorie

Soubor je uložen jako **sekvence bajtů** na určitém místě,
které určuje **souborová cesta**.

Při práci se souborem:

1. 📂 otevřeme soubor pomocí cesty
2. ✏️ čteme nebo zapisujeme data
3. 🔒 soubor uzavřeme

---

##  2. Typy souborů

###  Textový soubor

Obsahuje text uložený pomocí určitého kódování.

Např.:

- `.txt`
- `.csv`

###  Binární soubor

Obsahuje data ve formě bajtů.

Např.:

- obrázek
- video
- zvuk
- archiv

---

# 3. Způsoby práce se soubory v C#

Nejdůležitější jsou:

| Třída | Použití |
|---|---|
| `File` | jednoduché čtení/zápis celého souboru |
| `StreamWriter` | postupný zápis textu |
| `StreamReader` | postupné čtení textu |
| `Path` | vytváření souborových cest |

### Kdy co použít?

**File** → jednoduchá práce s celým menším souborem.

**StreamWriter / StreamReader** → postupné zapisování nebo čtení.

---

# 4. Třída `File`

Nejdříve:

```csharp
using System.IO;
```

Třída `File` obsahuje statické metody pro práci se soubory.

##  Zápis do souboru

### `WriteAllText()`

Zapíše text do souboru.

```csharp
string cesta = @"C:\Users\test\text.txt";
string text = "Ahoj soubore!";

File.WriteAllText(cesta, text);
```

⚠️ Pokud soubor už existuje, jeho obsah se **přepíše**.

##  Přečtení celého souboru

### `ReadAllText()`

```csharp
string obsah = File.ReadAllText(cesta);

Console.WriteLine(obsah);
```

##  Přidání textu na konec

### `AppendAllText()`

```csharp
File.AppendAllText(cesta, "Nový text");
```

Text se přidá za existující obsah.

Pro nový řádek:

```csharp
File.AppendAllText(cesta, "Nový řádek\n");
```

##  Kontrola existence

### `File.Exists()`

```csharp
if (File.Exists(cesta))
{
    Console.WriteLine("Soubor existuje.");
}
```

##  Odstranění

### `File.Delete()`

```csharp
File.Delete(cesta);
```

⚠️ Soubor se smaže **natrvalo**.

##  Vytvoření prázdného souboru

```csharp
File.Create(cesta);
```

##  Kopírování

```csharp
File.Copy(puvodniCesta, novaCesta, true);
```

- `puvodniCesta` → odkud
- `novaCesta` → kam
- `true` → přepsat existující soubor

##  Přesunutí

```csharp
File.Move(puvodniCesta, novaCesta);
```

---

# 5. `using`

`using` zajistí správné uvolnění zdroje po dokončení práce.

U souborů zajistí, že se soubor po práci **uzavře**.

```csharp
using (var writer = new StreamWriter(cesta))
{
    writer.WriteLine("Ahoj!");
}
```

Po skončení `using` se `StreamWriter` automaticky uvolní a soubor se zavře.


---

# 6. `StreamWriter`

`StreamWriter` slouží k **zápisu textu do souboru**.

Je vhodný pro postupný zápis a velké soubory.

```csharp
using (StreamWriter writer = new StreamWriter(cesta))
{
    writer.WriteLine("Ahoj soubore!");
    writer.WriteLine("Druhý řádek.");
}
```

##  `WriteLine()`

Zapíše text a přejde na nový řádek.

```csharp
writer.WriteLine("První řádek");
writer.WriteLine("Druhý řádek");
writer.WriteLine("Třetí řádek");
```

Výsledek:

```text
První řádek
Druhý řádek
Třetí řádek
```

##  `Write()`

Zapíše text **bez automatického přechodu na nový řádek**.

```csharp
writer.Write("Ahoj ");
writer.Write("světe!");
```

Výsledek:

```text
Ahoj světe!
```

---

# 7. `StreamReader`

`StreamReader` slouží ke **čtení textu ze souboru**.

Výhodou je postupné čtení – nemusíme načíst celý soubor najednou.

### Verze A

```csharp
using (StreamReader reader = new StreamReader(cesta))
{
    string? radek = reader.ReadLine(); // nacte (a ulozi) prvni radek 

    while (radek != null) // dokud radek neni null pracuj
    {
        Console.WriteLine(radek);
        radek = reader.ReadLine(); // nacte (a ulozi) dalsi radek
    }
}
```

### Verze H (jako Halfar) ` tá lepší`
```csharp
using (StreamReader reader = new StreamReader(cesta))
{
    string? radek; // vytvarime proměnou radek | ? - promena muze byt null
    while ((radek = reader.ReadLine()) != null) // porad nacitame dalsi radek dokud neskonci soubor (dostaneme hodnotu null)
    {
    Console.WriteLine(radek); // vypis
    }
}
```

##  `ReadLine()`

Načte **jeden řádek** ze souboru.

```csharp
string? radek = reader.ReadLine();
```

Když už žádný další řádek není, vrátí:

```csharp
null
```

---

# 8. Třída `Path`

`Path` slouží k vytváření a práci se **souborovými cestami**.

Různé operační systémy používají jiné oddělovače:

- Windows → `\`
- Linux / macOS → `/`

##  `Path.Combine()`

Spojí jednotlivé části cesty.

```csharp
string cesta = Path.Combine(
    "A",
    "B",
    "C",
    "priklad.txt"
);
```

Je lepší než ruční skládání cesty:

```csharp
string cesta = "A\\B\\C\\priklad.txt";
```

##  `Path.GetFullPath()`

Převede cestu na **absolutní cestu**.

A\B\C\priklad.txt    >>>    C:\Users\Yaroslav\Documents\A\B\C\priklad.txt

```csharp
string cesta = (@"A\B\C\priklad.txt");
string absolutniCesta = Path.GetFullPath(cesta); // soubor uz musi existovat jínak se vrací chyba
Console.WriteLine(absolutniCesta); // vraci celou cestu souboru
```


##  `Environment.SpecialFolder`

Převede cestu na **absolutní cestu**.

priklad.txt    >>>    C:\Users\Yaroslav\Documents\priklad.txt

```csharp
string cesta = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), // najde a ulozi cestu do slozky Documents
    "nazev.txt"); // nazev vytvořeneho souboru
```

---

# 9. Výjimky (`Exception`)

Výjimka = chyba nebo neočekávaný stav během běhu programu.

Při práci se soubory může nastat například:

- soubor neexistuje
- složka neexistuje
- nemáme oprávnění
- problém s diskem
- soubor používá jiný program

---

# 10. `try` / `catch`

Používá se pro **ošetření výjimek**.

```csharp
try
{
    // kód, který může způsobit chybu
}
catch (Exception ex)
{
    // co udělat při chybě
}
```

### Příklad

```csharp
try
{
    string obsah = File.ReadAllText("neexistujici.txt");
    Console.WriteLine(obsah);
}
catch (FileNotFoundException ex)
{
    Console.WriteLine("Soubor nenalezen: " + ex.Message);
}
// Ano, dají se kombinovat příkazy catch
catch (... ex)
{
    Console.WriteLine("...: " + ex.Message);
}
```

###  Princip

```text
try
 ↓
zkus provést kód
 ↓
chyba?
 ↓
ANO → catch
 ↓
zpracování chyby
```

---

# 11. Nejčastější výjimky

| Výjimka | Význam |
|---|---|
| `IOException` | obecná chyba vstupu/výstupu |
| `FileNotFoundException` | soubor nebyl nalezen |
| `DirectoryNotFoundException` | složka nebyla nalezena |
| `UnauthorizedAccessException` | nemáme oprávnění |
| `NotSupportedException` | nepodporovaný formát cesty |

---

# 12. NEJDŮLEŽITĚJŠÍ KÓD

##  Zapsat celý text

```csharp
File.WriteAllText(cesta, text);
```

##  Přidat text

```csharp
File.AppendAllText(cesta, text);
```

##  Přečíst celý soubor

```csharp
string obsah = File.ReadAllText(cesta);
```

##  Zkontrolovat existenci souboru

```csharp
if (File.Exists(cesta))
{
    // ...
}
```

##  Smazat soubor

```csharp
File.Delete(cesta);
```

##  Zapisovat po řádcích

```csharp
using (StreamWriter writer = new StreamWriter(cesta))
{
    writer.WriteLine("První řádek");
    writer.WriteLine("Druhý řádek");
}
```

##  Číst po řádcích

```csharp
using (StreamReader reader = new StreamReader(cesta))
{
    string? radek = reader.ReadLine();

    while (radek != null)
    {
        Console.WriteLine(radek);

        radek = reader.ReadLine();
    }
}
```

##  Vytvořit cestu

```csharp
string cesta = Path.Combine(
    "slozka",
    "podlozka",
    "soubor.txt"
);
```

##  Ošetřit chybu

```csharp
try
{
    // práce se souborem
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```

---

#  13. Celkový přehled

### `File`

```text
WriteAllText()   → přepíše / zapíše celý soubor
AppendAllText()  → přidá text na konec
ReadAllText()    → přečte celý soubor
Exists()         → zjistí, jestli soubor existuje
Create()         → vytvoří soubor
Delete()         → smaže soubor
Copy()           → zkopíruje soubor
Move()           → přesune soubor
```

### `StreamWriter`

```text
→ ZÁPIS

Write()          → zapíše text
WriteLine()      → zapíše text + nový řádek
```

### `StreamReader`

```text
→ ČTENÍ

ReadLine()       → přečte jeden řádek
null             → konec souboru
```

### `Path`

```text
Combine()        → spojí části cesty
GetFullPath()    → vytvoří absolutní cestu
```

### `using`

```text
→ automaticky uvolní / uzavře zdroj
```

### `try / catch`

```text
→ ošetření chyb
```
![](https://scontent-prg1-1.xx.fbcdn.net/v/t1.15752-9/833271007_1402541305324999_7225774309289545538_n.jpg?_nc_cat=105&ccb=1-7&_nc_sid=fc17b8&_nc_ohc=trXgyfp7qF4Q7kNvwEoQkDc&_nc_oc=AdodaFYnxMLq3_uBH9S2BITrjk3nwe4eIIhtj6EJ7TthWoBwoCY1FL9YOIRC8iK1LKY&_nc_zt=23&_nc_ht=scontent-prg1-1.xx&_nc_ss=7b6a8&oh=03_Q7cD6gHEZC28WHaIixb-DoB7uuJYdegNysvfSY2tNPnfJ_5Pzw&oe=6AEDD9B5)