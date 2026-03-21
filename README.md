# KUCUR (Kontrol Ultracerdas Curah dan Rembes)
**IoT-Based Smart Irrigation System with Real-Time Monitoring and Automation**

KUCUR is a comprehensive IoT smart irrigation system designed to monitor soil conditions and automate watering schedules. The system provides real-time monitoring, intelligent automation, remote control via a Web Dashboard, Telegram Bot integration, and a dedicated Chatbot for user interaction.

## 🚀 Features

- **Real-Time Monitoring**: Monitor sensor data and pump status in real-time via MQTT protocol.
- **Smart Automation & Scheduling**: Set up rule-based automation or time-based watering schedules.
- **Web-Based Dashboard**: A responsive user interface to control and monitor the entire irrigation system.
- **Telegram Bot Integration**: Receive alerts and control the irrigation system directly from Telegram.
- **AI/Chatbot Assistant**: Built-in chatbot interface to interact with the system easily.
- **Irrigation History**: Logs all watering activities and sensor metrics for historical analysis.
- **IoT Simulator**: Built-in simulator (`iot-simulator.js`) to test the backend and UI without requiring physical hardware.

## 🛠️ Technology Stack

- **IoT Hardware**: ESP8266 / ESP32 (C++ / Arduino IDE)
- **Backend**: Node.js, Express.js
- **Communication Protocol**: MQTT (Message Queuing Telemetry Transport)
- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Integrations**: Telegram Bot API

## 📂 Project Structure

```text
KUCUR/
├── backend/                # Node.js server API, MQTT client, and Bot
│   ├── src/
│   │   ├── controllers/    # API business logic
│   │   ├── database/       # Database configuration (db.js)
│   │   ├── models/         # Database models (IrrigationHistory.js)
│   │   ├── routes/         # Express routes (auth, schedule, chat, etc.)
│   │   ├── server.js       # Main entry point for the backend
│   │   ├── mqttClient.js   # MQTT connection handler
│   │   ├── telegram-bot.js # Telegram bot logic
│   │   └── iot-simulator.js# Hardware simulator for testing
├── web-ui/                 # Frontend Web Dashboard
│   ├── css/, js/           # Styling and frontend logic
│   ├── index.html          # Login / Landing page
│   ├── dashboard.html      # Main monitoring dashboard
│   ├── automation.html     # Scheduling and automation settings
│   ├── chatbot.html        # Smart assistant interface
│   └── history.html        # Irrigation data logs
└── EspClient/              # Microcontroller source code
    └── EspClient.ino       # ESP8266/ESP32 sketch for MQTT and sensors
```

## ⚙️ Setup & Installation

### 1. Backend Setup
1. Navigate to the backend directory:
   ```bash
   cd backend/src
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Configure environment variables:
   Copy `.env.example` to `.env` and fill in your configuration details (MQTT Broker, Telegram Token, Database URI, etc.).
   ```bash
   cp .env.example .env
   ```
4. Start the server:
   ```bash
   npm start
   # or run "node server.js"
   ```

### 2. Frontend Setup
The frontend uses standard web technologies. You can serve the `web-ui` directory using any web server (e.g., VS Code Live Server, Nginx, or a simple Python server).
```bash
cd web-ui
python3 -m http.server 8080
```
Access the dashboard via `http://localhost:8080`.

### 3. IoT Hardware Setup
1. Open `EspClient/EspClient.ino` using the Arduino IDE.
2. Install the necessary libraries (e.g., PubSubClient for MQTT, WiFi/ESP8266WiFi).
3. Update the WiFi credentials and MQTT Broker details in the `.ino` file.
4. Flash the code to your ESP8266 or ESP32 board.

### 4. Running the Simulator (Optional)
If you don't have the hardware ready, you can test the system using the built-in IoT Simulator:
```bash
cd backend/src
node simulator-cli.js
```

## 📡 MQTT Topics Architecture
*(Adjust the topics below based on your actual `mqttClient.js` and `EspClient.ino` configuration)*
- `kucur/sensor/data` - Publishes soil moisture, temperature, etc.
- `kucur/pump/status` - Publishes the current state of the water pump.
- `kucur/pump/control` - Subscribed by the ESP to trigger the pump manually.

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page if you want to contribute.

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.