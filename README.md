# jk 2020/9/1
ARDUINO
void setup(){}<--只執行一次，Arduino的初級設定 </p>
void loop(){}<--會重複執行，主程式的位置 </p>
第一個指令 </p> 
腳位模式:pinMode (pin,OUTPUT); </p>
腳位模式設定 所使用的腳位設定為輸入或輸出 </p>
設定腳位輸出(=0)，腳位輸入(=1) </p>

--------------------------------------------
第一個程式LED 閃爍 亮0.55 暗0.55 </p>
電路圖如下： </p>
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/4092F459-5D58-4E3F-A351-D81FAB0B066F.jpeg) </p>


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 2020/09/08
四顆LED燈同時閃爍 </p>
void setup() { </p>
  // put your setup code here, to run once: </p>
pinMode (2,OUTPUT); </p>
pinMode (3,OUTPUT); </p> 
pinMode (4,OUTPUT); </p>
pinMode (5,OUTPUT); </p>
} </p>
void loop() { </p> 
  // put your main code here, to run repeatedly: </p>
digitalWrite (2,LOW); </p>
digitalWrite (3,LOW); </p>
digitalWrite (4,LOW); </p>
digitalWrite (5,LOW); </p>
delay(100); </p>
digitalWrite (2,HIGH); </p>
digitalWrite (3,HIGH); </p>
digitalWrite (4,HIGH); </p>
digitalWrite (5,HIGH); </p>
delay(100); </p>
} </p>

--------------------------------------------
電路圖如下： </p>
