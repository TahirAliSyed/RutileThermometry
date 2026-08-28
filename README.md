**Rutile Thermometry — Machine Learning Pipeline**
**Overview:**
This repository implements the machine learning pipeline used in this study, along with instructions on how to use the developed models. 
The workflow covers model training, evaluation, and external validation. The trained model and scaler are provided as ready-to-use checkpoints.

**Repository Contents**
| File | Description |
| --- | --- |
| Code-1.ipynb | Multi-model training and evaluation using Rutile-DS-1 |
| Code-2.ipynb | RFR model trained on Rutile-DS-2 |
| Code-3.ipynb | External validation using Rutile-DS-3 |
| Zirconium-Excluded (24-elements) RFR.ipynb | Ablation study without Zr |
| Zirconium-Excluded (3-elements) RFR.ipynb | RFR model trained using Hf, U, Th |
| Random Forest Checkpoints | Trained RFR model checkpoints with different feature configurations |

**Notebooks**

**Code-1.ipynb:**
Trains and benchmarks six regression models — LightGBM, GBR, XGBoost, RFR, MLP, and SVR — on Rutile-DS-1.xlsx using 25 trace elements as input features and calibrated temperatures as the target.

**Code-2.ipynb:**
Trains an RFR model on Rutile-DS-2.xlsx using four features: Zr, Hf, Th, and U. **This is the final model that can be used for routine rutile thermometry.**

**Code-3.ipynb:**
Applies the pretrained RFR model to an independent dataset (Rutile-DS-3) for external validation without retraining.
Also serves as a template for applying the model to any new dataset — change the input file path and run.

**Zirconium-Excluded (24-elements) RFR.ipynb:**
Retrains RFR with Zr excluded from feature set to assess application potential when Zr measurements are unavailable. **This model is recommended for use where rutile lacks Zr or Zr concentration is below detection limit. This model yields temperature estimates with uncertainity of ~±30°C relative to full suite Zr-in-rutile thermometer.**

**Zirconium-Excluded (3-elements) RFR.ipynb:**
Trains an RFR model on 3 features including Hf, Th, and U. **This model can also be used in Zr-undersaturated systems and can yield temperature estimates with uncertainity of ~±38°C.**

**Instruction for applying the model to new data:**
To apply the pretrained RFR model to new rutile trace‑element data, use the provided model and scaler checkpoints.
A working example is in Code-3 and can be adapted by changing the input.
For cases where Zr measurements are unavailable, or analystically compromised, Zr-excluded RFR model checkpoints can be used following same route.

**Dependencies:**
pandas, numpy, scikit-learn, lightgbm, xgboost, matplotlib, seaborn, shap, joblib, openpyxl
