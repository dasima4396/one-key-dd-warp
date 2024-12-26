# Linux dd脚本
![](https://raw.githubusercontent.com/leitbogioro/Tools/master/imgs/1.png)

![](https://raw.githubusercontent.com/leitbogioro/Tools/master/imgs/2.png)

## 下载
<pre><code>wget --no-check-certificate -qO InstallNET.sh 'https://raw.githubusercontent.com/dasima4396/Tools/master/Linux_reinstall/InstallNET.sh' && chmod a+x InstallNET.sh</code></pre>
### Debian 12
<pre><code>bash InstallNET.sh -debian</code></pre>
### Alpine Linux Edge
<pre><code>bash InstallNET.sh -alpine</code></pre>
<b>Alpine Linux适合低配置小鸡，至少256MB运存.</b>
### AlmaLinux 9
<pre><code>bash InstallNET.sh -almalinux</code></pre>
### Ubuntu 22.04
<pre><code>bash InstallNET.sh -ubuntu</code></pre>
### Windows 11 Pro for Workstations
<pre><code>bash InstallNET.sh -windows</code></pre>

## SSH 和 RDP 的默认配置
### 默认用户名
Linux: root
<br />
<br />
Windows: Administrator
### 默认密码
Linux: LeitboGi0ro
<br />
<br />
Windows: Teddysun.com
### 默认端口
Linux: 不变
Windows: 3389
**-alpine 3.16-3.18/edge**: 推荐"edge" .
**-windows 10/11/2012/2016/2019/2022**: 
其他win版本:
- Windows 10 Enterprise LTSC 22H2中文
- Windows 11 Pro for Workstation 22H2 for simplified Chinese中文
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server 2019
- Windows Server 2022
<br />
<b>安装win命令 "bash InstallNET.sh -windows 版本号" 支持 IPv4/IPv6 dhcp or static
<br />
<br />
<b> 所有的win文件都在https://dl.lamp.sh/vhd/ 
**-lang/-language "cn, en or jp"**:
设置语言: -windows 10 -lang "en"
<br />
<br />
**-port ""**: 设置端口,范围1~65535
**-pwd/-password ''**: 设置密码，默认为'LeitboGi0ro'
<br />
<br />

**-swap/-virtualmemory/-virtualram "number, 单位 MB"**: 默认为 "0" 不设置swap。可用命令" -swap '1024' "设置1g的swap.
<br />
<br />
**--network "dhcp/auto" or "static/manual"**: 默认使用的网络形式，等同于 --ip-addr "" --ip-mask "" --ip-gate "", 该命令和上面三个只能二选一，而且必须在命令行最后面。
<br />
<br />

**--networkstack "ipv4", "ipv6" or "dual"**: 通过读取相关配置手动指定一个受支持的 IP 栈，而不是检查 IP 栈的连接性、"ipv4"表示IPv4, "ipv6"IPv6, "dual"表示双栈.
<br />
<br />

**--ip-addr "IPv4 address"**: 必须和--ip-gate and --ip-mask 一起, 在这种情况下, --network "static/manual" 自动设置.
<br />
<br />

**--ip-gate "IPv4 gateway"**: 必须和--ip-addr 以及 --ip-mask 一起
<br />
<br />

**--ip-mask "IPv4 subnet musk"**: 必须和--ip-addr 以及 --ip-gate 一起
<br />
<br />

**--ip-dns "IPv4 DNS server"**: 静态网络配置，默认为1.0.0.1 and 8.8.4.4可改为8.8.8.8等. 如果网络是DHCP, 就不要用!
<br />
<br />

**--ip6-addr "IPv6 address"**: 必须和--ip6-gate 以及 --ip6-mask 一起, 这种情况下--network "static/manual" 默认.
<br />
<br />

**--ip6-gate "IPv6 gateway"**: 必须和--ip6-addr 以及 --ip6-mask 一起
<br />
<br />

**--ip6-mask "IPv6 subnet musk"**: 必须和--ip6-addr 以及 --ip6-gate一起. IP计算网站: https://en.rakko.tools/tools/27/
ip6并没有ip4的子网掩码，它叫做前缀长度。比如/64或者/128
<br />
<br />

**--ip6-dns "IPv6 DNS server"**: 只用于静态网络配置，可自定义dns地址。
<br />
<br />

**--setipv6 "0 is disabled"**: 默认会开启ipv6,如果机子是Racknerd 或者 Virmach等只有ip4的话，他们会为 IPv4 协议栈服务器提供 IPv6 DNS，服务器将优先访问无效的 IPv6 网络，而不是 IPv4 优先，您需要移除 IPv6 modules通过命令 --setipv6 "0" 避免这种情况。
<br />
<br />

如果ip4或者6没有启动的话可通过命令手动开启
<pre><code>dhclient -6 "network adapter name"</pre></code>
<pre><code>dhclient -4 "network adapter name"</pre></code>

## 示例
<pre><code>bash InstallNET.sh -debian/kali/ubuntu/centos/almalinux/rockylinux/fedora(os type) 11(os version) -architecture 64 -port "端口" -pwd '密码' -mirror "链接" -filetype "gz or xz" -timezone "like Asia/Tokyo etc" --network "static"/--ip-addr 'x.x.x.x'(ip address) --ip-mask 'x.x.x.x'(subnet mask) --ip-gate 'x.x.x.x'(gateway) -firmware(Debian with hardware drivers)</code></pre>

- 脚本支持IPv6only机器只能用DHCP.
- 支持自动配置ip4/6，无需手动更改。仅支持Debian, DHCP.
- 自动检查网络是DHCP 还是 static

# 萌咖的dd脚本
据说dd ipv6 only的机器会失联，改天验证一下。
安装命令：
```bash
bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/dasima4396/Tools/master/InstallNET.sh') -d 12 -v 64 -a -p xxx -port 4598
```
-a表示自动安装，-p后面是密码 -d表示debian12。
dd ipv6 only机器要固定ip地址，命令为：
```bash
bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/dasima4396/Tools/master/InstallNET.sh') -a -d 12 -v 64 -p '自定义' -port 自定义 --ip-addr 2001:ae8:120:3a::1/64 --ip-gate 2001:258:250:3b:: --ip-mask 255.255.255.254 --ip-dns 2001:67c:2b0::4
```
上面的ip和gateway必须是网页上的。dns是nat64,能访问ip4
