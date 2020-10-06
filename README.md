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
# 2020/09/15-1
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

--------------------------------------------
# 2020/09/15-2
LED跑馬燈8顆左到右
```c++
int LED=10;
void setup() {
  for (int i=1 ;i<10;i++)
  pinMode (i, OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  for (int i=10; i>1; i--)
    digitalWrite(i,HIGH);
  if (LED>=1)
    digitalWrite(LED,LOW);
  else
    LED=10;
  LED--;

 delay (500);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/DD1E134D-F9AF-43D5-A198-4C487D2EA0E9.jpeg)
# 2020/09/15-3
LED跑馬燈8顆右到左
```c++
int b = 255;
int f = -1;
void setup() {
  pinMode(5,OUTPUT);
}
void loop() {
  analogWrite(5,b);
  b = b + f;
  if (b <=0||b >= 255)
     f = -f;
  delay(5);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/DD1E134D-F9AF-43D5-A198-4C487D2EA0E9.jpeg) 

--------------------------------------------
# 2020/09/16-4
呼吸燈
```c++
int b = 0;
int f = 1;
void setup() {
  pinMode(5,OUTPUT);
}
void loop() {
  analogWrite(5,b);
  b = b + f;
  if (b <=0)
     f = -f;
  if (b >= 255)
    f = -f;
  delay(5);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/19459A04-DC0A-4801-B51D-8CE212B31CEC.jpeg)


--------------------------------------------
# 2020/09/22-1
按鈕讓LED亮起，RESET鍵暗掉
```
void setup() {
 pinMode(2,INPUT);
 pinMode(3,OUTPUT);
 digitalWrite(3,HIGH);
 digitalWrite(2,HIGH);
}

void loop() {
  if(digitalRead(2) == 0)
  {
    digitalWrite(3,LOW);
  }
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/5ED182AD-53DF-4A06-894C-92C9442B20AB.jpeg)

--------------------------------------------
# 2020/09/22-2
切換LED亮或滅
```c++
int j=1,jj=1;
void setup() {
 pinMode(2,INPUT);
 pinMode(3,OUTPUT);
 digitalWrite(2,HIGH);
 digitalWrite(3,HIGH);
}
void loop() {
  if(!digitalRead(2))
  {
    while(!digitalRead(2))
    delay(20);
    jj=0;
  }
  else
  {
    if(!jj)
    {
      jj=1;
      j^=1;
    }
  }
  digitalWrite(3,j);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/5ED182AD-53DF-4A06-894C-92C9442B20AB.jpeg)

--------------------------------------------
# 2020/09/29-1
切換LED模式
```c++
byte ledpin[8]={3,4,5,6,7,8,9,10};
int jj =1 ,a=-1;
void setup()
{
  for(int i=0;i<8;i++)pinMode(ledpin[i],OUTPUT);
  for(int i=0;i<8;i++)digitalWrite(ledpin[i],1);
  pinMode(2,INPUT);
  digitalWrite(2,1);
}
void loop() 
{
  if(!digitalRead(2))
  {
    while(!digitalRead(2))delay(20);
    if(!jj)
    {
      a++;
      jj=1;
    }
  }
  else
  {
    jj=0;
    switch(a)
    {
      case 0:
        for(int i=0;i<8;i++)
        {
          for(int j=0;j<8;j++)digitalWrite(ledpin[j],1);
          digitalWrite(ledpin[i],0);
          delay(100);
        }
      break;
      case 1:
        for(int i=7;i>-1;i--)
          {
            for(int j=0;j<8;j++)digitalWrite(ledpin[j],1);
            digitalWrite(ledpin[i],0);
            delay(100);
          }
      break;
      case 2:
        for(int i=0;i<8;i++)digitalWrite(ledpin[i],1);
      break;
      case 3:
        a=0;
      break;
    }
  }
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/0C73F7E5-B205-4478-A07D-879436FD531A.jpeg)

--------------------------------------------
#2020/10/06
按鈕切換燈光以及切換LED模式
```c++
int b = 255;
int f = -1;
int jj = 1, a = -1;
int gg = 1 , B = -1;
void setup() {
  pinMode(2,INPUT);
  digitalWrite(2,1);
  pinMode(4,INPUT);
  digitalWrite(4,1);
for(int i=9;i<12;i++)
  pinMode(i,OUTPUT);
}
void loop() {
  if(!digitalRead(4))
  {
    while(!digitalRead(4))RGB(0,0,0);
    if(!gg)
    {
      B++;
      gg=1;
    }
  }
  else
  {
    gg=0;
    switch(B)
    {
      case 0:
      RGB(255,0,0);
      RGB(0,255,0);
      RGB(0,0,255);
      break;
      case 1:
      BRGB();
      break;
      case 2:
      ButtonRGB();
      break;
      case 3:
      B = 0;
      break;
    }
  }
}
void RGB(byte R ,byte G ,byte B) {
  analogWrite(9,R);
  analogWrite(10,G);
  analogWrite(11,B);
  delay(1000);
}
void BRGB() {
  analogWrite(9,b);
  b = b + f;
  if (b <=0||b >= 255)
     f = -f;
    delay(5);
}
void ButtonRGB() {
    if(!digitalRead(2))
  {
    while(!digitalRead(2))delay(20);
    if(!jj)
    {
      a++;
      jj=1;
    }
  }
  else
  {
    jj=0;
    switch(a)
    {
      case 0:
        RGB(255,0,0);
      break;
      case 1:
        RGB(0,255,0);
      break;
      case 2:
        RGB(0,0,255);
      break;
      case 3:
        RGB(255,255,0);
      break;
      case 4:
        RGB(0,255,255);
      break;
      case 5:
        RGB(255,0,255);
      break;
      case 6:
        a = 0;
      break;
    }
  }
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/jk/blob/master/0C73F7E5-B205-4478-A07D-879436FD531A.jpeg)
