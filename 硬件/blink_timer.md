## Blink\_Timer

先把我们Blink\_Delay一节中的代码贴过来:

```c
// the setup function runs once when you press reset or power the board
void setup() {
    // initialize digital pin LED_BUILTIN as an output.
    pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
    digitalWrite(LED_BUILTIN, HIGH); // turn the LED on (HIGH is the voltage level)
    delay(1000); // wait for a second
    digitalWrite(LED_BUILTIN, LOW); // turn the LED off by making the voltage LOW
    delay(1000); // wait for a second
}
```

灯亮, CPU停不下来, 空跑1000ms, 再灯灭, 再空跑1000ms...大好年华都浪费在空跑上, 如果有其他任务怎么办...所以这是一种很低效的做法, 几乎没有人会这么做.

学过单片机或微机原理的都知道一个叫定时器中断的东西, 我们开一个定时器中断, 比如1s中断一次, 中断中改变灯的状态即可, 其他时间该干嘛干嘛就好了.

[Arduino Reference](https://www.arduino.cc/en/Reference/HomePage\) 给出了一个 millis\(\) 函数:

> Returns the number of milliseconds since the Arduino board began running the current program. This number will overflow \(go back to zero\), after approximately 50 days.

我们可以用它来做一个定时器, 直接上代码啦:

```c
unsigned long savedTime = 0;
unsigned long nowTime = 0;
unsigned long passedTime = 0;

void setup() {
  // put your setup code here, to run once:
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  passedTime = millis() - savedTime;  //if millis() get max to zero, what will happen? 

  if(passedTime > 1000) {  //1000ms
    savedTime = millis();
    blinkTask();
  }
}

void blinkTask() {
  static unsigned int i = 0;
  if(i%2 == 1) {
    digitalWrite(LED_BUILTIN, HIGH);
  } else {
    digitalWrite(LED_BUILTIN, LOW);
  }
  ++i;
}
```

这样就很容易的实现了一个定时器的任务了, 如果还有其他任务, 就在 blinkTask\(\); 后面继续添加Task好了.  学过C的都知道要封装个结构体了, 至于面向对象的同学看不下去了, 要动手封装timer类了, 操作系统的同学看不下去了, 要加上优先级...有兴趣的可以自己搞一搞啦! 其实Arduino 有好多按捺不住的同学自己封装好了timer库了, 我们拿来自己用就好了, 如 [Timer Library for Arduino](http://playground.arduino.cc/Code/Timer) . 我们摘抄一个Timer Library的例子给大家看看:

```c
#include "Timer.h"


Timer t;


int ledEvent;


void setup()
{
  Serial.begin(9600);
  int tickEvent = t.every(2000, doSomething);
  Serial.print("2 second tick started id=");
  Serial.println(tickEvent);

  pinMode(13, OUTPUT);
  ledEvent = t.oscillate(13, 50, HIGH);
  Serial.print("LED event started id=");
  Serial.println(ledEvent);

  int afterEvent = t.after(10000, doAfter);
  Serial.print("After event started id=");
  Serial.println(afterEvent);

}


void loop()
{
  t.update();
}


void doSomething()
{
  Serial.print("2 second tick: millis()=");
  Serial.println(millis());
}


void doAfter()
{
  Serial.println("stop the led event");
  t.stop(ledEvent);
  t.oscillate(13, 500, HIGH, 5);
} 
```

运行之前需要先安装 Timer Library库, 这是Arduino库的通用安装方法:

> ## Installation
>
> You can download the library from here:
>
> [https://github.com/JChristensen/Timer](https://github.com/JChristensen/Timer)
>
> As with all libraries, unzip the file into the 'libraries' folder in your Arduino directory, which will be in something like 'My Documents\Arduino' on Windows, 'Documents/Arduino' on Mac etc. If this is the first library you have installed, you will need to create a directory there called 'libraries'.

我的Win10 的 libraries 目录在: C:\Users\weifengdq\Documents\Arduino\libraries, 其中weifengdq是我的电脑用户名. 换成你的就可以了.

