# **Final Project Submission Guidelines** 

### **Submission format:** 

Submit the following two files via Moodle: 

-  A single PDF report. 

-  A ZIP archive containing all Python source code used in the project. 

### **Oral presentation** 

In addition to the written report and source code, each pair will give a 15-minute Zoom presentation, followed by 5 minutes for questions. Additional details regarding the presentation schedule will be announced separately. 

The presentation should provide a concise overview of the motivation, methods, key results, and conclusions of the project. The presentation is part of the project assessment. 

## **General focus** 

The final report should be written in the style of a short scientific paper. The purpose of the report is not only to document the analyses performed, but to use those analyses to answer your research questions. Organize the report so that the reader can understand the motivation, methods, results, and conclusions of your project. 

**Focus on answering your research questions.** The purpose of the report is not to present every analysis in chronological order, but to use the analyses to answer the research questions you formulated. Organize the Results and Discussion sections around the scientific questions whenever appropriate. 

## **Document format** 

-  Submit one PDF report and one ZIP archive containing the Python source code. 

-  The main text of the report should be no longer than 10 pages. 

-  The page limit excludes plots, tables, references, and appendices, which may appear after the main text. 

-  Use standard formatting: 

   - Font: Times New Roman or similar, 11–12 pt. 

   - Line spacing: 1.0–1.5. 

   - Margins: approximately 1 inch (2.5 cm) on all sides. 

1 

## **Code submission** 

The ZIP archive should contain all Python code required to reproduce the analyses presented in the report. 

-  The code may be organized into one or more Python files ( `.py` ) or Jupyter notebooks ( `.ipynb` ). 

-  Include a short `README.txt` file explaining how to run the code and listing any required packages. 

-  The submitted code should reproduce all analyses, tables, and figures presented in the report. 

-  Use fixed random seeds whenever randomization is involved (e.g., train–test splitting, Random Survival Forests, or neural network training). 

## **Suggested report structure** 

Your report should include the following sections: 

### 1. **Title** 

Provide a clear and informative title. 

### 2. **Introduction and motivation** 

Present the clinical or scientific context of the problem and state the research questions addressed in the project. 

### 3. **Data and preprocessing** 

Briefly describe the dataset, the survival outcome, censoring, covariates, and preprocessing steps used in the analysis. Include essential details only; do not attach the dataset. 

### 4. **Brief recap of previous analyses** 

Summarize the main findings from Project Assignments 1 and 2 that are needed to motivate the final project. Do not reproduce the full previous analyses. 

### 5. **Methods** 

Describe the statistical and machine-learning methods used in the project, including the train–test split, the Cox model, Random Survival Forests, DeepSurv, Cox-Time, prediction procedures, calibration assessment, and test-set evaluation metrics. 

The Methods section should also include relevant implementation details, such as software packages, random seed, hyperparameter choices, and validation strategy if a validation set was used. 

2 

### 6. **Results** 

Present the main empirical findings. Include the refitted Cox model results, one-year prediction curves, model comparison results, calibration assessment, integrated Brier scores, and additional analyses motivated by your research questions. 

Every table and figure should be accompanied by a brief interpretation. Do not simply present numerical results; explain what they imply in the context of your research questions. 

### 7. **Discussion** 

Interpret the results in relation to your research questions. Discuss whether the different models led to similar or different conclusions, which model performed best, the strengths and limitations of your analysis, and possible extensions. 

8. **References (optional)** 

If external resources beyond the course materials were used (e.g., research papers or online documentation), cite them using a consistent citation style. 

## **Figures and tables** 

-  All figures and tables should be numbered. 

-  Each figure and table should have a descriptive caption. 

-  Axes should be clearly labeled, legends should be included where appropriate, and figures should be sufficiently large and readable. 

-  Refer to each figure and table explicitly in the main text. 

## **What not to include** 

-  Do not include source code in the report. Submit the code separately as a ZIP archive. 

-  Do not include the dataset. 

-  Do not submit multiple report files. 

-  Do not include raw software output without explanation. 

## **Writing style** 

-  Write clearly and concisely, using terminology appropriate for scientific writing. 

-  Define all symbols and abbreviations. 

-  Structure the report using clear sections and paragraphs. 

3 

-  Use visualizations to illustrate key findings, and refer to them appropriately in the text. 

-  You may use AI tools to assist with programming, writing, or editing. However, you remain fully responsible for the correctness of all analyses, interpretations, and conclusions. All submitted work should reflect your own understanding. 

4 

