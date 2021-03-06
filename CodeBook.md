## Getting and Cleaning Data Course Project CodeBook


### Summary
This Codebook is constructed to provide additional information of the Getting and Cleaning
Course project that describes the variables, the data, and any transformations/work performed
to clean up the dataset provided by [The UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones) webpage.

### Source
The original source data can be downloaded from [here](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip). It is then unzipped, saved to the Course project folder and used for further R cleaning analysis.

### Required Software Package
[Reshape2](https://cran.r-project.org/web/packages/reshape2/README.html), for more information please visit the [CRAN page](https://cran.r-project.org/web/packages/reshape2/index.html).

### Detailed Description
The datasets are desgined for a series of experiements, that have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

### Attribute Information
For each record in the dataset it is provided:
- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope.
- A 561-feature vector with time and frequency domain variables.
- Its activity label.
- An identifier of the subject who carried out the experiment.

### Project Procedures:
a R script called run_analysis is created with the following 5 steps:
#### 1. Merge the traning and the test sets to create one data set.
A set of 8 text files from the data folder are read:  
-  **features.txt**, 
-  **activity_labels.txt**,  
-  **subject_train.txt**,  
-  **x_train.txt**,  
-  **y_train.txt**
-  **subject_test.txt**, 
-  **x_test.txt** , 
-  **y_test.txt**

Column names are first assigned before mergeing.

#### 2. Extracts only the meansurements on the mean and standard deviation for each measurement.
Subset the merged data by using grep() and gsub() functions to extract the mean and standard deviation.
#### 3. Uses descriptive activity names to name the activities in the data set
Assign the column names **trainSubjects** for subject_train.txt; 
**trainActivities** for y_train.txt, and **xtrain for** x_train.txt, merge them for a final train dataset. Assign **testSubjects** for sub_train.txt; **testActivities** for y_test.txt and **xtest** for x_test.txt. Merge the latter three for a final test dataset. Eventually merge train dataset and test dataset into a final dataset using cbind() function.
#### 4. Appropriately labels the data set with descriptive variable names
Labels the dataset with "Subject", "Actvity_ID" and "Activity_Label", then use melt() to format the data.
#### 5. Create a second independently tidy set with the average of each variable for each activity and subject.
Use dcast() function to reshape the data frame with the mean function applied and assign the name **tidy_data**, 
Finally we create a separate tidy dataset using **write.table()** function and **row.names=FALSE** attribute 

#### The result of tidy_data.txt consists of following variables:
tBodyAcc-mean()-X 
tBodyAcc-mean()-Y 
tBodyAcc-mean()-Z 
tBodyAcc-std()-X 
tBodyAcc-std()-Y 
tBodyAcc-std()-Z 
tGravityAcc-mean()-X 
tGravityAcc-mean()-Y 
tGravityAcc-mean()-Z 
tGravityAcc-std()-X 
tGravityAcc-std()-Y 
tGravityAcc-std()-Z 
tBodyAccJerk-mean()-X 
tBodyAccJerk-mean()-Y 
tBodyAccJerk-mean()-Z
tBodyAccJerk-std()-X 
tBodyAccJerk-std()-Y 
tBodyAccJerk-std()-Z 
tBodyGyro-mean()-X 
tBodyGyro-mean()-Y 
tBodyGyro-mean()-Z 
tBodyGyro-std()-X 
tBodyGyro-std()-Y 
tBodyGyro-std()-Z 
tBodyGyroJerk-mean()-X 
tBodyGyroJerk-mean()-Y 
tBodyGyroJerk-mean()-Z 
tBodyGyroJerk-std()-X 
tBodyGyroJerk-std()-Y 
tBodyGyroJerk-std()-Z 
tBodyAccMag-mean()
tBodyAccMag-std() 
tGravityAccMag-mean()
tGravityAccMag-std() 
tBodyAccJerkMag-mean() 
tBodyAccJerkMag-std() 
tBodyGyroMag-mean()
tBodyGyroMag-std() 
tBodyGyroJerkMag-mean() 
tBodyGyroJerkMag-std() 
fBodyAcc-mean()-X 
fBodyAcc-mean()-Y 
fBodyAcc-mean()-Z 
fBodyAcc-std()-X 
fBodyAcc-std()-Y
fBodyAcc-std()-Z 
fBodyAcc-meanFreq()-X 
fBodyAcc-meanFreq()-Y 
fBodyAcc-meanFreq()-Z 
fBodyAccJerk-mean()-X 
fBodyAccJerk-mean()-Y 
fBodyAccJerk-mean()-Z 
fBodyAccJerk-std()-X 
fBodyAccJerk-std()-Y 
fBodyAccJerk-std()-Z 
fBodyAccJerk-meanFreq()-X 
fBodyAccJerk-meanFreq()-Y 
fBodyAccJerk-meanFreq()-Z 
fBodyGyro-mean()-X 
fBodyGyro-mean()-Y 
fBodyGyro-mean()-Z 
fBodyGyro-std()-X 
fBodyGyro-std()-Y 
fBodyGyro-std()-Z 
fBodyGyro-meanFreq()-X 
fBodyGyro-meanFreq()-Y 
fBodyGyro-meanFreq()-Z 
fBodyAccMag-mean() 
fBodyAccMag-std() 
fBodyAccMag-meanFreq() 
fBodyBodyAccJerkMag-mean() 
fBodyBodyAccJerkMag-std() 
fBodyBodyAccJerkMag-meanFreq() 
fBodyBodyGyroMag-mean() 
fBodyBodyGyroMag-std() 
fBodyBodyGyroMag-meanFreq() 
fBodyBodyGyroJerkMag-mean() 
fBodyBodyGyroJerkMag-std() 
fBodyBodyGyroJerkMag-meanFreq()
