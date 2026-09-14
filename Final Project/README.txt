Final Course Project — Survival Prediction and Model Comparison
Oded Katz (211862693), Diana Morgan (336472261)

CONTENTS
  final_proj.ipynb              all analyses, in the order of the assignment items
  trained_models/               fitted models cached by joblib (see RUNNING)
  figures/                      figures produced by the notebook
  tables/                       tables produced by the notebook, as CSV
  requirements_SAML_fin.txt     full pip freeze of the environment used

DATA
  The notebook expects the imputed dataset from Project Assignment 1 as
  imputed_data.csv. It is not included here. The path is set at the top of
  the notebook, in the Section 0 setup cell:

      DATA_PATH = os.path.join("..", "PA1", "imputed_data.csv")

  so by default the file is read from a sibling PA1/ directory next to this
  one. To read it from anywhere else, edit that line; there is no environment
  variable for it.

RUNNING
  jupyter lab final_proj.ipynb, then Run All.

  Cells 5.1, 7.2, 7.3, 7.4 and 10.3 load fitted models from trained_models/
  if the files are present and fit them otherwise:

      cox_train.joblib                         Section 5.1
      rsf.joblib                               Section 7.2
      deepsurv.joblib                          Section 7.3
      coxtime.joblib                           Section 7.4
      cox_int_bun.joblib, cox_int_age.joblib   Section 10.3

  All six must be present for the notebook to reproduce the numbers in the
  report. The two networks are the ones that matter here: deleting
  deepsurv.joblib or coxtime.joblib triggers a fresh hyperparameter search,
  and the result does not reproduce exactly across environments, so the
  DeepSurv and Cox-Time numbers will drift away from the reported ones.

  Seeding alone cannot prevent this. torch.manual_seed and np.random.seed fix
  the random numbers the networks draw, but not the order in which parallel
  kernels accumulate floating-point sums, and floating-point addition is not
  associative. On the GPU that order depends on cuBLAS and cuDNN algorithm
  selection; on the CPU it follows the thread count. The notebook pins neither
  torch.use_deterministic_algorithms nor torch.backends.cudnn.deterministic,
  so two runs on different hardware already differ in the last few digits.

  The Cox models and the forest are unaffected, which is why they reproduce
  exactly: lifelines optimises deterministically, and scikit-survival derives
  a seed per tree from random_state, so n_jobs does not change the fit.

  To re-run the searches from scratch anyway, delete trained_models/ first.
  The full search refits 180 models — 12 configurations x 5 folds for each of
  the forest, DeepSurv and Cox-Time — plus the final refits, so it takes
  considerably longer than a cached run.

  Random seed 42 is set once at the top of the notebook and governs the
  train-test split, the cross-validation folds, the forest, and network
  initialisation and batching.

PACKAGES  (Python 3.11.16, conda environment "SAML_fin")
  numpy 2.0.2              pandas 2.3.3
  scipy 1.17.1             matplotlib 3.11.1
  scikit-learn 1.9.0       statsmodels 0.15.0
  lifelines 0.30.3         scikit-survival 0.28.0
  pycox 0.3.0              torchtuples 0.2.2        torch 2.5.1+cu121
  joblib 1.6.0


  requirements_SAML_fin.txt is a full pip freeze of that environment:

      pip install -r requirements_SAML_fin.txt


HARDWARE
  torchtuples selects the GPU whenever torch.cuda.is_available(), and the
  notebook never overrides it, so DeepSurv and Cox-Time were trained on a
  CUDA device. The Cox models and the forest are CPU-only. On a machine with
  no GPU the notebook still runs, but the two networks train on the CPU
  instead, which is a different computation — one more reason to keep the
  cached models rather than refit.

FIGURE MAPPING
  Report figure -> file in latex/figs/ -> source file in figures/

  Figure 1   fig1.png     fig1_km_overall.png
  Figure 2   fig2.png     fig3_km_age_bun.png
  Figure 3   fig3.png     fig4_cox_vs_aft.png
  Figure 4   fig4.png     fig6_cox_one_year.png
  Figure 5   fig5.png     fig7a_age.png + fig7b_rdw.png + fig7c_bun_discharge.png
  Figure 6   fig6.png     fig8_calibration.png
  Figure 7   fig7.png     fig9_risk_tertiles.png
  Figure 8   fig8.png     fig10_interactions.png
  Figure A1  figA1.png    fig5_schoenfeld_train.png
  Figure A2  figA2.png    fig2_km_stratified.png
