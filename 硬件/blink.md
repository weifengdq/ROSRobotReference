## Arduino IDE Install

ArduinoIDE的下载地址为: [https://www.arduino.cc/en/main/software](https://www.arduino.cc/en/main/software) , 可以自行选择Windows, macOS, Linux的平台来下载. Win 10用户可以直接在应用商店搜索Arduino进行安装:

![](/assets/ArduinoIDEStore.png)

## Arduino Due Core Install

安装完后打开, 菜单栏选择 Tools -&gt; Board -&gt; Boards Manager...

![](/assets/BoardManager.png)

找到 Arduino SAM Boards\(32-bits ARM Cortex-M3\) by Arduino, 点击Install. 我这里已经安装过了:

![](/assets/BoardsManager.png)

## Arduino Due Driver

接下来是驱动安装, macOS和Linux用户是不需要的, Windows用户跑不了...  来吧!

找一根Micro-USB线连接Arduino Due的Programming口\(背面可以看到字符\)和电脑, 如图:

![](/assets/USBArduinoDue.png)

Win 10用户鼠标放到左下角Windows图标, 右键, 选择 设备管理器\(Deveice Manager\),  找到名为  “Ports \(COM & LPT\)”, 单击, 会看到 “Arduino Due...”类的字样, 右键, 选择更新驱动:

![](/assets/更新驱动.png)

那个自动更新需要联网, 或许也可以, 这里选择从本地寻找:

![](/assets/从本地浏览.png)

找到你的Arduino IDE的安装目录, 如从Win10应用商店安装的话, 路径应该是: C:\Program Files\WindowsApps\ArduinoLLC.ArduinoIDE\_1.8.1.0\_x64\_\_mdqgnx93n4wtt , 后面的数字可能会有不同, 选中drivers, 点击OK:

![](/assets/drivers.png)

之后就完成了安装, 可以在设备管理器中看到 "Arduino Due Programming Port\(COM13\)"之类的字样.

---

## Reference

[https://www.arduino.cc/en/Guide/ArduinoDue](https://www.arduino.cc/en/Guide/ArduinoDue)

一定去看看...

