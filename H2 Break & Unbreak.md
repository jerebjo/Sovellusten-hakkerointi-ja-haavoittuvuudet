# H2 Break and unbreak

## x) Lue/katso/kuuntele ja tiivistä

### OWASP: OWASP Top 10: A01 Broken Access Control
- Noin 94% ohjelmista kärsii joistakin pääsynhallinnan ongelmista.
- Yleisiä heikkouksia ovat mm. pääsynhallinnan kiertäminen URL-muokkauksilla, Pääsynhallinnan puutteet API-kutsujen POST-, PUT- ja DELETE-toiminnoissa ja mahdollisuus tarkastella tai muokata toisen käyttäjän tietoja.
- Pääsynhallinta toimii tehokkaasti vain luotetussa palvelinpuolen koodissa. Pääsy tulisi estää oletuksena, ottamatta huomioon julkisia resursseja. Vahvista myös tietueen omistajuus ja rajoita CORS-käyttöä.

### Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf
- Web-palvelimilla on monesti salaisia hakemistoja, joita ei ole linkitetty mihinkään.
- Salaisia hakemistoja voi etsiä komennoilla kuten: /secret, /.svn ja /admin.
- Fuff on monipuolinen fuzzing työkalu. Sen avulla voidaan löytää piilotettuja hakemistoja. Sitä voi käyttää esim. otsikoiden ja POST-parametrien fuzzaukseen.

### PortSwigger: Access control vulnerabilities and privilege escalation 
- Pääsynhallinta tarkoittaa rajoituksia, sille kuka voi suorittaa tiettyjä toimintoja tai pääsee tiettyihin resursseihin.
- Verkkosovelluksissa pääsynhallinta perustuu autentikointiin ja istunnonhallintaan.
- Rikkoutuneet pääsynhallinnat ovat yleisiä ja usein vakavia tietoturvaongelmia. Pääsynhallinnan suunnittelupäätökset tehdään ihmisten toimesta, joten virheiden mahdollisuus on suuri.

### Karvinen 2006: Raportin kirjoittaminen
- Raportointi on sitä kun kirjoitat ja kerrot täsmällisesti mitä teit ja mitä tapahtui. Raporttia kannattaa kirjoittaa sitä mukaan kun toimit. 
- Hyvä raportti on toistettava, täsmälllinen, helppolukuinen ja siinä viitataan lähteisiin.




## Lähteet
- OWASP. 2021. OWASP Top 10: A01 Broken Access Control. Luettavissa: (https://owasp.org/Top10/A01_2021-Broken_Access_Control/) Luettu: 31.10.2024.
- Karvinen, T. 2023. Find Hidden Web Directories - Fuzz URLs with ffuf. Luettavissa: (https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) Luettu: 31.10.2024.
