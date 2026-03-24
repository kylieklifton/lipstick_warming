# The Warming of Lipstick

An analysis of how MAC lipstick shades have shifted toward warmer undertones over time.

## Live Site
https://kylieklifton.github.io/lipstick_warming/

## Data Sources

### Reformulation Evidence (`data/reformulation_evidence.csv`)
Six MAC shades with documented undertone shifts, selected because:
- They are **classic/iconic shades** that have been in production for years
- They have **documented complaints** from beauty reviewers noting color changes
- MAC has **released "Cool" alternatives**, implicitly acknowledging the shift

These are not random selections. They represent cases where reformulation is publicly documented by beauty publications (Dazed Digital, Auxiliary Beauty) and confirmed by MAC's own product launches (Cool Spice, Ruby New, Cool Teddy).

### Shade Database (`data/mac_shades.csv`)
111 MAC lipstick shades scraped from Temptalia via Wayback Machine (November 2024 archive). This sample includes:
- Permanent shades
- Limited edition shades
- Discontinued shades

The sample represents the breadth of MAC's undertone distribution across their catalog, showing the brand currently skews 56% warm vs 33% cool.

### Temperature Scale (`data/temperature_change_mock.csv`)
Undertone shifts quantified on a 1-5 scale:
- 1 = Very cool (blue undertones)
- 2 = Cool
- 3 = Neutral
- 4 = Warm
- 5 = Very warm (orange/yellow undertones)

Values assigned based on documented descriptions in beauty reviews and MAC's own product descriptions.

## Methodology

Data collection documented in `data-diary.md`.

## Tools Used
- Python/Pandas for analysis
- Datawrapper for charts
- Wayback Machine for accessing archived Temptalia data
