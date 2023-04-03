# CIsco-packet-tracer-2
![image](https://user-images.githubusercontent.com/54288899/213748753-b4e61697-2d89-4ec0-a9b6-da43b78413a2.png)


om alles in dit repository te snappen moet je minimaal 1x naar de video's kijken
Alle scripts zijn in deze repository te vinden pas het script aan naar het ip plan en je zit gebakken.
bij de switcht script moet je de hostname telkens veranderen naar de juiste naam van de switch.
VOOR SWITCH 3 APARTE SCRIPT GEBRUIKEN!!!
bij de isp moet je port 100fx toevoegen en bij de DNS server 1FFE poort veranderen.

vergeet niet bij de isp de poorten naar een glasvezelport te veranderen en bij de DNS server


Alle laptops moeten wpc300n kaart hebben om te connecten met wifi (pc moet uit dan kaart erin vergeet hem dan nie weer aan te zetten!)
daarna navigeer je naar deskop en klik je op pc wireless om verbinden met het wifi netwerk te maken die jij bij de accespoints heb gezet/gecreeerd 


check op alle routers en de server naar de interface/settings dat de ip's toegevoegd zijn en dat portstatus op on staat.
ga elke apparaat langs printers hebben een static ip volg het ip plan. routers controleren.
Default Gateaway eindigt altijd met een .1 dns server ip is de .14 in het afbeelding.

volgorde van de scripts maakt in principe niet uit maar voor de zekerheid!
 
1. MLS
2. Switch
3. p_edge
4. ISP

Op het eind op elke modem Ip route 0.0.0.0 0.0.0.0 en eind hop ip om de connecties tussen de routers in te stellen         .
Ip route 0.0.0.0 0.0.0.0 Lo1 (alleen bij isp)




https://discord.gg/mxppaCMDkX <<<<<<<<<<<<<<<<<<<<<<<<<<<<<

discord link ^^^^^^^

----------------------------------------------------------------------------------------------------------------------------
![image](https://user-images.githubusercontent.com/54288899/229609205-403aee5f-a641-4be0-84fe-969653df383b.png)


B1K2W2 ( Packet Tracer examen samenvatting)
Video 1
Als eerste download je Visio om een tekening te maken. Als je dat hebt gedaan dan klik je in Visio op “Nieuwe tekening maken”. Dan kun je hier jouw eigen netwerktekening bouwen. Als je allemaal apparaten wilt toevoegen, dan druk je op “Meer Shapes”. Daarna klik je op Stencil Openen en zoek je het bestand 3015. Nu kun je de elementen toevoegen zoals Routers en andere hardware.
Daarna klik je bij ontwerpen op Formaat, die zet je op A4. Daarna naast Formaat klik je op Afdruk-afstand en kies je voor liggend.
Bij invoegen kun je apparaten met elkaar verbinden door Verbindingslijnen te kiezen en als je tekst wilt invoegen dan klik je op bijschrift.



----------------------------------------------------------------------------------------------------------------------------



Video 2
ADMIN-PC
In deze opdracht ga je een IP Tabel moeten invullen en dat kun je zo doen.
Het lokaal netwerk is Admin-PC totaan de Edge ( dus alles wat er tussen zit maakt ook deel uit van het lokale netwerk)
Nu gaan we bij admin-pc de command ipconfig uitvoeren voor de gateway. De gateway heb je nodig om de ssh command te gebruiken. En SSH is een beveiligde manier om met remote access jouw router en switch in te gaan.
De command die je moet typen om in de router of switch te komen >
Ssh –l (gebruikersnaam) (ip gateway)
Ssh –l admin01 192.168.1.1 (om in de edge te komen, hij is aangegeven dat je daarin moest)
Daarna gebruik je de commands show ip interface brief om alle IP-adressen te zien, die vul je dan in de tabel.
Daarna show run om de maskers te zien. Dus van S0/0/0 moet je die invullen en dat is 255.255.255.252
Om te zien welke interfaces met Edge verbonden zijn, gebruik je de command
Show lldp neighbours
Als lldp niet aan staat, dan doe je:
config t
Lldp run 

Daarna kijk je naar de Port ID, Device ID en Local interface
Port ID = Gig 0/1
Device ID = S1
Local interface = Gig 0/0
Daarna vul je in bij de kolom van Local Interface en Connected Neighbours alleen Gig0/1 | S1 in.






Hierna ga je naar de volgende om te kijken wat de ip routes zijn.
Show ip route connected
Hiermee zie je welke interface welke network heeft, en dat is dan bijvoorbeeld 209.165.200.4/30
Het subnet 255.255.255.252 heeft alleen 2 ip-adressen, dus 209.165.200.5 en 209.165.200.6 ( de opdracht geeft aan dat je 209.165.200.10 moet gebruiken)
209.165.200.7 is de broadcast. 
Je pingt de twee netwerken om te kijken of je response krijgt.
Daarna gebruik je de onderstaand command om in RBO-Edge te komen. ( als je inlogt dan pas zie je RBO-Edge)
RBO_Edge
ssh –l RBOadmin 209.165.200.10 

Daarna gebruik je de command show ip interface brief (afgekort: sh ip int brief) om te zien waarmee de RBO-Edge verbonden is, in dit geval is dat met G0/1 en G/0.
Show run om de subnet maskers te zien
Show lldp neighbours om te zien waar ze verbonden mee zijn. 
En in dit geval zie je dan dat RBO-Firewall verbonden is met RBO-Edge.
“als een ip adres wordt gebruikt dan is het vaak een ander ip-adres""
RBO-Firewall is de neighbour van RBO-Edge

Je gebruikt de command 
Show ip route connected en dan is het netwerk 192.168.3.248, die heeft alleen maar 2 ip's door het subnet masker 255.255.255.192, dus je hebt deze twee ip-adressen: 192.168.3.250 en 192.168.3.251
Daarna gebruik je de command 











RBO-Firewall
Ssh –l RBOadmin 192.168.3.250 om in RBO-Firewall te komen
Als je sh ip int brief gebruikt dan kent hij een interface Gi0/0 en Gi0/0 bij de RBO-Firewall
Daarna gebruik je show run om alle maskers te zien
En daarna show lldp neighbours om te kijken met wie hij verbonden is. 
Vul dit allemaal in het tabel!
Als een je een ip adress ziet dan is dat het netwerk en dan als het een subnet van 255.255.255.252 heeft / 30 dan weet je dat hij 2 ip adressen gebruikt. (na 2 tellen verder dus niet 1 en 2 maar bij 3 en 4 als je 1.1.1.1 als netwerk hebt dan ping je 1.1.1.3 en 1.1.1.4 bij dat subnet)
Bij RBO-Firewall is gig0/1 het ip-adress 192.168.4.254, daar is het ip-adres van de gateway 192.168.4.255.
Als je de gateway pingt , 192.168.4.255 dan krijg je ip-adressen:
192.168.4.131, 192.168.4.132 , 192.168.4.13
Daarna als je dit ip adres hebt gebruik je deze command


SW-RB01
Ssh –l RBOadmin 192.168.4.131
Daarna gebruik je de command:
Sh ip interface brief om te zien welke interfaces hij kent
Daarna gebruik je
Sh lldp neighbours om te kijken met wie hij verbonden is
Bij het vakje local interface and connected neighbour vul je de Device ID en local interface in bij de command show lldp neighbours
Daarna gebruik je show run om de masks te zien:










SW-RB02
Ssh –l RBOAdmin 192.168.4.132
Sw-rb02
Interface brief
Vlan 1 192.168.4.132
Sh lldp neighbours
SW-RB03
Sw-rbo 3
Ssh –l RBOadmin 192.168.4.133
Sh lldp nei
Sh ip int brief
Nu is de ip tabel af


-------------------------------------------------------------------------------------------------------------------

Video 3
Hoe maak je een tekening in Visio? Tip: zet de schermen naast elkaar, de gegevens van de tabel. 
Je neemt een PC, aantal switches, router, ( als het te groot is moet je die kleiner maken)
Invoegen > verbindingslijn ( om lijnen te trekken)
Invoegen > bijschrift ( om de apparatuur een naam te geven)
