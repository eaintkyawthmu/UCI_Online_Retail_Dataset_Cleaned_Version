# Online Retail DataSet

**Abstract**: This is a transnational data set which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail.

**Data Set Characteristics**:  Multivariate, Sequential, Time-Series

**Number of Instances**: 541909

**Area**: Business

**Attribute Characteristics**: Integer, Real

**Number of Attributes**:8

**Date Donated**: 2015-11-06

**Associated Tasks**: Classification, Clustering

**Missing Values?**: N/A

**Number of Web Hits**: 846307


**Source**:

Dr Daqing Chen, Director: Public Analytics group. chend '@' lsbu.ac.uk, School of Engineering, London South Bank University, London SE1 0AA, UK.


**Data Set Information**:

This is a transnational data set which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail.The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers.

**Citation**:

Daqing Chen, Sai Liang Sain, and Kun Guo, Data mining for the online retail industry: A case study of RFM model-based customer segmentation using data mining, Journal of Database Marketing and Customer Strategy Management, Vol. 19, No. 3, pp. 197â€“208, 2012 (Published online before print: 27 August 2012. doi: 10.1057/dbm.2012.17).

**Dataset Download Link**
https://archive.ics.uci.edu/ml/machine-learning-databases/00352/




```python
import pandas as pd
import matplotlib.pyplot as plt
```


```python
# Read the dataset (excel file) into a DataFrame
#Since there is only sheet in excel file we can use below code to read the entire excel file to dataframe
df_original = pd.read_excel('Online Retail.xlsx') 
df_original
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
      <th>InvoiceNo</th>
      <th>StockCode</th>
      <th>Description</th>
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>UnitPrice</th>
      <th>CustomerID</th>
      <th>Country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>536365</td>
      <td>85123A</td>
      <td>WHITE HANGING HEART T-LIGHT HOLDER</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>2.55</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>1</th>
      <td>536365</td>
      <td>71053</td>
      <td>WHITE METAL LANTERN</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>2</th>
      <td>536365</td>
      <td>84406B</td>
      <td>CREAM CUPID HEARTS COAT HANGER</td>
      <td>8</td>
      <td>2010-12-01 08:26:00</td>
      <td>2.75</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>3</th>
      <td>536365</td>
      <td>84029G</td>
      <td>KNITTED UNION FLAG HOT WATER BOTTLE</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>4</th>
      <td>536365</td>
      <td>84029E</td>
      <td>RED WOOLLY HOTTIE WHITE HEART.</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>541904</th>
      <td>581587</td>
      <td>22613</td>
      <td>PACK OF 20 SPACEBOY NAPKINS</td>
      <td>12</td>
      <td>2011-12-09 12:50:00</td>
      <td>0.85</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541905</th>
      <td>581587</td>
      <td>22899</td>
      <td>CHILDREN'S APRON DOLLY GIRL</td>
      <td>6</td>
      <td>2011-12-09 12:50:00</td>
      <td>2.10</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541906</th>
      <td>581587</td>
      <td>23254</td>
      <td>CHILDRENS CUTLERY DOLLY GIRL</td>
      <td>4</td>
      <td>2011-12-09 12:50:00</td>
      <td>4.15</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541907</th>
      <td>581587</td>
      <td>23255</td>
      <td>CHILDRENS CUTLERY CIRCUS PARADE</td>
      <td>4</td>
      <td>2011-12-09 12:50:00</td>
      <td>4.15</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541908</th>
      <td>581587</td>
      <td>22138</td>
      <td>BAKING SET 9 PIECE RETROSPOT</td>
      <td>3</td>
      <td>2011-12-09 12:50:00</td>
      <td>4.95</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
  </tbody>
</table>
<p>541909 rows × 8 columns</p>
</div>




```python
df =df_original.copy()
```


```python
# Display information about the DataFrame
print(df.info())
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 541909 entries, 0 to 541908
    Data columns (total 8 columns):
     #   Column       Non-Null Count   Dtype         
    ---  ------       --------------   -----         
     0   InvoiceNo    541909 non-null  object        
     1   StockCode    541909 non-null  object        
     2   Description  540455 non-null  object        
     3   Quantity     541909 non-null  int64         
     4   InvoiceDate  541909 non-null  datetime64[ns]
     5   UnitPrice    541909 non-null  float64       
     6   CustomerID   406829 non-null  float64       
     7   Country      541909 non-null  object        
    dtypes: datetime64[ns](1), float64(2), int64(1), object(4)
    memory usage: 33.1+ MB
    None



```python
print(df.describe())
```

                Quantity                    InvoiceDate      UnitPrice   
    count  541909.000000                         541909  541909.000000  \
    mean        9.552250  2011-07-04 13:34:57.156386048       4.611114   
    min    -80995.000000            2010-12-01 08:26:00  -11062.060000   
    25%         1.000000            2011-03-28 11:34:00       1.250000   
    50%         3.000000            2011-07-19 17:17:00       2.080000   
    75%        10.000000            2011-10-19 11:27:00       4.130000   
    max     80995.000000            2011-12-09 12:50:00   38970.000000   
    std       218.081158                            NaN      96.759853   
    
              CustomerID  
    count  406829.000000  
    mean    15287.690570  
    min     12346.000000  
    25%     13953.000000  
    50%     15152.000000  
    75%     16791.000000  
    max     18287.000000  
    std      1713.600303  


According to dataframe info there are 8 Columns and 541909 rows

It looks like 'Description' and 'CustomerID' have missing values 540455 and 406829.

So we should check the missing values first.



```python
df.isna().sum()
```




    InvoiceNo           0
    StockCode           0
    Description      1454
    Quantity            0
    InvoiceDate         0
    UnitPrice           0
    CustomerID     135080
    Country             0
    dtype: int64



Before we drop the missing values or fill, we have to make sure that the missing data is relatively small or not compared to the total dataset.


```python
# Get the total number of rows in the DataFrame
total_rows = len(df)

# Get the number of missing customer IDs
missing_customer_ids = df['CustomerID'].isna().sum()

# Get the percentage of missing customer IDs
missing_customer_percentage = (missing_customer_ids / total_rows) * 100

# Print the percentage of missing customer IDs
print("Percentage of Missing Customer IDs:", missing_customer_percentage)
```

    Percentage of Missing Customer IDs: 24.926694334288598


Luckly, we didn't drop anything, beacuse the percentage of Missing Customer IDs are 24.93% so it is around a quarter of our customer IDs. 

We decided not to drop anything, but we have to do something about the data so, we will fill those CustomerID with 0.


```python
df['CustomerID'].fillna(0, inplace=True)
```

After filling with 0 we should check that again, We should go further about Missing Customer ID later, but not now. we will just keep those rows with 0 in the data.


```python
df.isna().sum()
```




    InvoiceNo         0
    StockCode         0
    Description    1454
    Quantity          0
    InvoiceDate       0
    UnitPrice         0
    CustomerID        0
    Country           0
    dtype: int64



Now we want to invesgate Missing Descriptions


```python
# Get the number of Missing Descriptions
missing_descriptions = df['Description'].isna().sum()

# Calculate the percentage of Missing Descriptions
missing_descriptions_percentage = (missing_descriptions / total_rows) * 100

# Print the percentage of Missing Descriptions
print("Percentage of Missing Descriptions:", missing_descriptions_percentage)
```

    Percentage of Missing Descriptions: 0.2683107311375157


We can drop the missing description rows since it is only 0.27%. 
 Description is crucial in this dataset since it stores what is the transanction is about or cancel or return or discount info. We can't delete the Description before we check anything. So we will filled those rows with some text.


```python
# Fill missing Description values with "Missing_Description"
df['Description'] = df['Description'].fillna('Missing_Description')

# Select rows with 'Missing_Description' in the Description column
missing_descriptions = df[df['Description'] == 'Missing_Description']
missing_descriptions
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
      <th>InvoiceNo</th>
      <th>StockCode</th>
      <th>Description</th>
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>UnitPrice</th>
      <th>CustomerID</th>
      <th>Country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>622</th>
      <td>536414</td>
      <td>22139</td>
      <td>Missing_Description</td>
      <td>56</td>
      <td>2010-12-01 11:52:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>1970</th>
      <td>536545</td>
      <td>21134</td>
      <td>Missing_Description</td>
      <td>1</td>
      <td>2010-12-01 14:32:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>1971</th>
      <td>536546</td>
      <td>22145</td>
      <td>Missing_Description</td>
      <td>1</td>
      <td>2010-12-01 14:33:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>1972</th>
      <td>536547</td>
      <td>37509</td>
      <td>Missing_Description</td>
      <td>1</td>
      <td>2010-12-01 14:33:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>1987</th>
      <td>536549</td>
      <td>85226A</td>
      <td>Missing_Description</td>
      <td>1</td>
      <td>2010-12-01 14:34:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>535322</th>
      <td>581199</td>
      <td>84581</td>
      <td>Missing_Description</td>
      <td>-2</td>
      <td>2011-12-07 18:26:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>535326</th>
      <td>581203</td>
      <td>23406</td>
      <td>Missing_Description</td>
      <td>15</td>
      <td>2011-12-07 18:31:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>535332</th>
      <td>581209</td>
      <td>21620</td>
      <td>Missing_Description</td>
      <td>6</td>
      <td>2011-12-07 18:35:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>536981</th>
      <td>581234</td>
      <td>72817</td>
      <td>Missing_Description</td>
      <td>27</td>
      <td>2011-12-08 10:33:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>538554</th>
      <td>581408</td>
      <td>85175</td>
      <td>Missing_Description</td>
      <td>20</td>
      <td>2011-12-08 14:06:00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>United Kingdom</td>
    </tr>
  </tbody>
</table>
<p>1454 rows × 8 columns</p>
</div>



Now, all the missing data are filled. we are going to check again.


```python
df.isna().sum()
```




    InvoiceNo      0
    StockCode      0
    Description    0
    Quantity       0
    InvoiceDate    0
    UnitPrice      0
    CustomerID     0
    Country        0
    dtype: int64



Now it is time to check the data types before we touch any of the data.


```python
#We will check the datatype
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 541909 entries, 0 to 541908
    Data columns (total 8 columns):
     #   Column       Non-Null Count   Dtype         
    ---  ------       --------------   -----         
     0   InvoiceNo    541909 non-null  object        
     1   StockCode    541909 non-null  object        
     2   Description  541909 non-null  object        
     3   Quantity     541909 non-null  int64         
     4   InvoiceDate  541909 non-null  datetime64[ns]
     5   UnitPrice    541909 non-null  float64       
     6   CustomerID   541909 non-null  float64       
     7   Country      541909 non-null  object        
    dtypes: datetime64[ns](1), float64(2), int64(1), object(4)
    memory usage: 33.1+ MB


DataTypes looks ok, but We should see the data first.


```python
df.head(10)
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
      <th>InvoiceNo</th>
      <th>StockCode</th>
      <th>Description</th>
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>UnitPrice</th>
      <th>CustomerID</th>
      <th>Country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>536365</td>
      <td>85123A</td>
      <td>WHITE HANGING HEART T-LIGHT HOLDER</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>2.55</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>1</th>
      <td>536365</td>
      <td>71053</td>
      <td>WHITE METAL LANTERN</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>2</th>
      <td>536365</td>
      <td>84406B</td>
      <td>CREAM CUPID HEARTS COAT HANGER</td>
      <td>8</td>
      <td>2010-12-01 08:26:00</td>
      <td>2.75</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>3</th>
      <td>536365</td>
      <td>84029G</td>
      <td>KNITTED UNION FLAG HOT WATER BOTTLE</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>4</th>
      <td>536365</td>
      <td>84029E</td>
      <td>RED WOOLLY HOTTIE WHITE HEART.</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>5</th>
      <td>536365</td>
      <td>22752</td>
      <td>SET 7 BABUSHKA NESTING BOXES</td>
      <td>2</td>
      <td>2010-12-01 08:26:00</td>
      <td>7.65</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>6</th>
      <td>536365</td>
      <td>21730</td>
      <td>GLASS STAR FROSTED T-LIGHT HOLDER</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>4.25</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>7</th>
      <td>536366</td>
      <td>22633</td>
      <td>HAND WARMER UNION JACK</td>
      <td>6</td>
      <td>2010-12-01 08:28:00</td>
      <td>1.85</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>8</th>
      <td>536366</td>
      <td>22632</td>
      <td>HAND WARMER RED POLKA DOT</td>
      <td>6</td>
      <td>2010-12-01 08:28:00</td>
      <td>1.85</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>9</th>
      <td>536367</td>
      <td>84879</td>
      <td>ASSORTED COLOUR BIRD ORNAMENT</td>
      <td>32</td>
      <td>2010-12-01 08:34:00</td>
      <td>1.69</td>
      <td>13047.0</td>
      <td>United Kingdom</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail(10)
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
      <th>InvoiceNo</th>
      <th>StockCode</th>
      <th>Description</th>
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>UnitPrice</th>
      <th>CustomerID</th>
      <th>Country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>541899</th>
      <td>581587</td>
      <td>22726</td>
      <td>ALARM CLOCK BAKELIKE GREEN</td>
      <td>4</td>
      <td>2011-12-09 12:50:00</td>
      <td>3.75</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541900</th>
      <td>581587</td>
      <td>22730</td>
      <td>ALARM CLOCK BAKELIKE IVORY</td>
      <td>4</td>
      <td>2011-12-09 12:50:00</td>
      <td>3.75</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541901</th>
      <td>581587</td>
      <td>22367</td>
      <td>CHILDRENS APRON SPACEBOY DESIGN</td>
      <td>8</td>
      <td>2011-12-09 12:50:00</td>
      <td>1.95</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541902</th>
      <td>581587</td>
      <td>22629</td>
      <td>SPACEBOY LUNCH BOX</td>
      <td>12</td>
      <td>2011-12-09 12:50:00</td>
      <td>1.95</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541903</th>
      <td>581587</td>
      <td>23256</td>
      <td>CHILDRENS CUTLERY SPACEBOY</td>
      <td>4</td>
      <td>2011-12-09 12:50:00</td>
      <td>4.15</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541904</th>
      <td>581587</td>
      <td>22613</td>
      <td>PACK OF 20 SPACEBOY NAPKINS</td>
      <td>12</td>
      <td>2011-12-09 12:50:00</td>
      <td>0.85</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541905</th>
      <td>581587</td>
      <td>22899</td>
      <td>CHILDREN'S APRON DOLLY GIRL</td>
      <td>6</td>
      <td>2011-12-09 12:50:00</td>
      <td>2.10</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541906</th>
      <td>581587</td>
      <td>23254</td>
      <td>CHILDRENS CUTLERY DOLLY GIRL</td>
      <td>4</td>
      <td>2011-12-09 12:50:00</td>
      <td>4.15</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541907</th>
      <td>581587</td>
      <td>23255</td>
      <td>CHILDRENS CUTLERY CIRCUS PARADE</td>
      <td>4</td>
      <td>2011-12-09 12:50:00</td>
      <td>4.15</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
    <tr>
      <th>541908</th>
      <td>581587</td>
      <td>22138</td>
      <td>BAKING SET 9 PIECE RETROSPOT</td>
      <td>3</td>
      <td>2011-12-09 12:50:00</td>
      <td>4.95</td>
      <td>12680.0</td>
      <td>France</td>
    </tr>
  </tbody>
</table>
</div>



The dataset has 541909 rows and 8 columns. Invoice Numbers are 536365 to 581587 and there are more than one items in one Invoice. Moreover, the StockCode is combining some string and numbers. So we want to see more rows rather than head and tail.


```python
# Set the desired range of rows to display
pd.set_option('display.max_rows', 500)

