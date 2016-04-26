title: Win10下使用Cisco VPN Client出现442报错
date: 2015-12-24 11:34:37
tags: [Win10,Cisco,VPN]
---

拨号的时候出现: vpn 422 failed to enable virtual adapter 
运行regedit打开注册表编辑器

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\CVirtA 找到 DisplayName 项目

X86的系统将原内容
```
@oem16.inf,%CVirtA_Desc%;Cisco Systems VPN Adapter 
```
修改为 Cisco Systems VPN Adapter

X64的系统将原内容
```
@oem16.inf,%CVirtA_Desc%;Cisco Systems VPN Adapter for 64-bit Windows 
```
修改 Cisco Systems VPN Adapter for 64-bit Windows

原内容可能与例子不完全一致,反正最终意思就是保留Cisco这一段.