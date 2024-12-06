## H7 Uhagre2

## Käyttöympäristö

Prosessori: AMD Ryzen 5 5500H

RAM: 8 GB DDR4

Näytönohjain: NVIVIA GeForce RTX 2050

OS: Windows 10

## Ratkaise CryptoPals Set 1 -haasteet. Tehtävät saa ratkaista millä vain ohjelmointikielellä ja käyttää mitä tahansa tekstieditoria tai IDE:ä. Tehtäviä ei kannata ratkaista tekoälyllä, koska se vain kopioi malliratkaisun suoraan koulutusmateriaalistaan. 

### a) 1. Convert hex to base64

Aloitin avaamalla ensimmäisne haasteen. Seuraavaksi avasin microssa uuden tiedoston nimeltä `challenge1`.

    $ micro challenge1.py

En oikeastaan keksinyt miten voisin kääntää hex-stringin base64 muotoon, joten lähdin suoraan tutkimaan asiaa netistä. Törmäsin (he3, 2022) artikkeliin hex-merkkien kääntämisestä base64-merkeiksi. Kokeilin luoda oman koodini tämän pohjalta hyödyntäen myös materiaalissa olevia vinkkejä. 

![hextobase64](Kuvat/hextobase.png)

Tässä vielä tehtävän tulos: 

![challenge1 result](Kuvat/c1result.png)

### b) 2. Fixed XOR 

Tehtävä oli täysin hepreaa itselle, joten lähdin etsimään vinkkejä netistä kuinka yhdistää xor-merkkijonot yhteen pythonissa. Löysin netistä (Kültekin, Ö. 2021) artikkelin, josta sain apua tehtävään, sillä edes teron vinkit eivät auttaneet minua tehtävässä. Loin ohjelman nettisivun pohjalta: 

![challenge2 code](Kuvat/challenge2.png)

Tässä vielä koodi käännettynä: 

![Challenge 2 result](Kuvat/c2result.png)

## lähteet

- Karvinen, T. 4.12.2024. Tehtävänanto. h7-uhagre2 Luettavissa: https://terokarvinen.com/application-hacking/#h7-uhagre2 Luettu: 5.12.2024.
- He3. 2022. Hex to Base64: Converting Hexadecimal to Base64 Easily. Luettavissa: https://he3app.com/blogs/hex-to-base64-converting-hexadecimal-to-base64-easily Luettu: 5.12.2024.
- 


