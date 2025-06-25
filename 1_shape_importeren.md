# Deel 1: een shapefile importeren

In dit deel gaan we een shapefile in een geopackage importeren. Dit gaat, zoals we zullen zien, redelijk rechttoe rechtaan. Maar, misschien wel lastig als we het 2x proberen.

## De ogr2ogr syntax

Allereerst even de syntax van ogr2ogr erbij halen. Het commando is in de basis zo opgebouwd:

`ogr2ogr <output> <input> [<optie1> <optie2> .... ]`

Een paar dingen hierbij:

* <output> en <input> zijn verplicht, en ook in die volgorde
* Let hierbij op de extensies. Geef die altijd mee (dus .shp voor shapefiles, .gpkg voor geopackage, enz.)
* Alle andere opties mogen in willekeurige volgorde aan het commando worden toegevoegd. 

Voor een compleet overzicht van alle opties in ogr2ogr, zie [GDAL documentatie](https://gdal.org/en/stable/programs/ogr2ogr.html)
Al snel zullen we zien dat we een aantal van de extra opties goed kunnen gebruiken. 

Een optie die we meteen bij de eerste actie maar even introduceren is de `-f` optie. Hiermee bepalen we wat het uitvoerformaat moet zijn. Het is vrij gebruikelijk om deze optie vooraan in de commandoregel te zetten, in tegenstelling tot de (meeste) andere opties. Maar, zoals gezegd, hier ben je in principe vrij in. 

Als we een geopackage maken (of een dataset eraan toe willen voegen) is dit "GPKG". Als optie krijgen we dan dus `-f "GPKG"`. Dit gaan we dus nu toepassen.

## Een shapefile naar een geopackage converteren

We gaan een nieuwe geopackage maken, met daarin in eerste instantie één dataset. Bijvoorbeeld ...
Dowload ([hier](https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/e73b01f6-28c7-4bb7-a782-e877e8113e2c)een shapefile met provinciegrenzen. 
Vervolgens gebruiken we ogr2ogr om de dataset om te zetten in een nieuwe geopackage. Als we bovenstaande in acht nemen ziet het commando er ongeveer zo uit (uiteraard paden en bestandsnamen naar eigen smaak aanpassen):

`ogr2ogr -f "GPKG" "D:\data\test\provinciegrenzen.gpkg" "D:\data\invoer\GRS_1000_PROV_NL_V.shp"`

Als het goed is gaat de conversie redelijk snel. Laad zowel de originele shape als de nieuwe geopackage in QGIS en stel jezelf de volgende vragen:

* zijn alle objecten 1 op 1 goed in de geopackage terecht gekomen? 

, zie je verschillen. Hoeveel objecten zitten erin? 
Voer 't nog een keer uit, en bekijk het resultaat opnieuw. Is het resultaat overschreven? Er zijn opties -overwrite en -append. Blijkbaar is -overwrite de default.
Andere naam geven met -nln optie. Kan dat in dezelfde database? 
