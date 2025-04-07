# Netflix Data Cleaning Pipeline

This Jupyter Notebook performs data cleaning and type conversion on the Netflix Titles dataset (`netflix_titles.csv`). Below are the key changes made to the raw data.

## Changes Made

### 1. **Handled Missing Values**
- Identified null values with `data.isnull().sum()`
- Dropped all rows with missing values using `data.dropna(inplace=True)`
- Verified no nulls remain with `data.isnull().sum()`

### 2. **Data Type Conversions**
| Column | Original Type | New Type | Transformation |
|--------|--------------|----------|----------------|
| `date_added` | Object | `datetime64[ns]` | Converted to datetime (invalid→`NaT`) |
| `type` | Object | `category` | Optimized for low-cardinality |
| `rating` | Object | `category` | Optimized for low-cardinality |
| `release_year` | Object | `int64` | Coerced to numeric, filled NaN with 0 |
| Text columns* | Object | `string` | Ensured string type consistency |

*Text columns: `show_id`, `title`, `director`, `cast`, `country`, `duration`, `listed_in`, `description`

### 3. **Quality Checks**
- Removed duplicates: `data.duplicated().sum()`
- Verified final shape: `data.shape`
- Checked dtypes: `df.dtypes`

### 4. **Output**
- Saved cleaned data to: `New_Netflix_raw_data.csv`
- Confirmed successful save with print message

## How to Use
1. Place `netflix_titles.csv` in the same directory
2. Run all notebook cells sequentially
3. Find cleaned data in `New_Netflix_raw_data.csv`

## Dependencies
- Python 3.7+
- pandas
- numpy

