# Getting and Cleaning Data - Course Project

The data and instructions used for this project were sourced from the assignment on Coursera.

[Link to original data source.](https://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

[Link to data set names.](https://archive.ics.uci.edu/ml/machine-learning-databases/00240/UCI%20HAR%20Dataset.names)

This code first reads a file (features.txt) that contains the full list of variables (i.e.: columns) that are represented in the main data files for this project (X_test.txt & X_train.txt). These variables are meaningfully named in the context of the subject matter, and are judged to meet tidy data naming requirements.

These column names are named consistently such that those columns describing mean or standard deviation can be found by searching for "mean()" and "std()" (using grep).  This search returns a list of column indexes which is used to subset the data (which is then combined using rbind).

Additional columns are contained in:
* Y_test.txt & Y_train.txt - activity data, for which names are found in activity_labels.txt.
* subject_test.txt & subject_train.txt - data that identifies the subject/volunteer from which data was taken

Activity names are merged with the activity data (using merge and cbind), and both activity and subject data is merged with the main data. Column names are also added (using colnames), including names for the two additional columns
* "Subject" - an integer representing the volunteer from whom the data was sourced
* "Activity" - text that describes the activity being undertaken by the volunteer during data recording, e.g.: SITTING

Averages of all mean/std variables are calculated and grouped by Subject and Activity (using aggregate), and the result is written to a tab-delimited file named tidy_data.txt. Read the tidy data file in with:
df <- read.table("tidy_data.txt", header = TRUE)
