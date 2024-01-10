# Terminalen
Det är bra att ha grundläggande kunskap i hur man använder terminalen. Vissa program behöver köras eller installeras via terminalen.

## Kommandon
### Windows
#### cd
Navigera mellan mappar.
cd [mappens namn] för att gå till en mapp som finns i den mappen du befinner dig i.
```
C:\>cd .\Documents
C:\Documents>
# Nu har vi flyttats till mappen Documents, om vi vill backa tillbaks till C:\ kan vi göra på två sätt.
# .. betyder tillbaks ett steg
C:\Documents>cd .. 
# eller så kan vi skrev hela sökvägen
C:\Documents>cd C:
# Det funkar såklart lika om vi ska navigera till vilken mapp som helst
C:\Documents>cd C:\apache24\conf
```
#### dir
Listar innehållet i mappen du står i.
```
C:\www\cats\assets\images> dir
 Volume in drive C has no label.
 Volume Serial Number is 4C8F-9EC5

 Directory of C:\www\cats\assets\images> dir

2024-01-09  13:48    <DIR>          .
2024-01-09  13:48    <DIR>          ..
2024-01-08  17:27              2048 logo.png
2024-01-08  20:00    <DIR>          cats
2024-01-09  13:59    <DIR>          dogs
               1 File(s)             2048 bytes
               4 Dir(s)  430 011 715 584 bytes free

C:\www\cats\assets\images> dir
```
Här kan vi också se mapparna ".." och ".". 
".." pekar ett steg upp, i det här fallet mot mappen **assets**.
"." syftar på mappen vi för tillfället befinner oss i, alltså **images**.

#### code
Används för att starta VSCode eller öppna en fil med VSCode.
```
# Om vi anger ett filnamn efter kommer vi öppna den i VSCode.
C:\apache24\conf>code httpd.conf
# Om vi istället bara anger . kommer vi öppna mappen vi står i istället.
C:\www\mysite>code .
```