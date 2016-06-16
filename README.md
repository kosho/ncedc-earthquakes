# Earthquakes Demo

## Datasets

The earthquake datasets are gathered from the Northern California Earthquake Data Center through the [ANSS Composite Catalog Search](http://www.ncedc.org/anss/catalog-search.html).

**Acknowledgement**

"Waveform data, metadata, or data products for this study were accessed through the Northern California Earthquake Data Center (NCEDC), doi:10.7932/NCEDC."

### Earthquakes

Filename: earthquakes.txt
Search parameters: `catalog=ANSS, start_time=1898/01/01,00:00:00, end_time=2016/06/07,10:57:46, minimum_magnitude=0, maximum_magnitude=10, event_type=Ei`
Size: 3010078 lines (230265058 bytes)

### Blasts (Quarry or Nuclear)

Filename: blasts.txt
Search parameters: `catalog=ANSS, start_time=1898/01/01,00:00:00, end_time=2016/06/07,11:00:39, minimum_magnitude=0, maximum_magnitude=10, event_type=B`
Size:  29522 lines (2257360 bytes)

# Setting up

## Installing Logstash Environment Filter Plugin

The logstash configuration file requires `logstash-filter-environment` community-maintained plugin. You may install the plugin by running `bin/plugin install logstash-filter-environment` or modify the configuration file in order to associate the event types (earthquake or blast) to the `type` of the index.

## Ingesting Data

Extract the dataset archive with `tar 
Run the below commands to ingest the data sets to your Elasticsearch cluster. Please note, you may need to configure `ncedc-earthquakes-logstash.conf` file in case your are not running Elasticsearch node on your local host.

```
tail +1 earthquakes.txt| EVENT="blast" ../../logstash/bin/logstash -f ncedc-earthquakes-logstash.conf
tail +1 blasts.txt| EVENT="earthquake" ../../logstash/bin/logstash -f ncedc-earthquakes-logstash.conf
```

## Importing Kibana Visuals and Dashboards

1. Open Kibana and go to Settings > Indices. Type in `ncedc-earthquakes` as the index name and create the index pattern.
2. Go to Objects tab and click on Import, and select `ncedc-earthquakes-dashboard.json` by the file chooser.
3. Go to Dashboard and click on `Earthqueke` from the list of the dashboards.

# Earthquake Catalogues

## East Asia

### Tohoku Earthquake (March 11st, 2011)

The 2011 earthquake off the Pacific coast of Tōhoku (東北地方太平洋沖地震 Tōhoku-chihō Taiheiyō Oki Jishin?) was a magnitude 9.0 (Mw) undersea megathrust earthquake off the coast of Japan that occurred at 14:46 JST (05:46 UTC) on Friday 11 March 2011, with the epicentre approximately 70 kilometres (43 mi) east of the Oshika Peninsula of Tōhoku and the hypocenter at an underwater depth of approximately 30 km (19 mi). The earthquake is also often referred to in Japan as the Great East Japan earthquake (東日本大震災 Higashi nihon daishinsai) and also known as the 2011 Tohoku earthquake, and the 3.11 earthquake. It was the most powerful earthquake ever recorded to have hit Japan, and the fourth most powerful earthquake in the world since modern record-keeping began in 1900.

[Source](https://en.wikipedia.org/wiki/2011_Tōhoku_earthquake_and_tsunami)

## Americas

### Loma Prieta (October 17th, 1989)

The 1989 Loma Prieta earthquake occurred in Northern California on October 17 at 5:04 p.m. local time. The shock was centered in The Forest of Nisene Marks State Park approximately 10 mi (16 km) northeast of Santa Cruz on a section of the San Andreas Fault System and was named for the nearby Loma Prieta Peak in the Santa Cruz Mountains.

[Source](https://en.wikipedia.org/wiki/1989_Loma_Prieta_earthquake)

### Northridge (January 17th, 1994)

The 1994 Northridge earthquake occurred on Monday, January 17, at 4:30:55 a.m. PST and had its epicenter in Reseda, a neighborhood in the north-central San Fernando Valley region of Los Angeles, California.

[Source](https://en.wikipedia.org/wiki/1994_Northridge_earthquake)

### Haiti (January 12th, 2010)

The 2010 Haiti earthquake (French: Séisme de 2010 à Haïti; Haitian Creole: Tranblemanntè 12 janvye 2010 nan peyi Ayiti) was a catastrophic magnitude 7.0 Mw earthquake, with an epicenter near the town of Léogâne (Ouest), approximately 25 kilometres (16 mi) west of Port-au-Prince, Haiti's capital. 

[Source](https://en.wikipedia.org/wiki/2010_Haiti-earthquake)

### Baja California (April 4th, 2010)

The 2010 Baja California earthquake (also known as 2010 Easter earthquake, 2010 Sierra El Mayor earthquake, or 2010 El Mayor – Cucapah earthquake) occurred on April 4 (Easter Sunday) with a moment magnitude of 7.2 and a maximum Mercalli intensity of VII (Very strong). The shock originated at 15:40:41 local time south of Guadalupe Victoria, Baja California, Mexico.

[Source](https://en.wikipedia.org/wiki/2010_Baja_California_earthquake)


