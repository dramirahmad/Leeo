# Leeo

A smartthings device type for the Leeo smart alert. Utilizing the triggers from IFTTT, this device type will <p> 

          Update with Leeo's temp/humidity readings 
          Control the color of the actual Leeo device
          Function as a Smoke Detector/CO Sensor/Water Sensor

Commands:

          Send command "siren" for Carbon Monoxide
          Send command "strobe" for Smoke
          Send command "siren and strobe" for Water.
          Send command "lock" to clear Smoke alarm
          Send command "unlock" to clear CO. 

To receive Temperature and humidty values, as well as controlling the Leeo's color, CoRe pistons/IFTTT Recipe's must be setup. 

Temp/Humidity Piston
          
          Define a dynamic value for temp, and another for humidity, each with a value that is left blank.
          Define a condtion for a virtual device, which would be IFTTT, executing, with a value you decide.
          Copy the URL provided and save for later.
          Define a "then" action, using Location, to set variable. 
          Select either temp or humidity from the variable dropdown.
          For that variable's value, enter either {$args.temp} or {$args.humidity}
          Add a new statement, an action, using this deivce.
          Add a new task; either updateTemperature or updateHumidity.
          Select parameters, and add a string parameter. Choose variable. Select the corresponding variable.
          Repeat process for the other variable. 

IFTTT Recipe
          
          Configure a trigger for new sensor readings.
          Configure action to make a web request. 
          Use URL provided from CoRe for the action. 
          Metohd: Post. Content: json
          In the body of the request, add {"humidity":{{HumidityValue}}} or {"temp":{{TemperatureValue}}} 
          Create another recipe for the other variable. 
          
To control Leeo's color
          
          Create an IFTTT recipe, with a webhook trigger. Your event name will be used in the code of this DTH.
          For "which value" add an ingredient, Value 1. 
          Find the URL at line 185. 
          Enter your event name and Maker Channel Key where appropriate. 
          
