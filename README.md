## Wi-Fi Cartophrapher

An Android app written in [Kotlin](https://kotlinlang.org) for scanning Wi-Fi networks and capturing BSSID, SSID, capabilities, and signal strength at specific geolocations. The output is a JSON file, with the default name `wifi_map_data.json`, that contains an array of objects that follow this JSON schema.

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "patternProperties": {
    "^[0-9a-fA-F]{2}(:[0-9a-fA-F]{2}){5}$": {
      "type": "object",
      "properties": {
        "capabilities": {
          "type": "string",
          "pattern": "\\[.*\\]"
        },
        "frequency": {
          "type": "integer",
        },
        "lastUpdateTime": {
          "type": "integer",
        },
        "levels": {
          "type": "object",
          "patternProperties": {
            "^\\d{2}\\.\\d+,-?\\d{2}\\.\\d+$": {
              "type": "integer",
              "minimum": -90,
              "maximum": 0
            }
          },
          "additionalProperties": false
        },
        "ssid": {
          "type": "string",
        }
      },
      "required": ["capabilities", "frequency", "lastUpdateTime", "levels", "ssid"],
      "additionalProperties": false
    }
  },
  "additionalProperties": false
}
```

This repository is part of a toolchain. For full context, please see:

🗄️ https://github.com/marianpekar/wifi-map-guide
