                                                  Online lab assignment “Decision Trees”
Pre-requisite to carrying out the assignment:
1. Go through and watch all the lectures & lab tutorials of modules 8&9:
2. Download the student performance dataset, which is available on the UC Irvine machine learning repository at https://archive.ics.uci.edu/ml/datasets/student+performance.
3. Study the metadata explained under dataset and attribute information.
4. Extract the files from the student.zip folder and we will use the student-por.csv

Assignment due date: end of week # 10
You will have to provide a demonstration video for your solution and upload the video together with the solution on eCentennial through the assignment link. See the video recording instructions at the end of this document.
Load & check the data: 35 marks
1. Load the data (student-por.csv) into a pandas dataframe named data_firstname where first name is you name.
2. Carryout some initial investigations:
a. Check the names and types of columns.
b. Check the missing values.
c. Check the statistics of the numeric fields (mean, min, max, median, count,..etc.)
d. Check the categorical values.
e. In you written response write a paragraph explaining your findings about each column.
Pre-process and prepare the data for machine learning
3. Create a new target variable i.e. column name it pass_fristname, which will store the following per row:
a. 1 : if the total of G1, G2, G3 is greater or equal to 35
b. 0 : if the total of G1, G2, G3 is less than 35
4. Drop the columns G1, G2, G3 permanently.
5. Separate the features from the target variable (class) and store the features into a dataframe named features_first name and the target variable into a dataframe named target_variable_firstname.
6. Print out the total number of instances in each class and note into your report and explain your findings in terms of balanced and un-balanced.
7. Create two lists one to save the names of your numeric fields and on to save the names of your categorical fields. Name the lists numeric_features_firstname and cat_features_firstname respectively. To build the lists refer to the documentation https://pandas.pydata.org/pandas- docs/stable/reference/api/pandas.DataFrame.select_dtypes.html , be very careful what options you select and you don’t miss any columns.
8. Prepare a column transformer to handle all the categorical variables and convert them into numeric values using one-hot encoding. The transformer must preserve the rest of the columns. Refer to the following documentation https://scikit- learn.org/stable/modules/generated/sklearn.compose.ColumnTransformer.html and carefully check all the parameters. Name the transformer transformer_firstname.
9. Prepare a classifier decision tree model i.e. an estimator name it clf_firstname, set the criterion="entropy"and max_depth = 5. Refer to the documentation https://scikit-
learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html and check all possible parameters.
10. Build a pipeline name it pipeline_first_name. The pipeline should have two steps the first the column transformer you prepared in step 8 and the second the model you prepared in step 9.
11. Split your data into train 80% train and 20% test, use the last two digits of your student number for the seed. Name the train/test dataframes as follows : X_train_firstname, X_test firstname, y_train firstname, y_test firstname.
Build Classification Models 25 marks
12. Fit the training data to the pipeline you built in step #11.
13. Cross validate the output on the training data using 10-fold cross validation and use the last two digits of your student ID as seed and set the shuffle to True.
14. Print out the ten scores and the mean of the ten scores and add it to your written response.
15. Visualize the tree using Graphviz.
Note: If Graphviz is not installed please use an anaconda command prompt to install using:
conda install graphviz python-graphviz
Then make sure to add the path to the graphviz binaries to your environmental variables. On windows these paths could be:
C:\Anaconda3\envs\env_name\Library\bin\graphviz or C:\Anaconda3\Library\bin\graphvi z
16. Save the tree to a .png file and add it to your submission.
17. In you written response describe the key findings for the first level split i.e. which field it split on what are the samples.
18. Print out two accuracy score one for the model on the training set i.e. X_train, y_train and the other on the testing set i.e. X_test, y_test. Record both results in your written response.
19. Use the model to predict the test data and printout the accuracy, precision and recall scores and the confusion matrix. Note the results in your written response.
Fine tune the model 40 marks
20. Using Randomized grid search fine tune your model using the following set of parameters
parameters= parameters={'m min_samples_split' : range(10,300,20),'m max_depth': range(1,30,2),'m min_samples_leaf':range(1,15,3)}
For the randomized grid search object set the following parameters:
a. estimator= pipeline_first_name
b. param_grid= pipeline_first_name
c. scoring='accuracy'
d. param_distributions=parameters
e. cv=5
f. n_iter = 7 (Number of parameter settings that are sampled. n_iter trades off runtime vs quality of the solution.)
g. refit = True
h. verbose = 3
To learn how to use randomized grid search check the following reference: https://scikit- learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html
21. Fit your training data to the gird search object
22. Print out the best parameters and note them it in your written response.
23. Print out the score of the model and note it in your written response compare this score with original score you generated in step #14 is it better or worse and explain why.
24. Printout the best estimator and note it in your written response
25. Fit the test data using the fine-tuned model identified during grid search i.e the best estimator saved in the grid search object and note it in your written response.
26. Printout the precision, re_call and accuracy. Compare them with earlier readings you generated during steps 20. Are the better or worse explain why.
27. Save the model using the joblib (dump). Note the type should be .pkl
28. Save the full pipeline using the joblib – (dump).
Evaluation criteria
Not acceptable
Below
Average
Average
Competent
Excellent
0% - 24%
25%-49%
50-69%
70%-83%
84%-100%
Data exploration Visualization &
Pre-processing code
30%
Missing all requirements required
Some requirements are implemented.
Majority of requirements are implemented but some are malfunctioning.
Majority of requirements implemented.
All requirements are implemented
Correctly.
Model building Validation
&Testing
30%
No evidence of testing and evaluation of the requirements.
Minor evaluation and testing efforts.
Some of the requirements have been tested & evaluated.
Majority of requirements are tested & evaluated. Realistic evaluation and testing, comparing the solution to the requirements.
Code Documentation
5%
No comments explaining code.
Minor comments are implemented.
Some code is correctly commented.
Majority of code is correctly commented.
All code is correctly commented.
Written analysis
Content
10%
Missed all the key ideas; very shallow.
Shows some thinking and reasoning but most ideas are underdeveloped.
Indicates thinking and reasoning applied with original thought on a few ideas.
Indicates original thinking and develops ideas with sufficient and firm evidence.
Indicates synthesis of ideas, in-depth analysis and evidences original thought and support for the topic.
Written analysis Format and organization
5%
Writing lacks logical organization. It shows no coherence and ideas lack unity. Serious errors. No transitions.
Writing lacks logical organization. It shows some coherence but ideas lack unity. Serious errors.
Format needs
Writing is coherent and logically organized. Some points remain misplaced.
Format is neat but has some assembly errors.
Writing is coherent and logically organized with transitions used between ideas and paragraphs to create coherence. Overall unity of
Writing shows high degree of attention to logic and reasoning of all points. Unity clearly leads the reader to the conclusion.
Format is very messy.
attention, some major errors.
ideas is present. Format is neat and correctly assembled.
Format is neat and correctly assembled with professional look.
Demonstration Video
20%
Very weak no mention of the code changes. Execution of code not demonstrated.
Some parts of the code changes presented.
Execution of code partially demonstrated.
All code changes presented but without explanation why. Code demonstrated.
All code changes presented with explanation, exceeding time limit. Code demonstrated.
A comprehensive view of all code changes presented with explanation, within time limit. Code demonstrated.
Demonstration Video Recording
Please record a short video (max 8 minutes) to explain/demonstrate your assignment solution. You may use the Windows 10 Game bar to do the recording:
1. Press the Windows key + G at the same time to open the Game Bar dialog.
2. Check the "Yes, this is a game" checkbox to load the Game Bar.
3. Click on the Start Recording button (or Win + Alt + R) to begin capturing the video.
4. Stop the recording by clicking on the red recording bar that will be on the top right of the program window.
(If it disappears on you, press Win + G again to bring the Game Bar back.)
You'll find your recorded video (MP4 file), under the Videos folder in a subfolder called Captures. Or
You can use any other video recording package freely available.
End of lab assignment
