```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import matplotlib.ticker as ticker
```


```python
df= pd.read_csv(r'C:\Users\Grace Clinard\OneDrive\Supermarket_sales.csv')
df.head()
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
      <th>Unnamed: 0</th>
      <th>Order ID</th>
      <th>Order Date</th>
      <th>Ship Date</th>
      <th>Ship Mode</th>
      <th>Customer ID</th>
      <th>Customer Name</th>
      <th>Segment</th>
      <th>Country</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Product ID</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Product Name</th>
      <th>Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>CA-2017-152156</td>
      <td>8/11/2017</td>
      <td>11/11/2017</td>
      <td>Second Class</td>
      <td>CG-12520</td>
      <td>Claire Gute</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420.0</td>
      <td>South</td>
      <td>FUR-BO-10001798</td>
      <td>Furniture</td>
      <td>Bookcases</td>
      <td>Bush Somerset Collection Bookcase</td>
      <td>261.9600</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>CA-2017-152156</td>
      <td>8/11/2017</td>
      <td>11/11/2017</td>
      <td>Second Class</td>
      <td>CG-12520</td>
      <td>Claire Gute</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420.0</td>
      <td>South</td>
      <td>FUR-CH-10000454</td>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>Hon Deluxe Fabric Upholstered Stacking Chairs,...</td>
      <td>731.9400</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>CA-2017-138688</td>
      <td>12/6/2017</td>
      <td>16/06/2017</td>
      <td>Second Class</td>
      <td>DV-13045</td>
      <td>Darrin Van Huff</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90036.0</td>
      <td>West</td>
      <td>OFF-LA-10000240</td>
      <td>Office Supplies</td>
      <td>Labels</td>
      <td>Self-Adhesive Address Labels for Typewriters b...</td>
      <td>14.6200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>US-2016-108966</td>
      <td>11/10/2016</td>
      <td>18/10/2016</td>
      <td>Standard Class</td>
      <td>SO-20335</td>
      <td>Sean O'Donnell</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311.0</td>
      <td>South</td>
      <td>FUR-TA-10000577</td>
      <td>Furniture</td>
      <td>Tables</td>
      <td>Bretford CR4500 Series Slim Rectangular Table</td>
      <td>957.5775</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>US-2016-108966</td>
      <td>11/10/2016</td>
      <td>18/10/2016</td>
      <td>Standard Class</td>
      <td>SO-20335</td>
      <td>Sean O'Donnell</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311.0</td>
      <td>South</td>
      <td>OFF-ST-10000760</td>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>Eldon Fold 'N Roll Cart System</td>
      <td>22.3680</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail()
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
      <th>Unnamed: 0</th>
      <th>Order ID</th>
      <th>Order Date</th>
      <th>Ship Date</th>
      <th>Ship Mode</th>
      <th>Customer ID</th>
      <th>Customer Name</th>
      <th>Segment</th>
      <th>Country</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Product ID</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Product Name</th>
      <th>Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9795</th>
      <td>9796</td>
      <td>CA-2017-125920</td>
      <td>21/05/2017</td>
      <td>28/05/2017</td>
      <td>Standard Class</td>
      <td>SH-19975</td>
      <td>Sally Hughsby</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Chicago</td>
      <td>Illinois</td>
      <td>60610.0</td>
      <td>Central</td>
      <td>OFF-BI-10003429</td>
      <td>Office Supplies</td>
      <td>Binders</td>
      <td>Cardinal HOLDit! Binder Insert Strips,Extra St...</td>
      <td>3.798</td>
    </tr>
    <tr>
      <th>9796</th>
      <td>9797</td>
      <td>CA-2016-128608</td>
      <td>12/1/2016</td>
      <td>17/01/2016</td>
      <td>Standard Class</td>
      <td>CS-12490</td>
      <td>Cindy Schnelling</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Toledo</td>
      <td>Ohio</td>
      <td>43615.0</td>
      <td>East</td>
      <td>OFF-AR-10001374</td>
      <td>Office Supplies</td>
      <td>Art</td>
      <td>BIC Brite Liner Highlighters, Chisel Tip</td>
      <td>10.368</td>
    </tr>
    <tr>
      <th>9797</th>
      <td>9798</td>
      <td>CA-2016-128608</td>
      <td>12/1/2016</td>
      <td>17/01/2016</td>
      <td>Standard Class</td>
      <td>CS-12490</td>
      <td>Cindy Schnelling</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Toledo</td>
      <td>Ohio</td>
      <td>43615.0</td>
      <td>East</td>
      <td>TEC-PH-10004977</td>
      <td>Technology</td>
      <td>Phones</td>
      <td>GE 30524EE4</td>
      <td>235.188</td>
    </tr>
    <tr>
      <th>9798</th>
      <td>9799</td>
      <td>CA-2016-128608</td>
      <td>12/1/2016</td>
      <td>17/01/2016</td>
      <td>Standard Class</td>
      <td>CS-12490</td>
      <td>Cindy Schnelling</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Toledo</td>
      <td>Ohio</td>
      <td>43615.0</td>
      <td>East</td>
      <td>TEC-PH-10000912</td>
      <td>Technology</td>
      <td>Phones</td>
      <td>Anker 24W Portable Micro USB Car Charger</td>
      <td>26.376</td>
    </tr>
    <tr>
      <th>9799</th>
      <td>9800</td>
      <td>CA-2016-128608</td>
      <td>12/1/2016</td>
      <td>17/01/2016</td>
      <td>Standard Class</td>
      <td>CS-12490</td>
      <td>Cindy Schnelling</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Toledo</td>
      <td>Ohio</td>
      <td>43615.0</td>
      <td>East</td>
      <td>TEC-AC-10000487</td>
      <td>Technology</td>
      <td>Accessories</td>
      <td>SanDisk Cruzer 4 GB USB Flash Drive</td>
      <td>10.384</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9800 entries, 0 to 9799
    Data columns (total 18 columns):
     #   Column         Non-Null Count  Dtype  
    ---  ------         --------------  -----  
     0   Unnamed: 0     9800 non-null   int64  
     1   Order ID       9800 non-null   object 
     2   Order Date     9800 non-null   object 
     3   Ship Date      9800 non-null   object 
     4   Ship Mode      9800 non-null   object 
     5   Customer ID    9800 non-null   object 
     6   Customer Name  9800 non-null   object 
     7   Segment        9800 non-null   object 
     8   Country        9800 non-null   object 
     9   City           9800 non-null   object 
     10  State          9800 non-null   object 
     11  Postal Code    9789 non-null   float64
     12  Region         9800 non-null   object 
     13  Product ID     9800 non-null   object 
     14  Category       9800 non-null   object 
     15  Sub-Category   9800 non-null   object 
     16  Product Name   9800 non-null   object 
     17  Sales          9800 non-null   float64
    dtypes: float64(2), int64(1), object(15)
    memory usage: 1.3+ MB
    


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
      <th>Unnamed: 0</th>
      <th>Postal Code</th>
      <th>Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>9800.000000</td>
      <td>9789.000000</td>
      <td>9800.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4900.500000</td>
      <td>55273.322403</td>
      <td>230.769059</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2829.160653</td>
      <td>32041.223413</td>
      <td>626.651875</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1040.000000</td>
      <td>0.444000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2450.750000</td>
      <td>23223.000000</td>
      <td>17.248000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>4900.500000</td>
      <td>58103.000000</td>
      <td>54.490000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7350.250000</td>
      <td>90008.000000</td>
      <td>210.605000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>9800.000000</td>
      <td>99301.000000</td>
      <td>22638.480000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.isnull().sum()
```




    Unnamed: 0        0
    Order ID          0
    Order Date        0
    Ship Date         0
    Ship Mode         0
    Customer ID       0
    Customer Name     0
    Segment           0
    Country           0
    City              0
    State             0
    Postal Code      11
    Region            0
    Product ID        0
    Category          0
    Sub-Category      0
    Product Name      0
    Sales             0
    dtype: int64




