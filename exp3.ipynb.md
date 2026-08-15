import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv("student_data.csv")

# Remove duplicate records
df = df.drop_duplicates()

# Histogram for age
plt.figure(figsize=(8, 5))
plt.hist(df["age"], bins=8, color="skyblue", edgecolor="black")
plt.title("Distribution of Students' Age")
plt.xlabel("Age")
plt.ylabel("Number of Students")
plt.show()

OUTPUT<img width="623" height="419" alt="Screenshot 2026-08-15 142150" src="https://github.com/user-attachments/assets/41488868-a0ec-4018-8b7a-d4b6da9d8335" />




import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("student_data.csv")
# Remove duplicates
df = df.drop_duplicates()
# Histogram for final grade
plt.figure(figsize=(8, 5))
plt.hist(df["G3"], bins=10, color="orange", edgecolor="black")
plt.title("Distribution of Students' Final Grades")
plt.xlabel("Final Grade (G3)")
plt.ylabel("Number of Students")
plt.show()

OUTPUT

<img width="628" height="415" alt="Screenshot 2026-08-15 142338" src="https://github.com/user-attachments/assets/b49bef4d-4243-4dee-8576-3aec9d7d1c5a" />



import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("student_data.csv")
df = df.drop_duplicates()
plt.figure(figsize=(8, 5))
plt.hist(df["G1"], bins=10, alpha=0.5, label="G1", edgecolor="black")
plt.hist(df["G2"], bins=10, alpha=0.5, label="G2", edgecolor="black")
plt.hist(df["G3"], bins=10, alpha=0.5, label="G3", edgecolor="black")
plt.title("Distribution of Student Grades")
plt.xlabel("Grade")
plt.ylabel("Number of Students")
plt.legend()
plt.show()

OUTPUT<img width="624" height="410" alt="Screenshot 2026-08-15 142618" src="https://github.com/user-attachments/assets/e9333a83-335d-4d59-8a33-b6033701f898" />



