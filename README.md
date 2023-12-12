# Diamond-reports-on-R
# Diamonds
# case study on diamonds 
In this case study we will use different R Visualizations  methods on diamonds data to get useful nsights.
 * This dataset contains information about 53,940 round-cut diamonds and 10 variables measuring various pieces of information about the diamonds


install.packages("tidyverse")
library(tidyverse)
library(ggplot2)
data("diamonds")
View(diamonds)
### To see summarize  view of data frame 
 head(diamonds)
 
### to see broader view of a dataframe
 str(diamonds)
### To see column names
colnames(diamonds)
### to add any column
mutate(diamonds,carat_2=carat*100)
View(diamonds)


install.packages("here")
library(here)
install.packages("janitor")
library(janitor)
install.packages("skimr")
library(skimr)
skim_without_charts(diamonds)

This dataset contains information about 53,940 round-cut diamonds and 10 variables measuring various pieces of information about the diamonds
## To see structure of a data frame diamonds
head(diamonds)
## to see te glimpse of a dataframe
glimpse(penguins)
## to Sort
diamonds %>% arrange(price)
##Putting sort value in a variable diamonds_s
diamonds_s<-diamonds %>% arrange(price)


View(diamonds_s)

## mean of price of diamonds
diamonds %>% group_by(cut) %>% drop_na() %>% summarize(mean_pricem=mean(price))
## to find max price of diamonds
diamonds %>% group_by(cut) %>% drop_na() %>% summarize(max_price=max(price))
## to group 2 column cut and carat 
diamonds %>% group_by(cut,carat) %>% drop_na() %>% summarize(max_p1=max(price),mean_p1=mean(price))

![Screenshot (40)](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/752b59a5-2131-49de-959b-25282d71ccb4)

## Filter only fair cut
diamonds %>% filter(cut=="Fair")
## Adding new column 
mutate(diamonds,carat_2=carat*100)
![Screenshot (41)](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/ca1e1303-b966-4870-af1f-b9747a02c5ca)

#creating the plot cut length by price
ggplot(data = diamonds)+ geom_bar(mapping = aes(x=cut,fill=price))

![Rplot16](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/7f598154-c68c-4e9e-898c-cca5c818cd41)


# changing color to red
Adding border color red

ggplot(data = diamonds)+ geom_bar(mapping = aes(x=cut,fill=price,color="red"))

![Rplot17](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/8431505e-ecdd-45f7-8a6d-036f8eff8a4c)



## creating the carat by color bar plot 
ggplot(data = diamonds)+ geom_bar(mapping = aes(x=carat,fill=color))

![Rplot18](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/1a650187-1698-4815-9f2b-224bbabe57c6)

##  Creating the  carat by price bar plot

ggplot(data = diamonds)+ geom_bar(mapping = aes(x=carat,fill=price,color=clarity,shape=clarity,size=clarity))

![Rplot19](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/ff92c67e-a57c-4fd9-8673-b61b62c69d82)

## Showing Plot by adding  alpha
ggplot(data = diamonds)+ geom_bar(mapping = aes(x=cut,fill=price,alpha=clarity,color=clarity,shape=clarity,size=clarity))

![Rplot22](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/b335619c-53fe-4e0d-af9c-756e48c2254d)

#Showing plot through bar chart by facet_wrap

ggplot(data = diamonds)+ geom_bar(mapping = aes(x=cut,fill=price,alpha=clarity,color=clarity,shape=clarity,size=clarity))+
  facet_wrap(~clarity)

  ![Rplot23](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/dcbc6712-0eb8-47d6-9459-26f43c299105)


## Showing plot through bar chart by using facet_grid
ggplot(data = diamonds)+ geom_bar(mapping = aes(x=cut,fill=price,color=clarity,shape=clarity,size=clarity))+
  facet_grid(clarity~cut)
![Rplot26](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/6dfd69b9-a9e2-4066-a68f-7f42771584c3)






# Label fun and annonate
Giving title,subtitle,label and caption to the bar plot .

  ggplot(data = diamonds)+ geom_bar(mapping = aes(x=cut,fill=price,color=clarity,shape=clarity,size=clarity))+
  facet_grid(clarity~cut)+
  labs(title = "Cut by price",subtitle = "Bar plot", caption = "Data created by Moin Sabri ")+
  annotate("text",x=70,y=3500,label="S12",color="purple",fontface="bold",size=2.5,angle=70)


![Rplot25](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/cee3dac8-de8f-4509-9b1f-19771ef08a09)