```python
df.nunique()
```




    Unnamed: 0       9800
    Order ID         4922
    Order Date       1230
    Ship Date        1326
    Ship Mode           4
    Customer ID       793
    Customer Name     793
    Segment             3
    Country             1
    City              529
    State              49
    Postal Code       626
    Region              4
    Product ID       1861
    Category            3
    Sub-Category       17
    Product Name     1849
    Sales            5757
    dtype: int64




```python
df['Order Date'] = pd.to_datetime(df['Order Date'], format= "%d/%m/%Y")
df['Ship Date'] = pd.to_datetime(df['Ship Date'], format= "%d/%m/%Y")
df['Waiting Period'] = (df['Ship Date'] - df['Order Date']).dt.days
column_to_move = df.pop('Waiting Period')
df.insert(4,'Waiting Period', column_to_move)
df.head()
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
      <th>Unnamed: 0</th>
      <th>Order ID</th>
      <th>Order Date</th>
      <th>Ship Date</th>
      <th>Waiting Period</th>
      <th>Ship Mode</th>
      <th>Customer ID</th>
      <th>Customer Name</th>
      <th>Segment</th>
      <th>Country</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Product ID</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Product Name</th>
      <th>Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>CA-2017-152156</td>
      <td>2017-11-08</td>
      <td>2017-11-11</td>
      <td>3</td>
      <td>Second Class</td>
      <td>CG-12520</td>
      <td>Claire Gute</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420.0</td>
      <td>South</td>
      <td>FUR-BO-10001798</td>
      <td>Furniture</td>
      <td>Bookcases</td>
      <td>Bush Somerset Collection Bookcase</td>
      <td>261.9600</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>CA-2017-152156</td>
      <td>2017-11-08</td>
      <td>2017-11-11</td>
      <td>3</td>
      <td>Second Class</td>
      <td>CG-12520</td>
      <td>Claire Gute</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420.0</td>
      <td>South</td>
      <td>FUR-CH-10000454</td>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>Hon Deluxe Fabric Upholstered Stacking Chairs,...</td>
      <td>731.9400</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>CA-2017-138688</td>
      <td>2017-06-12</td>
      <td>2017-06-16</td>
      <td>4</td>
      <td>Second Class</td>
      <td>DV-13045</td>
      <td>Darrin Van Huff</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90036.0</td>
      <td>West</td>
      <td>OFF-LA-10000240</td>
      <td>Office Supplies</td>
      <td>Labels</td>
      <td>Self-Adhesive Address Labels for Typewriters b...</td>
      <td>14.6200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>US-2016-108966</td>
      <td>2016-10-11</td>
      <td>2016-10-18</td>
      <td>7</td>
      <td>Standard Class</td>
      <td>SO-20335</td>
      <td>Sean O'Donnell</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311.0</td>
      <td>South</td>
      <td>FUR-TA-10000577</td>
      <td>Furniture</td>
      <td>Tables</td>
      <td>Bretford CR4500 Series Slim Rectangular Table</td>
      <td>957.5775</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>US-2016-108966</td>
      <td>2016-10-11</td>
      <td>2016-10-18</td>
      <td>7</td>
      <td>Standard Class</td>
      <td>SO-20335</td>
      <td>Sean O'Donnell</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311.0</td>
      <td>South</td>
      <td>OFF-ST-10000760</td>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>Eldon Fold 'N Roll Cart System</td>
      <td>22.3680</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = df.drop(['Country', 'Unnamed: 0'], axis=1)
```


