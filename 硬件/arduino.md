## Arduino

> **Arduino **is a computer hardware and software company, project, and user community that designs and manufactures [microcontroller](https://en.wikipedia.org/wiki/Microcontroller) kits for building digital devices and interactive objects that can sense and control objects in the physical world.

这是 [Arduino Wikipedia](https://en.wikipedia.org/wiki/Arduino\) 对于Arduino的简介. Arduino是一系列开源硬件和软件的集合体, 硬件主控\(含相关\)上从简单的8位单片机到复杂的32位单片机都有, 加上各种扩展板传感器, 和第三方如树莓派, Intel伽利略板之类妙不可言的联系, 几乎可以满足大部分的应用需求. 官方目前把产品分为了入门级, 平衡级, 互联网, 教育, 可穿戴, 3D打印等几个类别. Arduino的软件是特别出彩的部分, 屏蔽了硬件, 提供了简洁的语言特性和统一的接口封装, 不论你是小白, 硬件开发人员, 软件开发人员都可以很快的入门.

---

## 常用工具

### [Arduino IDE](https://www.arduino.cc/en/main/software)

Arduino的集成开发环境, 可以编写, 编译, 上传代码, 集成有串口监视器. 不过编辑器功能较弱, 可以使用外部编辑器如Sublime Text, Atom, VS Code等\(都是跨平台的\). 下图是从Win10应用商店下载的Windows app版本, 不过也有网络编辑器, macOS, Linux各种版本.

![](/assets/ArduinoIDE.png)

### [Processing](http://processing.org/)

> Processing is a flexible software sketchbook and a language for learning how to code within the context of the visual arts.

据说Arduino IDE就是借鉴了Processing和Wiring的特性来的, 所以很多语法和Arduino类似. 用来写Arduino的上位机很不错, 而且也是Windows, macOS, Linux跨平台.

![](/assets/Processing.png)

### [Fritzing](http://fritzing.org/home/)

> Fritzing is an open-source hardware initiative that makes electronics accessible as a creative material for anyone.

Arduino, Raspberry Pi怎么接线之类的很形象的图很多都是用这个软件画的. Windows, macOS, Linux跨平台支持.

![](/assets/Fritzing.png)

### [Eagle](http://www.autodesk.com/products/eagle/overview)

> PCB layout software for every engineer
>
> Bring your electronic inventions to life with a complete set of PCB layout and schematic editing tools in EAGLE software.

目前属于Autodesk旗下的一款免费的原理图和PCB Layout软件, 官方的Arduino板子很多都是用这个软件画的. Windows, macOS, Linux跨平台支持. 下图是Arduino Due的PCB:

![](/assets/Eagle.png)

---

## 常用网址

* Arduino官网: [https://www.arduino.cc/](https://www.arduino.cc/), Learning那一栏必看的.  
* Github Arduino Trending: [https://github.com/trending/arduino](https://github.com/trending/arduino)
* Github Processing Trending: [https://github.com/trending/processing](https://github.com/trending/processing)

---

## 逸事

细心的孩子可能发现会有 arduino.cc 和 arduino.org 两个域名, 或者有Arduino和Genuino两个版本, 这是什么鬼? 其实两个域名都算官网, Arduino和Genuino也没什么差别, Quora的一个问题 [What is the difference between Arduino Uno and Genuino Uno?](https://www.quora.com/What-is-the-difference-between-Arduino-Uno-and-Genuino-Uno)  下面Anand Padmanabhan给出了一个回答, 引用如下:

> No. There is no difference. These are just 2 names of same product in different parts of the world - inside & outside US to be precise
>
> There was actually a split up between the 2 Arduino groups - Arduino.cc and Arduino.org
>
> Arduino.org were doing more of production and Arduino.cc was doing lot of development. Trademark of Arduino in US is with Arduino.cc and everywhere else is with Arduino.org; so Arduino.cc is selling it as Genuino boards outside US.
>
> Here is what has exactly happened - Arduino LLC is the company founded by \[Massimo Banzi\], \[David Cuartielles\], \[David Mellis\], \[Tom Igoe\] and \[Gianluca Martino\] in 2009 and is the owner of the Arduino trademark and gave us the designs, software, and community support that’s gotten the Arduino where it is. The boards were manufactured by a spinoff company, Smart Projects Srl, founded by the same \[Gianluca Martino\]. So far, so good.
>
> Things got ugly in November when \[Martino\] and new CEO \[Federico Musto\] renamed Smart Projects to Arduino Srl and registered arduino.org \(which is arguably a better domain name than the old arduino.cc\). Whether or not this is a infringement is waiting to be heard in the Massachussetts District Court.
>
> According to this Italian Wired article, the cause of the split is that \[Banzi\] and the other three wanted to internationalize the brand and license production to other firms freely, while \[Martino\] and \[Musto\] at the company formerly known as Smart Projects want to list on the stock market and keep all production strictly in the Italian factory.
>
> Naturally, a lot of the original Arduino’s Open Source Hardware credentials and ethos are hanging in the balance, not to mention its supply chain and dealer relationships.



