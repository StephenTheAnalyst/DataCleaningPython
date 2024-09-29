## In this project, i tried to pratice my data cleaning ability. This would serve as my very first attempt at cleaning data with python.... This file is a list of customers with thier choice on wether to be contacted or not. So i tried to clean it and shortlisted to those customers that don't mind being contacted..


```python
import pandas as pd
import matplotlib.pyplot as plt
```


```python
df = pd.read_excel(r"C:\Users\Ajewo\Downloads\Customer Call List.xlsx")
df
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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
      <th>Not_Useful_Column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>123/643/9775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>/White</td>
      <td>7066950392</td>
      <td>298 Drugs Driveway</td>
      <td>N</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>123-543-2345</td>
      <td>980 Paper Avenue, Pennsylvania, 18503</td>
      <td>Yes</td>
      <td>Y</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876|678|3469</td>
      <td>123 Dragons Road</td>
      <td>Y</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>Ron</td>
      <td>Swanson</td>
      <td>304-762-2467</td>
      <td>768 City Parkway</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>NaN</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876|678|3469</td>
      <td>98 Clue Drive</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>N/a</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>False</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street, New York</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>NaN</td>
      <td>612 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>...Potter</td>
      <td>7066950392</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876|678|3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson_</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123/643/9775</td>
      <td>121 Paper Avenue, Pennsylvania</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>7066950392</td>
      <td>3498 Super Lane</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1019</td>
      <td>Creed</td>
      <td>Braton</td>
      <td>N/a</td>
      <td>N/a</td>
      <td>N/a</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876|678|3469</td>
      <td>910 Tatooine Road, Tatooine</td>
      <td>Yes</td>
      <td>N</td>
      <td>True</td>
    </tr>
    <tr>
      <th>20</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876|678|3469</td>
      <td>910 Tatooine Road, Tatooine</td>
      <td>Yes</td>
      <td>N</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## I noticed number 19 was duplicated as 20, so i dropped number 20..


```python
df = df.drop_duplicates()
df
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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
      <th>Not_Useful_Column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>123/643/9775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>/White</td>
      <td>7066950392</td>
      <td>298 Drugs Driveway</td>
      <td>N</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>123-543-2345</td>
      <td>980 Paper Avenue, Pennsylvania, 18503</td>
      <td>Yes</td>
      <td>Y</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876|678|3469</td>
      <td>123 Dragons Road</td>
      <td>Y</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>Ron</td>
      <td>Swanson</td>
      <td>304-762-2467</td>
      <td>768 City Parkway</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>NaN</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876|678|3469</td>
      <td>98 Clue Drive</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>N/a</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>False</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street, New York</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>NaN</td>
      <td>612 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>...Potter</td>
      <td>7066950392</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876|678|3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson_</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123/643/9775</td>
      <td>121 Paper Avenue, Pennsylvania</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>7066950392</td>
      <td>3498 Super Lane</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1019</td>
      <td>Creed</td>
      <td>Braton</td>
      <td>N/a</td>
      <td>N/a</td>
      <td>N/a</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876|678|3469</td>
      <td>910 Tatooine Road, Tatooine</td>
      <td>Yes</td>
      <td>N</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## I noticed some last names had additional character at the end or beginning. I decided to stripe them off...


```python
df['Last_Name'] = df.Last_Name.str.lstrip('...')
df['Last_Name'] = df.Last_Name.str.lstrip('/')
df['Last_Name'] = df.Last_Name.str.rstrip('_')
df.head(5)
```

    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\2022115383.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df['Last_Name'] = df.Last_Name.str.lstrip('...')
    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\2022115383.py:2: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df['Last_Name'] = df.Last_Name.str.lstrip('/')
    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\2022115383.py:3: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df['Last_Name'] = df.Last_Name.str.rstrip('_')
    




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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
      <th>Not_Useful_Column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>123/643/9775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>White</td>
      <td>7066950392</td>
      <td>298 Drugs Driveway</td>
      <td>N</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>123-543-2345</td>
      <td>980 Paper Avenue, Pennsylvania, 18503</td>
      <td>Yes</td>
      <td>Y</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876|678|3469</td>
      <td>123 Dragons Road</td>
      <td>Y</td>
      <td>No</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



### The phone numbers weren't standardized. Some were having '-' while some had '/', i would need to make all in the same format. This took awhile, but i finally did it...


