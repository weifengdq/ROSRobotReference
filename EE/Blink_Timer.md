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

[Arduino Reference](https://www.arduino.cc/en/Reference/HomePage) 给出了一个 millis\(\) 函数: 

> Returns the number of milliseconds since the Arduino board began running the current program. This number will overflow \(go back to zero\), after approximately 50 days.

我们可以用它来做一个定时器: 

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



