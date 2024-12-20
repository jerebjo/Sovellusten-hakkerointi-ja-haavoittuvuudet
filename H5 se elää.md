## H5 Se elää!

## Käyttöympäristö

Prosessori: AMD Ryzen 5 5500H

RAM: 8 GB DDR4

Näytönohjain: NVIVIA GeForce RTX 2050

OS: Windows 10

## a) Lab1. Tutkiminen mikä on ohjelmassa vialla ja miten se korjataan. lab1.zip (22.11.2024)

Aloitin lataamalla `lab1` zip-tiedoston ja siirsin sen käyttäjä kansioon. Sen jälkeen ihan ensimmäiseksi kokeilin mitä ohjelma tekee kun sen ajaa: 

    $ ./gdb_example1

![ajotesti](Kuvat/ajotesti.png)

En oikein ymmärtänyt mitä tuo tarkoitti, joten aloin debuggamaan ohjelmaa tunnilla käytyjen ohjeiden mukaan. Käänsin ohjelman ja avasin debuggaus ohjelman komennoilla:

    $ gcc gdb_example1.c -g -Wall -Werror -o example1-gdb
    $ gdb example1-gdb 
    
![list](Kuvat/examplelist.png)

Aloitin debuggauksen siirtymällä `layout split` näkymään, jossa sitten pläräsin koodia eteenpäin: 

    $ break main
    $ run
    $ p(char*) $(esim rdi)
    $ nexti

Mennessäni eteenpäin ohjelmassa huomasin yhden error viestin joka näkyy kuvassa: 

![error](Kuvat/outoerror.png)

Tässä kohtaan päätin vielä siirtyä eteenpäin ja katsoa mitä tapahtuu.

![error2](Kuvat/goodmessage.png) 

Ohjelma antaa omituisia arvoja joita minulla oli hankaluuksia ymmärtää. Selasin silti vielä eteenpäin: 

![ohjelman lopetus](Kuvat/ohjelmanlopetus.png)

Jos ymmärrän kuvaa oikein niin ongelma on rivillä 7, joten lähdin tutkimaan koodia micro editorissa: 

    $ micro gdb_example1.c

Päätin lähteä googlaamaan mitä "segmentation fault" oikein tarkoittaa. (Samer, M. 2023) mukaan segmentation fault on virhe kun ohjelma yrittää päästä käsiksi muistiin johon sillä ei ole oikeuksia. Koska ohjelmassa on annettu `bad_messagen` arvoksi `NULL` ohjelma ei toimi oletetulla tavalla. Tein koodiin seuraavat korjaukset: 

![virheviesti](Kuvat/virheviesti.png)

Eli jos viestin arvo on `NULL` ohjelma palauttaa sen oikein eikä hajoa: 

![lab1fixed](Kuvat/fixedcode.png)

## b) Lab2. Selvitä salasana ja lippu + kirjoita raportti siitä miten aukesi. lab2.zip 

Latasin ensin tiedoston ja purin zip-tiedoston. Seuraavaksi käänsin ohjelman ja ajoin debuggerin: 

    $ gcc passtr.c -g -Wall -Werror -o passtr1
    $ gdb passtr1
    $ layout split

![layoutsplit2](Kuvat/lsplit.png)

Yritin pitkään mennä koodissa eteempäin ja ajaa esim. `p(char*) $rax`, mutta en millään saanut mitään järkevää. Sain kyllä tuolla tavalla esiin "sala-hakkeri-321", mutta, en usko tehtävässä haettiin aivan sitä. Arvelin, että tällä tehtävällä on jotain tekemistä ASCII-taulukon kanssa, mutta en osannut poimia debuggerin avulla oikeita arvoja joita verrata taulukkoon. Jätin tehtävän tähän...

![lab2](Kuvat/lab2.png)

## c) Lab3. Kokeile Nora Crackmes harjoituksia tehtävä 3 ja 4 ja loput vapaaehtoisia. Tindall 2023: NoraCodes / crackmes. 

### Tehtävä 3.

