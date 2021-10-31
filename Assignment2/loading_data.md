---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.12
    jupytext_version: 1.6.0
kernelspec:
  display_name: csc310
  language: python
  name: csc310
---

# Accesing Data

+++

Find 3 datasets of interest to you that are provided in different file formats. Choose datasets that are not too big, so that they do not take more than a few second to load. At least one dataset, must have non numerical (eg string or boolean) data in at least 1 column. Complete a dictionary for each with the url, a name, and what function should be used to load the data into a pandas.DataFrame.

Use a list of those dictionaries to iterate over the datasets and build a table that describes them, with the following columns ['name','source','num_rows', 'num_columns','source_file_name']. The source_file_name should be the part of the url after the last /. Display that summary table as a dataframe and save it as a csv, named dataset_summary.csv.

```{code-cell} ipython3
# imports
import pandas as pd
```

```{code-cell} ipython3
d1 = {'url':'https://www.numbeo.com/quality-of-life/rankings_by_country.jsp',
     'name': 'rankings_by_country',
     'load_func': 'pd.read_html()'}
    
d2 = {'url': 'https://en.wikipedia.org/wiki/List_of_best-selling_music_artists' ,
     'name': 'List_of_best-selling_music_artists' ,
     'load_func': 'pd.read_html()'}

d3 = {'url': 'https://finance.yahoo.com/quote/TSLA/history/' ,
     'name': 'history',
     'load_func': 'pd.read_html()'}

datasets_info_dict = [d1,d2,d3]
```

Use a list of those dictionaries to iterate over the datasets and build a table that describes them, with the following columns ['name','source','num_rows', 'num_columns','source_file_name'].

```{code-cell} ipython3

```

## Dataset summary


```{code-cell} ipython3
columns = ['name','source','num_rows', 'num_columns','source_file_name']
```

```{code-cell} ipython3
df1= pd.read_html('https://www.numbeo.com/quality-of-life/rankings_by_country.jsp')
```

```{code-cell} ipython3
df1[1]
```

```{code-cell} ipython3
type(df1[1])
```

```{code-cell} ipython3
df1[1].shape
```

```{code-cell} ipython3
df1[1].head()
```

```{code-cell} ipython3
df1[1].tail()
```

# display the heading with the last seven rows

```{code-cell} ipython3
df1[1].tail(7)
```

# make and display a new data frame with only the non numerical columns

```{code-cell} ipython3
df1[1].select_dtypes(exclude='number').style.hide_index() 
```

```{code-cell} ipython3
df1[1].index
```

was the format that the data was provided in a good format? why or why not?

+++

Yes. Because it was provided in rows and columns and data type was consistent in each column. 

```{code-cell} ipython3
df2= pd.read_html('https://en.wikipedia.org/wiki/List_of_best-selling_music_artists')
```

```{code-cell} ipython3
df2[0]
```

display the heading and the first three rows

```{code-cell} ipython3
df2[0].head(3)
```

display the datatype for each column

```{code-cell} ipython3
df2[0].dtypes
```

# Are there any variables where pandas may have read in the data as a datatype that’s not what you expect (eg a numerical column mistaken for strings)?

+++

no. all columns include non numerical characters.

```{code-cell} ipython3

```

```{code-cell} ipython3
df3= pd.read_html('https://finance.yahoo.com/quote/TSLA/history/')
```

```{code-cell} ipython3
df3[0]
```

display the first 5 even rows of the data for three columns of your choice

```{code-cell} ipython3
df3[0].iloc[::2, :].head()
```

```{code-cell} ipython3
even_rows = (df3[0].index % 2 == 0)
```

```{code-cell} ipython3
print(even_rows)
```

# try reading it in with the wrong read_ function. If you had done this by accident, how could you tell?

```{code-cell} ipython3
df3= pd.read_csv('https://finance.yahoo.com/quote/TSLA/history/')
```

I can undesrtand it by the error I am getting, as it says this fuction is not able to parse data

+++

# (for the process skill)

# Make a list of a data science pipeline and denote which types of programming might be helpful at each staged. Include this in a markdown cell in the same notebook with your analysis'''

+++

    O — Obtaining our data (MySQL)
    S — Scrubbing / Cleaning our data (Python or R)
    E — Exploring / Visualizing our data will allow us to find patterns and trends (Numpy, Matplotlib, Pandas or Scipy)
    M — Modeling our data will give us our predictive power as a wizard (Sci-kit Learn)
    N — Interpreting our data

+++

## Exploring <dataset name here> 

- display the heading with the last seven rows
- make a subset of the data columnwise by only keeping the non numerical columns.
- was the format that the data was provided in a good format? why or why not?

```{code-cell} ipython3

```

## Exploring <dataset name here>
    
- display the heading and the first three rows
- display the datatype for each column
- Are there any variables where pandas may have read in the data as a datatype that's not what you expect (eg a numerical column mistaken for strings)

```{code-cell} ipython3

```

## Exploring <dataset name>
    
- display the first 5 even rows of the data for three columns of your choice

```{code-cell} ipython3

```

## Testing reading in data

```{code-cell} ipython3

```
