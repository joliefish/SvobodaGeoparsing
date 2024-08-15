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

# Contact

If there are any issues or if you need any clarification, please do not hesitate to contact us :)

Jolie Zhou joliez@uw.edu

Camille Cole clcole5@ilstu.edu

Annie T. Chen atchen@uw.edu

# Citation

Please cite the following paper:

```bibtex
@inproceedings{zhou-etal-2024-basreh,
    title = "Basreh or Basra? Geoparsing Historical Locations in the Svoboda Diaries",
    author = "Zhou, Jolie  and
      Cole, Camille  and
      Chen, Annie",
    editor = "Fu, Xiyan  and
      Fleisig, Eve",
    booktitle = "Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics (Volume 4: Student Research Workshop)",
    month = aug,
    year = "2024",
    address = "Bangkok, Thailand",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.acl-srw.33",
    pages = "377--390",
    abstract = "Geoparsing, the task of assigning coordinates to locations extracted from free text, is invaluable in enabling us to place locations in time and space. In the historical domain, many geoparsing corpora are from large news collections. We examine the Svoboda Diaries, a small historical corpus written primarily in English, with many location names in transliterated Arabic. We develop a pipeline employing named entity recognition for geotagging, and a map-based generate-and-rank approach incorporating candidate name augmentation and clustering of location context words for geocoding. Our system outperforms existing map-based geoparsers in terms of accuracy, lowest mean distance error, and number of locations correctly identified. As location names may vary from those in knowledge bases, we find that augmented candidate generation is instrumental in the system{'}s performance. Among our candidate generation methods, the generation of transliterated names contributed the most to increased location matches in the knowledge base. Our main contribution is proposing an integrated pipeline for geoparsing of historical corpora using augmented candidate location name generation and clustering methods {--} an approach that can be generalized to other texts with foreign or non-standard spellings.",
}
```

# License

This work is distributed under an Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) license (https://creativecommons.org/licenses/by-nc/4.0/). Users are able to copy and redistribute the material in a non-commercial context, in any medium or form, and remix, transform, and build upon the material as long as they credit the investigator and indicate if changes were made.