# View the selected range of rows
print(df[:500])
```

        InvoiceNo StockCode                          Description  Quantity   
    0      536365    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6  \
    1      536365     71053                  WHITE METAL LANTERN         6   
    2      536365    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    3      536365    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    4      536365    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    5      536365     22752         SET 7 BABUSHKA NESTING BOXES         2   
    6      536365     21730    GLASS STAR FROSTED T-LIGHT HOLDER         6   
    7      536366     22633               HAND WARMER UNION JACK         6   
    8      536366     22632            HAND WARMER RED POLKA DOT         6   
    9      536367     84879        ASSORTED COLOUR BIRD ORNAMENT        32   
    10     536367     22745           POPPY'S PLAYHOUSE BEDROOM          6   
    11     536367     22748            POPPY'S PLAYHOUSE KITCHEN         6   
    12     536367     22749    FELTCRAFT PRINCESS CHARLOTTE DOLL         8   
    13     536367     22310              IVORY KNITTED MUG COSY          6   
    14     536367     84969   BOX OF 6 ASSORTED COLOUR TEASPOONS         6   
    15     536367     22623        BOX OF VINTAGE JIGSAW BLOCKS          3   
    16     536367     22622       BOX OF VINTAGE ALPHABET BLOCKS         2   
    17     536367     21754             HOME BUILDING BLOCK WORD         3   
    18     536367     21755             LOVE BUILDING BLOCK WORD         3   
    19     536367     21777          RECIPE BOX WITH METAL HEART         4   
    20     536367     48187                  DOORMAT NEW ENGLAND         4   
    21     536368     22960             JAM MAKING SET WITH JARS         6   
    22     536368     22913          RED COAT RACK PARIS FASHION         3   
    23     536368     22912       YELLOW COAT RACK PARIS FASHION         3   
    24     536368     22914         BLUE COAT RACK PARIS FASHION         3   
    25     536369     21756             BATH BUILDING BLOCK WORD         3   
    26     536370     22728            ALARM CLOCK BAKELIKE PINK        24   
    27     536370     22727            ALARM CLOCK BAKELIKE RED         24   
    28     536370     22726           ALARM CLOCK BAKELIKE GREEN        12   
    29     536370     21724      PANDA AND BUNNIES STICKER SHEET        12   
    30     536370     21883                     STARS GIFT TAPE         24   
    31     536370     10002          INFLATABLE POLITICAL GLOBE         48   
    32     536370     21791   VINTAGE HEADS AND TAILS CARD GAME         24   
    33     536370     21035      SET/2 RED RETROSPOT TEA TOWELS         18   
    34     536370     22326  ROUND SNACK BOXES SET OF4 WOODLAND         24   
    35     536370     22629                  SPACEBOY LUNCH BOX         24   
    36     536370     22659              LUNCH BOX I LOVE LONDON        24   
    37     536370     22631             CIRCUS PARADE LUNCH BOX         24   
    38     536370     22661      CHARLOTTE BAG DOLLY GIRL DESIGN        20   
    39     536370     21731        RED TOADSTOOL LED NIGHT LIGHT        24   
    40     536370     22900      SET 2 TEA TOWELS I LOVE LONDON         24   
    41     536370     21913       VINTAGE SEASIDE JIGSAW PUZZLES        12   
    42     536370     22540           MINI JIGSAW CIRCUS PARADE         24   
    43     536370     22544                 MINI JIGSAW SPACEBOY        24   
    44     536370     22492              MINI PAINT SET VINTAGE         36   
    45     536370      POST                              POSTAGE         3   
    46     536371     22086      PAPER CHAIN KIT 50'S CHRISTMAS         80   
    47     536372     22632            HAND WARMER RED POLKA DOT         6   
    48     536372     22633               HAND WARMER UNION JACK         6   
    49     536373    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6   
    50     536373     71053                  WHITE METAL LANTERN         6   
    51     536373    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    52     536373     20679                EDWARDIAN PARASOL RED         6   
    53     536373     37370           RETRO COFFEE MUGS ASSORTED         6   
    54     536373     21871                  SAVE THE PLANET MUG         6   
    55     536373     21071       VINTAGE BILLBOARD DRINK ME MUG         6   
    56     536373     21068      VINTAGE BILLBOARD LOVE/HATE MUG         6   
    57     536373     82483   WOOD 2 DRAWER CABINET WHITE FINISH         2   
    58     536373     82486    WOOD S/3 CABINET ANT WHITE FINISH         4   
    59     536373     82482    WOODEN PICTURE FRAME WHITE FINISH         6   
    60     536373    82494L          WOODEN FRAME ANTIQUE WHITE          6   
    61     536373    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    62     536373    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    63     536373     22752         SET 7 BABUSHKA NESTING BOXES         2   
    64     536373     21730    GLASS STAR FROSTED T-LIGHT HOLDER         6   
    65     536374     21258           VICTORIAN SEWING BOX LARGE        32   
    66     536375    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6   
    67     536375     71053                  WHITE METAL LANTERN         6   
    68     536375    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    69     536375     20679                EDWARDIAN PARASOL RED         6   
    70     536375     37370           RETRO COFFEE MUGS ASSORTED         6   
    71     536375     21871                  SAVE THE PLANET MUG         6   
    72     536375     21071       VINTAGE BILLBOARD DRINK ME MUG         6   
    73     536375     21068      VINTAGE BILLBOARD LOVE/HATE MUG         6   
    74     536375     82483   WOOD 2 DRAWER CABINET WHITE FINISH         2   
    75     536375     82486    WOOD S/3 CABINET ANT WHITE FINISH         4   
    76     536375     82482    WOODEN PICTURE FRAME WHITE FINISH         6   
    77     536375    82494L          WOODEN FRAME ANTIQUE WHITE          6   
    78     536375    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    79     536375    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    80     536375     22752         SET 7 BABUSHKA NESTING BOXES         2   
    81     536375     21730    GLASS STAR FROSTED T-LIGHT HOLDER         6   
    82     536376     22114    HOT WATER BOTTLE TEA AND SYMPATHY        48   
    83     536376     21733     RED HANGING HEART T-LIGHT HOLDER        64   
    84     536377     22632            HAND WARMER RED POLKA DOT         6   
    85     536377     22633               HAND WARMER UNION JACK         6   
    86     536378     22386              JUMBO BAG PINK POLKADOT        10   
    87     536378    85099C       JUMBO  BAG BAROQUE BLACK WHITE        10   
    88     536378     21033      JUMBO BAG CHARLIE AND LOLA TOYS        10   
    89     536378     20723             STRAWBERRY CHARLOTTE BAG        10   
    90     536378    84997B    RED 3 PIECE RETROSPOT CUTLERY SET        12   
    91     536378    84997C    BLUE 3 PIECE POLKADOT CUTLERY SET         6   
    92     536378     21094        SET/6 RED SPOTTY PAPER PLATES        12   
    93     536378     20725              LUNCH BAG RED RETROSPOT        10   
    94     536378     21559    STRAWBERRY LUNCH BOX WITH CUTLERY         6   
    95     536378     22352    LUNCH BOX WITH CUTLERY RETROSPOT          6   
    96     536378     21212      PACK OF 72 RETROSPOT CAKE CASES       120   
    97     536378     21975       PACK OF 60 DINOSAUR CAKE CASES        24   
    98     536378     21977   PACK OF 60 PINK PAISLEY CAKE CASES        24   
    99     536378     84991          60 TEATIME FAIRY CAKE CASES        24   
    100    536378    84519A      TOMATO CHARLIE+LOLA COASTER SET         6   
    101    536378    85183B  CHARLIE & LOLA WASTEPAPER BIN FLORA        48   
    102    536378    85071B   RED CHARLIE+LOLA PERSONAL DOORSIGN        96   
    103    536378     21931               JUMBO STORAGE BAG SUKI        10   
    104    536378     21929       JUMBO BAG PINK VINTAGE PAISLEY        10   
    105    536380     22961               JAM MAKING SET PRINTED        24   
    106    536381     22139     RETROSPOT TEA SET CERAMIC 11 PC         23   
    107    536381     84854                  GIRLY PINK TOOL SET         5   
    108    536381     22411    JUMBO SHOPPER VINTAGE RED PAISLEY        10   
    109    536381     82567            AIRLINE LOUNGE,METAL SIGN         2   
    110    536381     21672   WHITE SPOT RED CERAMIC DRAWER KNOB         6   
    111    536381     22774    RED DRAWER KNOB ACRYLIC EDWARDIAN        24   
    112    536381     22771  CLEAR DRAWER KNOB ACRYLIC EDWARDIAN        24   
    113    536381     71270                      PHOTO CLIP LINE         1   
    114    536381     22262                FELT EGG COSY CHICKEN         1   
    115    536381     22637                PIGGY BANK RETROSPOT          1   
    116    536381     21934                   SKULL SHOULDER BAG        10   
    117    536381     21169      YOU'RE CONFUSING ME METAL SIGN          3   
    118    536381     21166           COOK WITH WINE METAL SIGN          1   
    119    536381     21175          GIN + TONIC DIET METAL SIGN         2   
    120    536381    37444A      YELLOW BREAKFAST CUP AND SAUCER         1   
    121    536381    37444C       PINK BREAKFAST CUP AND SAUCER          1   
    122    536381     22086      PAPER CHAIN KIT 50'S CHRISTMAS          4   
    123    536381     22083            PAPER CHAIN KIT RETROSPOT         1   
    124    536381    84971S            SMALL HEART FLOWERS HOOK          6   
    125    536381     71270                      PHOTO CLIP LINE         3   
    126    536381     47580                TEA TIME DES TEA COSY         2   
    127    536381     22261          FELT EGG COSY WHITE RABBIT          1   
    128    536381     84832     ZINC WILLIE WINKIE  CANDLE STICK         1   
    129    536381     22644       CERAMIC CHERRY CAKE MONEY BANK         1   
    130    536381     21533             RETROSPOT LARGE MILK JUG         1   
    131    536381     21557               SET OF 6 FUNKY BEAKERS         2   
    132    536381   15056BL              EDWARDIAN PARASOL BLACK         2   
    133    536381    15056N            EDWARDIAN PARASOL NATURAL         2   
    134    536381     22646   CERAMIC STRAWBERRY CAKE MONEY BANK         4   
    135    536381     22176                    BLUE OWL SOFT TOY         1   
    136    536381     22438    BALLOON ART MAKE YOUR OWN FLOWERS         1   
    137    536381     21731        RED TOADSTOOL LED NIGHT LIGHT         2   
    138    536381     22778                   GLASS CLOCHE SMALL         3   
    139    536381     22719         GUMBALL MONOCHROME COAT RACK        36   
    140    536381     21523   DOORMAT FANCY FONT HOME SWEET HOME        10   
    141   C536379         D                             Discount        -1   
    142    536382     10002          INFLATABLE POLITICAL GLOBE         12   
    143    536382     21912             VINTAGE SNAKES & LADDERS         8   
    144    536382     21832                 CHOCOLATE CALCULATOR        12   
    145    536382     22411    JUMBO SHOPPER VINTAGE RED PAISLEY        10   
    146    536382     22379             RECYCLING BAG RETROSPOT         10   
    147    536382     22381               TOY TIDY PINK POLKADOT        50   
    148    536382     22798     ANTIQUE GLASS DRESSING TABLE POT         8   
    149    536382     22726           ALARM CLOCK BAKELIKE GREEN         4   
    150    536382     22926       IVORY GIANT GARDEN THERMOMETER        12   
    151    536382     22839      3 TIER CAKE TIN GREEN AND CREAM         2   
    152    536382     22838        3 TIER CAKE TIN RED AND CREAM         2   
    153    536382     22783     SET 3 WICKER OVAL BASKETS W LIDS         4   
    154   C536383    35004C      SET OF 3 COLOURED  FLYING DUCKS        -1   
    155    536384     82484    WOOD BLACK BOARD ANT WHITE FINISH         3   
    156    536384     84755  COLOUR GLASS T-LIGHT HOLDER HANGING        48   
    157    536384     22464          HANGING METAL HEART LANTERN        12   
    158    536384     21324         HANGING MEDINA LANTERN SMALL         6   
    159    536384     22457      NATURAL SLATE HEART CHALKBOARD         12   
    160    536384     22469                HEART OF WICKER SMALL        40   
    161    536384     22470                HEART OF WICKER LARGE        40   
    162    536384     22224               WHITE LOVEBIRD LANTERN         6   
    163    536384     21340  CLASSIC METAL BIRDCAGE PLANT HOLDER         2   
    164    536384     22189              CREAM HEART CARD HOLDER         4   
    165    536384     22427              ENAMEL FLOWER JUG CREAM         3   
    166    536384     22428             ENAMEL FIRE BUCKET CREAM         6   
    167    536384     22424               ENAMEL BREAD BIN CREAM         8   
    168    536385     22783     SET 3 WICKER OVAL BASKETS W LIDS         1   
    169    536385     22961               JAM MAKING SET PRINTED        12   
    170    536385     22960             JAM MAKING SET WITH JARS         6   
    171    536385     22663          JUMBO BAG DOLLY GIRL DESIGN        10   
    172    536385    85049A        TRADITIONAL CHRISTMAS RIBBONS        12   
    173    536385     22168        ORGANISER WOOD ANTIQUE WHITE          2   
    174    536385     22662          LUNCH BAG DOLLY GIRL DESIGN        10   
    175    536386     84880                WHITE WIRE EGG HOLDER        36   
    176    536386    85099C       JUMBO  BAG BAROQUE BLACK WHITE       100   
    177    536386    85099B              JUMBO BAG RED RETROSPOT       100   
    178    536387     79321                        CHILLI LIGHTS       192   
    179    536387     22780       LIGHT GARLAND BUTTERFILES PINK       192   
    180    536387     22779           WOODEN OWLS LIGHT GARLAND        192   
    181    536387     22466        FAIRY TALE COTTAGE NIGHTLIGHT       432   
    182    536387     21731        RED TOADSTOOL LED NIGHT LIGHT       432   
    183    536388     21754             HOME BUILDING BLOCK WORD         3   
    184    536388     21755             LOVE BUILDING BLOCK WORD         3   
    185    536388     21523   DOORMAT FANCY FONT HOME SWEET HOME         2   
    186    536388     21363              HOME SMALL WOOD LETTERS         3   
    187    536388     21411          GINGHAM HEART  DOORSTOP RED         3   
    188    536388     22318        FIVE HEART HANGING DECORATION         6   
    189    536388     22464          HANGING METAL HEART LANTERN        12   
    190    536388     22915        ASSORTED BOTTLE TOP  MAGNETS         12   
    191    536388     22922     FRIDGE MAGNETS US DINER ASSORTED        12   
    192    536388     22969         HOMEMADE JAM SCENTED CANDLES        12   
    193    536388     22923  FRIDGE MAGNETS LES ENFANTS ASSORTED        12   
    194    536388     21115                ROSE CARAVAN DOORSTOP         4   
    195    536388     22469                HEART OF WICKER SMALL        12   
    196    536388     22242        5 HOOK HANGER MAGIC TOADSTOOL        12   
    197    536389     22941         CHRISTMAS LIGHTS 10 REINDEER         6   
    198    536389     21622     VINTAGE UNION JACK CUSHION COVER         8   
    199    536389     21791   VINTAGE HEADS AND TAILS CARD GAME         12   
    200    536389    35004C      SET OF 3 COLOURED  FLYING DUCKS         6   
    201    536389    35004G           SET OF 3 GOLD FLYING DUCKS         4   
    202    536389    85014B               RED RETROSPOT UMBRELLA         6   
    203    536389    85014A         BLACK/BLUE POLKADOT UMBRELLA         3   
    204    536389     22193                 RED DINER WALL CLOCK         2   
    205    536389     22726           ALARM CLOCK BAKELIKE GREEN         4   
    206    536389     22727            ALARM CLOCK BAKELIKE RED          4   
    207    536389     22192                BLUE DINER WALL CLOCK         2   
    208    536389     22191               IVORY DINER WALL CLOCK         2   
    209    536389     22195         LARGE HEART MEASURING SPOONS        24   
    210    536389     22196         SMALL HEART MEASURING SPOONS        24   
    211    536390     22941         CHRISTMAS LIGHTS 10 REINDEER         2   
    212    536390     22960             JAM MAKING SET WITH JARS        12   
    213    536390     22961               JAM MAKING SET PRINTED        12   
    214    536390     22962                JAM JAR WITH PINK LID        48   
    215    536390     22963               JAM JAR WITH GREEN LID        48   
    216    536390     22968           ROSE COTTAGE KEEPSAKE BOX          8   
    217    536390    84970S    HANGING HEART ZINC T-LIGHT HOLDER       144   
    218    536390     22910    PAPER CHAIN KIT VINTAGE CHRISTMAS        40   
    219    536390     20668      DISCO BALL CHRISTMAS DECORATION       288   
    220    536390    85123A   WHITE HANGING HEART T-LIGHT HOLDER        64   
    221    536390     22197                 SMALL POPCORN HOLDER       100   
    222    536390     22198                LARGE POPCORN HOLDER         50   
    223    536390     21533             RETROSPOT LARGE MILK JUG        12   
    224    536390     21080  SET/20 RED RETROSPOT PAPER NAPKINS         96   
    225    536390     21094        SET/6 RED SPOTTY PAPER PLATES        96   
    226    536390     21086          SET/6 RED SPOTTY PAPER CUPS        48   
    227    536390     21786                   POLKADOT RAIN HAT        144   
    228    536390     22654                   DELUXE SEWING KIT         40   
    229    536390     21485     RETROSPOT HEART HOT WATER BOTTLE        24   
    230    536390    84029G  KNITTED UNION FLAG HOT WATER BOTTLE        24   
    231    536390    84030E        ENGLISH ROSE HOT WATER BOTTLE        24   
    232    536390     22174                           PHOTO CUBE        48   
    233    536390     22969         HOMEMADE JAM SCENTED CANDLES        96   
    234    536390    85099B              JUMBO BAG RED RETROSPOT       100   
    235   C536391     22556       PLASTERS IN TIN CIRCUS PARADE        -12   
    236   C536391     21984     PACK OF 12 PINK PAISLEY TISSUES        -24   
    237   C536391     21983     PACK OF 12 BLUE PAISLEY TISSUES        -24   
    238   C536391     21980    PACK OF 12 RED RETROSPOT TISSUES        -24   
    239   C536391     21484          CHICK GREY HOT WATER BOTTLE       -12   
    240   C536391     22557     PLASTERS IN TIN VINTAGE PAISLEY        -12   
    241   C536391     22553               PLASTERS IN TIN SKULLS       -24   
    242    536392     22150             3 STRIPEY MICE FELTCRAFT         6   
    243    536392     22619            SET OF 6 SOLDIER SKITTLES         4   
    244    536392     21891     TRADITIONAL WOODEN SKIPPING ROPE        12   
    245    536392     21889               WOODEN BOX OF DOMINOES        12   
    246    536392     22827   RUSTIC  SEVENTEEN DRAWER SIDEBOARD         1   
    247    536392     22127        PARTY CONES CARNIVAL ASSORTED        12   
    248    536392     22128           PARTY CONES CANDY ASSORTED        12   
    249    536392     22502           PICNIC BASKET WICKER SMALL         4   
    250    536392     84879        ASSORTED COLOUR BIRD ORNAMENT        16   
    251    536392     22338        STAR DECORATION PAINTED ZINC         24   
    252    536393     22180                       RETROSPOT LAMP         8   
    253    536394     21506           FANCY FONT BIRTHDAY CARD,         24   
    254    536394     22633               HAND WARMER UNION JACK        96   
    255    536394     22866        HAND WARMER SCOTTY DOG DESIGN        96   
    256    536394     22865               HAND WARMER OWL DESIGN        96   
    257    536394     22632            HAND WARMER RED RETROSPOT        96   
    258    536394     21485     RETROSPOT HEART HOT WATER BOTTLE        12   
    259    536394     22349         DOG BOWL CHASING BALL DESIGN        12   
    260    536394     22558      CLOTHES PEGS RETROSPOT PACK 24         48   
    261    536394     85152      HAND OVER THE CHOCOLATE   SIGN         12   
    262    536394    85123A   WHITE HANGING HEART T-LIGHT HOLDER        32   
    263    536394     22652                    TRAVEL SEWING KIT        20   
    264    536395     22188              BLACK HEART CARD HOLDER         8   
    265    536395     84879        ASSORTED COLOUR BIRD ORNAMENT        32   
    266    536395     21977   PACK OF 60 PINK PAISLEY CAKE CASES        24   
    267    536395     84991          60 TEATIME FAIRY CAKE CASES        24   
    268    536395     21212      PACK OF 72 RETROSPOT CAKE CASES        24   
    269    536395     21484          CHICK GREY HOT WATER BOTTLE         8   
    270    536395     21314        SMALL GLASS HEART TRINKET POT         8   
    271    536395     22730           ALARM CLOCK BAKELIKE IVORY         4   
    272    536395     22727            ALARM CLOCK BAKELIKE RED          8   
    273    536395     22729          ALARM CLOCK BAKELIKE ORANGE         8   
    274    536395     22726           ALARM CLOCK BAKELIKE GREEN         8   
    275    536395     22114    HOT WATER BOTTLE TEA AND SYMPATHY         8   
    276    536395     22867              HAND WARMER BIRD DESIGN        48   
    277    536395     22866        HAND WARMER SCOTTY DOG DESIGN        48   
    278    536396    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6   
    279    536396     71053                  WHITE METAL LANTERN         6   
    280    536396    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    281    536396   15056BL              EDWARDIAN PARASOL BLACK         6   
    282    536396     20679                EDWARDIAN PARASOL RED         6   
    283    536396     37370           RETRO COFFEE MUGS ASSORTED         6   
    284    536396     21871                  SAVE THE PLANET MUG         6   
    285    536396     21071       VINTAGE BILLBOARD DRINK ME MUG         6   
    286    536396     21068      VINTAGE BILLBOARD LOVE/HATE MUG         6   
    287    536396     82483   WOOD 2 DRAWER CABINET WHITE FINISH         2   
    288    536396     82486    WOOD S/3 CABINET ANT WHITE FINISH         4   
    289    536396     82482    WOODEN PICTURE FRAME WHITE FINISH         6   
    290    536396    82494L          WOODEN FRAME ANTIQUE WHITE         12   
    291    536396    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    292    536396    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    293    536396     22752         SET 7 BABUSHKA NESTING BOXES         2   
    294    536396     22803             IVORY EMBROIDERED QUILT          2   
    295    536396     21730    GLASS STAR FROSTED T-LIGHT HOLDER         6   
    296    536397    35004B          SET OF 3 BLACK FLYING DUCKS        12   
    297    536397    35004C      SET OF 3 COLOURED  FLYING DUCKS        48   
    298    536398     21980    PACK OF 12 RED RETROSPOT TISSUES         24   
    299    536398     21844                    RED RETROSPOT MUG         6   
    300    536398     22468         BABUSHKA LIGHTS STRING OF 10         4   
    301    536398     22637                PIGGY BANK RETROSPOT          8   
    302    536398     22752         SET 7 BABUSHKA NESTING BOXES         6   
    303    536398     48185                   DOORMAT FAIRY CAKE         2   
    304    536398     22632            HAND WARMER RED RETROSPOT        12   
    305    536398     22866        HAND WARMER SCOTTY DOG DESIGN        12   
    306    536398     22865               HAND WARMER OWL DESIGN        12   
    307    536398     21232       STRAWBERRY CERAMIC TRINKET BOX        12   
    308    536398     22064           PINK DOUGHNUT TRINKET POT         12   
    309    536398     22449             SILK PURSE BABUSHKA PINK         6   
    310    536398     22114    HOT WATER BOTTLE TEA AND SYMPATHY         4   
    311    536398     22835      HOT WATER BOTTLE I AM SO POORLY         8   
    312    536398     22112           CHOCOLATE HOT WATER BOTTLE         9   
    313    536398     21479        WHITE SKULL HOT WATER BOTTLE          4   
    314    536398     22111         SCOTTIE DOG HOT WATER BOTTLE         9   
    315    536399     22632            HAND WARMER RED POLKA DOT         6   
    316    536399     22633               HAND WARMER UNION JACK         6   
    317    536400     22969         HOMEMADE JAM SCENTED CANDLES        12   
    318    536401     22110          BIRD HOUSE HOT WATER BOTTLE         1   
    319    536401     22098            BOUDOIR SQUARE TISSUE BOX         1   
    320    536401     22100             SKULLS SQUARE TISSUE BOX         2   
    321    536401     22766                  PHOTO FRAME CORNICE         1   
    322    536401     22451              SILK PURSE BABUSHKA RED         1   
    323    536401     22549                     PICTURE DOMINOES         1   
    324    536401     84744           S/6 SEW ON CROCHET FLOWERS         1   
    325    536401    85049E            SCANDINAVIAN REDS RIBBONS         2   
    326    536401     21328               BALLOONS  WRITING SET          1   
    327    536401     22961               JAM MAKING SET PRINTED         4   
    328    536401    17091A              LAVENDER INCENSE IN TIN         1   
    329    536401     22473       TV DINNER TRAY VINTAGE PAISLEY         1   
    330    536401    84509A      SET OF 4 ENGLISH ROSE PLACEMATS         2   
    331    536401    84510A       SET OF 4 ENGLISH ROSE COASTERS         2   
    332    536401     22767          TRIPLE PHOTO FRAME CORNICE          2   
    333    536401     22768           FAMILY PHOTO FRAME CORNICE         1   
    334    536401     21463                 MIRRORED DISCO BALL          1   
    335    536401     21464  DISCO BALL ROTATOR BATTERY OPERATED         1   
    336    536401     20820                SILVER LOOKING MIRROR         3   
    337    536401     85150        LADIES & GENTLEMEN METAL SIGN         1   
    338    536401     22117     METAL SIGN HER DINNER IS SERVED          1   
    339    536401     21169      YOU'RE CONFUSING ME METAL SIGN          2   
    340    536401     48129                      DOORMAT TOPIARY         1   
    341    536401     82580                  BATHROOM METAL SIGN         1   
    342    536401     82578                   KITCHEN METAL SIGN         1   
    343    536401     82581                    TOILET METAL SIGN         2   
    344    536401     22413      METAL SIGN TAKE IT OR LEAVE IT          4   
    345    536401     21907            I'M ON HOLIDAY METAL SIGN         2   
    346    536401     22441    GROW YOUR OWN BASIL IN ENAMEL MUG         1   
    347    536401     21122   SET/10 PINK POLKADOT PARTY CANDLES         1   
    348    536401     22851   SET 20 NAPKINS FAIRY CAKES DESIGN          1   
    349    536401     84991          60 TEATIME FAIRY CAKE CASES         3   
    350    536401     22810            SET OF 6 T-LIGHTS SNOWMEN         1   
    351    536401     22809              SET OF 6 T-LIGHTS SANTA         1   
    352    536401     22435       SET OF 9 HEART SHAPED BALLOONS         2   
    353    536401     20966                 SANDWICH BATH SPONGE         3   
    354    536401     20963                    APPLE BATH SPONGE         1   
    355    536401     20961              STRAWBERRY BATH SPONGE          1   
    356    536401     22068          BLACK PIRATE TREASURE CHEST         2   
    357    536401     21743           STAR PORTABLE TABLE LIGHT          2   
    358    536401     21744      SNOWFLAKE PORTABLE TABLE LIGHT          2   
    359    536401    84709B            PINK OVAL JEWELLED MIRROR         1   
    360    536401     21592         RETROSPOT CIGAR BOX MATCHES          1   
    361    536401     21587         COSY HOUR GIANT TUBE MATCHES         2   
    362    536401     20992           JAZZ HEARTS PURSE NOTEBOOK         9   
    363    536401     22662          LUNCH BAG DOLLY GIRL DESIGN         1   
    364    536401    85123A   WHITE HANGING HEART T-LIGHT HOLDER         4   
    365    536401     22804      CANDLEHOLDER PINK HANGING HEART         3   
    366    536401     82483   WOOD 2 DRAWER CABINET WHITE FINISH         1   
    367    536401     20749           ASSORTED COLOUR MINI CASES         1   
    368    536401     20725              LUNCH BAG RED RETROSPOT         1   
    369    536401     22382           LUNCH BAG SPACEBOY DESIGN          2   
    370    536401     20726                   LUNCH BAG WOODLAND         1   
    371    536401     22384              LUNCH BAG PINK POLKADOT         1   
    372    536401     22467                    GUMBALL COAT RACK         5   
    373    536401    84625C  BLUE NEW BAROQUE CANDLESTICK CANDLE         3   
    374    536401    84625A   PINK NEW BAROQUECANDLESTICK CANDLE         3   
    375    536401     21108   FAIRY CAKE FLANNEL ASSORTED COLOUR         9   
    376    536401     22848           BREAD BIN DINER STYLE PINK         1   
    377    536401     21033      JUMBO BAG CHARLIE AND LOLA TOYS         4   
    378    536401    47570B                 TEA TIME TABLE CLOTH         1   
    379    536401    84030E        ENGLISH ROSE HOT WATER BOTTLE         1   
    380    536401     22428             ENAMEL FIRE BUCKET CREAM         2   
    381    536401     22502           PICNIC BASKET WICKER SMALL         2   
    382    536402     22086      PAPER CHAIN KIT 50'S CHRISTMAS         40   
    383    536402     22910    PAPER CHAIN KIT VINTAGE CHRISTMAS        40   
    384    536402     22837           HOT WATER BOTTLE BABUSHKA         36   
    385    536403     22867              HAND WARMER BIRD DESIGN        96   
    386    536403      POST                              POSTAGE         1   
    387    536404     22297            HEART IVORY TRELLIS SMALL        24   
    388    536404     22771  CLEAR DRAWER KNOB ACRYLIC EDWARDIAN        12   
    389    536404     22772   PINK DRAWER KNOB ACRYLIC EDWARDIAN        12   
    390    536404     22773  GREEN DRAWER KNOB ACRYLIC EDWARDIAN        12   
    391    536404     22805   BLUE DRAWER KNOB ACRYLIC EDWARDIAN        12   
    392    536404     22469                HEART OF WICKER SMALL        12   
    393    536404     22197                 SMALL POPCORN HOLDER        36   
    394    536404     21125   SET 6 FOOTBALL CELEBRATION CANDLES        12   
    395    536404     21126   SET OF 6 GIRLS CELEBRATION CANDLES        12   
    396    536404    85049C              ROMANTIC PINKS RIBBONS         12   
    397    536404    85049D                BRIGHT BLUES RIBBONS         12   
    398    536404    85049E            SCANDINAVIAN REDS RIBBONS        12   
    399    536404    85049G               CHOCOLATE BOX RIBBONS         12   
    400    536404     21061               PARTY INVITES FOOTBALL        12   
    401    536404     21063            PARTY INVITES JAZZ HEARTS        12   
    402    536404     21062               PARTY INVITES SPACEMAN        12   
    403    536404     84380    SET OF 3 BUTTERFLY COOKIE CUTTERS        12   
    404    536404     84378        SET OF 3 HEART COOKIE CUTTERS        12   
    405    536404     22964   3 PIECE SPACEBOY COOKIE CUTTER SET        12   
    406    536404     21213          PACK OF 72 SKULL CAKE CASES        24   
    407    536404     22417       PACK OF 60 SPACEBOY CAKE CASES        24   
    408    536404     21212      PACK OF 72 RETROSPOT CAKE CASES        24   
    409    536404     84992       72 SWEETHEART FAIRY CAKE CASES        24   
    410    536404     21975       PACK OF 60 DINOSAUR CAKE CASES        24   
    411    536404     22383              LUNCH BAG SUKI  DESIGN         10   
    412    536404     20728                  LUNCH BAG CARS BLUE        10   
    413    536404     20727              LUNCH BAG  BLACK SKULL.        10   
    414    536404     22296            HEART IVORY TRELLIS LARGE        24   
    415    536405     20914  SET/5 RED RETROSPOT LID GLASS BOWLS       128   
    416    536406    85123A   WHITE HANGING HEART T-LIGHT HOLDER         8   
    417    536406     71053                  WHITE METAL LANTERN         8   
    418    536406    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    419    536406     20679                EDWARDIAN PARASOL RED         6   
    420    536406     37370           RETRO COFFEE MUGS ASSORTED         6   
    421    536406     21871                  SAVE THE PLANET MUG         6   
    422    536406     21071       VINTAGE BILLBOARD DRINK ME MUG         6   
    423    536406     21068      VINTAGE BILLBOARD LOVE/HATE MUG         6   
    424    536406     82483   WOOD 2 DRAWER CABINET WHITE FINISH         4   
    425    536406     82486    WOOD S/3 CABINET ANT WHITE FINISH         4   
    426    536406     82482    WOODEN PICTURE FRAME WHITE FINISH         6   
    427    536406    82494L          WOODEN FRAME ANTIQUE WHITE          6   
    428    536406    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    429    536406    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    430    536406     22752         SET 7 BABUSHKA NESTING BOXES         2   
    431    536406     22803             IVORY EMBROIDERED QUILT          2   
    432    536406     21730    GLASS STAR FROSTED T-LIGHT HOLDER         6   
    433    536407     22632            HAND WARMER RED POLKA DOT         6   
    434    536407     22633               HAND WARMER UNION JACK         6   
    435    536408     22537         MAGIC DRAWING SLATE DINOSAUR        24   
    436    536408     22533     MAGIC DRAWING SLATE BAKE A CAKE         24   
    437    536408     20982          12 PENCILS TALL TUBE SKULLS        12   
    438    536408     21832                 CHOCOLATE CALCULATOR        12   
    439    536408     21915               RED  HARMONICA IN BOX         12   
    440    536408     21914               BLUE HARMONICA IN BOX         12   
    441    536408     21544      SKULLS  WATER TRANSFER TATTOOS         12   
    442    536408     22813         PACK 3 BOXES BIRD PANNETONE         12   
    443    536408     22114    HOT WATER BOTTLE TEA AND SYMPATHY         4   
    444    536408    84029E       RED WOOLLY HOTTIE WHITE HEART.         4   
    445    536408     21479        WHITE SKULL HOT WATER BOTTLE          4   
    446    536408     22964   3 PIECE SPACEBOY COOKIE CUTTER SET         6   
    447    536408     84375        SET OF 20 KIDS COOKIE CUTTERS        12   
    448    536408     22418               10 COLOUR SPACEBOY PEN        24   
    449    536408     22178      VICTORIAN GLASS HANGING T-LIGHT        12   
    450    536408    84970L     SINGLE HEART ZINC T-LIGHT HOLDER        12   
    451    536408     21733     RED HANGING HEART T-LIGHT HOLDER         6   
    452    536408     22465           HANGING METAL STAR LANTERN        12   
    453    536408     84949        SILVER HANGING T-LIGHT HOLDER         6   
    454    536408     20685                DOORMAT RED RETROSPOT         2   
    455    536408     48194                       DOORMAT HEARTS         2   
    456    536408     22488   NATURAL SLATE RECTANGLE CHALKBOARD        12   
    457    536408     22219   LOVEBIRD HANGING DECORATION WHITE         12   
    458    536408     84879        ASSORTED COLOUR BIRD ORNAMENT         8   
    459    536408     21754             HOME BUILDING BLOCK WORD         3   
    460    536408     21755             LOVE BUILDING BLOCK WORD         3   
    461    536408     22766                  PHOTO FRAME CORNICE         8   
    462    536408     22610             PENS ASSORTED FUNNY FACE        36   
    463    536408     22716                   CARD CIRCUS PARADE        12   
    464    536408     22706                       WRAP COWBOYS          25   
    465    536408     22371         AIRLINE BAG VINTAGE TOKYO 78         4   
    466    536408    85014B               RED RETROSPOT UMBRELLA         3   
    467    536408    85014A         BLACK/BLUE POLKADOT UMBRELLA         3   
    468    536408    84997B    RED 3 PIECE RETROSPOT CUTLERY SET         6   
    469    536408     21212      PACK OF 72 RETROSPOT CAKE CASES        24   
    470    536408     21210   SET OF 72 RETROSPOT PAPER  DOILIES        12   
    471    536408     22914         BLUE COAT RACK PARIS FASHION         3   
    472    536408     22553               PLASTERS IN TIN SKULLS        12   
    473    536408     16237                 SLEEPING CAT ERASERS        30   
    474    536408     22714                 CARD BIRTHDAY COWBOY        12   
    475    536408     22812     PACK 3 BOXES CHRISTMAS PANNETONE        12   
    476    536408     84347  ROTATING SILVER ANGELS T-LIGHT HLDR         6   
    477    536408     21587         COSY HOUR GIANT TUBE MATCHES        12   
    478    536408     22736          RIBBON REEL MAKING SNOWMEN         10   
    479    536408     22492              MINI PAINT SET VINTAGE         36   
    480    536408     22620          4 TRADITIONAL SPINNING TOPS        12   
    481    536408     22619            SET OF 6 SOLDIER SKITTLES         4   
    482    536408     21705              BAG 500g SWIRLY MARBLES        12   
    483    536409    90199C      5 STRAND GLASS NECKLACE CRYSTAL         3   
    484    536409     21479        WHITE SKULL HOT WATER BOTTLE          1   
    485    536409     22111         SCOTTIE DOG HOT WATER BOTTLE         1   
    486    536409     22785  SQUARECUSHION COVER PINK UNION FLAG         1   
    487    536409     22975           SPACEBOY CHILDRENS EGG CUP         1   
    488    536409     22972              CHILDREN'S SPACEBOY MUG         1   
    489    536409     22866        HAND WARMER SCOTTY DOG DESIGN         1   
    490    536409     22568                FELTCRAFT CUSHION OWL         1   
    491    536409     85116      BLACK CANDELABRA T-LIGHT HOLDER         1   
    492    536409     22664           TOY TIDY DOLLY GIRL DESIGN         1   
    493    536409     21609  SET 12 LAVENDER  BOTANICAL T-LIGHTS         1   
    494    536409     21866          UNION JACK FLAG LUGGAGE TAG         1   
    495    536409     20669                RED HEART LUGGAGE TAG         1   
    496    536409    90129F           RED GLASS TASSLE BAG CHARM         1   
    497    536409    90210B         CLEAR ACRYLIC FACETED BANGLE         1   
    498    536409    90199C      5 STRAND GLASS NECKLACE CRYSTAL         1   
    499    536409     21955    DOORMAT UNION JACK GUNS AND ROSES         1   
    
                InvoiceDate  UnitPrice  CustomerID         Country  
    0   2010-12-01 08:26:00       2.55     17850.0  United Kingdom  
    1   2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    2   2010-12-01 08:26:00       2.75     17850.0  United Kingdom  
    3   2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    4   2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    5   2010-12-01 08:26:00       7.65     17850.0  United Kingdom  
    6   2010-12-01 08:26:00       4.25     17850.0  United Kingdom  
    7   2010-12-01 08:28:00       1.85     17850.0  United Kingdom  
    8   2010-12-01 08:28:00       1.85     17850.0  United Kingdom  
    9   2010-12-01 08:34:00       1.69     13047.0  United Kingdom  
    10  2010-12-01 08:34:00       2.10     13047.0  United Kingdom  
    11  2010-12-01 08:34:00       2.10     13047.0  United Kingdom  
    12  2010-12-01 08:34:00       3.75     13047.0  United Kingdom  
    13  2010-12-01 08:34:00       1.65     13047.0  United Kingdom  
    14  2010-12-01 08:34:00       4.25     13047.0  United Kingdom  
    15  2010-12-01 08:34:00       4.95     13047.0  United Kingdom  
    16  2010-12-01 08:34:00       9.95     13047.0  United Kingdom  
    17  2010-12-01 08:34:00       5.95     13047.0  United Kingdom  
    18  2010-12-01 08:34:00       5.95     13047.0  United Kingdom  
    19  2010-12-01 08:34:00       7.95     13047.0  United Kingdom  
    20  2010-12-01 08:34:00       7.95     13047.0  United Kingdom  
    21  2010-12-01 08:34:00       4.25     13047.0  United Kingdom  
    22  2010-12-01 08:34:00       4.95     13047.0  United Kingdom  
    23  2010-12-01 08:34:00       4.95     13047.0  United Kingdom  
    24  2010-12-01 08:34:00       4.95     13047.0  United Kingdom  
    25  2010-12-01 08:35:00       5.95     13047.0  United Kingdom  
    26  2010-12-01 08:45:00       3.75     12583.0          France  
    27  2010-12-01 08:45:00       3.75     12583.0          France  
    28  2010-12-01 08:45:00       3.75     12583.0          France  
    29  2010-12-01 08:45:00       0.85     12583.0          France  
    30  2010-12-01 08:45:00       0.65     12583.0          France  
    31  2010-12-01 08:45:00       0.85     12583.0          France  
    32  2010-12-01 08:45:00       1.25     12583.0          France  
    33  2010-12-01 08:45:00       2.95     12583.0          France  
    34  2010-12-01 08:45:00       2.95     12583.0          France  
    35  2010-12-01 08:45:00       1.95     12583.0          France  
    36  2010-12-01 08:45:00       1.95     12583.0          France  
    37  2010-12-01 08:45:00       1.95     12583.0          France  
    38  2010-12-01 08:45:00       0.85     12583.0          France  
    39  2010-12-01 08:45:00       1.65     12583.0          France  
    40  2010-12-01 08:45:00       2.95     12583.0          France  
    41  2010-12-01 08:45:00       3.75     12583.0          France  
    42  2010-12-01 08:45:00       0.42     12583.0          France  
    43  2010-12-01 08:45:00       0.42     12583.0          France  
    44  2010-12-01 08:45:00       0.65     12583.0          France  
    45  2010-12-01 08:45:00      18.00     12583.0          France  
    46  2010-12-01 09:00:00       2.55     13748.0  United Kingdom  
    47  2010-12-01 09:01:00       1.85     17850.0  United Kingdom  
    48  2010-12-01 09:01:00       1.85     17850.0  United Kingdom  
    49  2010-12-01 09:02:00       2.55     17850.0  United Kingdom  
    50  2010-12-01 09:02:00       3.39     17850.0  United Kingdom  
    51  2010-12-01 09:02:00       2.75     17850.0  United Kingdom  
    52  2010-12-01 09:02:00       4.95     17850.0  United Kingdom  
    53  2010-12-01 09:02:00       1.06     17850.0  United Kingdom  
    54  2010-12-01 09:02:00       1.06     17850.0  United Kingdom  
    55  2010-12-01 09:02:00       1.06     17850.0  United Kingdom  
    56  2010-12-01 09:02:00       1.06     17850.0  United Kingdom  
    57  2010-12-01 09:02:00       4.95     17850.0  United Kingdom  
    58  2010-12-01 09:02:00       6.95     17850.0  United Kingdom  
    59  2010-12-01 09:02:00       2.10     17850.0  United Kingdom  
    60  2010-12-01 09:02:00       2.55     17850.0  United Kingdom  
    61  2010-12-01 09:02:00       3.39     17850.0  United Kingdom  
    62  2010-12-01 09:02:00       3.39     17850.0  United Kingdom  
    63  2010-12-01 09:02:00       7.65     17850.0  United Kingdom  
    64  2010-12-01 09:02:00       4.25     17850.0  United Kingdom  
    65  2010-12-01 09:09:00      10.95     15100.0  United Kingdom  
    66  2010-12-01 09:32:00       2.55     17850.0  United Kingdom  
    67  2010-12-01 09:32:00       3.39     17850.0  United Kingdom  
    68  2010-12-01 09:32:00       2.75     17850.0  United Kingdom  
    69  2010-12-01 09:32:00       4.95     17850.0  United Kingdom  
    70  2010-12-01 09:32:00       1.06     17850.0  United Kingdom  
    71  2010-12-01 09:32:00       1.06     17850.0  United Kingdom  
    72  2010-12-01 09:32:00       1.06     17850.0  United Kingdom  
    73  2010-12-01 09:32:00       1.06     17850.0  United Kingdom  
    74  2010-12-01 09:32:00       4.95     17850.0  United Kingdom  
    75  2010-12-01 09:32:00       6.95     17850.0  United Kingdom  
    76  2010-12-01 09:32:00       2.10     17850.0  United Kingdom  
    77  2010-12-01 09:32:00       2.55     17850.0  United Kingdom  
    78  2010-12-01 09:32:00       3.39     17850.0  United Kingdom  
    79  2010-12-01 09:32:00       3.39     17850.0  United Kingdom  
    80  2010-12-01 09:32:00       7.65     17850.0  United Kingdom  
    81  2010-12-01 09:32:00       4.25     17850.0  United Kingdom  
    82  2010-12-01 09:32:00       3.45     15291.0  United Kingdom  
    83  2010-12-01 09:32:00       2.55     15291.0  United Kingdom  
    84  2010-12-01 09:34:00       1.85     17850.0  United Kingdom  
    85  2010-12-01 09:34:00       1.85     17850.0  United Kingdom  
    86  2010-12-01 09:37:00       1.95     14688.0  United Kingdom  
    87  2010-12-01 09:37:00       1.95     14688.0  United Kingdom  
    88  2010-12-01 09:37:00       2.95     14688.0  United Kingdom  
    89  2010-12-01 09:37:00       0.85     14688.0  United Kingdom  
    90  2010-12-01 09:37:00       3.75     14688.0  United Kingdom  
    91  2010-12-01 09:37:00       3.75     14688.0  United Kingdom  
    92  2010-12-01 09:37:00       0.85     14688.0  United Kingdom  
    93  2010-12-01 09:37:00       1.65     14688.0  United Kingdom  
    94  2010-12-01 09:37:00       2.55     14688.0  United Kingdom  
    95  2010-12-01 09:37:00       2.55     14688.0  United Kingdom  
    96  2010-12-01 09:37:00       0.42     14688.0  United Kingdom  
    97  2010-12-01 09:37:00       0.55     14688.0  United Kingdom  
    98  2010-12-01 09:37:00       0.55     14688.0  United Kingdom  
    99  2010-12-01 09:37:00       0.55     14688.0  United Kingdom  
    100 2010-12-01 09:37:00       2.95     14688.0  United Kingdom  
    101 2010-12-01 09:37:00       1.25     14688.0  United Kingdom  
    102 2010-12-01 09:37:00       0.38     14688.0  United Kingdom  
    103 2010-12-01 09:37:00       1.95     14688.0  United Kingdom  
    104 2010-12-01 09:37:00       1.95     14688.0  United Kingdom  
    105 2010-12-01 09:41:00       1.45     17809.0  United Kingdom  
    106 2010-12-01 09:41:00       4.25     15311.0  United Kingdom  
    107 2010-12-01 09:41:00       4.95     15311.0  United Kingdom  
    108 2010-12-01 09:41:00       1.95     15311.0  United Kingdom  
    109 2010-12-01 09:41:00       2.10     15311.0  United Kingdom  
    110 2010-12-01 09:41:00       1.25     15311.0  United Kingdom  
    111 2010-12-01 09:41:00       1.25     15311.0  United Kingdom  
    112 2010-12-01 09:41:00       1.25     15311.0  United Kingdom  
    113 2010-12-01 09:41:00       1.25     15311.0  United Kingdom  
    114 2010-12-01 09:41:00       0.85     15311.0  United Kingdom  
    115 2010-12-01 09:41:00       2.55     15311.0  United Kingdom  
    116 2010-12-01 09:41:00       1.65     15311.0  United Kingdom  
    117 2010-12-01 09:41:00       1.69     15311.0  United Kingdom  
    118 2010-12-01 09:41:00       1.95     15311.0  United Kingdom  
    119 2010-12-01 09:41:00       2.10     15311.0  United Kingdom  
    120 2010-12-01 09:41:00       2.95     15311.0  United Kingdom  
    121 2010-12-01 09:41:00       2.95     15311.0  United Kingdom  
    122 2010-12-01 09:41:00       2.95     15311.0  United Kingdom  
    123 2010-12-01 09:41:00       2.95     15311.0  United Kingdom  
    124 2010-12-01 09:41:00       0.85     15311.0  United Kingdom  
    125 2010-12-01 09:41:00       1.25     15311.0  United Kingdom  
    126 2010-12-01 09:41:00       2.55     15311.0  United Kingdom  
    127 2010-12-01 09:41:00       0.85     15311.0  United Kingdom  
    128 2010-12-01 09:41:00       0.85     15311.0  United Kingdom  
    129 2010-12-01 09:41:00       1.45     15311.0  United Kingdom  
    130 2010-12-01 09:41:00       4.95     15311.0  United Kingdom  
    131 2010-12-01 09:41:00       2.95     15311.0  United Kingdom  
    132 2010-12-01 09:41:00       5.95     15311.0  United Kingdom  
    133 2010-12-01 09:41:00       5.95     15311.0  United Kingdom  
    134 2010-12-01 09:41:00       1.45     15311.0  United Kingdom  
    135 2010-12-01 09:41:00       2.95     15311.0  United Kingdom  
    136 2010-12-01 09:41:00       1.95     15311.0  United Kingdom  
    137 2010-12-01 09:41:00       1.65     15311.0  United Kingdom  
    138 2010-12-01 09:41:00       3.95     15311.0  United Kingdom  
    139 2010-12-01 09:41:00       1.06     15311.0  United Kingdom  
    140 2010-12-01 09:41:00       6.75     15311.0  United Kingdom  
    141 2010-12-01 09:41:00      27.50     14527.0  United Kingdom  
    142 2010-12-01 09:45:00       0.85     16098.0  United Kingdom  
    143 2010-12-01 09:45:00       3.75     16098.0  United Kingdom  
    144 2010-12-01 09:45:00       1.65     16098.0  United Kingdom  
    145 2010-12-01 09:45:00       1.95     16098.0  United Kingdom  
    146 2010-12-01 09:45:00       2.10     16098.0  United Kingdom  
    147 2010-12-01 09:45:00       1.85     16098.0  United Kingdom  
    148 2010-12-01 09:45:00       2.95     16098.0  United Kingdom  
    149 2010-12-01 09:45:00       3.75     16098.0  United Kingdom  
    150 2010-12-01 09:45:00       5.95     16098.0  United Kingdom  
    151 2010-12-01 09:45:00      14.95     16098.0  United Kingdom  
    152 2010-12-01 09:45:00      14.95     16098.0  United Kingdom  
    153 2010-12-01 09:45:00      16.95     16098.0  United Kingdom  
    154 2010-12-01 09:49:00       4.65     15311.0  United Kingdom  
    155 2010-12-01 09:53:00       6.45     18074.0  United Kingdom  
    156 2010-12-01 09:53:00       0.65     18074.0  United Kingdom  
    157 2010-12-01 09:53:00       1.65     18074.0  United Kingdom  
    158 2010-12-01 09:53:00       2.95     18074.0  United Kingdom  
    159 2010-12-01 09:53:00       2.95     18074.0  United Kingdom  
    160 2010-12-01 09:53:00       1.45     18074.0  United Kingdom  
    161 2010-12-01 09:53:00       2.55     18074.0  United Kingdom  
    162 2010-12-01 09:53:00       2.95     18074.0  United Kingdom  
    163 2010-12-01 09:53:00      12.75     18074.0  United Kingdom  
    164 2010-12-01 09:53:00       3.95     18074.0  United Kingdom  
    165 2010-12-01 09:53:00       5.95     18074.0  United Kingdom  
    166 2010-12-01 09:53:00       6.95     18074.0  United Kingdom  
    167 2010-12-01 09:53:00      10.95     18074.0  United Kingdom  
    168 2010-12-01 09:56:00      19.95     17420.0  United Kingdom  
    169 2010-12-01 09:56:00       1.45     17420.0  United Kingdom  
    170 2010-12-01 09:56:00       4.25     17420.0  United Kingdom  
    171 2010-12-01 09:56:00       1.95     17420.0  United Kingdom  
    172 2010-12-01 09:56:00       1.25     17420.0  United Kingdom  
    173 2010-12-01 09:56:00       8.50     17420.0  United Kingdom  
    174 2010-12-01 09:56:00       1.65     17420.0  United Kingdom  
    175 2010-12-01 09:57:00       4.95     16029.0  United Kingdom  
    176 2010-12-01 09:57:00       1.65     16029.0  United Kingdom  
    177 2010-12-01 09:57:00       1.65     16029.0  United Kingdom  
    178 2010-12-01 09:58:00       3.82     16029.0  United Kingdom  
    179 2010-12-01 09:58:00       3.37     16029.0  United Kingdom  
    180 2010-12-01 09:58:00       3.37     16029.0  United Kingdom  
    181 2010-12-01 09:58:00       1.45     16029.0  United Kingdom  
    182 2010-12-01 09:58:00       1.25     16029.0  United Kingdom  
    183 2010-12-01 09:59:00       5.95     16250.0  United Kingdom  
    184 2010-12-01 09:59:00       5.95     16250.0  United Kingdom  
    185 2010-12-01 09:59:00       7.95     16250.0  United Kingdom  
    186 2010-12-01 09:59:00       4.95     16250.0  United Kingdom  
    187 2010-12-01 09:59:00       4.25     16250.0  United Kingdom  
    188 2010-12-01 09:59:00       2.95     16250.0  United Kingdom  
    189 2010-12-01 09:59:00       1.65     16250.0  United Kingdom  
    190 2010-12-01 09:59:00       0.42     16250.0  United Kingdom  
    191 2010-12-01 09:59:00       0.85     16250.0  United Kingdom  
    192 2010-12-01 09:59:00       1.45     16250.0  United Kingdom  
    193 2010-12-01 09:59:00       0.85     16250.0  United Kingdom  
    194 2010-12-01 09:59:00       6.75     16250.0  United Kingdom  
    195 2010-12-01 09:59:00       1.65     16250.0  United Kingdom  
    196 2010-12-01 09:59:00       1.65     16250.0  United Kingdom  
    197 2010-12-01 10:03:00       8.50     12431.0       Australia  
    198 2010-12-01 10:03:00       4.95     12431.0       Australia  
    199 2010-12-01 10:03:00       1.25     12431.0       Australia  
    200 2010-12-01 10:03:00       5.45     12431.0       Australia  
    201 2010-12-01 10:03:00       6.35     12431.0       Australia  
    202 2010-12-01 10:03:00       5.95     12431.0       Australia  
    203 2010-12-01 10:03:00       5.95     12431.0       Australia  
    204 2010-12-01 10:03:00       8.50     12431.0       Australia  
    205 2010-12-01 10:03:00       3.75     12431.0       Australia  
    206 2010-12-01 10:03:00       3.75     12431.0       Australia  
    207 2010-12-01 10:03:00       8.50     12431.0       Australia  
    208 2010-12-01 10:03:00       8.50     12431.0       Australia  
    209 2010-12-01 10:03:00       1.65     12431.0       Australia  
    210 2010-12-01 10:03:00       0.85     12431.0       Australia  
    211 2010-12-01 10:19:00       8.50     17511.0  United Kingdom  
    212 2010-12-01 10:19:00       3.75     17511.0  United Kingdom  
    213 2010-12-01 10:19:00       1.45     17511.0  United Kingdom  
    214 2010-12-01 10:19:00       0.72     17511.0  United Kingdom  
    215 2010-12-01 10:19:00       0.72     17511.0  United Kingdom  
    216 2010-12-01 10:19:00       8.50     17511.0  United Kingdom  
    217 2010-12-01 10:19:00       0.64     17511.0  United Kingdom  
    218 2010-12-01 10:19:00       2.55     17511.0  United Kingdom  
    219 2010-12-01 10:19:00       0.10     17511.0  United Kingdom  
    220 2010-12-01 10:19:00       2.55     17511.0  United Kingdom  
    221 2010-12-01 10:19:00       0.72     17511.0  United Kingdom  
    222 2010-12-01 10:19:00       1.45     17511.0  United Kingdom  
    223 2010-12-01 10:19:00       4.25     17511.0  United Kingdom  
    224 2010-12-01 10:19:00       0.64     17511.0  United Kingdom  
    225 2010-12-01 10:19:00       0.64     17511.0  United Kingdom  
    226 2010-12-01 10:19:00       0.65     17511.0  United Kingdom  
    227 2010-12-01 10:19:00       0.32     17511.0  United Kingdom  
    228 2010-12-01 10:19:00       4.95     17511.0  United Kingdom  
    229 2010-12-01 10:19:00       4.25     17511.0  United Kingdom  
    230 2010-12-01 10:19:00       3.39     17511.0  United Kingdom  
    231 2010-12-01 10:19:00       3.75     17511.0  United Kingdom  
    232 2010-12-01 10:19:00       1.48     17511.0  United Kingdom  
    233 2010-12-01 10:19:00       1.25     17511.0  United Kingdom  
    234 2010-12-01 10:19:00       1.65     17511.0  United Kingdom  
    235 2010-12-01 10:24:00       1.65     17548.0  United Kingdom  
    236 2010-12-01 10:24:00       0.29     17548.0  United Kingdom  
    237 2010-12-01 10:24:00       0.29     17548.0  United Kingdom  
    238 2010-12-01 10:24:00       0.29     17548.0  United Kingdom  
    239 2010-12-01 10:24:00       3.45     17548.0  United Kingdom  
    240 2010-12-01 10:24:00       1.65     17548.0  United Kingdom  
    241 2010-12-01 10:24:00       1.65     17548.0  United Kingdom  
    242 2010-12-01 10:29:00       1.95     13705.0  United Kingdom  
    243 2010-12-01 10:29:00       3.75     13705.0  United Kingdom  
    244 2010-12-01 10:29:00       1.25     13705.0  United Kingdom  
    245 2010-12-01 10:29:00       1.25     13705.0  United Kingdom  
    246 2010-12-01 10:29:00     165.00     13705.0  United Kingdom  
    247 2010-12-01 10:29:00       1.25     13705.0  United Kingdom  
    248 2010-12-01 10:29:00       1.25     13705.0  United Kingdom  
    249 2010-12-01 10:29:00       5.95     13705.0  United Kingdom  
    250 2010-12-01 10:29:00       1.69     13705.0  United Kingdom  
    251 2010-12-01 10:29:00       0.65     13705.0  United Kingdom  
    252 2010-12-01 10:37:00       9.95     13747.0  United Kingdom  
    253 2010-12-01 10:39:00       0.42     13408.0  United Kingdom  
    254 2010-12-01 10:39:00       1.85     13408.0  United Kingdom  
    255 2010-12-01 10:39:00       1.85     13408.0  United Kingdom  
    256 2010-12-01 10:39:00       1.85     13408.0  United Kingdom  
    257 2010-12-01 10:39:00       1.85     13408.0  United Kingdom  
    258 2010-12-01 10:39:00       4.95     13408.0  United Kingdom  
    259 2010-12-01 10:39:00       3.75     13408.0  United Kingdom  
    260 2010-12-01 10:39:00       1.25     13408.0  United Kingdom  
    261 2010-12-01 10:39:00       2.10     13408.0  United Kingdom  
    262 2010-12-01 10:39:00       2.55     13408.0  United Kingdom  
    263 2010-12-01 10:39:00       1.65     13408.0  United Kingdom  
    264 2010-12-01 10:47:00       3.95     13767.0  United Kingdom  
    265 2010-12-01 10:47:00       1.69     13767.0  United Kingdom  
    266 2010-12-01 10:47:00       0.55     13767.0  United Kingdom  
    267 2010-12-01 10:47:00       0.55     13767.0  United Kingdom  
    268 2010-12-01 10:47:00       0.55     13767.0  United Kingdom  
    269 2010-12-01 10:47:00       3.45     13767.0  United Kingdom  
    270 2010-12-01 10:47:00       2.10     13767.0  United Kingdom  
    271 2010-12-01 10:47:00       3.75     13767.0  United Kingdom  
    272 2010-12-01 10:47:00       3.75     13767.0  United Kingdom  
    273 2010-12-01 10:47:00       3.75     13767.0  United Kingdom  
    274 2010-12-01 10:47:00       3.75     13767.0  United Kingdom  
    275 2010-12-01 10:47:00       3.95     13767.0  United Kingdom  
    276 2010-12-01 10:47:00       2.10     13767.0  United Kingdom  
    277 2010-12-01 10:47:00       2.10     13767.0  United Kingdom  
    278 2010-12-01 10:51:00       2.55     17850.0  United Kingdom  
    279 2010-12-01 10:51:00       3.39     17850.0  United Kingdom  
    280 2010-12-01 10:51:00       2.75     17850.0  United Kingdom  
    281 2010-12-01 10:51:00       4.95     17850.0  United Kingdom  
    282 2010-12-01 10:51:00       4.95     17850.0  United Kingdom  
    283 2010-12-01 10:51:00       1.06     17850.0  United Kingdom  
    284 2010-12-01 10:51:00       1.06     17850.0  United Kingdom  
    285 2010-12-01 10:51:00       1.06     17850.0  United Kingdom  
    286 2010-12-01 10:51:00       1.06     17850.0  United Kingdom  
    287 2010-12-01 10:51:00       4.95     17850.0  United Kingdom  
    288 2010-12-01 10:51:00       6.95     17850.0  United Kingdom  
    289 2010-12-01 10:51:00       2.10     17850.0  United Kingdom  
    290 2010-12-01 10:51:00       2.55     17850.0  United Kingdom  
    291 2010-12-01 10:51:00       3.39     17850.0  United Kingdom  
    292 2010-12-01 10:51:00       3.39     17850.0  United Kingdom  
    293 2010-12-01 10:51:00       7.65     17850.0  United Kingdom  
    294 2010-12-01 10:51:00      35.75     17850.0  United Kingdom  
    295 2010-12-01 10:51:00       4.25     17850.0  United Kingdom  
    296 2010-12-01 10:51:00       4.65     17924.0  United Kingdom  
    297 2010-12-01 10:51:00       4.65     17924.0  United Kingdom  
    298 2010-12-01 10:52:00       0.29     13448.0  United Kingdom  
    299 2010-12-01 10:52:00       2.95     13448.0  United Kingdom  
    300 2010-12-01 10:52:00       6.75     13448.0  United Kingdom  
    301 2010-12-01 10:52:00       2.55     13448.0  United Kingdom  
    302 2010-12-01 10:52:00       8.50     13448.0  United Kingdom  
    303 2010-12-01 10:52:00       7.95     13448.0  United Kingdom  
    304 2010-12-01 10:52:00       2.10     13448.0  United Kingdom  
    305 2010-12-01 10:52:00       2.10     13448.0  United Kingdom  
    306 2010-12-01 10:52:00       2.10     13448.0  United Kingdom  
    307 2010-12-01 10:52:00       1.25     13448.0  United Kingdom  
    308 2010-12-01 10:52:00       1.65     13448.0  United Kingdom  
    309 2010-12-01 10:52:00       3.35     13448.0  United Kingdom  
    310 2010-12-01 10:52:00       3.95     13448.0  United Kingdom  
    311 2010-12-01 10:52:00       4.65     13448.0  United Kingdom  
    312 2010-12-01 10:52:00       4.95     13448.0  United Kingdom  
    313 2010-12-01 10:52:00       3.75     13448.0  United Kingdom  
    314 2010-12-01 10:52:00       4.95     13448.0  United Kingdom  
    315 2010-12-01 10:52:00       1.85     17850.0  United Kingdom  
    316 2010-12-01 10:52:00       1.85     17850.0  United Kingdom  
    317 2010-12-01 10:53:00       1.45     13448.0  United Kingdom  
    318 2010-12-01 11:21:00       2.55     15862.0  United Kingdom  
    319 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    320 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    321 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    322 2010-12-01 11:21:00       3.35     15862.0  United Kingdom  
    323 2010-12-01 11:21:00       1.45     15862.0  United Kingdom  
    324 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    325 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    326 2010-12-01 11:21:00       1.65     15862.0  United Kingdom  
    327 2010-12-01 11:21:00       1.45     15862.0  United Kingdom  
    328 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    329 2010-12-01 11:21:00       4.95     15862.0  United Kingdom  
    330 2010-12-01 11:21:00       3.75     15862.0  United Kingdom  
    331 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    332 2010-12-01 11:21:00       9.95     15862.0  United Kingdom  
    333 2010-12-01 11:21:00       9.95     15862.0  United Kingdom  
    334 2010-12-01 11:21:00       5.95     15862.0  United Kingdom  
    335 2010-12-01 11:21:00       4.25     15862.0  United Kingdom  
    336 2010-12-01 11:21:00       4.95     15862.0  United Kingdom  
    337 2010-12-01 11:21:00       2.55     15862.0  United Kingdom  
    338 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    339 2010-12-01 11:21:00       1.69     15862.0  United Kingdom  
    340 2010-12-01 11:21:00       7.95     15862.0  United Kingdom  
    341 2010-12-01 11:21:00       0.55     15862.0  United Kingdom  
    342 2010-12-01 11:21:00       0.55     15862.0  United Kingdom  
    343 2010-12-01 11:21:00       0.55     15862.0  United Kingdom  
    344 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    345 2010-12-01 11:21:00       2.10     15862.0  United Kingdom  
    346 2010-12-01 11:21:00       2.10     15862.0  United Kingdom  
    347 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    348 2010-12-01 11:21:00       0.85     15862.0  United Kingdom  
    349 2010-12-01 11:21:00       0.55     15862.0  United Kingdom  
    350 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    351 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    352 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    353 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    354 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    355 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    356 2010-12-01 11:21:00       1.65     15862.0  United Kingdom  
    357 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    358 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    359 2010-12-01 11:21:00       5.95     15862.0  United Kingdom  
    360 2010-12-01 11:21:00       1.25     15862.0  United Kingdom  
    361 2010-12-01 11:21:00       2.55     15862.0  United Kingdom  
    362 2010-12-01 11:21:00       0.85     15862.0  United Kingdom  
    363 2010-12-01 11:21:00       1.65     15862.0  United Kingdom  
    364 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    365 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    366 2010-12-01 11:21:00       5.95     15862.0  United Kingdom  
    367 2010-12-01 11:21:00       7.95     15862.0  United Kingdom  
    368 2010-12-01 11:21:00       1.65     15862.0  United Kingdom  
    369 2010-12-01 11:21:00       1.65     15862.0  United Kingdom  
    370 2010-12-01 11:21:00       1.65     15862.0  United Kingdom  
    371 2010-12-01 11:21:00       1.65     15862.0  United Kingdom  
    372 2010-12-01 11:21:00       2.55     15862.0  United Kingdom  
    373 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    374 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    375 2010-12-01 11:21:00       2.55     15862.0  United Kingdom  
    376 2010-12-01 11:21:00      16.95     15862.0  United Kingdom  
    377 2010-12-01 11:21:00       2.95     15862.0  United Kingdom  
    378 2010-12-01 11:21:00      10.65     15862.0  United Kingdom  
    379 2010-12-01 11:21:00       4.25     15862.0  United Kingdom  
    380 2010-12-01 11:21:00       6.95     15862.0  United Kingdom  
    381 2010-12-01 11:21:00       5.95     15862.0  United Kingdom  
    382 2010-12-01 11:22:00       2.55     15513.0  United Kingdom  
    383 2010-12-01 11:22:00       2.55     15513.0  United Kingdom  
    384 2010-12-01 11:22:00       4.25     15513.0  United Kingdom  
    385 2010-12-01 11:27:00       1.85     12791.0     Netherlands  
    386 2010-12-01 11:27:00      15.00     12791.0     Netherlands  
    387 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    388 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    389 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    390 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    391 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    392 2010-12-01 11:29:00       1.65     16218.0  United Kingdom  
    393 2010-12-01 11:29:00       0.85     16218.0  United Kingdom  
    394 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    395 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    396 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    397 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    398 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    399 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    400 2010-12-01 11:29:00       0.85     16218.0  United Kingdom  
    401 2010-12-01 11:29:00       0.85     16218.0  United Kingdom  
    402 2010-12-01 11:29:00       0.85     16218.0  United Kingdom  
    403 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    404 2010-12-01 11:29:00       1.25     16218.0  United Kingdom  
    405 2010-12-01 11:29:00       2.10     16218.0  United Kingdom  
    406 2010-12-01 11:29:00       0.55     16218.0  United Kingdom  
    407 2010-12-01 11:29:00       0.55     16218.0  United Kingdom  
    408 2010-12-01 11:29:00       0.55     16218.0  United Kingdom  
    409 2010-12-01 11:29:00       0.55     16218.0  United Kingdom  
    410 2010-12-01 11:29:00       0.55     16218.0  United Kingdom  
    411 2010-12-01 11:29:00       1.65     16218.0  United Kingdom  
    412 2010-12-01 11:29:00       1.65     16218.0  United Kingdom  
    413 2010-12-01 11:29:00       1.65     16218.0  United Kingdom  
    414 2010-12-01 11:29:00       1.65     16218.0  United Kingdom  
    415 2010-12-01 11:32:00       2.55     14045.0  United Kingdom  
    416 2010-12-01 11:33:00       2.55     17850.0  United Kingdom  
    417 2010-12-01 11:33:00       3.39     17850.0  United Kingdom  
    418 2010-12-01 11:33:00       2.75     17850.0  United Kingdom  
    419 2010-12-01 11:33:00       4.95     17850.0  United Kingdom  
    420 2010-12-01 11:33:00       1.06     17850.0  United Kingdom  
    421 2010-12-01 11:33:00       1.06     17850.0  United Kingdom  
    422 2010-12-01 11:33:00       1.06     17850.0  United Kingdom  
    423 2010-12-01 11:33:00       1.06     17850.0  United Kingdom  
    424 2010-12-01 11:33:00       4.95     17850.0  United Kingdom  
    425 2010-12-01 11:33:00       6.95     17850.0  United Kingdom  
    426 2010-12-01 11:33:00       2.10     17850.0  United Kingdom  
    427 2010-12-01 11:33:00       2.55     17850.0  United Kingdom  
    428 2010-12-01 11:33:00       3.39     17850.0  United Kingdom  
    429 2010-12-01 11:33:00       3.39     17850.0  United Kingdom  
    430 2010-12-01 11:33:00       7.65     17850.0  United Kingdom  
    431 2010-12-01 11:33:00      35.75     17850.0  United Kingdom  
    432 2010-12-01 11:33:00       4.25     17850.0  United Kingdom  
    433 2010-12-01 11:34:00       1.85     17850.0  United Kingdom  
    434 2010-12-01 11:34:00       1.85     17850.0  United Kingdom  
    435 2010-12-01 11:41:00       0.42     14307.0  United Kingdom  
    436 2010-12-01 11:41:00       0.42     14307.0  United Kingdom  
    437 2010-12-01 11:41:00       0.85     14307.0  United Kingdom  
    438 2010-12-01 11:41:00       1.65     14307.0  United Kingdom  
    439 2010-12-01 11:41:00       1.25     14307.0  United Kingdom  
    440 2010-12-01 11:41:00       1.25     14307.0  United Kingdom  
    441 2010-12-01 11:41:00       0.85     14307.0  United Kingdom  
    442 2010-12-01 11:41:00       1.95     14307.0  United Kingdom  
    443 2010-12-01 11:41:00       3.95     14307.0  United Kingdom  
    444 2010-12-01 11:41:00       3.75     14307.0  United Kingdom  
    445 2010-12-01 11:41:00       3.75     14307.0  United Kingdom  
    446 2010-12-01 11:41:00       2.10     14307.0  United Kingdom  
    447 2010-12-01 11:41:00       2.10     14307.0  United Kingdom  
    448 2010-12-01 11:41:00       0.85     14307.0  United Kingdom  
    449 2010-12-01 11:41:00       1.25     14307.0  United Kingdom  
    450 2010-12-01 11:41:00       0.95     14307.0  United Kingdom  
    451 2010-12-01 11:41:00       2.95     14307.0  United Kingdom  
    452 2010-12-01 11:41:00       1.65     14307.0  United Kingdom  
    453 2010-12-01 11:41:00       1.65     14307.0  United Kingdom  
    454 2010-12-01 11:41:00       7.95     14307.0  United Kingdom  
    455 2010-12-01 11:41:00       7.95     14307.0  United Kingdom  
    456 2010-12-01 11:41:00       1.65     14307.0  United Kingdom  
    457 2010-12-01 11:41:00       0.85     14307.0  United Kingdom  
    458 2010-12-01 11:41:00       1.69     14307.0  United Kingdom  
    459 2010-12-01 11:41:00       5.95     14307.0  United Kingdom  
    460 2010-12-01 11:41:00       5.95     14307.0  United Kingdom  
    461 2010-12-01 11:41:00       2.95     14307.0  United Kingdom  
    462 2010-12-01 11:41:00       0.85     14307.0  United Kingdom  
    463 2010-12-01 11:41:00       0.42     14307.0  United Kingdom  
    464 2010-12-01 11:41:00       0.42     14307.0  United Kingdom  
    465 2010-12-01 11:41:00       4.25     14307.0  United Kingdom  
    466 2010-12-01 11:41:00       5.95     14307.0  United Kingdom  
    467 2010-12-01 11:41:00       5.95     14307.0  United Kingdom  
    468 2010-12-01 11:41:00       3.75     14307.0  United Kingdom  
    469 2010-12-01 11:41:00       0.55     14307.0  United Kingdom  
    470 2010-12-01 11:41:00       1.45     14307.0  United Kingdom  
    471 2010-12-01 11:41:00       4.95     14307.0  United Kingdom  
    472 2010-12-01 11:41:00       1.65     14307.0  United Kingdom  
    473 2010-12-01 11:41:00       0.21     14307.0  United Kingdom  
    474 2010-12-01 11:41:00       0.42     14307.0  United Kingdom  
    475 2010-12-01 11:41:00       1.95     14307.0  United Kingdom  
    476 2010-12-01 11:41:00       2.55     14307.0  United Kingdom  
    477 2010-12-01 11:41:00       2.55     14307.0  United Kingdom  
    478 2010-12-01 11:41:00       1.65     14307.0  United Kingdom  
    479 2010-12-01 11:41:00       0.65     14307.0  United Kingdom  
    480 2010-12-01 11:41:00       1.25     14307.0  United Kingdom  
    481 2010-12-01 11:41:00       3.75     14307.0  United Kingdom  
    482 2010-12-01 11:41:00       1.65     14307.0  United Kingdom  
    483 2010-12-01 11:45:00       6.35     17908.0  United Kingdom  
    484 2010-12-01 11:45:00       3.75     17908.0  United Kingdom  
    485 2010-12-01 11:45:00       4.95     17908.0  United Kingdom  
    486 2010-12-01 11:45:00       6.75     17908.0  United Kingdom  
    487 2010-12-01 11:45:00       1.25     17908.0  United Kingdom  
    488 2010-12-01 11:45:00       1.65     17908.0  United Kingdom  
    489 2010-12-01 11:45:00       2.10     17908.0  United Kingdom  
    490 2010-12-01 11:45:00       3.75     17908.0  United Kingdom  
    491 2010-12-01 11:45:00       2.10     17908.0  United Kingdom  
    492 2010-12-01 11:45:00       2.10     17908.0  United Kingdom  
    493 2010-12-01 11:45:00       2.95     17908.0  United Kingdom  
    494 2010-12-01 11:45:00       1.25     17908.0  United Kingdom  
    495 2010-12-01 11:45:00       1.25     17908.0  United Kingdom  
    496 2010-12-01 11:45:00       2.95     17908.0  United Kingdom  
    497 2010-12-01 11:45:00       2.95     17908.0  United Kingdom  
    498 2010-12-01 11:45:00       6.35     17908.0  United Kingdom  
    499 2010-12-01 11:45:00       7.95     17908.0  United Kingdom  


We can see the irregularities in the data. First, InvoiceNos and Stockcodes are not only number, it has some letters. There are negative quanities too. 

First, we need to change Invoice Column Datatype first. then we will create a column then we will seperate the data with letters from main dataframe.



```python
# Convert InvoiceNo to string data type
df.loc[:, 'InvoiceNo'] = df['InvoiceNo'].astype(str)
```

We noticed the negative number in quanitity column. So, how many unique letter groups and their respective count numbers are in the dataframe.



```python
group_counts = df['InvoiceNo'].str.extract(r'([a-zA-Z]+)').squeeze().value_counts()
print(group_counts)
```

    0
    C    9288
    A       3
    Name: count, dtype: int64


There are only 2 group in the invoice column. We should check those first.


```python
# Create the DataFrames A_rows and rest_rows
A_rows = df[df['InvoiceNo'].str.contains(r'A')]
C_rows = df[df['InvoiceNo'].str.contains(r'C')]

