# Jadu 

a ESP32-S3-WROOM-1U-N8R2 based micro-controller board. Primary purpose of the board was to use it as a wifi adapter in public event & for fimware uploading projects that I want to do. Such as make the esp32s3 act like as a SWD probe, firmware implementation on SWD protocol, Basic DP/AP access, Flash algorithm for nRF52. By this ESP32 will be enabled to talk to host over USB CDC & custom protocol. 


## Design 

Basically the DEVKIT design in smaller size. 

<img width="917" height="672" alt="Screenshot 2026-01-31 233028" src="https://github.com/user-attachments/assets/77ad9e6a-1e20-4685-89dd-b19b6ffac092" />

<img width="234" height="458" alt="Screenshot 2026-02-02 143637" src="https://github.com/user-attachments/assets/d0bc2d25-368e-435a-8e8e-324c1e44c3f6" />

<img width="287" height="462" alt="Screenshot 2026-02-02 143650" src="https://github.com/user-attachments/assets/2da926ba-0808-4562-b59b-08ac7a7161ae" />

<img width="682" height="605" alt="Screenshot 2026-02-02 143704" src="https://github.com/user-attachments/assets/3420ad13-2700-4562-9f2d-7cb84495e9b2" />

<img width="686" height="437" alt="Screenshot 2026-02-02 143713" src="https://github.com/user-attachments/assets/53777f97-b06b-4c16-b0d0-2794a00309f1" />


## Firmware 

For flashing use the ESP32S3 example project from ESP-IDF. The tusb_ncm. Purpose of tusb_ncm is that your computer will see the board as USB etthernet class. But there are some changes that you need to do.

<img width="332" height="343" alt="Screenshot 2026-02-02 000309" src="https://github.com/user-attachments/assets/0813824e-efea-4bc4-9a0b-641cec28f340" />

You have go to your projects SDK editor

<img width="1432" height="899" alt="image" src="https://github.com/user-attachments/assets/2ee0663e-8dc7-48af-a954-4c3209d63b24" />

You have to enable the tiny usb CDC feature because I want to work with serial devices. 

<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/0ed738e6-0471-4b91-87ad-fa93f1d9acdf" />

Then you have to select the tiny-usb network device _ ncm. It is the fastest and work with cross platform.

<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/dcfe75be-1d30-4e22-984a-93ef84a95457" />

Change the console routing because you want to flash the firmware with usb-c.

<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/0e415b43-b2f5-43fe-8f22-b7e6fc41964a" />

Disable the serial JTAG support. Otherwise it will clash with your output cause they use the same usb controller and fights with tiny usb.

<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/fb5ec8bb-9c26-4151-a5e0-a57516a34b89" />


After that the board will work like this 

PC  <—USB NCM—>  ESP32-S3  <—Wi-Fi STA—>  Router/AP

ESP will assume This PC is just another client on my Wi-Fi network.


After that just go to the ESP-IDF explorer. Click on the Full clean first and then click on build project. It will build the project for you.

<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/a1d11e7d-ec49-4ec4-986e-041623cc4a1f" />

Then connect the board to you computer and the device should pop up down below. Once you see the board and click on flash the firmware. YOu are done. Now you have a usb wifi adapter.
