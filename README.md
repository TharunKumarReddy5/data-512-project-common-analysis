<https://github.com/tterb/atomic-design-ui/blob/master/LICENSEs>

![contributors](https://img.shields.io/github/contributors/TharunKumarReddy5/data-512-homework_2.svg)

![codesize](https://img.shields.io/github/languages/code-size/TharunKumarReddy5/data-512-homework_2.svg)

![pullrequests](https://img.shields.io/github/issues-pr/TharunKumarReddy5/data-512-homework_2.svg)

![closedpullrequests](https://img.shields.io/github/issues-pr-closed-raw/TharunKumarReddy5/data-512-homework_2.svg)

data-512-project-common-analysis
================================

This repository contains the Common analysis for DATA 512 Human Centered Data
Science course project component at the University of Washington - Masters in
Data Science program

Date of Code Run: 2022-11-3

Goal: Considering Bias in Data
==============================

data-512-homework_2 project is an analysis exercise with primary goal to
understand the general biases in the models that originate from the bias in the
input data used for training the model. This short analysis on the quality of
wikipedia articles of politicians based on regions gives a good clarityon how
the coverage and quality of data varies among countries. It helps us understand
the causes and consequences of biased data in large, complex data science
projects.

Datasource Information
----------------------

The input data for this project is extracted from the below wikipedia
(politicians wikipedia pages) and prb (population) web pages. Additionally, two
more endpoints are used for page information and ORES scores. The datasource
endpoints are licensed under the [CC-BY-SA
3.0](CC-BY-SA%203.0%20and%20GFDL%20licenses) and [GFDL
licenses](CC-BY-SA%203.0%20and%20GFDL%20licenses). ORES is a machine learning
tool that can provide estimates of Wikipedia article quality. The ORES API
endpoint provides the article quality estimates from best to worst:

FA - Featured article

GA - Good article

B - B-class article

C - C-class article

Start - Start-class article

Stub - Stub-class article

-   [Politicians by
    Nationality](https://en.wikipedia.org/wiki/Category:Politicians_by_nationality)

-   [World
    Population](https://www.prb.org/international/indicator/population/table/)

-   [ORES REST API](https://www.mediawiki.org/wiki/ORES)

-   [Wikimedia Foundation REST API terms of
    use](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)

Issues and Special Considerations
---------------------------------

1.  There are few duplicates in the politicians input data file. All the
    absolute duplicates are filtered from the data but the duplicates at article
    name level are taken into account for per-capita calculations.

2.  There are few countries where the population is 0. This can be because the
    value is in millions and is rounded to the nearest decimal. These countries
    are filtered at Step 4 where the article-per-capita is calculated as they
    give infinity values because of 0 in the denominator

3.  Regions with cumulative population values are eliminated and the countries
    are mapped to the regions that are closest/lowest in the hierarchy of
    regions

Research Implications
---------------------

The key takeaway from this assignment is to understand the biases in the source
data to identify any model biases and avoid any misinterpretation of findings.
The bulk of online information contains some bias by nature. The biases may be
caused by a variety of factors, such as demographic, gender, cultural
prejudices, literacy rates etc. During the post-hoc analysis, several questions
came up regarding the articles per capita, including whether it was a reliable
indicator of coverage and if it was correlated with ORES ratings. Few biases in
the data are evident during post-hoc investigation. There are biases found in
Eastern Europe and Western Asia, having higher ranks for high quality articles
as compared to total articles. The articles per capita values appear to be
greatly reliant on the population of the country/region. For example, the
majority of the highest coverage countries/regions also have the lowest
population, and vice versa. In terms of article quality, non-native English
speakers had less high-quality articles than native speakers, indicating a
cultural-linguistic bias. All these inherent biases and few additional data
inconsistencies made me question the reliability of the per capita calculation
performed during the final steps of the exercise.

### What biases did you expect to find in the data (before you started working with it), and why?

Before the exercise, I expected high bias of high quality articles towards
developed countries, but the Wikipedia data is not present. There is a selection
bias involved in this exercise as there is missing data for many countries,
including major countries like US, Canada, Australia, etc. I expected less
article per capita value for South and East Asia due to high population. I also
expected high bias in because of high articles per capita for smaller countries
as their articles count is lesser than other countries. The ratings of
politicians from these countries would have been lesser since many politicians
wouldn't be famous. Also, the Asian and African countries' articles would have
less number of articles per capita attributing to literacy rates or the
cultural-linguistic bias in general there, which means articles in their native
languages would be better.

### What might your results suggest about (English) Wikipedia as a data source?

Data is dynamically changing on multiple runs hence could lead to inconsistency
in analysis. The ORES scores might not be trustworthy as they come from an AI
model that could be a victim of ideological, racial, gender, or cultural bias.
From the ORES Wiki, I came to know that the way the ORES model evaluates the
quality of the article itself appears to be biased toward the article's
structure rather than the content.

### Can you think of a realistic data science research situation where using these data (to train a model, perform hypothesis-driven research, or make business decisions) might create biased or misleading results, due to the inherent gaps and limitations of the data?

Biases may be present in many disciplines and models including content
moderation or NLP-based technologies that collect data from the internet. For
instance, we observed in the readings how gender, demographic, and cultural
biases might result in the models making predictions that may not be accurate.
Another illustration is the Islamophobia article, which shows how GPT-3 is
opposed to the specific religion. These restrictions are brought about by the
data that is given into these AI systems, which operate on the "Garbage In,
Garbage Out" tenet.

### How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?

For the regions and countries, there are missing Wikipedia articles information
in the dataset. Few countries have population values as 0. Because of the above
two reasons, the articles-per-capita might not represent the true values. Hence,
the researcher should extract the politicians Wikipedia articles from those of
the missing countries. Along with that, the ORES scores of articles for these
countries should also be obtained to get a true picture of the
high-quality-article-per-capita.

Dependencies
------------

Install the dependencies from the requirements.txt file using

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
python -m pip install -r requirements.txt
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Repository Structure
--------------------

Here are the main folders in our github data-512-homework_2 repository:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.
├── DATA 512 Homework 2 Tharun.ipynb
├── README.md
├── LICENSE
├── input
│   ├── politicians_by_country_SEPT.2022.csv
│   └── population_by_country_2022.csv
├── logs
│   ├── page_info_error_log.txt
│   └── scores_error_log.txt
├── output
│   ├── wp_countries-no_match.txt
│   └── wp_politicians_by_country.csv
├── plots
│   ├── bottom10_countries_by_coverage.png
│   ├── bottom10_countries_by_quality.png
│   ├── regions_high_quality_coverage.png
│   ├── regions_total_coverage.png
│   ├── top10_countries_by_coverage.png
│   └── top10_countries_by_quality.png
├── requirements.txt
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Input Data Files
----------------

-   population data (population_by_country_2022.csv) - Consists of countries,
    region and population for each country/region

-   Politicians data (politicians_by_country.SEPT.2022.csv) - Consists of
    crawled Wikipedia article pages about politicians fropm wide range of
    countries

Output Data Files
-----------------

### Countries with No Match

wp_countries-no_match.txt - All countries for which there are no matches i.e.,
either the population dataset does not have an entry for the equivalent
Wikipedia country, or vice-versa

### Consolidated Data

wp_politicians_by_country.csv - Consolidated the remaining data that contains
politicians data with population data into a single CSV file

### Screenshots

Examples of output plots generated by the functions

-   **Screenshot of plot 1:**  Top 10 Countries by Coverage

The first graph contains the bar plot indicating the top 10 countries by
coverage (total-article-per-capita)

[Image1](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/top10_countries_by_coverage.png)

![Alt text](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/top10_countries_by_coverage.png)

-   **Screenshot of plot 2:**  Bottom 10 Countries by Coverage

The second graph contains the bar plot indicating the bottom 10 countries by
coverage (total-article-per-capita)

[Image2](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/bottom10_countries_by_coverage.png)

![Alt text](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/bottom10_countries_by_coverage.png)

-   **Screenshot of plot 3:**  Top 10 Countries by High Quality Articles
    Coverage

The third graph contains the bar plot indicating the top 10 countries by high
quality coverage (high-quality-article-per-capita)

[Image3](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/top10_countries_by_quality.png)

![Alt text](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/top10_countries_by_quality.png)

-   **Screenshot of plot 4:**  Bottom 10 Countries by High Quality Articles
    Coverage

The fourth graph contains the bar plot indicating the bottom 10 countries by
high quality coverage (high-quality-article-per-capita)

[Image4](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/bottom10_countries_by_quality.png)

![Alt text](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/bottom10_countries_by_quality.png)

-   **Screenshot of plot 5:**  Geographic Regions by Total Coverage

The fifth graph contains the bar plot indicating the regions by coverage
(article-per-capita)

[Image5](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/regions_total_coverage.png)

![Alt text](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/regions_total_coverage.png)

-   **Screenshot of plot 6:**  Geographic Regions by High Quality Articles
    Coverage

The sixth graph contains the bar plot indicating the regions by high quality
coverage (high-quality-article-per-capita)

[Image6](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/regions_high_quality_coverage.png)

![Alt text](https://github.com/TharunKumarReddy5/data-512-homework_2/blob/main/plots/regions_high_quality_coverage.png)

Code Style
----------

Languages used: Python Coding Style: - PEP 8 - Docstrings

Following sofware design principles have been considered while packaging MLPA:

-   Modular design

    -   *'Somewhat General Purpose'* module

    -   Deep Modules

    -   Separation of Concerns

-   Reusability/Extensibility

-   Intuitable

-   Exception Handling

Authors
-------

-   [Tharun Kumar Reddy Karasani](https://github.com/TharunKumarReddy5)

![GitHub Contributors Image](https://contrib.rocks/image?repo=TharunKumarReddy5/data-512-homework_1)

Contribute
----------

This project is an open-source project- open to the Python user community for
contribution.
