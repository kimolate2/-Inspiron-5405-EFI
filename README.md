# Dell-Inspiron-5405-EFI
戴尔Inspiron 5405安装黑苹果macOS 15 Sequoia [基本可用]
CPU: AMD R5 4500U
网卡：高通QCA6x4a (无法驱动，后更换成了博通BCM94352Z)

按照下面步骤：
1. 使用RapidEFI 4.0配置基础EFI
我使用了Rapid EFI配置了基础EFI, 感谢作者搞了这么傻瓜式的工具的工具。
<img width="1584" height="892" alt="image" src="https://github.com/user-attachments/assets/178640bc-282f-4e24-acf7-7df3a989d6c9" />
工具非常简单，只需要选择好CPU, 平台，AMD和安装系统版本。后面的我选择了默认。前期尽量保证较少的驱动勾选项，不然容易卡码。最后点击“生成EFI”即可。
测试发现能进系统。
2. 修复触控板
触控板没有任何反应，后续查看多篇定制I2C触控板定制SSDT的教程，终于解决了。实际比想象中的简单。
首先需要添加SSDT-XOSI.aml和SSDT-GPIO.aml两个补丁，可以下载通用的
然后需要在屏蔽config.plist里面屏蔽_STA方法，这个方法在通电是会检测系统及额外参数来决定是否启用触控板。可以通过自定义补丁修改成一直启用，但是我发现直接屏蔽更快。
3. 修复WIFI
macOS 15 Sequoia移除了很多旧驱动，所以网上几乎很少的教程。于是翻看了国外的教程后，找到了方法。

