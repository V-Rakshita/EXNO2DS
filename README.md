# EXNO2DS
# AIM:
To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```python
import pandas as pd
import seaborn as sns
df = pd.read_csv("titanic_dataset.csv")
df
```
<img width="1561" height="699" alt="image" src="https://github.com/user-attachments/assets/8d217c0c-a684-4bb7-890d-1480713a6112" />

```python
df.shape
df.info
df.describe
```
<img width="742" height="770" alt="image" src="https://github.com/user-attachments/assets/9110815b-2ce9-4086-b8c5-0ca337fef34c" />

```python
df.set_index("PassengerId",inplace=True)
df
```
<img width="1368" height="648" alt="image" src="https://github.com/user-attachments/assets/547b106c-0fcd-4beb-b3b1-081b35b9e4ba" />

```python
df.isnull()
```
<img width="695" height="753" alt="image" src="https://github.com/user-attachments/assets/d382ef7b-8ac4-4c0c-ba06-20af1eaf10bb" />

```python
df.nunique()
```
<img width="242" height="224" alt="image" src="https://github.com/user-attachments/assets/d80a6919-7d79-4c97-aee9-6f8ea76a0cb3" />

```python
df['Survived'].value_counts()
```
<img width="392" height="143" alt="image" src="https://github.com/user-attachments/assets/937c9fac-ef59-4584-ae2c-f90dd153ea4a" />

```python
df.Pclass.unique()
```
<img width="554" height="92" alt="image" src="https://github.com/user-attachments/assets/f9d5fa69-948e-47ac-8ebd-512be7fcf93d" />

```python
df.Survived.unique()
```
<img width="337" height="95" alt="image" src="https://github.com/user-attachments/assets/6cd8a46c-8c6a-4f1c-b61e-80513706137d" />

### PLOTS
#### 1. Countplot 
```python
sns.countplot(x='Gender', hue='Pclass',data=df)
```
<img width="963" height="572" alt="image" src="https://github.com/user-attachments/assets/9b4b8cf0-0698-4766-9d3b-755e41433fd1" />

```python
df.rename(columns={'Sex':'Gender'},inplace=True)
df
```
<img width="958" height="618" alt="image" src="https://github.com/user-attachments/assets/c5ffe508-a515-4276-9621-577b4e6f7408" />

#### 2. Catplot
```python
sns.catplot(x='Survived',hue='Gender',data=df,kind='violin')
```
<img width="663" height="577" alt="image" src="https://github.com/user-attachments/assets/f49a4f94-26ae-4985-aecb-ef94d7c5d7c0" />

```python
sns.catplot(x='Survived',hue='Gender',data=df,kind='count')
```
<img width="641" height="583" alt="image" src="https://github.com/user-attachments/assets/9a836c18-1fc8-434e-8c14-7c8c53cb8213" />

```python
sns.catplot(x='Survived',col='Gender',data=df,kind='count')
```
<img width="951" height="524" alt="image" src="https://github.com/user-attachments/assets/c927bfbb-4312-4364-9193-17e2fe87bf05" />

#### 3. Boxplot
```python
sns.boxplot(data=df)
```
<img width="616" height="437" alt="image" src="https://github.com/user-attachments/assets/faf4fce4-10c6-4962-879a-78638d82d6cb" />

```python
df.boxplot(column='Age',by='Pclass')
```
<img width="593" height="544" alt="image" src="https://github.com/user-attachments/assets/1ab270f7-3008-41a3-8d3b-0423df6cd374" />

#### 4. Scatterplot
```python
sns.scatterplot(x='Age',y='Fare',data=df)
```
<img width="696" height="584" alt="image" src="https://github.com/user-attachments/assets/fb64ab10-37f3-473d-92d4-b2c85f418b2d" />

#### 5. Joinplot
```python
sns.jointplot(x='Age',y='Fare',data=df)
```
<img width="635" height="618" alt="image" src="https://github.com/user-attachments/assets/2afcd3bf-a6a4-4e63-9cba-b5f4c219dda1" />

```python
sns.jointplot(x='Age',y='Fare',data=df,kind='kde')
```
<img width="705" height="665" alt="image" src="https://github.com/user-attachments/assets/7832b08b-f070-4430-a83a-d2efac9ed863" />

```python
sns.jointplot(x='Age',y='Fare',data=df,kind='hist')
```
<img width="611" height="666" alt="image" src="https://github.com/user-attachments/assets/2d200458-d715-4818-9300-401a615b8b55" />

```python
sns.jointplot(x='Age',y='Fare',data=df,kind='scatter')
```
<img width="715" height="662" alt="image" src="https://github.com/user-attachments/assets/0e317f55-cb69-4560-82db-ff594fa26196" />

#### 6. Pairplot
```python
sns.pairplot(data=df)
```
<img width="854" height="810" alt="image" src="https://github.com/user-attachments/assets/06ff215e-3794-4386-9018-ac95debca717" />

#### 7. Heatmap
```python
cor1=df.select_dtypes(include=['number']).corr()
sns.heatmap(cor1,annot=True)
```
<img width="754" height="648" alt="image" src="https://github.com/user-attachments/assets/094d232b-b9c9-4470-938b-bbdd9efad904" />

```python
group = df.groupby(['Pclass','Survived'])
pclass_survived = group.size().unstack()
#unstack to convert back to dataframe
sns.heatmap(pclass_survived,annot=True,fmt='d')
```
<img width="726" height="652" alt="image" src="https://github.com/user-attachments/assets/c48b3eef-4534-4ec8-95ef-75e33c59420c" />

# RESULT
Hence, Exploratory Data Analysis has been performed on the given dataset.
