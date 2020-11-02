
dataDir <- "UCI HAR Dataset"
testDir <- "test"
trainDir <- "train"

# Read testdata
testData <- read.table(paste(dataDir, testDir, "X_test.txt", sep = "/"))
# Read traindata
trainData <- read.table(paste(dataDir, trainDir, "X_train.txt", sep = "/"))
# Merge testdata and traindata, i.e. concatenate both datasets in one dataset: allData
allData <- rbind(testData, trainData)

## Objective 1 fulfilled:
## 1. Merges the training and the test sets to create one data set.


# Add column names/variable names to allData
# Read features
features <- read.table(paste(dataDir, "features.txt", sep = "/"))
colNames <- features[,2]
names(allData) <- colNames

## Objective 4 fulfilled:
## 4. Appropriately labels the data set with descriptive variable names.


# Extract only the measurements on the mean and standard deviation for each measurement.
# These measurements are characterized by their column names.
# These column names contain "-mean()" or contain "-std()".
columns <- grep(pattern="-mean\\(\\)|-std\\(\\)", colNames)
allData <- allData[, columns]

## Objective 2 fulfilled:
## 2. Extracts only the measurements on the mean and standard deviation for each measurement.


# Add the activity for each measurement
# Read the test activities
testActivities <- read.table(paste(dataDir, testDir, "y_test.txt", sep = "/"))
# Read the train activities
trainActivities <- read.table(paste(dataDir, trainDir, "y_train.txt", sep = "/"))
# Merge the test and train activities
allActivities <- rbind(testActivities, trainActivities)
names(allActivities)[1] <- "ActivityId"

# Read the activity labels, a description of the activities,
# and add these to the dataset as the first column.
activityLabels <- read.table(paste(dataDir, "activity_labels.txt", sep = "/"))
allActivityLabels <- activityLabels[allActivities[,1],2]
allData <- cbind(allActivityLabels, allData)
names(allData)[1] <- "Activity"

## Objective 3 fulfilled:
## 3. Uses descriptive activity names to name the activities in the data set
## The column with activity names is labeled "Activity", according to
## objective 4.

# Save the dataset as a csv file
write.csv(allData, file = "allData.csv", row.names = FALSE)


# Create a second independent tidy data set with the average of each variable 
# for each activity and each subject.

# Read subjects for testdata
subjectTest <- read.table(paste(dataDir, testDir, "subject_test.txt", sep = "/"))
# Read subjects for traindata
subjectTrain <- read.table(paste(dataDir, trainDir, "subject_train.txt", sep = "/"))
# Merge subjectTest and subjectTrain, i.e. concatenate both subject sets in one subjectset: subjects
subjects <- rbind(subjectTest, subjectTrain)

# Add the subjects as a column to the measurements, allData
subjectData <- cbind(subjects, allData)
# Calculate the average/mean of the measurements
subjectData <- aggregate(subjectData[, 3:length(subjectData)], list(subjectData$V1, subjectData$Activity), mean)
# Reorder and label the subjet and activity columns
names(subjectData)[1:2] <- c("Subject", "Activity")
subjectData <- subjectData[with(subjectData, order(Subject, Activity)),]

# Save the dataset as a csv file
write.csv(subjectData, file = "subjectData.csv", row.names = FALSE)
