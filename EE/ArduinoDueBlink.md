## 点灯

点灯号称硬件界的"Hello World", 能点灯就表示环境搭建好了, 也就成功了1/3. 

连接Arduino Due的Programming USB口到电脑.

![](/assets/USBArduinoDue.png)

打开Arduino IDE, 选择File -&gt; Examples -&gt; Basics -&gt; Blink: 

![](/assets/Blink.png)

可以看到如下代码: 

```c
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
}
```

引用一下: 

> Most Arduino boards have a pin connected to an on-board LED in series with a resistor. The constant LED\_BUILTIN is the number of the pin to which the on-board LED is connected. Most boards have this LED connected to digital pin 13.

Arduino有个不成文的约定, 每个板子总有一个叫 13 的端口连接到LED, 并且高电平点亮. 以前可能会有 '\#define LED 13' 之类的代码, 现在直接省去宏定义, 用 LED\_BUILTIN 就可以了. 









---

## Reference

https://www.arduino.cc/en/Reference/Constants

https://www.arduino.cc/en/Reference/HomePage



















