📌 What I Learned Today

Today I focused on Power Query, especially how data is connected,filtered, cleaned, transformed, and prepared before building reports inPower BI.

1. ETL Process

ETL = Extract → Transform → Load

Extract: Get data from different sources.

Transform: Clean and prepare the data.

Load: Load the prepared data into the destination for analysisand visualization.

Common Data Sources

Database

CSV / Excel files

Kafka

APIs

Other data sources

Basic Data Flow

Data Sources
     ↓
Extract
     ↓
Power Query / Data Preparation
     ↓
Transform
     ↓
Load
     ↓
Power BI
     ↓
Data Visualization

Power Query is an important part of the data preparation andtransformation process.

2. Power Query -- Main Workflow

A simple Power Query workflow can be remembered as:

Connect

Filter

Clean Up

Transform

Combine

These steps help turn raw data into analysis-ready data.

3. Connect to Data Sources

The first step is to connect Power BI to the required data source.

Example Sources

Database ─────┐
File ─────────┤
Kafka ────────┼──→ Power BI / Power Query
API ──────────┘

Checking the Source Path

If something goes wrong with a CSV or file connection:

Power Query → Source / Source Settings

The source settings can be used to check or update the file path andconnection details.

4. Promote Headers

Sometimes the first row of the dataset contains column names but PowerQuery does not automatically recognize them as headers.

Example

Before:

Column1   Column2   Column3

ID        Name      Score1         A         302         B         60

After promoting headers:

ID   Name   Score

1    A      302    B      60

In Power Query

Home → Use First Row as Headers

A good header should clearly describe the data in the column.

Power Query can sometimes detect and promote headers automatically,but it is important to verify them.

5. Filter Data

Filtering helps remove unnecessary data and makes the dataset smallerand easier to work with.

Things to Check

Unnecessary columns

Blank rows

Unwanted records

Incorrect values

Remove an Unnecessary Column

Select the column → Right-click → Remove

Remove Blank Rows

Home → Remove Rows → Remove Blank Rows

Filter Rows

Use the filter/drop-down available on the column header to keep only therequired records.

Why Filter Data?

A smaller and relevant dataset is:

Easier to understand

Easier to analyze

Faster to process

Better for performance

6. Clean Data

Data cleaning means identifying and fixing problems in the dataset.

Common Cleaning Operations

Remove duplicates

Trim extra spaces

Standardize text case

Correct number formats

Correct date formats

Set correct data types

Handle missing values

Remove unwanted characters

7. Remove Duplicates

A duplicate is a record that appears more than once with the same orrepeated values.

Example

ID   Name     Score

1    A           301    A           302    B           60

Here, the first record is repeated.

How to Check Duplicates

First identify a column that should uniquely identify a record, such asa Customer ID or Primary Key.

You can also use:

Right-click column → Group By

For example, group by Customer ID and check whether an ID occurs morethan once.

Remove Duplicates

Home → Remove Rows → Remove Duplicates

Always understand whether repeated records are actually duplicatesbefore deleting them. Some repeated IDs may be valid in atransactional dataset.

8. Check Data Types

Every column should have the correct data type.

Common Data Types

Data          Suitable Type

Customer ID   Text / Whole Number depending on the dataName          TextAmount        Decimal NumberQuantity      Whole NumberPrice         Decimal NumberOrder Date    DateEmail         Text

Always check the values in a column and confirm that the data typematches the meaning of the data.

Example

If a column contains:

1
2
3
4

and these represent counts, Whole Number is appropriate.

9. Text Cleaning

Text data often contains inconsistent spaces, cases, or unwantedcharacters.

Important Text Operations

Trim

Removes unnecessary spaces from the beginning and end of text.

Example:

"  Divya  " → "Divya"

Change Case

Power Query can standardize text as:

lowercase

UPPERCASE

Capitalize Each Word

Example

Raw data:

USA
Germany
Canada
germany
India
Germany

After standardizing the case:

