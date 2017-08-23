#global active power n day of week
#Assignment 2
a<-read.table("C:/Users/ba4205/Desktop/coursera/exdata_data_household_power_consumption/household_power_consumption.txt",sep=';',header = TRUE)
rm(a)
b<-subset(a,a$Date %in% (c('1/2/2007','2/2/2007')))

#remove NA value
global_active_power<-as.numeric(b$Global_active_power)
datetime <- strptime(paste(b$Date, b$Time, sep=" "), "%d/%m/%Y %H:%M:%S") 
#create empty file in working dir
png("plot2.png", width=480, height=480)
#create histogramh
plot(datetime,global_active_power,type="l", xlab="", ylab="Global Active Power (kilowatts)")

#save graph and close
dev.off()
