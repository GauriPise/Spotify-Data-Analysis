# 🎧 Spotify Data Analysis 

---

## 📑 Table of Contents

1. Project Overview  
2. Dataset Description  
3. File Structure & Images  
4. Data Preparation & Transformations  
5. DAX Measures  
6. Key KPI Measures  
7. Artist / Genre Measures  
8. Day / Time Analysis  
9. Dashboard Pages & Visualizations  
10. Navigation, Bookmarks & Page Navigator  
11. Drill-Down & Interactivity  
12. Performance Optimization  
13. How to Reproduce / Deliverables  
14. Business Insights & Recommendations  

---

# 📌 1. Project Overview

This project analyzes Spotify music streaming data to uncover insights related to:

- 🎵 Song popularity  
- 🎤 Artist performance  
- 📈 Streaming trends  
- 👥 User listening behavior  

### 🎯 Objective:
To help understand **music trends, audience preferences, and top-performing artists** using data analytics.

---

# 📊 2. Dataset Description

The dataset contains Spotify track-level data:

| Column Name        | Description |
|-------------------|------------|
| Track_ID          | Unique track identifier |
| Track_Name        | Name of the song |
| Artist_Name       | Artist performing the song |
| Genre             | Music genre |
| Release_Date      | Date of release |
| Streams           | Number of streams |
| Popularity        | Popularity score |
| Duration          | Song duration |
| Danceability      | Danceability score |
| Energy            | Energy level |
| Tempo             | Beats per minute |

---

# 🧹 3. Data Preparation & Transformations

## Step 1: Data Cleaning
- Removed null values  
- Removed duplicate records  
- Standardized column names  

---

## Step 2: Data Type Conversion
- Converted Order_Date & Order_Time to datetime  
- Ensured numeric columns (Order_Value, Delivery_Time)  

---

## Step 3: Feature Engineering

### Extract Date Components
```python id="s1"
df['Year'] = df['Order_Date'].dt.year
df['Month'] = df['Order_Date'].dt.month
df['Day'] = df['Order_Date'].dt.day_name()

```
### Extract Hour
df['Hour'] = pd.to_datetime(df['Order_Time']).dt.hour
## Step 4: Create Day / Night Flag
df['Day_Night'] = df['Hour'].apply(lambda x: 'Day' if 6 <= x < 18 else 'Night')

## Step 5: Data Validation
- Checked delivery time consistency
- Verified order values

--
# 📐 5. DAX Measures (Power BI)
```
``` 
- ## Total Streams
  Total Streams = SUM('Spotify'[Streams])
- ## Total Tracks
  Total Tracks = COUNT('Spotify'[Track_ID])
- ## Average Popularity
  Avg Popularity = AVERAGE('Spotify'[Popularity])
---

# 📊 6. Key KPI Measures
- 🎵 Total Tracks
- 📈 Total Streams
- ⭐ Average Popularity
- 🎤 Top Artist
 --
 
 # 🎤 7. Artist / Genre Measures
- ## Streams by Artist
  Artist Streams = SUM('Spotify'[Streams])
- ## Streams by Genre
  Genre Streams = SUM('Spotify'[Streams])
---

# 📊 8. Dashboard Insights: Chart-by-chart analysis

## A)Excel:

### 1)Chart Type: Column chart
- Insight: Top 10 songs by streams
- Minimum stream count :218 and Song name :About Damn Time
- Maximum stream count :340 and Song name :SNAP

### 2) Chart Type: Pie chart
- Insight: Sum of streams by mode 
- Min:Major:1.95836E+1
- Max:Minor:1.29623E+1

### 3) Chart Type: Line chart
- Insight: Top 10 track name by sum of danceability and energy
- a)Sum of danceability: Max:168 and track name : About Damn Time
		           - Min:105 and track name : Let It Snow
- b)Sum of energy:Max: 163 and track name : Numb
		           - Min:56 and track name : Let It Snow
### 4) Chart Type: Line chart
- Insight: Count of track name by released year
- Min year:1930 and count of track name :1
- Max year:2022 and count of track name: 422

### 5) Chart Type: Bar chart
- Insight: Top 10 artist with most tracks in dataset
-  Mix track :8 and artist name:Field,BTS,Drake,21 Savage 
-  Max track :34 and artist name: Taylor Swift 

### 6) Chart Type: Donught chart
- Insight: Count of key by mode
-  Min:Minor:383
- Max:Major:475

### 7) Chart Type: Line chart
- Insight: Count of artist name by year and month
-  Min year:1930 ,month 1,count :1
-  Max year:2022,month :5,count:75

### 8) Chart Type: Column chart
- Insight: Top 15 sum of artist count in Spotify playlist
-  Min value:5 and artist count:182,197,332,577,859,894,1112,1845,1890,2341
-  Max value:12 and artist count :1150
---

