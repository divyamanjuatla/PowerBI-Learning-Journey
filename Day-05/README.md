Day 5 – Power Query: Reshaping Data

📌 Topic: Reshaping Data

What is Reshaping?

Reshaping means changing the layout or structure of a table without changing the actual meaning or values of the data.

It helps convert data into a format that is easier to understand, analyze, and visualize in Power BI.

Same data, different shape.

🔄 Pivot and Unpivot

The two important reshaping operations in Power Query are:

Pivot

Unpivot

They change rows into columns or columns into rows.

1. Unpivot Columns

What does Unpivot do?

Unpivot converts columns into rows.

Example:

Name

Jan

Feb

Maria

10

20

Ali

30

90

After Unpivot:

Name

Month

Value

Maria

Jan

10

Maria

Feb

20

Ali

Jan

30

Ali

Feb

90

Why use Unpivot?

Converts wide data into an analysis-friendly format.

Makes data easier to filter and group.

Works well with Power BI visualizations.

Helps create a proper tabular structure for analysis.

Simple rule

Columns → Rows = Unpivot

2. Pivot Columns

What does Pivot do?

Pivot converts rows into columns.

Example:

Name

Month

Value

Maria

Jan

10

Maria

Feb

20

Ali

Jan

30

Ali

Feb

90

After Pivot:

Name

Jan

Feb

Maria

10

20

Ali

30

90

Why use Pivot?

Creates a wider, human-friendly table.

Makes some reports easier to read.

Helps compare categories across columns.

Simple rule

Rows → Columns = Pivot

🔁 Pivot vs Unpivot

Operation

Changes

Main Purpose

Pivot

Rows → Columns

Create a wider, readable table

Unpivot

Columns → Rows

Create an analysis-friendly table

Easy way to remember

Pivot = Rows → Columns
Unpivot = Columns → Rows

📊 Why Reshaping Matters in Power BI

A table may be easy for a human to read but not ideal for analysis.

For example:

Name | Jan | Feb | Mar

can be reshaped into:

Name | Month | Value

This structure is often easier for:

Creating visualizations

Filtering data

Grouping by month

Performing calculations

Building reusable reports

Analyzing data dynamically


Take the unpivoted table and use Pivot Column to convert the Month values back into separate columns.
📝 Summary

Today I learned how to reshape data in Power Query using Pivot and Unpivot.

Main concepts

Pivot → Rows to Columns

Unpivot → Columns to Rows

Reshaping helps convert data into a structure that is easier to analyze and visualize in Power BI.
