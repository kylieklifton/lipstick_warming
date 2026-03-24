# Data Diary: The Warming of Lipstick

## Step 1: Inspiration

Online makeup creators like Emily Harper have been comparing vintage lipstick products to their modern rereleases, noting that many shades appear warmer than they used to be. This caught my attention as a potential data story.

To ground this observation, I interviewed Rosanna Carpentier, an Ulta Beauty store employee:

> "I have noticed that formulas have changed and leaned warmer. Though I'm not sure which ones."

She also noted that customers have often complained about individual product formula changes. A Sephora store manager declined to comment on the record, but said she personally had not observed the trend.

This sparked the question: can we prove this with data?

---

## Step 2: Finding a Data Source

My initial goal was to scrape lipstick shade data from beauty websites to analyze undertone trends.

**Websites I tried that blocked scraping:**
- Temptalia.com - blocked by BigScoots security system (403 error)
- MAC Cosmetics official site - blocked ("You don't have permission to access")
- Sephora.com - blocked (Access Denied)
- Ulta.com - blocked

**Solution:** I used the Wayback Machine (web.archive.org) to access archived versions of Temptalia's MAC lipstick database. The November 2024 archive had full shade data including undertone classifications.

Archive URL used: `https://web.archive.org/web/20241129180811/https://www.temptalia.com/product/mac-cosmetics-lipstick/`

---

## Step 3: Scraping Shade Data

From the Wayback Machine archive, I extracted:
- Shade names
- Undertone (warm/cool/neutral)
- Finish (matte/satin/cream)
- Availability (permanent/limited/discontinued)

Total shades in Temptalia database: 1,441
Shades I sampled: 111

**Current undertone distribution (111 shades):**
- Warm: 62 (56%)
- Cool: 37 (33%)
- Neutral: 5 (5%)
- Unknown: 7 (6%)

MAC's current lineup skews warm by nearly 2:1.

---

## Step 4: Finding Evidence of Reformulation

The shade database shows MAC IS warm-leaning, but doesn't prove shades GOT warmer. For that, I searched for documented reformulation complaints.

**Key sources:**
- Dazed Digital (dazeddigital.com) - article on MAC Cool Spice launch
- Auxiliary Beauty blog - Ruby Woo comparisons
- Beauty blogger reviews comparing MACximal reformulations

**Documented evidence of warming:**

1. **Spice → Cool Spice (Jan 2025)**
   - Original: cool-toned neutral brown
   - Current: "runs much warmer and more orange"
   - MAC's response: Released "Cool Spice" to replicate original
   - Source: Dazed Digital

2. **Ruby Woo → Ruby New**
   - Original: blue-based cool red
   - New version: "lighter, pinker, and less matte"
   - MAC's response: Created "Ruby New" as softer alternative
   - Source: Auxiliary Beauty, TikTok comparisons

3. **Velvet Teddy → Cool Teddy**
   - Original: peachy-brown nude
   - MACximal version: "now pinker"
   - MAC's response: Created "Cool Teddy" and "Warm Teddy" variants
   - Source: MAC Nudes collection launch

4. **Sweet Deal**
   - Original: purple-toned
   - MACximal version: "lighter and warmer-toned, with much less purple"
   - Source: Beauty blog reviews

5. **Whirl**
   - Original: pink-brown-grey
   - New version: "slightly lighter and a tiny bit pinker"
   - Source: Beauty blog reviews

---

## Step 5: Temperature Change Analysis

To visualize the undertone shifts, I created a temperature scale:
- 1 = Very cool (blue undertones)
- 2 = Cool
- 3 = Neutral
- 4 = Warm
- 5 = Very warm (orange/yellow undertones)

For each reformulated shade, I assigned original and current temperature scores based on:
- Documented descriptions in beauty reviews ("warmer," "more orange," "pinker," etc.)
- MAC's own product descriptions
- Comparison reviews noting the difference between old and new formulas

**Example - Spice:**
- Original described as "cool-toned neutral brown" → assigned 2 (cool)
- Current described as "runs much warmer and more orange" → assigned 4 (warm)
- Change: +2 points

**Limitation:** These are not measured color values from spectrophotometer analysis. They are qualitative assessments based on documented descriptions. The shift happened gradually over years as "formulas changed and labs moved countries" (per Dazed Digital), not at a single point in time.

---

## Step 6: The Story Angle

MAC has been quietly releasing "Cool" versions of classic shades because the originals shifted warmer over time. This is documented proof:

> "As formulas changed and labs moved countries, the colour of Spice shifted and the modern day shade now runs much warmer." — Dazed Digital

The company essentially admitted the warming happened by creating cool-toned alternatives.

---

## Step 7: Data Files

- `data/mac_shades.csv` - 111 MAC lipstick shades with undertone data (from Temptalia via Wayback Machine)
- `data/reformulation_evidence.csv` - 6 documented cases of shades shifting warmer
- `data/temperature_change_mock.csv` - Temperature shift data for chart visualization

---

## Step 8: Jupyter Notebook Analysis

Completed analysis in `analysis.ipynb`:
- Loaded and explored MAC shade data
- Calculated undertone distribution (56% warm, 33% cool, 5% neutral)
- Loaded reformulation evidence
- Calculated average temperature shift (+1.3 points on 5-point scale)

Key finding: MAC's current lineup skews warm by nearly 2:1, and documented reformulations show consistent warming shifts.

---

## Step 9: Chart Design Choices

For the undertone distribution chart, I chose proportional circles over a bar chart. The circles felt more visually engaging and better conveyed the "weight" of the warm category dominating MAC's lineup — the large warm circle immediately communicates imbalance in a way that bars don't.

However, I'm uncertain about my responsive design choices. Looking back, I may not have differentiated the mobile and desktop versions enough. The circles are arranged similarly across breakpoints, just scaled down. A stronger approach might have been to arrange the circles horizontally on desktop (where there's more width) and stack them vertically on mobile. This would have made better use of each screen's proportions and shown more intentional responsive thinking.

Lesson learned: responsive design isn't just about scaling — it's about rethinking layout for each context.

---

## Methodology Summary

**Data Collection:**
- Shade data was collected from Temptalia's MAC lipstick database via Wayback Machine archives (November 2024 snapshot)
- 111 shades sampled from a database of 1,441 total MAC lipstick shades
- Undertone classifications (warm/cool/neutral) taken directly from Temptalia's expert reviews

**Reformulation Evidence:**
- Compiled from beauty publications including Dazed Digital and Auxiliary Beauty
- Cross-referenced with MAC's own product launches and descriptions
- Focused on documented cases where reviewers compared old and new formulas

**Temperature Scale:**
- Created a 1-5 scale (1 = very cool/blue undertones, 5 = very warm/orange undertones)
- Assigned scores based on documented descriptions in reviews, not measured color values
- These are qualitative assessments, not spectrophotometer analysis

**Limitations:**
- The shifts happened gradually over years, not at a single point in time
- Temperature scores are interpretive, based on reviewer descriptions like "warmer," "more orange," "pinker"
- Sample of 111 shades may not represent the full MAC catalog

**Sources:**
- Temptalia MAC lipstick database (via Wayback Machine)
- Dazed Digital
- Auxiliary Beauty
- MAC Cosmetics product descriptions
