mport pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# =========================================================
# STEP 1: LOAD DATASET
# =========================================================

df = pd.read_csv(
    '/mnt/data/b89808f8-95e6-42fc-a7be-5844fbcec87d.csv'
)

# =========================================================
# STEP 2: CONVERT NUMERICAL COLUMNS
# =========================================================

df['Buy'] = pd.to_numeric(df['Buy'], errors='coerce')
df['Sell'] = pd.to_numeric(df['Sell'], errors='coerce')
df['Miles Price'] = pd.to_numeric(df['Miles Price'], errors='coerce')

# =========================================================
# STEP 3: SELECT COLUMNS
# =========================================================

cat_column = 'Type'

num_column = 'Buy'

x_line_column = 'Seasonal Availability'

y_line_column = 'Buy'

# =========================================================
# STEP 4: CREATE DASHBOARD
# =========================================================

fig, axes = plt.subplots(2, 2, figsize=(14, 10))

plt.subplots_adjust(hspace=0.4, wspace=0.3)

# =========================================================
# 1. PIE CHART
# =========================================================

df[cat_column].value_counts().head(5).plot.pie(
    ax=axes[0, 0],
    autopct='%1.1f%%',
    startangle=90
)

axes[0, 0].set_title(
    'Pie Chart: Top 5 Types',
    fontsize=11,
    fontweight='bold'
)

axes[0, 0].set_ylabel('')


# =========================================================
# 2. HISTOGRAM
# =========================================================

sns.histplot(
    data=df,
    x=num_column,
    kde=True,
    ax=axes[0, 1]
)

axes[0, 1].set_title(
    'Histogram: Buy Price Distribution',
    fontsize=11,
    fontweight='bold'
)

axes[0, 1].set_xlabel('Buy Price')
axes[0, 1].set_ylabel('Frequency')


# =========================================================
# 3. LINE CHART
# =========================================================

line_data = (
    df.groupby(x_line_column)[y_line_column]
    .mean()
    .reset_index()
)

sns.lineplot(
    data=line_data,
    x=x_line_column,
    y=y_line_column,
    marker='o',
    ax=axes[1, 0]
)

axes[1, 0].set_title(
    'Line Chart: Average Buy Price by Seasonal Availability',
    fontsize=11,
    fontweight='bold'
)

axes[1, 0].set_xlabel('Seasonal Availability')
axes[1, 0].set_ylabel('Average Buy Price')

axes[1, 0].tick_params(axis='x', rotation=45)


# =========================================================
# 4. CORRELATION HEATMAP
# =========================================================

num_df = df[['Buy', 'Sell', 'Miles Price']]

sns.heatmap(
    num_df.corr(),
    annot=True,
    fmt='.2f',
    ax=axes[1, 1]
)

axes[1, 1].set_title(
    'Correlation Heatmap',
    fontsize=11,
    fontweight='bold'
)

# =========================================================
# MAIN TITLE
# =========================================================

plt.suptitle(
    'Item Data Story Dashboard',
    fontsize=15,
    fontweight='bold'
)



OUTPUT
<img width="917" height="742" alt="Screenshot 2026-08-14 161112" src="https://github.com/user-attachments/assets/84ee698d-e83c-44b6-8419-f27c63bc7d9e" />


plt.show()
