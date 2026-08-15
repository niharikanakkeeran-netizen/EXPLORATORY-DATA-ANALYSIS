import pandas as pd
import matplotlib.pyplot as plt


# ============================================================
# Load the Student Performance Dataset
# ============================================================

df = pd.read_csv("student_data.csv")


# ============================================================
# Display First 7 Rows
# ============================================================

first7 = df.head(7)

print("First 7 Rows of the Student Performance Dataset")
print(first7)


# ============================================================
# Basic Dataset Information
# ============================================================

print("\nDataset Shape")
print(f"Rows: {df.shape[0]}")
print(f"Columns: {df.shape[1]}")


print("\nDataset Information")
df.info()


# ============================================================
# Statistical Summary
# ============================================================

print("\nStatistical Summary")
print(df.describe())


# ============================================================
# Average Grades
# ============================================================

average_grades = df[["G1", "G2", "G3"]].mean()

print("\nAverage Grades")
print(average_grades)


# ============================================================
# Plot Average Grades
# ============================================================

plt.figure(figsize=(8, 5))

average_grades.plot(
    kind="bar",
    color=["skyblue", "orange", "green"]
)

plt.title("Average Student Grades")
plt.xlabel("Grade Period")
plt.ylabel("Average Grade")
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()


OUTPUT

First 7 Rows of the Student Performance Dataset
  school sex  age address famsize Pstatus  Medu  Fedu      Mjob      Fjob  \
0     GP   F   18       U     GT3       A     4     4   at_home   teacher   
1     GP   F   17       U     GT3       T     1     1   at_home     other   
2     GP   F   15       U     LE3       T     1     1   at_home     other   
3     GP   F   15       U     GT3       T     4     2    health  services   
4     GP   F   16       U     GT3       T     3     3     other     other   
5     GP   M   16       U     LE3       T     4     3  services     other   
6     GP   M   16       U     LE3       T     2     2     other     other   

   ... famrel freetime  goout  Dalc  Walc health absences  G1  G2  G3  
0  ...      4        3      4     1     1      3        6   5   6   6  
1  ...      5        3      3     1     1      3        4   5   5   6  
2  ...      4        3      2     2     3      3       10   7   8  10  
3  ...      3        2      2     1     1      5        2  15  14  15  
4  ...      4        3      2     1     2      5        4   6  10  10  
5  ...      5        4      2     1     2      5       10  15  15  15  
6  ...      4        4      4     1     1      3        0  12  12  11  

[7 rows x 33 columns]

Dataset Shape
Rows: 395
Columns: 33

Dataset Information
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 395 entries, 0 to 394
Data columns (total 33 columns):
 #   Column      Non-Null Count  Dtype 
---  ------      --------------  ----- 
 0   school      395 non-null    object
 1   sex         395 non-null    object
 2   age         395 non-null    int64 
 3   address     395 non-null    object
 4   famsize     395 non-null    object
 5   Pstatus     395 non-null    object
 6   Medu        395 non-null    int64 
 7   Fedu        395 non-null    int64 
 8   Mjob        395 non-null    object
 9   Fjob        395 non-null    object
 10  reason      395 non-null    object
 11  guardian    395 non-null    object
 12  traveltime  395 non-null    int64 
 13  studytime   395 non-null    int64 
 14  failures    395 non-null    int64 
 15  schoolsup   395 non-null    object
 16  famsup      395 non-null    object
 17  paid        395 non-null    object
 18  activities  395 non-null    object
 19  nursery     395 non-null    object
 20  higher      395 non-null    object
 21  internet    395 non-null    object
 22  romantic    395 non-null    object
 23  famrel      395 non-null    int64 
 24  freetime    395 non-null    int64 
 25  goout       395 non-null    int64 
 26  Dalc        395 non-null    int64 
 27  Walc        395 non-null    int64 
 28  health      395 non-null    int64 
 29  absences    395 non-null    int64 
 30  G1          395 non-null    int64 
 31  G2          395 non-null    int64 
 32  G3          395 non-null    int64 
dtypes: int64(16), object(17)
memory usage: 102.0+ KB

Statistical Summary
              age        Medu        Fedu  traveltime   studytime    failures  \
count  395.000000  395.000000  395.000000  395.000000  395.000000  395.000000   
mean    16.696203    2.749367    2.521519    1.448101    2.035443    0.334177   
std      1.276043    1.094735    1.088201    0.697505    0.839240    0.743651   
min     15.000000    0.000000    0.000000    1.000000    1.000000    0.000000   
25%     16.000000    2.000000    2.000000    1.000000    1.000000    0.000000   
50%     17.000000    3.000000    2.000000    1.000000    2.000000    0.000000   
75%     18.000000    4.000000    3.000000    2.000000    2.000000    0.000000   
max     22.000000    4.000000    4.000000    4.000000    4.000000    3.000000   

           famrel    freetime       goout        Dalc        Walc      health  \
count  395.000000  395.000000  395.000000  395.000000  395.000000  395.000000   
mean     3.944304    3.235443    3.108861    1.481013    2.291139    3.554430   
std      0.896659    0.998862    1.113278    0.890741    1.287897    1.390303   
min      1.000000    1.000000    1.000000    1.000000    1.000000    1.000000   
25%      4.000000    3.000000    2.000000    1.000000    1.000000    3.000000   
50%      4.000000    3.000000    3.000000    1.000000    2.000000    4.000000   
75%      5.000000    4.000000    4.000000    2.000000    3.000000    5.000000   
max      5.000000    5.000000    5.000000    5.000000    5.000000    5.000000   

         absences          G1          G2          G3  
count  395.000000  395.000000  395.000000  395.000000  
mean     5.708861   10.908861   10.713924   10.415190  
std      8.003096    3.319195    3.761505    4.581443  
min      0.000000    3.000000    0.000000    0.000000  
25%      0.000000    8.000000    9.000000    8.000000  
50%      4.000000   11.000000   11.000000   11.000000  
75%      8.000000   13.000000   13.000000   14.000000  
max     75.000000   19.000000   19.000000   20.000000  

Average Grades
G1    10.908861
G2    10.713924
G3    10.415190
dtype: float64<img width="712" height="434" alt="Screenshot 2026-08-15 141702" src="https://github.com/user-attachments/assets/b6a50906-00e4-4b18-92cb-fae5ce91d12e" />
<img width="707" height="440" alt="Screenshot 2026-08-15 141605" src="https://github.com/user-attachments/assets/962cbe87-d770-43d3-9c3d-a2b0a8aeaf22" />
<img width="612" height="385" alt="Screenshot 2026-08-15 141405" src="https://github.com/user-attachments/assets/53ee98c7-500d-4f4d-bb06-4183ae889b30" />
<img width="519" height="525" alt="Screenshot 2026-08-15 141242" src="https://github.com/user-attachments/assets/e3dc4d7c-c96c-4d5b-b697-9a7a9f2ad927" />
<img width="719" height="442" alt="Screenshot 2026-08-15 141124" src="https://github.com/user-attachments/assets/b5426e53-fbfc-46ec-9f50-e430500acf01" />

