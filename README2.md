# Too Hot, Too Cold

An interactive world map that shows how livable 70 places become as the planet warms. Drag the warming dial and every place is rated month by month, from **Brutal cold** through **Comfortable** to **Pretty hard to live** and **Dangerous heat**, so you can see how many months a year each place spends too hot or too cold.

## Features

- **Warming dial** with two modes:
  - **Realistic** (0 to +5 °C global): cold places warm faster than the tropics, using rough regional factors.
  - **Same everywhere** (0 to +7 °C): the same warming added to every place.
- **Presets** for the 1991–2020 climate, today, the Paris 1.5 °C goal, 2100 on current policies, and 2100 with very high emissions.
- **Color by** worst month, typical month, heat only or cold only (blue = cold, red = heat).
- **A 12-month strip for every place**, with a count of months in each category and of "hard months".
- **Sweet-spot rings** for places whose warmest month still averages 25 °C or less.
- **Place details:** before/after temperatures, heat index, wet-bulb temperature, "hottest month like today's ___" comparisons, and local risks such as permafrost, sea level or fire.
- A table of every place, sorted from worst heat to worst cold, plus light and dark mode.

## Run it

It's a single static file. Open `index.html` in a browser, or host it with GitHub Pages:

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, pick **Deploy from a branch**, choose `main` and `/ (root)`, and save.
4. The site appears at `https://<your-username>.github.io/<repo-name>/` after a minute or two.

## How it works

- **Starting climates** are monthly average highs, lows and humidity from each city's climate table on Wikipedia, mostly 1991–2020 normals. Afternoon humidity uses the 3 pm figure where published, otherwise 80% of the monthly mean; a few humidity series are estimates.
- **Realistic mode** multiplies global warming by a simplified regional factor, blended month by month between a winter and a summer factor (Arctic winters about 3–4.5×, large continents about 1.3–1.8×, tropical coasts about 0.8×). These are simplifications of climate-model patterns, not real per-city projections. The 1991–2020 climate is about 0.9 °C above pre-industrial.
- **Each month's heat rating** uses the NOAA heat index on an average afternoon, assuming humidity stays about the same: under 27 °C comfortable, 27–32 warm, 32–41 hot, 41–48 pretty hard to live, 48+ dangerous. Average nights of 29 °C+ count as pretty hard, and a wet-bulb of 31 °C+ (Stull 2011 approximation) counts as dangerous.
- **Each month's cold rating** uses that month's average low: above 0 °C comfortable, to −8 chilly, to −18 cold, to −30 harsh, below that brutal.
- Labels are based on averages, so real heatwaves and cold snaps are worse.

## Credits

- Map shapes: [world-atlas](https://github.com/topojson/world-atlas) (Natural Earth data, public domain), embedded in the page.
- Libraries loaded from jsDelivr: [D3](https://d3js.org) and [topojson-client](https://github.com/topojson/topojson-client), both ISC licensed.
- Climate normals: the climate tables on each city's Wikipedia page, which cite national weather services (NOAA, Met Office, Roshydromet, CMA, JMA, BoM and others).
