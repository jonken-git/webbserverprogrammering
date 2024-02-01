# Dynamiska och Statiska Webbservrar
För att kunna lägga upp sin egen sida på internet behöver man antingen en statisk webbserver eller en dynamisk. Vilken typ av server du väljer beror på funktionaliteten på din hemsida. 
## Statiska webbservrar
Först ska vi förstå ordet statisk, [Synonymer.se](https://www.synonymer.se/sv-syn/statisk) säger följande: stillastående, oföränderlig och orörlig. Det ger oss ganska bra ledtrådar om vad en statisk webbserver innebär. 

En statisk webbserver skickar helt enkelt filer i deras befintliga skicka utan att göra modifieringar till dom. Hemsidor som hör hemma här kan vara:
+ Landningssida för ett företag
+ En enklare blogg
+ Informationssidor, exempelvis wiki

Dessa sidor ser likadana ut och beter sig likadant oavsett vem det är som besöker dom, innehållet är inte inställt efter användaren på något sätt.

## Dynamiska webbservrar
Motsattsordet till statisk är dynamisk, alltså något som är föränderligt. De flesta hemsidor du använder dig av idag är antagligen hostade på dynamiska webbservrar. Om vi går till exempelvis [Vklass](https://www.vklass.se/) så kommer innehållet på sidan skilja sig drastiskt, trots att vi står på samma adress (förutsatt att vi har loggat in).

Servern kan alltså läsa in vad just du ska kunna se och bygger sedan dynamiskt upp varje sida med ditt personliga innehåll. Det är en vesäntlig egenskap för att kunna bygga webbplatser med funktionalitet som användarna kan interagera med, tänk sociala medier, webbshoper. Det här typen av webbplats kallas ofta för webbapplikation.

Samspelet mellan klient och server är viktigt att förstå för att kunna bygga dynamiska siter. När ni skriver ```PHP```-kod så vet inte klienten om det, klienten får bara en ```HTML```-fil från servern som dynamiskt har byggts upp med ```PHP```. Alltså, koden ni skriver i ```PHP``` körs _enbart_ på webbservern. Det kan ni se om ni väljer att inspektera sidkällan i er webbläsare.

Vi kan titta på kodexemplet nedan.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
<?php
    for($i = 0; $i < 10; $i++)
    {
        if($i % 2 == 0)
        {
            echo("<b>" . $i . "</b>") . PHP_EOL;
        } 
        else 
        {
            echo("<i>" . $i . "</i>") . PHP_EOL;
        }
        echo("<br/>") . PHP_EOL;
    }
?>
</body>
</html>
```
I koden ovan så kan vi se att vi är i en ```PHP```-fil, vi har en loop där vi skriver ut ett tal innanför en ```<b>```-tag om det är jämnt, annars så skriver vi ut det mellan i ```<i>``` tag. Vi avslutar sen med en radbrytning. (Ignorera PHP_EOL).

Nedanför så ser vi ```HTML```-filen som vi har tagit emot i vår webbläsare. Den har alltså dynamiskt generats på servern.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
<b>0</b>
<br/>
<i>1</i>
<br/>
<b>2</b>
<br/>
<i>3</i>
<br/>
<b>4</b>
<br/>
<i>5</i>
<br/>
<b>6</b>
<br/>
<i>7</i>
<br/>
<b>8</b>
<br/>
<i>9</i>
<br/>
</body>
</html>
``` 
