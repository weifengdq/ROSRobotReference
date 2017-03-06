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

