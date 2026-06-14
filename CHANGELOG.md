# Changelog – GROWCTRL ESP

Die ESPHome-Firmware wird unabhängig von der Integration/den Karten versioniert
(eigene v4-Linie).

## [4.0.0] — Erstveröffentlichung als eigenständiges Repo

- **Relay Board v4** (`relay_board_v4.yaml`) – ESP32, 8 Relais, RS485-Master mit adaptivem
  Addon-System (HYDRO2/TERRA2/POWER4) und MQTT Discovery.
- **Sensor Node v4** (`sensor_node_v4.yaml`) – ESP32-C3, AHT21 + ENS160, TSL2591, 2× DS18B20,
  RS485-Anbindung ans Relay Board.
- `secrets.yaml.example` als Vorlage; echte Zugangsdaten über `secrets.yaml` (gitignored).
- Aus dem GROWCTRL-Monorepo in ein eigenes Repository ausgegliedert.
