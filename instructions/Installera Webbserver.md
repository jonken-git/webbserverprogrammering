# Installera Webbserver

## 1. Apache
1. Surfa till [Apache](https://httpd.apache.org) och leta reda på länken i första stycket som nämner _third party vendors._ Här kommer ni se ett antal länkar, klicka på _Apache Lounge_.
2. Ladda ned senaste versionen för 64-bitars Windows.
3. Lägg i roten till C: och döp mappen till apache24, alltså namnet på versionen du precis laddat ned. Sökvägen ska bli något i stil med C:/apache24
4. Öppna cmd som administratör. Följ installationsprocessen som står i readme-filen.
5. Starta _Apache Monitor_ (C:/apache24/bin/Apache Monitor.exe) och starta din webbserver därifrån.
6. Surfa till _localhost_ i din webbläsare för att se om det funkar. Om det funkar ser du antingen en massa information om Apache eller bara texten _"It works!"_.
*GÅ BARA VIDARE OM STEG 1 FUNKAR*

## 2. PHP
1. Surfa till [PHP](https://windows.php.net) och gå till _Downloads_.
2. Leta reda på version 8.2 av PHP som är Thread Safe.
3. Lägg i roten till C: och döp mappen till php82. Sökvägen ska bli C:/php82
4. Navigera till _httpd.conf_ i din _apache/conf_-mapp och ändra eller lägg till föjande
    + LoadModule php8_module "C:/php82/php8apahce2_4-dll"
    + AddHandler application/x-httpd-php.php
    + PHPIniDir "C:/php74"
5. Starta om din webbserver via _Apache Monitor_ och se att ikonen blir grön.
6. Surfa till _localhost_ och se att resultatet är som tidigare.
*GÅ BARA VIDARE OM STEG 1 OCH 2 FUNKAR*

## 3. WWW
1. Skapa en till mapp i C: som heter www.
2. Öppna _httpd.conf_ och sök efter "htdocs" (du ska få 2 träffar). Där ska du ändra sökvägen till mappen du precis skapat. Alltså C:/www
3. Starta om din webbserver via _Apache Monitor_ och se att ikonen blir grön.
4. Skapa C:/www/index.php med följade 3 rader.
```php
<?php
phpinfo();
?>
```
5. Surfa till _localhost_. Nu ser du antingen PHP-loggan och en väldigt stor mängd information, eller så ser du en lista med 1 fel, klicka på den isåfall.

## 4. Extra konfiguration
1. Gå till php-mappen C:/php82. Här kan du hitta 2 stycker filer som heter _php.ini_, en som heter _development_ och en som heter _production_.
2. Kopiera den som heter _development_ och döp den till php.ini.
3. Starta om din webbserver via _Apache Monitor_ och se att ikonen blir grön.
4. Surfa till _localhost_ och leta efter _Loaded Configuration File_ som bör visa php.ini-filen du precis skapade.
