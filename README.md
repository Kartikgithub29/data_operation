import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Step 1: Load the Dataset
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Eve'],
    'Age': [25, np.nan, 23, 27, 29],
    'Salary': [50000, 54000, np.nan, 58000, 62000]
}
df = pd.DataFrame(data)

# Step 2: Fill Missing Values
df['Age'].fillna(df['Age'].mean(), inplace=True)
df['Salary'].fillna(df['Salary'].median(), inplace=True)

# Step 3: Transformations
df['Age'] = df['Age'].astype(int)
df['Salary'] = df['Salary'].astype(int)
df['Age_Group'] = pd.cut(df['Age'], bins=[20, 25, 30], labels=['20-25', '25-30'])

# Step 4: Visualizations
plt.figure(figsize=(10, 6))
sns.barplot(x='Name', y='Salary', data=df)
plt.title('Salary of Employees')
plt.xlabel('Name')
plt.ylabel('Salary')
plt.show()

# Save the dataset to CSV
df.to_csv('processed_data.csv', index=False)
