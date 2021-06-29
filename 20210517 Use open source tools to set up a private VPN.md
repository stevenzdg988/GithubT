[#]: subject: (Use open source tools to set up a private VPN)
[#]: via: (https://opensource.com/article/21/5/open-source-private-vpn)
[#]: author: (Lukas Janėnas https://opensource.com/users/lukasjan)
[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

Use open source tools to set up a private VPN
使用开源工具创建私有 VPN
======
Use OpenWRT and Wireguard to create your own virtual private network on
your router.
![scrabble letters used to spell "VPN"][1]
使用 OpenWRT 和 Wireguard 在路由器上创建自己的虚拟专用网络。
![拼写为 “VPN”][1]

Getting from one place to another over a computer network can be a tricky thing. Aside from knowing the right address and opening the right ports, there's the question of security. For Linux, SSH is a popular default, and while there's a lot you can do with SSH it's still "just" a secure shell (that's what SSH stands for, in fact.) A broader protocol for encrypted traffic is VPN, which creates a unique, virtual private network between two points. With it, you can log in to a computer on another network and use all of its services (file shares, printers, and so on) just as if you were physically sitting in the same room, and every bit of data is encrypted from point to point.
通过计算机网络从一个地方到另一个地方可能是一件棘手的事情。除了知道正确的地址和打开正确的端口之外，还有安全问题。 对于 Linux，SSH 是一种流行的默认设置，虽然您可以使用 SSH 做很多事情，但它仍然“只是”一个安全外壳（实际上，这就是 SSH 代表的）。用于加密流量的更广泛的协议是 VPN，它创建了一个独特的两点之间的虚拟专用网络。有了它，您可以登录到另一个网络上的计算机并使用它的所有服务（文件共享、打印机，等等），就像您坐在同一个房间里一样，并且全部的数据都是从点到点加密的。

Normally, in order to make a VPN connection possible, the gateways into each network must accept VPN traffic, and some computer on your target network must be listening for VPN traffic. However, it's possible to run your own router firmware that runs a VPN server, enabling you to connect to your target network without having to worry about forwarding ports or thinking at all about internal topography. My favorite firmware is OpenWrt, and in this article I demonstrate how to set it up, and how to enable VPN on it.
通常，为了使 VPN 连接成为可能，进入每个网络的网关必须接受 VPN 流量，并且必须侦听目标网络上的某些计算机的 VPN 流量。但是，可以运行您自己的运行 VPN 服务器的路由器固件，使您能够连接到目标网络，而无需担心转发端口或完全考虑内部拓扑。我最喜欢的固件是 OpenWrt，在本文中我将演示如何设置它，以及如何启用 VPN。

### What is OpenWrt?什么是 OpenWrt？

[OpenWrt][2] is an open source project that uses Linux to target embedded devices. It's been around for more than 15 years and has a large and active community.
[OpenWrt][2] 是一个使用 Linux 面向嵌入式设备的开源项目。它已经存在超过 15 年，拥有庞大而活跃的社区。

There are many ways to use OpenWrt, but its main purpose is in routers. It provides a fully writable filesystem with package management, and because it is open source, you can see and modify the code and contribute to the ecosystem. If you would like to have more control over your router, this is the system you want to use.
使用 OpenWrt 的方法有很多种，但它的主要用途是在路由器中。它提供了一个具有包管理功能的完全可写的文件系统，并且由于它是开源的，您可以查看和修改代码并为生态系统做出贡献。如果您想对路由器进行更多控制，这就是您想要使用的系统。

OpenWrt supports many routers, including famous brands such as [Cisco][3], [ASUS][4], [MikroTik][5], [Teltonika Networks][6], [D-Link][7], [TP-link][8], [Buffalo][9], [Ubiquiti][10], and [many others][11].
OpenWrt 支持很多路由器，包括 [Cisco][3]，[ASUS][4]，[MikroTik][5]，[Teltonika Networks][6]，[D-Link][7]，[TP-link][8]，[Buffalo][9]，[Ubiquiti][10] 等知名品牌和 [许多其他品牌][11]。

### What is Wireguard?Wireguard 是什么？

[Wireguard][12] is open source virtual private network (VPN) software that is much faster, simpler, and more secure than other options such as OpenVPN. It uses state-of-the-art cryptography: ChaCha20 for symmetric cryptography; Curve 25519 (which uses elliptic curves) for key agreement; and BLAKE2 for hashing. These algorithms are designed in a way that is efficient on embedded systems. WIreguard is also available on a wide variety of operating system [platforms][13].
[Wireguard][12] 是开源虚拟专用网络 (VPN) 软件，它比 OpenVPN 等其他选项更快、更简单且更安全。它使用最先进的密码学：ChaCha20 用于对称密码学；用于密钥协商的曲线 25519（使用椭圆曲线）；和用于散列的 BLAKE2 。这些算法的设计方式在嵌入式系统上是高效的。WIreguard 也可用于各种操作系统[平台][13]。

### Prerequisites先决条件

For this project, you will need:

  * [Teltonika RUT955][14] or another router supported by OpenWrt
  * A public IP address to connect to your VPN from outside your network
  * An Android phone
对于这个项目，你需要：

   * [Teltonika RUT955][14] 或支持 OpenWrt 的其他路由器
   * 用于从外部网络连接到 VPN 的公网 IP 地址
   * 一部安卓手机

### Install OpenWrt安装 OpenWrt

To get started, download the OpenWrt image for your router. Use the [firmware selector][15] to check if OpenWrt supports your router and download the firmware. Enter your router's model, and it will show your options:
首先，下载路由器的 OpenWrt 镜像。使用[固件选择器][15]检查 OpenWrt 是否支持您的路由器并下载固件。输入您的路由器型号，将显示选项：

![OpenWRT 固件选择器][16]

(Lukas Janenas, [CC BY-SA 4.0][17])

Select the firmware version you want to download by using the drop-down input on the right side of the search box.
使用搜索框右侧的下拉输入选择要下载的固件版本。

Download the factory image.下载出厂镜像。

![下载出厂镜像][18]

(Lukas Janenas, [CC BY-SA 4.0][17])

Many routers allow you to flash unauthorized firmware from the web interface, but Teltonika Networks does not. To flash the OpenWrt firmware to a router like this, you need to use the bootloader. To do so, follow these steps:
许多路由器允许您从 Web 界面刷入未经授权的固件，但 Teltonika Networks 不允许。要将 OpenWrt 固件刷入这样的路由器，您需要使用引导加载程序。为此，请按照下列步骤操作：

  1. Unplug the router's power cable.
  2. Press and hold the Reset button.
  3. Plug in the router's power cable.
  4. Continue holding the reset button for 5 to 8 seconds after you plug the power cable in.
  5. Set computer's IP address to `192.168.1.15` and the netmask to `255.255.255.0`.
  6. Connect the router and your computer with an Ethernet cable over a LAN port.
  7. Open a web browser and enter `192.168.1.1:/index.html`.
  8. Upload and flash the firmware.
  1. 拔掉路由器的电源线。
  2. 按住重置按钮。
  3. 插入路由器的电源线。
  4. 插入电源线后，继续按住重置按钮 5 到 8 秒。
  5. 将计算机的 IP 地址设置为 `192.168.1.15`，将网络掩码设置为 `255.255.255.0`。
  6. 使用以太网电缆通过 LAN 端口连接路由器和计算机。
  7. 打开网页浏览器并输入`192.168.1.1:/index.html`。
  8. 上传并刷写固件。

The flashing process can take up to three minutes. Afterward, you should be able to reach the router's web interface by entering `192.168.1.1` in a browser. There is no password set by default.
刷机过程可能占用三分钟。之后，您应该可以通过在浏览器中输入 `192.168.1.1` 来访问路由器的 Web 界面。 默认情况下没有设置密码

![OpenWrt 授权][19]

(Lukas Janenas, [CC BY-SA 4.0][17])

### Configure network connectivity配置网络连接

Network connectivity is a requirement. If your Internet service provider (ISP) assigns your IP address automatically using DHCP, you just need to plug your Ethernet cable into the WAN port of your router.
网络连接是必要条件。如果您的 Internet 服务提供商 (ISP) 使用 DHCP 自动分配您的 IP 地址，您只需将以太网电缆插入路由器的 WAN 端口。

If you need to assign the IP address manually, navigate to **Network → Interfaces**. Select **Edit** to edit your WAN interface. From the **Protocol** field, select **Static address**, and select **Switch protocol**.
如果您需要手动分配 IP 地址，导航至  **Network → Interfaces**。选择 **Edit** 编辑您的 WAN 接口。从 **Protocol** 字段中，选择 **Static address**，然后选择 **Switch protocol**。

![手动分配 IP 地址][20]

(Lukas Janenas, [CC BY-SA 4.0][17])

In the **IPv4 address** field, enter your router's address. Set **IPv4 netmask** to match your network subnet; enter the **IPv4 gateway** address you will use to connect to the network; and enter the DNS server's address in the **Use custom DNS servers** field. Save the configuration.
在 **IPv4 address** 字段中，输入您的路由器地址。设置 **IPv4 netmask** 以匹配您的网络子网；输入您将用于连接到网络的 **IPv4 gateway** 地址； 并在 **Use custom DNS servers** 字段中输入 DNS 服务器的地址。保存配置。

That's it! You have successfully configured your WAN interface to get network connectivity.
就是这样！您已成功配置 WAN 接口以获得网络连接。

### Install the necessary packages安装必要的包

The firmware doesn't include many packages by default, but OpenWrt has a package manager with a selection of packages you can install. Navigate to **System → Software** and update your package manager by selecting **Update lists…**
默认情况下，固件不包含很多包，但 OpenWrt 有一个选择可安装的包管理器。导航到 **System → Software** 并通过选择 **Update list...** 更新您的包管理器。

![OpenWrt 包管理器][21]

(Lukas Janenas, [CC BY-SA 4.0][17])

In the Filter input, type **Wireguard**, and wait until the system finds all the packages that include this keyword. Find and install the package named **luci-app-wireguard**.
在过滤器输入中，键入 **Wireguard**，等待系统找到所有包含该关键字的包。找到并安装名为 **luci-app-wireguard** 的包。

![luci-app-wireguard 包][22]

(Lukas Janenas, [CC BY-SA 4.0][17])

This package includes a web interface to configure Wireguard and installs all the dependencies necessary for Wireguard to work.
该软件包包括一个用于配置 Wireguard 的 Web 界面，并安装 Wireguard 所必需的所有依赖项。

If you get a warning that a package is missing and can't be found in the repositories before installing the Wireguard package, just ignore it and proceed.
如果您在安装 Wireguard 软件包之前收到一个软件包丢失的警告并且在存储库中找不到，请忽略它并继续。

Next, find and install the package named **luci-app-ttyd**. This will be used to access the terminal later.
接下来，找到并安装名为 **luci-app-ttyd** 的包。这将用于稍后访问终端。

After these packages are installed, reboot your router for the changes to take effect.
安装这些软件包后，重新启动路由器以使更改生效。

### Configure the Wireguard interface配置 Wireguard 接口

Next, create the Wireguard interface. Navigate to **Network → Interfaces** and select **Add new interface…** on the bottom-left. In the pop-up window, enter your desired name for the interface, choose **Wireguard VPN** from the drop-down list, and select **Create interface** on the lower-right.
接下来，创建 Wireguard 接口。导航到 **Network → Interfaces** 并选择左下角的 **Add new interface...**。在弹出窗口中，输入您想要的接口名称，从下拉列表中选择 **Wireguard VPN**，然后选择右下角的 **Create interface**。

![创建 Wireguard 接口][23]

(Lukas Janenas, [CC BY-SA 4.0][17])

In the new pop-up window, select **Generate Key** to generate a private key for the Wireguard interface. In the **Listen Port** field, enter your desired port. I will use the default Wireguard port, **51820**. In the **IP Addresses** field, assign the IP address which will be used for the Wireguard interface. In this example, I use `10.0.0.1/24`. The number **24** indicates the size of my subnet.
在新弹出的窗口中，选择 **Generate Key** 为 Wireguard 接口生成私钥。在 **Listen Port** 字段中，输入所需的端口。我将使用默认的 Wireguard 端口，**51820**。在 **IP Addresses** 字段中，分配将用于 Wireguard 接口的 IP 地址。在这个例子中，我使用了 `10.0.0.1/24`。数字 **24** 表明我的子网的大小。

![创建 Wireguard 接口][24]

(Lukas Janenas, [CC BY-SA 4.0][17])

Save the configuration and restart the interface.
保存配置并重启接口。

Navigate to **Services → Terminal**, log into the shell, and enter the command `wg show`. You will see some information about your Wiregaurd interface, including its public key. Copy down the public key—you will need it to create peers later.
导航到 **Services → Terminal**，登录到 shell，然后输入命令 `wg show`。您将看到有关 Wiregaurd 接口的一些信息，包括其公钥。复制公钥——稍后您将需要它来创建对等点。

![Wireguard 公钥][25]

(Lukas Janenas, [CC BY-SA 4.0][17])

### Configure the firewall配置防火墙

Navigate to **Network → Firewall** and select the **Traffic Rules** tab. On the bottom of the page, select **Add**. In the **Name** field of the pop-up window, give your rule a name, e.g., **Allow-wg**. Next, change the **Destination zone** from **Lan** to **Device**, and set the **Destination port** to 51820.
导航到 **Network → Firewall** 并选择 **Traffic Rules** 选项卡。在页面底部，选择 **Add**。在弹出窗口的 **Name** 字段中，为您的规则命名，例如 **Allow-wg**。接下来，将 **Destination zone** 从 **Lan** 更改为 **Device**，并将 **Destination port** 设置为 51820。

![Wireguard 防火墙设置][26]

(Lukas Janenas, [CC BY-SA 4.0][17])

Save the configuration.保存配置。

### Configure Wireguard on an Android phone在 Android 手机上配置 Wireguard

Install the [Wireguard app][27] on your phone from Google Play. Once it's installed, open the app and create a new interface from scratch. In the **Name** field, enter the name you want to use for your interface. In the **Private key** field, press the double-arrow icon on the right to generate a key pair. You will need the public key from above to create a peer between your phone and router. In the **Addresses** field, assign the IP address you will use to reach the phone over VPN. I will use `10.0.0.2/24`. In **Listen port**, enter a port; I will again use the default port.
从 Google Play 在您的手机上安装 [Wireguard 应用程序][27]。安装后，打开应用程序并从头开始创建一个新接口。在 **Name** 字段中，输入要用于接口的名称。在 **Private key** 字段中，按右侧的双箭头图标生成密钥对。您将需要上面的公钥来在您的手机和路由器之间创建一个对等点。在 **Addresses** 字段中，分配您将用于通过 VPN 访问电话的 IP 地址。我将使用 `10.0.0.2/24`。在 **Listen port**中，输入端口；我将再次使用默认端口。

![在 Android 上设置 VPN 接口][28]

(Lukas Janenas, [CC BY-SA 4.0][17])

Save the configuration.保存配置。

To add a peer to the configuration, select **Add peer**. In the **Public key** field, enter your router's Wireguard public key. In the **Endpoint** field, enter your router's public IP address and port separated by a colon, e.g., `12.34.56.78:51820`. In the **Allowed IP**s field, enter the IP addresses you want to reach through the Wireguard interface. (You can enter your router's VPN interface IP address and LAN interface address.) The IP addresses must be separated by commas. You can also define the size of the subnet.
要向配置中添加对等点，请选择 **Add peer**。在 **Public key** 字段中，输入路由器的 Wireguard 公钥。在 **Endpoint** 字段中，输入路由器的公共 IP 地址和端口，以冒号分隔，例如 `12.34.56.78:51820`。在 **Allowed IP** 字段中，输入要通过 Wireguard 接口访问的 IP 地址。 （您可以输入路由器的 VPN 接口 IP 地址和 LAN 接口地址。）IP 地址必须用逗号分隔。您还可以定义子网的大小。

![在 Android 上添加 VPN 对等点][29]

(Lukas Janenas, [CC BY-SA 4.0][17])

Save the configuration.保存配置。

There's one last step left in the configuration: adding a peer on the router.
配置中还剩下最后一步：在路由器上添加一个对等点。

### Add a peer on the router在路由器上添加一个对等点

Navigate to **Network → Interfaces** and select your Wireguard interface. Go to the **Peers** tab and select **Add peer**. In the **Description** field, enter the peer's name. In the **Public Key** field, enter your phone's Wireguard interface public key, and in the **Allowed IPs** field, enter your phone's Wireguard interface IP address. Check the **Route Allowed IPs** checkbox.
导航到 **Network → Interfaces** 并选择您的 Wireguard 接口。转到 **Peers** 选项卡并选择 **Add peer**。 在 **Description** 字段中，输入对等方的名称。在 **Public Key** 字段中输入手机的 Wireguard 接口公钥，在 **Allowed IPs** 字段中输入手机的 Wireguard 接口 IP 地址。选中 **Route Allowed IPs** 复选框。

![Adding a peer on the router][30]

(Lukas Janenas, [CC BY-SA 4.0][17])

Save the configuration and restart the interface.
保存配置并重启接口。

### Test the configuration测试配置

Open a web browser on your phone. In the URL bar, enter the IP address `10.0.0.1` or `192.168.1.1`. You should be able to reach your router's website.
在手机上打开网络浏览器。在 URL 栏中，输入 IP 地址 `10.0.0.1` 或 `192.168.1.1`。您应该能够访问路由器的网站。

![从 Android 登录 VPN][31]

(Lukas Janenas, [CC BY-SA 4.0][17])

### Your very own VPN您自己的 VPN 

There are lots of VPN services being advertised these days, but there's a lot to be said for owning and controlling your own infrastructure, especially when that infrastructure only exists to boost security. There's no need to rely on somebody else to provide you with a secure connection to your data. Using OpenWrt and Wireguard, you can have your own open source VPN solution.
这些天有很多 VPN 服务商在做广告，但是拥有和控制自己的基础设施还有很多话要说，尤其是当该基础设施仅用于提高安全性时。无需依赖其他人为您提供安全的数据连接。使用 OpenWrt 和 Wireguard，您可以拥有自己的开源 VPN 解决方案。

--------------------------------------------------------------------------------

via: https://opensource.com/article/21/5/open-source-private-vpn

作者：[Lukas Janėnas][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/lukasjan
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/vpn_scrabble_networking.jpg?itok=pdsUHw5N (scrabble letters used to spell "VPN")
[2]: https://openwrt.org/
[3]: https://www.cisco.com/c/en/us/products/routers/index.html
[4]: https://www.asus.com/Networking-IoT-Servers/WiFi-Routers/All-series/
[5]: https://mikrotik.com/
[6]: https://teltonika-networks.com/
[7]: https://www.dlink.com/en/consumer
[8]: https://www.tp-link.com/us/
[9]: https://www.buffalotech.com/products/category/wireless-networking
[10]: https://www.ui.com/
[11]: https://openwrt.org/toh/views/toh_fwdownload
[12]: https://www.wireguard.com/
[13]: https://www.wireguard.com/install/
[14]: https://teltonika-networks.com/product/rut955/
[15]: https://firmware-selector.openwrt.org/
[16]: https://opensource.com/sites/default/files/uploads/openwrt_firmware-selector.png (OpenWRT firmware selector)
[17]: https://creativecommons.org/licenses/by-sa/4.0/
[18]: https://opensource.com/sites/default/files/uploads/downloadfactoryimage.png (Downloading the Factory Image)
[19]: https://opensource.com/sites/default/files/uploads/openwrt_authorization.png (OpenWrt authorization)
[20]: https://opensource.com/sites/default/files/uploads/openwrt_staticaddress.png (Assigning IP address manually)
[21]: https://opensource.com/sites/default/files/uploads/openwrt_update-lists.png (OpenWrt package manager)
[22]: https://opensource.com/sites/default/files/uploads/wireguard-package.png (luci-app-wireguard package)
[23]: https://opensource.com/sites/default/files/uploads/wireguard_createinterface.png (Creating Wireguard interface)
[24]: https://opensource.com/sites/default/files/uploads/wireguard_createinterface2.png (Creating Wireguard interface)
[25]: https://opensource.com/sites/default/files/uploads/wireguard_publickey.png (Wireguard public key)
[26]: https://opensource.com/sites/default/files/uploads/wireguard-firewallsetup.png (Wireguard firewall setup)
[27]: https://play.google.com/store/apps/details?id=com.wireguard.android&hl=lt&gl=US
[28]: https://opensource.com/sites/default/files/uploads/vpn_inferfacesetup.png (Setting up VPN interface on Android)
[29]: https://opensource.com/sites/default/files/uploads/addpeeronphone.png (Adding a VPN peer on an Android)
[30]: https://opensource.com/sites/default/files/uploads/addpeeronrouter.png (Adding a peer on the router)
[31]: https://opensource.com/sites/default/files/uploads/android-vpn-login.png (Logging into the VPN from Android)
