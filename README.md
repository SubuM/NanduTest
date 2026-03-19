# NanduTest
Test and practice repo for Nandu. This repository contains various data engineering and Python coding scenarios to practice optimized approaches versus standard implementations.

## Scenarios Overview

### [Scenario 1: The Event Deduplicator](file:///Users/subha/AntigravityRepos/NanduTest/Scenario_1/TheEventDeduplicator.md)
**Goal**: Process a stream of log data and keep only the **first occurrence** of each unique `request_id`.
**Key Lesson**: Understand the difference between Python's hashing in sets ($O(1)$ lookup) and how Pandas manages memory blocks for deduplication.

### [Scenario 2: Broken Sensor Aggregator](file:///Users/subha/AntigravityRepos/NanduTest/Scenario_2/BrokenSensorAggregator.md)
**Goal**: Calculate the **average reading per sensor** for sensors with more than 10 valid (non-NaN) readings.
**Key Lesson**: Leveraging "split-apply-combine" logic in Pandas for efficient aggregation compared to manual iteration.

### [Scenario 3: Cross Reference Lookup](file:///Users/subha/AntigravityRepos/NanduTest/Scenario_3/CrossReferenceLookup.md)
**Goal**: Enrich a massive Sales Table with product names from a small Lookup Table.
**Key Lesson**: Broadcasting a small dictionary can often be faster than a full SQL-style join for small lookup tables.

---
*Pro-Tip: Always pay attention to Time Complexity ($O(n)$). Standard Python loops can be bottlenecks where vectorized Pandas operations or dictionary lookups keep pipelines humming.*
