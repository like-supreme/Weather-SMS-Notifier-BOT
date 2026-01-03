# Weather-SMS-Notifier-BOT
A Python automation bot that checks the upcoming weather forecast using OpenWeatherMap and sends an SMS reminder via Twilio if rain is expected in the next hours


# ☔ Rain Alert SMS Bot (OpenWeatherMap + Twilio)

A simple Python automation project that checks the short-term weather forecast using the **OpenWeatherMap Forecast API** and sends you an **SMS alert via Twilio** if rain is expected.

---

## 🚀 Features

- Fetches forecast data from OpenWeatherMap (5-day / 3-hour forecast)
- Checks the next few forecast entries (configurable)
- Detects rain conditions using weather condition codes
- Sends an SMS reminder using Twilio
- Supports proxy environments (useful for restricted networks)

---

## 🧠 How It Works

1. Call OpenWeatherMap forecast endpoint with latitude/longitude
2. Read weather condition codes from the returned forecast list
3. If any condition code < 700 (rain/snow/etc.), set `will_rain = True`
4. If `will_rain`:
   - Initialize Twilio client (optionally with proxy)
   - Send an SMS reminder: "Bring an umbrella ☔️"

---

## 🛠 Tech Stack

- Python
- Requests
- OpenWeatherMap API
- Twilio API (SMS)
- Optional proxy support using `TwilioHttpClient`

---

## 📦 Installation

1. Clone the repository:
   git clone https://github.com/your-username/rain-alert-sms-bot.git
   cd rain-alert-sms-bot

 pip install requests twilio  

🔐 Environment Variables

Create environment variables before running:

Required

OWM_API_KEY → OpenWeatherMap API key

TWILIO_AUTH_TOKEN → Twilio Auth Token

TWILIO_ACCOUNT_SID → Twilio Account SID

TWILIO_FROM_NUMBER → Your Twilio number (e.g. +1XXXXXXXXXX)

TWILIO_TO_NUMBER → Your verified phone number (e.g. +90XXXXXXXXXX)

Optional

HTTPS_PROXY → if you're behind a proxy (school/company network)

Example (Linux/macOS):

export OWM_API_KEY="your_key"
export TWILIO_ACCOUNT_SID="ACxxxxxxxxxxxxxxxxxxxxx"
export TWILIO_AUTH_TOKEN="xxxxxxxxxxxxxxxxxxxxx"
export TWILIO_FROM_NUMBER="+1xxxxxxxxxx"
export TWILIO_TO_NUMBER="+90xxxxxxxxxx"


Windows PowerShell:

setx OWM_API_KEY "your_key"
setx TWILIO_ACCOUNT_SID "ACxxxxxxxxxxxxxxxxxxxxx"
setx TWILIO_AUTH_TOKEN "xxxxxxxxxxxxxxxxxxxxx"
setx TWILIO_FROM_NUMBER "+1xxxxxxxxxx"
setx TWILIO_TO_NUMBER "+90xxxxxxxxxx"

⚙️ Configuration

Change forecast location by editing latitude/longitude:

weather_params = {
  "lat": 46.947975,
  "lon": 7.447447,
  "cnt": 4
}


cnt=4 checks the next 4 forecast entries (~12 hours ahead)

▶️ Run
python main.py


If rain is expected, you will receive an SMS.

⚠️ Notes

OpenWeatherMap forecast uses 3-hour intervals.

Twilio trial accounts can only send messages to verified numbers.

For some regions (e.g., Turkey), Twilio may require enabling SMS Geo Permissions.

🔮 Improvements (Ideas)

Schedule script to run every morning (cron / Task Scheduler)

Add temperature / wind threshold alerts

Support multiple cities and multiple recipients

Send WhatsApp notifications as an alternative



