
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

----------

## **3. Clean Column Data**

### **A. Transaction_ID**

-   Check for duplicates to ensure all transaction IDs are unique. Remove any duplicate rows.

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