# Print the DataFrames A_rows and rest_rows using f-strings
print(f"A_rows:\n{A_rows}\n")
print(f"Rest_rows:\n{C_rows}")
```

    A_rows:
           InvoiceNo StockCode      Description  Quantity         InvoiceDate   
    299982   A563185         B  Adjust bad debt         1 2011-08-12 14:50:00  \
    299983   A563186         B  Adjust bad debt         1 2011-08-12 14:51:00   
    299984   A563187         B  Adjust bad debt         1 2011-08-12 14:52:00   
    
            UnitPrice  CustomerID         Country  
    299982   11062.06         0.0  United Kingdom  
    299983  -11062.06         0.0  United Kingdom  
    299984  -11062.06         0.0  United Kingdom  
    
    Rest_rows:
           InvoiceNo StockCode                       Description  Quantity   
    141      C536379         D                          Discount        -1  \
    154      C536383    35004C   SET OF 3 COLOURED  FLYING DUCKS        -1   
    235      C536391     22556    PLASTERS IN TIN CIRCUS PARADE        -12   
    236      C536391     21984  PACK OF 12 PINK PAISLEY TISSUES        -24   
    237      C536391     21983  PACK OF 12 BLUE PAISLEY TISSUES        -24   
    ...          ...       ...                               ...       ...   
    540449   C581490     23144   ZINC T-LIGHT HOLDER STARS SMALL       -11   
    541541   C581499         M                            Manual        -1   
    541715   C581568     21258        VICTORIAN SEWING BOX LARGE        -5   
    541716   C581569     84978  HANGING HEART JAR T-LIGHT HOLDER        -1   
    541717   C581569     20979     36 PENCILS TUBE RED RETROSPOT        -5   
    
                   InvoiceDate  UnitPrice  CustomerID         Country  
    141    2010-12-01 09:41:00      27.50     14527.0  United Kingdom  
    154    2010-12-01 09:49:00       4.65     15311.0  United Kingdom  
    235    2010-12-01 10:24:00       1.65     17548.0  United Kingdom  
    236    2010-12-01 10:24:00       0.29     17548.0  United Kingdom  
    237    2010-12-01 10:24:00       0.29     17548.0  United Kingdom  
    ...                    ...        ...         ...             ...  
    540449 2011-12-09 09:57:00       0.83     14397.0  United Kingdom  
    541541 2011-12-09 10:28:00     224.69     15498.0  United Kingdom  
    541715 2011-12-09 11:57:00      10.95     15311.0  United Kingdom  
    541716 2011-12-09 11:58:00       1.25     17315.0  United Kingdom  
    541717 2011-12-09 11:58:00       1.25     17315.0  United Kingdom  
    
    [9288 rows x 8 columns]


It turns out that A are just adjustments and not related to our dataframe. So we will drop these rows.


```python
# Drop rows with 'A' in the letter group from the main df
df = df[~df['InvoiceNo'].str.contains(r'A')].reset_index(drop=True)
```

Now, let's get back to 'C' invoices.  A was Adjustment so since it start wih C , it should be cancelled invoices. but we have to check and make sure that the InvoiceNo with the letters and the negative quantity are related or not.


```python
# Check if there are any rows in the subset with missing unit prices, customer IDs, and quantities
if len(df['InvoiceNo'].str.contains(r'C')) and len(df['Quantity'] <= 0):
    print("The Invoice_with_C and the negative quantities are related")
