# Power BI Merge Queries — Practice Files

This folder contains two small Power BI Desktop files and their source Excel workbooks, used to practice the **Merge Queries** (join) feature in Power Query.

## Files

| File | Type | Description |
|---|---|---|
| `MergeQueryExample.xlsx` | Source data | Two sheets — `Sales` and `Customers` — used as the source tables for `merge.pbix` |
| `merge.pbix` | Power BI file | Data model built by merging `Sales` and `Customers` on `CustomerID` |
| `MERGE_Q_2.xlsx` | Source data | Two sheets — `StudentTable` and `CourseTable` — used as the source tables for `new_merge.pbix` |
| `new_merge.pbix` | Power BI file | Data model built by merging `StudentTable` and `CourseTable` on `CourseCode` |

Both `.pbix` files contain only a data model (no report visuals have been built on the pages yet) — they were created in the Power BI cloud service, version 1.28.

## Source data

### `MergeQueryExample.xlsx`

**Sales**
| CustomerID | SalesAmount |
|---|---|
| 101 | 5000 |
| 102 | 7000 |
| 103 | 3000 |
| 104 | 9000 |
| 105 | 4000 |

**Customers**
| CustomerID | CustomerName |
|---|---|
| 101 | Amit |
| 102 | Bhavna |
| 103 | Chetan |
| 106 | Divya |

> Note the mismatch: `Sales` has customers 101–105, `Customers` has 101, 102, 103, 106. This is intentional — it's what makes the table useful for comparing different join types (Inner, Left/Right Outer, Full Outer, Anti joins), since some keys only exist on one side.

**Common key:** `CustomerID`

### `MERGE_Q_2.xlsx`

**StudentTable**
| StudentID | StudentName | CourseCode | City |
|---|---|---|---|
| STU101 | Ayesha Khan | C001 | Mumbai |
| STU102 | Zainab Patel | C002 | Pune |
| STU103 | Aarav Shah | C003 | Delhi |
| STU104 | Riya Mehta | C001 | Mumbai |
| STU105 | Imran Sheikh | C004 | Hyderabad |

**CourseTable**
| CourseCode | CourseName | Duration | Fees |
|---|---|---|---|
| C001 | Advanced Excel | 3 Months | 8000 |
| C002 | Power BI | 4 Months | 10000 |
| C003 | Tableau | 3 Months | 9000 |
| C004 | MS Office | 2 Months | 6000 |
| C005 | SQL Database | 3 Months | 8500 |

> `CourseTable` includes `C005`, which no student is enrolled in — useful for showing how unmatched rows behave under different join kinds.

**Common key:** `CourseCode`

## How to open

1. Open `merge.pbix` or `new_merge.pbix` in **Power BI Desktop**.
2. Go to **Home → Transform Data** to open the Power Query Editor and inspect the applied **Merge Queries** step (join kind, key columns, and any expanded columns).
3. The original Excel files (`MergeQueryExample.xlsx`, `MERGE_Q_2.xlsx`) are included so the merge can be reproduced or modified — reconnect the data source path in Power Query if it can't find the file automatically.

## Purpose

These files are practice/demo material for learning how **Merge Queries** works in Power Query (Power BI / Excel Get & Data), covering:
- Matching rows between two tables on a common key
- Handling keys that exist in only one table
- Expanding merged columns into the base table

## Suggested next steps

- Add report visuals (tables/cards) on the report pages to show the merged results.
- Try re-doing each merge with a different join kind (Inner, Left Outer, Right Outer, Full Outer, Left Anti, Right Anti) to see how the row count and null handling change.
