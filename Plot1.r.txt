
#electricity data plotting
#******************* https://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip
#Assignment 1
a<-read.table("C:/Users/suman/Desktop/datasciencecoursera/household_power_consumption.txt",sep=';',header = TRUE)
rm(a)
b<-subset(a,a$Date %in% (c('1/2/2007','2/2/2007')))

#frequency of kw
#remove NA value
global_active_power<-as.numeric(b$Global_active_power)
#create empty file in working dir
png("plot1.png", width=480, height=480)
#create histogramh
hist(global_active_power,col='red',main="global active power",xlab="global active power(kilowatt)")
#save graph and close
dev.off()

