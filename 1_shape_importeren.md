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