```python
df.Phone_Number = df.Phone_Number.str.replace('-','')
df.Phone_Number = df.Phone_Number.str.replace('N/a',' ')
df.Phone_Number = df.Phone_Number.str.replace('/','')
df.Phone_Number = df.Phone_Number.str.replace('|','')
df
```

    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\613324680.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.Phone_Number = df.Phone_Number.str.replace('-','')
    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\613324680.py:2: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.Phone_Number = df.Phone_Number.str.replace('N/a',' ')
    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\613324680.py:3: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.Phone_Number = df.Phone_Number.str.replace('/','')
    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\613324680.py:4: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.Phone_Number = df.Phone_Number.str.replace('|','')
    




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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
      <th>Not_Useful_Column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>1235455421</td>
      <td>123 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>1236439775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>White</td>
      <td>NaN</td>
      <td>298 Drugs Driveway</td>
      <td>N</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>1235432345</td>
      <td>980 Paper Avenue, Pennsylvania, 18503</td>
      <td>Yes</td>
      <td>Y</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>8766783469</td>
      <td>123 Dragons Road</td>
      <td>Y</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>Ron</td>
      <td>Swanson</td>
      <td>3047622467</td>
      <td>768 City Parkway</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>NaN</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>8766783469</td>
      <td>98 Clue Drive</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td></td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>False</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>1235455421</td>
      <td>25th Main Street, New York</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>NaN</td>
      <td>612 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>Potter</td>
      <td>NaN</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>1235432345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>8766783469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>3047622467</td>
      <td>214 HR Avenue</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>1235455421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>1236439775</td>
      <td>121 Paper Avenue, Pennsylvania</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>NaN</td>
      <td>3498 Super Lane</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1019</td>
      <td>Creed</td>
      <td>Braton</td>
      <td></td>
      <td>N/a</td>
      <td>N/a</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>8766783469</td>
      <td>910 Tatooine Road, Tatooine</td>
      <td>Yes</td>
      <td>N</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.Phone_Number = df.Phone_Number.astype('string')
df.Phone_Number = df.Phone_Number.fillna('')
df.Phone_Number = df.Phone_Number.apply(lambda x: x[0:3] + '-'+ x[3:6] + '-' + x[6:10])
```

    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\589375295.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.Phone_Number = df.Phone_Number.astype('string')
    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\589375295.py:2: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.Phone_Number = df.Phone_Number.fillna('')
    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\589375295.py:3: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.Phone_Number = df.Phone_Number.apply(lambda x: x[0:3] + '-'+ x[3:6] + '-' + x[6:10])
    


```python
df
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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
      <th>Not_Useful_Column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>123-643-9775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>White</td>
      <td>--</td>
      <td>298 Drugs Driveway</td>
      <td>N</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>123-543-2345</td>
      <td>980 Paper Avenue, Pennsylvania, 18503</td>
      <td>Yes</td>
      <td>Y</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876-678-3469</td>
      <td>123 Dragons Road</td>
      <td>Y</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>Ron</td>
      <td>Swanson</td>
      <td>304-762-2467</td>
      <td>768 City Parkway</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>--</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876-678-3469</td>
      <td>98 Clue Drive</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>--</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>False</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street, New York</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>--</td>
      <td>612 Shire Lane, Shire</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>Potter</td>
      <td>--</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876-678-3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123-643-9775</td>
      <td>121 Paper Avenue, Pennsylvania</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>--</td>
      <td>3498 Super Lane</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1019</td>
      <td>Creed</td>
      <td>Braton</td>
      <td>--</td>
      <td>N/a</td>
      <td>N/a</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876-678-3469</td>
      <td>910 Tatooine Road, Tatooine</td>
      <td>Yes</td>
      <td>N</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## Some address had some additional information like zip code and what not.I decided to keep only the street name...


