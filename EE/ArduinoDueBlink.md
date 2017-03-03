## 点灯

点灯\(Blink\)号称硬件界的"Hello World", 能点灯就表示环境搭建好了, 也就成功了1/3.

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

代码中大致可以看出, Arduino遵循驼峰命名法, 第一个单词小写, 后面的单词首字母大写.

setup, 相当于初始化, 开机后先执行setup中代码, 执行过去直接就进loop永久循环了.

> The setup\(\) function is called when a sketch starts. Use it to initialize variables, pin modes, start using libraries, etc. The setup function will only run once, after each powerup or reset of the Arduino board.
>
> After creating a setup\(\) function, which initializes and sets the initial values, the loop\(\) function does precisely what its name suggests, and loops consecutively, allowing your program to change and respond. Use it to actively control the Arduino board.

pinMode\(pin, mode\)用来配置引脚的模式; pin是数字引脚号, 对应板子上的数字\(Arduino Due是0~53\); mode: INPUT, OUTPUT, or INPUT\_PULLUP, 也就是配置成输入, 输出或者输入上拉. 这里我们驱动LED, 所以配置为输出.

LED\_BUILTIN, 可以直接用数字13替换, 引用一下:

> Most Arduino boards have a pin connected to an on-board LED in series with a resistor. The constant LED\_BUILTIN is the number of the pin to which the on-board LED is connected. Most boards have this LED connected to digital pin 13.

Arduino有个不成文的约定, 每个板子总有一个叫 13 的端口连接到LED, 并且高电平点亮. 以前可能会有 '\#define LED\_PIN_ 13' _或者 _ _'int ledPin = 13' 之类的代码, 现在直接省去宏定义, 用 LED\_BUILTIN 就可以了.

digitalWrite\(pin, value\); pin: the pin number  
; value: HIGH or LOW; 这里就是设置LED引脚输出高电平\(HIGH\)或者低电平\(LOW\).

delay\(ms\); Pauses the program for the amount of time \(in miliseconds\) specified as parameter. delay\(1000\)也就是延时1s.

接下来, 点击Tools, 选择板子类型和串口号:

![](/assets/选择.png)

然后点击图中3的按钮, 编译程序上传到板子中, 就可以看到字符为L处的LED亮1s, 灭1s, 循环往复.

这就是Blink, 恭喜你完成了硬件界的"Hello World"!

---

## Reference

[https://www.arduino.cc/en/Reference/Constants](https://www.arduino.cc/en/Reference/Constants)

[https://www.arduino.cc/en/Reference/HomePage](https://www.arduino.cc/en/Reference/HomePage)

