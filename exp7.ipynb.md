Program 1: Down-Sampling (Daily to Monthly)


import pandas as pd
# Load the dataset
df = pd.read_csv("netflix_titles.csv")
 
# Clean and convert date_added column into datetime format
df["date_added"] = df["date_added"].str.strip()
df["date_added"] = pd.to_datetime(df["date_added"], format="%B %d, %Y")
 
# Drop rows with missing dates
df = df.dropna(subset=["date_added"])
 
# Set date_added as index
df.set_index("date_added", inplace=True)
 
# Filter for the year 2021
df_2021 = df[df.index.year == 2021]
 
# Down-Sampling (Daily to Monthly) - count of titles added per month
monthly_data = df_2021.resample("ME").size()
monthly_data.name = "Titles_Added"
 
print("Monthly Summary of Titles Added (2021)")
print(monthly_data)

OUTPUT<img width="531" height="344" alt="Screenshot 2026-08-16 084639" src="https://github.com/user-attachments/assets/c5288d55-6231-4057-834d-750169d6797b" />



Program 2: Up-Sampling (Monthly to Daily)

import pandas as pd 
# Load the dataset
df = pd.read_csv("netflix_titles.csv")
 
# Clean and convert date_added column into datetime format
df["date_added"] = df["date_added"].str.strip()
df["date_added"] = pd.to_datetime(df["date_added"], format="%B %d, %Y")
 
# Drop rows with missing dates
df = df.dropna(subset=["date_added"])
 
# Set date_added as index
df.set_index("date_added", inplace=True)
 
# Filter for the year 2021
df_2021 = df[df.index.year == 2021]
 
# Down-Sampling (Daily to Monthly) - count of titles added per month
monthly_data = df_2021.resample("ME").size().to_frame(name="Titles_Added")
 
# Up-Sampling (Monthly to Daily)
daily_data = monthly_data.resample("D").ffill()
 
# Display the result
print("Up-Sampled Daily Data")
print(daily_data.head(15))

OUTPUT<img width="316" height="475" alt="Screenshot 2026-08-16 084745" src="https://github.com/user-attachments/assets/cf623f2b-5d02-47df-9c54-981b9ac2ccc7" />

