## Lab Report: Data Binning and Formatting
**Student Name:** Vedant Trivedi  
**PRN:** 25070123121  
**Experiment No:** 14

### 1. Aim
To implement data binning (bucketing), data type conversion, and string formatting in Python using the `pandas` library to transform raw numerical data into meaningful categorical groups.

### 2. Theory
* **Data Binning:** A data pre-processing technique used to reduce the effects of minor observation errors or to group continuous values into a smaller number of "bins."
    * **`pd.cut()`:** This function is used to segment and sort data values into bins. It is ideal for converting a numerical variable into a categorical variable (e.g., Price $\rightarrow$ Low/Medium/High).
* **Data Formatting:** Ensuring data is in the correct shape and type for analysis. This includes:
    * **Type Casting:** Converting integers to floats for precision using `.astype()`.
    * **String Normalization:** Converting text to uppercase or lowercase for consistency.
* **Sorting:** Arranging data in ascending or descending order to identify top or bottom performers.



### 3. Logic
The logic applied in this script focuses on **segmentation**:
1.  **Define Thresholds:** Creating a list of "bins" (the edges of the buckets) and "labels" (the names for those buckets).
2.  **Mapping:** Applying `pd.cut` to map every numerical value into its corresponding label.
3.  **Sanitization:** Converting units (like Units_Sold) to float to allow for decimal calculations if needed later, and standardizing product names to uppercase to avoid "Laptop" and "laptop" being treated as different items.
4.  **Multi-Dimensional Binning:** Applying the same logic across different metrics like `Price`, `Units_Sold`, and `Delivery_Time` to create a multi-categorical profile for each row.

### 4. One-Liner Code Explanations
* `pd.cut(df['Price'], bins=bins1, labels=labels1)`: Segments the Price column into categories based on the defined ranges.
* `df.dtypes`: Displays the current data type of every column in the DataFrame.
* `df['Units_Sold'].astype(float)`: Permanently changes the data type of the Units_Sold column from integer to float.
* `df['Product'].str.upper()`: Standardizes all text in the Product column to capital letters.
* `df.sort_values(by='Price')`: Rearranges the entire table based on the Price column in ascending order.
* `ascending=False`: A parameter within `sort_values` that sorts data from highest to lowest.
* `df['Order_Category'].value_counts()`: Provides a frequency count of how many items fall into each bin.

### 5. Algorithm
1.  **Import** `pandas` and `numpy`.
2.  **Initialize Data:** Create a dictionary containing products, prices, and sales data.
3.  **Perform Binning:**
    * Define numerical boundaries (e.g., `[0, 20000, 30000, 60000]`).
    * Define corresponding text labels (e.g., `['Low', 'Medium', 'High']`).
    * Use `pd.cut()` to create a new categorical column.
4.  **Format Data:**
    * Convert numeric columns to `float` using `astype()`.
    * Convert string columns to `upper()` for uniformity.
5.  **Sort Insights:** Sort the DataFrame by `Units_Sold` to see the most popular products.
6.  **Analyze Orders:** Apply similar binning to a "Food Delivery" dataset to categorize `Order_Value`, `Delivery_Time`, and `Distance`.
7.  **Verify:** Use `value_counts()` to check the distribution of orders across the new categories.

### 6. Conclusion
By completing this experiment, I have learned how to transform raw, continuous numbers into descriptive categories. This is essential for business logic, such as defining "Fast" vs "Slow" deliveries. I also practiced data consistency techniques like type conversion and string formatting, which ensure that the dataset remains clean and professional for reporting or machine learning models.

---
