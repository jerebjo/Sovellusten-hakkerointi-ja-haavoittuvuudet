# H6 Sulaa hulluutta

## Käyttöympäristö

Prosessori: AMD Ryzen 5 5500H

RAM: 8 GB DDR4

Näytönohjain: NVIVIA GeForce RTX 2050

OS: Windows 10

## a) Tutki tiedostoa h1.jpg jo opituilla työkaluilla. Mitä saat selville? (27.11.2024)

Aloitin tehtävän lataamalla kuvan, jotta pystyisin tarkastelemaan sitä terminaalin puolella: 

    $ wget https://terokarvinen.com/application-hacking/h1.jpg

Seuraavaksi lähdin tutkimaan mitä kuva sisältää: 

    $ file h1.jpg

![kuvantiedot](Kuvat/kuvantiedot.png)

Komennon avulla selvisi vähän lisätietoja kuvasta, mutta arvelempa, että se on syönyt muutakin. Lähdin seuraavaksi tutkimaan tiedostoa, `strings` -komennon avulla: 

    $ Strings h1.jpg | less

![Strings-komennon tulos](Kuvat/stringsh1.png)

`Strings`-komennon avulla tiedostosta löytyi omituisia merkkijonoja, mutta en oikein saanut koppia siitä mitä ne tarkoittavat. Päätin tutkia työkaluja netistä ja törmäsin (Piyushagg, 2021) -ohjeeseen exiftool-työkalusta. Päätin ladata työkalyn ja testata: 

    $ sudo apt-get install exiftool
    $ exiftool h1.jpg

![exiftool testi](Kuvat/exiftool.png)