USA
Germany
Canada
Germany
India
Germany

This avoids treating values with different capitalization as differentcategories.

10. Replace Unwanted Characters

Sometimes a column contains unwanted symbols or characters.

Example

If a value contains:

ABC#123

and # is not required, use:

Replace Values

Find:

#

Replace with:

(empty)

Result:

ABC123

This is useful for cleaning IDs, names, addresses, and other textfields.

11. Cleaning Different Columns

Last Name

Possible cleaning steps:

Trim spaces

Standardize the case

Use Capitalize Each Word if required

Example:

"  smith  " → "Smith"

Email

Recommended checks:

Trim spaces

Convert to lowercase

Check for unwanted characters

Check whether the value has a valid-looking email structure

Example:

"  DIVYA@EMAIL.COM  "
        ↓
"divya@email.com"

Customer ID

Check for:

Mixed characters

Unnecessary spaces

Unwanted symbols

Inconsistent formatting

If the ID contains separators such as -, Power Query can also useSplit Column to separate the required parts.

Amount

Check:

Correct numeric data type

Decimal places

Rounding requirements

For example, if an amount should not contain unnecessary decimal places,use the appropriate number transformation or rounding operation.

Price

Check:

Correct decimal data type

Required number of decimal places

Rounding

Example:

125.678
   ↓
125.7

if the business requirement is one decimal place.

Order Date

The column should have the appropriate Date data type.

Check:

Date format

Invalid values

Errors

If errors are present, they can be handled using options such as:

Replace Errors → null

Only replace errors with null when that is appropriate for the analysis.

12. Test Case -- Standardizing Values

A common data-quality problem is having the same value written indifferent ways.

Example

Raw data:

USA
Germany
Canada
germany
India
Germany

The values Germany and germany refer to the same country but havedifferent capitalization.

Solution

Use:

Trim

lowercase

UPPERCASE

Capitalize Each Word

The goal is to make equivalent values consistent.

13. Power Query Interface

Some useful areas of the Power Query interface:

Left Side

Shows the available queries/tables.

Middle

Shows the data preview.

Right Side

Shows Query Settings and Applied Steps.

Each transformation creates an Applied Step.

Formula Bar / M Code

Power Query uses the M language.

Each transformation step has code behind it.

You can inspect the generated M code to understand what Power Query isdoing.

Advanced Editor

Home → Advanced Editor

The Advanced Editor allows you to view the complete M code for thequery.

14. Applied Steps

Power Query records transformations as steps.

Example:

Source
   ↓
Promoted Headers
   ↓
Removed Blank Rows
   ↓
Removed Columns
   ↓
Changed Type
   ↓
Removed Duplicates

This makes the transformation process repeatable.

If the source data is refreshed, Power Query can apply the steps again.

15. Key Learning Summary

Today I learned that data preparation is an important part of dataanalysis.

My workflow:

1. Connect to Source
        ↓
2. Promote Headers
        ↓
3. Filter Data
        ↓
4. Clean Data
        ↓
5. Transform Data
        ↓
6. Check Data Types
        ↓
7. Handle Duplicates / Missing Values / Errors
        ↓
8. Load Data
        ↓
9. Build Power BI Visualizations

🎯 Day 3 Practice

Connect a CSV file to Power BI.

Check the source path.

Promote the first row as headers.

Remove an unnecessary column.

Remove blank rows.

Filter unwanted records.

Remove duplicate records.

Check every column's data type.

Trim text columns.

Standardize text case.

Replace unwanted characters.

Check and clean email values.

Check Customer ID formatting.

Format Amount and Price correctly.

Convert Order Date to the Date data type.

Handle errors and missing values.

Review Applied Steps.

Open Advanced Editor and inspect the M code.

💡 Main Takeaway

Power Query is used to connect, clean, transform, and prepare databefore using it for analysis and visualization in Power BI.

Connect → Filter → Clean → Transform → Combine → Load → Visualize
