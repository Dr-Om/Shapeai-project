# Shapeai-project
import requests
#import os
from datetime import datetime

api_key = '4b6629d6da63592351d5afbd39efce17'
location = input("Enter the city name: ")

complete_api_link = "https://api.openweathermap.org/data/2.5/weather?q="+location+"&appid="+api_key
api_link = requests.get(complete_api_link)
api_data = api_link.json()

#create variables to store and display data
temp_city = ((api_data['main']['temp']) - 273.15)
weather_desc = api_data['weather'][0]['description']
hmdt = api_data['main']['humidity']
wind_spd = api_data['wind']['speed']
date_time = datetime.now().strftime("%d %b %Y | %I:%M:%S %p")

print("-------------------------------------------------------------")
print("Weather Stats for - {}  || {}".format(location.upper(), date_time))
print("--------------------------------------------------------------")

print("Current temperature is: {:.2f} deg C".format(temp_city))
print("Current weather desc  :",weather_desc)
print("Current Humidity      :",hmdt, '%')
print("Current wind speed    :",wind_spd ,'kmph') 
dr=open('word.txt','w+')
dr.write("-------------------------------------------------------------\n")
dr.write("Weather Stats for - {}  || {} \n".format(location.upper(), date_time))
dr.write("--------------------------------------------------------------\n")
dr.write("Current temperature is: {:.2f} deg C\n".format(temp_city))
dr.write("Current weather desc :{} \n".format(weather_desc))
dr.write("Current Humidity   :{} %   \n".format(hmdt))
dr.write("Current wind speed :{} 'kmph'  \n".format(wind_spd ,'kmph'))

dr.close()
