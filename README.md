#### 脚本自动检测：一键给PVE增加温度和cpu频率显示，NVME，机械固态硬盘信息

- **理论上适合任何设备**
- **自动适配传感器数据**
- **自动检测NVME硬盘数量**
- **自动检测机械，固态硬盘数量**
- **自动检测CPU核心数量**

#### 使用方法：

可以一键执行下面：

```
(curl -Lf -o /tmp/temp.sh https://raw.githubusercontent.com/NetDoge/PVE-manager-status/main/showtempcpufreq.sh || curl -Lf -o /tmp/temp.sh https://mirror.ghproxy.com/https://raw.githubusercontent.com/NetDoge/PVE-manager-status/main/showtempcpufreq.sh) && chmod +x /tmp/temp.sh && /tmp/temp.sh remod
```

> [!IMPORTANT]
>
> 没有显示功耗的，请执行下面的命令安装依赖，请确保安装成功，就是最后的一行的输出，必须为 “成功!” 才表示安装成功了。

```
apt update ; apt install linux-cpupower && modprobe msr && echo msr > /etc/modules-load.d/turbostat-msr.conf && chmod +s /usr/sbin/turbostat && echo 成功！
```

#### 如果你已经用别人的脚本之类的修改过页面，请先用下面命令先回复官方设置之后，才可以运行本脚本：

```
apt update
apt install --reinstall pve-manager=$(dpkg -l pve-manager | tail -n 1 | awk '{print $3}')
apt install --reinstall proxmox-widget-toolkit=$(dpkg -l proxmox-widget-toolkit | tail -n 1 | awk '{print $3}')
rm -f /usr/share/perl5/PVE/API2/Nodes.pm*bak
rm -f /usr/share/pve-manager/js/pvemanagerlib.js*bak
rm -f /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js*bak
```

> [!TIP]
>
> 另外：每次pve升级之后都需要执行一次脚本，因为升级后PVE会自己还原文件





更新：

- 2023.1.10
  理论上适合任意设备！
  添加nvme硬盘信息显示
- 2023.1.11
  效果优化
  加入固态硬盘和机械硬盘信息
  CPU频率加入调速器，最大最小频率
  NVME加入读写数据量显示
  修复bug
- 2023.1.12
  细节优化
- 2023.1.14
  细节优化
- 2023.1.15
  修正右栏高度和左栏一致，解决双栏浮动布局错位问题
- 2023.1.18
  优化布局，修正温度获取bug
- 2023.4.14
  添加NVME健康度和0E显示
- 2023.9.4
  修复一些设备因为温度问题无限转圈圈
- 2023.9.5
  增加CPU功耗显示
- 2023.12.13
  机械硬盘休眠状态不去获取SMART
