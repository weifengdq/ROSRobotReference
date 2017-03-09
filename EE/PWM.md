## PWM

PWM, Pulse Width Modulation\(脉冲宽度调制\)的缩写. 以前用白炽灯的时候, 我们知道是50Hz的正弦交流电, 尽管电压信号不断变化, 但由于频率较快, 人眼看不出很明显的闪烁, 220V指的是方均根值. 我们把正弦波换成方波, 就有了类似PWM的概念, 我们不主要关注是3.3V还是5V单片机产生的PWM波, 它们对于使用来说几乎没有区别, 我们关注的特征值主要是**周期**\(频率\)和**占空比**, 给定一个特定频率的方波, PWM调制的就是这个占空比.

![](/assets/占空比.png)

PWM平均值的计算可以通过积分积出来: 

![](/assets/PWM1.png)

波形为f\(t\), 周期T, 最小值ymin, 最大值ymax, 占空比D, 则平均值为:

![](/assets/PWM平均值.png)

如果ymin = 0, 则: 

![](/assets/PWM平均值3.png)

这就是我们常见的形式.

PWM还有一个**分辨率**的概念, 我们常说的 7bit, 8bit, 10bit, 12bit, 16bitPWM指的就是分辨率. 常说的无级调速其实还是有级的, 只不过级数多了而已. 如果分辨率是1bit, 就有只有开和关两种状态, 如果是2bit分辨率, 就有0%, 25%, 50%, 100%4种状态. 类似我们开车时的挂1 2 3 4挡, 8bit PWM 就有256种状态. 

PWM主要调的是占空比, 那这个周期或者频率怎么确定? 得看应用场景了, 从维基摘一段: 

> Switching has to be done several times a minute in an electric stove; 120 Hz in a lamp dimmer; between a few kilohertz \(kHz\), to tens of kHz for a motor drive; and well into the tens or hundreds of kHz in audio amplifiers and computer power supplies.

PWM有哪些应用, 举几个常见但绝不完全的例子:

* LED的亮度调节, 如液晶屏背光, 呼吸灯等.
* 产生模拟输出, 只需要后面接一个滤波器如RC滤波器就可以实现一个DA的功能.
* 产生音频信号, 数字音频就是这么来的.
* 控制电机转速, 不论是直流电机, 无刷电机都是PWM进行调速的.
* 产生调制信号, 如红外遥控也是PWM.

单片机产生PWM至少有两种方法, 一种是 Bit-banging 技术:

> Bit banging is a technique for serial communications using software instead of dedicated hardware. Software directly sets and samples the state of pins on the microcontroller, and is responsible for all parameters of the signal: timing, levels, synchronization, etc.

那分辨率又怎么选, 看你想要达到的调节精度了, 想调节的越平滑越精细那就选越高分辨率的PWM好了,  同样是电机调速, 普通风扇用8bit\(分辨率256\)PWM就可以了, 如果是车床, 医疗机器人之类的, 妥妥的12bit, 16bit吧.

上个代码看看:

```c
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delayMicroseconds(100); // Approximately 10% duty cycle @ 1KHz
  digitalWrite(13, LOW);
  delayMicroseconds(1000 - 100);
}
```

delayMicroseconds\(\)是延时多少微秒, 这个程序产生1kHz, 10%占空比的方波, 有1000的分辨率\(1000种状态\). 如果去掉delayMicroseconds\(\), 我们可以得到恐怖的几百千甚至可能上兆的频率. 如果单片机有定时器的话, 我们可以用定时器来精确产生各种频率占空比的PWM波.

另外一种产生PWM的方法就是直接填寄存器了, 现在

## Reference

https://en.wikipedia.org/wiki/Pulse-width\_modulation


