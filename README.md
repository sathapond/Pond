**DEVIO AIS NB-IoT  Smart controller kit**
===================


เป็นอุปกรณ์อุตสาหกรรมที่ให้การเชื่อมต่อที่เชื่อถือได้และปลอดภัยสำหรับพอร์ตอนุกรม (RS485) ตาม IoT อุตสาหกรรม, การอ่านค่าเซนเซอร์ Analogs, RS485 การควบคุม I/O เพื่อสั่งใช้งานอุปกรณ์เช่น Relay, Buzzer, LED


อุปกรณ์อุตสาหกรรม **DEVIO AIS NB-IoT Smart controller kit**  รองรับการส่งข้อมูลแบบโปร่งใสช่วยให้คุณถ่าย


เปรียบได้ว่าเป็นเครื่องมือกำหนดค่าที่มีประสิทธิภาพใช้งานง่ายและสะดวกสำหรับการกำหนดค่าตั้งค่า

###**Diagram**
[![controller.jpg](https://i.postimg.cc/d33FxSVT/controller.jpg)](https://postimg.cc/Ppg0LyZt)

----------
**Specifications**
-------------
###**Tables**
              
Item  | DEVIO AIS NB-IoT Smart Controller kit
------------- | -------------
**Serial Interface**  |
Ports  | 1-RS485   
**Digital I/O** |
Digital I/O  | 13-Digital I/O   
**Analog Inputs** |
Analog Inputs  | 4-Inputs  
**External Storage**  | 
SD (Optional) | 1 x Micro SD interface, Up to 32G
**Software**|
Management| Magellan Platform
**Others** |
Reset Button | 1
LED Indicator | 1 
Built-in | RTC, Relay, Buzzer

###**Usability**
ขั้นตอนการใช้งาน
1.	ถอด Micro SD Card ที่ติดอยู่กับตัวอุปกรณ์ออกมา
2.	นำ Micro SD Card ไปเสียบเข้ากับ PC, Note book เพื่ออ่านไฟล์โดยใช้ Card Reader 
3.	ทำการเปิดไฟล์ .csv* เลือกไฟล์ Config ตามความต้องการ โดยในที่นี่เราจะยกตัวอย่างการใช้งานทั้ง 3 รูปแบบ คือ Modbus, Analog และ Digital
3.1 Config Modbus
เปิดไฟล์ MODBUS.csv เมื่อเปิดไฟล์เราจะพบหน้าต่าง Config ของการอ่าน Modbus
[![md.png](https://i.postimg.cc/vZ8VY5Z8/md.png)](https://postimg.cc/jL95vwfB) 
หลังจากนั้นให้ผู้ใช้งานกำหนดค่าต่างๆที่ต้องการใช้งาน

หลังจากที่กำหนดค่า Config เสร็จแล้วให้ทำการกด Save ไฟล์

เมื่อเสร็จแล้วให้นำ Micro SD Card กลับเข้าไปเสียบเข้ากับตัวอุปกรณ์

หลังจากนั้นให้ทำการกดปุ่ม Reset 1 ครั้งเพื่อให้อุปกรณ์ทำการอ่านค่า Config จากไฟล์ MODBUS.csv

3.2 Config Analog
เปิดไฟล์ ANALOG.csv เมื่อเปิดไฟล์เราจะพบหน้าต่าง Config ของการอ่านค่า Analog
[![analoh.png](https://i.postimg.cc/kX7HCMLN/analoh.png)](https://postimg.cc/MXr5bw6X)
หลังจากนั้นให้ผู้ใช้งานกำหนดค่าต่างๆที่ต้องการใช้งาน

หลังจากที่กำหนดค่า Config เสร็จแล้วให้ทำการกด Save ไฟล์

เมื่อเสร็จแล้วให้นำ Micro SD Card กลับเข้าไปเสียบเข้ากับตัวอุปกรณ์

หลังจากนั้นให้ทำการกดปุ่ม Reset 1 ครั้งเพื่อให้อุปกรณ์ทำการอ่านค่า Config จากไฟล์ ANALOG.csv
