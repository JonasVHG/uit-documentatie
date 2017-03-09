---
---

# Mailing ophalen

{server}/mailing/v2/{ID} waarbij {ID} de ID is van de mailing

* Methode: GET
* Authenticatie: UserAccessToken van de gebruiker die admin permissie op de Service Consumer heeft

## Response

### Succes

HTTP 200 OK met een response body in XML formaat  

<table border="1" cellpadding="1" cellspacing="1"><tbody><tr><td> code</td> <td> Status code string</td> </tr><tr><td> mailing</td> <td> mailing entiteit</td></tr></tbody></table>

### Fout

HTTP status code, eventueel aangevuld met een XML body met extra informatie.

<table border="1" cellpadding="1" cellspacing="1"><tbody><tr><td> HTTP 403 Forbidden</td> <td> Er werd geen of geen geldig UserAccessToken meegestuurd.</td> </tr><tr><td> HTTP 401 Unauthorized</td> <td> De gebruiker heeft geen rechten om de huidige actie uit te voeren. (bv. is geen admin van de Service Consumer)</td></tr></tbody></table>

## Voorbeeld

Request

  POST {server}/mailing/template

Response

  <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
  <response xmlns:rdf="<http://www.w3.org/1999/02/22-rdf-syntax-ns"> xmlns:foaf="<http://xmlns.com/foaf/0.1/"> xmlns:cdb="<http://www.cultuurdatabank.com/XMLSchema/CdbXSD/3.1/FINAL"> xmlns:geo="[http://www.w3.org/2003/01/geo/wgs84\_pos#">](http://www.w3.org/2003/01/geo/wgs84_pos#">)  
  <code>MailingSuccess</code>

  <mailing>  
  <enabled>false</enabled>  
  <id>3</id>  
  <name>test2</name>  
  <serviceConsumerKey>68bd998e84216f530bb5b4f742ffab41</serviceConsumerKey>

  <template>

  <id>1</id>  
  <name>TestTemplate</name>  
  <template>template</template>  
  <subject>TestMailing</subject>  
  <frequency>DAILY</frequency>  
  <startDay>0</startDay>  
  <startHour>0</startHour>  
  <startMinute>0</startMinute>  
  <startDayOfWeek>0</startDayOfWeek>  
  <recommendationsResultEqualTreshold>100</recommendationsResultEqualTreshold>  
  <searchResultEqualTreshold>100</searchResultEqualTreshold>  
  <serviceConsumerKey>68bd998e84216f530bb5b4f742ffab41</serviceConsumerKey>  
  </template>  
  </mailing>

  </response>