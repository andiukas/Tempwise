# Tempwise BG-BT1W BBQ termometro integracija į Home Assistant per MQTT

![BG-BT1W](https://github.com/user-attachments/assets/a37e6533-3d26-472e-9849-3f8e7589b346)

Šiame projekte parodyta, kaip **Tempwise BG-BT1W** Bluetooth termometro duomenis perduoti į **Home Assistant** naudojant **MQTT** brokerį.

---

## Duomenų srautas
1. **Termometras** → Bluetooth → **Python/MQTT skriptas** (publikuoja duomenis į brokerį)  
2. **MQTT brokeris** → Home Assistant (per MQTT integraciją)  
3. **Home Assistant** → sukuria sensorių ir atvaizduoja temperatūrą

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

## Parametrų paaiškinimas
name – sensoriaus pavadinimas, rodomas Home Assistant
state_topic – MQTT temos adresas, į kurį publikuojami duomenys (pvz. home/sensors/temp)
unit_of_measurement – matavimo vienetai (°C)
device_class – nurodo, kad tai temperatūros sensorius