## B)Microsoft Power Bi:

### 1) Chart Type: Line chart
-  Insight: Distribution of bpm across songs
-  Minimum count of song:1 and  bpm:67,73,74,75,86
-  Maximum count of song:39 and bpm:120

### 2) Chart Type: Bar chart
-  Insight: Top 10 streams by track name
-  Min stream:2591224264, track name: Closer
-  Max stream:3703895074, track name: Blinding Lights

### 3) Chart Type: Column chart
-  Insight: Top 20 artist name by count of track name 
-  Min count track:1, track name: Wizkid,Toian,Metro Boomin,Don Toliver,Beam
-  Max count track:2, track name: XXXTENTACION

### 4) Chart Type: Line chart
-  Insight: Count of track name by released year and month 
-  Min Count of track name : 1,year 2020 ,month:8
-  Max count track name:75,year 2020,month:5

### 5) Chart Type: Column chart
-  Insight: Count of track name by key
-  Max count track :5,key:C#
-  Min count track:1,key:A

### 6) Chart Type: Pie chart
-  Insight: Count of key by mode
-  -  Min:Minor:430(42.29%)
-  Max: Major:550(57.71%)

### 7) Chart Type: Line chart
-  Insight: Avg of streams by released year
-  Min Year:1930 and avg of stream:90598517.00
-  Max: Year:1975 and avg of stream:2103052676.00


### 8) Chart Type: Donught chart
-  Insight: Avg of streams by mode
-  Min: Minor and avg of stream:485.94 M(47.61%)
-  Max: Major and avg of stream:534.83 M(52.39%)

## C) Tableau Public Edition 

### 1) Chart Type: Bar chart
-  Insight: Top 10 songs by streams
-  Min: stream:2565529629 and track name : Starboy
-  Max :Stream:3703895074 and track name Blinding Lights

### 2) Chart Type: Pie chart
-  Insight: Song distribution by mode
-  Min: Minor and song distribution :403
-  Max: Major and song distribution:550

### 3) Chart Type: Packed bubble chart
-  Insight: Top 10 artist popularity
-  Min Popularity: Imagine Dragons, Arctic Monkeys, Bruno Mars
-  Max Popularity:Ed Sheeran, The Weekend , Taylor Swift

### 4) Chart Type: Line chart
-  Insight: Sum of liveness, valence, speechiness , instrumentalness, energy by released year
-  a)Liveness: Min:8, year:1930 and max:7434
-  b)Valence: Min:49, year:1930 and max:20699
-  c)Speechiness: Min:5, year:1930 and max:4717
-  d)Instrumentalness: Min:4, year:1930 and max:517
-  e)Energy: Min:80 ,year:1930 and max:25560


### 5) Chart Type: Column chart
-  Insight: Top 10 artist by total streams
-  Min stream:176474912 and artist name :Ed Sheeran
-  Max stream:7436274050 and artist name :Bad Bunny

### 6) Chart Type: Pie chart
-  Insight: Sum of bpm by mode
-  Min :Minor:49143
-  Max:Major:67638

### 7) Chart Type: Area chart
-  Insight: Monthly song releases 
-  Min Count of track name:46,released month:8
-  Max count of track name:134,released month:1

### 8) Chart Type: Tree map chart
-  Insight: Key analysis
-  Min stream:18250205825 and key: D#
-  Max stream:72513629843 and key :C#
---

# 🔍 9. Drill-Down & Interactivity
- ## Drill-Down:
- Year → Track
- Artist → Song
- ## Filters:
- Artist
- Genre
- Year
- ## Interactivity:
- Cross-filtering
- Dynamic visuals

---

- # #⚡ 10. Performance Optimization
- Removed unnecessary columns
- Optimized DAX
- Reduced visual load
---


# ⚡ 11. Performance Optimization
- Removed unnecessary columns
- Optimized DAX calculations
- Reduced visuals per page

---


--- 

# 📈 11. Business Insights & Recommendations

- 📊 Key Insights
- 🎤 Few artists dominate total streams
- 🎵 Certain genres outperform others
- 📈 Streaming trends increase over time
- ⭐ Popularity strongly impacts streams
---

# ⭐12. Conclusion

This project demonstrates:

- End-to-end Spotify data analysis
- Dashboard creation using Excel, Power BI & Tableau
- Strong business insight generation

# 💡13.Dashboard Images
### Excel Dashboard
<img src="https://github.com/GauriPise/Spotify-Data-Analysis/blob/main/Screenshot 2026-04-18 175251.png" width="1000"> <br>

--- 
### Power BI Dashboard
<img src="https://github.com/GauriPise/Spotify-Data-Analysis/blob/main/Screenshot 2026-04-18 175353.png" width="1000"> <br>




