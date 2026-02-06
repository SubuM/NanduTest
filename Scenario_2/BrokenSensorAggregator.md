## The Goal
You have sensor readings with the following fields:
- `Timestamp`
- `Sensor_ID`
- `Value`

Some values are `None` or `NaN`.  
You need to calculate the **average reading per sensor**, but only for sensors that have **more than 10 valid readings**.

## Python Standard Approach
- Use `collections.defaultdict(list)` to group values
- Iterate manually to:
  - Filter out invalid (`None` / `NaN`) values
  - Calculate the mean

## Pandas Approach
- Use:
  ```python
  df.groupby('Sensor_ID')['Value'].agg(['count', 'mean'])
  ```
  and then filter the resulting DataFrame where count > 10.

### The Lesson
In the real world, "broadcasting" a small dictionary is often faster than a full SQL-style join if the lookup table is tiny.
This highlights the beauty of split–apply–combine logic.

### Pro-Tip from the Field
When practicing, pay attention to Time Complexity. A nested loop in standard Python ($O(n^2)$) will kill a production pipeline, whereas a Pandas vectorized operation or a Python dictionary lookup ($O(1)$) will keep things humming.
