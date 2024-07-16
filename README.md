# Basreh or Basra? Geoparsing Historical Locations in the Svoboda Diaries

## Overview

The Joseph Mathia Svoboda diaries capture over 40 years of trade on the Tigris, life, politics, and the landscape of Ottoman Iraq through the perspective of a British steamship purser with a rich family history and local connections. Of the 49 JMS diaries that we have in our collection, 3 have been published on the website, with more in progress. Unfortunately, not all of the Joseph’s diaries have survived, and some of those which have are in poor shape.

The data used in geoparsing is the data for diaries 47 and 48 released in the [ASIS&T 2023 Workshop "Exploring Collaborative Interpretive Practice"](https://github.com/svobodadiaries/collab-interpret).

Relevant links:
- [Svoboda Diaries Project website](https://svobodadiariesproject.org/)
- [Svoboda Diaries Project data downloads (published version of the three diaries, volumes 47-49)](https://www.svobodadiariesproject.org/svoboda-diaries-data/)


## Contents of this repository

### `gold/01_ner`: Gold NER annotations for Diary 47 / 48

- day: day in diary, number starting from 1
- start_span: index of first character in original span in the diary entry, 0-indexed
- end_span: index of last character in original span + 1 in the diary entry, 0-indexed
- original_entity: the span of text captured by `entry_contents[start_span : end_span]`
- resolved_entity: the span of text that the original span is resolved to, such that the same location referent has the same resolved span


### `gold/02_geo`: Gold geocoordinates for Diary 47 / 48

- day: day in diary, number starting from 1
- start_span: index of first character of first occurring original span in the diary entry, 0-indexed
- end_span: index of last character of first occurring original span + 1 in the diary entry, 0-indexed
- resolved_entity: the span of text that the original span is resolved to, such that the same location referent has the same resolved span
- lat: latitude in decimal degrees
- lng: longitude in decimal degrees


Each row has a unique resolved entity name, i.e., a unique location.

Missing data is empty for the latitude and longitude.


### `results/01_ner`: NER results for Diary 47 / 48

This folder contains the NER results with the resolution step as described in Section 3.2 Geotagging.

These NER files are also used as input into CLAVIN and Edinburgh, as explained in Section 3.4 Experimental Setup.


### `results/02_geo`: Geocoordinate results for Diary 47 / 48

This folder contains two subfolders:

1. `01_geocoding-only`: Contains the geocoding results of CLAVIN, Edinburgh, and Cluster+Rank as described in Section 3.4 Experimental Setup.

2. `appendix_end-to-end`: Contains the geoparsing results of CLAVIN and Edinburgh as end-to-end geoparsers.

Note that the results of Cluster+Rank were used in both of the comparisons in Table 4 and Table 8 (in the Appendix).


# Citation

Please cite the following paper:

# License

This work is distributed under an Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) license (https://creativecommons.org/licenses/by-nc/4.0/). Users are able to copy and redistribute the material in a non-commercial context, in any medium or form, and remix, transform, and build upon the material as long as they credit the investigator and indicate if changes were made.
