# Python-Excel Integration

```python
import pandas as pd
import openpyxl

# Load Excel file
excel_data = pd.read_excel('path/to/excel_file.xlsx')

# Process data in Python
excel_data['total'] = excel_data['quantity'] * excel_data['price']

# Save processed data back to Excel
excel_data.to_excel('path/to/processed_excel_file.xlsx', index=False)

# Use openpyxl for advanced Excel manipulations
wb = openpyxl.load_workbook('path/to/processed_excel_file.xlsx')
sheet = wb.active

# Add conditional formatting
from openpyxl.styles import PatternFill

for row in sheet.iter_rows(min_row=2, max_row=sheet.max_row, min_col=4, max_col=4):
    for cell in row:
        if cell.value > 100:
            cell.fill = PatternFill(start_color="FFEE08", end_color="FFEE08", fill_type="solid")

wb.save('path/to/processed_excel_file.xlsx')
