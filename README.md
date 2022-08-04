# Movies-ETL

## Project Outline
The analysis for this project consists of a background summary and coding notes.

### Background
As an introduction to ETL (a data Extract-Transform-Load process), a set of files
related to movie metadata and ratings information is read in (Extracted), cleaned
and otherwise prepared (Transformed) and merged (Loaded) into database (for this,
we continued with PostgreSQL) tables as well as read in Jupyter Notebook Pandas
DataFrames. The data -- sourced from Wikipedia, Kaggle, and MovieLens files before
being prepared -- is to be utilized in a "hackathon" analysis tournament organized
by *Britta* for *Amazing Prime.*

For the hackathon, the three files are to provide raw ratings as well as budget, box
office, release date, running time and what is found after a cleaning transformation
to be 27 additional columns of metadata for several thousand movie titles.

### ETL Process
The process is continuous improvement of three phases until an educated  judgment
call is made that the effort to retrieve more usable data formats will be more than
the quality of information that will be provided by the extra "cleaning." These three
phases are described in the module as:
- Inspect
- Plan
- Execute

The *inspection* phase involves looking over what data is available, so that an informed
*plan* can be formulated for carrying out (*executing*) the transformation of what can be
(usually?) a messy set of data potentially requiring a multitude of inspect-plan-execute
iterations before being fit for analysis purposes.

Note<sup>module 8.5.1</sup> that although "the most common (way) to create a data pipeline
(that) ETL isn't the only way." Also noted is "the **Extract, Load, and Transform (ELT)**
paradigm" whereby "data is stored as unstructured data in a data lake and transformed when
analyses are performed. This (method) requires very powerful analytical tools to perform
the transformation tasks quickly, where ETL frontloads the transformation to make analyses
easier to perform."

### Coding Notes

Britta and Amazing Prime, pleased with the dataset, would like to "keep it updated on a
daily basis (and thus) Britta (wants) to create an automated pipeline that takes in new
data, performs the appropriate transformations, and loads the data into existing tables."<sup>module 8 challenge</sup>

The challenge assignment thereby "consists of four technical analysis deliverables:"
- Deliverable 1. an ETL function--in the `ETL_function_test.ipynb` file--to read three data files
- Deliverable 2. Extract(ion) and Transform(ation)--in the `ETL_clean_wiki_movies.ipynb` file--of
the Wikipedia data file from Deliverable 1.
- Deliverable 3. Extract(ion) and Transform(ation)--in the `ETL_clean_kaggle_data.ipynb` file--of
the Kaggle metadata and MovieLens rating data files from Deliverable 1.
- Deliverable 4. Create--in the `ETL_create_database.ipynb` file--the Movie Database

Two images below depicting the number of records in the PostgreSQL tables for the `movies` and `ratings` tables:
<img src="/Resources/movies_query.png" width="40%">
<img src="/Resources/ratings_query.png" width="55%">

Notes:
>> - Two files for the Wikipedia data are included in the Resources folder; they are copies but each with a different type of hyphenation in the name.
>> - When cleaning the data, be aware of the different types of hyphenation that may be utilized in data so that regex (regular expressions) text
matching strings will appropriately filter/select data.
>> - The inspection step to become familiar with what data is available may involve visualization in scatter plots.
>> - The execute step of creating the PostgreSQL `ratings` table required that the (Pandas) dataframe `to_sql()` method have
 the `if_exists` option set to 'append' rather than 'replace' as otherwise the reading of the number of rows was being truncated.
-TA J Caro assisted discovery of / recovery from this issue.
>> - Creation of the `ratings` PostgreSQL table--as the table was over 26 million records--required breaking into a `chunksize`
of 1000000.
>> - The .gitignore file (python version) for this repository was not initially created but added later.
>> - Adding files from local repository branch by navigating to the location in "File Explorer" then right-clicking to specify "GitBash here"
-learned of this method assisted by TA J Caro
