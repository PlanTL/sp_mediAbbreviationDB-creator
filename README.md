# AbreMES-X: Extractor de Abreviaturas Médicas en Español (Spanish Medical Abbreviation extractor)

## Introduction

This is the software used to generate the Spanish Medical Abbreviation DataBase (https://github.com/PlanTL/AbreMES-DB). 
The database is generated by detecting abbreviations and their potential definitions explicitly mentioned in the same sentence,  extracted from the metadata of different biomedical publications written in Spanish that contain the titles and abstracts. 
The sources of these publications are SciELO[1], IBECS[2] and Pubmed[3] and the chosen schema is Dublin Core. We use the official ones from SciELO and customized adaptations of the XML files to Dublin Core from IBECS and Pubmed metadata. 

We use a modified version of the algorithm developed by Schwartz & Hearst[4], adapted to the Spanish language and applying specific filters to improve the results. Users are permitted to change the code and adapt it to their needs without any restrictions, like adapting the abbreviation-definition extractor into other languages, domains, or other document types to analyze.


## Prerequisites

This software has been compiled with Java SE 1.8 and it should work with recent versions. You can download Java from the following website: https://www.java.com/en/download

Stanford CoreNLP is needed as well. We used version 3.9.0 for this work, and latest versions should work as well. Stanford CoreNLP is licensed under the GNU General Public License (v3 or later). You can download it from the following website: https://stanfordnlp.github.io/CoreNLP/

GeoNames is a geographical database which covers over eleven million placements. GeoNames is distributed under Creative Commons BY-4.0 license. It is available for download free or charge: http://www.geonames.org


## Directory structure

<pre>
exec/
The executable to generate the database.

exec/AbreMES_X_lib/
Stanford CoreNLP module, necessary to get the abbreviations.

src/
Source code used to generate de database.

src/resources/
Files needed to execute the database generator:

  - corpora_list.txt: includes the folders where your corpus metadata are stored. The file needs 
  to have one corpus per line with the following format: "corpus_name {TAB} corpus_folder". 
  Included corpus metadata must follow the Dublin Core format.
  
  - geonames.zip: includes all the world location names extracted from GeoNames.
  
  - JST_spa.txt contains all Journal Subject Terms extracted from the Spanish edition of MeSH 
  (Medical Subject Headings). 
</pre>


## Usage

The executable file "AbreMES_X.jar" is the program you need to generate your abbreviation-definition database. The executable needs one single parameter: the folder where the database will be stored. Before executing, you need to follow these two steps:

1. Create the output folder manually.
2. Store inside that folder the files found in the folder src/resources.

Remember that your corpora must be in Dublin Core format only. Learn more about Dublin Core in the following website: http://dublincore.org/

One your output directory is ready, just type the following command in your terminal:

<pre>
$ java -jar AbreMES_X.jar RESOURCES_DIRECTORY OUTPUT_DIRECTORY
</pre>


## Examples
<pre>
$ java -jar AbreMES_X.jar ~/AbreMES_X/resources ~/AbreMES_X/DB
</pre>


## Contact

PlanTL.Sanidad@bsc.es

## License

(This is so-called MIT/X License)

Copyright (c) 2017-2018 Secretaría de Estado para el Avance Digital (SEAD)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## References

[1] Scientific Electronic Library Online (SciELO Spain) is an electronic virtual library covering a collection of Spanish health scientific journals selected following preestablished quality criteria. Developed and maintained by the Spanish National Library of Health Sciences.  http://scielo.isciii.es

[2] Bibliographical database for health articles, contains abstracts and references of different articles written in Spanish. Developed and maintained by the Carlos III Health Institute in Madrid, Spain. http://ibecs.isciii.es

[3] PubMed is a free search engine accessing primarily the MEDLINE database of references and abstracts on life sciences and biomedical topics. The United States National Library of Medicine (NLM) at the National Institutes of Health maintains the database as part of the Entrez system of information retrieval. https://www.ncbi.nlm.nih.gov/pubmed/

[4] A.S. Schwartz, M.A. Hearst, "A Simple Algorithm for Identifying Abbreviation Definitions in Biomedical Text"
