# H3 No Strings Attached

## Käyttöympäristö

Prosessori: AMD Ryzen 5 5500H

RAM: 8 GB DDR4

Näytönohjain: NVIVIA GeForce RTX 2050

OS: Windows 10

## a) Strings. Lataa ezbin-challenges.zip Aja 'passtr'. Selvitä oikea salasana 'strings' avulla. Selvitä myös lippu. (Ensisijaisesti katsomatta sorsia, jos osaat.) 

Aloitin lataamalla zip-tiedoston: 

      $ sudo apt-get update
      $ wget https://terokarvinen.com/loota/yctjx7/ezbin-challenges.zip
      unzip ezbin-challenges.zip

Seuraavaksi selvitin mitä 'strings' tarkoittaa Chat GPT:n avulla. Selvisi, että työkalun avulla voi selvittää mitä tekstijonoja tietty tiedosto sisältää. Ajoin seuraavan komennon: 

            $ strings passtr.c


            

