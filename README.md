# Getting and Cleaning Data - Course Project

This code first reads a file (features.txt) that contains the full list of variables (i.e.: columns)
that are represented in the main data files for this project (X_test.txt & X_train.txt).

These column names are named consistently such that those columns describing mean or standard deviation
can be found by searching for "mean()" and "std()" (using grep).  This search returns a list
of column indexes which is used to subset the data (which is combined using rbind).

Additional columns are contained in:
Y_test.txt & Y_train.txt - activity data, for which names are found in activity_labels.txt
subject_test.txt & subject_train.txt - data that indetifies the subject/user from which data was taken

Activity names are merged with the activity data (using merge and cbind), and both activity and subject
data is merged with the main data. Column names are also added (using colnames).

Averages of all mean/std variables are calculated and grouped by Subject and Activity (using aggregate),
and the result is written to a file.
