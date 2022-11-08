# salt1

Ensiksi pitää luoda master ja minion.

sudo apt-get update

sudo apt-get -y install salt-master salt-minion

Kun olet saanut luotua masterin ja minionin onnistuneesti sinun pitää resettaa minioni, jotta se voi saada yhteyden masteriin.

sudo systemctl restart salt-minion.service

sen jälkeen komennolla sudo salt-key -A ja hyväksymällä "yes".

Masteri antaa käyttöohjeet minionille joten ensiksi pitää luoda kansio /srv/salt/

sudo mkdir -p /srv/salt/ 

tämän jälkeen voidaan luota hello.sls tekstieditorilla.

sudoedit /srv/salt.hello.sls
 /tmp/hellojarkko.txt:
   file.managed:
     -source: salt://hellojarkko.txt
     
     sudo salt ´*´ state.apply hello
     
     sudoedit /srv/salt/top.sls
     base:
        '*':
            - hello
            
   sudo salt '*' state.highstate
   
   grains.item komennolla saat tietoja koneesta esim. local grains.item interface ipv4 saat koneen ip osoitteen. Komento grains.items itsessään listaa kaikki koneen tiedot.
   
   
   
