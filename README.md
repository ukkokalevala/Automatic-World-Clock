Automatic World Clock — Project Description
Overview
The Automatic World Clock is an ESP32-based desktop clock that cycles through major world capitals every 10 seconds, displaying the current local time and date for each city on a compact OLED screen. It combines Wi-Fi connectivity, NTP (Network Time Protocol) synchronization, and a clean multi-region display layout to create a "flip-through-the-world" clock experience.

How It Works
Boot & Connect — On startup, the ESP32 initializes a 128×64 SSD1306 OLED display over I2C and connects to a configured Wi-Fi network.

Time Sync — The device fetches accurate UTC time from pool.ntp.org and applies a per-city GMT offset.

Automatic Cycling — Every 10 seconds, the clock advances to the next capital in a predefined list, briefly flashing the city name before showing its live clock.

Live Display — The screen continuously refreshes, showing the city, country, time, date, and day of the week.

Features
🌍 13 World Capitals — Cape Town, London, Paris, Berlin, Moscow, Dubai, Mumbai, Beijing, Tokyo, Sydney, New York, Los Angeles, and Rio de Janeiro.

🕐 Accurate NTP Time Sync — Each city uses its correct GMT offset (including half-hour zones like Mumbai, GMT+5:30).

🔄 Auto-Flip Every 10 Seconds — Hands-free rotation through all capitals.

📺 Two-Zone OLED Layout — City/country in the top zone, time/date/day in the bottom zone.

📐 Smart Text Centering — Measures actual pixel width and clamps to the screen edge so long city names never get clipped.

📶 Wi-Fi Status Feedback — Serial output and on-screen prompts during connection and sync.

Hardware Requirements
Component	Details
Microcontroller	ESP32 (any dev board)
Display	SSD1306 OLED, 128×64, I2C
Wiring	SCL → GPIO7, SDA → GPIO6
Power	USB 5V
Software Dependencies
Wire.h — I2C communication

Adafruit_GFX.h — Graphics primitives

Adafruit_SSD1306.h — OLED driver

WiFi.h — Network connection

time.h — NTP time functions

Configuration
Before uploading, edit these two lines in the source:

cpp
const char* WIFI_SSID     = "Antonelli";       // Your Wi-Fi name
const char* WIFI_PASSWORD = "maomao1206";      // Your Wi-Fi password
To add or remove cities, simply edit the CAPITALS[] array — each entry takes a name, country, and GMT offset in seconds.

Display Layout
text
┌────────────────────────────┐
│   Cape Town, S. Africa     │  ← Yellow zone (city info)
├────────────────────────────┤
│        14:32:07            │  ← Large time (size 2)
│      ────────────          │
│       11 Oct 2026          │  ← Date
│           Sun              │  ← Day of week
└────────────────────────────┘
Use Cases
Desk ornament / educational gadget for time-zone awareness

IoT starter project for learning Wi-Fi + NTP + OLED integration

Gift for travelers, remote teams, or anyone with international contacts

Possible Extensions
Add a push-button to manually advance cities or pause the rotation

Include weather data via an API (OpenWeatherMap)

Show a small world map icon or flag per country

Sync offsets automatically using configTime with DST awareness

Add a buzzer for hourly chimes

Summary
A compact, self-contained IoT clock that turns a small OLED into a window to the world — no manual time-setting, no buttons, just accurate local times from 13 major cities, rotating automatically every 10 seconds.

# 🌍 Automatic World Clock (ESP32 + OLED)

An ESP32-based desk clock that cycles through 13 world capitals every
10 seconds, displaying the accurate local time and date for each city
on a 128×64 OLED — fully automatic, no buttons required.

## Features
- 13 world capitals with correct GMT offsets (incl. half-hour zones)
- Wi-Fi + NTP time sync via `pool.ntp.org`
- Auto-flip every 10 seconds
- Two-zone OLED layout: city/country on top, time/date/day below
- Smart text centering that prevents clipping on long city names

## Hardware
| Component | Notes |
|-----------|-------|
| ESP32 dev board | Any variant |
| SSD1306 OLED | 128×64, I2C |
| Wiring | **SCL → GPIO7**, **SDA → GPIO6** |

## Dependencies
- Adafruit GFX
- Adafruit SSD1306
- WiFi (built-in)
- time.h (built-in)

## Setup
1. Clone this repo.
2. Open the sketch in the Arduino IDE.
3. Edit your credentials:
   ```cpp
   const char* WIFI_SSID     = "YOUR_WIFI";
   const char* WIFI_PASSWORD = "YOUR_PASSWORD";
