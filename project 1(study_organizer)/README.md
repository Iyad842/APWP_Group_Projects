# 📚 Study Organizer

A command-line Python program that helps students build and manage a structured weekly study schedule using prioritized subjects, time-block recommendations, AI tool suggestions, and goal tracking.

---

## Features

- **Smart Subject Prioritization** — Automatically reorders subjects from most to least difficult for optimal learning flow.
- **Time Block Recommendations** — Suggests morning, afternoon, and evening study windows based on focus levels.
- **Pomodoro-Style Schedule** — Generates a 10-log daily plan with 25-minute study sessions and 5-minute breaks.
- **AI Tool Suggestions** — Recommends a specialized AI tool for each subject (e.g., GeoGebra for Math, Prisma for Art).
- **Weekly Goal Calculation** — Computes total study hours per subject for the week.
- **Schedule Persistence** — Saves the generated schedule to a `study_schedule.json` file for later reference.
- **Day Filtering** — Optionally display the schedule for a single specific day via a command-line flag.

---

## Subjects

The program works with the following five subjects, reordered by difficulty:

| Priority | Subject          |
|----------|-----------------|
| 1        | Math            |
| 2        | Physics         |
| 3        | History         |
| 4        | Turkish Language|
| 5        | Art             |

---

## Requirements

- Python 3.x
- No external dependencies — uses only Python standard library modules:
  - `argparse`
  - `os`
  - `json`
  - `datetime`

---

## Usage

### Run the full weekly schedule

```bash
python study_organizer.py
```

### Show schedule for a specific day

```bash
python study_organizer.py --day Monday
```

or using the short flag:

```bash
python study_organizer.py -d Friday
```

**Valid day values:** `Monday`, `Tuesday`, `Wednesday`, `Thursday`, `Friday`

---

## Output

Running the program will:

1. Print today's date.
2. Display the prioritized subject order.
3. Show optimal study time slots with focus tips.
4. Generate and print a 10-session daily log for each study day.
5. Save the full schedule to `study_schedule.json`.
6. List recommended AI tools per subject.
7. Display a one-week target completion date.
8. Print weekly study goals per subject (4 hours and 10 minutes each).

### Example output snippet

```
Monday's Study Log:
  Log 1: Math - 25 min and 5 min break,
  Log 2: Physics - 25 min and 5 min break,
  Log 3: History - 25 min and 5 min break,
  ...
```

---

## Schedule File

The generated schedule is saved as `study_schedule.json` in the project directory. Example structure:

```json
{
    "Monday": [
        {
            "log": 1,
            "subject": "Math",
            "duration": "25 min study, 5 min break"
        },
        ...
    ],
    ...
}
```

---

## Recommended AI Tools

| Subject          | AI Tool       |
|-----------------|---------------|
| Math            | GeoGebra      |
| Physics         | Gauth         |
| Turkish Language| Talkpal       |
| History         | Historact AI  |
| Art             | Prisma        |

---

## Project Structure

```
study-organizer/
├── study_organizer.py      # Main program
├── study_schedule.json     # Auto-generated schedule (created on first run)
└── README.md
```

---

## Notes

- The schedule covers **Monday through Friday** only.
- Each subject receives equal weekly study time: **4 hours and 10 minutes** (10 sessions × 25 minutes).
- Subject cycling in the daily log is based on the prioritized order, wrapping around as needed.
