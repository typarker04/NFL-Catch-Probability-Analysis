# NFL Catch Probability Predictor

Predicting catch success using machine learning on Next Gen Stats tracking data from the 2023 season.

<img width="686" height="455" alt="Screenshot 2025-12-05 at 10 38 04 AM" src="https://github.com/user-attachments/assets/33ba9a30-4d3c-4aab-b77c-c06d4493738a" />



## Project Overview

Built a Random Forest model to predict catch probability based on player positioning, achieving 64% accuracy. The system identifies critical moments where positioning changes shifted catch probability by 10%+.

## Key Features

-   Engineered 7+ spatial features from player tracking data (separation, positioning advantage, coverage density)
-   Processed 1,800+ plays across 11 weeks of NFL data
-   Frame-by-frame visualization showing probability evolution during ball flight
-   Critical moment detection identifying when receiver/defender actions changed the outcome

## Results

-   **Model Accuracy:** 64% (OOB Error: 36%)
-   **Key Predictors:** Separation at arrival (30.8), Separation at throw (18.4)
-   **Insights:** Defender positioning matters more when separation is tight

## Tech Stack

-   **R:** dplyr, ggplot2, randomForest, tidyr
-   **Data:** NFL Next Gen Stats tracking data
-   **Methods:** Feature engineering, Random Forest classification, time-series analysis

## Project Structure

```         
├── data/               # Raw and processed data
├── p3-final.Rmd        # Main analysis notebook
├── index.html          # Published report
├── NFL_prob.pdf        # Presentation
└── README.md
```

## Quick Start

``` r
# Load model
model <- readRDS("/data/rf_model.rds")

# Analyze a play
play <- get_play(week = 1, play_number = 5)
result <- evaluate_single_play(play$input, play$output, model)
print(result$plot)
```


## Key Insights

1.  Separation at ball arrival is the strongest predictor (MeanDecreaseAccuracy: 30.8)
2.  Positioning advantage (who's closer to landing spot) improves predictions by 5%
3.  Critical moments occur when separation changes by 2+ yards in a single frame

## Future Work

-   Add defender orientation features to capture coverage quality
-   Implement frame-level temporal model for true dynamic predictions
-   Expand to other seasons
