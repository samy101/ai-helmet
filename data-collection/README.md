## 📷 Capturing Images Using Nicla Vision

If you are setting up Nicla Vision with OpenMV IDE for the first time, please follow this guide first:  
[Getting Started with Nicla Vision and OpenMV IDE (Arduino Docs)](https://docs.arduino.cc/tutorials/nicla-vision/getting-started/)  

You may also find this step-by-step lab very helpful (covers Arduino IDE, OpenMV firmware, and Edge Impulse integration):  
[MLSysBook Lab – Nicla Vision Setup with OpenMV & Edge Impulse](https://www.mlsysbook.ai/contents/labs/arduino/nicla_vision/setup/setup.html)

Collecting sign-board images **directly using Nicla Vision** is important for two reasons:

- It captures data from the **same viewpoint and optics** as the final AI Helmet (helmet-like, forward-facing view), which reduces domain shift between training and deployment.  
- It ensures the model sees **real-world lighting, clutter, and distances** similar to what riders will encounter on actual roads.

Nicla Vision has **16 MB of QSPI flash for storage**, which is exposed as a small USB drive when connected to a computer. In our setup (saving compressed 240×240 images), this typically allows storing on the order of **~150–250 images in one session** before the flash fills up, depending on JPEG quality, other files on the device, and exact settings. If you need more images, you can periodically copy them to your computer and clear the storage.

![Pin Diagram](../images/pindiagram.png)

Follow these steps to capture images with Nicla Vision for creating your own dataset:

1. **Wire the push button**  
   - Connect one pin of the button to **A0** on Nicla Vision.  
   - Connect the other pin of the button to **GND**.

2. **Copy the capture script**  
   - Save `main.py` (image-capture script) to the **Nicla Vision** storage.

3. **Set Wi-Fi credentials (optional, for live view)**  
   - Open `main.py` and update:
     - `SSID` = your Wi-Fi network name  
     - `KEY` = your Wi-Fi password  

4. **Capture images**  
   - Power the Nicla Vision (e.g., via USB or power bank).  
   - Press the **push button** to capture an image using the onboard camera.  
   - The **green LED** will turn on briefly to indicate a successful capture.  
   - When later connected to a computer, you may need to press the **reset** button once to refresh and view the stored images.

5. **(Optional) Live camera preview while capturing**  
   - You can use the browser-based MJPEG stream (see the *Deployment* section, Step 4) to **view the camera output in real time** while collecting images.
