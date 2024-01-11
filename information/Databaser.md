# Databaser
## Kapitel 17 MySQL och andra databaser

### Allmänt om databaser

#### När de används

En stor del av, eller kanske alla webbplatser du besöker ute på nätet har något system för att hantera sitt innehåll. En gästbok, eller ett forum eller en site med nyheter har i regel någon typ av formulär där man kan skriva information som sedan lagras dynamiskt på webbservern. Sedan kanske en administratör kan logga in och ändra denna text och allt detta hanteras helt utan att någon behöver ändra något i HTML-koden.
Databaser används i samband med i princip alla kända webbplatser, allt från nyhetssiter, communityn, bloggar till avancerade verktyg såsom simulatorer och betalsystem.

#### Olika databassystem

För att lagra något i en databas så behöver man först och främst ett databashanteringssystem. Det finns flera olika stora system, några av de största är MySQL, Microsoft SQL (Mssql) och Oracle. 
Alla har olika styrkor och svagheter, men det spelar i regel ingen större roll vilket som används rent praktiskt eftersom de är ganska lika i både hur de används och hur de presterar. Men när man arbetar med PHP så är det överlägset vanligast att använda MySQL, vilket är för att PHP har ett väldigt utbrett stöd för det och för att MySQL både är blixtsnabbt, lättanvänt och gratis.

### MySQL

MySQL är det databassystem vi kommer att använda oss av framöver. Det är gratis, det är ursprungligen svenskt (_MySQL AB_ i Uppsala) och det är kanske den vanligaste databashanteraren som finns, vilket gör det väldigt lätt att hitta lösningar på problem på nätet eftersom det finns massor av kompetenta databastekniker.

### Hur man arbetar med en databas

Man arbetar med databaser genom att skriva kommandon, ungefär som programmering. Du kan skriva ett kommando som "jag vill stoppa in talet 7 och texten 'hej' i databasen". Man kan även formulera "jag vill hämta alla personer i databasen som heter 'Kalle'". Båda dessa kan formuleras med SQL (**S**tructured **Q**uery **L**anguage) som är det språket som används när man kommunicerar med databashanteraren.

Själva kommunikationen med databasen kan man göra direkt från Windows via terminalen om man vill, eller att man laddar ned ett gränssnitt för att komma åt databasen på ett smidigt sätt. 
När vi jobbar med webbplatser så sköter vi all kommunikation via PHP som skickar meddelanden till MySQL och får svar tillbaka med den informationen som behövs.

### Vad MySQL består av
![TW Bild Databas exempel](image.png)
MySQL är en **databashanterare** som består av en eller flera **databaser**. Oftast har man en databas
per webbplats, så driver du tre skilda webbplatser så har du sannolikt tre databaser.

Varje databas består av en eller flera **tabeller**. En tabell är i praktiken en lista med saker, t.ex. en lista med användare, nyhetsinlägg, galleribilder eller någon annan typ av data som hanteras dynamiskt. Med dynamisk data menar vi alltså sånt som du kan ändra på, lägga till och ta bort osv. Motsatsen är statisk data som till exempel en HTML-fil som alltid serverar ssamma innehåll.

Varje tabell innehåller bara en typ av data (lista), så du har en tabell för användare, en annan för nyheter och en tredje för galleribilder osv. En webbplats kan mycket väl ha allt från *3* till *50* tabeller för att hålla koll på alla sina användare, inloggningar, nyheter och övrigt innehåll.

När man vill lagra en person i sin lista med användare så har ju denna person ett gäng egenskaper.  Man behöver kanske ett _användarnamn_ , _lösenord_ , _e-postadress_ och allt vad det nu kan vara. Dessa egenskaper i en tabell kallas fält. En tabell innehåller normalt 3 – 30 fält. Du kan försöka komma på 5 till som kan vara intressant att ha so fält i en tabell som lagrar användare.

## Grundläggande SQL-frågor

### Alla databashanterare använder kommandon

När man kommunicerar med sin databas (oavsett om det är MySQL eller någon annan databashanterare) så skriver man kommandon till databashanteraren tillsammans med de eventuella uppgifter som ska föras in i databasen.

### MySQL-frågor

