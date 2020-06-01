DS18B20 Temperature to mqtt for Raspberry Pi
=============================

Reads the the temperature of DS18B20 sensors and sends it to a mqtt broker.


Installation:
-------------------

    pip install rpi-temperature-mqtt

Configuration:
-------------------

Needs a json configuration file as follows (don't forget to change ip and credentials ;-)):


.. code:: json

    {
        "mqtt_client_id": "power_meter",
        "mqtt_host": "192.168.0.210",
        "mqtt_port": "1883",
        "sources": [
            {
              "serial": "10-0008031e4d9e",
              "topic": "tele/ServerRoom/rack0_front_bottom",
              "device": "rack0_lower_front"
            },
            {
             "serial": "10-0008031e804b",
             "topic": "tele/ServerRoom/rack0_front_bottom",
             "device": "rack0_upper_front"            },
            {
              "serial": "10-0008031eaac7",
             "topic": "tele/ServerRoom/rack0_front_bottom",
              "device": "rack0_upper_rear"            }
          ]
    }


Optional json variables:
-------------------

Wait before query all sensors again (defaults to 300)
    
    "wait_update": "60",
    
Wait between sensor reads (defaults to 5)
    
    "wait_process": "3",
    
In case your mqtt has user and passwd
    
    "mqtt_user": "username",
    
    "mqtt_password": "password",

You may enable verbose mode to catch issues, also enable for systemd 

    "verbose": "true",


Start:
-------------------

    rpi-temperature-mqtt config.json
