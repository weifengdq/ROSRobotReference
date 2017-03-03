## [Arduino Due](https://www.arduino.cc/en/Main/ArduinoBoardDue)

> The Arduino Due is the first Arduino board based on a 32-bit ARM core microcontroller. With 54 digital input/output pins, 12 analog inputs, it is the perfect board for powerful larger scale Arduino projects.

![](/assets/ArduinoDueBoard.png)

Arduino Due基于 Atmel SAM3X8E ARM Cortex-M3 CPU. IO最大电平是3.3V, 如果接5V器件, 需要接电平转换电路, 后面我们会提及.

> It has 54 digital input/output pins \(of which 12 can be used as PWM outputs\), 12 analog inputs, 4 UARTs \(hardware serial ports\), a 84 MHz clock, an USB OTG capable connection, 2 DAC \(digital to analog\), 2 TWI, a power jack, an SPI header, a JTAG header, a reset button and an erase button.

Programming Port和NativePort都可以用来下载程序, 官方推荐Programming Port.

官方给的参数:

![](/assets/ArduinoDue参数.png)

---

## Reference

https://www.arduino.cc/en/Main/ArduinoBoardDue

网址的最下面可以下载ArduinoDue的原理图和PCB\(解压后可以使用Eagle打开\).



