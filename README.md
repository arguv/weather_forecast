# Weather Forecast

Python examples for fetching weather data from Open-Meteo, processing it with pandas, and plotting it with Matplotlib. An internet connection is required.

## About the project

This learning project demonstrates how to request weather data from an API, organize it in a pandas DataFrame, calculate temperature statistics, and export a chart and CSV file.

The main script, `py_weather_forecast.py`, shows Paris temperatures for the past seven completed days. Despite its filename, it displays recent past weather rather than a future forecast. Temperatures are in degrees Celsius.

## Set up the project

Install Python 3.9 or newer and Git, then follow these steps.

### 1. Clone the repository

```bash
git clone https://github.com/arguv/weather_forecast.git
cd weather_forecast
```

If you already have the project locally, open a terminal in its root directory.

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate the virtual environment

On Linux or macOS:

```bash
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

On Windows Command Prompt:

```bat
.venv\Scripts\activate.bat
```

### 4. Install dependencies

```bash
python -m pip install requests pandas matplotlib tzdata
```

`requests` fetches the data, `pandas` processes it, `matplotlib` creates the chart, and `tzdata` supplies timezone data on systems that need it.

### Optional: configure PyCharm

Open the project in PyCharm and select the existing virtual environment as the project interpreter: `.venv/bin/python` on Linux/macOS or `.venv\Scripts\python.exe` on Windows. Set the run configuration's working directory to the project root.

## Run

Run commands from the repository root:

```bash
python py_weather_forecast.py
```

The script prints the calculated average temperature and a message confirming that files were saved. Open `data/weather_chart.png` to view the chart; it is saved rather than opened automatically.

This script fetches daily maximum and minimum temperatures for the seven completed days ending yesterday in Paris. It uses the `Europe/Paris` timezone, a 30-second request timeout, and error handling for network failures, HTTP errors, and invalid JSON.

The chart and CSV include a temperature midpoint calculated as `(maximum + minimum) / 2`. The script labels this value as the average, but it is not a mean calculated from temperatures throughout the day. It also prints the mean of these daily midpoints.

## Output

The main script creates the `data/` directory and writes:

- `data/weather_chart.png` — maximum, minimum, and midpoint temperature chart.
- `data/city_weather.csv` — dates and temperature values.

Running it again overwrites these files. The `data/` directory is excluded from Git.

## Other examples

- `py_weather.py` — prints current temperatures for Paris, London, and Tokyo.
- `py_weather_by_date.py` — an earlier example that prints Paris daily data and saves a chart and CSV to the same output paths. Create `data/` before running it, because it saves the chart before creating the directory.