```python
df = df.set_index('Order ID')
```


```python
df['Order Year']= df['Order Date'].dt.year
df.head()
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
      <th>Order Date</th>
      <th>Ship Date</th>
      <th>Waiting Period</th>
      <th>Ship Mode</th>
      <th>Customer ID</th>
      <th>Customer Name</th>
      <th>Segment</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Product ID</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Product Name</th>
      <th>Sales</th>
      <th>Order Year</th>
    </tr>
    <tr>
      <th>Order ID</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>CA-2017-152156</th>
      <td>2017-11-08</td>
      <td>2017-11-11</td>
      <td>3</td>
      <td>Second Class</td>
      <td>CG-12520</td>
      <td>Claire Gute</td>
      <td>Consumer</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420.0</td>
      <td>South</td>
      <td>FUR-BO-10001798</td>
      <td>Furniture</td>
      <td>Bookcases</td>
      <td>Bush Somerset Collection Bookcase</td>
      <td>261.9600</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>CA-2017-152156</th>
      <td>2017-11-08</td>
      <td>2017-11-11</td>
      <td>3</td>
      <td>Second Class</td>
      <td>CG-12520</td>
      <td>Claire Gute</td>
      <td>Consumer</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420.0</td>
      <td>South</td>
      <td>FUR-CH-10000454</td>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>Hon Deluxe Fabric Upholstered Stacking Chairs,...</td>
      <td>731.9400</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>CA-2017-138688</th>
      <td>2017-06-12</td>
      <td>2017-06-16</td>
      <td>4</td>
      <td>Second Class</td>
      <td>DV-13045</td>
      <td>Darrin Van Huff</td>
      <td>Corporate</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90036.0</td>
      <td>West</td>
      <td>OFF-LA-10000240</td>
      <td>Office Supplies</td>
      <td>Labels</td>
      <td>Self-Adhesive Address Labels for Typewriters b...</td>
      <td>14.6200</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>US-2016-108966</th>
      <td>2016-10-11</td>
      <td>2016-10-18</td>
      <td>7</td>
      <td>Standard Class</td>
      <td>SO-20335</td>
      <td>Sean O'Donnell</td>
      <td>Consumer</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311.0</td>
      <td>South</td>
      <td>FUR-TA-10000577</td>
      <td>Furniture</td>
      <td>Tables</td>
      <td>Bretford CR4500 Series Slim Rectangular Table</td>
      <td>957.5775</td>
      <td>2016</td>
    </tr>
    <tr>
      <th>US-2016-108966</th>
      <td>2016-10-11</td>
      <td>2016-10-18</td>
      <td>7</td>
      <td>Standard Class</td>
      <td>SO-20335</td>
      <td>Sean O'Donnell</td>
      <td>Consumer</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311.0</td>
      <td>South</td>
      <td>OFF-ST-10000760</td>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>Eldon Fold 'N Roll Cart System</td>
      <td>22.3680</td>
      <td>2016</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.heatmap(df.corr(), annot = True)

plt.show()
```

    C:\Users\Grace Clinard\AppData\Local\Temp\ipykernel_27500\2121288392.py:1: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.
      sns.heatmap(df.corr(), annot = True)
    


    
