# Formula 1 Data Analysis Project

## Overview
This project provides tools to extract, analyze, and visualize Formula 1 racing data using the Ergast Motor Racing API. It allows users to fetch historical race results, driver standings, and other F1 statistics for data analysis purposes.

## Features
- Fetch race results across multiple F1 seasons
- Analyze driver performance and constructor dominance
- Generate visualizations of race statistics
- Extract driver standings and championship data
- Save data to CSV files for further analysis

## Requirements
- Python 3.6+
- Required Python packages:
  - requests
  - pandas
  - matplotlib
  - seaborn

## Installation

1. Clone this repository or download the script files
2. Install required packages:

```bash
pip install requests pandas matplotlib seaborn
```

## Usage

### Basic Usage

Run the main script to fetch and analyze F1 data:

```bash
python f1_analysis.py
```

By default, this will:
- Fetch race results for the 2019-2023 F1 seasons
- Save race results to `f1_race_results.csv`
- Generate visualization charts in PNG format
- Display summary statistics in the console
- Fetch and save driver standings for the most recent season

### Customizing Analysis

You can modify the seasons to analyze by editing the `seasons` list in the `main()` function:

```python
seasons = [2023, 2022, 2021, 2020, 2019]  # Change these years as needed
```

## Functions

### Data Fetching

#### `fetch_f1_race_results(year, round_num=None)`
Fetches race results for a specific year using the Ergast API.

- **Parameters**:
  - `year` (int): The F1 season year
  - `round_num` (int, optional): Specific race round number. If None, fetches all races.
- **Returns**:
  - Pandas DataFrame with race results

#### `fetch_multiple_seasons(seasons)`
Fetches F1 data for multiple seasons.

- **Parameters**:
  - `seasons` (list): List of years to fetch
- **Returns**:
  - DataFrame: Combined data from all seasons

#### `fetch_driver_standings(year)`
Fetches driver standings for a season.

- **Parameters**:
  - `year` (int): The F1 season year
- **Returns**:
  - DataFrame: Driver standings

### Analysis

#### `analyze_f1_data(df)`
Performs basic analysis on F1 race data.

- **Parameters**:
  - `df` (DataFrame): Pandas DataFrame with F1 race results
- **Returns**:
  - DataFrame: Analyzed data with additional calculated fields

#### `constructor_performance_analysis(df)`
Analyzes constructor performance trends over seasons.

- **Parameters**:
  - `df` (DataFrame): Pandas DataFrame with F1 race results

### Additional Data Functions

#### `fetch_qualifying_results(year, round_num=None)`
Fetches qualifying results for a season or specific race.

#### `fetch_lap_times(year, round_num, lap_num=None)`
Fetches lap times for a specific race.

#### `fetch_pit_stops(year, round_num)`
Fetches pit stop data for a race.

## Generated Files

The script generates the following files:

- **CSV Files**:
  - `f1_race_results.csv`: All race results for the fetched seasons
  - `f1_driver_standings_YYYY.csv`: Driver standings for the most recent season analyzed

- **Visualization Files**:
  - `driver_wins.png`: Bar chart of race wins by driver
  - `constructor_wins.png`: Bar chart of race wins by constructor
  - `constructor_wins_by_season.png`: Bar chart of constructor wins by season
  - `driver_points.png`: Bar chart of top 10 F1 drivers by points
  - `constructor_win_percentage.png`: Line chart of constructor win percentages by season

## Example Output

### Race Results CSV Format

| Grand Prix | Circuit | Date | Winner | Car | Laps | Time | Season |
|------------|---------|------|--------|-----|------|------|--------|
| Bahrain Grand Prix | Bahrain International Circuit | 2023-03-05 | Max Verstappen | Red Bull | 57 | 1:33:56.736 | 2023 |
| ... | ... | ... | ... | ... | ... | ... | ... |

### Driver Standings CSV Format

| Position | Driver | Constructor | Points | Wins |
|----------|--------|-------------|--------|------|
| 1 | Max Verstappen | Red Bull | 575.0 | 19 |
| 2 | Sergio Perez | Red Bull | 285.0 | 2 |
| ... | ... | ... | ... | ... |

## Ergast API Endpoints Used

This project utilizes the following Ergast API endpoints:

- Race Results: `http://ergast.com/api/f1/{year}/results.json`
- Driver Standings: `http://ergast.com/api/f1/{year}/driverStandings.json`

## Extending the Project

You can extend this project by:

1. Adding more API endpoints from the Ergast API
2. Creating additional visualizations
3. Implementing machine learning models to predict race outcomes
4. Building a web interface to display the data
5. Performing more complex statistical analysis

## API Rate Limiting

The Ergast API has a rate limit of 4 requests per second and 200 requests per hour. This script respects these limits, but if you're making frequent requests, consider adding delay between requests:

```python
import time
time.sleep(0.25)  # Add a 250ms delay between requests
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- [Ergast Motor Racing API](http://ergast.com/mrd/) for providing the Formula 1 data
- Formula 1 for the exciting sport that drives this project
