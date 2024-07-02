# Data Import and Export

## Import Data from Excel to Python
```python
import pandas as pd

# Import data from Excel
excel_data = pd.read_excel('path/to/excel_file.xlsx')

# Process data in Python
processed_data = excel_data.dropna()

# Export data back to Excel
processed_data.to_excel('path/to/processed_data.xlsx', index=False)

## Export Data from Python to Excel
```python
import pandas as pd

# Sample data
data = {'Name': ['John', 'Anna', 'Peter'], 'Age': [28, 24, 35]}

# Create DataFrame
df = pd.DataFrame(data)

# Export to Excel
df.to_excel('path/to/exported_data.xlsx', index=False)
