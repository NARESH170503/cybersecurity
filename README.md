import requests
from datetime import datetime
api_key='87d845b0b6cf29baa1a73cc34b067a95'
location=input("ENTER THE CITY NAME:")
complete_api_link="https://api.openweathermap.org/data/2.5/weather?q="+location+"&appid="+api_key
api_link=requests.get(complete_api_link)
api_data=api.link.json()
temp_city=((api_data['main']['temp'])-273.15)
weather_desc=api_data['weather'][0]['description']
hmdt=api_data['main']['humidity']
wind_spd=api_data['wind']['speed']
date_time=datetime.now().strftime("%d %b %Y|%I:%M:%S %p")
print("------------------------------------------------")
print("weather stats for -{} ||{}".format(location.upper(),date_time))
print("current temperature is:{:.2f}deg C".format(temp_city))
print("CURRENT WEATHER DESC :",weather_desc)
print("CURRENT HUMIDITY :",hmdt,'%')
print("CURRENT WIND SPEED :",wind_spd,'kmph')
print("======================================")
txtlist=[temp_city,weather_desc,hmdt,wind_spd,date_time]
with open("textfile.txt", mode='w',encoding='utf-8') as f :
    f.write("---------------------------------------------/n")
    f.write("weather stats for - {} || {}".format(location.upper(),date_time))
    f.write("/n---------------------------------------------/n")
    f.write("CURRENT TEMPERATURE IS:{:.2f}deg C/n".format(txtlist[0]))
    f.write("{},{} /n".format("current weather desc :",txtlist[1]))
    f.write("{},{}.{} /n".format("CURRENT HUMIDITY :",txtlist[2],"%"))
    f.write("{},{},{} /n".format("CURRENT WIND SPEED :",txtlist[3],"kmph"))
    f.write("======================================================")
