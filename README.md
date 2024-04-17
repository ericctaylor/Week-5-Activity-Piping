# Week-5-Activity-Piping

#TASK: run the code below to get and save the dataset
download.file(url = "https://projects.fivethirtyeight.com/soccer-api/international/2022/wc_matches.csv", destfile = "WorldCup.csv")
#Then you need to name your dataset. Run this:
WorldCup<- read.csv("WorldCup.csv")

#TASK: take a look at the World Cup data. 
summary(WorldCup)

#TASK: Install and call the dplyr package. 
install.packages("dplyr")
library(dplyr)

#Let's make a random sample of our data and save it
#Task: run the code below
mysample<-sample_n(WorldCup, size=15, replace = FALSE, weight = NULL, .env = NULL)

#TASK: Save the new sample as a csv file
write.csv(mysample, "mysample.csv")


#TASK: revise this code chunk using piping
mysample4 <- mysample %>%
  arrange(date) %>%
  filter(spi1 < 80) %>%
  rename(Index1 = spi1, Index2 = spi2) %>%
  select(Index1, Index2, team1, team2) %>%
  summary() %>%
  print()
