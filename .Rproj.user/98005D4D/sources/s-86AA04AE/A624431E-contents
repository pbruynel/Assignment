

dataDir <- "UCI HAR Dataset"

# Read testdata
testDir <- "test"
testDataFile <- "X_test.txt"
testDataPath <- paste(dataDir, testDir, testDataFile, sep = "/")
testData <- read.table(testDataPath)

fileName <- "X_test.txt"
testData <- readData(paste(dataDir, testDir, sep = "/"), fileName)

# Read traindata
trainDir <- "train"
trainDataFile <- "X_train.txt"
trainDataPath <- paste(dataDir, trainDir, trainDataFile, sep = "/")
trainData <- read.table(trainDataPath)

# Merge testdata and traindata, i.e. concatenate both datasets in one dataset: allData
allData <- rbind(testData, trainData)

## Objective 1 fulfilled:
## 1. Merges the training and the test sets to create one data set.


# Add column names/variable names to allData
featureFile <- "features.txt"
featureFilePath <- paste(dataDir, featureFile, sep="/")
features <- read.table(featureFilePath)
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
testActivitiesFile <- "y_test.txt"
testActivitiesPath <- paste(dataDir, testDir, testActivitiesFile, sep = "/")
testActivities <- read.table(testActivitiesPath, col.names="ActivityId")
# Read the train activities
trainActivitiesFile <- "y_train.txt"
trainActivitiesPath <- paste(dataDir, trainDir, trainActivitiesFile, sep = "/")
trainActivities <- read.table(trainActivitiesPath, col.names="ActivityId")
# Merge the test and train activities
allActivities <- rbind(testActivities, trainActivities)

# Read the activity labels, a description of the activities,
# and add these to the dataset as the first column.
activityLabelsFile <- "activity_labels.txt"
activityLabelsPath <- paste(dataDir, activityLabelsFile, sep="/")
activityLabels <- read.table(activityLabelsPath)
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
subjectTestFile <- "subject_test.txt"
subjectTestPath <- paste(dataDir, testDir, subjectTestFile, sep = "/")
subjectTest <- read.table(subjectTestPath)

# Read subjects for traindata
subjectTrainFile <- "subject_train.txt"
subjectTrainPath <- paste(dataDir, trainDir, subjectTrainFile, sep = "/")
subjectTrain <- read.table(subjectTrainPath)

# Merge subjectTest and subjectTrain, i.e. concatenate both subject sets in one subjectset: subjects
subjects <- rbind(subjectTest, subjectTrain)

# Add the subjects as a column to the measurements, allData
subjectData <- cbind(subjects, allData)
# Calculate the average/mean of the measurements
subjectData <- aggregate(subjectData[, 3:length(subjectData)], list(subjectData$V1, subjectData$Activity), mean)
# Reorder and label the subjet and activity columns
subjectData <- subjectData[,c(2,1,3:length(subjectData))]
names(subjectData)[1:2] <- c("Subject", "Activity")
subjectData <- subjectData[with(subjectData, order(Subject, Activity)),]

# Save the dataset as a csv file
write.csv(subjectData, file = "subjectData.csv", row.names = FALSE)


# Returns a data.frame from the specified datafile.
#  - filePath = path to the file that contains the data
#  - fileName = name of the file that contains the data
readData <- function(filePath, fileName) 
{
  dataFile <- paste(filePath, fileName, sep = "/")
  read.table(dataFile)
}