else:
    print("The Invoice_with_C and the negative quantities are not related")
```

    The Invoice_with_C and the negative quantities are related


Since these two are related, the C columns are return invoices.So, we need to seperate these into another dataframe and we will check the cancelled items later.


```python
# Filter the DataFrame for cancelled invoices
cancelled_df = df[df['InvoiceNo'].str.contains(r'C')]

# Export cancelled_df to a CSV file with all columns
cancelled_df.to_csv('cancelled_invoices.csv', index=False, columns=cancelled_df.columns)
```

We also export cancelled_df to csv file as a backup. Now we will delete those rows from our main data frame and reset the index.


```python
# Drop rows with 'C' in the letter group from the main df
df = df[~df['InvoiceNo'].str.contains(r'C')].reset_index(drop=True)
```


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 532618 entries, 0 to 532617
    Data columns (total 8 columns):
     #   Column       Non-Null Count   Dtype         
    ---  ------       --------------   -----         
     0   InvoiceNo    532618 non-null  object        
     1   StockCode    532618 non-null  object        
     2   Description  532618 non-null  object        
     3   Quantity     532618 non-null  int64         
     4   InvoiceDate  532618 non-null  datetime64[ns]
     5   UnitPrice    532618 non-null  float64       
     6   CustomerID   532618 non-null  float64       
     7   Country      532618 non-null  object        
    dtypes: datetime64[ns](1), float64(2), int64(1), object(4)
    memory usage: 32.5+ MB


Now we have only 532618 rows and 8 columns. We should look through our data again.


```python
# View the selected range of rows
print(df[:100])
```

       InvoiceNo StockCode                          Description  Quantity   
    0     536365    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6  \
    1     536365     71053                  WHITE METAL LANTERN         6   
    2     536365    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    3     536365    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    4     536365    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    5     536365     22752         SET 7 BABUSHKA NESTING BOXES         2   
    6     536365     21730    GLASS STAR FROSTED T-LIGHT HOLDER         6   
    7     536366     22633               HAND WARMER UNION JACK         6   
    8     536366     22632            HAND WARMER RED POLKA DOT         6   
    9     536367     84879        ASSORTED COLOUR BIRD ORNAMENT        32   
    10    536367     22745           POPPY'S PLAYHOUSE BEDROOM          6   
    11    536367     22748            POPPY'S PLAYHOUSE KITCHEN         6   
    12    536367     22749    FELTCRAFT PRINCESS CHARLOTTE DOLL         8   
    13    536367     22310              IVORY KNITTED MUG COSY          6   
    14    536367     84969   BOX OF 6 ASSORTED COLOUR TEASPOONS         6   
    15    536367     22623        BOX OF VINTAGE JIGSAW BLOCKS          3   
    16    536367     22622       BOX OF VINTAGE ALPHABET BLOCKS         2   
    17    536367     21754             HOME BUILDING BLOCK WORD         3   
    18    536367     21755             LOVE BUILDING BLOCK WORD         3   
    19    536367     21777          RECIPE BOX WITH METAL HEART         4   
    20    536367     48187                  DOORMAT NEW ENGLAND         4   
    21    536368     22960             JAM MAKING SET WITH JARS         6   
    22    536368     22913          RED COAT RACK PARIS FASHION         3   
    23    536368     22912       YELLOW COAT RACK PARIS FASHION         3   
    24    536368     22914         BLUE COAT RACK PARIS FASHION         3   
    25    536369     21756             BATH BUILDING BLOCK WORD         3   
    26    536370     22728            ALARM CLOCK BAKELIKE PINK        24   
    27    536370     22727            ALARM CLOCK BAKELIKE RED         24   
    28    536370     22726           ALARM CLOCK BAKELIKE GREEN        12   
    29    536370     21724      PANDA AND BUNNIES STICKER SHEET        12   
    30    536370     21883                     STARS GIFT TAPE         24   
    31    536370     10002          INFLATABLE POLITICAL GLOBE         48   
    32    536370     21791   VINTAGE HEADS AND TAILS CARD GAME         24   
    33    536370     21035      SET/2 RED RETROSPOT TEA TOWELS         18   
    34    536370     22326  ROUND SNACK BOXES SET OF4 WOODLAND         24   
    35    536370     22629                  SPACEBOY LUNCH BOX         24   
    36    536370     22659              LUNCH BOX I LOVE LONDON        24   
    37    536370     22631             CIRCUS PARADE LUNCH BOX         24   
    38    536370     22661      CHARLOTTE BAG DOLLY GIRL DESIGN        20   
    39    536370     21731        RED TOADSTOOL LED NIGHT LIGHT        24   
    40    536370     22900      SET 2 TEA TOWELS I LOVE LONDON         24   
    41    536370     21913       VINTAGE SEASIDE JIGSAW PUZZLES        12   
    42    536370     22540           MINI JIGSAW CIRCUS PARADE         24   
    43    536370     22544                 MINI JIGSAW SPACEBOY        24   
    44    536370     22492              MINI PAINT SET VINTAGE         36   
    45    536370      POST                              POSTAGE         3   
    46    536371     22086      PAPER CHAIN KIT 50'S CHRISTMAS         80   
    47    536372     22632            HAND WARMER RED POLKA DOT         6   
    48    536372     22633               HAND WARMER UNION JACK         6   
    49    536373    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6   
    50    536373     71053                  WHITE METAL LANTERN         6   
    51    536373    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    52    536373     20679                EDWARDIAN PARASOL RED         6   
    53    536373     37370           RETRO COFFEE MUGS ASSORTED         6   
    54    536373     21871                  SAVE THE PLANET MUG         6   
    55    536373     21071       VINTAGE BILLBOARD DRINK ME MUG         6   
    56    536373     21068      VINTAGE BILLBOARD LOVE/HATE MUG         6   
    57    536373     82483   WOOD 2 DRAWER CABINET WHITE FINISH         2   
    58    536373     82486    WOOD S/3 CABINET ANT WHITE FINISH         4   
    59    536373     82482    WOODEN PICTURE FRAME WHITE FINISH         6   
    60    536373    82494L          WOODEN FRAME ANTIQUE WHITE          6   
    61    536373    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    62    536373    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    63    536373     22752         SET 7 BABUSHKA NESTING BOXES         2   
    64    536373     21730    GLASS STAR FROSTED T-LIGHT HOLDER         6   
    65    536374     21258           VICTORIAN SEWING BOX LARGE        32   
    66    536375    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6   
    67    536375     71053                  WHITE METAL LANTERN         6   
    68    536375    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    69    536375     20679                EDWARDIAN PARASOL RED         6   
    70    536375     37370           RETRO COFFEE MUGS ASSORTED         6   
    71    536375     21871                  SAVE THE PLANET MUG         6   
    72    536375     21071       VINTAGE BILLBOARD DRINK ME MUG         6   
    73    536375     21068      VINTAGE BILLBOARD LOVE/HATE MUG         6   
    74    536375     82483   WOOD 2 DRAWER CABINET WHITE FINISH         2   
    75    536375     82486    WOOD S/3 CABINET ANT WHITE FINISH         4   
    76    536375     82482    WOODEN PICTURE FRAME WHITE FINISH         6   
    77    536375    82494L          WOODEN FRAME ANTIQUE WHITE          6   
    78    536375    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    79    536375    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    80    536375     22752         SET 7 BABUSHKA NESTING BOXES         2   
    81    536375     21730    GLASS STAR FROSTED T-LIGHT HOLDER         6   
    82    536376     22114    HOT WATER BOTTLE TEA AND SYMPATHY        48   
    83    536376     21733     RED HANGING HEART T-LIGHT HOLDER        64   
    84    536377     22632            HAND WARMER RED POLKA DOT         6   
    85    536377     22633               HAND WARMER UNION JACK         6   
    86    536378     22386              JUMBO BAG PINK POLKADOT        10   
    87    536378    85099C       JUMBO  BAG BAROQUE BLACK WHITE        10   
    88    536378     21033      JUMBO BAG CHARLIE AND LOLA TOYS        10   
    89    536378     20723             STRAWBERRY CHARLOTTE BAG        10   
    90    536378    84997B    RED 3 PIECE RETROSPOT CUTLERY SET        12   
    91    536378    84997C    BLUE 3 PIECE POLKADOT CUTLERY SET         6   
    92    536378     21094        SET/6 RED SPOTTY PAPER PLATES        12   
    93    536378     20725              LUNCH BAG RED RETROSPOT        10   
    94    536378     21559    STRAWBERRY LUNCH BOX WITH CUTLERY         6   
    95    536378     22352    LUNCH BOX WITH CUTLERY RETROSPOT          6   
    96    536378     21212      PACK OF 72 RETROSPOT CAKE CASES       120   
    97    536378     21975       PACK OF 60 DINOSAUR CAKE CASES        24   
    98    536378     21977   PACK OF 60 PINK PAISLEY CAKE CASES        24   
    99    536378     84991          60 TEATIME FAIRY CAKE CASES        24   
    
               InvoiceDate  UnitPrice  CustomerID         Country  
    0  2010-12-01 08:26:00       2.55     17850.0  United Kingdom  
    1  2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    2  2010-12-01 08:26:00       2.75     17850.0  United Kingdom  
    3  2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    4  2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    5  2010-12-01 08:26:00       7.65     17850.0  United Kingdom  
    6  2010-12-01 08:26:00       4.25     17850.0  United Kingdom  
    7  2010-12-01 08:28:00       1.85     17850.0  United Kingdom  
    8  2010-12-01 08:28:00       1.85     17850.0  United Kingdom  
    9  2010-12-01 08:34:00       1.69     13047.0  United Kingdom  
    10 2010-12-01 08:34:00       2.10     13047.0  United Kingdom  
    11 2010-12-01 08:34:00       2.10     13047.0  United Kingdom  
    12 2010-12-01 08:34:00       3.75     13047.0  United Kingdom  
    13 2010-12-01 08:34:00       1.65     13047.0  United Kingdom  
    14 2010-12-01 08:34:00       4.25     13047.0  United Kingdom  
    15 2010-12-01 08:34:00       4.95     13047.0  United Kingdom  
    16 2010-12-01 08:34:00       9.95     13047.0  United Kingdom  
    17 2010-12-01 08:34:00       5.95     13047.0  United Kingdom  
    18 2010-12-01 08:34:00       5.95     13047.0  United Kingdom  
    19 2010-12-01 08:34:00       7.95     13047.0  United Kingdom  
    20 2010-12-01 08:34:00       7.95     13047.0  United Kingdom  
    21 2010-12-01 08:34:00       4.25     13047.0  United Kingdom  
    22 2010-12-01 08:34:00       4.95     13047.0  United Kingdom  
    23 2010-12-01 08:34:00       4.95     13047.0  United Kingdom  
    24 2010-12-01 08:34:00       4.95     13047.0  United Kingdom  
    25 2010-12-01 08:35:00       5.95     13047.0  United Kingdom  
    26 2010-12-01 08:45:00       3.75     12583.0          France  
    27 2010-12-01 08:45:00       3.75     12583.0          France  
    28 2010-12-01 08:45:00       3.75     12583.0          France  
    29 2010-12-01 08:45:00       0.85     12583.0          France  
    30 2010-12-01 08:45:00       0.65     12583.0          France  
    31 2010-12-01 08:45:00       0.85     12583.0          France  
    32 2010-12-01 08:45:00       1.25     12583.0          France  
    33 2010-12-01 08:45:00       2.95     12583.0          France  
    34 2010-12-01 08:45:00       2.95     12583.0          France  
    35 2010-12-01 08:45:00       1.95     12583.0          France  
    36 2010-12-01 08:45:00       1.95     12583.0          France  
    37 2010-12-01 08:45:00       1.95     12583.0          France  
    38 2010-12-01 08:45:00       0.85     12583.0          France  
    39 2010-12-01 08:45:00       1.65     12583.0          France  
    40 2010-12-01 08:45:00       2.95     12583.0          France  
    41 2010-12-01 08:45:00       3.75     12583.0          France  
    42 2010-12-01 08:45:00       0.42     12583.0          France  
    43 2010-12-01 08:45:00       0.42     12583.0          France  
    44 2010-12-01 08:45:00       0.65     12583.0          France  
    45 2010-12-01 08:45:00      18.00     12583.0          France  
    46 2010-12-01 09:00:00       2.55     13748.0  United Kingdom  
    47 2010-12-01 09:01:00       1.85     17850.0  United Kingdom  
    48 2010-12-01 09:01:00       1.85     17850.0  United Kingdom  
    49 2010-12-01 09:02:00       2.55     17850.0  United Kingdom  
    50 2010-12-01 09:02:00       3.39     17850.0  United Kingdom  
    51 2010-12-01 09:02:00       2.75     17850.0  United Kingdom  
    52 2010-12-01 09:02:00       4.95     17850.0  United Kingdom  
    53 2010-12-01 09:02:00       1.06     17850.0  United Kingdom  
    54 2010-12-01 09:02:00       1.06     17850.0  United Kingdom  
    55 2010-12-01 09:02:00       1.06     17850.0  United Kingdom  
    56 2010-12-01 09:02:00       1.06     17850.0  United Kingdom  
    57 2010-12-01 09:02:00       4.95     17850.0  United Kingdom  
    58 2010-12-01 09:02:00       6.95     17850.0  United Kingdom  
    59 2010-12-01 09:02:00       2.10     17850.0  United Kingdom  
    60 2010-12-01 09:02:00       2.55     17850.0  United Kingdom  
    61 2010-12-01 09:02:00       3.39     17850.0  United Kingdom  
    62 2010-12-01 09:02:00       3.39     17850.0  United Kingdom  
    63 2010-12-01 09:02:00       7.65     17850.0  United Kingdom  
    64 2010-12-01 09:02:00       4.25     17850.0  United Kingdom  
    65 2010-12-01 09:09:00      10.95     15100.0  United Kingdom  
    66 2010-12-01 09:32:00       2.55     17850.0  United Kingdom  
    67 2010-12-01 09:32:00       3.39     17850.0  United Kingdom  
    68 2010-12-01 09:32:00       2.75     17850.0  United Kingdom  
    69 2010-12-01 09:32:00       4.95     17850.0  United Kingdom  
    70 2010-12-01 09:32:00       1.06     17850.0  United Kingdom  
    71 2010-12-01 09:32:00       1.06     17850.0  United Kingdom  
    72 2010-12-01 09:32:00       1.06     17850.0  United Kingdom  
    73 2010-12-01 09:32:00       1.06     17850.0  United Kingdom  
    74 2010-12-01 09:32:00       4.95     17850.0  United Kingdom  
    75 2010-12-01 09:32:00       6.95     17850.0  United Kingdom  
    76 2010-12-01 09:32:00       2.10     17850.0  United Kingdom  
    77 2010-12-01 09:32:00       2.55     17850.0  United Kingdom  
    78 2010-12-01 09:32:00       3.39     17850.0  United Kingdom  
    79 2010-12-01 09:32:00       3.39     17850.0  United Kingdom  
    80 2010-12-01 09:32:00       7.65     17850.0  United Kingdom  
    81 2010-12-01 09:32:00       4.25     17850.0  United Kingdom  
    82 2010-12-01 09:32:00       3.45     15291.0  United Kingdom  
    83 2010-12-01 09:32:00       2.55     15291.0  United Kingdom  
    84 2010-12-01 09:34:00       1.85     17850.0  United Kingdom  
    85 2010-12-01 09:34:00       1.85     17850.0  United Kingdom  
    86 2010-12-01 09:37:00       1.95     14688.0  United Kingdom  
    87 2010-12-01 09:37:00       1.95     14688.0  United Kingdom  
    88 2010-12-01 09:37:00       2.95     14688.0  United Kingdom  
    89 2010-12-01 09:37:00       0.85     14688.0  United Kingdom  
    90 2010-12-01 09:37:00       3.75     14688.0  United Kingdom  
    91 2010-12-01 09:37:00       3.75     14688.0  United Kingdom  
    92 2010-12-01 09:37:00       0.85     14688.0  United Kingdom  
    93 2010-12-01 09:37:00       1.65     14688.0  United Kingdom  
    94 2010-12-01 09:37:00       2.55     14688.0  United Kingdom  
    95 2010-12-01 09:37:00       2.55     14688.0  United Kingdom  
    96 2010-12-01 09:37:00       0.42     14688.0  United Kingdom  
    97 2010-12-01 09:37:00       0.55     14688.0  United Kingdom  
    98 2010-12-01 09:37:00       0.55     14688.0  United Kingdom  
    99 2010-12-01 09:37:00       0.55     14688.0  United Kingdom  



```python
df.describe()
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
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>UnitPrice</th>
      <th>CustomerID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>532618.000000</td>
      <td>532618</td>
      <td>532618.000000</td>
      <td>532618.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>10.240024</td>
      <td>2011-07-04 17:05:51.870532864</td>
      <td>3.868412</td>
      <td>11426.529088</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-9600.000000</td>
      <td>2010-12-01 08:26:00</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.000000</td>
      <td>2011-03-28 12:13:00</td>
      <td>1.250000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3.000000</td>
      <td>2011-07-20 11:54:00</td>
      <td>2.080000</td>
      <td>14362.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>10.000000</td>
      <td>2011-10-19 12:21:00</td>
      <td>4.130000</td>
      <td>16255.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>80995.000000</td>
      <td>2011-12-09 12:50:00</td>
      <td>13541.330000</td>
      <td>18287.000000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>159.593999</td>
      <td>NaN</td>
      <td>32.470442</td>
      <td>6810.887001</td>
    </tr>
  </tbody>