![png](output_11_1.png)
    


Which Region yields the most Sales?


```python
df2 = df.groupby('Region').sum('Sales')
df2 = df2.drop(['Order Year','Postal Code','Waiting Period'], axis = 1)
df2 = df2.sort_values(['Sales'], ascending=False)
df2
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
      <th>Sales</th>
    </tr>
    <tr>
      <th>Region</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>West</th>
      <td>710219.6845</td>
    </tr>
    <tr>
      <th>East</th>
      <td>669518.7260</td>
    </tr>
    <tr>
      <th>Central</th>
      <td>492646.9132</td>
    </tr>
    <tr>
      <th>South</th>
      <td>389151.4590</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.plot(kind = 'bar')
```




    <Axes: xlabel='Region'>




    
![png](output_14_1.png)
    


Which years have been the best/worst in regards to sales?


```python
df3 = df.groupby('Order Year')[df.columns[15:16]].sum('Sales')
df3
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
      <th>Sales</th>
    </tr>
    <tr>
      <th>Order Year</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2015</th>
      <td>479856.2081</td>
    </tr>
    <tr>
      <th>2016</th>
      <td>459436.0054</td>
    </tr>
    <tr>
      <th>2017</th>
      <td>600192.5500</td>
    </tr>
    <tr>
      <th>2018</th>
      <td>722052.0192</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns
```




    Index(['Order Date', 'Ship Date', 'Waiting Period', 'Ship Mode', 'Customer ID',
           'Customer Name', 'Segment', 'City', 'State', 'Postal Code', 'Region',
           'Product ID', 'Category', 'Sub-Category', 'Product Name', 'Sales',
           'Order Year'],
          dtype='object')




