# 04 Onderzoeken

## Voorbereiding

Ga verder met het bestand dat je in de vorige module hebt gemaakt.

## Opdracht

Binnen de **Politie** is je leidinggevende bijzonder te spreken over de geografische mogelijkheden van Power BI. Het is echter niet heel handig om alle geografische achtergrondinformatie over een regio in elk rapport te herhalen. Het liefst zou ze bij bijvoorbeeld een uitschieter in registraties in een bepaalde veiligheidsregio willen kunnen "doorklikken" naar alle informatie van die veiligheidsregio. Bijvoorbeeld de trend in misdaden de afgelopen jaren, de verdeling naar type misdaad in de gemeenten, etc..

Dit "doorklikken" wordt in Power BI **Onderzoeken** genoemd. In [module 3](../03-visuals-and-interaction/03-visuals-and-interaction.md) hebben we al gekeken naar de *drilldown*. *Onderzoeken* houdt in de basis in dat je een getal onder de loep neemt op een andere pagina of in een ander rapport. Op deze manier kun je eenvoudig de context bekijken - bijvoorbeeld van de misdaden binnen een bepaalde veiligheidsregio.

## Onderzoeken binnen een rapport

Wanneer je *onderzoeken* binnen een rapport mogelijk wilt maken, moet je de volgende zaken regelen:

*. Er moet een pagina zijn wat het *doel* van je onderzoek is.
   * In het voorbeeld hierboven: de pagina "Veiligheidsregio details"
*. Op deze *doel*pagina moet je een "analyseveld" instellen. In het voorbeeld hierboven is dit de naam van de veiligheidsregio: wanneer je die ergens in het rapport tegenkomt, kun je in twee klikken naar de detail-pagina navigeren, wat dan automatisch gefilterd is op de betreffende categorie.
   * In het voorbeeld hierboven is het *analyseveld* `Veiligheidsregio naam`.

### Drillthrough instellen in je rapport

1. Voeg een pagina toe met de naam "Veiligheidsregio details"
1. Voeg hierop een *Kaart visual* toe (![Icon of map visual](img/02-kaart-visual.png)). Configureer deze als volgt:
  * **Locatie**: **Gemeente naam met land** (tabel *Geografie*)
  * **Belgrootte**: **Aantal geregistreerde misdaden** (tabel *Registraties (gemeente)*)
1. Voeg nu ook een zgn. "Treemap" visual toe voor *Aantal geregistreerde misdaden per Misdaad omschrijving*:
1. Klik ergens op het canvas zodat er geen *visual* meer geselecteerd is.
1. In het **Visualisaties** paneel onder het kopje **Onderzoeken** vind je nu een vakje "Analysevelden hier toevoegen". Sleep hier het veld **Veiligheidsregio naam** heen (tabel *Geografie*)
1. Ga terug naar de pagina *Geregistreerde misdaden*, en rechtsklik op één van de veiligheidsregio's in de grafiek. Als het goed is heb je nu een submenu *Onderzoeken* naar de *Veiligheidsregio details*-pagina

    Om het af te maken, kun je nu de **Veiligheidsregio details** pagina verbergen (rechtsklik op de tab, kies **Verbergen**). Publiceer het rapport naar een workspace en bekijk het resultaat.

    Probeer nu zelf een tweede onderzoeks-pagina "Misdaad details" aan te maken waarbij je alle gegevens over een misdaadtype op een rij zet. Filter op basis van het veld **Misdaad code** (tabel *Registraties (Gemeente)*). Geef de volgende zaken weer:

*Bij elk punt staat wat extra uitdaging - deze hoef je niet uit te voeren. Mocht alles je echter gemakkelijk afgaan en je wilt wat meer de grenzen van Power BI opzoeken, dan kun je je hier even in vastbijten*

1. Verkopen per man / vrouw / getrouwd / ongetrouwd
   * Extra uitdaging: voeg bijbehorende titels toe binnen de visual ("Married men", "Single men", etc.)
2. Verkopen per productkleur
   * Eerste extra uitdaging: geef alleen de 5 bestverkopende kleuren weer
   * Tweede extra uitdaging: laat de kleur bepaald worden door de productkleur
3. Internet Total Sales per jaar
4. Internet Total Units per jaar

![Voorbeeld resultaat opdracht](img/05-drillthrough-within-report-final.png)

Wanneer je drillthrough pagina correct werkt, zou je vanaf pagina "Product Sales" nu een drillthrough moeten kunnen maken naar "Product Category Details"

## Drillthrough tussen meerdere rapporten

