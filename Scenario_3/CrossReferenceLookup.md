# Enriching a Sales Table with a Lookup Table

## The Goal
You have a small **Lookup Table** mapping `Product_ID` → `Product_Name` and a massive **Sales Table**.  
You need to enrich the Sales Table with the product names.

## Python Standard Approach
- Load the lookup table into a `dict` for **O(1)** lookup time
- Iterate through the sales records
- Use `.get()` to pull the product name for each record

## Pandas Approach
- Use:
  ```python
  pd.merge(sales_df, products_df, on='Product_ID', how='left')
  ```

### The Lesson
In real-world pipelines, broadcasting a small dictionary is often faster than a full SQL-style join if the lookup table is tiny.

### Pro-Tip from the Field
When practicing, pay attention to Time Complexity. A nested loop in standard Python ($O(n^2)$) will kill a production pipeline, whereas a Pandas vectorized operation or a Python dictionary lookup ($O(1)$) will keep things humming.
