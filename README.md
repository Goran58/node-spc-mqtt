# Binding between Vanderbilt/Siemens SPC intrusion system and a MQTT broker

This nodejs module is used to mirror status from Vanderbilt/Siemens SPC intrusion system to a MQTT broker, e.g Mosquitto. 

<b>NOTE!</b> To be able to use this module you also need to have SPC Web Gateway from [Lundix IT](http://forum.lundix.se) installed. SPC Web Gateway is providing a generic open REST and Websocket interface to Vanderbilt/Siemens SPC intrusion system.

### MQTT topics and messages
Default main topic is /SPC and default message format {"update_time": &lt;MILLISECONDS&gt;,"status":&lt;STATUS&gt;}

####/SPC/G_SPC_AREA_MODE_&lt;AREA_ID&gt;
AREA_ID is 1 - Number of defined areas.<br>
Status:
- "unset"
- "partset_a"
- "partset_b"
- "set"
- "unknown"

####/SPC/G_SPC_ZONE_INPUT_&lt;ZONE_ID&gt;
ZONE_ID is 1 - Number of defined zones.<br>
Status:
- "closed"
- "open"
- "short"
- "disconnected"
- "pir_masked"
- "dc_substitution"
- "sensor_missing"
- "offline"
- "unknown"

####/SPC/G_SPC_ZONE_STATUS_&lt;ZONE_ID&gt;
ZONE_ID is 1 - Number of defined zones.<br>
Status:
- "ok"
- "inhibit"
- "isolate"
- "soak"
- "tamper"
- "alarm"
- "trouble"
- "unknown"

### Supported events
Following events are supported:
- Zone closed/open  
- Zone inhibited/de-inhibited  
- Zone isolated/de-isolated  
- Alarm armed/disarmed (Area set, Area partset A/B, Area unset)
- Burglar alarm/restored

More event types can very easy be added to the module.
  
## Installation
      
	git clone https://github.com/Goran58/node-spc-mqtt.git
	cd node-spc-mqtt
	npm install
	
## Configuration

- Modify the settings in config.json according to your environment.

## Start
	./node-spc-mqtt.js
