Google Sheet version available [here](https://docs.google.com/spreadsheets/d/1pG6s1GSp5EsioxBNKygunq6cCuEfsRMBglveLMXDo-c/edit#gid=1937130730).

# Steps taken in creating the variables

The Broader Impact Statement data was collected from the papers listed in NeurIPS 2020 proceedings [website](https://proceedings.neurips.cc/). 1899 paper PDFs were downloaded in November 2021. One paper was later taken down from the website and has therefore been removed from the dataset, which now includes 1898 papers. The PDFs were then converted to XML using the PDFX academic [web tool](http://pdfx.cs.man.ac.uk/). The conversion resulted in 1891 xmls, 1890 discounting the paper that was later removed. Eight of the 1899 original PDFs were image-based PDFs and had to be hand coded.

The 1890 xml files were parsed using the “scrapping.py” code on [this github repository](https://github.com/paulsedille/NeurIPS-Broader-Impact-Statements) which constructs a database with the following variables: title, paper identifier, paper link, impact statement, impact title, word count, sentence count, citation count, has positive, has negative, has opt out, has NA and has impact statement.

Unfortunately, the PDF to XML conversion process is prone to coding errors that make the resulting xml files impossible to reliably parse for every paper’s impact statement and related variables. In order to minimise errors, the code was altered multiple times to attempt to accurately scrape as many impact statements as possible (accounting for as many of the ways in which impact statements are coded in the xml files as possible, or for the fact some of them were spread across more than one page, included images and/or tables, etc.). Each new iteration of the code was compared with the original one so as to identify and correct any remaining errors. This process was repeated until the new code outputs did not help locate any new errors in the main database. 

Paper subject data was pulled in from a dataset provided by NeurIPS linking paper titles to their primary and secondary subject areas and “clustering preference.” Authors and affiliations were extracted from [this dataset](https://github.com/nd7141/icml2020/blob/master/neurips_2020_accepted.txt) containing paper titles, authors, and affiliations and matched to papers based first on title, then on authors. Due to title discrepancies, some papers had to be manually matched. Authors for which no affiliation was listed were manually looked up. Affiliation type utilized [this dataset](https://docs.google.com/spreadsheets/d/1CT3hCvbKxyJeS1FdrZtlK5MTuvWsfXR_/edit#gid=255761468). Not all affiliations were present; anything containing “University” was automatically categorized as “Academic.” Approximately 600 other affiliations present in the papers were not listed in the dataset; these were manually categorized. Country-level affiliation location used [this dataset](https://github.com/nd7141/icml2020/blob/master/university2.csv). Again, not every affiliation was included, so manual lookups filled in the gaps. For affiliations with multinational corporations for which no narrower location was given (e.g. Google), the location of their headquarters was used. 


## paper title (separate scrape)
Paper title scraped from the NeurIPS 2020 proceedings website [main page](https://proceedings.neurips.cc/paper/2020).

## paper authors (separate scrape)
Paper title scraped from the NeurIPS 2020 proceedings website [main page](https://proceedings.neurips.cc/paper/2020).

## title
Paper title scraped from the PDF papers after XML conversion.

## paper identifier
Paper identifier scraped from the PDF papers’ url on the NeurIPS 2020 proceedings website, based off of this repeated pattern in every paper’s URL: "[IDENTIFIER]-Paper.pdfx.xml"

## paper link
Paper URL scraped from the papers’ PDF page on the NeurIPS 2020 proceedings website.

## impact statement
Text of the paper’s broader impact statement scraped from the XML database using the code on [this github repository](https://github.com/paulsedille/NeurIPS-Broader-Impact-Statements).

## impact title
Title of the paper’s broader impact statement scraped from the XML database using the code on [this github repository](https://github.com/paulsedille/NeurIPS-Broader-Impact-Statements).

## word count
The word count of the text of the broader impact statement.

## sentence count
The sentence count of the text of the broader impact statement, obtained using the [NLTK package](https://www.nltk.org/) and corrected for miscounts (“e.g. ” and “i.e. ”) using [this code](https://github.com/paulsedille/NeurIPS-Broader-Impact-Statements/academic-pdf-scrap/tree/sentences/functions).

## opt out
Whether or not the broader impact statement was considered to be an “opt out” (authors do not believe their work has any foreseeable societal consequence and that a discussion of broader impacts is generally not applicable) according to a human reviewer. As much as possible, consistent principles were used. In particular, many authors note their work is “theoretical” or “foundational” but this alone was not enough for the statement to be counted as an opt out. In addition, many authors only consider the benefits of their work on the scientific/research community (usually only the AI/ML community) without considering impacts beyond this, but this was not counted as an opt out unless authors explicitly noted their work did not have broader social or ethical impacts.
Not all statements were reviewed. Reviewed statements include the 300 shortest statements (by word count) as well as statements that included specific text strings often associated with opt outs, e.g. “this work does not present any foreseeable societal consequence." or simply “foreseeable,” “not applicable,” etc.

## ambiguous opt out
Whether or not the broader impact statement was considered to be an “ambiguous opt out” according to a human reviewer. This variable should be considered along with the “opt out” variable. This variable was necessary as many broader impact statements (especially shorter ones) often opt out while simultaneously making comments on the paper’s broader impact, or make ambiguous distinctions between present and future impacts, direct and indirect impacts, immediate and downstream impacts, etc., discussing one but opting out of discussing the other. 

## manually corrected
Whether or not the text of the broader impact statement or other variables were manually corrected by a human modifying the data set.

## human review
Whether or not the text of the broader impact statement or other variables were manually reviewed by a human and confirmed correct, regardless of whether or not a correction was made.

## Image based PDF
Eight of the 1899 originally downloaded PDFs were image-based and could not be converted to XMLs. They therefore had to be hand coded. Those papers are coded as TRUE for this variable, all others are coded as FALSE.

## paper title (subjects)
Variable provided by NeurIPS team.

## primary subject area
Variable provided by NeurIPS team.

## secondary subject areas
Variable provided by NeurIPS team.

## clustering subject preference
Variable provided by NeurIPS team.

## authors
Extracted from [this dataset](https://github.com/nd7141/icml2020/blob/master/neurips_2020_accepted.txt).

## affiliations
Extracted from [this dataset](https://github.com/nd7141/icml2020/blob/master/neurips_2020_accepted.txt).

## academic
Whether at least one affiliation is an academic institution. Created by matching affiliations in [this dataset](https://docs.google.com/spreadsheets/d/1CT3hCvbKxyJeS1FdrZtlK5MTuvWsfXR_/edit#gid=255761468), with heavy cleaning and additions. 

## industry
Whether at least one affiliation is an industry institution. Created by matching affiliations in [this dataset](https://docs.google.com/spreadsheets/d/1CT3hCvbKxyJeS1FdrZtlK5MTuvWsfXR_/edit#gid=255761468), with heavy cleaning and additions. 

## mixed
Whether a paper has both academic and industry affiliations. Created by matching affiliations in [this dataset](https://docs.google.com/spreadsheets/d/1CT3hCvbKxyJeS1FdrZtlK5MTuvWsfXR_/edit#gid=255761468), with heavy cleaning and additions. 

## country
The country or countries in which a paper’s affiliations are based. Created by matching affiliations in [this dataset](https://github.com/nd7141/icml2020/blob/master/university2.csv), with heavy cleaning and additions. 



# Synonym lists

Negative and positive word lists were established using [Wordnet](https://wordnet.princeton.edu/)'s synset (semantic) relations. An initial list of ~20 words was selected by the authors for both positive and negative keywords, including words like “positive” and “benefit” used by the NeurIPS organisers in presenting requirements for Broader Impact Statements. The list was then expanded by following the semantic relations of the initial words in Wordnet. Related words produced in this way were then selected for their relevance to our work’s topic and aim. The search stopped when the authors felt new words being found were too far from the original (semantic) intent of the list. Where relevant, derived forms of relevant words were also included, e.g. Benefit, Benefits, Benefited, Beneficial, etc. Finally, the authors also reviewed the top 500 most frequent words, extracted from our Broader Impact Statement dataset, for positive and negative words not already noted, and these were included in our final word lists. (Popular technical ML/AI words that in some contexts may have a positive or negative connotation like “optimise” or “robust" were not included.)



## Note on geographic variables
Turkey was classified under “Asia” for continent and Russia was classified under "Europe."
