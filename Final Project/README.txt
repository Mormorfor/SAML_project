Final Course Project — Survival Prediction and Model Comparison
Oded Katz (211862693), Diana Morgan (336472261)

CONTENTS
  final_proj.ipynb    all analyses, in the order of the assignment items
  trained_models/     fitted models cached by joblib (see RUNNING)
  figures/            figures produced by the notebook
  tables/             tables produced by the notebook, as CSV

DATA
  The notebook expects the imputed dataset from Project Assignment 1 as
  imputed_data.csv, placed next to the notebook. It is not included here.
  To read it from elsewhere, set the environment variable DDS_DATA_PATH
  to its full path before starting Jupyter.

RUNNING
  jupyter lab final_proj.ipynb, then Run All.

  Cells 5.1, 7.2, 7.3, 7.4 and 10.3 load fitted models from trained_models/
  if the files are present and fit them otherwise. With the directory as
  shipped the notebook reproduces the reported numbers in a few minutes.
  To re-run the hyperparameter searches from scratch, delete trained_models/
  first; the full run takes roughly <N> minutes on a CPU.

  Random seed 42 is set once at the top of the notebook and governs the
  train-test split, the cross-validation folds, the forest, and network
  initialisation and batching.

PACKAGES  (Python 3.11)
  numpy <ver>            pandas <ver>
  scipy <ver>            matplotlib <ver>
  scikit-learn <ver>     statsmodels <ver>
  lifelines <ver>        scikit-survival <ver>
  pycox <ver>            torchtuples <ver>        torch <ver>
  joblib <ver>

FIGURE MAPPING (report -> file in figures/)
  Figure 1  fig1_km_overall.png
  Figure 2  fig3_km_age_bun.png
  Figure 3  fig4_cox_vs_aft.png
  Figure 4  fig6_cox_one_year.png
  Figure 5  fig7_model_curves.png
  Figure 6  fig8_calibration.png
  Figure 7  fig9_risk_tertiles.png
  Figure 8  fig10_interactions.png
  Figure A1 fig5_schoenfeld_train.png
  Figure A2 fig2_km_stratified.png