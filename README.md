# NeurIPS-Broader-Impact-Statements
This is the repository for the "NeurIPS Broader Impact Statements" article, which investigates the benefits and challenges of the [NeurIPS 2020](https://proceedings.neurips.cc/paper/2020) conference requirement that all papers include a broader impact statement.
We have created a dataset containing the impact statements from all NeurIPS 2020 papers, along with additional information such as affiliation type, location and subject area, and a visualisation tool for exploration. 

## Functions Available
This repository contains:
* The [main dataset](https://github.com/paulsedille/NeurIPS-Broader-Impact-Statements/tree/main/main-dataset) of impact statements from all NeurIPS 2020 papers, along with additional information. (Google Sheet version available [here](https://docs.google.com/spreadsheets/d/1pG6s1GSp5EsioxBNKygunq6cCuEfsRMBglveLMXDo-c/edit?usp=sharing).)
* The [code](https://github.com/paulsedille/NeurIPS-Broader-Impact-Statements/tree/main/academic-pdf-scrape) used to download, convert and scrape all the PDFs submitted for NeurIPS 2020
* The [code](https://github.com/paulsedille/NeurIPS-Broader-Impact-Statements/blob/main/BIS_analysis_for_release.ipynb) used to collect all the additional information about the  impact statements such as affiliation type, location and subject area.

## Dataset limitations
This dataset has limitations that should be taken into consideration when using it. In particular, the method used to collect broader impact statements involved automated downloads, conversions and scraping and was not error-proof. Although care has been taken to identify and correct as many errors as possible, not all texts have been reviewed by a human. This means it is possible some of the broader impact statements contained in the dataset are truncated or otherwise incorrectly extracted from their original article. For more details, see our [notes-on-data.md](https://github.com/paulsedille/NeurIPS-Broader-Impact-Statements/blob/main/main-dataset/notes-on-data.md).

## Background
Ethics statements have been proposed as a mechanism to increase transparency and promote reflection of the societal impacts of published research. In 2020, the machine learning (ML) conference NeurIPS broke new ground by requiring that all papers include a broader impact statement.
These statements provide a unique opportunity to investigate the benefits and challenges of research governance mechanisms, as well as providing an insight into how ML researchers think about the societal impacts of their own work. 
We encourage other researchers to use our dataset to deepen our analysis, and more broadly, to further understand how researchers responded to this requirement, and to investigate the benefits and challenges of this and related mechanisms. 