</table>
</div>



Although we drop our negative rows, there seems to be negative quanitites left. we should check that.


```python
negative_quantity_rows = df[df['Quantity'] < 0]
negative_quantity_rows['Description'].value_counts()
```




    Description
    Missing_Description                    862
    check                                  120
    damages                                 45
    damaged                                 42
    ?                                       41
    sold as set on dotcom                   20
    Damaged                                 14
    thrown away                              9
    Unsaleable, destroyed.                   9
    ??                                       7
    wet damaged                              5
    damages?                                 5
    ebay                                     5
    smashed                                  4
    missing                                  3
    wet pallet                               3
    CHECK                                    3
    mixed up                                 2
    incorrect stock entry.                   2
    crushed                                  2
    adjustment                               2
    wet/rusty                                2
    reverse 21/5/10 adjustment               2
    ?missing                                 2
    damages wax                              2
    Dotcom sales                             2
    sold as 1                                2
    counted                                  2
    stock check                              2
    ???missing                               2
    printing smudges/thrown away             2
    rusty throw away                         2
    dotcom                                   2
    wet rusty                                2
    test                                     1
    incorrectly put back into stock          1
    Incorrect stock entry.                   1
    historic computer difference?....se      1
    Dagamed                                  1
    OOPS ! adjustment                        1
    Damages/samples                          1
    ?display?                                1
    ????damages????                          1
    temp adjustment                          1
    Crushed                                  1
    crushed ctn                              1
    taig adjust no stock                     1
    wrongly coded-23343                      1
    code mix up? 84930                       1
    Sold as 1 on dotcom                      1
    lost??                                   1
    crushed boxes                            1
    ???                                      1
    lost in space                            1
    ????missing                              1
    ?? missing                               1
    rusty thrown away                        1
    sold with wrong barcode                  1
    ???lost                                  1
    missing?                                 1
    wrongly marked carton 22804              1
    Wrongly mrked had 85123a in box          1
    water damaged                            1
    dotcom sales                             1
    Damages                                  1
    WET/MOULDY                               1
    wet                                      1
    wrongly coded 20713                      1
    20713                                    1
    Breakages                                1
    stock creditted wrongly                  1
    20713 wrongly marked                     1
    wet boxes                                1
    Wet pallet-thrown away                   1
    mouldy                                   1
    wet?                                     1
    can't find                               1
    re-adjustment                            1
    water damage                             1
    wrongly marked. 23343 in box             1
    mouldy, unsaleable.                      1
    thrown away-can't sell                   1
    thrown away-can't sell.                  1
    ?lost                                    1
    barcode problem                          1
    wrong barcode                            1
    wrong barcode (22467)                    1
    throw away                               1
    broken                                   1
    damaged stock                            1
    damages/display                          1
    Thrown away.                             1
    ?sold as sets?                           1
    ? sold as sets?                          1
    wrongly sold sets                        1
    dotcom sold sets                         1
    Amazon sold sets                         1
    wrongly sold as sets                     1
    Dotcom set                               1
    MIA                                      1
    showroom                                 1
    incorrectly made-thrown away.            1
    samples/damages                          1
    label mix up                             1
    Dotcom                                   1
    Given away                               1
    mouldy, thrown away.                     1
    faulty                                   1
    re dotcom quick fix.                     1
    Dotcom sold in 6's                       1
    sold in set?                             1
    Not rcvd in 10/11/2010 delivery          1
    mix up with c                            1
    Show Samples                             1
    found some more on shelf                 1
    Printing smudges/thrown away             1
    sold as set by dotcom                    1
    sold as set on dotcom and amazon         1
    Water damaged                            1
    incorrectly credited C550456 see 47      1
    reverse previous adjustment              1
    damages/dotcom?                          1
    sold as set/6 by dotcom                  1
    Thrown away-rusty                        1
    damages/credits from ASOS.               1
    cracked                                  1
    samples                                  1
    damages/showroom etc                     1
    adjust                                   1
    wrong code                               1
    wrong code?                              1
    Missing                                  1
    Display                                  1
    DAMAGED                                  1
    POSSIBLE DAMAGES OR LOST?                1
    MERCHANT CHANDLER CREDIT ERROR, STO      1
    mystery! Only ever imported 1800         1
    sold as 22467                            1
    lost                                     1
    Name: count, dtype: int64



