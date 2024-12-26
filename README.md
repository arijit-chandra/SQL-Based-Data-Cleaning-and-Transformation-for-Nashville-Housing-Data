# SQL-Based-Data-Cleaning-and-Transformation-for-Nashville-Housing-Data

This repository contains SQL scripts used for cleaning and transforming housing data from the NashvilleHousing table within the Portfolio database. The scripts focus on data quality improvements, such as handling missing values, correcting data types, and separating concatenated fields into distinct columns.

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Database Setup](#database-setup)
- [Scripts Overview](#scripts-overview)
- [Data Cleaning Steps](#data-cleaning-steps)
- [Usage](#usage)
- [License](#license)

## Overview
The objective of this project is to clean the Nashville Housing data for better analysis and reporting. The data included properties' information such as property address, sale date, and owner address, which needed refinement to ensure it adhered to data quality standards. Key tasks included:
- Data type modification
- Null value handling and population
- Data normalization (splitting addresses into separate fields)
- Duplicate detection and removal
- Column renaming and cleanup

## Prerequisites
- SQL Server Management Studio (SSMS) or any SQL client that supports SQL Server
- CSV file containing Nashville housing data
- Basic understanding of SQL and database operations

## Database Setup

### Creating the Database and Table
1. **Create the Portfolio Database**:
   ```sql
   CREATE DATABASE Portfolio;
   GO
   ```

2. **Create the NashvilleHousing Table**:
   ```sql
   USE Portfolio;
   ```

### Importing Data
Follow these steps to import data using SSMS:

1. **Launch Import Wizard**:
   - Right-click on the NashvilleHousing Table in Object Explorer
   - Select `Tasks > Import Data`

2. **Configure Data Source**:
   - Select `Flat File Source` as the data source type
   - Browse and select your CSV file
   - Review and adjust column mappings as needed

3. **Set Destination**:
   - Choose `SQL Server Native Client` as the destination
   - Select the Portfolio database and NashvilleHousing table
   - Map the columns appropriately

4. **Complete Import**:
   - Review the summary and execute the import
   - Verify the data after import completion

## Scripts Overview
The following SQL tasks are performed in the provided scripts:

1. **Modifying Data Types**:
   - Changing the `SaleDate` column to the `DATE` data type

2. **Handling Null Values**:
   - Identifying and updating missing property addresses using a self-join

3. **Splitting Addresses**:
   - Splitting the `PropertyAddress` and `OwnerAddress` columns into separate address, city, and state columns

4. **Data Normalization**:
   - Standardizing values in the `SoldAsVacant` column by updating them to 'Y' for 'Yes' and 'N' for 'No'

5. **Duplicate Removal**:
   - Using a Common Table Expression (CTE) with `ROW_NUMBER()` to detect and remove duplicate records

6. **Column Cleanup**:
   - Dropping unused columns and renaming others for better clarity

## Data Cleaning Steps
1. **Modify Sale Date Column**:
   ```sql
   ALTER TABLE Portfolio..NashvilleHousing
   ALTER COLUMN SaleDate DATE;
   ```

## Usage
1. Set up the database and table structure as described in the Database Setup section
2. Import your Nashville housing data
3. Execute the cleaning scripts in sequence
4. Verify the results after each transformation step

## License
This project is licensed under the MIT License - see the LICENSE file for details.