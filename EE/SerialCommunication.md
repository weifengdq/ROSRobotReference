## 串口通信

我们打开File -&gt; Example -&gt; Communication -&gt; SerialEvent：

![](/assets/SerialEvent.png)

下载到Arduino Due中, 然后点击右上角的串口监视器图标:

![](/assets/SerialMonitor.png)

然后按照图中配置:

![](/assets/SerialMonitor2.png)

我们在输入框中输入一行字母, 然后按下回车, 就可以在接收框中看到刚才输入框中的内容.

我们把代码贴过来:

```c
String inputString = "";         // a string to hold incoming data
boolean stringComplete = false;  // whether the string is complete

void setup() {
  // initialize serial:
  Serial.begin(9600);
  // reserve 200 bytes for the inputString:
  inputString.reserve(200);
}

void loop() {
  // print the string when a newline arrives:
  if (stringComplete) {
    Serial.println(inputString);
    // clear the string:
    inputString = "";
    stringComplete = false;
  }
}

/*
  SerialEvent occurs whenever a new data comes in the
 hardware serial RX.  This routine is run between each
 time loop() runs, so using delay inside loop can delay
 response.  Multiple bytes of data may be available.
 */
void serialEvent() {
  while (Serial.available()) {
    // get the new byte:
    char inChar = (char)Serial.read();
    // add it to the inputString:
    inputString += inChar;
    // if the incoming character is a newline, set a flag
    // so the main loop can do something about it:
    if (inChar == '\n') {
      stringComplete = true;
    }
  }
}
```

**String**

> The String object allows you to manipulate strings of text in a variety of useful ways. You can append characters to Strings, combine Strings through concatenation, get the length of a String, search and replace substrings, and more.

**boolean**

> A boolean holds one of two values, true or false. \(Each boolean variable occupies one byte of memory.\)

**Serial.begin\(\)**

> Sets the data rate in bits per second \(baud\) for serial data transmission. For communicating with the computer, use one of these rates: 300, 600, 1200, 2400, 4800, 9600, 14400, 19200, 28800, 38400, 57600, or 115200. You can, however, specify other rates - for example, to communicate over pins 0 and 1 with a component that requires a particular baud rate.

Serial.begin\(9600\): 设置串口0通信的波特率为9600bps. Arduino Due还有Serial1, Serial2, Serial3. 连接USB Programming Port口的是Serail.

**string.reserve\(size\)**

> The String reserve\(\) function allows you to allocate a buffer in memory for manipulating strings.

inputString\(200\); 为inputString分配200字节的buffer.

**Serial.println\(\)**

> Prints data to the serial port as human-readable ASCII text followed by a carriage return character \(ASCII 13, or '\r'\) and a newline character \(ASCII 10, or '\n'\). This command takes the same forms as Serial.print\(\).

类似于我们C中的printf, 只不过用法上有些区别, 而且在后面加了换行:

> Serial.print\(78\) gives "78"
>
> Serial.print\(1.23456\) gives "1.23"
>
> Serial.print\('N'\) gives "N"
>
> Serial.print\("Hello world."\) gives "Hello world."

我们以前学习51单片机的时候 , 有一个关键字叫code, 或者STM32的全局const关键字, 可以把字符串放到Flash中, 而不是RAM中, 这样虽然速度稍慢, 但可以存储的字符量一下在变大了好多, 毕竟RAM一般比FLASH少, 类似我们电脑内存比硬盘容量小, 像Arduino Due的RAM只有96kB, Flash有512kB.

> You can pass flash-memory based strings to Serial.print\(\) by wrapping them with F\(\). For example :
>
> Serial.print\(F\(“Hello World”\)\)

这就是Arduino中把字符串放到Flash中的方法, 也就是使用F\(\)即可.

**serialEvent\(\)**

> Called when data is available. Use Serial.read\(\) to capture this data.

串口0的接收中断, Arduino mega还有 serialEvent1\(\), serialEvent2\(\), serialEvent3\(\)等.

**Serial.available\(\)**

> Get the number of bytes \(characters\) available for reading from the serial port. This is data that's already arrived and stored in the serial receive buffer \(which holds 64 bytes\). available\(\) inherits from the Stream utility class.
>
> Returns
>
> the number of bytes available to read

**Serial.read\(\)**

> Reads incoming serial data. read\(\) inherits from the Stream utility class.
>
> Returns
>
> the first byte of incoming serial data available \(or -1 if no data is available\) - int

程序就先看到这里.

---

## Reference

[https://www.arduino.cc/en/Reference](https://www.arduino.cc/en/Reference/Serial)

---

华丽的分割线后， 我们来看下原理图：

![](/assets/TXRX.png)串口0通过一片 ATMEGA16U2 作USB转串口. 这是个单片机, 封装了很多东西. 据说ATMEGA16U2已经成了新出的Arduino的标配.

其他我们用作USB转串口的还有 CH340, CH341,  PL2303, CP2102, CP2104, 双串口的CP2105， FT2232等.

---

接下来分享一篇以前的文章, 可以让分不清TTL, CMOS, RS232的人有一个明确的区分:

[硬件选讲之UART](http://blog.csdn.net/weifengdq/article/details/39451733)

