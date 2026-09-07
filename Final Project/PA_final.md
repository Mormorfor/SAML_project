# **Final Course Project: Survival Prediction and Model Comparison** 

Spring 2026 DDS, Technion 

### **Due: September 14, 2026 at 23:59 (submit in pairs via Moodle)** 

The final project consists of (i) a written report, (ii) Python source code, and (iii) a 15-minute Zoom presentation followed by 5 minutes of questions. 

This final project continues the analyses conducted in Project Assignments 1 and 2. You should use the same synthetic dataset assigned to you in the previous project assignments. Unless otherwise specified, all analyses should be performed using the dataset after imputing missing values (as in Project Assignment 1) and replacing the individual comorbidity indicators by the comorbidity burden variable (as in Project Assignment 2). 

The goal of the final project is to revisit your original research questions, summarize the main findings from the earlier assignments, and compare several survival prediction methods using a train–test evaluation framework. 

Your final report should be written as a coherent scientific report rather than as a list of separate answers. The report should include enough detail to explain what was done, why it was done, and what conclusions can be drawn from the analyses. 

## **Oral presentation** 

Each pair will present its project in a 15-minute Zoom presentation, followed by 5 minutes for questions and discussion. The presentation should summarize the research questions, the main methods, the principal findings, and the overall conclusions. Additional details regarding the presentation schedule will be announced separately. 

## **Instructions** 

1. **Brief recap of Project Assignment 1** 

   - Briefly summarize the exploratory survival analysis conducted in Project Assignment 1. Your summary should include: 

      -  a short description of the dataset and survival outcome; 

      -  the sample size, number of events, and number of censored observations; 

      -  a concise table or summary of the main covariates; 

      -  the overall Kaplan–Meier survival curve; 

      -  one or two meaningful stratified Kaplan–Meier curves; 

      -  the research question or questions that motivated your analysis. 

Do not reproduce the full analysis from Project Assignment 1. Include only the information needed to motivate the final project. 

1 

### 2. **Brief recap of Project Assignment 2** 

Briefly summarize the main findings from Project Assignment 2. 

Your summary should include: 

-  the final Cox model selected in Project Assignment 2; 

-  the main covariates associated with post-discharge survival; 

-  whether changes in BUN during hospitalization appeared to add prognostic information; 

-  the main conclusions from the proportional hazards diagnostics; 

-  the comparison between the Cox model and the log-normal AFT model for oneyear survival prediction. 

Again, do not reproduce the full analysis from Project Assignment 2. Focus on the findings that are relevant for the new analyses in this final project. 

### 3. **Research questions** 

Restate the research question or questions from Project Assignment 1. 

You may update, refine, or add new research questions based on what you have learned throughout the course. 

Clearly state the final research questions that will guide the analyses in this project. 

If your research questions require the individual comorbidity indicators rather than the comorbidity burden variable, you may use the original comorbidity variables in the relevant analyses below. Clearly justify this choice. 

### 4. **Train–test split** 

Split the data into a training set and a test set using an 80/20 split. Use a fixed random seed and report the seed used. 

The training set should be used for model fitting. The test set should be used only for final model evaluation. 

Students who wish to tune hyperparameters may instead use a 60/20/20 split, corresponding to training, validation, and test sets. The validation set may be used for hyperparameter tuning and model selection. The test set should still be used only once, for the final comparison of the fitted models. 

The same training, validation (if used), and test sets should be used for all subsequent analyses and for all fitted models. 

### 5. **Refitting the selected Cox model** 

Refit the final Cox model selected in Project Assignment 2 using only the training data. 

Report the estimated hazard ratios, 95% confidence intervals, and p-values. 

2 

Compare the results with those obtained in Project Assignment 2 using the full dataset. Discuss whether the estimated effects and conclusions changed meaningfully after fitting the model on the training data only. 

Assess the proportional hazards assumption for the refitted Cox model using the training data. 

Perform a formal test based on Schoenfeld residuals and produce Schoenfeld residual plots for all covariates. Compare the estimated hazard ratios, confidence intervals, statistical significance, and proportional hazards diagnostics with those obtained in Project Assignment 2. Discuss whether fitting the model on the training data changes your conclusions regarding the proportional hazards assumption. 