*Drillthrough* is ook mogelijk tussen meerdere rapporten: je kunt dan de data vanuit een andere invalshoek meer verdieping geven in een ander rapport.

Om Drillthrough tussen meerdere rapporten werkend te krijgen hebben we (minstens) twee rapporten nodig:

* Het *bron-rapport*. Dit is het rapport waar je vandaan komt (hier "doe" je een drillthrough)
* Het *doel-rapport*. Dit is het rapport waar je terecht komt na een drillthrough.

Maak nu eerst via *File*, *New* een nieuw rapport dat verbinding maakt met de dataset AdventureWorks in je eigen workspace en sla dit op onder de naam *module-4-drillthrough-report*.

Maak in dit nieuwe rapport een drillthrough filter per **Year** (tabel *Date*, in de hierarchy *Calendar*). Let erop dat je hier instelt dat je **Year** gebruiken moet als *categorie*:

![Use calendar year as drillthrough per category](img/04-calendar-year-drillthrough-as-category.png)

Je kunt vervolgens in het lijstje onder deze instelling een jaar kiezen dat je *nu* wilt weergeven (feitelijk filter je de data op "alleen de data van jaar X"). Zodra je via een *drillthrough* op dit rapport belandt, wordt dit filter vervangen door het jaartal waarmee je de drillthrough uitvoert. Het toevoegen van dit filter geeft je echter een beter gevoel over hoe de cijfers eruit zou zien bij een drillthrough van (bijvoorbeeld) 2012.

Vul vervolgens het rapport met inzichten over een jaar:

1. Het verloop van verkopen door het jaar heen (let op dat deze correct gesorteerd is)
2. De verhouding tussen de verkopen t.o.v. een kwartaal geleden

Stel vervolgens de drillthrough reporting in:

* In het **bron-rapport** (waar de drillthrough vandaan komt)
  * **File** -> **Options and settings** -> **Options**
  * Onder **Current file**, open **Report settings**
  * Zet het vinkje bij **Allow visuals in this report to use drillthrough targets from other reports**  
![Enable cross report drillthrough in source report](img/06-enable-cross-report-drillthrough-source.png)
* In het **doel-rapport** (waar de drillthrough naartoe gaat):
  * Zet het vinkje **Cross-report** bij je **Drillthrough filter**  
![Enable cross report drillthrough in target report](img/07-enable-cross-report-drillthrough-target.png)

Publiceer het rapport, en test of de drillthrough over rapporten heen werkt in de Power BI Portal.

## Bonus-opgaven

### Aanpassen drillthrough-naam

Standaard heeft de drillthrough de naam `Page1 [naam-van-oorspong-rapport]`. Zorg ervoor dat hier een zinnige naam komt te staan, die de lading dekt.

![Deze beschrijving kan beter...](img/09-onzinnige-naam.png)

## Oplossing

Hier vind je de eindpunten van deze opdracht: [04-01-Solution.pbit](04-01-Solution.pbit) en [04-02-Solution.pbit](04-02-Solution.pbit)

## Video

Hier vind je de [Walkthrough video](https://vimeo.com/584747083/d8e167c13e)


## Volgende modules

De volgende module is Module 5: Self-service reporting. We beginnen hier met [CSV-bestanden inladen](../05-self-service-reporting/05-csv-inladen.md).

Hieronder vind je een overzicht van alle modules:

1. [Introductie Power BI Desktop](../01-introduction/01-introduction-powerbi-desktop.md)
2. [Rapporteren op Power BI Datasets en eerste visualisatie](../02-reporting-on-dataset/02-reporting-on-dataset.md)
3. [Visuals en interactie](../03-visuals-and-interaction/03-visuals-and-interaction.md)
4. [Drillthrough](../04-drillthrough/04-drillthrough.md) (huidige module)
5. Self-service reporting
   * [CSV-bestanden inladen](../05-self-service-reporting/05-csv-inladen.md)
   * [SQL data inladen](../05-self-service-reporting/06-sql-inladen.md)
6. Data Modeling 101
   * [Relaties](../06-data-modeling-101/07-relaties.md)
   * [Opschonen van je datamodel](../06-data-modeling-101/08-opschonen.md)
7. [Introductie Power Query (GUI)](../07-power-query-gui/09-power-query.md)
8. [Publiceren en samenwerken in workspaces](../08-publishing-and-collaboration-in-workspaces/10-publishing-and-collaboration-in-workspaces.md)
9. [Calculated Columns met DAX](../09-dax/11-calc-columns.md)
