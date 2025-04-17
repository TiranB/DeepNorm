# DeepNorm - A Structured Power Query Solution for Normalization
DeepNorm is a layered data modeling project that applies advanced normalization techniques to transform raw datasets into deeply structured, multi-form relational models. It focuses on minimizing redundancy, enhancing data integrity, and building scalable database foundations. The transformation of the single merged table into a relational data model is done by using Excel Power Query.

## 📖 Project Overview
DeepNorm showcases how raw, denormalized data can be systematically transformed into a fully normalized structure (1NF, 2NF, 3NF) using Excel Power Query and modeled in Power Pivot. The project emphasizes clarity, integrity, and scalability in data modeling — essential principles for building clean, relational datasets in Excel that support efficient analysis and reporting.

## 🎯 Objectives
 - Import raw data into Power Query and understand
 - Apply First, Second, and Third Normal Forms
 - Load Normalized data into PowerPivot and define relationships between the tables using appropriate keys
 - Validate Data Integrity and Model Structure


## 📚 Normalization Layers Covered
| Normal Form | Purpose | Achieved In |
|-------------|---------|-------------|
| 1NF | Remove repeating groups and ensure atomicity | Raw → 1NF |
| 2NF | Remove partial dependencies | 1NF → 2NF |
| 3NF | Remove transitive dependencies | 2NF → 3NF |

## 🔗 Data Source
- **Dataset**: [Download Full Raw Dataset (Google Drive)](https://drive.google.com/drive/folders/1GpMdtZYvHN8pgTiexpg7ZpTUFaZEyjQK?usp=sharing)  
- **Type**: Flat file (Excel)
- **Rows**: [62885 rows]
- **Field Categories**: Customer, Transaction, Products, Dates

## 🛠 Tools Used
- Power Query
- Power Pivot

## 🧭 Step-by-Step Process

### 🔹 Step 1: Understand the data
  - Imported the dataset into Excel.
  - Loaded the data into Power Query Editor to transform.
  - Identified repeating groups, redundant fields, and potential functional dependencies.

### 🔹 Step 2: Apply first Normal Form (1NF)
  - Ensured Atomicity
  - Ensured the uniqueness of the identifiers of rows

### 🔹 Step 3: Apply Second Normal Form (2NF)
  - Created separate dimension tables for Customers, Products, and stores
     - Duplicate the transaction table three times to create the dimension tables.
     - Removed Unrelated columns from the respective dimensions.
     - Sorted for clear structure
     - Confirmed the uniqueness of the primary key columns by checking the 'column profile' in 'view' tab (select the 'Column profiling based on entire dataset' 
       option in the left bottom corner of the Power Query editor)
       [Preview of Column Profile'](https://github.com/TiranB/DeepNorm/blob/main/profile%20view%20image.JPG)
  - Remove all the dimensional level data from the transaction table (Fact Table)
  - Established foreign key relationships
  - After all of those steps, there are remainings of  partial dependencies in the transactions table.
    The non-key attributes of  Order date, Delivery Date, Customer ID, and Store ID depend on OrderNumber which is a part of the composite primary key
    (OrderNumber and Line Item). Because of that An Orders table needed to be created for further limitation of data redundancy. Mentioned fields were replaced in 
    the Orders table. The transaction table was renamed as 'Order Line Items'. So we have the deepest level of granularity in the 'Order Line Item ' table.
  - Close and Apply as a Data Model and Explore the 2NF in Power Pivot
    ![Star schema for 2NF](https://github.com/TiranB/DeepNorm/blob/main/star%20schema%20for%202%20NF.JPG)

### 🔹 Apply Third Normal Form (3NF): Remove Transitive Dependencies (Non-key attributes should not depend on other non-key attributes)
  - In the 'Products' table 'ProductCategory' and 'ProductSubcategory' fields depend on 'ProductCategoryID' and 'ProductSubcategoryID' respectively. This is 3NF 
    violation. So those fields were separated into new tables. (Categories, Subcategories)
  - Close and Apply as a Data Model and Explore the 3NF in Power Pivot.
    ![Snowflake Schema for 3NF](https://github.com/TiranB/DeepNorm/blob/main/snowflake%20schema%20for%203NF.JPG)  

## 🧠 Key Learnings  
  1. Practical understanding of Normalization (1NF, 2NF, 3NF)
     - Gained hands-on experience in applying normalization rules to reshape a denormalized dataset into a clean, structured, and relational model.
  2. Using Excel Power Query for Data Transformation
     - Learned to use Power Query as an ETL tool — importing, cleaning, splitting, and restructuring raw data into multiple related tables efficiently.
  3. Building Relational Data Models in Excel
  4. Minimizing Redundancy and Improving Data Integrity
     - Identified and removed duplicated or repetitive data to ensure consistency, reduce storage waste, and increase accuracy in reporting.





## 👤 Author

**Tiran Bhashitha**  
📧 tiran199820@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/tiran-bashitha-t199802) • [GitHub](https://github.com/TiranB)


     
     
    


