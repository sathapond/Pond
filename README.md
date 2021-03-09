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


----------

###**Usability**
ขั้นตอนการใช้งาน
1.	ถอด Micro SD Card ที่ติดอยู่กับตัวอุปกรณ์ออกมา
2.	นำ Micro SD Card ไปเสียบเข้ากับ PC, Note book เพื่ออ่านไฟล์โดยใช้ Card Reader 
3.	ทำการเปิดไฟล์ .csv* เลือกไฟล์ Config ตามความต้องการ โดยในที่นี่เราจะยกตัวอย่างการใช้งานทั้ง 3 รูปแบบ คือ Modbus, Analog และ Digital


###**Config Modbus**

เปิดไฟล์ MODBUS.csv เมื่อเปิดไฟล์เราจะพบหน้าต่าง Config ของการอ่าน Modbus
[![md.png](https://i.postimg.cc/vZ8VY5Z8/md.png)](https://postimg.cc/jL95vwfB) 
หลังจากนั้นให้ผู้ใช้งานกำหนดค่าต่างๆที่ต้องการใช้งาน

การ **Config Modbus** นั้นจะมีส่วนสำคัญที่ต้องรู้ โดยเราจะอธิบายแต่ละส่วน ดังนี้
๏ส่วนของ Header ประกอบไปด้วย

 [![Capture.png](https://i.postimg.cc/c6qSJG36/Capture.png)](https://postimg.cc/8fb3y3tV)

	- บรรทัดที่ 1 สั่งเปิดการใช้งาน on หรือ off พอร์ตการสื่อสาร RS485
	- บรรทัดที่ 2 สั่งใช้งาน on หรือ off เพื่อส่งค่าไปแสดงผลบน Magellan Platform
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

๏**ส่วนที่สอง** นั้นจะเป็นส่วนของ Operator ในส่วนนี้เราจะทำการระบุ Register Address ของอุปกรณ์เพื่ออ่านค่าต่างๆ และสามารถใช้งาน Operator ในการ บวก ลบ คูณ หรือ หาร ค่าที่อ่านมาได้ แล้วยังสามารถตั้งชื่อให้กับค่า Address ที่อ่านมาได้โดยใส่ใน Colum ของ Name

[![Capture2.png](https://i.postimg.cc/GtcPrQjJ/Capture2.png)](https://postimg.cc/jwFn4ymL)

	- บรรทัดที่ 8-17 ใช้ระบุ Register Address ที่ต้องการอ่านค่า สามารถอ่านค่าแอดเดรสได้สูงสุด 10 ค่า แต่ถ้าหากต้องการอ่านเพียงค่าเดียว ให้กำหนด none ในแต่ละบรรทัด 

ในที่นี่จะยกตัวอย่าง Register Address ของ AW5485 เป็นเซนเซอร์วัดอุณหภูมิและความชื้น
[![Capture3.png](https://i.postimg.cc/7LZfxRvL/Capture3.png)](https://postimg.cc/RW2MdXZr)

โดยจะระบุค่า 0x0005 เพื่อทำการอ่านค่า Temperature และใช้งาน Operator ซึ่งจะใช้การกำหนด / เพื่อหารค่า แล้วทำการกำหนดค่า 100 ดังนั้นค่าที่ได้จากการอ่านจะหารด้วย 100  หลังจากนั้นทำการใส่ชื่อโดยที่นี่จะใส่คำว่า Temp และทำการใส่ none ในบรรทัดอื่นที่ไม่ได้ใช้งาน

[![Captur.png](https://i.postimg.cc/XNdrQV9w/Captur.png)](https://postimg.cc/grcc0bSJ)

๏**ส่วนสุดท้าย** ในส่วนนี้จะเป็นการกำหนด Buad Rate และ Serial communication
[![Capture5.png](https://i.postimg.cc/sgTJWXcQ/Capture5.png)](https://postimg.cc/0zJmR9hP)

	- บรรทัดที่ 23 กำหนด Buad Rate
	- บรรทัดที่ 24 เลือกกำหนด Serial Protocol ซึ่งเราจะมีให้เรียกใช้งาน 12 รูปแบบ
**อ่านข้อมูลเพิ่มเติมได้ที่**
https://blog.thaieasyelec.com/espino32-ch7-how-to-use-uart/

4.หลังจากที่กำหนดค่า Config เสร็จแล้วให้ทำการกด Save ไฟล์ โดยการกด Ctrl+S 

5.เมื่อเสร็จแล้วให้นำ Micro SD Card กลับเข้าไปเสียบเข้ากับตัวอุปกรณ์

6.หลังจากนั้นให้ทำการกดปุ่ม Reset 1 ครั้งเพื่อให้อุปกรณ์ทำการอ่านค่า Config จากไฟล์ MODBUS.csv


----------


###**Config Analog**

เปิดไฟล์ ANALOG.csv เมื่อเปิดไฟล์เราจะพบหน้าต่าง Config ของการอ่านค่า Analog
[![analoh.png](https://i.postimg.cc/kX7HCMLN/analoh.png)](https://postimg.cc/MXr5bw6X)
หลังจากนั้นให้ผู้ใช้งานกำหนดค่าต่างๆที่ต้องการใช้งาน

การ **Config Analog** นั้นจะมีส่วนสำคัญที่ต้องรู้ โดยเราจะอธิบายแต่ละส่วน ดังนี้
๏**ส่วนแรก** ประกอบไปด้วย

[![Capture6.png](https://i.postimg.cc/rF47DHXy/Capture6.png)](https://postimg.cc/CzFctmx9)

	- บรรทัดที่ 1, 6, 11, 16  สั่งเปิดปิดการใช้งาน on หรือ off พอร์ตการสื่อสาร Analog
	- บรรทัดที่ 2, 7, 12, 17  ตั้งชื่อให้กับ พอร์ตที่ใช้งาน
	- บรรทัดที่ 3, 8, 13, 18  กำหนดค่า min 
	- บรรทัดที่ 4, 9, 14, 19  กำหนดค่า max 

๏**ส่วนสุดท้าย**

[![Capture7.png](https://i.postimg.cc/nV0y8mKZ/Capture7.png)](https://postimg.cc/w3RfL7bb)

	- บรรทัดที่ 21 สั่งใช้งาน on หรือ off เพื่อส่งค่าไปแสดงผลบน Magellan Platform
หลังจากที่กำหนดค่า Config เสร็จแล้วให้ทำการกด Save ไฟล์

เมื่อเสร็จแล้วให้นำ Micro SD Card กลับเข้าไปเสียบเข้ากับตัวอุปกรณ์

หลังจากนั้นให้ทำการกดปุ่ม Reset 1 ครั้งเพื่อให้อุปกรณ์ทำการอ่านค่า Config จากไฟล์ ANALOG.csv


----------
###**Config Digital I/O**
เปิดไฟล์ DIGITAL.csv เมื่อเปิดไฟล์เราจะพบหน้าต่าง Config ของการควบคุม Digital Inputs และ Digital Output 
[![1.png](https://i.postimg.cc/JzhQvT3c/1.png)](https://postimg.cc/6yDRGfmy)
หลังจากนั้นให้ผู้ใช้งานกำหนดค่าต่างๆที่ต้องการใช้งาน

การ **Config Digital I/O** นั้นจะมีส่วนสำคัญที่ต้องรู้ โดยเราจะอธิบายแต่ละส่วน ดังนี้
๏**ส่วนแรก** ประกอบไปด้วย

[![2.png](https://i.postimg.cc/kMf6z7Tz/2.png)](https://postimg.cc/V50kbPQW)
[![3.png](https://i.postimg.cc/Kjzzxg0V/3.png)](https://postimg.cc/R6k9Tq5Q)
[![4.png](https://i.postimg.cc/pXh8Cgsz/4.png)](https://postimg.cc/kBCBXh3g)
	
	- บรรทัดที่ 3, 7, 11, 15, 19, 23, 27, 31, 35, 39, 43, 47, 51, 55 
	  ในส่วนนี้จะเป็นการ สั่งใช้งานเปิด on หรือ off พอร์ต Digital I/O
	- บรรทัดที่ 4, 8, 12, 16, 20, 24, 28, 32, 36, 40, 44, 48, 52, 56
	  ในส่วนนี้จะเป็นการกำหนดว่าจะให้ พอร์ต Digital เป็น Input หรือ Output
	- บรรทัดที่ 5, 9, 13, 17, 21, 25, 29, 33, 37, 41, 45, 49, 53, 57
	  ในส่วนนี้จะเป็นการกำหนดชื่อให้กับ พอร์ต Digital I/O ซึ่งผู้ใช้กำหนดได้อย่างอิสระ
	
[![6.png](https://i.postimg.cc/L8kVkcsv/6.png)](https://postimg.cc/9DMTCNZq)

	- บรรทัดที่ 59 สั่งเปิดการใช้งาน on หรือ off เพื่อให้ Buzzer ทำงานหรือไม่ทำงาน
	- บรรทัดที่ 60 กำหนดชื่อของ Buzzer ผู้ใช้สามารถเปลี่ยนแปลงได้
	- บรรทัดที่ 62 สั่งเปิดการใช้งาน on หรือ off เพื่อให้ Relay 0 ทำงานหรือไม่ทำงาน
	- บรรทัดที่ 63 กำหนดชื่อของ Relay ผู้ใช้สามารถเปลี่ยนแปลงได้
	- บรรทัดที่ 65 สั่งเปิดการใช้งาน on หรือ off เพื่อให้ Relay 0 ทำงานหรือไม่ทำงาน
	- บรรทัดที่ 63 กำหนดชื่อของ Relay ผู้ใช้สามารถเปลี่ยนแปลงได้
	- บรรทัดที่ 68 สั่งเปิดปิดการใช้งาน on หรือ off การส่งค่าไปแสดงผลบน Magellan Platform
