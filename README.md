# Wikipedia TFIDF Analyzer
[![Go Report Card](https://goreportcard.com/badge/github.com/negapedia/wikitfidf)](https://goreportcard.com/report/github.com/negapedia/wikitfidf)
[![GoDoc](https://godoc.org/github.com/negapedia/wikitfidf?status.svg)](https://godoc.org/github.com/negapedia/wikitfidf)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=negapedia_wikiconflict&metric=bugs)](https://sonarcloud.io/dashboard?id=negapedia_wikiconflict)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=negapedia_wikiconflict&metric=coverage)](https://sonarcloud.io/dashboard?id=negapedia_wikiconflict)
[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=negapedia_wikiconflict&metric=ncloc)](https://sonarcloud.io/dashboard?id=negapedia_wikiconflict)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=negapedia_wikiconflict&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=negapedia_wikiconflict)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=negapedia_wikiconflict&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=negapedia_wikiconflict)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=negapedia_wikiconflict&metric=security_rating)](https://sonarcloud.io/dashboard?id=negapedia_wikiconflict)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=negapedia_wikiconflict&metric=vulnerabilities)](https://sonarcloud.io/dashboard?id=negapedia_wikiconflict)
[![Build Status](https://travis-ci.org/negapedia/wikitfidf.svg?branch=develop)](https://travis-ci.org/negapedia/wikitfidf)<br>
Negapedia TFIDF Analyzer analyze Wikipedia's dumps and makes statistical analysis on reverts text.<br>
The data produced in output can be used to clarify the theme of the contrast inside a Wikipedia page.<br>

#### Handled languages
`english`, `arabic`, `danish`, `dutch`, `finnish`, `french`, 
`german`, `greek`, `hungarian`, `indonesian`, `italian`, 
`kazakh`, `nepali`, `portuguese`, `romanian`, 
`russian`, `spanish`, `swedish`, `turkish`, `armenian`, 
`azerbaijani`, `basque`, `bengali`, `bulgarian`, `catalan`, 
`chinese`, `croatian`, `czech`, `galician`, `hebrew`, `hindi`, 
`irish`, `japanese`, `korean`, `latvian`, `lithuanian`, 
`marathi`, `persian`, `polish`, `slovak`, `thai`, `ukrainian`, 
`urdu`, `simple-english`
<br>
This kind of data come from [Negapedia/nltk](https://github.com/negapedia/nltk)

##### Badwords handled languages
`english`, `arabic`, `danish`, `dutch`, `finnish`, `french`, 
`german`, `hungarian`, `italian`, `portuguese`, 
`spanish`, `swedish`, `chinese`, `czech`, `hindi`, `japanese`, 
`korean`, `persian`, `polish`, `thai`, `simple-english`
<br>
This kind of data come from [Negapedia/badwords](https://github.com/negapedia/badwords)

#### Outuput files
- `GlobalPagesTFIDF.json`: contains for every page the list of words associated with their absolute frequency and tf-idf value;
- `GlobalPagesTFIDF_topNwords.json`: as `GlobalPagesTFIDF.json`, but are reported only the most important N words (in term of tf-idf value);
- `GlobalWords.json`: contains all the analyzed wiki's words associated with their absolute frequency;
- `GlobalTopic.json`: contains all the words in every topic (using [Negapedia](http://en.negapedia.org) topics);
- `BadWordsReport.json`: contains for every page which has them, a list of badwords associated with their absolute frequency.

#### Minimum and Recommended Requirements
The minimum requirements which are needed for executing the project in reasonable times are:
- At least 4 cores-8 threads CPU;
- At least 16GB of RAM (required);
- At least 300GB of disk space.

However the recommended requirements are:
- 32GB of RAM or more (highly recommended).

## Usage
#### Building docker image
``docker build -t <image_name> .``<br>
from the root of repository directory.

#### Running docker image
``docker run -d -v <path_on_fs_where_to_save_results>:<container_results_path> <image_name>``<br>
example:<br>
``docker run -d -v /path/2/out/dir:/data my_image ``<br>

#### Executions flags
- `-lang`: wiki language;
- `-d`: container result dir;
- `-s`: revert starting date to consider;
- `-e`: revert ending date to consider;
- `-specialList`: special page list to consider;
- `-rev`: number of revert to consider;
- `-topPages`: number of top words per page to consider;
- `-topWords`: number of top words of global words to consider;
- `-topTopic`: number of top words per topic to consider;
- `-delete`: if true, after compressing results directory will be deleted (default: true);
- `-test`: if true, logs are shown and is processed a single dump.

<br>example:<br>
``docker run -v /path/2/out/dir:/data wikitfidf dothething -lang it``

#### Installation
Go packages can be installed by:<br>
``go get github.com/negapedia/wikitfidf``
<br> and docker image can be downloaded by:<br>
``docker pull negapedia/wikitfidf``
