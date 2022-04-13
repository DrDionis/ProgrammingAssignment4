This script performs preparation of the data according to the assignment requirements.

1. Download the dataset
The dataset is downloaded and extracted into the folder called UCI HAR Dataset.

2. Assign each data to variables
features <- features.txt : 561 observations, 2 variables.
The features selected for this database are obtained from the accelerometer and gyroscope 3-axial raw signals.

activities <- activity_labels.txt : 561 observations, 2 variables.
List of activities and its codes.

subject_train <- test/subject_train.txt : 7352 observations, 1 variable.
contains train data of 21/30 volunteer train subjects observed

x_train <- test/X_train.txt : 7352 observations, 561 variables.
contains the recorded train data of the features

y_train <- test/y_train.txt : 7352 observations, 1 variable.
contains the train data of the code labels of the activities

subject_test <- test/subject_test.txt : 2947 observations, 1 variable.
contains test data of 9/30 volunteer test subjects observed

x_test <- test/X_test.txt : 2947 observations, 561 variables.
contains the test data of the features

y_test <- test/y_test.txt : 2947 observations, 1 variable.
contains the test data of the code labels of the activities


3. Merges the training and the test sets to create one data set
x_set (10299 observations, 561 variables) is created by merging x_train and x_test using rbind() function
y_set (10299 observations, 1 variable) is created by merging y_train and y_test using rbind() function
Subject (10299 observations, 1 variable) is created by merging subject_train and subject_test using rbind() function
Merged_Data (10299 observations, 563 variables) is created by merging Subject, x_set and y_set using cbind() function

4. Extracts only the measurements on the mean and standard deviation for each measurement
Tidy (10299 observations, 88 variables) is created by sub-setting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

5. Uses descriptive activity names to name the activities in the dataset
Entire numbers in code column of the Tidy replaced with corresponding activity taken from second column of the activities variable

6. Appropriately labels the dataset with descriptive variable names
code column in Tidy renamed into activities
All Acc in the name of the column is replaced with Accelerometer
All Gyro in the name of the column is replaced with Gyroscope
All BodyBody in the name of the column is replaced with Body
All Mag in the name of the column is replaced with Magnitude
All that starts with character f in the name of the column is replaced with Frequency
All that starts with character t in the name of the column is replaced with Time
All that has -mean in the name of the column is replaced with Mean
All that has -std in the name of the column is replaced with STD
All that has -freq in the name of the column is replaced with Frequency
All that has angle in the name of the column is replaced with Angle
All that has gravity in the name of the column is replaced with Gravity

7. From the dataset in step 4, creates a second, independent tidy dataset with the average of each variable for each activity and each subject
Final_Data (180 observations, 88 variables) is created by summarizing Tidy taking the means of each variable for each activity and each subject after grouped by subject and activity.
Export Fina_lData into final_D_data.txt file.