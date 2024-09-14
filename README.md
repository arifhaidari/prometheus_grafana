## Prometheus + Grafana

## ML Monitoring Project

This project is developed under the supervision and training course of DataScientest to learn the MLOPs and specifically the concept of monitoring by doing.

## Project Organization

    ├── LICENSE
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── logs               <- Logs from training and predicting
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   ├── check_structure.py
    │   │   ├── import_raw_data.py
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   ├── visualization  <- Scripts to create exploratory and results oriented visualizations
    │   │   └── visualize.py
    │   └── config         <- Describe the parameters used in train_model.py and predict_model.py

---

## Steps to follow to setup

Convention : All python scripts must be run from the root specifying the relative file path.

### 1- Create a virtual environment using Virtualenv.

    `python -m venv my_env`

### Activate it

    `./my_env/Scripts/activate`

### Install the packages from requirements.txt

    `pip install -r .\requirements.txt` ### You will have an error in "setup.py" but this won't interfere with the rest

### 2- Execute import_raw_data.py to import the 4 datasets.

    `python .\src\data\import_raw_data.py` ### It will ask you to create a new folder, accept it.

### 3- Execute make_dataset.py initializing `./data/raw` as input file path and `./data/preprocessed` as output file path.

    `python .\src\data\make_dataset.py`

### 4- Execute train_model.py to instanciate the model in joblib format

    `python .\src\models\train_model.py`

### 5- Finally, execute predict_model.py with respect to one of these rules :

- Provide a json file as follow :

  `python ./src/models/predict_model.py ./src/models/test_features.json`

test_features.json is an example that you can try

- If you do not specify a json file, you will be asked to enter manually each feature.

### Steps to run:

To provide a more realistic example of how you can fill in the values based on actual accident data (instead of all zeros), here’s an updated version of a sample input:

```json
{
  "place": 1, // Place of accident
  "catu": 2, // Category of user (e.g., driver, passenger)
  "sexe": 1, // Gender (1 = Male, 2 = Female)
  "secu1": 3.0, // Security equipment (e.g., seatbelt)
  "year_acc": 2023, // Year of accident
  "victim_age": 30, // Age of the victim
  "catv": 4, // Vehicle category
  "obsm": 2, // Observations made during the accident
  "motor": 1, // Type of motor used
  "catr": 3, // Road category
  "circ": 1, // Road circulation type
  "surf": 2, // Road surface type
  "situ": 1, // Accident situation
  "vma": 50, // Maximum speed on the road
  "jour": 15, // Day of the accident
  "mois": 9, // Month of the accident
  "lum": 3, // Light conditions (e.g., daytime, night)
  "dep": 75, // Department (region code)
  "com": 101, // Commune code
  "agg_": 1, // Urban or rural area
  "int_": 2, // Type of intersection
  "atm": 1, // Weather conditions
  "col": 1, // Type of collision
  "lat": 48.8566, // Latitude of the accident location
  "long": 2.3522, // Longitude of the accident location
  "hour": 14, // Hour of the accident
  "nb_victim": 1, // Number of victims
  "nb_vehicules": 2 // Number of vehicles involved
}
```

### How to Use it in Swagger UI:

1. Open the Swagger UI at `http://localhost:8000/docs`.
2. Navigate to the `/predict/` POST endpoint.
3. Use the above JSON sample as the body of the request.
4. Execute the request, and you should receive a response with the predicted severity.

This sample input is more realistic and reflects typical values you might encounter in accident prediction datasets.

---

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
