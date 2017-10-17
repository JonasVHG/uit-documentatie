---
---
# Locatie

Het is verplicht aan te geven waar het event doorgaat. Dit is de locatie van het evenement. 
Elke locatie heeft een naam en adres:

~~~xml
<location>
  <address>
    <physical>
        <city>Heist-op-den-Berg</city>
        <country>BE</country>
        <zipcode>2220</zipcode>
    </physical>
  </address>
  <label>CC Zwaneberg</label>
</location>
~~~

Om de uniciteit van de locaties te kunnen garanderen, heeft elke locatie een uniek locatie-ID binnen UiTdatabank. 
Dit ID zorgt er bovendien voor dat de locatie aanklikbaar is op UiTinVlaanderen en de andere kanalen van UiT.

Bij het importeren van evenementen is het daarom aangeraden het ID van een reeds bestaande locatie mee te sturen als attribuut in de node van de locatienaam, zoals in onderstaand voorbeeld:

~~~xml
<location>
<label cdbid="55CA2F39-A8CE-F67A-24C2FF99F9AFB1F6">CC Zwaneberg</label>
</location>
~~~
 
De correcte locatie-id’s kunnen opgevraagd worden via [helpdesk@publiq.be](mailto:helpdesk@publiq.be).