Aloitin tehtävän kääntämällä sen ja avaamalla ohjelman debuggerissa:

    $ gcc crackme03.64 -g -Wall -o crackme03
    $ gdb crackme03
    $ list

Tämän jälkeen siirryin layout split näkymään ja laitoin breakpointin `main`-funktioon ja selasin koodia rivi kerrallaan. 

    $ layout split
    $ break main
    $ run 

Selasin koodia pitkään kokeilemalla eri asioita, mutta mikään ei tuntunut antavan vihjeitä. Huomasin, että koodissa on kohta, jossa lukee salasanan oikea pituus ja merkkijono mihin salasanaa verrataan: 

![lab3](Kuvat/lab3.png) (23.11.2024) 

Koodissa oli myös maski ja arvot joiden perusteella merkkijono muutetaan oikeaksi salasanaksi. Lähdin ihmettelemään ASCII-taulukkoa. Yritin verrata ASCII-taulukossa olevia arvoja merkkijonoon, joka oli kirjoitettu koodiin "lAmBdA". Maskissa oli arvoja ja ne olivat '{2, 3, 2, 3, 5}' Arvelin, että ne lisätään alkuperäiseen arvoon, joten kokeilin lisätä ne merkkijonoon ja siten muodostaa uuden: 

![ASCII](Kuvat/ASCIItable.png)

- l = 108 + 2 = 110 "n"
- A = 65 + 3 = 68 "D" 
- m = 109 + 2 = 111 "o"
- B = 66 + 3 = 69 "E"
- d = 100 + 5 = 105 "i"
- A = 65 +3 = 68 "D"

Eli maskattu salasana olisi "nDoEiD"

Sitten ajoin ohjelman ja päätin kokeilla. Se ei ollut oikein, joten aloin miettimään, että teinköhän jonkun kääntövirheen. Luulin ymmärtäneeni oikein, että maskissa on vain 5 numeroa, koska alkuperäisessä merkkijonossa on kaksi A-kirjainta. Tässä kohtaan testailin eri versioita, kunnes tajusin, että ehkä kuudetta kirjainta ei maskata ollenkaan, joten kokeilin uudelleen:

![lab3ratkaisu](Kuvat/lab3solution.png) 

Oikea salasana oli siis "nDoEiA" koska viimeistä kirjainta ei maskattu. En osaa sanoa, ratkaisinko tehtävän oikein, mutta tässä on miten itse ymmärsin tehtävän. 

### Tehtävä 4.


Tämän tehtävän aloitin testaamalla mitä koodi tekee ajessa. No idea oli samankaltainen kuin edellisessäkin, eli syötetään ohjelman ajon yhteydessä salasana. Lähdin liikkeelle siitä että käänsin koodin ja avasin debuggerin: 

    $ gcc crackme04.c -g -Well -Werror -o crackme04
    $ gdb crackme04

Seuraavaksi siirryin `layout split` näkymään: 

    $ layout split
    $ break main
    $ run

Liikuin koodia eteenpäin rivi kerrallaan `nexti` -komennolla ja tarkastelin eri arvoja printtaamalla ne, mutta en onnistunut saamaan ohjelmasta juuri mitään irti. Leikin ohjelmalla vielä pari tuntia ja lopulta päätin, että tämä riittää minulle. Katsotaan tunnilla miten tämä lopulta ratkaistiin. 

![lab4](Kuvat/kokeilu.png)
    



## Lähteet

- Iso-Anttila, L. Tehtävänanto. h5 Se elää! Luettavissa: https://terokarvinen.com/application-hacking/#h5-se-elaa Luettu: 22.11.2024
- Samer,M. 30.8.2023. Medium. Understanding Segmentation Fault in C: Causes and Solutions. Luettavissa: https://medium.com/@mohamedsamer1532/understanding-segmentation-fault-in-c-causes-and-solutions-ed3d1c159d76 Luettu: 22.11.2024.
- 23.11.2024. ASCII Table. Luettavissa: https://www.asciitable.com/ Luettu: 23.11.2024.
