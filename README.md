Automatic World Clock — Project Description
Overview
The Automatic World Clock is an ESP32-based desktop clock that cycles through major world capitals every 10 seconds, displaying the current local time and date for each city on a compact OLED screen. It combines Wi-Fi connectivity, NTP (Network Time Protocol) synchronization, and a clean multi-region display layout to create a "flip-through-the-world" clock experience.

How It Works
Boot & Connect — On startup, the ESP32 initializes a 128×64 SSD1306 OLED display over I2C and connects to a configured Wi-Fi network.

Time Sync — The device fetches accurate UTC time from pool.ntp.org and applies a per-city GMT offset.

Automatic Cycling — Every 10 seconds, the clock advances to the next capital in a predefined list, briefly flashing the city name before showing its live clock.

Live Display — The screen continuously refreshes, showing the city, country, time, date, and day of the week.

Features
13 World Capitals — Cape Town, London, Paris, Berlin, Moscow, Dubai, Mumbai, Beijing, Tokyo, Sydney, New York, Los Angeles, and Rio de Janeiro.

Accurate NTP Time Sync — Each city uses its correct GMT offset (including half-hour zones like Mumbai, GMT+5:30).

Auto-Flip Every 10 Seconds — Hands-free rotation through all capitals.

Two-Zone OLED Layout — City/country in the top zone, time/date/day in the bottom zone.

Smart Text Centering — Measures actual pixel width and clamps to the screen edge so long city names never get clipped.

Wi-Fi Status Feedback — Serial output and on-screen prompts during connection and sync.

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

const char* WIFI_SSID     = "YOUR_SSID";       // Your Wi-Fi name
const char* WIFI_PASSWORD = "YOUR_PASSWORD";      // Your Wi-Fi password
To add or remove cities, simply edit the CAPITALS[] array — each entry takes a name, country, and GMT offset in seconds.

