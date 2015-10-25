---
title: "README"
author: "Ryan deMartino"
date: "Sunday, October 25, 2015"
output: html_document
---
For below: where tset (for example) is used, trset is interchangeable in terms of explanation.  The t and tr were chosen to represent the test and training sets, respectively.


Only one script was used for this - "run_analysis.R".  The script reads in the raw data into various variables (as described in CodeBook.md) and then combines the measurements (tset) with the subject (subt) and labels (tlabs) using cbind().  Once both sets were handled the same way, they were combined using rbind().  Next a variable containing the column labels (fhead) was applied to the combined set using names().  The subset of the set containing only means and standard deviations was created using select() and contains() and matches().  Finally, this was merged with the file containing the activity descriptions (to replace the previous numbers representing them) and summarized by taking the means of all of these variables using ddply() and numcolwise(mean).  