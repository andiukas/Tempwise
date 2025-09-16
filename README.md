# Tempwise BG-BT1W BBQ termometro integracija į Home Assistant per MQTT

![BG-BT1W](https://github.com/user-attachments/assets/a37e6533-3d26-472e-9849-3f8e7589b346)

Šiame projekte parodyta, kaip **Tempwise BG-BT1W** Bluetooth termometro duomenis perduoti į **Home Assistant** naudojant **MQTT** brokerį.

---

## Python scriptas
1. **Skripto failo sukūrimas terminale** → nano /root/bg_bt1w.py
2. **Pateikto skripto išsaugojimas** → CTRL+O, ENTER, CTRL+X
3. **Python skripto paleidimas terminale** → python3 /root/bg_bt1w.py

**Jei viskas gerai, terminale pamatysi:**


✅ Prisijungta prie įrenginio!  
✅ MQTT prisijungta sėkmingai  

🌡️ Temperatūra: 0.29 °C  
🌡️ Temperatūra: 0.29 °C  
🌡️ Temperatūra: 0.29 °C  



## Duomenų srautas
1. **Termometras** → Bluetooth → **Python/MQTT skriptas** (publikuoja duomenis į brokerį)  
2. **MQTT brokeris** → Home Assistant (per MQTT integraciją)  
3. **Home Assistant** → Sukuria sensorių ir atvaizduoja temperatūrą

---

## Home Assistant konfigūracija

Į `configuration.yaml` pridėkite MQTT sensoriaus aprašą:

```yaml
mqtt:
  sensor:
    - name: "BG-BT1W Temperatūra"
      state_topic: "home/sensors/temp"
      unit_of_measurement: "°C"
      device_class: temperature
      value_template: "{{ (value | float * 100) | round(0) }}"


## Parametrų paaiškinimas
name – sensoriaus pavadinimas, rodomas Home Assistant
state_topic – MQTT temos adresas, į kurį publikuojami duomenys (pvz. home/sensors/temp)
unit_of_measurement – matavimo vienetai (°C)
device_class – nurodo, kad tai temperatūros sensorius
value_template - reikšmę sensoriaus padauginta iš 100

