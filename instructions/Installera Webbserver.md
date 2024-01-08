# Installera Webbserver

## 1. Apache
1. Surfa till [Apache](https://httpd.apache.org) och leta reda på länken i första stycket som nämner **third party vendors**. Här kommer du se ett antal länkar, klicka på **Apache Lounge**.
1. Ladda ned senaste versionen för 64-bitars Windows.
1. Lägg i roten till **C:** och döp mappen till **apache24**, alltså namnet på versionen du precis laddat ned. Sökvägen blir då **C:/apache24**
    1. Dubbelkolla så att du inte har fått en mappstruktur som ser ut som **C:/Apache24/apache24**. Om du har flera nivåer än en får du flytta innehållet och sen ta bort den tomma mappen.
1. Öppna cmd som administratör. Följ installationsprocessen som står i ReadMe-filen.
1. Starta _Apache Monitor_ (**C:/apache24/bin/Apache Monitor.exe**) och starta din webbserver därifrån. Om det är helt tomt i _Apache Monitor_ har du inte följt instruktionerna i ReadMe-filen. Tips: Du vill installera Apache som en service
1. Surfa till **localhost** i din webbläsare för att se om det funkar. Om det funkar ser du antingen en massa information om Apache eller bara texten **"It works!"**.

*GÅ BARA VIDARE OM STEG 1 FUNKAR*

## 2. PHP
1. Surfa till [PHP](https://windows.php.net) och gå till **Downloads**.
1. Leta reda på version 8.2 av PHP som är Thread Safe.
1. Lägg i roten till C: och döp mappen till php82. Sökvägen ska bli **C:/php82**
1. Navigera till **httpd.conf** i din **C:/apache24/conf**-mapp och ändra eller lägg till föjande
    ```apacheconf
    # PHP modul för apache
    LoadModule php_module "C:/php82/php8apache2_4.dll"
    # Hantera våra filer som slutar med .php
    SetHandler application/x-httpd-php .php
    # Mappen där vår config-fil för PHP finns
    PHPIniDir "C:/php82"
    ```
1. Starta om din webbserver med **Apache Monitor** och se till att ikonen blir grön.
1. Surfa till **localhost** och se att resultatet är som tidigare.

*GÅ BARA VIDARE OM STEG 1 OCH 2 FUNKAR*
### 2.1 PHP Path
Lägg till PHP till dina miljövariabler.
1. Tryck på Windowsknappen och sök efter **Miljövariabler**, välj alternativet som heter något i stil med **Redigera systemets miljövariabler**. 
    1. Välj "Miljövariabler"
    1. I den övre listan, markera variabeln **Path** och välj **Redigera...**
    1. Klicka på **Ny** och skriv in sökvägen till din PHP-mapp (borde vara **C:/php82**)
    1. Klicka **OK** i alla rutor som du öppnat (borde vara 3st).
1. Öppna en **NY** konsol och skriv ```php --version``` för att bekräfta att PHP lagts till i din **Path**, du får lite information som till exempel PHPs version.
    1. Om du inte får någon information gör följande:
        1. Gå till dina miljövariabler och dubbelkolla att du angett rätt sökväg till din PHP-mapp.
        1. Start om datorn.

## 3. WWW
1. Skapa en till mapp i C: som heter www.
1. Öppna **httpd.conf** och sök efter "htdocs" (du ska få 2 träffar). Där ska du ändra sökvägen till mappen du precis skapat. Alltså **C:/www**. Om du vill kan du skata en variabel till din sökväg på följande sätt.
    ```apacheconf
    # My server root 
    Define WWWROOT "C:/www"
    DocumentRoot "${WWWROOT}"
    <Directory "${WWWROOT}">
        # 
        # Possible valies for the Options directive are "None", "All"
        ...
    </Directory>
    ```
1. Scrolla ner lite eller sök efter "DirectoryIndex" och lägg till "index.php" framför "index.html". Det berättar för din webbserver att leta efter antingen index.php eller index.html om du har surfat till en mapp.
    ```apacheconf
    DirectoryIndex index.php index.html
    ```
1. Starta om din webbserver med **Apache Monitor** och se att ikonen blir grön.
1. Skapa **C:/www/index.php** med följade 3 rader.
    ```php
    <?php
    phpinfo();
    ?>
    ```
1. Surfa till **localhost**. Nu ser du antingen PHP-loggan och en väldigt stor mängd information, eller så ser du en lista med 1 fil, klicka på den isåfall.
Om du inte ser något testa att starta om datorn

## 4. PHP Konfiguration
1. Gå till php-mappen **C:/php82**. Här kan du hitta 2 stycken filer, en som heter **php.ini-development** och en som heter **php.ini-production**.
1. Kopiera den som heter **development** och döp den till php.ini.
1. Starta om din webbserver med **Apache Monitor** och se att ikonen blir grön.
1. Surfa till **localhost** och leta efter **Loaded Configuration File** som bör visa **php.ini**-filen du precis skapade.
