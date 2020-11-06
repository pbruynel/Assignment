README
================

The repository contains files for the final assignment of the course
*Getting and Cleaning Data*.  
The course is the third of ten courses of the [Data Science Specialization](https://www.coursera.org/specializations/jhu-data-science) on Coursera offered by Johns Hopkins University.  

## Assignment
The assignment is described as follows:  

---

The purpose of this project is to demonstrate your ability to collect, work 
with, and clean a data set. The goal is to prepare tidy data that can be used 
for later analysis. You will be required to submit:

1. a tidy data set as described below
2. a link to a Github repository with your script for performing the analysis
3. a code book that describes the variables, the data, and any transformations 
or work that you performed to clean up the data called CodeBook.md.

You should also include a README.md in the repo with your scripts. This repo 
explains how all of the scripts work and how they are connected.  

One of the most exciting areas in all of data science right now is wearable 
computing - see for example this article . Companies like Fitbit, Nike, and 
Jawbone Up are racing to develop the most advanced algorithms to attract new 
users. The data linked to from the course website represent data collected from 
the accelerometers from the Samsung Galaxy S smartphone. A full description is 
available at the site where the data was obtained:  
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones  
Here are the data for the project:  
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip  
You should create one R script called run_analysis.R that does the following.

1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each 
measurement.
3. Uses descriptive activity names to name the activities in the data set
4. Appropriately labels the data set with descriptive variable names.
5. From the data set in step 4, creates a second, independent tidy data set with 
the average of each variable for each activity and each subject.

---

## Datasets
The repository contains the original dataset downloaded and unzipped from the 
source mentioned in the assignment.
All the original datafiles are located in the directory 'UCI HAR Dataset'.  
The resulting tidy dataset that is generated is named *allData* and is written 
to a txt-file named 'allData,txt'. It is contained in this repository.  
The additional dataset that is created from the *allData* dataset is named
*avgSubjectActivityData* and is also written to a txt-file 'avgSubjectActivityData.txt'.
This file is added to the repository as well.

## R-script
The R-script that carries out the transformation from the original datasets into
the *allData* tidy dataset and the *avgSubjectActivityData* dataset as well is 
found in the file 'run_analysis.R', as the assignment requires.  
For the script to run succesfully it is required that the current working 
directory contains the subdirectory 'UCI HAR Dataset', including the original 
datafiles.

## Other files
Besides the R-script and the datasets the repository contains a few other files:
CodeBook.md and README.md. Providing these two files is part of the assignment.  
The CodeBook.md file gives a description of the process of generating the tidy
dataset *allData* by the R-script run_analysys.R. Furthermore, it explains the 
structure and meaning of the tidy dataset.
The README.md is the file you are currently reading.