```python
df. Address = df.Address.str.split(',', expand = True)[0]
df
```

    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\969517268.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df. Address = df.Address.str.split(',', expand = True)[0]
    




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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
      <th>Not_Useful_Column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>123-643-9775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>White</td>
      <td>--</td>
      <td>298 Drugs Driveway</td>
      <td>N</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>123-543-2345</td>
      <td>980 Paper Avenue</td>
      <td>Yes</td>
      <td>Y</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876-678-3469</td>
      <td>123 Dragons Road</td>
      <td>Y</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>Ron</td>
      <td>Swanson</td>
      <td>304-762-2467</td>
      <td>768 City Parkway</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>--</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876-678-3469</td>
      <td>98 Clue Drive</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>--</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>False</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>--</td>
      <td>612 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>Potter</td>
      <td>--</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876-678-3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>N</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123-643-9775</td>
      <td>121 Paper Avenue</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>--</td>
      <td>3498 Super Lane</td>
      <td>Y</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1019</td>
      <td>Creed</td>
      <td>Braton</td>
      <td>--</td>
      <td>N/a</td>
      <td>N/a</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876-678-3469</td>
      <td>910 Tatooine Road</td>
      <td>Yes</td>
      <td>N</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



### Here, I wanted to standardize the answers the customer gave for 'Paying Customer', but replace wasn't doing the job okay, so i decided to use map.... 


```python
df['Paying Customer'] = df['Paying Customer'].map({'No': 'No','Yes': 'Yes','N': 'No','Y': 'Yes'})
df
```

    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\4244845362.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df['Paying Customer'] = df['Paying Customer'].map({'No': 'No','Yes': 'Yes','N': 'No','Y': 'Yes'})
    




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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
      <th>Not_Useful_Column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>123-643-9775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>White</td>
      <td>--</td>
      <td>298 Drugs Driveway</td>
      <td>No</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>123-543-2345</td>
      <td>980 Paper Avenue</td>
      <td>Yes</td>
      <td>Y</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876-678-3469</td>
      <td>123 Dragons Road</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>Ron</td>
      <td>Swanson</td>
      <td>304-762-2467</td>
      <td>768 City Parkway</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>--</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876-678-3469</td>
      <td>98 Clue Drive</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>--</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>False</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>--</td>
      <td>612 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>Potter</td>
      <td>--</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876-678-3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>N</td>
      <td>False</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123-643-9775</td>
      <td>121 Paper Avenue</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>--</td>
      <td>3498 Super Lane</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1019</td>
      <td>Creed</td>
      <td>Braton</td>
      <td>--</td>
      <td>N/a</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876-678-3469</td>
      <td>910 Tatooine Road</td>
      <td>Yes</td>
      <td>N</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## Standardizing the 'Do_Not_Contact' column was easy given it is the same issue as the one above, so i just copied and pasted, and switched the names :)


```python
df['Do_Not_Contact'] = df['Do_Not_Contact'].map({'No': 'No','Yes': 'Yes','N': 'No','Y': 'Yes'})
df
```

    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\594505581.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df['Do_Not_Contact'] = df['Do_Not_Contact'].map({'No': 'No','Yes': 'Yes','N': 'No','Y': 'Yes'})
    




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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
      <th>Not_Useful_Column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>123-643-9775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>White</td>
      <td>--</td>
      <td>298 Drugs Driveway</td>
      <td>No</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>123-543-2345</td>
      <td>980 Paper Avenue</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876-678-3469</td>
      <td>123 Dragons Road</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>Ron</td>
      <td>Swanson</td>
      <td>304-762-2467</td>
      <td>768 City Parkway</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>--</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876-678-3469</td>
      <td>98 Clue Drive</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>--</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>False</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>--</td>
      <td>612 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>Potter</td>
      <td>--</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876-678-3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123-643-9775</td>
      <td>121 Paper Avenue</td>
      <td>Yes</td>
      <td>No</td>
      <td>False</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>--</td>
      <td>3498 Super Lane</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1019</td>
      <td>Creed</td>
      <td>Braton</td>
      <td>--</td>
      <td>N/a</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876-678-3469</td>
      <td>910 Tatooine Road</td>
      <td>Yes</td>
      <td>No</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## I decided to drop the 'Not_Useful_Column' column


```python
df.drop(columns = 'Not_Useful_Column', inplace = True )
```

    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\2939274843.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.drop(columns = 'Not_Useful_Column', inplace = True )
    


