# 📍 Location Map Visualizer

An interactive map visualizer for GPS location data. Generates an HTML map with animated trails, heatmaps, and clickable timestamps from a CSV file.

## 🗂️ Input Format

A `.csv` file with **no header**, one location per row:

```
46.8446159, -96.813092, 2020-01-24 14:32:44
46.8636490, -96.802439, 2020-02-11 09:19:57
...
```

| Column | Type | Description |
|--------|------|-------------|
| `lat` | float | Latitude |
| `lon` | float | Longitude |
| `timestamp` | datetime | `YYYY-MM-DD HH:MM:SS` |

> Supported encodings: UTF-8, **UTF-16** (auto-detected), Latin-1, CP1252.

## 📦 Requirements

```bash
pip install pandas folium
```

## 🚀 Usage

```bash
python3 mapexploit.py
```

By default the script reads `points.csv` from the current directory and outputs `carte_deplacements.html`.

To change the input file, edit line 6 in `mapexploit.py`:

```python
df = pd.read_csv("your_file.csv", ...)
```

## 🗺️ Output

An interactive HTML file (`carte_deplacements.html`) that you can open in any browser.

| Feature | Description |
|---------|-------------|
| 🟣 Animated trail | Animated path following chronological order |
| 🔥 Heatmap | Highlights frequently visited areas |
| 🟢 Start marker | First recorded location |
| 🔴 End marker | Last recorded location |
| 🔵 Clickable points | Each point shows its exact timestamp on click |

### Preview

```
[Heatmap + animated trail across 250 GPS points — Jan to Mar 2020]
[Fargo, North Dakota area]
```

## 📁 Project Structure

```
.
├── mapexploit.py           # Main script
├── points.csv              # Input data
└── carte_deplacements.html # Generated map (output)
```

## 🧠 How It Works

1. Loads and parses the CSV (handles multiple encodings)
2. Sorts all points chronologically
3. Renders an interactive map using [Folium](https://python-visualization.github.io/folium/) with:
   - `AntPath` for the animated trail
   - `HeatMap` plugin for density visualization
   - `CircleMarker` for individual points

## 📝 License

MIT
