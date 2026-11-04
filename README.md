# Smart Savings

An ICT 336 workshop application built with Streamlit and two saved machine learning models.

- **Fixed deposit:** estimates the probability that a customer will open a fixed deposit after a bank call.
- **Saver group:** uses K-Means to group customers by annual income and spending score, then displays a savings tip and customer chart.
- **About the models:** displays the model information and scores included with the project.

This application is for teaching purposes and is not financial advice.

## Run locally

Use Python 3.12 and run the following commands from the project folder.

On Windows (PowerShell):

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m streamlit run app.py
```

On macOS or Linux:

```bash
python3.12 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python -m streamlit run app.py
```

Open the local URL printed by Streamlit. Run from the project folder so the application can find the model and CSV files.

## Project files

| File | Purpose |
| --- | --- |
| `app.py` | Streamlit application |
| `requirements.txt` | Validated Python dependencies, including scikit-learn 1.6.1 and PyArrow 24.0.0 |
| `savings_model.joblib` | Saved fixed-deposit prediction model and metadata |
| `saver_model.joblib` | Saved customer-group model and metadata |
| `customers_with_groups.csv` | Customer income, spending scores, and assigned groups |

The saved models are included, so no training step is needed to start the application. Training code and the original training datasets are not included.

## Streamlit Community Cloud

Deploy `SaltyLem0n/Smart_Saving`, branch `main`, with `app.py` as the entrypoint and Python **3.12** in Advanced settings.

The dependency versions are pinned to the stack verified locally on Windows with Python 3.12. The checks covered initial rendering, both prediction buttons, and a browser connection to the running server. PyArrow is pinned to 24.0.0 to match the compatibility fallback seen in the cloud deployment log.

These local checks do not establish that the cloud deployment is healthy. If the cloud page stays on its loading spinner after the server starts, inspect the current Cloud logs and hosting status before changing the models or retraining them.

Startup messages prefixed with `[Smart Savings]` show when the app script starts, finishes importing dependencies, loads its models, and loads the CSV. An unchanging loading page with no script-start message suggests the problem happens before script execution. A message followed by a traceback or no later checkpoint helps identify the startup stage to investigate.

## GitHub Pages

`index.html` runs the app entirely in the browser using Stlite 0.85.1 and Pyodide 0.27.7 (Python 3.12). Its browser dependencies are configured in `index.html`, independently of the server's `requirements.txt`.

The browser launcher pins scikit-learn to **1.6.1**, matching the saved models, together with the NumPy, SciPy, and pandas versions available in that Pyodide distribution. Upgrading the browser runtime without checking model compatibility can cause `joblib.load()` to fail with an error such as `AttributeError: ... _RemainderColsList`.

To preview locally, run `py -3.12 -m http.server 8765 --bind 127.0.0.1` from the project folder and open `http://127.0.0.1:8765/`. The first visit downloads the Python runtime and packages from CDNs, so it needs an internet connection and can take longer to load.

Browser smoke checks on 2026-11-04 loaded both models, rendered the dropdowns, and exercised both prediction buttons. Default inputs produced a fixed-deposit probability displayed as 37% and saver group 0 (Balanced middle), matching the local Python results. The saver table and customer chart also rendered. These checks used the local static preview; the deployed GitHub Pages site still needs checking after publishing the changes.

## Dataset references

The application credits these Kaggle datasets:

- Bank Marketing: `henriqueyamahata/bank-marketing`
- Mall Customer Segmentation Data: `vjchoudhary7/customer-segmentation-tutorial-in-python`
