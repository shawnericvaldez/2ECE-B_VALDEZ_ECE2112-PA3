# 2ECE-B_VALDEZ_ECE2112-PA3

**By: Shawn Eric M. Valdez**

The notebook in this repository is the submission for Programming Assignment 3 for ECE2112, which required solving 3 data analysis problems using Pandas.

To solve all the problems in this Programming Assignment, the Pandas library was imported using:

```python
import pandas as pd
```

The dataset cars.csv was loaded into a DataFrame named cars using:

```python
cars = pd.read_csv('cars.csv')
```

# **A. Positional and Label-based Slicing**

Display the shape and complete list of column names of cars. Using positional slicing, create cars_6_to_10 containing rows 6 through 10 of the dataset. From cars_6_to_10, display only the columns Model, mpg, cyl, hp, and gear, in that order.

Solution Used:
```python
cars.shape
cars.columns

cars_6_to_10 = cars.iloc
cars_6_to_10

cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]
```

cars.shape and cars.columns are evaluated to retrieve the DataFrame's dimensions (32 rows, 12 columns) and column headers. Positional slicing via .iloc[5:10] extracts rows 6 through 10 (since Python uses 0-based indexing) and assigns them to cars_6_to_10. Finally, label-based indexing with .loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']] selects and displays only the specified columns in that exact order, without altering the underlying data.

# **B. Model Lookup**

Using Boolean indexing on the Model column, display the complete row for Toyota Corolla and store it in toyota. For Pontiac Firebird, display only the columns Model, mpg, hp, and wt, and store it in pontiac.

Solution Used:
```python
toyota = cars[cars['Model'] == 'Toyota Corolla']
toyota

pontiac = cars[cars['Model'] == 'Pontiac Firebird'][['Model', 'mpg', 'hp', 'wt']]
pontiac
```

Boolean indexing with the condition cars['Model'] == 'Toyota Corolla' filters the DataFrame for the matching record and stores the full row in toyota. Similarly, cars['Model'] == 'Pontiac Firebird' isolates the row for the Pontiac Firebird, and column filtering [['Model', 'mpg', 'hp', 'wt']] extracts only the four required variables before storing the result in pontiac.

# **C. Multi-Model Subsetting**

Create a DataFrame named selected_cars containing only the records for three models: Datsun 710, Lotus Europa, and Ferrari Dino. For these records, retain only Model, mpg, cyl, hp, and gear. Display selected_cars and its shape.

Solution Used:
```python
selected_cars = cars.loc[(cars['Model'] == 'Datsun 710') |
                         (cars['Model'] == 'Lotus Europa') |
                         (cars['Model'] == 'Ferrari Dino'),
                         ['Model', 'mpg', 'cyl', 'hp', 'gear']]
selected_cars
selected_cars.shape
```
Label-based indexer .loc[] evaluates multiple conditions chained together with the bitwise OR (|) operator to isolate the rows corresponding to 'Datsun 710', 'Lotus Europa', and 'Ferrari Dino'. The secondary list argument within .loc specifies the precise order of columns ('Model', 'mpg', 'cyl', 'hp', 'gear') to extract simultaneously, creating the DataFrame selected_cars. Evaluating selected_cars.shape confirms the output dimensions of 3 rows and 5 columns.
