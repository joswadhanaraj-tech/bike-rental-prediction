# Bike Rental Demand Analysis

This project explores the Washington, D.C. bike-sharing dataset and uses regression models to predict daily bike rental counts from seasonal, calendar, and weather information.

## Project contents

| File | Description |
| --- | --- |
| `PRCP-1018-BikeRental-Project.ipynb` | Jupyter notebook with data exploration, visualizations, model training, and evaluation |
| `day.csv` | Daily bike rental records (731 days) |
| `hour.csv` | Hourly bike rental records (17,379 hours) |
| `model_comparison.csv` | Model evaluation results saved by the notebook |
| `Readme.txt` | Original dataset documentation and field descriptions |

The notebook currently analyzes `day.csv`. It examines rental patterns across seasons, years, months, weather, working days, and normalized weather measurements. It then compares four regression models using a held-out test set.

## Requirements

- Python 3
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn

Install the Python dependencies with:

```bash
python -m pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

## Run the analysis

Open a terminal in the project directory and launch Jupyter:

```bash
jupyter notebook
```

Open `PRCP-1018-BikeRental-Project.ipynb` and run the cells in order. Keep `day.csv` in the project directory so the notebook can load it. The final cells display the model comparison and save the results to `model_comparison.csv`.

## Features and target

The target is `cnt`, the total number of daily rentals. The notebook uses these input features:

`season`, `yr`, `mnth`, `holiday`, `weekday`, `workingday`, `weathersit`, `temp`, `atemp`, `hum`, and `windspeed`.

The `casual` and `registered` columns are intentionally excluded because they are components of `cnt` and would leak information about the target.

## Current model results

The checked-in `model_comparison.csv` contains the following results. Your results may vary if the data or notebook changes.

| Model | MAE | RMSE | R² |
| --- | ---: | ---: | ---: |
| Linear Regression | 617.39 | 831.29 | 0.8277 |
| Decision Tree | 662.80 | 983.98 | 0.7585 |
| Random Forest | 429.96 | 677.09 | 0.8857 |
| Gradient Boosting | 462.77 | 661.38 | 0.8909 |

The notebook identifies the model with the lowest RMSE as the best model; in the checked-in results, that is Gradient Boosting.

## Dataset citation

The dataset contains Washington, D.C. Capital Bikeshare records from 2011 and 2012, aggregated by hour and day and supplemented with weather and seasonal information. For use in publications, cite:

> Fanaee-T, Hadi, and João Gama. “Event labeling combining ensemble detectors and background knowledge.” *Progress in Artificial Intelligence* (2013), pp. 1–15. https://doi.org/10.1007/s13748-013-0040-3
