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

## Dataset references

The application credits these Kaggle datasets:

- Bank Marketing: `henriqueyamahata/bank-marketing`
- Mall Customer Segmentation Data: `vjchoudhary7/customer-segmentation-tutorial-in-python`
