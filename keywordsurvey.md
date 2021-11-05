---
title: Keyword Survey
layout: template
filename: keywordsurvey
--- 
# Methods for Collecting and Processing Keywords

## Analysis of the Paper Search Results from Institute of Electrical and Electronics Engineers (IEEE) and The Optical Society (OSA) 

In order to find the trends in research related to phase change material (PCM), a keyword search for the academic peer-reviewed papers is conducted. As an initial step, the paper search services of Institute of Electrical and Electronics Engineers (IEEE) and The Optical Society (OSA) are selected to collect papers related to PCM. 

One notable search feature of the IEEE and OSA paper search services is that the citation information includes the keywords selected by the authors. For example, suppose paper A has been retrieved by searching with the search word “phase change material”. The citation data bundled with the paper search result contain author-selected keywords such as germanium compounds, thermal conductivity, random-access storage, and so on.

The idea of estimating research trends is that these keywords are closely related to the search word “phase change material.” If the keywords are repeatedly seen in other searched papers as well, it can be regarded that those keywords are more popular among researchers and there might be a strong research trend represented by the keywords.

Selection of IEEE and OSA paper archives was determined in terms of the application area. While IEEE papers focus more on electronics-related research issues, OSA focuses on optics. Thus, the keyword searches with “phase change material” for both paper archives are expected to provide PCM research trends in (i) electronics in general and in (ii) optics.

