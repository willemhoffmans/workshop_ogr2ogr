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



