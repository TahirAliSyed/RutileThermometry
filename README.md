**Rutile Thermometry — Machine Learning Pipeline**
**Overview**
This repository implements the machine learning pipeline used in this study, along with instructions on how to use the developed models. 
The workflow covers model training, evaluation, and external validation. The trained model and scaler are provided as ready-to-use checkpoints.

**Repository Contents**
| File | Description |
| --- | --- |
| Code-1.ipynb | Multi-model training and evaluation |
| Code-2.ipynb | Final RFR model training |
| Code-3.ipynb | External validation and prediction template |
| Zirconium_Excluded.ipynb | Ablation study without Zr |
| RFR_Rutile_DS2.pkl | Trained RFR model checkpoint |
| Scaler_Rutile_DS2.pkl | Fitted MinMaxScaler |

**Notebooks**

**Code-1.ipynb**
Trains and benchmarks six regression models — LightGBM, GBR, XGBoost, RFR, MLP, and SVR — on Rutile-DS-1.xlsx using 25 trace elements as input features and calibrated temperature as the target.

**Code-2.ipynb**
Trains an RFR on Rutile-DS-2.xlsx using four features: Zr, Hf, Th, and U. This is the final model recommended for general use.

**Code-3.ipynb**
Applies the Code-2 RFR to an independent dataset (Rutile-DS-3.xlsx) for external validation without retraining.
Also serves as a template for applying the model to any new dataset — change the input file path and run.

**Zirconium_Excluded.ipynb**
Retrains all six models with Zr excluded to assess performance when Zr measurements are unavailable.

**Instruction for Applying the Model to New Data**
To apply the Random Forest Regressor (RFR) developed in this study, the input dataset must contain the four trace element columns Zr, Hf, Th, and U.
Scale the features using the provided scaler (Scaler_Rutile_DS2.pkl) and run prediction using the provided model (RFR_Rutile_DS2.pkl).The provided scaler must always be used as-is.
A working example is in Code-3.ipynb and can be adapted by changing the input file path.
For cases where Zr measurements are unavailable, refer to Zirconium_Excluded.ipynb. 

**Dependencies**
pip install pandas numpy scikit-learn lightgbm xgboost matplotlib seaborn shap joblib openpyxl
