# 🎓 ICT Year 2 — Python Projects Portfolio

A collection of three Python projects covering CLI tooling, web scraping with database management, and data science with interactive visualization.

**Authors:** Iyad Kabel, Y.H.Y.M.Bakr Raiyan, Amro Jamal Al Ddın, Christ Barhith Boka, Muzammal Yaquib
**Program:** Software Engineering, Year 2

---

## 📂 Projects

| # | Project | Stack | Description |
|---|---------|-------|-------------|
| 1 | [Study Organizer](#1--study-organizer) | Python CLI | Weekly study schedule generator |
| 2 | [Movie Database Manager](#2--movie-database-manager) | Python + MongoDB + BeautifulSoup | IMDb scraper with OOP design |
| 3 | [Istanbul Traffic Accidents Analysis](#3--istanbul-traffic-accidents-analysis) | Python + React.js | Data scraping, analysis & dashboard |

---

---

## 1. 📚 Study Organizer

A command-line program that builds and manages a structured weekly study schedule with prioritized subjects, time-block tips, AI tool suggestions, and goal tracking.

### Features

- **Smart Subject Prioritization** — Reorders subjects from most to least difficult.
- **Time Block Recommendations** — Morning, afternoon, and evening focus tips.
- **Pomodoro-Style Schedule** — 10 daily sessions of 25 min study + 5 min break.
- **AI Tool Suggestions** — Recommends a specialized tool per subject.
- **Weekly Goal Calculation** — Computes total study time per subject.
- **Schedule Persistence** — Saves to `study_schedule.json`.
- **Day Filtering** — View a single day via a CLI flag.

### Subjects (by priority)

| Priority | Subject           |
|----------|------------------|
| 1        | Math             |
| 2        | Physics          |
| 3        | History          |
| 4        | Turkish Language |
| 5        | Art              |

### Requirements

- Python 3.x
- Standard library only: `argparse`, `os`, `json`, `datetime`

### Usage

```bash
# Full weekly schedule
python study_organizer.py

# Single day
python study_organizer.py --day Monday
python study_organizer.py -d Friday
```

**Valid days:** `Monday` `Tuesday` `Wednesday` `Thursday` `Friday`

### Output

1. Today's date
2. Prioritized subject order
3. Optimal time slots with focus tips
4. 10-session daily log for each study day
5. Schedule saved to `study_schedule.json`
6. Recommended AI tools per subject
7. One-week target completion date
8. Weekly study goals (4 hrs 10 min per subject)

### Recommended AI Tools

| Subject          | Tool         |
|-----------------|--------------|
| Math            | GeoGebra     |
| Physics         | Gauth        |
| Turkish Language| Talkpal      |
| History         | Historact AI |
| Art             | Prisma       |

### Schedule File (`study_schedule.json`)

```json
{
    "Monday": [
        {
            "log": 1,
            "subject": "Math",
            "duration": "25 min study, 5 min break"
        }
    ]
}
```

### Project Structure

```
study-organizer/
├── study_organizer.py
├── study_schedule.json   # Auto-generated on first run
└── README.md
```

---

---

## 2. 🎬 Movie Database Manager

A Python application that scrapes movie data from IMDb using BeautifulSoup, optionally integrates with the TMDb API, and stores everything in MongoDB with a full OOP architecture.

### Features

- Scrapes IMDb Top 250 movies with BeautifulSoup
- Optional TMDb API integration for additional data
- MongoDB storage with duplicate prevention
- Full OOP design: abstract classes, inheritance, protocols, data classes, type hints, and ORM pattern

### Bonus Points

| Category    | Implementation                             | Points |
|-------------|--------------------------------------------|--------|
| Database    | MongoDB with CRUD operations               | +15    |
| OOP         | Data classes + type checking + ORM pattern | +15    |
| Web Scraping| BeautifulSoup + API                        | Base   |
| **Total**   |                                            | **+30**|

### Requirements

- Python 3.8+
- MongoDB installed and running locally
- (Optional) TMDb API key

### Dependencies

```
requests
beautifulsoup4
pymongo
lxml
```

### Installation

**1. Install MongoDB**

```bash
# macOS
brew install mongodb-community && brew services start mongodb-community

# Linux
sudo apt-get install mongodb && sudo systemctl start mongodb

# Windows — download from https://www.mongodb.com/try/download/community
```

**2. Clone & set up**

```bash
git clone <your-repo-url>
cd movie-database-manager
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

**3. (Optional) Get a TMDb API key**

Create a free account at [themoviedb.org](https://www.themoviedb.org/), go to Settings > API, and request a key.

**4. Run**

```bash
python main.py
```

### OOP Highlights

```python
# Data class
@dataclass
class Movie:
    title: str
    year: int
    rating: float
    genres: List[str] = field(default_factory=list)

# Abstract base class
class Scraper(ABC):
    @abstractmethod
    def scrape(self) -> List[Movie]:
        pass

# Protocol for type safety
class DatabaseProtocol(Protocol):
    def save_movie(self, movie: Movie) -> bool: ...

# ORM-like pattern
class MongoDBManager:
    def save_movie(self, movie: Movie) -> bool:
        return self.collection.insert_one(movie.to_dict())
```

### Project Structure

```
project2&3(movie_scraper)/
├── models.py
├── scraper_base.py
├── imdb_scraper.py
├── tmdb_scraper.py
├── database.py
├── manager.py
├── main.py
├── requirements.txt
└── README.md
```

---

---

## 3. 🚦 Istanbul Traffic Accidents Analysis

A data science project that scrapes traffic accident data from multiple news sources, cleans and analyzes it using statistical methods, and presents findings through an interactive React.js dashboard.

### Features

- Web scraping from 3 sources (IPA, Daily Sabah, Xinhua)
- Multi-step data cleaning pipeline
- IQR-based anomaly detection
- Interactive React.js + Recharts dashboard

### Bonus Points

| Category            | Implementation                  | Points |
|---------------------|---------------------------------|--------|
| Messy web data      | Scraped from 3 sources          | +10    |
| Data science        | Anomaly detection with IQR      | +15    |
| React visualization | Interactive dashboard           | +15    |
| **Total**           |                                 | **+40**|

### Requirements

- Python 3.8+
- pip packages: `requests`, `beautifulsoup4`, `pandas`, `numpy`

### Installation

```bash
git clone <your-repo-url>
cd istanbul-traffic-analysis

python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt

python analysis.py
```

Open `dashboard.html` in a browser to view the interactive visualization.

### Data Cleaning Pipeline

| Step | Problem | Solution |
|------|---------|----------|
| 1 | 3 different date formats | Standardized with `pd.to_datetime()` |
| 2 | 15% missing weather data | Filled with "Unknown" category |
| 3 | Numbers written in Turkish text | Custom Turkish number parser |
| 4 | Duplicate records across sources | Matched by date + time + location |
| 5 | Mixed percentages vs. absolute counts | Normalized to absolute counts |
| 6 | Impossible values (e.g., 9999/hour) | Removed via IQR outlier detection |

### Statistical Analysis

**Descriptive stats:**
- Mean: 118.2 accidents/month
- Median: 120 accidents/month
- Range: 87 (Feb) – 238 (Sep)

**IQR Anomaly Detection:**
```
Q1 = 98 | Q3 = 142 | IQR = 44
Upper Bound = Q3 + 1.5 × IQR = 208
Lower Bound = Q1 - 1.5 × IQR = 32

→ September (238) is a statistical anomaly (+30 above upper bound)
```

### Key Findings

- **Peak hours:** 16:00–18:00 (evening rush, 203 accidents)
- **Weather:** Clear weather accounts for 49% of accidents due to higher traffic volume
- **September anomaly:** 101% above monthly average — likely linked to school season start and construction

### Project Structure

```
python_project4(istanbul_traffic_analysis)/
├── scraper.py
├── analysis.py
├── dashboard.html
├── scraped_accidents.csv
├── requirements.txt
└── README.md
```

---

## 📄 License

All projects created for educational purposes. Traffic data sourced from publicly available news sources; proper attribution provided.