Table 1 shows the top 30 keywords appeared in the search result (with “phase change material”) sorted by the appearing frequency. In order to put a bound in the research trend period, the search is filtered from the year 2004 to 2019. “Phase change material” is provided as the search word. [IEEE search services](https://ieeexplore.ieee.org/search/advanced) generated a total of 5891 results and [OSA](https://www.osapublishing.org/search.cfm) generated 974 papers, as of December 8, 2019. Since manually retrieving all the search results from the web pages takes excessive time and effort, the first 1000 search results from IEEE and 500 searches from OSA results are selected to further analyze the keywords listed in the papers.

The keyword information can be extracted from the citation data (RIS format in particular) provided by the search services and a simple Python script was written to extract the keywords. Once the keywords are retrieved, its frequencies are counted and sorted in a descending order. From Table 1, it can be seen that the keywords chosen by the authors show different trends depending on the search results being from IEEE or OSA archive.

| **Keyword (IEEE)**                 | **Count** |
| ---------------------------------- | --------- |
| Phase  change materials            | 795       |
| phase  change materials            | 755       |
| phase  change memories             | 461       |
| Phase  change memory               | 331       |
| Resistance                         | 202       |
| germanium  compounds               | 193       |
| phase  change material             | 191       |
| Crystallization                    | 179       |
| PCM                                | 161       |
| phase  change memory               | 140       |
| thermal  conductivity              | 130       |
| thermal  energy storage            | 130       |
| antimony  compounds                | 127       |
| Heating                            | 124       |
| Nonvolatile  memory                | 120       |
| Temperature  measurement           | 112       |
| Temperature                        | 111       |
| Thermal  conductivity              | 108       |
| random-access  storage             | 104       |
| Amorphous  materials               | 100       |
| Conductivity                       | 98        |
| Programming                        | 93        |
| Ge2Sb2Te5                          | 90        |
| latent  heat                       | 87        |
| Switches                           | 84        |
| Phase  change random access memory | 79        |
| Electrodes                         | 79        |
| chalcogenide  glasses              | 75        |
| crystallisation                    | 69        |

| **Keyword  (OSA)**            | **Count** |
| ----------------------------- | ---------- |
| Refractive  index             | 159        |
| Phase  shift                  | 108        |
| Laser  beams                  | 72         |
| Thin  films                   | 67         |
| Phase  measurement            | 63         |
| Phase  modulation             | 53         |
| Scanning  electron microscopy | 47         |
| Metamaterials                 | 43         |
| Electric  fields              | 42         |
| Optical  properties           | 37         |
| Laser  materials processing   | 35         |
| X ray  diffraction            | 35         |
| Effective  refractive index   | 33         |
| Optical  materials            | 32         |
| Laser  materials              | 30         |
| Material  properties          | 29         |
| Surface  plasmons             | 29         |
| Laser  irradiation            | 27         |
| Absorption  coefficient       | 26         |
| Optical  components           | 26         |
| Spatial  light modulators     | 24         |
| Raman  spectroscopy           | 24         |
| Photonic  crystals            | 23         |
| Electron  beam lithography    | 23         |
| Optical  constants            | 22         |
| Optical  data storage         | 21         |
| Interferometry                | 19         |
| Fused silica                  | 19         |
| Optical  devices              | 19         |

Table 1. Top frequency keywords appeared in IEEE and OSA paper search results (with the search word of “phase change material”)

## Analysis of _Nature_ and _Science Magazine_ Paper Archives

The same keyword search and frequency-listing method above can be repeated for [_Nature_](https://www.nature.com/srep/) and [_Science Magazine_ paper search services](https://advances.sciencemag.org/). The idea of choosing _Nature_ and  _Science Magazine_ is that papers accepted by those organizations are more broadly and generally positioned than by IEEE or OSA. Thus, checking the keywords in _Nature_ or  _Science Magazine_ might produce trend estimations beyond the bounds of electronics or optics applications that were checked in the previous section. 

One unfortunate problem with the _Nature_ and  _Science Magazine_ paper search services is that the search results do not provide the keyword information selected by the authors. As a second-best measure, the paper titles are separated into words instead and their word frequencies are counted to check the trend. For example, a paper with the title “A map for phase-change materials” generates a word list of “A, map, for, phase-change, materials”. Insignificant words such as a, the, for, and so on are taken out later manually. The same title-breaking step is repeated for other searched paper titles and the frequencies of each word are counted.

For _Nature_ paper archive, a total of 370 results are generated with the search word “phase change material.” The publication time period is bounded from 2004 to 2019. Table 2 shows the first 30 words with the frequency counts sorted in a descending order. While the word listing on the left are not specific as was in Table 1 where the author-selected keywords are counted, it still shows frequently used words from the paper titles.

In contrast with _Nature_ paper archive search, search for  _Science Magazine_ paper archives generated only 33 results. Since this number of articles can be placed in the manual analysis, the word counting of the paper titles are omitted for the  _Science Magazine_ articles.

| **Word (_Nature_)** | **Count** |
| ------------------ | ---------- |
| map                | 121        |
| phase-change       | 77         |
| materials          | 70         |
| projected          | 70         |
| memory             | 69         |
| devices            | 63         |
| designing          | 53         |
| crystallization    | 48         |
| universal          | 42         |
| neuro-inspired     | 31         |
| computing          | 26         |
| rewriteable        | 25         |
| data               | 23         |
| storage            | 23         |
| resonant           | 22         |
| bonding            | 22         |
| crystalline        | 22         |
| comparison         | 21         |
| study              | 20         |
| mesoporous         | 15         |
| silica             | 15         |
| nanoscale          | 14         |
| microsphere        | 13         |
| active             | 12         |
| carbon             | 12         |
| used               | 12         |
| matrix             | 11         |
| shape-stabilized   | 10         |
| phase              | 10         |

Table 2. Top frequency words from the paper titles that appear in _Nature_ paper search results (with the search word of “phase change material”)

## Analysis of American Institute of Aeronautics and Astronautics (AIAA) Paper Archive

Finally, the word counting of the paper titles is repeated for American Institute of Aeronautics and Astronautics (AIAA) paper archive search results. Since AIAA paper search service does not provide the keywords information selected by the authors either, the paper titles are broken down into words and counted individually. 

The purpose of analyzing AIAA paper archive is to find the trends of PCM uses or applications in aerospace or aeronautical fields. Since aerospace engineering requires the state-of-the-art applications of materials used in aircrafts or spacecrafts, estimation of the newest trend in PCM use can be an important information that can help direct (or allocate) future research resources optimally. 

Table 3 shows the first 30 words with the frequency counts sorted in a descending order from the AIAA paper search results (with the search word of “phase change material”). As was in the previous cases, the paper publication dates are bounded into from 2004 to 2019. The total of 370 search results are obtained.

| **Word  (AIAA)** | **Count** |
| ---------------- | ---------- |
| laminated        | 130        |
| composite        | 80         |
| high             | 78         |
| conductivity     | 74         |
| phase            | 60         |
| change           | 51         |
| material         | 50         |
| (pcm)            | 47         |
| drywall          | 44         |
| system           | 39         |
| experimental     | 38         |
| investigation    | 33         |
| ice              | 28         |
| heat             | 25         |
| exchangers       | 18         |
| encapsulated     | 18         |
| slurry           | 17         |
| flow             | 17         |
| manifold         | 17         |
| microchannels    | 16         |
| graphitized      | 15         |
| carbon           | 15         |
| foam             | 15         |
| with             | 15         |
| thermal          | 13         |
| energy           | 13         |
| storage          | 12         |
| testing          | 12         |
| failure          | 12         |

Table 3. Top frequency words from the paper titles that appear in AIAA paper search results (with the search word of “phase change material”)