Låt oss titta på ett exempel på en tabell och titta hur vi kan arbeta med den.

Tabell: personer

| id | förnamn | efternamn | ålder |
|---|---|---|-----|
| 1 | Adam | Eriksson | 17 |
| 2 | Nils | Andersson | 18 |
| 3 | Arnold | Sten | 55 |
| 4 | Kalle  | Svensson | 21 |

#### Mata in data - INSERT
I den här tabellen har vi några personer från början så ska vi titta hur man gör för att stoppa in ytterligare en person i tabellen.

```INSERT INTO my_table (field1, field2) VALUES(value1, value2)```

Logiken är att frågan för att lägga in en rad i databasen med en INSERT-fråga inleds med INSERT INTO.
Efter det skriver man tabellen som man ska lägga in innehållet i. Sedan anger man vilka fält som ska användas (field1, field2, fieldN) följt av ordet VALUES och alla värden (value1, value2, valueN).

Om vi ska skapa en person i tabellen som heter Lars Stenberg som är 60 år så skriver man såhär:
```sql
INSERT INTO personer (namn, ålder) VALUES('Lars Stenberg', 60)
```

De ord som ingår i språket MySQL, alltså allt förutom dina egna tabell- och fältnamn samt de värden
som matas in skrivs med VERSALER (stora bokstäver). Det gör inget om man slarvar med det
eftersom det inte har någon betydelse som funktion, dock blir koden lättare för dig att läsa och
arbeta med om man försöker hålla sig till det tankesättet. Efter ovanstående INSERT-fråga ser
tabellen ut såhär:

| id | förnamn | efternamn | ålder |
|---|---|---|-----|
| 1 | Adam | Eriksson | 17 |
| 2 | Nils | Andersson | 18 |
| 3 | Arnold | Sten | 55 |
| 4 | Kalle  | Svensson | 21 |
| 5 | Lars  | Stenberg | 21 |

Alltså, en ny rad med id 5 har skapats, med Lars Stenberg, 60.

#### Hämta data - SELECT

Om du istället vill hämta information från tabellen använder du en SELECT-fråga. Om du vill hämta
alla rader och alla fält från tabellen personer så kan du skriva såhär:

```sql
SELECT * FROM personer
```

Det som hämtas nu är alltså den fullständiga tabellen med allt innehåll, alltså:

| id | förnamn | efternamn | ålder |
|---|---|---|-----|
| 1 | Adam | Eriksson | 17 |
| 2 | Nils | Andersson | 18 |
| 3 | Arnold | Sten | 55 |
| 4 | Kalle  | Svensson | 21 |
| 5 | Lars  | Stenberg | 21 |

Om du bara vill hämta fälten id och ålder och totalt ignorerar namnen kan du istället skriva:
```SELECT id, ålder from personer```
... och få följande resultat:

 Tabell: personer
| id | ålder |
|----|-----|
| 1 | 17 |
| 2 | 18 |
| 3 | 55 |
| 4 | 21 |
| 5 | 60 |

Du kan alltid manuellt välja vilka fält du vill hämta, **\*** hämtar alla, annars skriver du alla fält du vill ha kommaseparerade med varandra. ```(SELECT a,b,c,d FROM tabell)```.
Om du inte vill hämta alla rader, utan t.ex. alla personer som är äldre än 20 så kan du skriva:
```SELECT * FROM personer WHERE alder > 20```
Du kan även kombinera WHERE med att bara hämta vissa utvalda fält, som t.ex:
```SELECT namn FROM personer WHERE alder >= 21```

Vilket ger följande resultat:

Tabell: personer
namn
Arnold Sten
Kalle Svensson
Lars Stenberg
Det går att skriva väldigt avancerade SELECT-frågor där man kan kombinera diverse påståenden fritt
för att bara hämta precis det man behöver.

SELECT * FROM personer WHERE id = 1 OR (ålder > 20 AND ålder <= 40)

Vad gör ovanstående rad? Jo, den hämtar alla rader som har id 1 eller som har en person vars ålder
är större än 20 men samtidigt max 40 (mindre eller lika med 40). Den hämtar alltså _Adam_ och _Kalle_!

