Tempwise BG-BT1W BBQ termometro integraciją į Homeassistant per MQTT integraciją. 
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/a37e6533-3d26-472e-9849-3f8e7589b346" />

Duomenų perdavimas iš MQTT į Homeassitant, bei sensoriaus sukūrimas:

mqtt:
  sensor:
    - name: "BG-BT1W Temperatūra"
      state_topic: "home/sensors/temp"
      unit_of_measurement: "°C"
      device_class: temperature
