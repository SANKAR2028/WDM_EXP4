### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07/02/26
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```
import pandas as pd
import matplotlib.pyplot as plt

# Read CSV
visitor_df = pd.read_csv('/content/clustervisitor new.csv')

# Create age groups
age_groups = {
    'Young': visitor_df['Age'] <= 30,
    'Middle-aged': (visitor_df['Age'] > 30) & (visitor_df['Age'] <= 50),
    'Elderly': visitor_df['Age'] > 50
}

# Count visitors in each group
visitor_counts = []

for group, condition in age_groups.items():
    visitors_in_group = visitor_df[condition]
    count = len(visitors_in_group)
    visitor_counts.append(count)
    
    print(f"Count : {count}")
    print(f"Visitors in {group} age group:")
    print(visitors_in_group)


```
### Output:
<img width="555" height="723" alt="image" src="https://github.com/user-attachments/assets/666d1203-83a9-4a0b-82e2-c3acc2f663b8" />

### Visualization:
```

visitor_counts = []

for group, condition in age_groups.items():
    visitors_in_group = visitor_df[condition]
    count = len(visitors_in_group)
    visitor_counts.append(count)
    
    print(f"Count : {count}")
    print(f"Visitors in {group} age group:")
    print(visitors_in_group)

# Labels
age_group_labels = list(age_groups.keys())

# Different colors for each bar
colors = ['blue', 'green', 'red']

# Plot
plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, visitor_counts, color=colors)

plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')

plt.show()
```
### Output:
<img width="908" height="617" alt="image" src="https://github.com/user-attachments/assets/30c85d2a-e301-4c3e-bbe2-2bb1af1e0290" />

### Program:
```
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt
df1 = visitor_df ['Age']
df2 = visitor_df ['income']
df3 = pd.concat([df1,df2], axis = 1)

s= StandardScaler()
newdf= s.fit_transform(df3)
k = KMeans(n_clusters=4, random_state=42)
df3['cluster'] = k.fit_predict(newdf)
df3


```
### Output:
<img width="419" height="696" alt="image" src="https://github.com/user-attachments/assets/5b0c0b1d-0a69-4588-8934-cc57f2789f30" />

### Visualization:
```

import matplotlib.pyplot as plt
plt.scatter(df3['Age'], df3['income'], c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('visitors distribution in different clusters')
plt.show()
```
### Output:
<img width="842" height="515" alt="image" src="https://github.com/user-attachments/assets/1fa428c7-9fdb-42dc-b3b8-6868a085a613" />


### Result:
Thus the Cluster and Visitor Segmentation for Navigation patterns in Python is implemented Successfully.
