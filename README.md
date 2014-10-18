##The following section needs the gdata package for selection for column names. (It will be used to select the measurements that include mean and standard deviation.)
##install gdata package for column selection
##install.packages("gdata")


##The first steps is to read the necessary text files. There are totally 8 text files. There are 1) labels for 561 features measurements. 2) labels for activity type when the subjects were wearing the devices and the signals were collected. 3) single column that contains the subject labels in the training data, which can be used to connect with the information from measurement. 4)single column that contains the activity type labels in the training data, which can be used to connect with the information from measurement. 5) the measurement information for 561 features in the training data. File 6-8 are similar to File 3-5, but the subjects are in the test section.
##The labels from all the features included will be read and tranformed to a data frame that can be used as the column name in the later steps.


##read features.txt, which contains the list of all features
feature <-read.table("./UCI HAR Dataset/features.txt", colClasses="character")

##remove the column name
names(feature) <- NULL
##delete the first column that contains V1,V2, etc.
feature <- feature[,-1]
##tranform row to column
colfeature <- t(feature)


##read the activity_labels.txt, which contains 6 activities
actlab <-(read.table("./UCI HAR Dataset/activity_labels.txt", colClasses="character"))
##lower the cases
actlab$V2 <-tolower(actlab$V2)


##read the subject_train.txt, of which each row identifies the subject who performed the activity in the training part.
##train subject data: (7352 obs. 30); single column
subtrain <-read.table("./UCI HAR Dataset/train/subject_train.txt")


##read the y_train.txt, which has the numeric codes of the activities each subject was doing when the measurement was taken.
##the codes correspond to those in the activity_labes.txt; single column
trainlab <-read.table("./UCI HAR Dataset/train/y_train.txt")


##read the X_train.txt, which contains the features information for the subjects in the training set.
##(7352 obs, V561) A 561-feature vectors with time and frequency domain variable. These features correspond to those in the features.txt.
train <-read.table("./UCI HAR Dataset/train/X_train.txt", stringsAsFactors=FALSE)


##read the subject_test.txt, of which each row identifies the subject who performed the activity in the test part.; single column
subtest <-read.table("./UCI HAR Dataset/test/subject_test.txt")


##read the y_test.txt, which has the numeric codes of the activities each subject was doing when the measurement was taken.
##the codes correspond to those in the activity_labes.txt; single column
testlab <-read.table("./UCI HAR Dataset/test/y_test.txt")

##read the X_test.txt, which contains the features information for the subjects in the testing set.
##A 561-feature vectors with time and frequency domain variable. These features correspond to those in the features.txt.
#(2947 obs, V561)
test <-read.table("./UCI HAR Dataset/test/X_test.txt", stringsAsFactors=FALSE)



###After reading files, the subject labels, the activity labels and the measurement information in the training part are combined together. Then use the same way to combine those in the testing part. Finally, these two part are combined toghether.

###Merges the training and the test sets to create one data set. 

##(1)combine activity labels, subject labels, and the collected information in the training set.
new_training <- cbind(trainlab, subtrain, train)

##(2)combine activity labels, subject labels, and the collected information in the test set.
new_test <- cbind(testlab, subtest, test)

##(3)combine previous two data frames: training and test data
a_newdata <- rbind(new_training, new_test)

##(4)used the tranformed feature labels from the first section as the column names of combined new dataset from the last step.
#add two column names for the columns that contain information of activity and subject.
colnames(a_newdata) <- c("activity", "subject_id", colfeature)



###The third step is to extract the necessary measurement. The column variables include the measurement variables.
###Extracts the measurements that either has the mean and standard deviation.

##Every column contains a specific measurement, so columns were selected by names that include "mean", "Mean", or "std".
##Use gdata package to create the list of column names that include the criteria.
library(gdata)
matchlist <- matchcols(a_newdata, with=c("mean", "Mean", "std"), method="or")
list <- as.character(unlist(matchlist, use.names = FALSE))

##use the list to subset the combined data to form an extracted data.
b_newdata <- subset(a_newdata,select=c("activity", "subject_id", list))



####After retrieving the needed measurment variables, all the measurements from single variable for each subject and each activity are aggregated and calcaluate the mean. From here, a new dataset is generated.
###Creates a data set with the average of each variable for each activity and each subject.

##aggregate the data by the columns of activity label and subject labels, and generate the means for each measurement.
attach(b_newdata)
aggdata <-aggregate(b_newdata, by=list(activity, subject_id), FUN=mean, na.rm=TRUE)
##order the dataset first by activity column and then by subject labels.
aggdata <- aggdata[order(aggdata$activity, aggdata$subject_id) , ]



#####Finally, the labels for each activity and measurement are attached to the new dataset and rewrite some of the variable names. 
###Labels the data set with descriptive variable names and activities. 

##merge the activity label (actlab, by column V1) from the first section to aggdata (by activity column)
c_newdata <- merge(actlab, aggdata, by.x="V1", by.y="activity", all=TRUE)
##remove unnecessary columns (column group1 and group2 generated from the aggregation process and V1 from the merging process.)
c_newdata <-c_newdata[,c(-1, -3, -4)]

##replacement some text strings in the variable names(column names)- feature measurements.
df <- colnames(c_newdata) 
df <- gsub("()", "", df, fixed = TRUE)
df <- gsub("-", "_", df, fixed =TRUE)
df <- gsub("BodyBody", "Body", df, fixed =TRUE)
df <- gsub(",", "_", df, fixed =TRUE)
df <- gsub("angle(tBodyAccJerkMean)_gravityMean)", "angle(tBodyAccJerkMean_gravityMean)",df, fixed =TRUE)
df <- sub("V2", "activity_type", df)
colnames(c_newdata) <- df


###save the dataset
write.table(c_newdata, file = "tidydata.txt", col.names = TRUE, row.names = FALSE)

