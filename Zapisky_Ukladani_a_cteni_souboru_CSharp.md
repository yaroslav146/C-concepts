# 📁 Ukládání a čtení souborů v C#

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

# 🧰 3. Způsoby práce se soubory v C#

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

# 📁 4. Třída `File`

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

# 🔄 5. `using`

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

# ✏️ 6. `StreamWriter`

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

##  Zápis proměnné

```csharp
string jmeno = "Yaroslav";

using (StreamWriter writer = new StreamWriter(cesta))
{
    writer.WriteLine(jmeno);
}
```

---

# 📖 7. `StreamReader`

`StreamReader` slouží ke **čtení textu ze souboru**.

Výhodou je postupné čtení – nemusíme načíst celý soubor najednou.

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

##  `ReadLine()`

Načte **jeden řádek** ze souboru.

```csharp
string? radek = reader.ReadLine();
```

Když už žádný další řádek není, vrátí:

```csharp
null
```

##  Čtení celého souboru po řádcích

Nejdůležitější konstrukce:

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

###  Princip

```text
ReadLine()
    ↓
načte řádek
    ↓
radek != null ?
    ↓
ANO → zpracuj řádek
    ↓
ReadLine()
    ↓
další řádek
    ↓
...
    ↓
null → konec souboru
```

---

# 🛣️ 8. Třída `Path`

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
string cesta = Path.Combine(
    "A",
    "B",
    "priklad.txt"
);

string absolutniCesta = Path.GetFullPath(cesta);

Console.WriteLine(absolutniCesta);
```

---

# ⚠️ 9. Výjimky (`Exception`)

Výjimka = chyba nebo neočekávaný stav během běhu programu.

Při práci se soubory může nastat například:

- soubor neexistuje
- složka neexistuje
- nemáme oprávnění
- problém s diskem
- soubor používá jiný program

---

# 🛡️ 10. `try` / `catch`

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
// Ano, dají se kombinovat příkazy pass
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

# ❗ 11. Nejčastější výjimky

| Výjimka | Význam |
|---|---|
| `IOException` | obecná chyba vstupu/výstupu |
| `FileNotFoundException` | soubor nebyl nalezen |
| `DirectoryNotFoundException` | složka nebyla nalezena |
| `UnauthorizedAccessException` | nemáme oprávnění |
| `NotSupportedException` | nepodporovaný formát cesty |

---

# 🎯 12. NEJDŮLEŽITĚJŠÍ KÓD

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

##  Zkontrolovat soubor

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
