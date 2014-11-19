##Get_and_Clean_project
##=====================

The assessed programming project required for the Getting & Cleaning Data course. Provided the R-script  
run-analysis.R is present in the top-level directory of the UCI_HAR directory, and sourced apppropriately
a call to the function run_analysis will perform the entire task. 

###[ run_analysis() ]  
 Function to perform the data cleaning and summarizing specified in the "Getting and Cleaning Data"  
 course as listed in the programming project specifications. A call to this function  will perform  
 the entire task  
 It will work as specified if it is run while the setwd() specifies the Global Environment as  
 the top level directory of the UCIHAR dataset  
 The initial merging, cleaning and selection of the data and assignment of meaningful labels  
 is perfomed by the function merge_subset_and_label()  
 This dataset (in the form of a data frame) is subsequently summarized by the function summary_mean(df)  
 by aggregating subsets of data corresponding to individual subject/activity labels, taking the   
 average of the mean values for each subset. This data is written to a text file named "data_mean_summ.txt"  
 =================================================================================================================  


###[ merge_subset_and_label() ]   
Function to :  
 ==(1) read the files summarising the numerical/positional codes and explicit labels for the   
   features recorded in these datasets   
 ==(2) from the feature labels identify the column indices of ALL labels containing "mean" or  
   "std" (case insensitive) maintaining relative order of labels  
 ==(3) make two calls to do_cbind(), with the tokens "train" and "test" to obtain matrices   
   containing the factor codes and feature values for both data sets (check for equality of  
   the number of observation within each terminate with error state if necessary)  
 ==(4) merge the training and test data sets into one matrix  
 ==(5) extract the factor columns and required feature columns fron the matrix  
 ==(6) give the columns the explicit labels as column names, convert to a data frames and convert   
      the numeric activity factors into explicit labels  
 ==(7) return the data frame  
 =================================================================================================================  


###[ do_cbind<-function(token) ]   
 Function to :  
 ==(1) accept a token ("test" or "train") to enable the explicit generation of valid  
    filenames for i) the codes for the activity associated with each observation ii) the subject  
    performing the activity for each observation iii) the 561 feature numerical vector generated  
    from the particular observation.  
 ==(2) read the data from files into dataframes check number of observations in each and return an  
    error state if they are NOT equal  
 ==(3) If equal,convert all data structures to matrices and prepend the subjectIDs and activity  
    codes to the left hand side (columns 1 and 2) of the matrix which.  
 ==(4) return the constructed matrix   =================================================================================================================    


###[ summary_mean(df) ]
 Function to:  
 ==(1)take a tidied data set in data frame format  
 ==(2) use aggregate() to subset the data according to the factors recorded in the   
   first two columns and calculates the mean value of the subset   
 ==(3) edit the column labels for the two factors to meaningful values   
 ==(4) Output the summary to a specified text file    
 =================================================================================================================  