```python
df
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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>Abed</td>
      <td>Nadir</td>
      <td>123-643-9775</td>
      <td>93 West Main Street</td>
      <td>No</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>White</td>
      <td>--</td>
      <td>298 Drugs Driveway</td>
      <td>No</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>Dwight</td>
      <td>Schrute</td>
      <td>123-543-2345</td>
      <td>980 Paper Avenue</td>
      <td>Yes</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876-678-3469</td>
      <td>123 Dragons Road</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>Ron</td>
      <td>Swanson</td>
      <td>304-762-2467</td>
      <td>768 City Parkway</td>
      <td>Yes</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>--</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876-678-3469</td>
      <td>98 Clue Drive</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>--</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>--</td>
      <td>612 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>Potter</td>
      <td>--</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Yes</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876-678-3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123-643-9775</td>
      <td>121 Paper Avenue</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>--</td>
      <td>3498 Super Lane</td>
      <td>Yes</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1019</td>
      <td>Creed</td>
      <td>Braton</td>
      <td>--</td>
      <td>N/a</td>
      <td>NaN</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876-678-3469</td>
      <td>910 Tatooine Road</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
</div>



## Now, It was time to shortlist the list.. I created another variable and assinged it to the customers that don't mind being contacted.


```python
df2 = df[~(df['Do_Not_Contact'] == 'Yes')]
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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>Walter</td>
      <td>White</td>
      <td>--</td>
      <td>298 Drugs Driveway</td>
      <td>No</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876-678-3469</td>
      <td>123 Dragons Road</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>Jeff</td>
      <td>Winger</td>
      <td>--</td>
      <td>1209 South Street</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876-678-3469</td>
      <td>98 Clue Drive</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>--</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1011</td>
      <td>Samwise</td>
      <td>Gamgee</td>
      <td>--</td>
      <td>612 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1012</td>
      <td>Harry</td>
      <td>Potter</td>
      <td>--</td>
      <td>2394 Hogwarts Avenue</td>
      <td>Yes</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876-678-3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123-643-9775</td>
      <td>121 Paper Avenue</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1018</td>
      <td>Clark</td>
      <td>Kent</td>
      <td>--</td>
      <td>3498 Super Lane</td>
      <td>Yes</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876-678-3469</td>
      <td>910 Tatooine Road</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = df2[~(df2.Phone_Number == '--')]
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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876-678-3469</td>
      <td>123 Dragons Road</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876-678-3469</td>
      <td>98 Clue Drive</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1009</td>
      <td>Gandalf</td>
      <td>NaN</td>
      <td>--</td>
      <td>123 Middle Earth</td>
      <td>Yes</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876-678-3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123-643-9775</td>
      <td>121 Paper Avenue</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876-678-3469</td>
      <td>910 Tatooine Road</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.drop( index = 8, inplace = True)
```

    C:\Users\Ajewo\AppData\Local\Temp\ipykernel_8404\244168511.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df2.drop( index = 8, inplace = True)
    

## Then I finally reset the index so as not to confuse who is reading this :)


```python
df2.reset_index(drop = True, inplace = True)
```


```python
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
      <th>CustomerID</th>
      <th>First_Name</th>
      <th>Last_Name</th>
      <th>Phone_Number</th>
      <th>Address</th>
      <th>Paying Customer</th>
      <th>Do_Not_Contact</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>Frodo</td>
      <td>Baggins</td>
      <td>123-545-5421</td>
      <td>123 Shire Lane</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1005</td>
      <td>Jon</td>
      <td>Snow</td>
      <td>876-678-3469</td>
      <td>123 Dragons Road</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1008</td>
      <td>Sherlock</td>
      <td>Holmes</td>
      <td>876-678-3469</td>
      <td>98 Clue Drive</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1010</td>
      <td>Peter</td>
      <td>Parker</td>
      <td>123-545-5421</td>
      <td>25th Main Street</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1013</td>
      <td>Don</td>
      <td>Draper</td>
      <td>123-543-2345</td>
      <td>2039 Main Street</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1014</td>
      <td>Leslie</td>
      <td>Knope</td>
      <td>876-678-3469</td>
      <td>343 City Parkway</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1015</td>
      <td>Toby</td>
      <td>Flenderson</td>
      <td>304-762-2467</td>
      <td>214 HR Avenue</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1016</td>
      <td>Ron</td>
      <td>Weasley</td>
      <td>123-545-5421</td>
      <td>2395 Hogwarts Avenue</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1017</td>
      <td>Michael</td>
      <td>Scott</td>
      <td>123-643-9775</td>
      <td>121 Paper Avenue</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1020</td>
      <td>Anakin</td>
      <td>Skywalker</td>
      <td>876-678-3469</td>
      <td>910 Tatooine Road</td>
      <td>Yes</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
