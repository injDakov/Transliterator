# Dakov.Transliterator

[![License](http://img.shields.io/:license-MIT-blue.svg)](https://licenses.nuget.org/MIT) [![NuGet Badge](https://buildstats.info/nuget/Dakov.Transliterator)](https://www.nuget.org/packages/Dakov.Transliterator/) 

Both directions transliteration .Net library converting Cyrillic to Latin by the Basic or Bulgarian rule set.

**If my small library saved you time and you think that is useful, you can share it with your friends or colleagues.**\
**And if you want, don't hesitate to grab me a beer. :)**

#### An expression of gratitude
For each person who donates, I can allocate space for his name, project, or other information that he wants to share with my auditory.
The data will be in the section **Friends and Supporters**.
This also can be ads exchange. :)

#### Donation opportunities
All wallets are provided and supported by [Bitfinex](https://bitfinex.com/?refcode=kwqvP9OMT). Please read the actual information.

* **Bitcoin (BTC)**\
Address - **3FqXqTzGhzxosERosz832F7rGDXMteMjRh**

* **Ethereum (ETH)** At this time Bitfinex does not accept transactions sent from smart contracts.\
Address - **0x818E07acD7d75d1812B2E7067e417C5Bc80d327E**

* **XRP (XRP)** Sending XRP requires both an address and a Tag\
Address - **rLW9gnQo7BQhU6igk5keqYnH3TVrCxGRzm**\
Tag - **2345006832**

* **Dogecoin (DOGE)**\
Address - **DNXrvtmrSWVyBKfmPizXQsreqLSRJQpqCv**

* **Bitcoin Cash Node (BCHN)** Depositing anything other than BCH Node WILL RESULT IN LOSS OF FUNDS. Bitfinex currently is not supporting automated chain splits.\
Address - **bitcoincash:qz4tu69cn50gryhdahemytrszdtnn9vwtqexclhleq**

* **Litecoin (LTC)**\
Address - **MD7ngCjhUbLNZfnvLdXkVu1LUkXwZMTHmF**

* **Monero (XMR)**\
Address - **86GNkvtYzbEZwq5MxpVvzP7kZ2tUgea5SKy8FTJ4S48fY8hz3DYBPWwJsLNz2woi7dQi34TYkcPDpZKh7iZLaaMLGHrSTwZ**

**Note:** It is recommended that you check the transaction fees before making a transaction and then select the appropriate currency. Sometimes the fees are extremely high.

# Installation

Its can be installed and use via [NuGet](https://www.nuget.org/packages/Dakov.Transliterator/):

#### Package Manager
```powershell
Install-Package Dakov.Transliterator
```
#### .NET CLI
```
dotnet add package Dakov.Transliterator
```

# How to use it

We should include the library after the installation.
```cs
using Dakov.Transliterator;
```
Code snippets show how to call the methods.
```cs
var cyrillicText = "Съученичките Мария и Дияна скачаха с бънджи.";

var options1 = new TransliterationOption
{
    TransliterationRuleset = TransliterationRuleset.Basic,
    UrlCompatibility = false,
    WordSeparator = '-',
};

// If we miss the TransliterationOption param we will use the default values.
// We can see it in the example above "option1".
var latinText0 = Transliterator.CyrillicToLatin(cyrillicText);
// The result is : Sauchenichkite Mariya i Diyana skachaha s bandzhi.

var latinText1 = Transliterator.CyrillicToLatin(cyrillicText, options1);
// The result is : Sauchenichkite Mariya i Diyana skachaha s bandzhi.

var options2 = new TransliterationOption
{
    TransliterationRuleset = TransliterationRuleset.Bulgarian,
};

var latinText2 = Transliterator.CyrillicToLatin(cyrillicText, options2);
// The result is : Sauchenichkite Maria i Diyana skachaha s bandzhi.
// One of the differences between the Basic and Bulgarian rule set you can see in the name "Мария".
// According to the Article 5(2) of the Transliteration Law.

var options3 = new TransliterationOption
{
    TransliterationRuleset = TransliterationRuleset.Bulgarian,
    UrlCompatibility = true,
};

var latinText3 = Transliterator.CyrillicToLatin(cyrillicText, options3);
// The result is : sauchenichkite-maria-i-diyana-skachaha-s-bandzhi

var options4 = new TransliterationOption
{
    TransliterationRuleset = TransliterationRuleset.Bulgarian,
    UrlCompatibility = true,
    WordSeparator = '_',
};

var latinText4 = Transliterator.CyrillicToLatin(cyrillicText, options4);
// The result is : sauchenichkite_maria_i_diyana_skachaha_s_bandzhi

var listOfCyrillicTexts = new List<string>()
{
    "Съученичките Мария и Дияна скачаха с бънджи.",
    "Полета от високо е опасен и вдига адреналина.",
    "На следващият ден двете момичета разказаха на приятелите си."
};

var listOfCyrillicTexts0 = Transliterator.CyrillicToLatin(listOfCyrillicTexts);
// The result is :
// - Sauchenichkite Mariya i Diyana skachaha s bandzhi.
// - Poleta ot visoko e opasen i vdiga adrenalina.
// - Na sledvashtiyat den dvete momicheta razkazaha na priyatelite si.

var listOfCyrillicTexts1 = Transliterator.CyrillicToLatin(listOfCyrillicTexts, options1);
// The result is :
// - Sauchenichkite Mariya i Diyana skachaha s bandzhi.
// - Poleta ot visoko e opasen i vdiga adrenalina.
// - Na sledvashtiyat den dvete momicheta razkazaha na priyatelite si.

// The similar description is valid and for the methods LatinToCyrillic

var latinText = "Sauchenichkite Mariya i Diyana skachaha s bandzhi.";
var cyrillicText = Transliterator.LatinToCyrillic(latinText);
// The result is : Саученичките Мария и Дияна скачаха с банджи.
// But in transliteration via Basic ruleset from Latin to Cyrillic have small percentage inaccuracies.
```

# Transliteration law

The full text on Transliteration Law you can [read here (on Bulgarian).](https://www.lex.bg/laws/ldoc/2135623667)

#### Basic character pairs

| Cyrillic  |   Latin   |
|-----------|-----------|
|   А, а    |   A, a    |
|   Б, б    |   B, b    |
|   В, в    |   V, v    |
|   Г, г    |   G, g    |
|   Д, д    |   D, d    |
|   Е, е    |   E, e    |
|   Ж, ж    |   Zh, zh  |
|   З, з    |   Z, z    |
|   И, и    |   I, i    |
|   Й, й    |   Y, y    |
|   К, к    |   K, k    |
|   Л, л    |   L, l    |
|   М, м    |   M, m    |
|   Н, н    |   N, n    |
|   О, о    |   O, o    |
|   П, п    |   P, p    |
|   Р, р    |   R, r    |
|   С, с    |   S, s    |
|   Т, т    |   T, t    |
|   У, у    |   U, u    |
|   Ф, ф    |   F, f    |
|   Х, х    |   H, h    |
|   Ц, ц    |   Ts, ts  |
|   Ч, ч    |   Ch, ch  |
|   Ш, ш    |   Sh, sh  |
|   Щ, щ    |   Sht, sht|
|   Ъ, ъ    |   A, a    |
|   Ь, ь    |   Y, y    |
|   Ю, ю    |   Yu, yu  |
|   Я, я    |   Ya, ya  |

#### Bulgarian specific rules and exceptions

|   Cyrillic        |   Latin           |                           Description                                 |
|-------------------|-------------------|-----------------------------------------------------------------------|
| ия                | ia                | Article 5(2): In case these two letters are at the end of the word.   |
| България          | Bulgaria          | Article 6                                                             |
| Стара планина     | Stara planina     | Article 7(1)                                                          |
| Атанасовско езеро | Atanasovsko ezero | Article 7(1)                                                          |
| Нос Емине         | Cape Emine        | Article 7(2)                                                          |
| Централен Балкан  | Tsentralen Balkan | Article 7(3)                                                          |
| София-юг          | Sofia-yug         | Article 7(3)                                                          |
| Перник-север      | Pernik-sever      | Article 7(3)                                                          |
| Златни пясъци     | Zlatni рyasatsi   | Article 8                                                             |
| Горна Оряховица   | Gorna Oryahovitsa | Article 8                                                             |

# Friends and Supporters

Waiting for the first friends! :) 

# To-Do List

 - Acception generic objects as parameters in transliteration methods.
 - Extending exception support.
 - Adding specific rules for other languages.

# Author

#### Petar Dakov

* [LinkedIn](https://bg.linkedin.com/in/dakov)
* [Personal Website](http://dakov.net/)

# License

[![License](http://img.shields.io/:license-MIT-blue.svg)](https://licenses.nuget.org/MIT)