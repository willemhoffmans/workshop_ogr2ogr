# OGR2OGR in PostGIS

Mocht je oefeningen in deze workshop liever in een PostGIS omgeving toepassen in plaats van een Geopackage? Dat kan uiteraard!

Vervang in de te bouwen commandoregels dan (voorbeeld):

`-f "GPKG" "D:\data\test\resultaten.gpkg"`

in het volgende:

`-f "PostgreSQL" PG:"dbname='databasenaam' user='gebruiker' host='host' password=mypassword port=5432"`

Het laatste hangt af van hoe PostgreSQL geconfigureerd is. Als je bijvoorbeeld in een lokale database werkt met dezelfde gebruikersnaam als waarmee je op je laptop bent ingelogd, dan hoef je bij `PG:` alleen de databasenaam op te geven. 

Uiteraard is het wel belangrijk dat je de benodigde rechten op de database hebt. 

Als je in je database meerdere schema's hebt, zul je ook de schemanaam in je resultaten op moeten geven bij gebruik van het `-nln` argument.
