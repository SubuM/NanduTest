### The Goal
You are receiving a stream of log data. Some events are duplicates.  
You need to keep only the **first occurrence** of each unique `request_id`.

### Python Standard Approach
- Use a `set` to track seen IDs
- Use a `list` to store the unique records
- This provides **O(1)** lookup time and is very memory-efficient for streaming

### Pandas Approach
- Use:
  ```python
  df.drop_duplicates(subset=['request_id'], keep='first')
  ```

### The Lesson
Understand how Python handles hashing in sets versus how Pandas manages memory blocks for deduplication.

### Pro-Tip from the Field
When practicing, pay attention to Time Complexity. A nested loop in standard Python ($O(n^2)$) will kill a production pipeline, whereas a Pandas vectorized operation or a Python dictionary lookup ($O(1)$) will keep things humming.
