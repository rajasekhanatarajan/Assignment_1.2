What should be the output of the following Script?
v <- c( 2,5.5,6)

t <- c(8, 3, 4)

print(v%/%t)

ans:[1] 0 1 1

You have 25 excel files with names as xx_1.xlsx, xx_2.xlsx,……..xx_25.xlsx in a dir.
Write a program to extract the contents of each excel sheet and make it one df.

ans:

getwd()

library(xlsx)

files=list.files(pattern=".xlsx")

for(i in 1:length(files))

{filename=files[i]

data=read.xlsx(file = filename,header = T)

assign(x = filename,value = data)}

#you can bind them together in one dataframe with bind_rows from dplyr:

library(dplyr)

#one more option is as follows

df<-lapply(files, read.xlsx) %>% bind_rows()

If the above 25 files were csv files, what would be your script to read?
ans:

getwd()

files=list.files(pattern=".csv")

for(i in 1:length(files))

{filename=files[i]

data=read.csv(file = filename,header = T)

assign(x = filename,value = data)}

#Suppose the columns are the same for each file,

#you can bind them together in one dataframe with bind_rows from dplyr:

library(dplyr)

#one more option is as follows

df<-lapply(files, read.csv) %>% bind_rows()
