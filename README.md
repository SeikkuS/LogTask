# x)

THE FUTURE OF EMPLOYMENT: HOW SUSCEPTIBLE ARE JOBS TO COMPUTERISATION?

Lähde: https://www.oxfordmartin.ox.ac.uk/downloads/academic/The_Future_of_Employment.pdf

- Artikkelissa mainitaan alussa että keskimäärin 47% Yhdysvaltojen työpaikoista ovat vaarassa siirtyä tietokoneella pyöritettäväksi automaattiseksi työksi.

- Artikkelissa on otettu huomioon mm. koneoppimisen (Machine Learning) sekä robotiikan (Mobile Robotics) sekä tekoälyn (Artificial Intelligence) kehittyminen ja hyödyntämisen lisääntyminen. 

- Iso syy tietokoneellistamisen yleistymiselle on teknologisten palveluiden jatkuvasti laskevat hinnat. 

# a)

30.1. klo 9.25

    cd var/log/
    cat syslog
    
Valitsin riviksi: 

    ![kuva](https://user-images.githubusercontent.com/105205141/215414776-7fb8f28c-9f02-4a16-9b8b-f233c2ee580b.png)
    
Tässä rivissä päivä on 30.1. ja aika on 9.30 (oikeassa aikavyöhykkeessä). Ilmoitus sanoo että hostname service on onnistuneesti käynnistynyt. Kävin katsomassa mitä hostname service tekee selaimella ja vastaukseksi sain:

systemd-hostnamed.service is a system service that may be used to change the system's hostname and related machine metadata from user programs.

klo 9.35

    cat auth.log
    
 ![kuva](https://user-images.githubusercontent.com/105205141/215415986-4851c2be-9fe3-4bb1-b745-88f250379c29.png)
 
 tässä rivissä päivä ja aika on oikein. En ymmärtänyt, mitä rivissä tarkoitetaan, joten tutkin mitä kyseinen rivi tekee ja sain vastaukseksi tämän: 
  It simply runs a root session which executes run-parts and then closes the session.
  
klo 9.41

  tein kyseisen tehtävän eri koneella, jossa on asennettuna Ubuntu, ja huomasin että 
  
      sudo apt-get-install apache2
      
 ei ole Ubuntussa toimiva komento, tutkin mikä oikea komento Ubuntulla on. Oikea komento oli
 
      sudo apt install apache2
      
      cat apache2/access.log
      
 en ollut vielä yrittänyt yhdistää apache2 palvelimeen, joten cat-komento ei tulostanut mitään.
 
 ![kuva](https://user-images.githubusercontent.com/105205141/215417623-5a0b262a-dc5b-44dd-af9e-456265daf933.png)

yhdistin apache2 palvelimeen käynnistettyäni sen, jolloin sain tällaisen rivin access.logiin

![kuva](https://user-images.githubusercontent.com/105205141/215418133-2816ee3a-d174-4ea1-a6f2-79ef7abc1405.png)

aika ja päivä on oikein, logi kirjoittaa myös aikavyöhykkeen (+0200). Kyseinen rivi yrittää get-komennolla hakea favicon.ico (ikonia) ja 404 koodi viittaa siihen että kyseistä ikonia ei löydy. Logissa näkyy, että palvelimelle on yhdistetty Firefoxilla ja kyseisen palvelimen linkki, johon yhdistettiin: http:/localhost/.


    cat apache2/error.log
    
![kuva](https://user-images.githubusercontent.com/105205141/215421238-4581357f-8832-4dbc-97d1-78e674c2f2d9.png)

klo 10.05

tässä näkyy päivä ja aika oikein (millisekuntien tarkkuudella). Kyseinen rivi on siis toteutunut klo 9.45 siinä näkyy Apache 2 versio Apache 2.4.52 ja version käyttöjärjestelmä (Ubuntu). 

# b)

Yritin aiheuttaa errorin Apache2 palvelimeen, sain sivun näyttämään error 404 hakemalla sivussa http://localhost/test, mutta kyseinen error ei ilmestynyt error.logiin
