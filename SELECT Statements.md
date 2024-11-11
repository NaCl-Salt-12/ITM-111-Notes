
Tags: #WIP
Links:  [[MySQL]], [[MySQL Functions]]
___

# SELECT Statements
The __SELECT__ Statement is used to query information from a Database.

## 5 Clauses of <font color="#4bacc6">SELECT</font> Statements 

```SQL
SELECT    --The columns displayed in the query result 
FROM      -- Specifies the table pulled from         
WHERE     --Filters the rows by those that match the condition
ORDER BY  --Specifies how to sort the rows
LIMIT     --The number of rows to return
```

### <font color="#4bacc6">SELECT</font> and <font color="#00b0f0">FROM</font> Statements
```SQL
SELECT column1, column2, ...
FROM table_name;
```
In the __SELECT__ statement you can list the columns that you want to query separated by a comma
table_name is the name of the table your querying 

#### Column Name
```SQL
SELECT product_name, list_price
FROM product;
```
###### Result
```csvtable
source: attachments/csv/bike_example.csv
maxRows: 6
```

#### All Columns Using asterisk
Alternatively you can use an asterisk to select all columns in the table
```SQL
SELECT *
FROM product;
```
###### Result
```csvtable
source: attachments/csv/bike_example_complete.csv
maxRows: 6

```
#### Columns with Calculations 
You can do basic calculations within __SELECT__ statements such as:
- Addition(+)
- Subtraction(-) 
- Multiplication( * )
- Division( / )
- [[Modulus]] (%) 
Note this does change the column header in the result.
```SQL
SELECT product_name, list_price + 50.00
FROM product;
```
###### Result
```csvtable
source: attachments/csv/bike_example_math.csv
maxRows: 6
```
#### Alias
You can change the displayed column name with the __AS__ keyword, this is caused an alias.
```SQL
SELECT product_name, list_price + 50.00 AS 'Markup Price'
FROM product;
```
###### Results
```csvtable
source: attachments/csv/bike_example_AS.csv
```
#### Columns created with functions
You can use [[MySQL Functions|functions]] in the __SELECT__ statement. For example you can use the [[ROUND()]] function to round the price to the nearest dollar.
```SQL
SELECT product_name, ROUND(list_price) AS 'nearest_dollar'
FROM product;
```
###### Result
```csvtable
source: attachments/csv/bike_example_functions.csv
```
#### DISTINCT
The keyword __DISCTINCT__ when used with __SELECT__ eliminates all duplicate records. You can also use with functions like __COUNT__ to count the number of unique records. 

##### Without __DISTINCT__:
```SQL
SELECT model_year
FROM product;
```
###### Result
```csvtable
source: attachments/csv/bike_example_year.csv
maxRows: 6
```
##### With __DISTINCT__:
```SQL
SELECT DISTINCT model_year
FROM product;
```
###### Result
```csvtable
source: attachments/csv/bike_example_DISTINCT.csv
```
###### Further Clarification
Note that if you have multiple columns displayed it makes sure the entire row is __DISTINCT__
for example if you have:
```SQL
SELECT product_name, list_price
FROM product;
```
Result
```csvtable
source: attachments/csv/bike_example.csv
maxRows: 6
```

the result will be the same as if you used 

```SQL
SELECT DISTINCT product_name, list_price
FROM product;
```
Result:
```csvtable
source: attachments/csv/bike_example.csv
maxRows: 6
```
Even if the price was the same for two products it still would be __DISTINCT__ because the product name is different

Created:: 2024-11-07 17:02