### 6. **One-year survival prediction using the refitted Cox model** 

Using the Cox model fitted on the training data, estimate the one-year survival probability 



Produce prediction plots for age, RDW, and discharge BUN. 

For each covariate separately, plot the estimated one-year survival probability as a function of that covariate while holding all remaining covariates fixed at representative values. 

For continuous covariates, use the median value in the training data. For binary and categorical covariates, use the most common category in the training data. 

Briefly interpret the resulting prediction plots. 

7. **Fitting additional survival prediction models** 

Fit the following additional models using the training data: 

-  Random Survival Forests; 

-  DeepSurv; 

-  Cox-Time. 

Use the same set of covariates used in the refitted Cox model, unless your research question motivates a clearly explained alternative. Save the fitted models for use in the subsequent prediction and model comparison analyses. 

For each model, briefly describe how the model estimates individual survival, and report the main tuning choices or hyperparameters used. If you tune hyperparameters, describe the validation procedure. If you do not tune hyperparameters, clearly state the values used and justify them briefly. 

3 

8. **Comparison of one-year survival prediction curves** 

For each fitted model, compute the predicted one-year survival probability 



For age, RDW, and discharge BUN, compare the predicted one-year survival probabilities across the Cox model, Random Survival Forest, DeepSurv, and Cox-Time. 

Produce three figures, one for each covariate (age, RDW, and discharge BUN). Each figure should display the prediction curves from all four models on the same axes using identical covariate grids and the same representative values (defined in 6) for the remaining covariates. 

Discuss similarities and differences among the models. In particular, comment on whether the models suggest similar or different relationships between one-year survival and the three covariates. 

### 9. **Test-set model comparison** 

Use the test set to compare the predictive performance of the fitted models. 

For each individual in the test set and for each fitted model, compute the predicted one-year survival probability 



and define the corresponding predicted one-year risk 



Compare the fitted models using the following performance measures: 

###  **Discrimination.** 

Compute Uno’s time-dependent C-index with evaluation horizon _τ_ = 1 year using � the predicted one-year risks _ri_ . 

###  **Calibration.** 

Divide the test subjects into ten approximately equal-sized groups (deciles) according to their predicted one-year survival probabilities. Within each group, estimate the observed one-year survival probability using the Kaplan–Meier estimator. Produce a calibration plot comparing the mean predicted and observed one-year survival probabilities. 

Briefly comment on the calibration of each model. 

###  **Prediction accuracy.** 

Compute the integrated Brier score (IBS) over the first year of follow-up. Since time is measured in months, define 

4 



where BS(<sup>�</sup> _t_ ) denotes the IPCW Brier score at month _t_ . Approximate the integral using the trapezoidal rule applied to the IPCW Brier scores evaluated at the monthly time points 



Summarize the results for all models in a single table and discuss the relative strengths and weaknesses of the different prediction methods. 

### 10. **Additional analyses based on your research questions** 

Perform additional analyses motivated by your final research questions. 

Examples include, but are not limited to: 

-  subgroup analyses; 

-  interaction effects; 

-  additional prediction plots; 

-  comparison of high-risk and low-risk patients; 

-  assessing whether different models lead to different scientific conclusions; 

-  evaluating model performance in clinically meaningful subgroups. 

Clearly explain why the additional analyses are relevant to your research questions and interpret the results. 

If your research questions require predictors that were not included in the standard analysis (for example, the individual comorbidity indicators instead of the comorbidity burden variable), you may perform additional analyses using those variables. Clearly justify any departures from the standard modeling strategy and discuss how they affect your conclusions. 

### 11. **Final discussion** 

Summarize the main findings from the final project. 

Your discussion should address: 

-  which covariates appear most strongly associated with post-discharge survival; 

-  whether the conclusions from the Cox model were stable after fitting the model on the training data only; 

-  whether the more flexible models suggested important nonlinear effects or different prediction patterns; 

5 

-  which model performed best on the test set according to discrimination, calibration, and prediction error; 

-  whether the different models led to similar or different answers to your research questions; 

-  the main limitations of your analysis. 

6 

