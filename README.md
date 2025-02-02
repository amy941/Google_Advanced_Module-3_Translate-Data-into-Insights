# OVERVIEW:

# Case Study: TikTok 🎵
## Link here: [Case Study: TikTok](............)

## Scenario:


## What I Learned:

## PACE: Plan 📝
**1) Imports, Links, and Loading:**

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

## PACE: Analyze 🔎
**2) Inspect the data:**

- ```.head()```, ```.size```, ```.shape```

✍️ ```.head()```: **display the first few rows** of the df.

  ```.size```: **# of rows multiple by # of columns** in a df.
    
  ```.shape```: an attribute in Python, will output **the dimension** of a dataset as: ([rows] , [columns])

      
- ```.info()```, ```.describe()```

✍️ ```.info()```: provide **total number of rows** (19,382) **and columns** (12), also state the **names and data types** of each column and **the size** of the df.

📸📸📸📸

```.describe()``: generate a table of **descriptive stats.**

📸📸📸📸

⚠️⚠️⚠️ **Things should notice:**
  
* video_duration_sec: max = 60
* video_view_count: max = ~1,000,000 (1e6)
* video_like_count: max = ~660,000
* video_share_count: max = ~260,000
* video_download_count: max = ~15,000
* video_comment_count: max = ~10,000


---

## PACE: Construct 📊
**3) Build visualizations:**

- Create a **BOX PLOT** and **HISTOGRAM** to examine columns of *count* variables (ex: video_duration_sec, video_view_count, video_like_count,...)

```python
plt.figure(figsize=(7,1))
plt.title('video_duration_sec')

sns.boxplot(x=data['video_duration_sec'])

plt.show()
```
📸📸📸📸

✍️ ```sns.boxplot(x=data['video_duration_sec'])```: *sns.boxplot()* function takes positional argument of x, representing the x-axis in the data. The x-axis will represent the ```video_duration_sec``` column from the df. 

🔁 Write similar code blocks for ```video_view_count```, ```video_like_count```, ```video_comment_count```, ```video_share_count``, ```video_download_count```

```python
plt.figure(figsize=(5,3))
plt.title('video duration sec_HISTOGRAM')

sns.histplot(data['video_duration_sec'], bins=range(0, 61, 5))  #start, stop, step

plt.show()
```

📸📸📸📸

✍️ ```sns.histplot(x, bins, binrange, binwidth, ...)```: to generate a histogram in seaborn.
- x: a sequence of values representing the data you want to plot.
- bins: ```bins=range(0, 61, 5)``` defines the x-axis starts at 0, stops at 61, and increments by 5.

🔁 Write similar code blocks for ```video_view_count```, ```video_comment_count```, ```video_share_count``, ```video_download_count```

⚠️⚠️⚠️ Check out my work here:

```python

---


## PACE: Execute 🤝

