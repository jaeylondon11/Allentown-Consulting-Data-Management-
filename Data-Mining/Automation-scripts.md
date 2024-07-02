# Data Reload Automation Script

```python
import pandas as pd
import mysql.connector
from datetime import datetime

# Connect to source system
source_db = mysql.connector.connect(
    host="source_host",
    user="source_user",
    password="source_password",
    database="source_db"
)

# Connect to target system
target_db = mysql.connector.connect(
    host="target_host",
    user="target_user",
    password="target_password",
    database="target_db"
)

# Extract data
query = "SELECT * FROM daily_transactions"
data = pd.read_sql(query, source_db)

# Transform data
data['date'] = pd.to_datetime(data['date']).dt.strftime('%Y-%m-%d')

# Load data
cursor = target_db.cursor()
for index, row in data.iterrows():
    cursor.execute(
        "INSERT INTO transactions (id, amount, date) VALUES (%s, %s, %s)",
        (row['transaction_id'], row['amount'], row['date'])
    )
target_db.commit()

#
