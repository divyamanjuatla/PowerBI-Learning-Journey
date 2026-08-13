Day 4 – Power Query: Missing Values, Transformations, Combining Tables & Joins

📌 What I Learned Today

Today I continued learning Power Query in Power BI, focusing on handling missing values, transforming columns, combining tables using Merge and Append, understanding SQL-style joins, and cleaning the final dataset.

1. Handling Missing Values

Missing values can appear in different forms:

NULL – the value is unknown or missing.

Empty string – a text value with no characters (""), whose length is 0.

Whitespace – a value that contains spaces, such as "   ".

Handling Missing Values

The correct replacement depends on the meaning of the column.

For numeric data, possible approaches include:

Keep the value as NULL when it is genuinely unknown.

Replace with 0 when zero is logically meaningful.

Replace with the mean or median when appropriate.

Example:

100, 200 → Mean = (100 + 200) / 2 = 150
100, 200, 300 → Mean = (100 + 200 + 300) / 3 = 200

Do not blindly replace every missing value with 0. The replacement should make business and analytical sense.

For dates, a default date can be used only when required by the business rule. Otherwise, keeping the value as NULL may be more appropriate.

2. Transform Data

Important Power Query transformations learned today:

Split Columns

Merge Columns

Extract Parts

Change Data Type

Replace Values

Format Text

Combine Tables

3. Split Columns

Split Column separates one column into multiple columns using a delimiter.

Example:

Laptop Pro | Electronics
Gaming Mouse | Accessories

Splitting by | produces:

Product Name

Category

Laptop Pro

Electronics

Gaming Mouse

Accessories

Common delimiters include |, ,, -, /, and space.

4. Merge Columns

Merge Columns combines two or more columns into one.

Example:

First Name

Last Name

Divya

Manju

After merging:

Divya Manju

A separator such as a space can be selected.

5. Extract Parts of a Column

Power Query can extract:

Text Before Delimiter

Text After Delimiter

Text Between Delimiters

First Characters

Last Characters

Example:

C-100-BE

A required part such as 100 can be extracted using delimiters.

Extract Email Domain

For:

divya@example.com

Use Extract → Text After Delimiter with @.

Result:

example.com

6. Combine Tables

Power Query provides two major ways to combine tables:

             Combine
            /               Merge       Append

They solve different problems.

7. Merge Queries

Merge combines tables based on a matching column/key. It is similar to a SQL JOIN.

Example:

Table A

ID

Name

1

A

2

B

3

C

Table B

ID

Category

1

Electronics

2

Accessories

3

Furniture

Merging on ID brings related columns from Table B into Table A.

Steps

Select the first query.

Choose Merge Queries.

Select the second query.

Select the matching key column in both tables.

Select the required join type.

Click OK.

Expand the merged column.

Select the required fields.

Key Concept

Merge → combine columns from related tables using a matching key.

8. Append Queries

Append combines rows from two or more tables. It is similar to a SQL UNION.


Key Concept

Append → combine rows from tables with the same or compatible columns.

9. Merge vs Append

Feature

Merge

Append

Combines

Columns

Rows

Based on

Matching key

Similar column structure

SQL Equivalent

JOIN

UNION

Main purpose

Bring related information together

Stack datasets together

Easy Way to Remember

MERGE  → More columns
APPEND → More rows

10. SQL-Style Joins

The main join types studied today are:

Inner Join

Left Outer Join

Right Outer Join

Full Outer Join

Left Anti Join

Right Anti Join

Inner Join

Returns only records that match in both tables.

A ∩ B

Only matching records.

Left Outer Join

Returns:

All records from the left table

Matching records from the right table

All A + matching B

Unmatched right-side values appear as null.

Right Outer Join

Returns:

All records from the right table

Matching records from the left table

Matching A + all B

Full Outer Join

Returns:

All records from Table A

All records from Table B

Matching records are combined

All A + All B

Left Anti Join

Returns records present in the left table but not in the right table.

A - B

Useful for finding records missing from the right table.

Right Anti Join

Returns records present in the right table but not in the left table.

B - A

Useful for finding records missing from the left table.

Join Summary

Join Type

Result

Inner

Only matching records

Left Outer

All left + matching right

Right Outer

All right + matching left

Full Outer

All records from both

Left Anti

Left records with no right match

Right Anti

Right records with no left match

11. Combining Monthly Files

When data is stored in separate files such as:

orders_jan.csv
orders_feb.csv
orders_mar.csv

they can be connected and appended into one dataset.

January
   ↓
February → Append → Combined Orders
   ↑
March

This is useful when multiple files have the same structure.

12. Clean Up

After transforming and combining data, perform a final cleanup.

Cleanup Tasks

Remove unnecessary columns.

Rename tables and columns.

Follow clear naming conventions.

Review column names.

Check data types.

Check duplicate records.

Check key/identifier columns.

Check unwanted values.

Verify the final dataset.

Example meaningful names:

Sales
Orders
Customers
Categories
Order_ID
Customer_ID
Country_Code
Email
Email_Domain

13. Overall Power Query Workflow

Connect
   ↓
Promote Headers
   ↓
Filter
   ↓
Clean
   ↓
Handle Missing Values
   ↓
Transform
   ↓
Split / Merge / Extract
   ↓
Combine
   ├── Merge → Join tables
   └── Append → Stack rows
   ↓
Final Cleanup
   ↓
Load
   ↓
Power BI Visualization

