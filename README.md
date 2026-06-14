<div align="center">

<img src="assets/growctrl_logo.png" alt="GROWCTRL Logo" width="160">

# 🌱 GROWCTRL ESP

**ESPHome-Firmware für die GROWCTRL-Hardware** – die Geräteebene unter der
[GROWCTRL-Integration](https://github.com/MrDarkvoid/growctrl) für Home Assistant.

![Lizenz](https://img.shields.io/badge/Lizenz-GC--SAL%201.0-7BE8A8)
![ESPHome](https://img.shields.io/badge/ESPHome-ESP32-41BDF5)
![Version](https://img.shields.io/badge/Version-4.0.0-7BE8A8)

*MrDarkvoid – entwickelt in Zusammenarbeit mit Claude (Anthropic), Vibe Coding*

</div>

---

## Was ist das?

Diese Firmware macht die **eigentliche Gerätesteuerung**: Relais schalten, Sensoren lesen,
RS485-Addons anbinden. Home Assistant (mit der GROWCTRL-Integration) ist die **Aufsichts- und
Konfigurationsschicht** darüber – die Steuerlogik wird **nicht doppelt** gehalten.

> Diese Hardware ist **optional**. GROWCTRL läuft auch mit beliebigen anderen HA-Schaltern
> (z. B. Zigbee-Steckdosen). Wer die GROWCTRL-Boards nutzt, bekommt mit dieser Firmware die
> passende ESPHome-Basis.

## Inhalt

| Datei | Gerät | Funktion |
|-------|-------|----------|
| `relay_board_v4.yaml` | **Relay Board v4** – ESP32 (esp32dev) | 8 Relais (Licht, Heizung, CO₂-Ventil, Pumpe, Lüfter, 3× Reserve). RS485-Master für bis zu 3 Addons (HYDRO2/TERRA2/POWER4) mit HELLO/ACK/ADATA-Protokoll. Publiziert MQTT Discovery. |
| `sensor_node_v4.yaml` | **Sensor Node v4** – ESP32-C3 Mini | AHT21 + ENS160 (Temp/rF/CO₂/TVOC), TSL2591 (Lux), 2× DS18B20 (1-Wire), RS485-Anbindung ans Relay Board. |
| `secrets.yaml.example` | – | Vorlage für die Zugangsdaten (kopieren nach `secrets.yaml`). |

## Einrichtung

1. **ESPHome** installieren (Add-on in HA oder `pip install esphome`).
2. `secrets.yaml.example` nach **`secrets.yaml`** kopieren und echte Werte eintragen
   (WLAN, API-Key, OTA, MQTT). `secrets.yaml` ist via `.gitignore` ausgeschlossen.
3. Flashen:
   ```bash
   esphome run relay_board_v4.yaml
   esphome run sensor_node_v4.yaml
   ```
4. Die Geräte erscheinen in Home Assistant (API/MQTT Discovery). Danach in der
   **GROWCTRL-Integration** die jeweiligen Schalter/Sensoren den Stationen/Zelten zuordnen.

## Sicherheit

Diese Firmware schaltet **Netzspannung** (Relais für Licht, Heizung, Pumpen). Für korrekte
Verdrahtung, Absicherung (FI/LS, geeignete Relais/Schütze) und Aufsicht bist allein **du**
verantwortlich. Bereitstellung ohne Gewähr – siehe [`LICENSE`](LICENSE).

## Lizenz

GROWCTRL Source-Available License (GC-SAL) 1.0 – siehe [`LICENSE`](LICENSE).
Privat & nicht-kommerziell frei mit Namensnennung „MrDarkvoid"; kommerzielle Nutzung,
Re-Hosting und modifizierte Veröffentlichungen nur mit schriftlicher Zustimmung.

<div align="center">

*🌱 GROWCTRL ESP · GC-SAL 1.0 · MrDarkvoid*

</div>
