title: cisco 2504 wireless controller 基本设定
date: 2016-05-15 09:10:18
tags: Cisco
categories:
---
控制器为 cisco 2504 wireless controller  
建议把固件版本更新到 Software Version 8.0  
ip：10.24.1.254 / 255.255.255.0  
GW ：10.24.1.1  
DNS : 8.8.8.8  
两个SSID :  Office 及 VIP  
WPA+WPA2密码验证


AP共有9台
自动分配IP
<!--more-->首先要对Controller做基本配置如下

```
Would you like to terminate autoinstall? [yes]: yes
System Name [Cisco_be:72:24] (31 characters max): WLC2504
Enter Administrative User Name (24 characters max): cisco
Enter Administrative Password (3 to 24 characters): ********
Re-enter Administrative Password                 : ********

Enable Link Aggregation (LAG) [yes][NO]: yes
Management Interface IP Address: 10.24.1.254
Management Interface Netmask: 255.255.255.0
Management Interface Default Router: 10.24.1.1

Cleaning up Provisioning SSID

Error: failed to disable Day0 ssid. return Code : 7

Management Interface VLAN Identifier (0 = untagged): 0
Management Interface DHCP Server IP Address: 192.168.0.2

Virtual Gateway IP Address: 1.1.1.1

Multicast IP Address: 239.0.1.1

Mobility/RF Group Name: ContosoGroup

Network Name (SSID): Office

Configure DHCP Bridging Mode [yes][NO]: no

Allow Static IP Addresses [YES][no]: yes

Configure a RADIUS Server now? [YES][no]: no
Warning! The default WLAN security policy requires a RADIUS server.
Please see documentation for more details.

Enter Country Code list (enter 'help' for a list of countries) [US]: TW

Enable 802.11b Network [YES][no]: yes
Enable 802.11a Network [YES][no]: yes
Enable 802.11g Network [YES][no]: yes
Enable Auto-RF [YES][no]: yes
Enter the date in MM/DD/YY format: 10/08/15
Enter the time in HH:MM:SS format: 09:05:35
Would you like to configure IPv6 parameters[YES][no]: no

Configuration correct? If yes, system will save it and reset. [yes][NO]: yes
Cleaning up Provisioning SSID

Configuration saved!
Resetting system with new configuration...

Configuration saved!
Resetting system with new configuration...
重新开机过程略
Starting mDNS Services: ok
Starting Management Services: 
   Web Server:    CLI:    Secure Web: ok

(Cisco Controller) 

Enter User Name (or 'Recover-Config' this one-time only to reset configuration to factory defaults)

User:

```
利用浏览器连线到10.24.1.254，并登入刚刚设定的帐号及密码


点选左上方的Advance


接着要修改SSID的验证方式，请点选WLANs页面 -> WLAN ID 的数字 1的地方


General页面中的Broadcast SSID 要勾选


Security -> Layer 2 -> WPA Policy 及 WPA Encryption TKIP 要勾以及Authentication Key Management 要改选择PSK 然后输入Pre-Share Key



设定完之后请点选右上Apply

新增另一个SSID Name，点选右边的Create NEW


输入另一个SSID Name : VIP，然后点选左上角的Apply

接着把 VIP的status勾选起来

设定VIP SSID的 安全性，页面选择Security -> Layer 2 -> WPA Policy 及 WPA Encryption TKIP 要勾以及Authentication Key Management 要改选择PSK 然后输入Pre-Share Key


 
按下画面右上角的Apply 套用及右上的Save Config，完成SSID新增的工作

登入Controller 后，在WLANs -> WLAN ID下的数字 -> 在点选QoS 页面 -> 把Application Visibility  Enabled勾选起来，在Monitor页面才会显示通讯种类 




在WIRELESS -> Access Points -> All APs -> Radios -> 802.11a/n/ac -> 选择要调整的AP 右边的Config选项

 将频宽选到 80MHz，另一个选项 Assignment Method 则改成Custom 选择其中一个(153,149,157,161)  当AP位置靠的越近，频率一定要调开，不然会干扰，若多个AP，则是AP位置离的越远，频率可以重复，由于距离变远了，即使频率相同，干扰会减少 

另外，如果内部网路已经确定没有802.11ab的无线网卡的话，可以把一些用不到的频率关掉，以减少干扰
从WIRELESS -> 802.11a/n/ac -> High Throughput (802.11n/ac) 把右手边54M 以下的通通关掉 

本文参考： [新竹资讯黑手的维修记录][1]


[1]:http://kbwangtw.blogspot.mx/
