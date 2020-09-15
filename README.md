# jk 2020/9/1
ARDUINO
void setup(){}<--只執行一次，Arduino的初級設定 </p>
void loop(){}<--會重複執行，主程式的位置  </p>
第一個指令 </p>
腳位模式:pinMode (pin,OUTPUT);  </p>
腳位模式設定 所使用的腳位設定為輸入或輸出 </p> 
設定腳位輸出(=0)，腳位輸入(=1) </p>

--------------------------------------------
第一個程式LED 閃爍 亮0.55 暗0.55 </p>
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/4092F459-5D58-4E3F-A351-D81FAB0B066F.jpeg) 


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 2020/09/08
四顆LED燈同時閃爍 
```c++
void setup() {
  // put your setup code here, to run once:
pinMode (2,OUTPUT);
pinMode (3,OUTPUT);
pinMode (4,OUTPUT);
pinMode (5,OUTPUT);
}
void loop() {
  // put your main code here, to run repeatedly:
digitalWrite (2,LOW);
digitalWrite (3,LOW);
digitalWrite (4,LOW);
digitalWrite (5,LOW);
delay(100);
digitalWrite (2,HIGH);
digitalWrite (3,HIGH);
digitalWrite (4,HIGH);
digitalWrite (5,HIGH);
delay(100);
}
``` 
--------------------------------------------
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/2DBBEB56-89E3-4B52-A44C-F983056C9875.jpeg) 

--------------------------------------------
# 2020/09/15
LED跑馬燈
```c++
int LED=6;
void setup() {
  for (int i=2 ;i<6;i++)
  pinMode (i, OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  for (int i=5; i>1; i--)
    digitalWrite(i,HIGH);
  if (LED>=2)
    digitalWrite(LED,LOW);
  else
    LED=6;
  LED--;

 delay (500);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/4E9708B3-E93D-4508-9749-1F0F93F0AA24.jpeg)
