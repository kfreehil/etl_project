For our project we were gathering data with the intent of analyzing the relationship between Corruption, GDP & Population size across various
countries around the globe.

* **E**xtract: original data sources and how the data was formatted (CSV, JSON, pgAdmin 4, etc).
    - We used 3 csv files sourced from the world bank, international monetary fund & dataworld.com respectively (links below)
        
        https://data.worldbank.org/indicator/sp.pop.totl
        https://www.imf.org/external/datamapper/NGDPD@WEO/OEMDC/ADVEC/WEOWORLD
        https://data.world/agriculture/worldwide-gov-indicators

* **T**ransform: what data cleaning or transformation was required.
    - We needed to find a common field across the 3 datas files to build our database around.  We had two options, 'country_name'
    and 'country_code.  We decided on 'country_name' mainly because 'country_code' was only readily available in two of the three source files where
    as 'country_name' was present in all 3. An extra bit of data cleansing would have been required had we gone the other route. With that decision 
    made we began cleaning the files.

    # The Cleaning #: 
    We had to identify inconsistencies in the 'country_name' field across all 3 files (Corruption, GDP & Population)
    The countries covered within each file weren't perfectly aligned, though there was a broad overlap amongst them making the project worthwhile.
    More importantly, however, we needed to manage different alias names used for various countries across the three sources - this was 
    probably our biggest challenge.  We used dictionaries to identify these discrepencies and then again later to map the 'alias' country names to a
    unified list of names we drew from one of the source files.  
    
    We also had to remove columns from our dataframes. The source files we used were a time-series, each broken down by year and (again) imperfectly 
    overlapping. At this stage Ed's version diverges slightly from mine.  He aimed to widdle the three files down to one table, which 
    naturally nudged him to focus on a single year of data that was shared across the 3 source files to make the data more managable.  I opted for 
    3 tables in the end, allowing future users more flexibility in what they can view while carrying the extra burden of having to implement there 
    own queries and filters when needed.

    From there it was just renaming some columns and uploading to our database. 

* **L**oad: the final database, tables/collections, and why this was chosen.
    - We chose postgres becuase we felt the data set had enough structure that it lent itself to some of the viewing 
        features an SQL database offers like Sql joins, views and tables.
    - We also recognized the data was small enough in size and scale to manage on our local computers making postgres
        an appropriate database to use.