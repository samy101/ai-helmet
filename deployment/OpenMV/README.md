## 🚀 Model Deployment

If you are setting up Nicla Vision with OpenMV IDE for the first time, please follow this guide first:  
[Getting Started with Nicla Vision and OpenMV IDE (Arduino Docs)](https://docs.arduino.cc/tutorials/nicla-vision/getting-started/)  

You may also find this step-by-step lab very helpful (covers Arduino IDE, OpenMV firmware, and Edge Impulse integration):  
[MLSysBook Lab – Nicla Vision Setup with OpenMV & Edge Impulse](https://www.mlsysbook.ai/contents/labs/arduino/nicla_vision/setup/setup.html)

### Steps to Run

1. **Update Wi-Fi credentials**  
   Open `main.py` and set your Wi-Fi details:
   - `SSID` = your Wi-Fi network name  
   - `KEY` = your Wi-Fi password  

2. **Copy model file and MicroPython script to Nicla Vision**  
   Connect the Arduino Nicla Vision over USB and copy the following files to its storage:
   - `main.py`  
   - `trained.tflite`  
   - `labels.txt`  

3. **Connect the buzzer (optional alerting)**  
   - Connect the **buzzer signal** to pin **A0** on the Nicla Vision.  
   - Connect the **other buzzer pin** to **GND**.  
   The buzzer will sound when certain sign boards are detected.

4. **View real-time detections in a browser (debugging)**  
   - Once powered and connected to Wi-Fi, the Nicla Vision starts an MJPEG stream on port `8080`.  
   - Open a browser and visit:  
     `http://<NICLA_IP_ADDRESS>:8080/`  
   - The IP address (e.g., `192.168.243.41`) can be:
     - Found using any standard IP scanner on your network, **or**
     - Read from the **OpenMV IDE serial monitor**, where the script prints the assigned IP after connecting to Wi-Fi.

### Additional Info 

1. The device blinks **blue** when connected to Wi-Fi.  
2. The device blinks **yellow** when another device opens the IP address link to view the camera output.

![Real-Time Detection 2](../../images/real-time-detection3.png)

*Figure 1: Demo showing detection of a “No Parking” sign.*

### 🔁 Additional Models

Two additional TensorFlow Lite models are available in the `models/` directory:

- **Model1.tflite** – Contains **10 classes**, including *place-identification boards*.  
- **Model2.tflite** – Contains **9 classes**, where the *place-identification* sign class is **absent**.

The *place-identification* class was added in `Model1.tflite` to enable future work on **OCR-based reading of text on sign boards**.

By default, the project uses `Model2.tflite` as the active model, stored as `trained.tflite` in the main directory.  
If you want to switch to `Model1.tflite` (or any other model), simply:

1. Copy the desired `.tflite` file into the main directory.  
2. Rename it to `trained.tflite`.

---

**NOTE:**  
On newer firmware versions of OpenMV IDE, some APIs and syntax may have changed. You may need to update parts of the code accordingly (you can refer to the latest machine learning examples in the OpenMV IDE).  
The current code has been tested with **OpenMV IDE v4.1.5**.  
Older releases are available here: https://github.com/openmv/openmv-ide/releases/

**References:**  
1. [Nicla Vision](https://docs.arduino.cc/hardware/nicla-vision/)
2. [Run OpenMV library or firmware (Edge Impulse Docs)](https://docs.edgeimpulse.com/hardware/deployments/run-openmv)  
3. [Nicla Vision Setup with Arduino, OpenMV, and Edge Impulse (MLSysBook Lab)](https://www.mlsysbook.ai/contents/labs/arduino/nicla_vision/setup/setup.html)
