# Exercise 3. - GroupBy

### Introduction:

GroupBy can be summarized as Split-Apply-Combine.

Special thanks to: https://github.com/justmarkham for sharing the dataset and materials.

Check out this [Diagram](http://i.imgur.com/yjNkiwL.png)  

Check out [Alcohol Consumption Exercises Video Tutorial](https://youtu.be/az67CMdmS6s) to watch a data scientist go through the exercises


### Step 1. Import the necessary libraries


```python
import pandas as pd
```

### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/justmarkham/DAT8/master/data/drinks.csv). 

### Step 3. Assign it to a variable called drinks.


```python
drinks = pd.read_csv('https://raw.githubusercontent.com/justmarkham/DAT8/master/data/drinks.csv')
print(drinks)
```

             country  beer_servings  spirit_servings  wine_servings  \
    0    Afghanistan              0                0              0   
    1        Albania             89              132             54   
    2        Algeria             25                0             14   
    3        Andorra            245              138            312   
    4         Angola            217               57             45   
    ..           ...            ...              ...            ...   
    188    Venezuela            333              100              3   
    189      Vietnam            111                2              1   
    190        Yemen              6                0              0   
    191       Zambia             32               19              4   
    192     Zimbabwe             64               18              4   
    
         total_litres_of_pure_alcohol continent  
    0                             0.0        AS  
    1                             4.9        EU  
    2                             0.7        AF  
    3                            12.4        EU  
    4                             5.9        AF  
    ..                            ...       ...  
    188                           7.7        SA  
    189                           2.0        AS  
    190                           0.1        AS  
    191                           2.5        AF  
    192                           4.7        AF  
    
    [193 rows x 6 columns]
    

### Step 4. Which continent drinks more beer on average?


```python
print(drinks[['continent','beer_servings']].groupby(['continent']).sum().sort_values('beer_servings').tail(1))

```

               beer_servings
    continent               
    EU                  8720
    

### Step 5. For each continent print the statistics for wine consumption.


```python
print(drinks[['continent','wine_servings']].groupby(['continent']).sum())
```

               wine_servings
    continent               
    AF                   862
    AS                   399
    EU                  6400
    OC                   570
    SA                   749
    

### Step 6. Print the mean alcohol consumption per continent for every column


```python
print(drinks[['continent', 'beer_servings', 'spirit_servings', 'wine_servings', 'total_litres_of_pure_alcohol']].groupby(['continent']).mean())
```

               beer_servings  spirit_servings  wine_servings  \
    continent                                                  
    AF             61.471698        16.339623      16.264151   
    AS             37.045455        60.840909       9.068182   
    EU            193.777778       132.555556     142.222222   
    OC             89.687500        58.437500      35.625000   
    SA            175.083333       114.750000      62.416667   
    
               total_litres_of_pure_alcohol  
    continent                                
    AF                             3.007547  
    AS                             2.170455  
    EU                             8.617778  
    OC                             3.381250  
    SA                             6.308333  
    

### Step 7. Print the median alcohol consumption per continent for every column


```python
print(drinks[['continent', 'beer_servings', 'spirit_servings', 'wine_servings', 'total_litres_of_pure_alcohol']].groupby(['continent']).median())
```

               beer_servings  spirit_servings  wine_servings  \
    continent                                                  
    AF                  32.0              3.0            2.0   
    AS                  17.5             16.0            1.0   
    EU                 219.0            122.0          128.0   
    OC                  52.5             37.0            8.5   
    SA                 162.5            108.5           12.0   
    
               total_litres_of_pure_alcohol  
    continent                                
    AF                                 2.30  
    AS                                 1.20  
    EU                                10.00  
    OC                                 1.75  
    SA                                 6.85  
    

### Step 8. Print the mean, min and max values for spirit consumption.
#### This time output a DataFrame


```python
drinks.groupby('continent').spirit_servings.agg(['mean', 'min', 'max'])
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
      <th>mean</th>
      <th>min</th>
      <th>max</th>
    </tr>
    <tr>
      <th>continent</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>AF</th>
      <td>16.339623</td>
      <td>0</td>
      <td>152</td>
    </tr>
    <tr>
      <th>AS</th>
      <td>60.840909</td>
      <td>0</td>
      <td>326</td>
    </tr>
    <tr>
      <th>EU</th>
      <td>132.555556</td>
      <td>0</td>
      <td>373</td>
    </tr>
    <tr>
      <th>OC</th>
      <td>58.437500</td>
      <td>0</td>
      <td>254</td>
    </tr>
    <tr>
      <th>SA</th>
      <td>114.750000</td>
      <td>25</td>
      <td>302</td>
    </tr>
  </tbody>
</table>
</div>


