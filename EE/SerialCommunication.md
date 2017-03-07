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

String: 

> The String object allows you to manipulate strings of text in a variety of useful ways. You can append characters to Strings, combine Strings through concatenation, get the length of a String, search and replace substrings, and more.

boolean:

> A boolean holds one of two values, true or false. \(Each boolean variable occupies one byte of memory.\)

Serial.begin\(\):

> Sets the data rate in bits per second \(baud\) for serial data transmission. For communicating with the computer, use one of these rates: 300, 600, 1200, 2400, 4800, 9600, 14400, 19200, 28800, 38400, 57600, or 115200. You can, however, specify other rates - for example, to communicate over pins 0 and 1 with a component that requires a particular baud rate.

Serial.begin\(9600\): 设置串口0通信的波特率为9600bps. Arduino Due还有Serial1, Serial2, Serial3. 连接USB Programming Port口的是Serail.

string.reserve\(size\): 

> The String reserve\(\) function allows you to allocate a buffer in memory for manipulating strings.

inputString\(200\); 为inputString分配200字节的buffer.

Serial.println\(\):

> Prints data to the serial port as human-readable ASCII text followed by a carriage return character \(ASCII 13, or '\r'\) and a newline character \(ASCII 10, or '\n'\). This command takes the same forms as Serial.print\(\).

类似于我们C中的printf, 只不过用法上有些区别, 而且在后面加了换行:

> Serial.print\(78\) gives "78"
>
> Serial.print\(1.23456\) gives "1.23"
>
> Serial.print\('N'\) gives "N"
>
> Serial.print\("Hello world."\) gives "Hello world."

我们以前学习51单片机的时候 , 有一个关键字叫coe, 可以把字符串放到Flash中, 而不是RAM中, 这样虽然速度稍慢, 但可以存储的字符量一下在变大了好多, 毕竟RAM只有

 

 

---

## Reference

https://www.arduino.cc/en/Reference/Serial



