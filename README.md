**DEVIO AIS NB-IoT  Smart controller kit**
===================


เป็นอุปกรณ์อุตสาหกรรมที่ให้การเชื่อมต่อที่เชื่อถือได้และปลอดภัยสำหรับพอร์ตอนุกรม (RS485) ตาม IoT อุตสาหกรรม, การอ่านค่าเซนเซอร์ Analogs, RS485 การควบคุม I/O เพื่อสั่งใช้งานอุปกรณ์เช่น Relay, Buzzer, LED


อุปกรณ์อุตสาหกรรม **DEVIO AIS NB-IoT Smart controller kit** 


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
๏ส่วนแรก
	ในส่วนนี้การคอนฟิกของ MODBUS นั้นจะสามารถคอนฟิกเพียงใช้คอลัมน์ A เท่านั้นในคอลัมน์อื่นใช้เป็นเพียงคำอธิบาย 

 [![Capture.png](https://i.postimg.cc/c6qSJG36/Capture.png)](https://postimg.cc/8fb3y3tV)

	- บรรทัดที่ 1 สั่งใช้งานกำหนด on หรือ off ในคอลัมน์ A เพื่อใช้พอร์ตการสื่อสาร RS485
	- บรรทัดที่ 2 สั่งใช้งานกำหนด on หรือ off ในคอลัมน์ A เพื่อส่งค่าไปแสดงผลบน Magellan Platform 
	- บรรทัดที่ 3 ในส่วนนี้แต่ละเฟรมร้องขอจะบรรจุหมายเลขฟังก์ชั่นที่นิยามลักษณะการทำงานที่ถูกต้องการให้สแลฟดำเนินการ ความหมายของฟิลด์ข้อมูลขึ้นอยู่กับหมายเลขหรือชนิดฟังก์ชั่นที่ใช้ การร้องขอในบางครั้งอาจเรียกอีกอย่างว่า คิวรี (Query) ซึ่งเป็นศัพท์ทางเทคนิคที่ใช้กันมากในระบบฐานข้อมูล

> **Note:** 
> - FC 01 สำหรับ read Coil แสดงสถานะของ Digital Output
(0 = OFF, 1 = ON) ฟังก์ชั่นนี้อนุญาตให้มาสเตอร์สามารถดึงสถานะ ON/OFF ของคอยล์ในตัวสแลฟซึ่งปกติแล้วจะใช้บอกสถานะการคอนโทรลของสแลฟว่าควบคุมอะไรอย่างไรในขณะนั้น 
> - FC 02 สำหรับการ read Discrete input แสดงสถานะของ Digital Input
(0 = OFF, 1 = ON) ฟังก์ชั่นนี้ทำให้มาสเตอร์สามารถอ่านค่าอินพุตแบบดิสครีต (Discrete Input) หรือดิจิตอลอินพุตในอุปกรณ์สแลฟ ฟิลด์ข้อมูลของเฟรมร้องขอจะประกอบด้วยหมายเลขแอดเดรสของอินพุตแรกตามด้วยจำนวนดิจิตอลอินพุตที่ต้องการอ่าน 
> - FC 03 สำหรับ read Holding register แสดงค่าของ Analog Output ฟังก์ชั่นนี้ทำให้มาสเตอร์สามารถดึงค่าในรีจิสเตอร์ของสแลฟได้ โดยทั่วไปคือค่าเซตติ้งหรือพารามิเตอร์ของอุปกรณ์นั้น ๆ
> - FC 04 สำหรับการ read Input register แสดงค่าของ Analog Input ฟังก์ชั่นนี้อนุญาตให้มาสเตอร์ สามารถอ่านค่าอินพุตรีจิสเตอร์จากหลาย ๆ รีจิสเตอร์ในอุปกรณ์สแลฟ โดยทั่วไปอินพุตรีจิสเตอร์จะมีไว้เก็บค่าวัดอะนาลอก

**อ่านข้อมูลเพิ่มเติมได้ที่**
http://www.wisco.co.th/main/articles/Modbus ,
http://www.thailandindustry.com/indust_newweb/articles_preview.php?cid=10995

	- บรรทัดที่ 4 Address ของอุปกรณ์ Slave แต่ละตัวที่ได้รับการกำหนดอยู่ Address ในช่วง 1–247 เมื่อ Slave มีส่งการตอบสนองของมัน Address ของตัวมันเองจะอยู่ในขอบเขต Address Field ของการตอบสนองเพื่อให้อุปกรณ์ Master ทราบว่าอุปกรณ์ Slave กำลังตอบสนองอยู่

๏**ส่วนที่สอง** 
	นั้นจะเป็นส่วนของ Operator ในส่วนนี้เราจะทำการระบุ Register Address ของอุปกรณ์เพื่ออ่านค่าต่างๆ และสามารถใช้งาน Operator ในการ บวก ลบ คูณ หรือ หาร ค่าที่อ่านมาได้ แล้วยังสามารถตั้งชื่อให้กับค่า Address ที่อ่านมาได้โดยใส่ใน Colum ของ Name

[![Capture2.png](https://i.postimg.cc/GtcPrQjJ/Capture2.png)](https://postimg.cc/jwFn4ymL)

	- บรรทัดที่ 7 เป็นส่วนของ header ตารางซึ่งจะระบุตาม Colum ดังนี้
		  คอลัมน์ A คือ ส่วนของการกำหนด Register Address ของอุปกรณ์
		  คอลัมน์ B คือ ส่วนของ Operator  ที่จะใช้ในการ บวก(+) ลบ(-) คูณ(*) และ 
			      หาร( / ) ค่าที่อ่านมาได้
		  คอลัมน์ C คือ ส่วนของค่าที่จะใช้ในการ Operate
		  คอลัมน์ D คือ ส่วนของกำหนดชื่อให้กับ Register Address 
	- บรรทัดที่ 8-17 ใช้ระบุ Register Address ที่ต้องการอ่านค่า สามารถอ่านค่าแอดเดรสได้สูงสุด 10 ค่า แต่ถ้าหากต้องการอ่านเพียงค่าเดียว ให้กำหนด none ในแต่ละบรรทัด 

ในที่นี่จะยกตัวอย่าง Register Address ของ AW5485 เป็นเซนเซอร์วัดอุณหภูมิและความชื้น
[![Capture3.png](https://i.postimg.cc/7LZfxRvL/Capture3.png)](https://postimg.cc/RW2MdXZr)

**ตัวอย่าง** โดยจะระบุค่า 0x0005 เพื่อทำการอ่านค่า Temperature และใช้งาน Operator ซึ่งจะใช้การกำหนด / เพื่อหารค่า แล้วทำการกำหนดค่า 100 ดังนั้นค่าที่ได้จากการอ่านจะหารด้วย 100  หลังจากนั้นทำการใส่ชื่อโดยที่นี่จะใส่คำว่า Temp และทำการใส่ none ในบรรทัดอื่นที่ไม่ได้ใช้งาน

[![Captur.png](https://i.postimg.cc/XNdrQV9w/Captur.png)](https://postimg.cc/grcc0bSJ)

๏**ส่วนสุดท้าย** 
	ในส่วนนี้จะเป็นการกำหนด Buad Rate และ Serial communication

[![Capture5.png](https://i.postimg.cc/sgTJWXcQ/Capture5.png)](https://postimg.cc/0zJmR9hP)

	- บรรทัดที่ 23 กำหนด Buad Rate ในคอมลัมน์ A
	- บรรทัดที่ 24 เลือกกำหนด Serial Protocol ในคอลัมน์ A ซึ่งเราจะมีให้เรียกใช้งาน 12 รูปแบบ 
**อ่านข้อมูลเพิ่มเติมได้ที่**
https://blog.thaieasyelec.com/espino32-ch7-how-to-use-uart/

4.หลังจากที่กำหนดค่า Config เสร็จแล้วให้ทำการกด Save ไฟล์ โดยการกด Ctrl+S 

5.เมื่อเสร็จแล้วให้นำ Micro SD Card กลับเข้าไปเสียบเข้ากับตัวอุปกรณ์

6.หลังจากนั้นให้ทำการกดปุ่ม Reset 1 ครั้งเพื่อให้อุปกรณ์ทำการอ่านค่า Config จากไฟล์ MODBUS.csv

7.ทำการเปิด google chrome แล้วไปที่ https://magellan.ais.co.th/users/signin
ทำการสมัครและล็อคอิน 
[![11.png](https://i.postimg.cc/CLbBPQR2/11.png)](https://postimg.cc/0b2yrZdG)
8.ไปที่หน้า Things และคลิกปุ่ม“ Register thing” หรือ“ +”
[![S-27123714.jpg](https://i.postimg.cc/MZNFwdWx/S-27123714.jpg)](https://postimg.cc/Wtmn6mFf)
9. กรอกแบบฟอร์ม“ Thing Name”,“ ICCID”,“ IMEI” โดย ICCID, IMEI สามารถดูได้ที่กล่อง DEVIO NB-IoT Devkit I 
[![aa.jpg](https://i.postimg.cc/qMHxQYJt/aa.jpg)](https://postimg.cc/XXx5Ysy3)
ICCID คือหมายเลขของ S/N
[![dd.jpg](https://i.postimg.cc/63YxzRRq/dd.jpg)](https://postimg.cc/1nnd38v1)
10.คลิกที่ "Things" จะพบค่า Temp ที่ส่งมา
[![Temp-payload.jpg](https://i.postimg.cc/yx01jWVb/Temp-payload.jpg)](https://postimg.cc/q6MHMJ6s)
11.คลิกที่ "Dashboard" ไปที่ >"+Create Dashboard" ทำการกรอกข้อมูล แล้วคลิก"Create Dashboard" จะพบหน้าต่างของ Dashboard ที่เราสร้าง
[![Temp-payload-dashboard.jpg](https://i.postimg.cc/CKtwVb52/Temp-payload-dashboard.jpg)](https://postimg.cc/v1WJrgW7)
12.คลิกที่ "Create Widgets"
[![dashboard.jpg](https://i.postimg.cc/RVbsddD2/dashboard.jpg)](https://postimg.cc/6ynf5rwh)
13.หลังจากนั้นให้เลือก widgets ตามลักษณะการใช้งาน โดยในที่นี่เราจะใช้รูปแบบ "Animation" และใช้การแสดงผลในรูปแบบ> "Circular Gauge" หลังจากนั้นคลิก "Next"
[![create-widjet.jpg](https://i.postimg.cc/Prf92Prv/create-widjet.jpg)](https://postimg.cc/bdMmvYnq)
14.กรอกแบบฟอร์ม "Create Widget" และทำการเลือก Thing name ให้ตรงกับที่สร้างในตอนต้น
[![widget-data.jpg](https://i.postimg.cc/L4WL0Wmk/widget-data.jpg)](https://postimg.cc/pyDmmqhy)
15.เลือก Sensor ให้ตรงกับตัวแปรที่ส่งมา ในที่นี่คือ "Temp" เมื่อครบแล้วทำการคลิก "Next"
[![widget-data-sensor.jpg](https://i.postimg.cc/7Z9gXZhh/widget-data-sensor.jpg)](https://postimg.cc/ts1Z4yhG)
16.ทำการกรอกข้อมูลให้ครบตามแบบฟอร์ม
[![widget-option.jpg](https://i.postimg.cc/qMbJLf00/widget-option.jpg)](https://postimg.cc/GHDnL5HS)
17.เมื่อทำตามขั้นตอนจนครบแล้วจะพบหน้าต่างแสดงผลค่า Temp ที่เราส่งมา
[![finish-Temp-dashboard.jpg](https://i.postimg.cc/XvFn4p57/finish-Temp-dashboard.jpg)](https://postimg.cc/xk0wPjgW)

ปล.รูปแบบจะแตกต่างกันไปตามการใช้งาน "Widgets" ที่เราเลือกใช้

----------


###**Config Analog**

เปิดไฟล์ ANALOG.csv เมื่อเปิดไฟล์เราจะพบหน้าต่าง Config ของการอ่านค่า Analog
[![analoh.png](https://i.postimg.cc/kX7HCMLN/analoh.png)](https://postimg.cc/MXr5bw6X)
หลังจากนั้นให้ผู้ใช้งานกำหนดค่าต่างๆที่ต้องการใช้งาน

การ **Config Analog** นั้นจะมีส่วนสำคัญที่ต้องรู้ โดยเราจะอธิบายแต่ละส่วน ดังนี้

๏**ส่วนแรก** ประกอบไปด้วย
	ในส่วนนี้การคอนฟิกของ MODBUS นั้นจะสามารถคอนฟิกเพียงใช้คอลัมน์ A เท่านั้นในคอลัมน์อื่นใช้เป็นเพียงคำอธิบาย 

[![Capture6.png](https://i.postimg.cc/rF47DHXy/Capture6.png)](https://postimg.cc/CzFctmx9)

	- บรรทัดที่ 1, 6, 11, 16  สั่งเปิดปิดการใช้งาน on หรือ off ใน คอลัมน์ A เพื่อใช้พอร์ตการสื่อสาร Analog 
	- บรรทัดที่ 2, 7, 12, 17  ตั้งชื่อให้กับ พอร์ตที่ใช้งาน ในคอลัมน์ A
	- บรรทัดที่ 3, 8, 13, 18  กำหนดค่า min ในคอลัมน์ A
	- บรรทัดที่ 4, 9, 14, 19  กำหนดค่า max ในคอลัมน์ A 

๏**ส่วนสุดท้าย**

[![Capture7.png](https://i.postimg.cc/nV0y8mKZ/Capture7.png)](https://postimg.cc/w3RfL7bb)

	- บรรทัดที่ 21 สั่งใช้งาน on หรือ off เพื่อส่งค่าไปแสดงผลบน Magellan Platform ในคอลัมน์ A
หลังจากที่กำหนดค่า Config เสร็จแล้วให้ทำการกด Save ไฟล์

เมื่อเสร็จแล้วให้นำ Micro SD Card กลับเข้าไปเสียบเข้ากับตัวอุปกรณ์

หลังจากนั้นให้ทำการกดปุ่ม Reset 1 ครั้งเพื่อให้อุปกรณ์ทำการอ่านค่า Config จากไฟล์ ANALOG.csv


----------
###**Config Digital I/O**
เปิดไฟล์ DIGITAL.csv เมื่อเปิดไฟล์เราจะพบหน้าต่าง Config ของการควบคุม Digital Inputs และ Digital Output 
[![1.png](https://i.postimg.cc/JzhQvT3c/1.png)](https://postimg.cc/6yDRGfmy)
หลังจากนั้นให้ผู้ใช้งานกำหนดค่าต่างๆที่ต้องการใช้งาน

การ **Config Digital I/O** นั้นจะมีส่วนสำคัญที่ต้องรู้ โดยเราจะอธิบายแต่ละส่วน ดังนี้
๏**ส่วนแรก** 
	ในส่วนนี้การคอนฟิกของ MODBUS นั้นจะสามารถคอนฟิกเพียงใช้คอลัมน์ A เท่านั้นในคอลัมน์อื่นใช้เป็นเพียงคำอธิบาย 

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
	- บรรทัดที่ 66 กำหนดชื่อของ Relay ผู้ใช้สามารถเปลี่ยนแปลงได้
	- บรรทัดที่ 68 สั่งเปิดปิดการใช้งาน on หรือ off การส่งค่าไปแสดงผลบน Magellan Platform

๏**ส่วนที่สอง** 
	นั้นจะเป็นส่วนของการ **Config Time** กำหนดค่าเวลา ประกอบไปด้วย

[![8.png](https://i.postimg.cc/T3GWqhF5/8.png)](https://postimg.cc/sv6X3fV3)

	- บรรทัดที่ 73 เป็นส่วนของ header ตารางซึ่งจะระบุตาม Colum ดังนี้
		  คอลัมน์ A คือ ส่วนของการกำหนดชื่อ
		  คอลัมน์ B คือ ส่วนของการเปิดปิดการใช้งานค่าเวลาที่กำหนด
		  คอลัมน์ C คือ ส่วนของการกำหนดจำนวนวันที่ต้องการให้ทำงาน
		  คอลัมน์ D คือ ส่วนของการกำหนด ชั่วโมง การทำงาน
		  คอลัมน์ E คือ ส่วนของการกำหนด นาที การทำงาน
		  คอลัมน์ F คือ ส่วนของการกำหนด วินาที การทำงาน
	- บรรทัดที่ 74-83 เป็นส่วนของการกำหนดการใช้ Time ตามรูปแบบ 
		  เช่น ทำการ Config ค่าในบรรทัดที่ 27  
		        คอลัมน์ A 	กำหนดชื่อ Time1 
		        คอลัมน์ B	กำหนด on
		        คอลัมน์ C	กำหนด วัน เป็น 1 = 1 วัน
	        	คอลัมน์ D	กำหนด ชั่วโมง เป็น 5 = 5ชั่วโมง 	
	        	คอลัมน์ E	กำหนด นาที เป็น 30 = 30 นาที 	
	        	คอลัมน์ F	กำหนด วินาที เป็น 0 = 0 วินาที

	ผลที่ได้คือ จะทำงานเป็นจำนวน 1 วัน ทำงาน 5 ชั่วโมงกับอีก 30 นาที

๏**ส่วนสุดท้าย** ในส่วนนี้จะเป็นการกำหนดเงื่อนไขของการใช้งานค่าเวลาซึ่ง
เราจะสามารถนำส่วนของการ **Config Time** มาใช้ในเงื่อนไขได้ด้วย ส่วนของ Output Condition นั้นจะมีรายละเอียดดังนี้

[![9.png](https://i.postimg.cc/kXW55VKH/9.png)](https://postimg.cc/MvKwPps0)

	- บรรทัดที่ 89 เป็นส่วนของ header ตารางซึ่งจะระบุตาม Colum ดังนี้
		  คอลัมน์ A คือ กำหนด on หรือ off เพื่อเปิด/ปิด พอร์ต Digital
		  คอลัมน์ B คือ กำหนด on หรือ off เพื่อเปิด/ปิดการใช้งาน loop การทำงาน
		  คอลัมน์ C คือ กำหนดพอร์ตที่จะใช้งาน D0-D15
		  คอลัมน์ D คือ กำหนดสถานะการทำงาน high หรือ low 
		  คอลัมน์ E คือ กำหนดเวลาในการส่ง Output 
		  คอลัมน์ F คือ ส่วนนี้จะเป็นการนำ name ของอุปกรณ์ที่เราอ่านมาได้จากพอร์ตของ RS485, Analog หรือ Digital มาเข้าเงื่อนไขเพื่อทำการเปรียบเทียบ
		  คอลัมน์ G คือ กำหนดเครื่องหมาย >, <, =, >=, <=, #เพื่อเปรียบเทียบ
		  คอลัมน์ H คือ กำหนดค่าตัวแปร ค่าที่อ่านมาได้จากอุปกรณ์ หรือ เวลา เพื่อนำมาเข้าเงื่อนไขเพื่อทำการเปรียบเทียบ
	- บรรทัดที่ 90-99 เป็นส่วนของการกำหนดการใช้เงื่อนไข ตามรูปแบบ 
		  เช่น ทำการ Config ค่าในบรรทัดที่ 90
			คอลัมน์ A กำหนด on
			คอลัมน์ B กำหนด on 
			คอลัมน์ C กำหนด พอร์ต D1 
			คอลัมน์ D กำหนด สถานะพอร์ตให้เป็น high
			คอลัมน์ E กำหนด ส่งเอาต์พุต 0.5 วินาที
			คอลัมน์ F กำหนด Time count (การนับเวลา)
			คอลัมน์ G กำหนด เครื่องหมาย =
			คอลัมน์ H กำหนด ดึงชื่อตัวแปร Time3 (จาก Time Config)
	ผลที่ได้คือ เปิดใช้งาน (on)  พอร์ต D1 ให้ส่ง high เป็นเวลา 0.5 วิ เมื่อนับเวลาไปได้เท่ากับเวลาที่ Time3 เก็บค่าไว้ คือ 0.5 วินาที จะทำงานแบบนี้วนไปเรื่อยเนื่องจาก เปิดการใช้งาน (on) loop activate
