
# Scenario: Analyzing Sales Data for a Small Retail Store Using Excel

## Background
You are a data analyst hired by a small retail store to help improve their sales. The store sells various products, and the owner wants to understand:

1. **Which products perform best and worst.**  
2. **How sales vary by date and category.**  
3. **The impact of discounts on sales.**  

---

## Dataset: Retail Sales Data

### Columns:
- **Transaction_ID:** Unique identifier for each transaction.  
- **Date:** Date of the transaction.  
- **Product:** Name of the product sold.  
- **Category:** Product category.  
- **Price:** Price of the product sold.  
- **Quantity:** Quantity of items sold.  
- **Discount:** Discount applied (%).  
- **Revenue:** Revenue generated from the sale.

### Dataset Preview
![Screenshot 2025-01-06 094715](https://github.com/user-attachments/assets/149422db-35b1-4123-83da-5f1204a30260)

### New to Excel 
[watch this video](https://youtu.be/LgXzzu68j7M?si=kUxmaJvVkn4X_do2)
# Data Cleaning 

Below are step-by-step instructions to clean the provided dataset in Excel. Each step addresses specific inconsistencies or errors in the data.

----------

## **1. Prepare the Dataset**

-   **Backup the Data**: Always create a copy of the original dataset before making any changes.
-   **Identify Issues**: Review the dataset to spot anomalies such as:
    -   Inconsistent formatting.
    -   Missing or invalid values.
    -   Duplicate rows.
    -   Errors in calculations.

----------

## **2. Standardize Column Headers**

-   Ensure that column headers are consistent and properly formatted:
    -   Remove leading/trailing spaces.
    -   Capitalize the first letter of each word for readability (e.g., `Transaction_ID`, `Product`).
    -   Replace ambiguous column names with more descriptive ones if needed.
![Screenshot 2025-01-06 093423](https://github.com/user-attachments/assets/8dbdd1c0-0b18-44f2-a0f2-3cf6b3a8011f)

----------

## **3. Clean Column Data**

### **A. Transaction_ID**

-   Check for duplicates to ensure all transaction IDs are unique. Remove any duplicate rows.

Here’s how you can identify and manage duplicate values in Excel:

---

### **1. Using Conditional Formatting**
1. **Select the Data Range**:
   - Highlight the column or range of data where you want to check for duplicates.
  
   - ![Screenshot 2025-01-06 100501](https://github.com/user-attachments/assets/50cb8642-cd88-4473-ac23-1a842d95ca1f)

2. **Apply Conditional Formatting**:
   - Go to **Home > Conditional Formatting > Highlight Cell Rules > Duplicate Values**.
  
   - ![Screenshot 2025-01-06 100818](https://github.com/user-attachments/assets/61453a24-28cc-4911-9ea5-c49c07bfe2a1)

3. **Customize the Formatting**:
   - Choose the formatting style (e.g., red fill, yellow text) to highlight duplicates.
  
   - ![Screenshot 2025-01-06 101026](https://github.com/user-attachments/assets/41529511-3dcd-4451-89e0-eb1eccbae205)

4. **Review Duplicates**:
   - Review the highlighted cells to see where duplicates exist.
  
   - ![Screenshot 2025-01-06 101209](https://github.com/user-attachments/assets/64299da5-fda5-4744-9a06-2b08ce2bb7dc)

---

##### **2. Using the COUNTIF Formula**
1. **Add a Helper Column**:
   - Insert a new column next to your dataset and label it `Duplicate Check`.

2. **Enter the Formula**:
   - In the first cell of the helper column (e.g., `G2`), enter:
     ```
     =COUNTIF(A:A, A2)>1
     ```
     Replace `A:A` with the column range and `A2` with the starting cell of the column you are checking.

     ![Screenshot 2025-01-06 102359](https://github.com/user-attachments/assets/b653fc97-06aa-4131-947f-cc2f29a03153)

3. **Interpret the Results**:
   - Values greater than `1` indicate duplicates.

---
### **Convert Data to an Excel Table First?**

Converting your dataset into an Excel table provides several benefits:
1. **Dynamic Range**: Automatically adjusts for new rows or columns added to the dataset.
2. **Easier Sorting and Filtering**: Built-in dropdown menus for quick sorting and filtering.
3. **Consistent Formatting**: Alternate row shading and style options improve readability.
4. **Simplified Formulas**: Column headers become references, making formulas easier to read.
5. **Error Reduction**: Protects against accidental changes to the structure.

---

### **Steps to Convert Data to an Excel Table**
1. **Select the Data**:
   - Highlight the entire dataset, including headers.(CTRL A)

2. **Convert to Table**:
   - Go to **Insert > Table** or press **Ctrl + T**.
  
   - ![Screenshot 2025-01-04 145421](https://github.com/user-attachments/assets/d23d2760-0953-43a3-bb49-fc56ec627f59)

3. **Confirm Table Options**:
   - Ensure the **My Table Has Headers** checkbox is selected and click **OK**.
  
   - ![Screenshot 2025-01-04 145630](https://github.com/user-attachments/assets/738075bf-3f4d-4009-87c9-76eb00e103c5)

4. **Rename the Table** *(Optional)*:
   - Go to **Table Design > Table Name** and give the table a meaningful name.

Your data is now ready for streamlined cleaning and analysis!
---

##### Remove Duplicates
1. **Select the Dataset**:
   - Highlight your entire dataset, including headers.

2. **Open the Remove Duplicates Dialog**:
   - Go to **Data > Remove Duplicates**.

3. **Specify Columns**:
   - In the dialog box:
     - Ensure the **My Data Has Headers** checkbox is selected.
     - Check the columns where duplicates need to be checked.
    
     - ![Screenshot 2025-01-06 105144](https://github.com/user-attachments/assets/b76c9047-f344-457f-90c6-1546c216587d)
    
**Reason for Removing Duplicates in the Transaction_ID Column**

The `Transaction_ID` column is meant to uniquely identify each transaction. Duplicate values in this column can lead to:

1. **Data Integrity Issues**: Duplicate transaction IDs may cause confusion about whether multiple rows represent the same transaction or separate ones.
2. **Inaccurate Analysis**: Duplicate entries can inflate totals (e.g., revenue, quantity) and skew metrics.
3. **Errors in Reporting**: Reporting systems may treat duplicates as legitimate entries, leading to misleading insights.
4. **Redundant Data**: Retaining duplicates increases the size of the dataset unnecessarily, making it harder to manage.

By removing duplicates in the `Transaction_ID` column, you ensure that each transaction is unique, improving data accuracy and reliability for further analysis.

4. **Review the Results**:
   - Excel will display a message showing the number of duplicates removed and unique values remaining.

---
### **B. Date**

-   Standardize date formats:
    1.  Select the column.
    2.  Go to **Data > Text to Columns** if the format needs splitting.
    3.  Use **Format Cells** (Ctrl+1) to convert all dates to a consistent format (e.g., `YYYY-MM-DD`).

### **C. Product**

-   Correct spelling and capitalization inconsistencies:
    -   Use **Find and Replace** (Ctrl+H):
        -   Replace `LAPTOP`, `laptop` → `Laptop`.
        -   Replace `SHOES`, `shoes` → `Shoes`.
        -   Replace `backpakc` → `Backpack`, etc.
    -   Use Excel's **Flash Fill** to quickly standardize.

### **D. Category**

-   Standardize categories to consistent capitalization (e.g., `Clothing`, `Electronics`).
-   Use a helper column and the `PROPER` function to correct inconsistent cases:
    
    ```
    =PROPER(A2)
    
    ```
    

### **E. Price**

-   Remove currency symbols (`$`) using **Find and Replace**:
    1.  Find: `$`
    2.  Replace: (leave empty).
-   Ensure all prices are numeric using the `VALUE` function if needed:
    
    ```
    =VALUE(A2)
    
    ```
    

### **F. Quantity**

-   Check for invalid values:
    -   Replace negative quantities with `ABS(A2)` or mark them for review.
    -   Fill in missing quantities with appropriate placeholders (e.g., `0`).

### **G. Discount**

-   Ensure all discount values are numeric or in percentage format.
-   Remove `%` symbols using **Find and Replace** and convert to decimal:
    
    ```
    =A2/100
    
    ```
    

### **H. Revenue**

-   Validate revenue calculations using the formula:
    
    ```
    Revenue = (Price × Quantity) - (Price × Quantity × Discount)
    
    ```
    
-   Highlight mismatched values with conditional formatting.

----------

## **4. Handle Missing Values**

-   Use **Filter** to identify rows with missing values.
-   Impute missing values based on context:
    -   If `Price` is missing, use the average price for that product category.
    -   If `Revenue` is missing, recalculate using `Price`, `Quantity`, and `Discount`.

----------

## **5. Remove Duplicates**

-   Select the dataset.
-   Go to **Data > Remove Duplicates**.
-   Select all columns to ensure unique rows.

----------

## **6. Validate Data**

-   Use **Data Validation**:
    -   For `Price`, set a rule for numeric values > 0.
    -   For `Quantity`, ensure integers ≥ 0.
    -   For `Discount`, ensure values between 0 and 1.

----------

## **7. Add Consistency Checks**

-   Add helper columns to flag inconsistencies:
    -   For `Revenue`:
        
        ```
        =IF(A2=(B2*C2)*(1-D2), "Valid", "Invalid")
        
        ```
        
    -   For negative values:
        
        ```
        =IF(A2<0, "Error", "OK")
        
        ```
        

----------

## **8. Final Formatting**

-   Apply consistent number formatting:
    -   **Currency** for `Price` and `Revenue`.
    -   **Percentage** for `Discount`.
    -   **Number** for `Quantity`.
-   Align text for better readability.

----------

## **9. Document Changes**

-   Maintain a log of changes made for reference.
-   Save the cleaned dataset with a new name (e.g., `Cleaned_Transactions.xlsx`).
