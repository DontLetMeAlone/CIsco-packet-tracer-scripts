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
