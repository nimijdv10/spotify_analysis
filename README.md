# Spotify Listening History — Personal Data Analysis

A personal end-to-end data analysis of 7 years of Spotify streaming history using Python. Built as a portfolio project to demonstrate analyst thinking not just reporting numbers, but understanding what caused them.

---

## Project motivation

As a data analyst, the goal isn't just to produce numbers but to explain what's behind them. I used my own Spotify extended streaming history to apply core statistical concepts to data I actually care about, and to tell a story that goes beyond the output.

---

## Dataset

- **Source:** Spotify Extended Streaming History (requested via Spotify Privacy Settings)
- **Period:** 2019 – 2026
- **Size:** 82,848 rows × 20 columns
- **Format:** JSON files (`StreamingHistory_Audio_*.json`)

Key columns used:

| Column | Description |
|---|---|
| `ts` | Timestamp of play (UTC) |
| `ms_played` | Milliseconds played |
| `master_metadata_track_name` | Track name |
| `master_metadata_album_artist_name` | Artist name |
| `platform` | Device used |
| `conn_country` | Country of connection |

---

## Tools & libraries

- Python 3
- pandas
- matplotlib
- seaborn
- Google Colab

---

## Project structure

```
spotify-analysis/
│
├── spotify_analytics.ipynb   # Main analysis notebook
├── README.md                 # Project documentation
│
└── outputs/
    ├── play_distribution.png
    ├── top_15_artists.png
    ├── listening_heatmap.png  
    └── yoy_change.png
```

---

## Key findings

### 1. Taylor Swift dominance
6,087 plays which is nearly 2x my #2 artist (Pritam). That's 327 hours, or 13 full days of listening. My roommate was a Swiftie in 2023. The data tells the rest.

### 2. Frequency vs duration — the Katy Perry insight
Katy Perry ranks **#10 by play count** but jumps to **#7 by total minutes listened**. Two metrics, two completely different stories. Knowing which metric to use is what separates a useful analysis from a misleading one.

### 3. Life events in the data
My listening spiked **+73.3% in 2023**, it is the year I moved to Canada for my Master's. New city, daily commutes on public transport, background music at the workplace. The data captured a life change before I consciously noticed it.

### 4. Mean vs median — understanding skew
- Mean play time: **2.93 min**
- Median play time: **3.26 min**
- Mean < Median → **left skew**

A pocket of short plays drags the mean below the median. Reporting only the mean would underrepresent typical listening behaviour. Both metrics are reported with an explanation of the gap.

### 5. 2020 anomaly
Only 13 unique tracks in all of 2020 that's a **-96.3% drop** from 2019. Something happened that year. The data doesn't explain why. But I know.

---

## Statistical concepts applied

| Concept | Application |
|---|---|
| Mean vs median | Play duration analysis, skew detection |
| Distribution & skewness | Histogram of play durations |
| IQR & outlier detection | Identifying long plays (mantras, nonstop mixes) |
| YoY % change | Tracking listening growth year over year |
| Frequency vs duration | Artist ranking by plays vs total minutes |
| Cohort analysis | Breaking behaviour by year |
| Data cleaning | Handling null values, string "None", timezone conversion |

---

## Data cleaning decisions

- Timestamps converted from UTC to `America/Toronto` (primary listening location from 2023)
- Null artist/track rows (63 rows of podcast/audiobook entries) removed after replacing string `"None"` with `NaN`
- Short plays retained deliberately as skips are behaviour too
- Outliers (plays > Q3 + 1.5×IQR) identified and examined which mostly included long devotional tracks and nonstop mixes, not errors

---

## How to run

1. Request your Spotify Extended Streaming History at `spotify.com → Account → Privacy Settings → Download your data`
2. Upload the JSON files to Google Colab
3. Run `spotify_analytics.ipynb` top to bottom

---

## Author

**Nimisha Mavjibhai Jadav**  
Aspiring Data Analyst | Python · SQL · Excel · Tableau 
[LinkedIn](https://www.linkedin.com/in/nimisha-jadav/) · 
