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

การ **Config Modbus** นั้นจะมีส่วนสำคัญที่ต้องรู้ โดยเราจะอธิบายแต่ละส่วน ดังนี้
 ส่วนของ Header ประกอบไปด้วย
 [![Capture.png](https://i.postimg.cc/c6qSJG36/Capture.png)](https://postimg.cc/8fb3y3tV)

	- บรรทัดที่ 1 สั่ง On หรือ Off พอร์ตการสื่อสาร RS485
	- บรรทัดที่ 2 สั่ง On หรือ Off การส่งค่าไปแสดงผลบน Magellan Platform
	- บรรทัดที่ 3 ในส่วนนี้แต่ละเฟรมร้องขอจะบรรจุหมายเลขฟังก์ชั่นที่นิยามลักษณะการทำงานที่ถูกต้องการให้สแลฟดำเนินการ ความหมายของฟิลด์ข้อมูลขึ้นอยู่กับหมายเลขหรือชนิดฟังก์ชั่นที่ใช้ การร้องขอในบางครั้งอาจเรียกอีกอย่างว่า คิวรี (Query) ซึ่งเป็นศัพท์ทางเทคนิคที่ใช้กันมากในระบบฐานข้อมูล

> - FC 01 สำหรับ read Coil แสดงสถานะของ Digital Output
(0 = OFF, 1 = ON) ฟังก์ชั่นนี้อนุญาตให้มาสเตอร์สามารถดึงสถานะ ON/OFF ของคอยล์ในตัวสแลฟซึ่งปกติแล้วจะใช้บอกสถานะการคอนโทรลของสแลฟว่าควบคุมอะไรอย่างไรในขณะนั้น 
> - FC 02 สำหรับการ read Discrete input แสดงสถานะของ Digital Input
(0 = OFF, 1 = ON) ฟังก์ชั่นนี้ทำให้มาสเตอร์สามารถอ่านค่าอินพุตแบบดิสครีต (Discrete Input) หรือดิจิตอลอินพุตในอุปกรณ์สแลฟ ฟิลด์ข้อมูลของเฟรมร้องขอจะประกอบด้วยหมายเลขแอดเดรสของอินพุตแรกตามด้วยจำนวนดิจิตอลอินพุตที่ต้องการอ่าน 
> - FC 03 สำหรับ read Holding register แสดงค่าของ Analog Output ฟังก์ชั่นนี้ทำให้มาสเตอร์สามารถดึงค่าในรีจิสเตอร์ของสแลฟได้ โดยทั่วไปคือค่าเซตติ้งหรือพารามิเตอร์ของอุปกรณ์นั้น ๆ
> - FC 04 สำหรับการ read Input register แสดงค่าของ Analog Input ฟังก์ชั่นนี้อนุญาตให้มาสเตอร์ สามารถอ่านค่าอินพุตรีจิสเตอร์จากหลาย ๆ รีจิสเตอร์ในอุปกรณ์สแลฟ โดยทั่วไปอินพุตรีจิสเตอร์จะมีไว้เก็บค่าวัดอะนาลอก

**อ่านข้อมูลเพิ่มเติมได้ที่**
http://www.wisco.co.th/main/articles/Modbus
http://www.thailandindustry.com/indust_newweb/articles_preview.php?cid=10995

	- บรรทัดที่ 4 Address ของอุปกรณ์ Slave แต่ละตัวที่ได้รับการกำหนดอยู่ Address ในช่วง 1–247 เมื่อ Slave มีส่งการตอบสนองของมัน Address ของตัวมันเองจะอยู่ในขอบเขต Address Field ของการตอบสนองเพื่อให้อุปกรณ์ Master ทราบว่าอุปกรณ์ Slave กำลังตอบสนองอยู่
