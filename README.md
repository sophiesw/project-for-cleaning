

The following section needs the gdata package for selection for column names. (It will be used to select the measurements that include mean and standard deviation.)

The first steps is to read the necessary text files. There are totally 8 text files. There are 1) labels for 561 features measurements. 2) labels for activity type when the subjects were wearing the devices and the signals were collected. 3) single column that contains the subject labels in the training data, which can be used to connect with the information from measurement. 4)single column that contains the activity type labels in the training data, which can be used to connect with the information from measurement. 5) the measurement information for 561 features in the training data. File 6-8 are similar to File 3-5, but the subjects are in the test section.

After reading files, the subject labels, the activity labels and the measurement information in the training part are combined together. Then use the same way to combine those in the testing part. Finally, these two part are combined toghether.

The third step is to extract the necessary measurements. The column variables include the measurement variables. Therefore, the desired measurement variables will be selected from the column names.

After retrieving the needed measurment variables, all the measurements from single variable for each subject and each activity are aggregated and calcaluate the mean. From here, a new dataset is generated.

Finally, the labels for each activity and measurement are attached to the new dataset and rewrite some of the variable names. 
