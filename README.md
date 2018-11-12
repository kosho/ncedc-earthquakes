# Earthquakes Demo

## Datasets

The earthquake datasets are gathered from the Northern California Earthquake Data Center through the [ANSS Composite Catalog Search](http://www.ncedc.org/anss/catalog-search.html).

**Acknowledgement**

"Waveform data, metadata, or data products for this study were accessed through the Northern California Earthquake Data Center (NCEDC), doi:10.7932/NCEDC."

### Earthquakes

Filename: earthquakes-full.txt  
Search parameters: `catalog=ANSS, start_time=1989/01/01,00:00:00, end_time=2017/11/01,00:00:00, minimum_magnitude=0, maximum_magnitude=10, event_type=E`  
Size: 

### Blasts (Quarry or Nuclear)

Filename: blasts-full.txt  
Search parameters: `catalog=ANSS, start_time=1989/01/01,00:00:00, end_time=2017/11/01,00:00:00, minimum_magnitude=0, maximum_magnitude=10, event_type=B`  
Size: 17976 lines (1364546 bytes)

## Setting up

### Ingesting Data

Download and extract the dataset archive with `tar zxf ncedc-earthquakes-dataset.tar.gz` from the terminal. Run the below commands to ingest the data sets to your Elasticsearch cluster. Please note, you may need to configure `ncedc-earthquakes-logstash.conf` file in case your are not running Elasticsearch node on your local host.

```
tail -n +2 earthquakes.txt| EVENT="earthquake" logstash/bin/logstash -f ncedc-earthquakes-logstash.conf
tail -n +2 blasts.txt| EVENT="blast" logstash/bin/logstash -f ncedc-earthquakes-logstash.conf
```

### Importing Kibana Visuals and Dashboards

1. Open Kibana and go to Management > Index Patterns. Type in `ncedc-earthquakes` as the index name and create the index pattern.
2. Go to Saved Objects tab and click on Import, and select `ncedc-earthquakes-dashboard.json` by the file chooser.
3. Select `ncedc-earthquakes` as the new index pattern when the Index Pattern Conflicts dialog prompted.
3. Go to Dashboard and click on `Earthqueke` from the list of the dashboards.

