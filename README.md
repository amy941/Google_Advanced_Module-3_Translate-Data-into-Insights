# OVERVIEW:

# Case Study: TikTok 🎵
## Link here: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Module-3_Translate-Data-into-Insights)

## Scenario:

---


# PACE: Plan 📝
### **1) Imports, Links, and Loading:**

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

```python
data = pd.read_csv("tiktok_dataset.csv")
```

✍️ Library/package:

**- NumPy:** for *vector and matrix computations.*

**- Pandas:** for manipulating and analyzing *tabular data.*

**- matplotlib and seaborn:** to create *graphs, charts, and other data viz.*

  
---

# PACE: Analyze 🔎
### **2) Inspect the data:**

- ```.head()```, ```.size```, ```.shape```

✍️ ```.head()```: **display the first few rows** of the df.

```.size```: **# of rows multiple by # of columns** in a df.
    
```.shape```: an attribute in Python, will output **the dimension** of a dataset as: ([rows] , [columns])

      
- ```.info()```, ```.describe()```

✍️ ```.info()```: provide **total number of rows** (19,382) **and columns** (12), also state the **names and data types** of each column and **the size** of the df.

![info](https://github.com/user-attachments/assets/f0e528eb-5b3b-4617-91cf-cf0e16dcc966)

✍️ ```.describe()```: generate a table of **descriptive stats.**

![describe](https://github.com/user-attachments/assets/e56edd89-a1cc-46bb-b184-e6a4de071f36)

🔴 **Things should notice:**
  
* video_duration_sec: max = 60
* video_view_count: max = ~1,000,000 (1e6)
* video_like_count: max = ~660,000
* video_share_count: max = ~260,000
* video_download_count: max = ~15,000
* video_comment_count: max = ~10,000


---

# PACE: Construct 📊
### **3) Build visualizations:**

Create a **BOX PLOT** and **HISTOGRAM** to examine columns of ```count``` variables (ex: video_duration_sec, video_view_count, video_like_count,...)

```python
plt.figure(figsize=(7,1))
plt.title('video_duration_sec')

sns.boxplot(x=data['video_duration_sec'])

plt.show()
```
![boxplot_1](https://github.com/user-attachments/assets/2d2aa5b0-37e4-41c0-baf3-0a2657ed1e25)


✍️ ```sns.boxplot(x=data['video_duration_sec'])```: *sns.boxplot()* function takes positional argument of x, representing the x-axis in the data. The x-axis will represent the ```video_duration_sec``` column from the df. 

🔁 Write similar code blocks for ```video_view_count```, ```video_like_count```, ```video_comment_count```, ```video_share_count```, ```video_download_count```. The rest of my work: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Module-3_Translate-Data-into-Insights)

```python
plt.figure(figsize=(5,3))
plt.title('video duration sec_HISTOGRAM')

sns.histplot(data['video_duration_sec'], bins=range(0, 61, 5))  #start, stop, step

plt.show()
```

![hist_1](https://github.com/user-attachments/assets/0677cd51-6254-43ac-9583-8cd75b43b03e)

✍️ ```sns.histplot(x, bins, binrange, binwidth, ...)```: to generate a histogram in seaborn.
- x: a sequence of values representing the data you want to plot.
- bins: ```bins=range(0, 61, 5)``` defines the x-axis starts from 0, stops at 61, and increments by 5.

🔁 Write similar code blocks for ```video_view_count```, ```video_comment_count```, ```video_share_count``, ```video_download_count```

⚠️⚠️⚠️ Check out my work here: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Module-3_Translate-Data-into-Insights)

```python
plt.figure(figsize=(5,3))
plt.title('video like count_HISTOGRAM')

# Create histogram
ax = sns.histplot(data['video_like_count'], bins=range(0, (7 * 10**5 + 1), 10**5))

# Set x-tick positions
xticks = range(0, 7 * 10**5 + 1, 10**5)
ax.set_xticks(xticks)

# Set x-tick labels
labels = [str(i) + 'k' for i in range(0, 701, 100)]  # Adjust this to match the number of ticks
ax.set_xticklabels(labels)

plt.show()
```

![hist_2](https://github.com/user-attachments/assets/f8d62a96-59da-4dc8-8172-423dc95f0ce9)

✍️ ```sns.histplot(data['video_like_count'], bins=range(0, (7 * 10**5 + 1), 10**5))```: As we observed from the summary table for descriptive stats in step 2, the maximum of ```video_like_count``` is around 660,000 likes. Thus, we have to customize the bin range and bin width accordingly.
- Start from 0 up to....
- 7*(10^5) + 1 = 700,001 = 700K
- a step of 10^5= 100,000 = 100K

✍️ ```labels = [str(i) + 'k' for i in range(0, 701, 100)] ```: use for loops to iterate over ```range(0,701,100)``` (start from 0 to 700 in steps of 100). Each number ``i``` is converted into a string and ```k``` is added to show values in a more readable way (ex: 100k intead of 100000).

⚠️⚠️⚠️ Check out my work here: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Module-3_Translate-Data-into-Insights)

-----
**Create HISTOGRAM for claim status**

- Claim status by verification status
- Claim status by author ban status
- Median view counts by ban status

**Median view counts by ban status**: create a **bar plot** with 3 bars: one for each author ban status (active, under review, banned). The height of each bar should correspond with the **MEDIAN** number of views for all videos with that author ban status.

```python
ban_status_counts = data.groupby(['author_ban_status']).median(numeric_only=True).reset_index()

plt.figure(figsize=(5,3))
plt.title('Median view count by ban status')

sns.barplot(data=ban_status_counts,
             x= 'author_ban_status',
             y= 'video_view_count',
             order= ['active', 'under review', 'banned'],
             palette= {'active':'green', 'under review':'orange', 'banned':'red'},
             alpha= 0.5
)

plt.show()
```

![bar_median](https://github.com/user-attachments/assets/6b429f95-fe92-405c-92ae-643f05faa149)


✍️ ```ban_status_counts = data.groupby(['author_ban_status']).median(numeric_only=True).reset_index()```




✍️ 



⚠️⚠️⚠️ Check out my work here: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Module-3_Translate-Data-into-Insights)

---


# PACE: Execute 🤝