As we can see, all description are damanged, checked, lost, smashed, and the missing_descriptions we marked. So we will seperate those rows as damaged_df and export csv as a backup.


```python
# Filter the DataFrame for cancelled invoices
damaged_df = negative_quantity_rows

# Export damaged_df to a CSV file with all columns
damaged_df.to_csv('damaged_df.csv', index=False, columns=damaged_df.columns)
```


```python
# Drop the damaged rows from the main DataFrame
df = df[df['Quantity'] >= 0]

# Reset the index of the updated DataFrame
df.reset_index(drop=True, inplace=True)
```


```python
df.describe()
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
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>UnitPrice</th>
      <th>CustomerID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>531282.000000</td>
      <td>531282</td>
      <td>531282.000000</td>
      <td>531282.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>10.655317</td>
      <td>2011-07-04 18:15:26.858729728</td>
      <td>3.878140</td>
      <td>11455.263062</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>2010-12-01 08:26:00</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.000000</td>
      <td>2011-03-28 11:59:00</td>
      <td>1.250000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3.000000</td>
      <td>2011-07-20 12:01:00</td>
      <td>2.080000</td>
      <td>14375.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>10.000000</td>
      <td>2011-10-19 12:35:00</td>
      <td>4.130000</td>
      <td>16261.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>80995.000000</td>
      <td>2011-12-09 12:50:00</td>
      <td>13541.330000</td>
      <td>18287.000000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>156.830764</td>
      <td>NaN</td>
      <td>32.510663</td>
      <td>6795.268735</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 531282 entries, 0 to 531281
    Data columns (total 8 columns):
     #   Column       Non-Null Count   Dtype         
    ---  ------       --------------   -----         
     0   InvoiceNo    531282 non-null  object        
     1   StockCode    531282 non-null  object        
     2   Description  531282 non-null  object        
     3   Quantity     531282 non-null  int64         
     4   InvoiceDate  531282 non-null  datetime64[ns]
     5   UnitPrice    531282 non-null  float64       
     6   CustomerID   531282 non-null  float64       
     7   Country      531282 non-null  object        
    dtypes: datetime64[ns](1), float64(2), int64(1), object(4)
    memory usage: 32.4+ MB


The summary provide insights for the dataset.

Our DataFrame now has 531,282 rows with 8 columns:

 1   StockCode    531282 non-null  object        
 2   Description  531282 non-null  object        
 3   Quantity     531282 non-null  int64         
 4   InvoiceDate  531282 non-null  datetime64[ns]
 5   UnitPrice    531282 non-null  float64       
 6   CustomerID   531282 non-null  float64       
 7   Country      531282 non-null  object

Quantity: The average quantity is approximately 10.66, with a minimum of 1 and a maximum of 80,995. The standard deviation is 156.83.

InvoiceDate: The earliest invoice date is on December 1, 2010, and the latest is on December 9, 2011.

UnitPrice: The average unit price is approximately 3.88, with a minimum of 0 and a maximum of 13,541.33. The standard deviation is 32.51.

CustomerID: The average customer ID is approximately 11,455.26, with a minimum of 0 and a maximum of 18,287. The standard deviation is 6,795.27.


```python
# Reset the index
df = df.reset_index(drop=True)

