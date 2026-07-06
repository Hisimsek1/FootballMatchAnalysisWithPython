# 2018 FIFA World Cup Final — France vs Croatia

Event-level match analysis of the 2018 FIFA World Cup Final using StatsBomb open data.

## Data Source

All data is fetched at runtime from the [StatsBomb Open Data](https://github.com/statsbomb/open-data) repository via the `statsbombpy` Python library. No local data files are required.

- Competition: FIFA World Cup 2018
- Match: France 4–2 Croatia
- Match ID resolved dynamically via `sb.matches(competition_id=43, season_id=3)`

## Requirements

```
pip install statsbombpy mplsoccer matplotlib numpy pandas scipy
```

Python 3.8 or higher is required.

## Notebook

Open and run `Match_Analysis.ipynb` sequentially from top to bottom. An active internet connection is required on first run to fetch data from StatsBomb. All visualizations are saved automatically to `figures/`.

## Visualizations

### Player Touch Heatmap — Pogba

Gaussian KDE over all event locations for Paul Pogba.

![Pogba Heatmap](figures/gorsel_01_oyuncu_isi_pogba.png)

---

### Player Touch Heatmap — Modrić

Gaussian KDE over all event locations for Luka Modrić.

![Modrić Heatmap](figures/gorsel_02_oyuncu_isi_modric.png)

---

### Team Pass Density Heatmap — France

Gaussian KDE on pass origin coordinates for France.

![France Pass Heatmap](figures/gorsel_03_pas_isi_fransa.png)

---

### Team Pass Density Heatmap — Croatia

Gaussian KDE on pass origin coordinates for Croatia.

![Croatia Pass Heatmap](figures/gorsel_04_pas_isi_hirvatistan.png)

---

### Shot Map — France

Scatter on half-pitch. Stars mark goals, circles mark non-goals.

![France Shot Map](figures/gorsel_05_sut_fransa.png)

---

### Shot Map — Croatia

Scatter on half-pitch. Stars mark goals, circles mark non-goals.

![Croatia Shot Map](figures/gorsel_06_sut_hirvatistan.png)

---

### Pass Network — France

Average player positions connected by edges weighted by pass-pair frequency.

![France Pass Network](figures/gorsel_07_pas_agi_fransa.png)

---

### Pass Network — Croatia

Average player positions connected by edges weighted by pass-pair frequency.

![Croatia Pass Network](figures/gorsel_08_pas_agi_hirvatistan.png)

---

### xG Timeline

Cumulative StatsBomb xG step chart with goal markers and half-time line.

![xG Timeline](figures/gorsel_09_xg.png)

---

### Match Momentum

3-minute rolling action count (line) and per-minute momentum differential (bar).

![Match Momentum](figures/gorsel_16_momentum.png)

---

### Counter-Press Heatmap

Gaussian KDE on pressure events occurring within 5 seconds of an opponent ball loss.

![Counter-Press France](figures/gorsel_22_counter_press_fransa.png)

---

### Goal Buildup Map

Last 8 events before each goal shown as an arrow chain, one subplot per goal.

![Goal Buildup](figures/gorsel_24_gol_yapilanma.png)

---

## Full Visualization List

| # | Plot | Method |
|---|------|--------|
| 1 | Player Touch Heatmap — Pogba | Gaussian KDE over all event locations |
| 2 | Player Touch Heatmap — Modrić | Gaussian KDE over all event locations |
| 3 | Team Pass Density Heatmap — France | Gaussian KDE on pass origin coordinates |
| 4 | Team Pass Density Heatmap — Croatia | Gaussian KDE on pass origin coordinates |
| 5 | Shot Map — France | Scatter on half-pitch, goals starred |
| 6 | Shot Map — Croatia | Scatter on half-pitch, goals starred |
| 7 | Pass Network — France | Average player positions + pass-pair frequency edges |
| 8 | Pass Network — Croatia | Average player positions + pass-pair frequency edges |
| 9 | xG Timeline | Cumulative StatsBomb xG step chart with goal markers |
| 10 | Defensive Action Map — France | Scatter by event type (Pressure, Block, Interception, Ball Recovery) |
| 11 | Defensive Action Map — Croatia | Scatter by event type |
| 12 | Progressive Pass Map — France | Arrows for passes gaining ≥10m toward goal |
| 13 | Progressive Pass Map — Croatia | Arrows for passes gaining ≥10m toward goal |
| 14 | Player Radar — Pogba vs Modrić | 7-metric polar comparison |
| 15 | Player Radar — Mbappé vs Perišić | 7-metric polar comparison |
| 16 | Match Momentum | 3-minute rolling action count, dual subplot |
| 17 | Zone Control Map | 6-zone pitch split, action-count ratio by dominant team |
| 18 | Dribble Map — France | Successful vs failed dribbles, success rate labelled |
| 19 | Dribble Map — Croatia | Successful vs failed dribbles, success rate labelled |
| 20 | Pass Direction Rose — France | Polar histogram (24 bins) of pass angles |
| 21 | Pass Direction Rose — Croatia | Polar histogram (24 bins) of pass angles |
| 22 | Counter-Press Heatmap — France | Gaussian KDE on pressures within 5s of opponent ball loss |
| 23 | Counter-Press Heatmap — Croatia | Gaussian KDE on pressures within 5s of opponent ball loss |
| 24 | Goal Buildup Map | Last 8 events before each goal, arrow-chain per subplot |

## Coordinate System

StatsBomb events use a 120 × 80 unit pitch:
- x: 0 (own goal line) to 120 (opponent goal line)
- y: 0 (left touchline) to 80 (right touchline)

`mplsoccer` is used for all pitch drawings with `pitch_type='statsbomb'`.

## Project Structure

```
France-Croatia2018/
├── Match_Analysis.ipynb
├── README.md
├── LICENSE
└── figures/                 # output PNGs (24 files)
    ├── gorsel_01_oyuncu_isi_pogba.png
    ├── gorsel_02_oyuncu_isi_modric.png
    └── ...
```

## License

MIT License
