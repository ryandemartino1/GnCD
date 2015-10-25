---
title: "CodeBook"
author: "Ryan deMartino"
date: "Friday, October 23, 2015"
output: html_document
---

BRIEF DESCRIPTION:  The data were provided as .txt files containing measurements from a smartphone (561 different measurements at each sample time), a list of those variable names, a list of subjects (as numbers) corresponding to the measurements, a list of activities (walking, laying, etc.) as numbers corresponding to the measurements.

VARIABLES:

  Inital load of raw data, read with read.table():
    features - contains the list of the variable names measured in the study (ex: "fBodyGyro-mean()-X")
    subt - contains the list of subjects for each measurement from the test data set
    subtr - contains the list of subjects for each measurement from the training data set
    tlabs - contains the list of activities for each measurement (as a number) from the test data set
    trlabs - contains the list of activities for each measurement (as a number) from the training data   
      set
    tset - contains the measurements of the variables listed in features for the test data set
    trset - contains the measurements of the variables listed in features for the training data set
    alabs - contains the description of the numbered activity labels found in tlabs and trlabs
  
  First step (combined tset, subt, tlabs with cbind()):
    tcomb - contains a set with all relevant data and labels (except activity descriptions) for test set
    , used cbind
    trcomb - contains a set with all relevenat data and labels (except activity descriptions) for 
    training set, used cbind
    comb - contains the combined set of both test and training sets (tcomb + trcomb), used rbind
    dummy - dummy var to hold the future column titles "Subject" and "ActivityNum"
    fhead - features + dummy; will be used to name all of the columns in comb variable, used rbind
    temp - the comb variable with duplicate names removed to make the select function work properly
    cleancomb - pulls only means, stdevs, and Subject/ActivityNum columns, used select and contains
    /matches
    combfinal - cleancomb merged with alabs to put the activity descriptions in, used merge
    summarizeddata - the final output file, contains the summarized data by Subject, Activity, and 
    variable, used ddply
