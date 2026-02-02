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

For flashing use the ESP32S3 example project from ESP-IDF. The tusb_ncm & tusb_serial_device. Purpose of tusb_ncm is that your computer will see the board as USB ethernet class. And the purpose of tusb_serial_device is to check logs during development if the wifi is working or not.

<img width="332" height="343" alt="Screenshot 2026-02-02 000309" src="https://github.com/user-attachments/assets/0813824e-efea-4bc4-9a0b-641cec28f340" />

After that the board will work like this 

1. USB Ethernet device (what the PC sees)

2. Wi-Fi STA (ESP connects to Wi-Fi)

3. NAT (ESP routes traffic USB ↔ Wi-Fi)


Last piece 

Copy the main.c file from the repo ( I am not still sure that It shows error or not. I can confirm after getting the board.) and replace it with the existing one. 

Now build the firmware from your IDF and flash it to the board (use the USB to UART usb-c port). Hopefully if you connect it to your computer it should work.
