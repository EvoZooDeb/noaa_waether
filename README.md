# noaa_waether
NOAA Weather Data Processing

# Usage:
source('noaa_weather_station_data_processing.R')

ws_data.df <- processWSFile('128300-99999-2019.gz')

# temperatue formatting and rescaling
as.numeric(paste(substr((ws_data.df$air_temp),1,1),as.numeric(substr((ws_data.df$air_temp),2,5)),sep='')) / 10

# Simple Mapping WS
lon <- as.numeric(paste(substr((ws_data.df$lon),1,1),as.numeric(substr((ws_data.df$lon),2,7)),sep='')) / 1000
lat <- as.numeric(paste(substr((ws_data.df$lat),1,1),as.numeric(substr((ws_data.df$lat),2,7)),sep='')) / 1000

# library(rworldmap)
newmap <- getMap(resolution = "low")
plot(newmap, xlim = c(-20, 59), ylim = c(-35, 71), asp = 1)
points(lon, lat, col = "black", bg= "red", cex = 1.2, pch=23)
