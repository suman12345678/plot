
#4 different plot 
a<-read.table("C:/Users/ba4205/Desktop/coursera/exdata_data_household_power_consumption/household_power_consumption.txt",sep=';',header = TRUE)
rm(a)
b<-subset(a,a$Date %in% (c('1/2/2007','2/2/2007')))

#remove NA value
submetering1<-as.numeric(b$Global_active_power)
submetering2<-as.numeric(b$Sub_metering_2)
submetering3<-as.numeric(b$Sub_metering_3)

voltage<-as.numeric(b$Voltage)
globalactivepower<-as.numeric(b$Global_active_power)
globalreactivepower<-as.numeric(b$Global_reactive_power)
datetime <- strptime(paste(b$Date, b$Time, sep=" "), "%d/%m/%Y %H:%M:%S") 
#create empty file in working dir
png("plot4.png", width=480, height=480)
par(mfrow = c(2, 2)) #created to set 4 below graphs in one file

plot(datetime,globalactivepower,type="l", xlab="datetime", ylab="global active power")

#create diff plot for voltage
plot(datetime,voltage,type="l", xlab="datetime", ylab="voltage")

#create bar for 3 y and x datetime
plot(datetime,submetering1,type="l", xlab="", ylab="energy sub metering")
lines(datetime, submetering2, type="l", col="red")
lines(datetime, submetering3, type="l", col="blue")
#label
legend("topright", c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"), lty=1, lwd=2.5, col=c("black", "red", "blue"))


plot(datetime,globalreactivepower,type="l", xlab="datetime", ylab="global reactive power")



#save graph and close
dev.off()
