# Data-Cleaning-Reporting-Automation
import pandas as pd
# Load Dataset
df = pd.read_csv("data.csv")
print("Original Data:")
print(df.head())
# Remove Duplicate Records
df = df.drop_duplicates()
# Fill Missing Numeric Values with Mean
numeric_cols = df.select_dtypes(include=['number']).columns
for col in numeric_cols:
    df[col].fillna(df[col].mean(), inplace=True)
# Fill Missing Text Values
text_cols = df.select_dtypes(include=['object']).columns
for col in text_cols:
    df[col].fillna("Unknown", inplace=True)
# Save Cleaned Data
df.to_csv("cleaned_data.csv", index=False)
# Save Report
with open("report.txt", "w") as file:
    file.write("Data Cleaning Report
")
    file.write("-------------------
")
for key, value in report.items():
        file.write(f"{key}: {value}
")
print("
Cleaned data saved as 'cleaned_data.csv'")
print("Report saved as 'report.txt'")
# Generate Summary Report
report = {
"Total Rows": len(df),
"Total Columns": len(df.columns),
"Missing Values": df.isnull().sum().sum(),
"Duplicate Records": df.duplicated().sum()
}
print("
Data Cleaning Report")
print("---------------------")
for key, value in report.items():
print(f"{key}: {value}")