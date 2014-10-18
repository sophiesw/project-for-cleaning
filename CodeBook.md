CodeBook

"activity_type" 
Description: The activities that each person performed when wearing a smartphone on the waist.
Value: walking, walking_upstairs, walking_downstairs, sitting, standing, laying

"subject_id"
Description: The identifiers for 30 volunteers
Value: 1-30

The following variables were retrieved from the complete list of variables of each feature vactor. The retrieved criteria were the variables must either have mean or standard deviation. After retrieving, the values from each measurement were averaged for the same subject with the same activity. Therefore, the values in this dataset for the variables is a mean.

The meaning of abbreviation in the variables follow the below rules.
t: time domain signals
f: frequency domain signals
X,Y,Z: denoted three axial
tBodyAcc: body acceleration signals
tGravityAcc: gravity acceleration signals
tBodyAccJerk: signals obtained from the body linear acceleration 
tBodyGyroJerk: signals obtained from angular velocity 
tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag: magnitude(Mag) calculated using the Euclidean norm.
fBodyAcc, fBodyAccJerk, fBodyGyro, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag: applied with a Fast Fourier Transform
angle() variable: additional vectors obtained by averaging the signals in a signal window sample
mean: Mean value
std: Standard deviation
Note: Features are normalized and bounded within [-1,1].

Detailed name of measured variables included in this dataset.
"tBodyAcc_mean_X"
"tBodyAcc_mean_Y" 
"tBodyAcc_mean_Z"
"tGravityAcc_mean_X"
"tGravityAcc_mean_Y"
"tGravityAcc_mean_Z"
"tBodyAccJerk_mean_X"
"tBodyAccJerk_mean_Y"
"tBodyAccJerk_mean_Z"
"tBodyGyro_mean_X"
"tBodyGyro_mean_Y"
"tBodyGyro_mean_Z"
"tBodyGyroJerk_mean_X"
"tBodyGyroJerk_mean_Y"
"tBodyGyroJerk_mean_Z"
"tBodyAccMag_mean"
"tGravityAccMag_mean"
"tBodyAccJerkMag_mean"
"tBodyGyroMag_mean"
"tBodyGyroJerkMag_mean"
"fBodyAcc_mean_X"
"fBodyAcc_mean_Y"
"fBodyAcc_mean_Z"
"fBodyAcc_meanFreq_X" 
"fBodyAcc_meanFreq_Y"
"fBodyAcc_meanFreq_Z"
"fBodyAccJerk_mean_X"
"fBodyAccJerk_mean_Y"
"fBodyAccJerk_mean_Z"
"fBodyAccJerk_meanFreq_X"
"fBodyAccJerk_meanFreq_Y"
“fBodyAccJerk_meanFreq_Z"
“fBodyGyro_mean_X"
“fBodyGyro_mean_Y" 
"fBodyGyro_mean_Z"
“fBodyGyro_meanFreq_X"
“fBodyGyro_meanFreq_Y"
“fBodyGyro_meanFreq_Z"
"fBodyAccMag_mean" 
“fBodyAccMag_meanFreq" 
“fBodyAccJerkMag_mean" 
“fBodyAccJerkMag_meanFreq" 
”fBodyGyroMag_mean"
“fBodyGyroMag_meanFreq"
“fBodyGyroJerkMag_mean"
“fBodyGyroJerkMag_meanFreq" 
”angle(tBodyAccMean_gravity)"
“angle(tBodyAccJerkMean_gravityMean)"
“angle(tBodyGyroMean_gravityMean)"
“angle(tBodyGyroJerkMean_gravityMean)"
”angle(X_gravityMean)"
“angle(Y_gravityMean)"
“angle(Z_gravityMean)"
“tBodyAcc_std_X" 
”tBodyAcc_std_Y" 
“tGravityAcc_std_X"
“tGravityAcc_std_Y" 
”tGravityAcc_std_Z" 
“tBodyAccJerk_std_X" 
“tBodyAccJerk_std_Y"
“tBodyAccJerk_std_Z" 
”tBodyGyro_std_X"
“tBodyGyro_std_Y"
“tBodyGyro_std_Z"
“tBodyGyroJerk_std_X" 
”tBodyGyroJerk_std_Y"
“tBodyGyroJerk_std_Z"
“tBodyAccMag_std" 
“tGravityAccMag_std" 
”tBodyAccJerkMag_std"
“tBodyGyroMag_std" 
“tBodyGyroJerkMag_std"
“fBodyAcc_std_X"
”fBodyAcc_std_Y" 
“fBodyAcc_std_Z" 
“fBodyAccJerk_std_X" 
“fBodyAccJerk_std_Y" 
”fBodyAccJerk_std_Z" 
“fBodyGyro_std_X" 
“fBodyGyro_std_Y" 
“fBodyGyro_std_Z" 
”fBodyAccMag_std" 
“fBodyAccJerkMag_std"
“fBodyGyroMag_std" 
“fBodyGyroJerkMag_std"

