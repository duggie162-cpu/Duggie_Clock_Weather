# Duggie Desk Clock / Temperature Display v1.0

A simple WiFi‑enabled desk clock and outside temperature display built around an ESP8266 and a 1.9" 128×64 OLED screen. The device syncs time using NTP and fetches current outdoor temperature data from OpenWeatherMap. A single button is used to toggle between **Clock Mode** and **Temperature Mode**.

---

## ✨ Features

* **NTP‑synchronized clock** (auto updates from the internet)
* **12‑hour time format** with AM / PM indicator
* **Outside temperature display** (via OpenWeatherMap API)
* **OLED boot logo** shown on startup
* **Single button UI** to switch display modes
* **Debounced button handling** for reliable input

---

## 🧰 Hardware Requirements

* ESP8266‑based board (NodeMCU, ESP‑12F, etc.)
* 1.9" OLED display (128×64, SSD1306, I2C)
* Momentary push button
* WiFi connection

### Pin Connections

| Function | ESP8266 Pin | Label |
| -------- | ----------- | ----- |
| OLED SDA | GPIO4       | D2    |
| OLED SCL | GPIO5       | D1    |
| Button   | GPIO14      | D5    |

> Button is wired to **GND** and uses the internal pull‑up resistor.

---

## 📦 Required Libraries

Install the following libraries through the Arduino Library Manager:

* ESP8266WiFi
* WiFiUdp
* NTPClient
* ESP8266HTTPClient
* ArduinoJson
* Adafruit GFX Library
* Adafruit SSD1306

---

## 🌐 Configuration

Before uploading, edit the following values in the sketch:

### WiFi Credentials

```cpp
const char* ssid     = "SSID";
const char* password = "Password";
```

### Time Zone

```cpp
const long utcOffsetInSeconds = -5 * 3600; // EST
```

Adjust this value for your local time zone.

### OpenWeatherMap Settings

```cpp
const char* weatherApiKey = "KEY";
const char* city = "City";
const char* countryCode = "Country";
```

* Sign up at **[https://openweathermap.org/](https://openweathermap.org/)** to get a free API key
* Temperature units are set to **Fahrenheit** (`imperial`)

---

## 🖥️ Display Modes

### Clock Mode (Default)

* Shows current time (HH:MM:SS)
* 12‑hour format with AM / PM
* Title banner: `Duggie CLOCK`

### Temperature Mode

* Shows outside temperature in °F
* Updates every **10 minutes**
* Displays `Loading...` until data is received

---

## 🔘 Button Behavior

* **Short press** toggles between Clock and Temperature modes
* Button input is debounced in software

---

## 🚀 Boot Behavior

1. OLED initializes
2. Custom **Duggie Tech boot logo** is displayed for 3 seconds
3. WiFi connection begins
4. Clock display starts immediately

---

## ⚠️ Notes & Limitations

* Requires an active WiFi connection for time and weather updates
* If WiFi is unavailable:

  * Clock will continue running using last known time
  * Temperature data will not update
* Weather data refresh interval: **10 minutes**

---

## 📜 License

**Do whatever you want with it.**

Use it, modify it, break it, improve it, and make it your own.

---

## 👤 Author

**Duggie**
Duggie Tech Projects

---

Happy hacking 🚀
