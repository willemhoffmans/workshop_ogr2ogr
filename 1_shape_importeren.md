# Deel 1: een shapefile importeren

In dit deel gaan we een shapefile in een geopackage importeren. Dit gaat, zoals we zullen zien, redelijk rechttoe rechtaan. Maar, misschien wel lastig als we het 2x proberen.

## De ogr2ogr syntax

Allereerst even de syntax van ogr2ogr erbij halen. Het commando is in de basis zo opgebouwd:

`ogr2ogr <output> <input> [<argument1> <argumenten> .... ]`

Een paar dingen hierbij:

* <output> en <input> zijn verplicht, en ook in die volgorde
* Let hierbij op de extensies. Geef die altijd mee (dus .shp voor shapefiles, .gpkg voor geopackage, enz.)
* Alle andere argumenten mogen in willekeurige volgorde aan het commando worden toegevoegd. 

Voor een compleet overzicht van alle argumenten in ogr2ogr, zie [GDAL documentatie](https://gdal.org/en/stable/programs/ogr2ogr.html)
Al snel zullen we zien dat we een aantal van de extra argumenten goed kunnen gebruiken. 

Een argument dat we meteen bij de eerste actie maar even introduceren is `-f`. Hiermee bepalen we wat het uitvoerformaat moet zijn. Het is vrij gebruikelijk om dit argument vooraan in de commandoregel te zetten, in tegenstelling tot de (meeste) andere argumenten. Maar, zoals gezegd, hier ben je in principe vrij in. 

Als we een geopackage maken (of een dataset eraan toe willen voegen) is dit "GPKG". Als optie krijgen we dan dus `-f "GPKG"`. Dit gaan we dus nu toepassen.

## Een shapefile naar een geopackage converteren

We gaan een nieuwe geopackage maken, met daarin in eerste instantie één dataset. Bijvoorbeeld de provinciegrenzen van Nederland.
Dowload ([hier](https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/e73b01f6-28c7-4bb7-a782-e877e8113e2c) een shapefile met provinciegrenzen. 
Vervolgens gebruiken we ogr2ogr om de dataset om te zetten in een nieuwe geopackage. Als we bovenstaande in acht nemen ziet het commando er ongeveer zo uit (uiteraard paden en bestandsnamen naar eigen smaak aanpassen):

`ogr2ogr -f "GPKG" "D:\data\test\provinciegrenzen.gpkg" "D:\data\invoer\GRS_1000_PROV_NL_V.shp"`

Als het goed is gaat de conversie redelijk snel. Laad zowel de originele shape als de nieuwe geopackage in QGIS en stel jezelf de volgende vragen:

* zijn alle objecten 1 op 1 goed in de geopackage terecht gekomen?
* zijn er verschillen in de attribuuttabel?
* wat is eigenlijk de tabelnaam in de geopackage? Heet ie nu "provinciegrenzen" of is het nog steeds "GRS_1000_PROV_NL_V.shp"?

Om die laatste vraag goed te beantwoorden is het wel handig om in de Browser van QGIS een connectie te maken met de nieuwe database: rechts op Geopackage klikken en New Connection kiezen. Je kan dan vervolgens zien wat er in de geopackage zit. Dit komt ook verderop in de workshop wel van pas.

![QGIS Browser](/images/QGIS_browser.png)

## Een paar extra argumenten
Je ziet het: de tabel heeft nog steeds die cryptische naam. Dat moet natuurlijk anders. Gelukkig hebben we hiervoor een extra argument: `-nln`, ofwel: "new layer name". 
Laten we dus het commando uitbreiden en de uitvoerlaag een nieuwe naam geven, bijvoorbeeld 'provinciegrenzen'. Je krijgt dan:

`ogr2ogr -f "GPKG" "D:\data\test\provinciegrenzen.gpkg" "D:\data\invoer\GRS_1000_PROV_NL_V.shp" -nln provinciegrenzen`

Bekijk het resultaat in de Browser van QGIS, vergeet niet de _Refresh_ knop om de inhoud bij te werken. Wat zit er nu in de geopackage? Als het goed is alléén de laag met de nieuwe naam! Op zich is dat voor nu wel handig, zijn we die lelijke naam meteen kwijt. Maar het is wel tricky: blijkbaar overschrijft ogr2ogr zonder pardon de oude laag zonder dat verder te melden. Probeer maar eens zelf uit: voer het commando nóg een keer uit, maar noem het resultaat nu provinciegrenzen2: `-nln provinciegrenzen2`. 

Een fijne mogelijkheid bij een geopackage is dat je er meerdere kaartlagen (tabellen) in kwijt kan. Als we, even voor het voorbeeld van nu, een extra versie van de provnciegrenzen in de geopackage willen hebben, bijvoorbeeld om in te editen, dan hebben we nog een extra argument nodig: `- overwrite`. 
Breid het commando nog verder uit met dit argument, en zorg ervoor dat er nog een kopie van de provinciegrenzen tabel in de geopackage komt, uiteraard onder een andere naam. Bijvoorbeeld:

`ogr2ogr -f "GPKG" "D:\data\test\provinciegrenzen.gpkg" "D:\data\invoer\GRS_1000_PROV_NL_V.shp" -nln provinciegrenzen_edit -overwrite`

Als dit goed is gegaan, kijk nog eens in de QGIS Browser. Zie je nu 2 tabellen in de geopackage? 

![Browser 2 tabellen](/images/broser_2tabellen.png)
