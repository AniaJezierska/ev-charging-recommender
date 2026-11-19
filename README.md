# EV Charging Recommender — Engineering Thesis

Polish-Japanese Academy of Information Technology, Warsaw · 2025

For my engineering thesis, I developed a machine learning system to help EV drivers decide where and when to charge. My work covered two tasks: forecasting electricity prices and ranking charging stations. I evaluated the approach using data from Warsaw, Amsterdam, and London.

## How the recommendation works

1. **Forecast electricity prices.** A Random Forest model predicts hourly electricity prices for each city over the next 24 hours.
2. **Rank charging stations.** For a given city and hour, CatBoostRanker ranks stations using features such as the number of charging points, free-flow traffic speed, and location within the city.
3. **Recommend a station and time.** The system combines the forecast electricity price with estimated travel time and queue risk to suggest where and when to charge.

## Results

| Task | Evaluation | Result |
| --- | --- | --- |
| Hourly electricity price forecasting | Mean absolute error on the validation set | Approximately 12 EUR/MWh |
| Charging station ranking | Mean NDCG@10 across leave-one-city-out evaluations for Amsterdam, London, and Warsaw | 0.923 |

## Data limitation

Live charger occupancy was unavailable. I used station characteristics, including the number of charging points and the city zone, to estimate queue risk. The ranking results therefore describe how well the model reproduced the project's scoring criteria. Actual waiting times at the stations would be needed to validate the queue estimates.