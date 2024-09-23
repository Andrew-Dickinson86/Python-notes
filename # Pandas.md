## <center>Pandas</center>

### Useful Links

[Python Quick Reference](https://www.python.org/ftp/python/doc/1.1/quick-ref.1.1.html)

[Python3 cheat sheet](https://perso.limsi.fr/pointal/_media/python:cours:mementopython3-english.pdf)

[Python.org](https://www.python.org/)

[Python Standard Library](https://docs.python.org/3/library/index.html)

[Python Functions](https://docs.python.org/3/library/functions)

[Python Pandas](https://pandas.pydata.org/)

---

|<td colspan=3> <center><bold><h3>**Table of contents**<center>|||
|---|:---|:---:|
|**01.**|[**Pandas**](#Pandas)|import library,<br>create df from file / dictionary / columns,<br>saving df,<br>head / tail / take / info / describe / columns / index / shape / loc / iloc / unique methods,<br>selecting data,<br>rename / reorder columns, set index / index name<br>drop function<br>groupby( ) method|

* Pandas are a Python library for data analysis, mainly used for tabular data  
* Dataframe selections containing numerical values can be passed to statistical functions (e.g. **`dfVar['col_name_to_select].mean()`**)  

**import pandas**:  

**`import pandas as pd`**  

* Keyword **"import"** to import library  
* **"pandas"** is the library name  
* Keyword **"as"** is **optional** to change name referred to in script...in this case "pd"  
* Once the library has been imported, we have access to pre-built functions and classes  


```python
# importing "pandas" library and assigning it to name "pd"

import pandas as pd
```

**import specific package**  

**`from libraryName import packageName`**  
* Will import only the package named from the library named  
* Can change name package will be referred to in script by optionally including **as newReferringName** after imported package name  

**print all variables and function names of a module**:  

**`print(dir(moduleName))`**  
* This will print all the variables and function names from the module given  


```python
# example of printing all variables and function names of a module

dir(pd)
```




    ['BooleanDtype',
     'Categorical',
     'CategoricalDtype',
     'CategoricalIndex',
     'DataFrame',
     'DateOffset',
     'DatetimeIndex',
     'DatetimeTZDtype',
     'ExcelFile',
     'ExcelWriter',
     'Flags',
     'Float32Dtype',
     'Float64Dtype',
     'Float64Index',
     'Grouper',
     'HDFStore',
     'Index',
     'IndexSlice',
     'Int16Dtype',
     'Int32Dtype',
     'Int64Dtype',
     'Int64Index',
     'Int8Dtype',
     'Interval',
     'IntervalDtype',
     'IntervalIndex',
     'MultiIndex',
     'NA',
     'NaT',
     'NamedAgg',
     'Period',
     'PeriodDtype',
     'PeriodIndex',
     'RangeIndex',
     'Series',
     'SparseDtype',
     'StringDtype',
     'Timedelta',
     'TimedeltaIndex',
     'Timestamp',
     'UInt16Dtype',
     'UInt32Dtype',
     'UInt64Dtype',
     'UInt64Index',
     'UInt8Dtype',
     '__builtins__',
     '__cached__',
     '__doc__',
     '__docformat__',
     '__file__',
     '__getattr__',
     '__git_version__',
     '__loader__',
     '__name__',
     '__package__',
     '__path__',
     '__spec__',
     '__version__',
     '_config',
     '_hashtable',
     '_is_numpy_dev',
     '_lib',
     '_libs',
     '_np_version_under1p18',
     '_testing',
     '_tslib',
     '_typing',
     '_version',
     'api',
     'array',
     'arrays',
     'bdate_range',
     'compat',
     'concat',
     'core',
     'crosstab',
     'cut',
     'date_range',
     'describe_option',
     'errors',
     'eval',
     'factorize',
     'get_dummies',
     'get_option',
     'infer_freq',
     'interval_range',
     'io',
     'isna',
     'isnull',
     'json_normalize',
     'lreshape',
     'melt',
     'merge',
     'merge_asof',
     'merge_ordered',
     'notna',
     'notnull',
     'offsets',
     'option_context',
     'options',
     'pandas',
     'period_range',
     'pivot',
     'pivot_table',
     'plotting',
     'qcut',
     'read_clipboard',
     'read_csv',
     'read_excel',
     'read_feather',
     'read_fwf',
     'read_gbq',
     'read_hdf',
     'read_html',
     'read_json',
     'read_orc',
     'read_parquet',
     'read_pickle',
     'read_sas',
     'read_spss',
     'read_sql',
     'read_sql_query',
     'read_sql_table',
     'read_stata',
     'read_table',
     'read_xml',
     'reset_option',
     'set_eng_float_format',
     'set_option',
     'show_versions',
     'test',
     'testing',
     'timedelta_range',
     'to_datetime',
     'to_numeric',
     'to_pickle',
     'to_timedelta',
     'tseries',
     'unique',
     'util',
     'value_counts',
     'wide_to_long']



**Reading files to dataframes**:  

**`path_var = "file_path.ext"`**  
**`dataframe_varObj = pd.read_fileType(path_var)`**  
* The above assigns the **file path to a variable** then applies the **read function to assign the data** to a **dataframe object**  
* This then allows various methods to be applied to be able to work with the data in the dataframe  
* **Dataframes** are comprised of **rows and colums**  
* Ensure to **include extension** in file_path  


```python
# example reading data from a CSV file (typical file type used to store data)

csv_path = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloper\
SkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%204/data/TopSellingAlbums.csv'

df_csv = pd.read_csv(csv_path)
df_csv
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
      <th>Genre</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Released.1</th>
      <th>Soundtrack</th>
      <th>Rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Michael Jackson</td>
      <td>Thriller</td>
      <td>1982</td>
      <td>0:42:19</td>
      <td>pop, rock, R&amp;B</td>
      <td>46.0</td>
      <td>65</td>
      <td>30-Nov-82</td>
      <td>NaN</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AC/DC</td>
      <td>Back in Black</td>
      <td>1980</td>
      <td>0:42:11</td>
      <td>hard rock</td>
      <td>26.1</td>
      <td>50</td>
      <td>25-Jul-80</td>
      <td>NaN</td>
      <td>9.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pink Floyd</td>
      <td>The Dark Side of the Moon</td>
      <td>1973</td>
      <td>0:42:49</td>
      <td>progressive rock</td>
      <td>24.2</td>
      <td>45</td>
      <td>01-Mar-73</td>
      <td>NaN</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Whitney Houston</td>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>0:57:44</td>
      <td>R&amp;B, soul, pop</td>
      <td>27.4</td>
      <td>44</td>
      <td>17-Nov-92</td>
      <td>Y</td>
      <td>8.5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Meat Loaf</td>
      <td>Bat Out of Hell</td>
      <td>1977</td>
      <td>0:46:33</td>
      <td>hard rock, progressive rock</td>
      <td>20.6</td>
      <td>43</td>
      <td>21-Oct-77</td>
      <td>NaN</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Eagles</td>
      <td>Their Greatest Hits (1971-1975)</td>
      <td>1976</td>
      <td>0:43:08</td>
      <td>rock, soft rock, folk rock</td>
      <td>32.2</td>
      <td>42</td>
      <td>17-Feb-76</td>
      <td>NaN</td>
      <td>7.5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Bee Gees</td>
      <td>Saturday Night Fever</td>
      <td>1977</td>
      <td>1:15:54</td>
      <td>disco</td>
      <td>20.6</td>
      <td>40</td>
      <td>15-Nov-77</td>
      <td>Y</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Fleetwood Mac</td>
      <td>Rumours</td>
      <td>1977</td>
      <td>0:40:01</td>
      <td>soft rock</td>
      <td>27.9</td>
      <td>40</td>
      <td>04-Feb-77</td>
      <td>NaN</td>
      <td>6.5</td>
    </tr>
  </tbody>
</table>
</div>




```python
# example reading data from Excel file
# Note printing a dataframe object will cause a normal text output (When using jupyter notebooks, you won't see a difference otherwise)

xlsx_path = 'https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/Cognitive\
Class/PY0101EN/Chapter%204/Datasets/TopSellingAlbums.xlsx'

df_xlsx = pd.read_excel(xlsx_path)
print(df_xlsx)
```

                Artist                            Album  Released    Length  \
    0  Michael Jackson                         Thriller      1982  00:42:19   
    1            AC/DC                    Back in Black      1980  00:42:11   
    2       Pink Floyd        The Dark Side of the Moon      1973  00:42:49   
    3  Whitney Houston                    The Bodyguard      1992  00:57:44   
    4        Meat Loaf                  Bat Out of Hell      1977  00:46:33   
    5           Eagles  Their Greatest Hits (1971-1975)      1976  00:43:08   
    6         Bee Gees             Saturday Night Fever      1977  01:15:54   
    7    Fleetwood Mac                          Rumours      1977  00:40:01   
    
                             Genre  Music Recording Sales (millions)  \
    0               pop, rock, R&B                              46.0   
    1                    hard rock                              26.1   
    2             progressive rock                              24.2   
    3               R&B, soul, pop                              27.4   
    4  hard rock, progressive rock                              20.6   
    5   rock, soft rock, folk rock                              32.2   
    6                        disco                              20.6   
    7                    soft rock                              27.9   
    
       Claimed Sales (millions) Released.1 Soundtrack  Rating  
    0                        65 1982-11-30        NaN    10.0  
    1                        50 1980-07-25        NaN     9.5  
    2                        45 1973-03-01        NaN     9.0  
    3                        44 1992-11-17          Y     8.5  
    4                        43 1977-10-21        NaN     8.0  
    5                        42 1976-02-17        NaN     7.5  
    6                        40 1977-11-15          Y     7.0  
    7                        40 1977-02-04        NaN     6.5  
    

**create dataframes from a dictionary**:  

**`dic_var = {"key1":[listVal1, listVal2], "key2":[listVal1,listVal2]}  
dataframe_varObj = pd.DataFrame(dic_var, *index)`**  
* **Values must be in list format** to ensure order  
* Keyword **"DataFrame"** is **capitalized** as shown  
* **"index"** is **optional** and can be used to **define own indexing (row identifiers)** by assigning a list or tuple ect  


```python
# example creating a Dataframe from a Dictionary

songs = {"Album":["Thriller","Back in Black", "The Dark Side of the Moon", "The Bodyguard", "Bat Out of Hell"],
         "Released":[1982,1980, 1973, 1992, 1977], 
         "Length":["00:42:19", "00:42:11", "00:42:49", "00:57:44", "00:46:33"]}

songs_frame = pd.DataFrame(songs)
songs_frame
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Thriller</td>
      <td>1982</td>
      <td>00:42:19</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Back in Black</td>
      <td>1980</td>
      <td>00:42:11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>The Dark Side of the Moon</td>
      <td>1973</td>
      <td>00:42:49</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>00:57:44</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Bat Out of Hell</td>
      <td>1977</td>
      <td>00:46:33</td>
    </tr>
  </tbody>
</table>
</div>



**new dataframe from columns**:  

**`new_df_varObj = df_varObj[["col_header1", "col_header2"...]]`**  
* New Dataframes can be created from the column headers  
* **TWO Square brackets** are required to create it **as a Dataframe**  
* When **only ONE square bracket** is used, it will create a **series**....Panda series are essentially a 1D Dataframe  
* Column headers are **case sensitive**  


```python
# example showing new Dataframe from column headers

length_df = songs_frame[["Album","Length"]]
length_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Album</th>
      <th>Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Thriller</td>
      <td>00:42:19</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Back in Black</td>
      <td>00:42:11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>The Dark Side of the Moon</td>
      <td>00:42:49</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Bodyguard</td>
      <td>00:57:44</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Bat Out of Hell</td>
      <td>00:46:33</td>
    </tr>
  </tbody>
</table>
</div>



**append column**:  
    
**`df_varObj["new_col_header"] = ["row1", "row2"...]`**  
* Must contain **same number** of **elements** as current dataframe number of **rows**  
* Will append new column to last column of dataframe  


```python
# example appending new column to a dataframe with a list

df_xlsx["new"] = ['a','b','c','d','d','d','g','t']
df_xlsx
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
      <th>Genre</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Released.1</th>
      <th>Soundtrack</th>
      <th>Rating</th>
      <th>new</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Michael Jackson</td>
      <td>Thriller</td>
      <td>1982</td>
      <td>00:42:19</td>
      <td>pop, rock, R&amp;B</td>
      <td>46.0</td>
      <td>65</td>
      <td>1982-11-30</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AC/DC</td>
      <td>Back in Black</td>
      <td>1980</td>
      <td>00:42:11</td>
      <td>hard rock</td>
      <td>26.1</td>
      <td>50</td>
      <td>1980-07-25</td>
      <td>NaN</td>
      <td>9.5</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pink Floyd</td>
      <td>The Dark Side of the Moon</td>
      <td>1973</td>
      <td>00:42:49</td>
      <td>progressive rock</td>
      <td>24.2</td>
      <td>45</td>
      <td>1973-03-01</td>
      <td>NaN</td>
      <td>9.0</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Whitney Houston</td>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>00:57:44</td>
      <td>R&amp;B, soul, pop</td>
      <td>27.4</td>
      <td>44</td>
      <td>1992-11-17</td>
      <td>Y</td>
      <td>8.5</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Meat Loaf</td>
      <td>Bat Out of Hell</td>
      <td>1977</td>
      <td>00:46:33</td>
      <td>hard rock, progressive rock</td>
      <td>20.6</td>
      <td>43</td>
      <td>1977-10-21</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>d</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Eagles</td>
      <td>Their Greatest Hits (1971-1975)</td>
      <td>1976</td>
      <td>00:43:08</td>
      <td>rock, soft rock, folk rock</td>
      <td>32.2</td>
      <td>42</td>
      <td>1976-02-17</td>
      <td>NaN</td>
      <td>7.5</td>
      <td>d</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Bee Gees</td>
      <td>Saturday Night Fever</td>
      <td>1977</td>
      <td>01:15:54</td>
      <td>disco</td>
      <td>20.6</td>
      <td>40</td>
      <td>1977-11-15</td>
      <td>Y</td>
      <td>7.0</td>
      <td>g</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Fleetwood Mac</td>
      <td>Rumours</td>
      <td>1977</td>
      <td>00:40:01</td>
      <td>soft rock</td>
      <td>27.9</td>
      <td>40</td>
      <td>1977-02-04</td>
      <td>NaN</td>
      <td>6.5</td>
      <td>t</td>
    </tr>
  </tbody>
</table>
</div>



**series**:  

**`df_varObj["col_header"]`**  
OR  
**`df_varObj.col_header`**  - Only works if column name does not have spaces  
* A series is a **one dimensional** labled array, capable of holding data of any type  
* Method shown here will return the **entire column**  


```python
# example showing a Panda "series"

length_series = songs_frame["Released"]
length_series
```




    0    1982
    1    1980
    2    1973
    3    1992
    4    1977
    Name: Released, dtype: int64



**return multiple columns:**  

`df_var[["col_header, "col_header2", ...]]`  
* Access multiple columns as a pandas dataframe  
* Note **double brackets**  


```python
# can also access series with dot notation if column name does not have spaces

songs_frame.Album
```




    0                     Thriller
    1                Back in Black
    2    The Dark Side of the Moon
    3                The Bodyguard
    4              Bat Out of Hell
    Name: Album, dtype: object




```python
# example showing a Panda df being accessed by multiple column names - note double brackets

songs_frame[["Album", "Released"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Album</th>
      <th>Released</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Thriller</td>
      <td>1982</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Back in Black</td>
      <td>1980</td>
    </tr>
    <tr>
      <th>2</th>
      <td>The Dark Side of the Moon</td>
      <td>1973</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Bodyguard</td>
      <td>1992</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Bat Out of Hell</td>
      <td>1977</td>
    </tr>
  </tbody>
</table>
</div>



**saving dataframes**:  
 
To convert a dataset (list) to a dataframe:  
**`dataframeVar = pd.DataFrame(populatedDataset[1:],columns=populatedDataset[0])`**  
* This uses the first entry of the dataset as the column headers  

**`df.to_fileType("file_name.extension", sep=",", columns=None, header=True, index=True, index_label=None)`**  
* Use this method to save a dataframe to a file  
* **`sep=`** is the desired delimiter, defaults to **`","`**   
* **`columns=`** defaults to **None**, option to pass a sequence of column headers (present in dataframe) to write to file. **Columns not passed, will not be written to file**  
* **`header=`** defaults to **True**, when true, writes column headers. If a list of strings is given it is assumed to be aliases for the column names  
* **`index=`** defaults to **True**, when true, writes row names (index), note this **adds an extra column** to the file  
* **`index_label`** defaults to **None**, option to pass a str or sequence to rename columns, though note **current column headers are still present, but moved further along**  


```python
# reading in file for examples below

import csv

dataset =[]

with open('data/iris.csv') as fs:
    csv_reader = csv.reader(fs,delimiter=',') #if it is a comma, it can be omitted
    for row in csv_reader:
        dataset.append(row)
```


```python
dataset[:5]
```


```python
# example saving to csv file after first converting a dataset (list) to a dataframe

df = pd.DataFrame(dataset[1:], columns=dataset[0])
df.to_csv("data/panda, saving dataframe.csv", index=False)
```

[How to Work with Excel files in Pandas (see if getting errors)](https://towardsdatascience.com/how-to-work-with-excel-files-in-pandas-c584abb67bfb)


```python
# example saving to excel file

df.to_excel("data/panda, saving dataframe.xlsx")
```

**head** method:  

**`dataframe_varObj.head()`**  
* **.head( ) method** allows the **first 5 rows** to be examined 
* Can specify how many **rows to be displayed** in argument


```python
# example of .head() method with CSV file

df_csv.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
      <th>Genre</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Released.1</th>
      <th>Soundtrack</th>
      <th>Rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Michael Jackson</td>
      <td>Thriller</td>
      <td>1982</td>
      <td>0:42:19</td>
      <td>pop, rock, R&amp;B</td>
      <td>46.0</td>
      <td>65</td>
      <td>30-Nov-82</td>
      <td>NaN</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AC/DC</td>
      <td>Back in Black</td>
      <td>1980</td>
      <td>0:42:11</td>
      <td>hard rock</td>
      <td>26.1</td>
      <td>50</td>
      <td>25-Jul-80</td>
      <td>NaN</td>
      <td>9.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pink Floyd</td>
      <td>The Dark Side of the Moon</td>
      <td>1973</td>
      <td>0:42:49</td>
      <td>progressive rock</td>
      <td>24.2</td>
      <td>45</td>
      <td>01-Mar-73</td>
      <td>NaN</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Whitney Houston</td>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>0:57:44</td>
      <td>R&amp;B, soul, pop</td>
      <td>27.4</td>
      <td>44</td>
      <td>17-Nov-92</td>
      <td>Y</td>
      <td>8.5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Meat Loaf</td>
      <td>Bat Out of Hell</td>
      <td>1977</td>
      <td>0:46:33</td>
      <td>hard rock, progressive rock</td>
      <td>20.6</td>
      <td>43</td>
      <td>21-Oct-77</td>
      <td>NaN</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
</div>



**tail** method:  

**`dataframe_varObj.tail()`**  
* **.tail( ) method** allows the **last 5 rows** to be examined 
* Can specify how many **rows to be displayed** in argument


```python
# example of .tail() method with Excel file

df_xlsx.tail()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
      <th>Genre</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Released.1</th>
      <th>Soundtrack</th>
      <th>Rating</th>
      <th>new</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>Whitney Houston</td>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>00:57:44</td>
      <td>R&amp;B, soul, pop</td>
      <td>27.4</td>
      <td>44</td>
      <td>1992-11-17</td>
      <td>Y</td>
      <td>8.5</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Meat Loaf</td>
      <td>Bat Out of Hell</td>
      <td>1977</td>
      <td>00:46:33</td>
      <td>hard rock, progressive rock</td>
      <td>20.6</td>
      <td>43</td>
      <td>1977-10-21</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>d</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Eagles</td>
      <td>Their Greatest Hits (1971-1975)</td>
      <td>1976</td>
      <td>00:43:08</td>
      <td>rock, soft rock, folk rock</td>
      <td>32.2</td>
      <td>42</td>
      <td>1976-02-17</td>
      <td>NaN</td>
      <td>7.5</td>
      <td>d</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Bee Gees</td>
      <td>Saturday Night Fever</td>
      <td>1977</td>
      <td>01:15:54</td>
      <td>disco</td>
      <td>20.6</td>
      <td>40</td>
      <td>1977-11-15</td>
      <td>Y</td>
      <td>7.0</td>
      <td>g</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Fleetwood Mac</td>
      <td>Rumours</td>
      <td>1977</td>
      <td>00:40:01</td>
      <td>soft rock</td>
      <td>27.9</td>
      <td>40</td>
      <td>1977-02-04</td>
      <td>NaN</td>
      <td>6.5</td>
      <td>t</td>
    </tr>
  </tbody>
</table>
</div>



**take** method:  

**`dataframe_varObj.take([indices], axis=0, **kwargs)`**  
* Return the elements in the given positional indices along an axis  
* Can be used to return specific rows by specifying indices in order you would like displayed  
* `kwargs` is for compatibility with numpy.take(), no effect on ouput  


```python
# example of .take() method  

df_xlsx.take([5, 3])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
      <th>Genre</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Released.1</th>
      <th>Soundtrack</th>
      <th>Rating</th>
      <th>new</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>Eagles</td>
      <td>Their Greatest Hits (1971-1975)</td>
      <td>1976</td>
      <td>00:43:08</td>
      <td>rock, soft rock, folk rock</td>
      <td>32.2</td>
      <td>42</td>
      <td>1976-02-17</td>
      <td>NaN</td>
      <td>7.5</td>
      <td>d</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Whitney Houston</td>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>00:57:44</td>
      <td>R&amp;B, soul, pop</td>
      <td>27.4</td>
      <td>44</td>
      <td>1992-11-17</td>
      <td>Y</td>
      <td>8.5</td>
      <td>d</td>
    </tr>
  </tbody>
</table>
</div>



**info** method:  

**`df_var.info()`**  
* Returns some basic info of the data types in the dataset  


```python
# example of info method  

df_xlsx.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 8 entries, 0 to 7
    Data columns (total 11 columns):
     #   Column                            Non-Null Count  Dtype         
    ---  ------                            --------------  -----         
     0   Artist                            8 non-null      object        
     1   Album                             8 non-null      object        
     2   Released                          8 non-null      int64         
     3   Length                            8 non-null      object        
     4   Genre                             8 non-null      object        
     5   Music Recording Sales (millions)  8 non-null      float64       
     6   Claimed Sales (millions)          8 non-null      int64         
     7   Released.1                        8 non-null      datetime64[ns]
     8   Soundtrack                        2 non-null      object        
     9   Rating                            8 non-null      float64       
     10  new                               8 non-null      object        
    dtypes: datetime64[ns](1), float64(2), int64(2), object(6)
    memory usage: 832.0+ bytes
    

**describe** method:  

**`df_var.describe()`**  
* If dataset includes **numeric data**, can **get descriptive statistics** using the describe()  
* **count**: Count number of non-NA/null observations <br>
* **max**: Maximum of the values in the object.<br>*italicised text*
* **min**: Minimum of the values in the object.<br>
* **mean**: Mean of the values.<br>
* **std**: Standard deviation of the observations.<br>
* **percentiles**: The percentiles to include in the output. All should fall between 0 and 1. The default is [.25, .5, .75], which returns the 25th, 50th, and 75th percentiles


```python
# example of describe method

df_xlsx.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Released</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1979.250000</td>
      <td>28.125000</td>
      <td>46.125000</td>
      <td>8.250000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>5.800246</td>
      <td>8.189322</td>
      <td>8.271077</td>
      <td>1.224745</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1973.000000</td>
      <td>20.600000</td>
      <td>40.000000</td>
      <td>6.500000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1976.750000</td>
      <td>23.300000</td>
      <td>41.500000</td>
      <td>7.375000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1977.000000</td>
      <td>26.750000</td>
      <td>43.500000</td>
      <td>8.250000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1980.500000</td>
      <td>28.975000</td>
      <td>46.250000</td>
      <td>9.125000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1992.000000</td>
      <td>46.000000</td>
      <td>65.000000</td>
      <td>10.000000</td>
    </tr>
  </tbody>
</table>
</div>



**return column names**:  

**`df_varObj.columns`**  
* Will return all the **column headers**  


```python
# creating new dataframe

df = pd.read_csv(csv_path)
```


```python
# showing full df
df
```


```python
# getting column headers

df.columns
```

**return index**:  

**`df_varObj.index`**  
* Will return **range for rows** or **index names** if not integers    


```python
# getting indexes

df.index
```

**shape** method:  

**`df_varObj.shape`**  
* Will return **size of dataframe** (# rows, # columns)  
* Note **index NOT included** as a column in the dataframe  


```python
# getting shape of a dataframe

df.shape
```

**.loc[ ]** method (Label of column):  

**`df_varObj.loc[row_index_Name, "col_header"]`**  
OR **pass in conditional:**  
**`df_varObj.loc[df_varObj["col_to_search"] comparator condition]`**  - This will also work without `.loc`   
* Selection by **label**  
* If only inputting **`row_index_Name`** , this will return the entire row selected  
* Rows start at **0**  
* **NOTE** row index is the **name of the row** and not necessarily an integer...**IT IS NOT** the **"index"**  
* **Square brackets**  
* Returns **KeyError** if **column header not found**


```python
# printing df for viewing

songs_frame
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Thriller</td>
      <td>1982</td>
      <td>00:42:19</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Back in Black</td>
      <td>1980</td>
      <td>00:42:11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>The Dark Side of the Moon</td>
      <td>1973</td>
      <td>00:42:49</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>00:57:44</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Bat Out of Hell</td>
      <td>1977</td>
      <td>00:46:33</td>
    </tr>
  </tbody>
</table>
</div>




```python
songs_frame.loc[0]
```


```python
# example of .loc[] method

songs_frame.loc[3, "Album"]
```


```python
# creating new dataframe and changing index names

df_example = pd.DataFrame(songs)

df_example.index = ("A","B","C","D","E")
df_example
```


```python
# loc example showing that row indexing is done by row index "name"

df_example.loc["D","Album"]
```


```python
# printing for viewing

df_xlsx
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
      <th>Genre</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Released.1</th>
      <th>Soundtrack</th>
      <th>Rating</th>
      <th>new</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Michael Jackson</td>
      <td>Thriller</td>
      <td>1982</td>
      <td>00:42:19</td>
      <td>pop, rock, R&amp;B</td>
      <td>46.0</td>
      <td>65</td>
      <td>1982-11-30</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AC/DC</td>
      <td>Back in Black</td>
      <td>1980</td>
      <td>00:42:11</td>
      <td>hard rock</td>
      <td>26.1</td>
      <td>50</td>
      <td>1980-07-25</td>
      <td>NaN</td>
      <td>9.5</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pink Floyd</td>
      <td>The Dark Side of the Moon</td>
      <td>1973</td>
      <td>00:42:49</td>
      <td>progressive rock</td>
      <td>24.2</td>
      <td>45</td>
      <td>1973-03-01</td>
      <td>NaN</td>
      <td>9.0</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Whitney Houston</td>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>00:57:44</td>
      <td>R&amp;B, soul, pop</td>
      <td>27.4</td>
      <td>44</td>
      <td>1992-11-17</td>
      <td>Y</td>
      <td>8.5</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Meat Loaf</td>
      <td>Bat Out of Hell</td>
      <td>1977</td>
      <td>00:46:33</td>
      <td>hard rock, progressive rock</td>
      <td>20.6</td>
      <td>43</td>
      <td>1977-10-21</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>d</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Eagles</td>
      <td>Their Greatest Hits (1971-1975)</td>
      <td>1976</td>
      <td>00:43:08</td>
      <td>rock, soft rock, folk rock</td>
      <td>32.2</td>
      <td>42</td>
      <td>1976-02-17</td>
      <td>NaN</td>
      <td>7.5</td>
      <td>d</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Bee Gees</td>
      <td>Saturday Night Fever</td>
      <td>1977</td>
      <td>01:15:54</td>
      <td>disco</td>
      <td>20.6</td>
      <td>40</td>
      <td>1977-11-15</td>
      <td>Y</td>
      <td>7.0</td>
      <td>g</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Fleetwood Mac</td>
      <td>Rumours</td>
      <td>1977</td>
      <td>00:40:01</td>
      <td>soft rock</td>
      <td>27.9</td>
      <td>40</td>
      <td>1977-02-04</td>
      <td>NaN</td>
      <td>6.5</td>
      <td>t</td>
    </tr>
  </tbody>
</table>
</div>




```python
# example of using .loc for conditional search

df_xlsx.loc[df_xlsx["Released"] > 1978]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
      <th>Genre</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Released.1</th>
      <th>Soundtrack</th>
      <th>Rating</th>
      <th>new</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Michael Jackson</td>
      <td>Thriller</td>
      <td>1982</td>
      <td>00:42:19</td>
      <td>pop, rock, R&amp;B</td>
      <td>46.0</td>
      <td>65</td>
      <td>1982-11-30</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AC/DC</td>
      <td>Back in Black</td>
      <td>1980</td>
      <td>00:42:11</td>
      <td>hard rock</td>
      <td>26.1</td>
      <td>50</td>
      <td>1980-07-25</td>
      <td>NaN</td>
      <td>9.5</td>
      <td>b</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Whitney Houston</td>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>00:57:44</td>
      <td>R&amp;B, soul, pop</td>
      <td>27.4</td>
      <td>44</td>
      <td>1992-11-17</td>
      <td>Y</td>
      <td>8.5</td>
      <td>d</td>
    </tr>
  </tbody>
</table>
</div>




```python
# above can also be done as follows

df_xlsx[df_xlsx["Released"] > 1978]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Album</th>
      <th>Released</th>
      <th>Length</th>
      <th>Genre</th>
      <th>Music Recording Sales (millions)</th>
      <th>Claimed Sales (millions)</th>
      <th>Released.1</th>
      <th>Soundtrack</th>
      <th>Rating</th>
      <th>new</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Michael Jackson</td>
      <td>Thriller</td>
      <td>1982</td>
      <td>00:42:19</td>
      <td>pop, rock, R&amp;B</td>
      <td>46.0</td>
      <td>65</td>
      <td>1982-11-30</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AC/DC</td>
      <td>Back in Black</td>
      <td>1980</td>
      <td>00:42:11</td>
      <td>hard rock</td>
      <td>26.1</td>
      <td>50</td>
      <td>1980-07-25</td>
      <td>NaN</td>
      <td>9.5</td>
      <td>b</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Whitney Houston</td>
      <td>The Bodyguard</td>
      <td>1992</td>
      <td>00:57:44</td>
      <td>R&amp;B, soul, pop</td>
      <td>27.4</td>
      <td>44</td>
      <td>1992-11-17</td>
      <td>Y</td>
      <td>8.5</td>
      <td>d</td>
    </tr>
  </tbody>
</table>
</div>



**slicing using loc**:  

**`df_varObj.loc[start_row_index_Name : end_row_index_Name, start_col_header : end_col_header]`**  
* This will slice a dataframe to create a new one  
* **Square** brackets  
* **NOTE** row index is the **name of the row** and not necessarily an integer...**IT IS NOT** the **"index"**  
* **Bewear** If row index names are default integers, a slice such as 1:3 will return rows 2,3 and 4 with names 1,2 and 3 accordingly   
* Can be assigned to a new variable to save
* If **only selecting one column or row**, this will **return as Pandas Series** rather than a dataframe     


```python
# example of slicing a Dataframe using .loc[] method

songs_frame.loc[1:4,"Released":"Length"]
```


```python
# loc slicing example showing that row indexing is done by row index "name"

df_example.loc["B":"D","Released":"Length"]
```

**.iloc[ ]** method (Index-label of column):    

**`df_varObj.iloc[row_index, col_index]`**  
* Selection by **position**  
* If only inputting **`row_index`** , this will return the entire row selected  
* Rows and Columns start at **0** (not including index column)  
* **Square brackets**  
* Returns **IndexError** if requested indexer is out-of-bounds  


```python
# example of .iloc[] method

songs_frame.iloc[0,0]
```

**slicing using .iloc[ ]** method:  

**`df_varObj.iloc[start_row_index : end_row_index, start_col_index : end_col_index]`**  
* This will slice a dataframe to create a new one  
* Can be assigned to a new variable to save  
* **Square** brackets  
* If **only selecting one column or row**, this will **return as Pandas Series** rather than a dataframe   


```python
# example of slicing a Dataframe using .iloc[] method

new_df2 = df_csv.iloc[1:4,3:6]
new_df2
```

**unique** method:  

**`df_varObj["col_header_toCheck"].unique()`**  
* Finds unique values in a column and returns values as an array  
* **Square** brackets  


```python
# example of .unique() method

df["Released"].unique()
```

**selecting data with condition**:  


**`df_varObj[df_varObj.col_header condition_to_check]`**  
**Can also be written:**  
**`df_varObj[df_varObj["col_header"]condition_to_check]`**  
* Without the first df_varObj name and first set of square brackets, this will return a series with boolean values relevant to the conditon to be checked against  
* Assign to a new variable to save  


```python
# printing datafram again for comparison to below examples

df
```


```python
# exmple of condition checking column "Released" and outputting in a series
# note this could also be written as: df["Released"]>=1980

df.Released>=1980
```


```python
# example of condition checking column "Released" and outputting to a dataframe
# note this could also be written as: df[df.Released>1980]

yearDF = df[df["Released"]>=1980]
yearDF
```

**rename columns with a list**:  

**`df_varObj.columns = ["col_header1", "col_header2"...]`**  
* Must contain **same number** of **elements** as current dataframe number of **columns**  
* Will replace column headers in order of list  


```python
# example changing all column headers with a list

length_df.columns = ["a", 1]
length_df
```

**reorder columns**:  

**`df_varObj = df_varObj[["new_1st_col_header", "new_2nd_col_header"...]]`**  
* Will reorder columns with their related data  


```python
# example of reordering columns

length_df = length_df[[1,'a']]
length_df
```

**set index**:  

**`df_varObj.set_index(["col_header1","col_header2"], *drop=Bool, append=Bool, inplace=Bool)`**  
* If only using one column to set index, square brackets are not required  
* **drop** is **optional**, defaults to True, when False will keep original column as well as assign to index  
* **append** is **optional**, defaults to False, when True will add new index to existing rather than replacing  
* **inplace** is **optional**, defaults to False, when True will make changes to original dataframe rather than having to set it to a new dataframe variable object  


```python
# example of replacing default index with existing columns  

dfIndex = df.set_index(["Genre","Released"])
dfIndex
```

**set index with list or tuple**:  

**`df_varObj.index = list or tuple`**  
* This will replace the existing index with the given list or tuple elements  
* There must be the same number of elements as current index values  
* **Overwrites** current dataframe unless assinging to a new one  
* **Will NOT** reset indexes to original columns  


```python
# example setting index to a given tuple
# note both index columns were replaced by the tuple and not reinserted to the dataframe

indexTuple = ("a","b", "c","d","e","f","g","h")      # populating tuple for index

dfTupleIndex = dfIndex[:]            # cloning dataframe to prevent overwriting original
dfTupleIndex.index = indexTuple      # setting index to tuple elements
dfTupleIndex                         # printing dataframe
```

**set index name**:  

**`df_varObj.index.name = "New Name"`**  
* This will set the index columns name  
* Setting to **None** will clear the indexes name  


```python
# example setting index Name

dfTupleIndex.index.name = "Tuple Index"
dfTupleIndex
```


```python
# example clearing index name

dfTupleIndex.index.name = None
dfTupleIndex
```

**reset to default index**:  

**`df_varObj.reset_index(*drop=Bool, *inplace=Bool)`**  
* Will reset index values to default integers  
* **drop** is **optional**, defaults to False, when **True will NOT reinsert column** back into dataframe   
* **inplace** is **optional**, defaults to False, when True will make changes to original dataframe rather than having to set it to a new dataframe variable object  
* If index had no column header, new header (when column is reinserted to dataframe) will be "index"  


```python
# example of resetting index to default integer values

dfTupleIndex.reset_index(drop=True,inplace=True)
dfTupleIndex
```

**drop** function:  

**`df_varObj.drop(self, labels=None, axis=0, index=None, columns=None)`**  
* **`labels`** = Index or column labels to drop  
* **`axis`** = Whether to drop labels from the index (0 or ‘index’) or columns (1 or ‘columns’)  
* **`index`** = Alternative to specifying axis (labels, axis=0 is equivalent to index=labels)  
* **`columns`** = Alternative to specifying axis (labels, axis=1 is equivalent to columns=labels)  


```python
# library imported for examples below
import numpy as np
```


```python
df = pd.DataFrame(np.arange(12).reshape(3, 4),
                  columns=['P', 'Q', 'R', 'S'])
df
```


```python
df.drop(['Q', 'R'], axis=1)
```

**groupby( )** method:  

**`groupedDataFrameObj = dataFrameObj.groupby(groupingCriteria)`**  
* [Further information](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html)  
* **`groupingCriteria`** is usually a column header but can be any function by which to split the data  
* if **`groupingCriteria`** is a **single** column, it can be passed as a **string**, **multiple** should be passed as a **list**  
* The dataframe can be displayed by determining how to display each group value:  

$\;\;\;\;\;\;\;\;$**`groupedDataFrameObj.first( )`**  
* **`first( )`** displays the first in the table for each group  
* **`last( )`** displays the last in the table  
* **`min( )`** displays the minimum for each group  
* **`max( )`** displays the maximum for each group  
* **`mean( )`** displays the mean for each group  


* This can be saved back to a csv or excel file as a dataframe object can be  


```python
# Creating dataframe to show groupby

df = pd.read_excel("data/iris.xlsx")

df
```


```python
# Grouping by species, and showing the row of the first in the dataframe 

groupedDataFrame = df.groupby("species") 

groupedDataFrame.first() 
```


```python
# Multiple grouping, first by column "species", then by column "sepal_width"
# Showing the row of the last result in dataframe of each group

groupedDataFrame = df.groupby(["species", "sepal_width"]) 
groupedDataFrame.last()
```


```python
# Getting group "species = versicolour and sepal_width = 2.2"

groupedDataFrame.get_group(("versicolor", 2.2))
```


```python
# Performing mathematical operations on each cell and returning result grouped by column "species"

groupedDataFrame = df.groupby("species").mean()
groupedDataFrame
```

[<p style="text-align: right;">**⬆ Top of Page ⬆**</p>](#Pandas)

---
