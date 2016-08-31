# Earthquakes Demo

## Datasets

The earthquake datasets are gathered from the Northern California Earthquake Data Center through the [ANSS Composite Catalog Search](http://www.ncedc.org/anss/catalog-search.html).

**Acknowledgement**

"Waveform data, metadata, or data products for this study were accessed through the Northern California Earthquake Data Center (NCEDC), doi:10.7932/NCEDC."

### Earthquakes

Filename: earthquakes.txt  
Search parameters: `catalog=ANSS, start_time=1989/01/01,00:00:00, end_time=2016/08/31,05:02:49, minimum_magnitude=0, maximum_magnitude=10, event_type=E`  
Size: 2394928 lines (183051645 bytes)

### Blasts (Quarry or Nuclear)

Filename: blasts.txt  
Search parameters: `catalog=ANSS, start_time=1989/01/01,00:00:00, end_time=2016/08/31,05:03:01, minimum_magnitude=0, maximum_magnitude=10, event_type=B`  
Size:  17637 lines (1337354 bytes)

## Setting up

### Installing Logstash Environment Filter Plugin

The logstash configuration file requires `logstash-filter-environment` community-maintained plugin. You may install the plugin by running `bin/logstash-plugin install logstash-filter-environment` or modify the configuration file in order to associate the event types (earthquake or blast) to the `type` of the index.

### Ingesting Data

Extract the dataset archive with `tar zxf ncedc-earthquakes-dataset.tar.gz` from the terminal. Run the below commands to ingest the data sets to your Elasticsearch cluster. Please note, you may need to configure `ncedc-earthquakes-logstash.conf` file in case your are not running Elasticsearch node on your local host.

```
tail +1 earthquakes.txt| EVENT="earthquake" logstash/bin/logstash -f ncedc-earthquakes-logstash.conf
tail +1 blasts.txt| EVENT="blast" logstash/bin/logstash -f ncedc-earthquakes-logstash.conf
```

### Installing Timelion Plugin

The Kibana dashboard requires the `timelion` plugin. You may install the plugin by running `bin/kibana-plugin install timelion`

### Importing Kibana Visuals and Dashboards

1. Open Kibana and go to Settings > Indices. Type in `ncedc-earthquakes` as the index name and create the index pattern.
2. Go to Objects tab and click on Import, and select `ncedc-earthquakes-dashboard.json` by the file chooser.
3. Go to Dashboard and click on `Earthqueke` from the list of the dashboards.

