---

# 🕷️ ESP8266 Quadruped Spider Robot - Web Controlled

This is a **quadruped robot** powered by **ESP8266**, controlled via a **web-based interface** using **WebSockets**. The project integrates **12 servos** (3 per leg) and can move **forward, backward, left, and right** using real-time web controls.  

## 🚀 Features
- **Web-Based Control**: Control the robot from a browser (no app needed).  
- **Real-Time Commands**: Uses **WebSockets** for low-latency movement control.  
- **ESP8266 Standalone Server**: The robot connects to a Wi-Fi network and is accessible via its IP.  
- **12 Servo Motors**: Each leg has **3 servos** for precise movements.  
- **Expandable Sensors**: Supports **VL53L1X (LiDAR)** and **MPU6050 (IMU)** for advanced navigation.  

## 📷 Future Upgrades
- **ESP32-CAM Integration**: Add live video streaming to the control interface.  
- **Obstacle Avoidance**: Use LiDAR to detect obstacles.  
- **Balance Control**: Implement IMU-based stability for smoother motion.  

---

## 🛠️ Hardware Components
| Component       | Quantity | Description |
|---------------|----------|------------|
| **ESP8266**  | 1  | Main microcontroller for Wi-Fi control |
| **SG90 Servos** | 12 | 3 per leg for movement |
| **ESP32-CAM** (Future) | 1 | For video streaming |
| **VL53L1X LiDAR** (Future) | 1 | For obstacle detection |
| **MPU6050 IMU** (Future) | 1 | For balance and stability |
| **Battery Pack** | 1 | Power source for servos & ESP |

---

## 🔌 Wiring Diagram (Basic)
```
ESP8266 GPIOs -> 12 Servo Motors
ESP8266 Wi-Fi -> Web Interface
```

---

## 🌐 Web-Based Interface
The **control webpage** is hosted on the ESP8266 itself.  
🖥️ Open a browser and go to:  
```
http://<ESP8266-IP-Address>
```
🔹 **Controls Available**:
- Move **Forward, Backward, Left, Right**
- **Stop** the robot
- Future: Live Camera Stream (ESP32-CAM)

---

## 📜 Installation & Setup
### 1️⃣ Install Required Libraries in Arduino IDE
- **ESPAsyncWebServer** ([Download](https://github.com/me-no-dev/ESPAsyncWebServer))
- **ESPAsyncTCP** ([Download](https://github.com/me-no-dev/ESPAsyncTCP))
- **Servo.h** (Pre-installed in Arduino IDE)

### 2️⃣ Upload the Code
1. Open `quadruped_robot.ino` in **Arduino IDE**.
2. Set **Board**: `NodeMCU 1.0 (ESP8266)`
3. Set **Baud Rate**: `115200`
4. Upload the code to ESP8266.

### 3️⃣ Connect to Wi-Fi
- **Check Serial Monitor** (`115200 baud`) to get the **ESP8266 IP Address**.
- Open a browser and **enter the IP** to access the control panel.

---

## 🖥️ WebSocket-Based Control Code (Example)
```cpp
server.on("/control", HTTP_GET, [](AsyncWebServerRequest *request){
    if(request->hasParam("dir")){
        String direction = request->getParam("dir")->value();
        if(direction == "forward") { moveForward(); }
        else if(direction == "backward") { moveBackward(); }
        else if(direction == "left") { turnLeft(); }
        else if(direction == "right") { turnRight(); }
        else { stopMovement(); }
    }
    request->send(200, "text/plain", "OK");
});
```
> The webpage sends commands like `/control?dir=forward` to **ESP8266**, which then moves the robot.

---

## 🛠️ Troubleshooting
### **1. ESP8266 Not Connecting to Wi-Fi?**
✔ Ensure SSID & password are correct.  
✔ Restart router & ESP8266.  
✔ Check Serial Monitor for errors.  

### **2. Can't Access the Web Interface?**
✔ Get ESP8266's IP from Serial Monitor.  
✔ Ensure mobile/PC is on the same Wi-Fi network.  

### **3. Servo Motors Not Moving?**
✔ Ensure servos are powered correctly.  
✔ Check **GPIO pins** in the code match your wiring.  
✔ Test a single servo using `servo.write()` commands.  

---

## 📜 License
This project is open-source under the **MIT License**. Feel free to modify and contribute!  

---

## 🔥 Future Improvements
- ✅ **ESP32-CAM video streaming** integration  
- ✅ **IMU-based balance & terrain detection**  
- ✅ **Autonomous mode using LiDAR**  
- ✅ **Battery monitoring system**  

---
## 👥 Team Members
- **Raghuvamsy** (Leader,3D Prototype Designer & Software Developer) - [GitHub](https://github.com/Raghuvamsy)
- **Saahit** (Animation & Visualization) - [GitHub](https://github.com/Brainitech)
- **Rajesh** (Software Developer) - [GitHub](https://github.com/Rajesh-kumar23-ctl)
- **Tashfiya** (PPT & Software Developer) - [GitHub](https://github.com/Tashfiya-05)
- **Om Prakash** (Electronics & Hardware) - [GitHub](https://github.com/OM-cypher)
- **Efron**
- **Snehasis** (Software Developer) - [GitHub](https://github.com/omm-2005)


  
---

## 📩 Contribute
🔹 **Found a bug?** Open an [Issue](https://github.com/Raghuvamsy/quadruped-robot-esp8266/issues)  
🔹 **Want to improve?** Submit a Pull Request  

---

🚀 **Project by [Raghuvamsy](https://github.com/Raghuvamsy)& Team** 

🎯 Making robotics **smarter** & **simpler** with ESP8266! 🦾  

---
