# Exercise 2. - Filtering and Sorting Data

Check out [Euro 12 Exercises Video Tutorial](https://youtu.be/iqk5d48Qisg) to watch a data scientist go through the exercises

This time we are going to pull data directly from the internet.

### Step 1. Import the necessary libraries


```python
import pandas as pd
```

### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/kflisikowsky/pandas_exercises/refs/heads/main/Euro_2012_stats_TEAM.csv). 

### Step 3. Assign it to a variable called euro12.


```python
euro12 = pd.read_csv('Euro_2012_stats_TEAM.csv')
print(euro12)
```

                       Team  Goals  Shots on target  Shots off target  \
    0               Croatia      4               13                12   
    1        Czech Republic      4               13                18   
    2               Denmark      4               10                10   
    3               England      5               11                18   
    4                France      3               22                24   
    5               Germany     10               32                32   
    6                Greece      5                8                18   
    7                 Italy      6               34                45   
    8           Netherlands      2               12                36   
    9                Poland      2               15                23   
    10             Portugal      6               22                42   
    11  Republic of Ireland      1                7                12   
    12               Russia      5                9                31   
    13                Spain     12               42                33   
    14               Sweden      5               17                19   
    15              Ukraine      2                7                26   
    
       Shooting Accuracy % Goals-to-shots  Total shots (inc. Blocked)  \
    0              51.9%            16.0%                          32   
    1              41.9%            12.9%                          39   
    2              50.0%            20.0%                          27   
    3              50.0%            17.2%                          40   
    4              37.9%             6.5%                          65   
    5              47.8%            15.6%                          80   
    6              30.7%            19.2%                          32   
    7              43.0%             7.5%                         110   
    8              25.0%             4.1%                          60   
    9              39.4%             5.2%                          48   
    10             34.3%             9.3%                          82   
    11             36.8%             5.2%                          28   
    12             22.5%            12.5%                          59   
    13             55.9%            16.0%                         100   
    14             47.2%            13.8%                          39   
    15             21.2%             6.0%                          38   
    
        Hit Woodwork  Penalty goals  Penalties not scored  ...  Saves made  \
    0              0              0                     0  ...          13   
    1              0              0                     0  ...           9   
    2              1              0                     0  ...          10   
    3              0              0                     0  ...          22   
    4              1              0                     0  ...           6   
    5              2              1                     0  ...          10   
    6              1              1                     1  ...          13   
    7              2              0                     0  ...          20   
    8              2              0                     0  ...          12   
    9              0              0                     0  ...           6   
    10             6              0                     0  ...          10   
    11             0              0                     0  ...          17   
    12             2              0                     0  ...          10   
    13             0              1                     0  ...          15   
    14             3              0                     0  ...           8   
    15             0              0                     0  ...          13   
    
        Saves-to-shots ratio  Fouls Won Fouls Conceded  Offsides  Yellow Cards  \
    0                  81.3%         41             62         2             9   
    1                  60.1%         53             73         8             7   
    2                  66.7%         25             38         8             4   
    3                  88.1%         43             45         6             5   
    4                  54.6%         36             51         5             6   
    5                  62.6%         63             49        12             4   
    6                  65.1%         67             48        12             9   
    7                  74.1%        101             89        16            16   
    8                  70.6%         35             30         3             5   
    9                  66.7%         48             56         3             7   
    10                 71.5%         73             90        10            12   
    11                 65.4%         43             51        11             6   
    12                 77.0%         34             43         4             6   
    13                 93.8%        102             83        19            11   
    14                 61.6%         35             51         7             7   
    15                 76.5%         48             31         4             5   
    
        Red Cards  Subs on  Subs off  Players Used  
    0           0        9         9            16  
    1           0       11        11            19  
    2           0        7         7            15  
    3           0       11        11            16  
    4           0       11        11            19  
    5           0       15        15            17  
    6           1       12        12            20  
    7           0       18        18            19  
    8           0        7         7            15  
    9           1        7         7            17  
    10          0       14        14            16  
    11          1       10        10            17  
    12          0        7         7            16  
    13          0       17        17            18  
    14          0        9         9            18  
    15          0        9         9            18  
    
    [16 rows x 35 columns]
    

### Step 4. Select only the Goal column.


```python
goals = euro12['Goals']
print(goals)
```

    0      4
    1      4
    2      4
    3      5
    4      3
    5     10
    6      5
    7      6
    8      2
    9      2
    10     6
    11     1
    12     5
    13    12
    14     5
    15     2
    Name: Goals, dtype: int64
    

### Step 5. How many team participated in the Euro2012?


```python
print(euro12.shape[0])
```

    16
    

### Step 6. What is the number of columns in the dataset?


```python
print(euro12.shape[1])
```

    35
    

### Step 7. View only the columns Team, Yellow Cards and Red Cards and assign them to a dataframe called discipline


```python
discipline = euro12[['Team','Yellow Cards','Red Cards']]
print(discipline)
```

                       Team  Yellow Cards  Red Cards
    0               Croatia             9          0
    1        Czech Republic             7          0
    2               Denmark             4          0
    3               England             5          0
    4                France             6          0
    5               Germany             4          0
    6                Greece             9          1
    7                 Italy            16          0
    8           Netherlands             5          0
    9                Poland             7          1
    10             Portugal            12          0
    11  Republic of Ireland             6          1
    12               Russia             6          0
    13                Spain            11          0
    14               Sweden             7          0
    15              Ukraine             5          0
    

### Step 8. Sort the teams by Red Cards, then to Yellow Cards


```python
print(euro12.sort_values(by=['Red Cards','Yellow Cards']))
```

                       Team  Goals  Shots on target  Shots off target  \
    2               Denmark      4               10                10   
    5               Germany     10               32                32   
    3               England      5               11                18   
    8           Netherlands      2               12                36   
    15              Ukraine      2                7                26   
    4                France      3               22                24   
    12               Russia      5                9                31   
    1        Czech Republic      4               13                18   
    14               Sweden      5               17                19   
    0               Croatia      4               13                12   
    13                Spain     12               42                33   
    10             Portugal      6               22                42   
    7                 Italy      6               34                45   
    11  Republic of Ireland      1                7                12   
    9                Poland      2               15                23   
    6                Greece      5                8                18   
    
       Shooting Accuracy % Goals-to-shots  Total shots (inc. Blocked)  \
    2              50.0%            20.0%                          27   
    5              47.8%            15.6%                          80   
    3              50.0%            17.2%                          40   
    8              25.0%             4.1%                          60   
    15             21.2%             6.0%                          38   
    4              37.9%             6.5%                          65   
    12             22.5%            12.5%                          59   
    1              41.9%            12.9%                          39   
    14             47.2%            13.8%                          39   
    0              51.9%            16.0%                          32   
    13             55.9%            16.0%                         100   
    10             34.3%             9.3%                          82   
    7              43.0%             7.5%                         110   
    11             36.8%             5.2%                          28   
    9              39.4%             5.2%                          48   
    6              30.7%            19.2%                          32   
    
        Hit Woodwork  Penalty goals  Penalties not scored  ...  Saves made  \
    2              1              0                     0  ...          10   
    5              2              1                     0  ...          10   
    3              0              0                     0  ...          22   
    8              2              0                     0  ...          12   
    15             0              0                     0  ...          13   
    4              1              0                     0  ...           6   
    12             2              0                     0  ...          10   
    1              0              0                     0  ...           9   
    14             3              0                     0  ...           8   
    0              0              0                     0  ...          13   
    13             0              1                     0  ...          15   
    10             6              0                     0  ...          10   
    7              2              0                     0  ...          20   
    11             0              0                     0  ...          17   
    9              0              0                     0  ...           6   
    6              1              1                     1  ...          13   
    
        Saves-to-shots ratio  Fouls Won Fouls Conceded  Offsides  Yellow Cards  \
    2                  66.7%         25             38         8             4   
    5                  62.6%         63             49        12             4   
    3                  88.1%         43             45         6             5   
    8                  70.6%         35             30         3             5   
    15                 76.5%         48             31         4             5   
    4                  54.6%         36             51         5             6   
    12                 77.0%         34             43         4             6   
    1                  60.1%         53             73         8             7   
    14                 61.6%         35             51         7             7   
    0                  81.3%         41             62         2             9   
    13                 93.8%        102             83        19            11   
    10                 71.5%         73             90        10            12   
    7                  74.1%        101             89        16            16   
    11                 65.4%         43             51        11             6   
    9                  66.7%         48             56         3             7   
    6                  65.1%         67             48        12             9   
    
        Red Cards  Subs on  Subs off  Players Used  
    2           0        7         7            15  
    5           0       15        15            17  
    3           0       11        11            16  
    8           0        7         7            15  
    15          0        9         9            18  
    4           0       11        11            19  
    12          0        7         7            16  
    1           0       11        11            19  
    14          0        9         9            18  
    0           0        9         9            16  
    13          0       17        17            18  
    10          0       14        14            16  
    7           0       18        18            19  
    11          1       10        10            17  
    9           1        7         7            17  
    6           1       12        12            20  
    
    [16 rows x 35 columns]
    

### Step 9. Calculate the mean Yellow Cards given per Team


```python
print(euro12['Yellow Cards'].mean())
```

    7.4375
    

### Step 10. Filter teams that scored more than 6 goals


```python
print(euro12[euro12['Goals'] > 6])
```

           Team  Goals  Shots on target  Shots off target Shooting Accuracy  \
    5   Germany     10               32                32             47.8%   
    13    Spain     12               42                33             55.9%   
    
       % Goals-to-shots  Total shots (inc. Blocked)  Hit Woodwork  Penalty goals  \
    5             15.6%                          80             2              1   
    13            16.0%                         100             0              1   
    
        Penalties not scored  ...  Saves made  Saves-to-shots ratio  Fouls Won  \
    5                      0  ...          10                 62.6%         63   
    13                     0  ...          15                 93.8%        102   
    
       Fouls Conceded  Offsides  Yellow Cards  Red Cards  Subs on  Subs off  \
    5              49        12             4          0       15        15   
    13             83        19            11          0       17        17   
    
        Players Used  
    5             17  
    13            18  
    
    [2 rows x 35 columns]
    

### Step 11. Select the teams that start with G


```python
print(euro12[euro12['Team'].str.startswith("G") == True])
```

          Team  Goals  Shots on target  Shots off target Shooting Accuracy  \
    5  Germany     10               32                32             47.8%   
    6   Greece      5                8                18             30.7%   
    
      % Goals-to-shots  Total shots (inc. Blocked)  Hit Woodwork  Penalty goals  \
    5            15.6%                          80             2              1   
    6            19.2%                          32             1              1   
    
       Penalties not scored  ...  Saves made  Saves-to-shots ratio  Fouls Won  \
    5                     0  ...          10                 62.6%         63   
    6                     1  ...          13                 65.1%         67   
    
      Fouls Conceded  Offsides  Yellow Cards  Red Cards  Subs on  Subs off  \
    5             49        12             4          0       15        15   
    6             48        12             9          1       12        12   
    
       Players Used  
    5            17  
    6            20  
    
    [2 rows x 35 columns]
    

### Step 12. Select the first 7 columns


```python
print(euro12.iloc[:, 0:7])
```

                       Team  Goals  Shots on target  Shots off target  \
    0               Croatia      4               13                12   
    1        Czech Republic      4               13                18   
    2               Denmark      4               10                10   
    3               England      5               11                18   
    4                France      3               22                24   
    5               Germany     10               32                32   
    6                Greece      5                8                18   
    7                 Italy      6               34                45   
    8           Netherlands      2               12                36   
    9                Poland      2               15                23   
    10             Portugal      6               22                42   
    11  Republic of Ireland      1                7                12   
    12               Russia      5                9                31   
    13                Spain     12               42                33   
    14               Sweden      5               17                19   
    15              Ukraine      2                7                26   
    
       Shooting Accuracy % Goals-to-shots  Total shots (inc. Blocked)  
    0              51.9%            16.0%                          32  
    1              41.9%            12.9%                          39  
    2              50.0%            20.0%                          27  
    3              50.0%            17.2%                          40  
    4              37.9%             6.5%                          65  
    5              47.8%            15.6%                          80  
    6              30.7%            19.2%                          32  
    7              43.0%             7.5%                         110  
    8              25.0%             4.1%                          60  
    9              39.4%             5.2%                          48  
    10             34.3%             9.3%                          82  
    11             36.8%             5.2%                          28  
    12             22.5%            12.5%                          59  
    13             55.9%            16.0%                         100  
    14             47.2%            13.8%                          39  
    15             21.2%             6.0%                          38  
    

### Step 13. Select all columns except the last 3.


```python
print(euro12.iloc[:, :-3])
```

                       Team  Goals  Shots on target  Shots off target  \
    0               Croatia      4               13                12   
    1        Czech Republic      4               13                18   
    2               Denmark      4               10                10   
    3               England      5               11                18   
    4                France      3               22                24   
    5               Germany     10               32                32   
    6                Greece      5                8                18   
    7                 Italy      6               34                45   
    8           Netherlands      2               12                36   
    9                Poland      2               15                23   
    10             Portugal      6               22                42   
    11  Republic of Ireland      1                7                12   
    12               Russia      5                9                31   
    13                Spain     12               42                33   
    14               Sweden      5               17                19   
    15              Ukraine      2                7                26   
    
       Shooting Accuracy % Goals-to-shots  Total shots (inc. Blocked)  \
    0              51.9%            16.0%                          32   
    1              41.9%            12.9%                          39   
    2              50.0%            20.0%                          27   
    3              50.0%            17.2%                          40   
    4              37.9%             6.5%                          65   
    5              47.8%            15.6%                          80   
    6              30.7%            19.2%                          32   
    7              43.0%             7.5%                         110   
    8              25.0%             4.1%                          60   
    9              39.4%             5.2%                          48   
    10             34.3%             9.3%                          82   
    11             36.8%             5.2%                          28   
    12             22.5%            12.5%                          59   
    13             55.9%            16.0%                         100   
    14             47.2%            13.8%                          39   
    15             21.2%             6.0%                          38   
    
        Hit Woodwork  Penalty goals  Penalties not scored  ...  Clean Sheets  \
    0              0              0                     0  ...             0   
    1              0              0                     0  ...             1   
    2              1              0                     0  ...             1   
    3              0              0                     0  ...             2   
    4              1              0                     0  ...             1   
    5              2              1                     0  ...             1   
    6              1              1                     1  ...             1   
    7              2              0                     0  ...             2   
    8              2              0                     0  ...             0   
    9              0              0                     0  ...             0   
    10             6              0                     0  ...             2   
    11             0              0                     0  ...             0   
    12             2              0                     0  ...             0   
    13             0              1                     0  ...             5   
    14             3              0                     0  ...             1   
    15             0              0                     0  ...             0   
    
        Blocks  Goals conceded Saves made  Saves-to-shots ratio  Fouls Won  \
    0       10               3         13                 81.3%         41   
    1       10               6          9                 60.1%         53   
    2       10               5         10                 66.7%         25   
    3       29               3         22                 88.1%         43   
    4        7               5          6                 54.6%         36   
    5       11               6         10                 62.6%         63   
    6       23               7         13                 65.1%         67   
    7       18               7         20                 74.1%        101   
    8        9               5         12                 70.6%         35   
    9        8               3          6                 66.7%         48   
    10      11               4         10                 71.5%         73   
    11      23               9         17                 65.4%         43   
    12       8               3         10                 77.0%         34   
    13       8               1         15                 93.8%        102   
    14      12               5          8                 61.6%         35   
    15       4               4         13                 76.5%         48   
    
        Fouls Conceded  Offsides  Yellow Cards  Red Cards  
    0               62         2             9          0  
    1               73         8             7          0  
    2               38         8             4          0  
    3               45         6             5          0  
    4               51         5             6          0  
    5               49        12             4          0  
    6               48        12             9          1  
    7               89        16            16          0  
    8               30         3             5          0  
    9               56         3             7          1  
    10              90        10            12          0  
    11              51        11             6          1  
    12              43         4             6          0  
    13              83        19            11          0  
    14              51         7             7          0  
    15              31         4             5          0  
    
    [16 rows x 32 columns]
    

### Step 14. Present only the Shooting Accuracy from England, Italy and Russia


```python
euro12.set_index('Team',inplace=True)
print(euro12.loc[['England','Italy','Russia'], 'Shooting Accuracy'])
```

    Team
    England    50.0%
    Italy      43.0%
    Russia     22.5%
    Name: Shooting Accuracy, dtype: object
    
