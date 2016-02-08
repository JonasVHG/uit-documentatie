---
---

# Gefacetteerde classificatie

Een gefacetteerde classificatie is een classificatie waarbij informatie in categorieën wordt onderverdeeld die verschillende facetten of attributen van de informatie weergeven. In tegenstelling tot een hiërarchische classificatie die informatie in één vaste categorie onderbrengt.

Een gefacetteerde of faceted search op een bepaald facet brengt de zoekresultaten onder in verschillende facetten, toont voor ieder facet het aantal en laat toe om de zoekresultaten te filteren op een bepaald facet. Een gefacetteerde search kan m.a.w. gebruikt worden om de zoekresultaten op een overzichtelijke manier weer te geven.

Opmerking: verschillende facetten kunnen met elkaar overlappen, dus een document kan zich in meer dan één facet bevinden. Bijvoorbeeld een document bevindt zich in het facet “today” en in het facet “thisweekend”.

Wanneer een facetField meegegeven wordt aan de search query, dan wordt in de ouput teruggegeven:

* Een opsomming van de mogelijke waardes van het facet met voor iedere waarde het aantal documenten.
* Het totaal aantal documenten.
* De zoekresultaten.

**Voorbeeld**

Zoek volgens facet “stad”

```
{server}/searchv2/search?q=Speelgoed&rows=10&facetField=city
```

In UiTdatabank zijn er drie speciale facetten: datetype, category en categorie dimensie.

## Facet “datetype”

Datetype is een apart te gebruiken zoekveld en een geldig facetField. Het facet type “datetype” bevat volgende facetten: today, tomorrow, thisweekend, nextweekend, next7days, next14days, next30days, next3months, next6months, next12months, permanent.

```
{server}/searchv2/search?q=Speelgoed&rows=10&facetField=datetype
```


## Facet “category”

Category is geen zoekveld, maar wel een geldig facetField. Ieder document behoort tot één of meerdere categorieën. Een categorie behoort tot een domein.

```
{server}/searchv2/search/?q=*:*&rows=2&facetField=category
```

Een specifieke toevoeging voor de UiTdatabank maakt het mogelijk om alle documenten te vinden waaraan een categorie is toegekend EN de documenten waaraan een onderliggende categorie is toegekend.

D.m.v. de velden category_id en category_name kan gezocht worden op de categorie. Voor elk document worden ook de category_id en category_name van de parent categorieen geïndexeerd. Zodoende zal “Bezoek de Bibliotheektoren van Leuven” ook gevonden worden als gezocht wordt op categorie “Bezoeken”.


Deze query geeft geen resultaten:

```
{server}/searchv2/search?q=exact_category_name:Doen
```

Deze query toont wel alle events die in een subcategorie van “Doen” zitten terug (workshops, quizzen, …):

```
{server}/searchv2/search?q=category_name:Doen
```

Een overzicht van alle categorieën en een uitleg over hoe de UiTdatabank categorisatieservice te consulteren vind je hier http://tools.uitdatabank.be/docs/uitdatabank-categorisatie-service.

## Facet “categorie dimensie”

Op basis van de verschillende eigenschappen van een document, kunnen we verschillende dimensies van categorisatie onderscheiden. Voorbeeld: voor wat een event betreft, kunnen we stellen dat elk event, onder meer, een bepaald type heeft (tentoonstelling, festival, beurs, etc.) en een bepaalde doelgroep (gezinnen, kinderen tussen 12 en 14 jaar, etc.).

Aan elke dimensie (bv. “type”) wordt vervolgens een geheel van categorieën of een categorisatiekorf (bv. “tentoonstelling”, “festival”, etc.) verbonden. De categorieën hebben uitsluitend betrekking op één specifieke dimensie.

Het is nu mogelijk om te zoeken/filteren/facetteren op categorie dimensies. Elke dimensie kan als volgt aangesproken worden: category_{dimensie}name of category{dimensie}_id.

Het overzicht van alle dimensies is hier te vinden: http://taxonomy.uitdatabank.be/api/domain/.

Voorbeeld alle events in Gent thematisch gefacetteerd

```
{server}/searchv2/search?q=*.*&rows=0&group=event&facetField=category_theme_name&fq=city:Gent
```