```python
df3.plot()
```




    <Axes: xlabel='Order Year'>




    
![png](output_18_1.png)
    


Which year/months have been our best/worst in regards to Sales volume?


```python
state_sales = df.groupby(['State'])['Sales'].sum()

print(state_sales)
```

    State
    Alabama                  19510.6400
    Arizona                  35272.6570
    Arkansas                 11678.1300
    California              446306.4635
    Colorado                 31841.5980
    Connecticut              13384.3570
    Delaware                 27322.9990
    District of Columbia      2865.0200
    Florida                  88436.5320
    Georgia                  48219.1100
    Idaho                     4382.4860
    Illinois                 79236.5170
    Indiana                  48718.4000
    Iowa                      4443.5600
    Kansas                    2914.3100
    Kentucky                 36458.3900
    Louisiana                 9131.0500
    Maine                     1270.5300
    Maryland                 23705.5230
    Massachusetts            28634.4340
    Michigan                 76136.0740
    Minnesota                29863.1500
    Mississippi              10771.3400
    Missouri                 22205.1500
    Montana                   5589.3520
    Nebraska                  7464.9300
    Nevada                   16729.1020
    New Hampshire             7292.5240
    New Jersey               34610.9720
    New Mexico                4783.5220
    New York                306361.1470
    North Carolina           55165.9640
    North Dakota               919.9100
    Ohio                     75130.3500
    Oklahoma                 19683.3900
    Oregon                   17284.4620
    Pennsylvania            116276.6500
    Rhode Island             22525.0260
    South Carolina            8481.7100
    South Dakota              1315.5600
    Tennessee                30661.8730
    Texas                   168572.5322
    Utah                     11220.0560
    Vermont                   8929.3700
    Virginia                 70636.7200
    Washington              135206.8500
    West Virginia             1209.8240
    Wisconsin                31173.4300
    Wyoming                   1603.1360
    Name: Sales, dtype: float64
    


```python
state_sales.plot(kind = 'bar')
```




    <Axes: xlabel='State'>




    
![png](output_21_1.png)
    



```python
df['Order Year'].info()
```

    <class 'pandas.core.series.Series'>
    Index: 9800 entries, CA-2017-152156 to CA-2016-128608
    Series name: Order Year
    Non-Null Count  Dtype
    --------------  -----
    9800 non-null   int64
    dtypes: int64(1)
    memory usage: 153.1+ KB
    


```python
state_sales = df.groupby('State')['Sales'].sum()

print(state_sales)
```

    State
    Alabama                  19510.6400
    Arizona                  35272.6570
    Arkansas                 11678.1300
    California              446306.4635
    Colorado                 31841.5980
    Connecticut              13384.3570
    Delaware                 27322.9990
    District of Columbia      2865.0200
    Florida                  88436.5320
    Georgia                  48219.1100
    Idaho                     4382.4860
    Illinois                 79236.5170
    Indiana                  48718.4000
    Iowa                      4443.5600
    Kansas                    2914.3100
    Kentucky                 36458.3900
    Louisiana                 9131.0500
    Maine                     1270.5300
    Maryland                 23705.5230
    Massachusetts            28634.4340
    Michigan                 76136.0740
    Minnesota                29863.1500
    Mississippi              10771.3400
    Missouri                 22205.1500
    Montana                   5589.3520
    Nebraska                  7464.9300
    Nevada                   16729.1020
    New Hampshire             7292.5240
    New Jersey               34610.9720
    New Mexico                4783.5220
    New York                306361.1470
    North Carolina           55165.9640
    North Dakota               919.9100
    Ohio                     75130.3500
    Oklahoma                 19683.3900
    Oregon                   17284.4620
    Pennsylvania            116276.6500
    Rhode Island             22525.0260
    South Carolina            8481.7100
    South Dakota              1315.5600
    Tennessee                30661.8730
    Texas                   168572.5322
    Utah                     11220.0560
    Vermont                   8929.3700
    Virginia                 70636.7200
    Washington              135206.8500
    West Virginia             1209.8240
    Wisconsin                31173.4300
    Wyoming                   1603.1360
    Name: Sales, dtype: float64
    
