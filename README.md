Pidio
=====

A very simple script to use **Raspberry Pi** as a **webradio**. You can use it in two
ways: With a speaker or like a radio transmitter. When used like a radio
transmitter you will need an FM radio to hear the webradio.

Configuration
-------------

The settings are in etc/pidio.json :
```json
{
  "wifi": {
    "name": "...",
    "password": "..."
  },
  "fm": {
    "frequency": 104.2
  },
  "radios": [
    {"name": "RCF", "url": "http://rcf.streamakaci.com/rcf.mp3"},
    {"name": "RCF Anjou", "url": "http://rcf.streamakaci.com/rcf49.mp3"},
    {"name": "Radio Notre Dame", "url": "http://windu.radionotredame.net/RadioNotreDame-Fm.mp3"}
  ]
}
```
 `wifi:` To connect to Wifi network, leave empty otherwise (ethernet).  
 `fm:` To transmit over FM, leave empty if using a speaker.

How it works
------------

**Pidio** is a simple bash script which listen to GPIO and start webradio
according to your settings. It uses *wiringPi* (http://wiringpi.com) to use
GPIOs, *pifm* to transmit over FM (http://icrobotics.co.uk/wiki/index.php/Turning_the_Raspberry_Pi_Into_an_FM_Transmitter)
and *jq* (https://stedolan.github.io/jq/) to read the JSON settings.

GPIO
----

**On/Off switch** must be plugged on the **pin 11**.  
**Next station button** must be plugged on the **pin12**.  
**FM antenna** must be plugged on the **pin 7**.  
