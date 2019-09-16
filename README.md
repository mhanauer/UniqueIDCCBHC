# UniqueIDCCBHC
########## Unique ID for Qlik AVATAR IDs
### Before running, copy IDs from ACCESS and place new IDs underneath with 2's in the indicator save new data set and run the code below.
setwd("S:/Indiana Research & Evaluation/Matthew Hanauer/CCBHCTracking")
UniqueIDTester = read.csv("UniqueIDTester.csv", header= TRUE)
UniqueIDTester$dup_var = duplicated(UniqueIDTester$AVATAR.ID)
tail(UniqueIDTester)
UniqueIDTester = subset(UniqueIDTester, dup_var == FALSE & Indicator == 2)
UniqueIDTester = data.frame(AVATAR.ID = UniqueIDTester$AVATAR.ID)
write.csv(UniqueIDTester, "unique_ID_results.csv", row.names = TRUE)