print(f"Cleaned_Data:\n{df}")
```

    Cleaned_Data:
           InvoiceNo StockCode                          Description  Quantity   
    0         536365    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6  \
    1         536365     71053                  WHITE METAL LANTERN         6   
    2         536365    84406B       CREAM CUPID HEARTS COAT HANGER         8   
    3         536365    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   
    4         536365    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   
    ...          ...       ...                                  ...       ...   
    531277    581587     22613          PACK OF 20 SPACEBOY NAPKINS        12   
    531278    581587     22899         CHILDREN'S APRON DOLLY GIRL          6   
    531279    581587     23254        CHILDRENS CUTLERY DOLLY GIRL          4   
    531280    581587     23255      CHILDRENS CUTLERY CIRCUS PARADE         4   
    531281    581587     22138        BAKING SET 9 PIECE RETROSPOT          3   
    
                   InvoiceDate  UnitPrice  CustomerID         Country  
    0      2010-12-01 08:26:00       2.55     17850.0  United Kingdom  
    1      2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    2      2010-12-01 08:26:00       2.75     17850.0  United Kingdom  
    3      2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    4      2010-12-01 08:26:00       3.39     17850.0  United Kingdom  
    ...                    ...        ...         ...             ...  
    531277 2011-12-09 12:50:00       0.85     12680.0          France  
    531278 2011-12-09 12:50:00       2.10     12680.0          France  
    531279 2011-12-09 12:50:00       4.15     12680.0          France  
    531280 2011-12-09 12:50:00       4.15     12680.0          France  
    531281 2011-12-09 12:50:00       4.95     12680.0          France  
    
    [531282 rows x 8 columns]


**Title: UCI Online Retail Dataset - Cleaned Version**

Description:

This dataset contains the final cleaned version of the UCI Online Retail Dataset, which has been processed by #EaintKyawtHmu. Aspiring to be a part of the AI/ML field, I have undertaken the task of cleaning the data to make it suitable for analysis and modeling purposes.

The UCI Online Retail Dataset is widely used in the data science community for various research and analysis tasks. However, it is important to note that the copyright for this dataset is owned by UCI, and I do not claim any copyright over it. My role was to assist my coworkers, ML engineers, in ensuring that the data is as clean and reliable as possible.

This cleaned version of the dataset is made available for anyone to use and analyze. I believe in the power of open data and collaboration within the community. Therefore, please feel free to utilize this dataset in your projects, research, or any other endeavors.

By sharing this cleaned dataset, I aim to contribute to the collective effort of improving data quality and fostering advancements in the field of AI/ML. I hope this dataset proves to be a valuable resource for researchers, data scientists, and enthusiasts alike.

Thank you for your interest, and please don't hesitate to reach out if you have any questions or need further assistance.


