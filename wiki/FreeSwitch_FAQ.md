---
layout: default
title: FreeSWTICH FAQ
---

# FreeSWITCH FAQ

基于<http://wiki.freeswitch.org/wiki/FreeSwitch_FAQ> 2010-05-01.

## 基本问题
### 啊，你们提供了一个如此强大的系统，那你们有什么心愿吗？

这里有每个开发者的 Wishlist：

* Anthony Minessale (anthm) - <http://www.amazon.com/gp/registry/wishlist/1NQC79YV4RB83>
* Mike Jerris (MikeJ) - <http://www.amazon.com/gp/registry/wishlist/1ELF2W9FAIN2N>
* Brian West (bkw_) - <http://www.amazon.com/gp/registry/wishlist/1BWDJUX5LYQE0>
* Raymond Chandler ([intra]lanman) - <http://www.amazon.com/gp/registry/wishlist/27XDISBBI4NOU>


### 在 sofia 呼叫字符串中，% 和 @ 有何不同？
这很简单，你可以有多种选择。如果 domain 是一个 profile 的别名，那你你可以用 sofia/domain\_name/user；如果 domain 不是别名，那可你可以使用 sofia/profile\_name/user%domain；但如果你想呼叫一个远端的 SIP URI，并且对方不需要认证，那么你可以直接使用 sofia/profile\_name/remoteuser@remoteip

### ${var} 与 $${var} 有何不同？

${var} 回在每次执行到 dialplan 时进行扩展，而 $${var} 则是在模块加载或 reloadxml 时一次性扩展的。更详细的信息见 conf/vars.xml 中的注释。

### set 和 export 程序有何区别？

set 在当前 channel 上设置变量，而 export 在（a-leg 和 b-leg） 两个 channel 上都设置。当然，你也可以只在 b-leg 上设置，如：
    <action application="export" data="nolocal:foo=bar"/>
### PBX 与 软交换的区别是什么？只是语义问题吗？

一个 PBX 通常用于公司内部提供小型的语音信箱、分机、电话会议等服务。它主要关注于不同的分机间能互相通信。

而一个软交换是一个连接多种网络的设备，通常可以路由不同协议的电话，把电话从一个终端路由到另一个终端（如一个PBX设置）。当然 FreeSWITCH 也可以做为一个 PBX 使用，但它的功能远不止于此。FreeSWITCH 可以装载很多不同的模块，运行起来相当于一个包含好多 PBX 的集群。通常的 PBX 都将全部 PBX 功能置于单一的核心中，这使用它们在想用作软交换时比 FreeSWITCH 要困难地多。

### FreeSWITCH™  是用什么语言写的？

很多种语言。核心是用 C 写的。大部分的模块是 C 和 C++。某些模块则使用了其它一些语言，包括但不限于 JavaScript/ECMAScript、Lua、Perl、 Python、Ruby、Java 和 .NET。

### 你怎么评价你已前做过的 Asterisk 开发？

那些工作并没有白费。我有时还在使用它，甚至有时我还提供这方面的咨询服务。我花了很多年贡献代码，我也为 Asterisk 开发了许多第三方的模块，现在在我的 [asterisk stuff](http://www.freeswitch.org/node/50) 页面还可以找到。我只是简单地认为 FreeSWITCH 代理电话的未来。

### FreeSWITCH 能做什么？

FreeSWITCH 终点模块实现了 SIP, IAX2, H.323 (with OPAL), Skype, Jingle (Google Talk), 声卡（通过 mod_portaudio）以及 TDM 语音卡（Sangoma 或 Zaptel 兼容卡）。你可以把它用做一个 VoIP通信服务器，协议转换网关，以及执行由JavaScript、Perl、Lua 或 C# 写的 IVR 语音菜单脚本。它有一个事件引擎可以通知你任何正在发生的事件，还有 XML RPC接口，你可以用它通过 HTTP 与 系统核心进行交互。

有一个用于读取数据的抽象层，它支持 XML、外部的 HTTP服务器、INI文件，以及目录查询（如LDAP）等。拨号计划通过 XML 与 Perl 兼容的正则表达式的结合对电话进行路由。

### 什么？你刚才说它还可以也 Google Talk 通信？

是的，2006 年3 月我自己写了一个 XMPP 电话信令库与 Google 的 Google Talk 进行通信，你可以用一个 Jabber 账号同时与任意多路 Google Talk 客户端通话，当然也可以像 SIP 或 H.323 那样实现 IVR。如果通信的两端都是 FreeSWITCH, 你还可以绕过 NAT 发送扩展的数据，如 Caller ID 和 DNIS。这里有一个关于 Google Talk 与 SIP 电话通信的教程： <http://www.alijawad.org/cms/index.php?option=com_content&task=view&id=21&Itemid=2>。

### 有人将 FreeSWITCH 用于生产环境吗？

是的。

### 它同时支持多少路通话？有基准测试吗？

这依赖于你的程序以及配置。你需要用你的程序进行压力测试来获取你的极限。你所能做的完全依赖于你的需求。请不要在 FreeSWITCH 邮件列表中问这样的问题，因为你总是会得到相同的官方回答：“我们只对每一个特定的 FreeSWITCH 部署进行基准测试，因为不同的部署方式会得到不同的值。如果你需要，你可以获取该项目的商业支持。我们曾经历过回答这种问题的教训，所以我们的策略是不在公共的论坛上对该问题发表任何意见”。

### 你们做该项目多久了？

最早的发行版本是在 2006 年，只能做少的功能。实际上我从 2005 年 10 月起就利用业余时间开发。

### 什么时候才有第一个真正的发行版？

第一个真正的发行版是版本 1.0.0，发行于 2008 年 5 月 26 日， 星期一。后来，有来其它的 5 个发行版。现在最新的版本是 1.0.6，发布于 2010 年 6 月。所有发行版可以在我们的[文件服务器](http://files.freeswitch.org/)上找到。

### 什么是 ClueCon？

[ClueCon](http://www.cluecon.com) 是电话系统开发者的年度盛会，在芝加哥举行。会上会有来自不同的 VoIP 项目的领袖及其它开发者展示、讨论及交流意见. 它为期三天，是一个绝好的机会可以在白天交流技术，晚上则享受芝加哥的美景。
                                       
### 什么电话能在 FreeSWITCH 下工作？                           
见 Interop List：<http://wiki.freeswitch.org/wiki/Interop_List>
   
### FreeSWITCH 一定要以 root 用户运行吗？
不。

## 获取帮助

### 有帮助文档吗？
是的，我们的 wiki 上有超过 500 页的文档：<http://wiki.freeswitch.org/wiki/Documentation>。也有中文的文档在：<http://www.freeswitch.org.cn/document>。                                       

### 你们支持 IRC 吗？Q: Do you guys support IRC?
是的。志愿者和 FreeSWITCH 专家聚集在 irc.freenode.net 上的 #freeswitch 频道。你可以使用很多 ICR 客户端，如 mIRC for Windows、Limechat for Mac/OSX、Irssi 或 XChat for Unix 类的系统、ChatZilla for Mozilla 浏览器或任何其它标准的 IRC 程序。在里面，我们主要说英语，不过，我们确实有一个支持多种语言的自动的翻译服务。

### 是否有一个电话会议系统我可以参与有关 FreeSWITCH 的讨论呢？

是的。我们支持多种方式呼叫我们。以下的方式都会到同一个地方：
    SIP: 888@conference.freeswitch.org
    H.323: 888@conference.freeswitch.org
    Google Talk/Jingle: freeswitch@gmail.com
    Google Talk/Jingle: 888@jabber.asterlink.com
    IAX: guest@conference.freeswitch.org/888

### 是否有邮件列表？

当然，请到 <http://lists.freeswitch.org> 登记。

## 调试与排错

### 有没有关于排错与汇报 BUG 的指南？我该从哪里开始呢？

从这里开始，Reporting Bugs - <http://wiki.freeswitch.org/wiki/Reporting_Bugs>，它会回答你很多问题。

### 当我从 FreeSWITCH 呼叫 Snome 电话时，在控制台上看到 "a=crypto in RTP/AVP, refer to RFC 3711"，怎么办？

您需要到 Snome 的配置界面，identity-\>rtp，并把 RTP/SAVP 设成 optional。

### 我的 FreeSWITCH 不影响任何 SIP 请求，我也用 tcpdump 检查了，发送端的正常的，但 FreeSWITCH 就是没有反应，怎么回事呢？

一般来说是你的防墙惹得祸，在 tcpdump 中能看到防火墙之外的数据包，你最好关掉防火墙试试，如“service iptables stop” 或“/etc/init.d/iptables stop”。

### 我刚装好了 FreeSWITCH，但在启动的时候显示错误：SQL ERR[no such table: \<table_name\>

通常这条信息之后会有一条“Auto Generating Table!”的信息。那说明这是正常的。因为你是第一次使用，当 FreeSWITCH 找不到 sqlite 数据库或表时，它会自己创建。只要以后重启 FreeSWITCH 时不再出此错误，就没事。

### show channels、conference list、以及其它控制台命令什么也显示不出来。

可能是核心数据库的结构乱了，这些命令都是从数据库中获取数据，删掉所有数据库（在Linux/Unix上用 rm -rf /usr/local/freeswitch/db/\*）重启 FreeSWITCH 试试看。

### 我在 Win32 上装了 FreeSWITCH 但是不能启动，我应该检查什么？
你需要 msvcr80d.dll ，它应该在你系统 system 或 system32 目录中已经存在的。如果你找不到这个 dll，那么你可以试试安装 Microsoft Visual C++ 2005 Redistributable 包。

### 如何调试 SIP？

参见：<http://wiki.freeswitch.org/wiki/Debugging_Freeswitch> 及 <http://wiki.freeswitch.org/wiki/Sofia>。

### 如何带 debug 符号编译 FreeSWITCH ？

    export CFLAGS="-g -ggdb"
    export MOD_CFLAGS="-g -ggdb"
    ./configure
    make megaclean （如果所有它依赖的库都需要 debug 的话， 或者）
    make sure （如果只需要 FreeSWITCH）
    
### 我收到 “Invalid Application \<name\>” 是什么意思？

该错误最可能的原因是你没有加载正确的模块。

### mod_spidermonkey_odbc 出错：::Error SQLConnect=-1 errno=0 [unixODBC][Driver Manager]Data source name not found, and no default driver specified

确认你的 ODBC 驱动（odbc.ini）及数据源（odbcinst.ini）在 /usr/local/freeswitch/etc 目录下，（这些文件通常在 /etc 目录，做个符号链接就行）。参见：<http://wiki.freeswitch.org/wiki/Mod_spidermonkey_odbc#General_Configuration>

### ICMP error 是什么错误？

由于某种原因，你的连接请求被拒绝了，详见<http://wiki.freeswitch.org/wiki/Connection_Refused>。

### 在 Ubuntu 64-bit (gutsy/intrepid) 上启动时出现：segmentation fault

ncurses 库有一个问题。解决的办法是：
    apt-get install libncurses5-dev
重新编译 libedit：
    cd libs/libedit 
    make clean
    sh configure.gnu
    make
    cd ../..
    make clean
    make install

## 运行在后台

我如何让 FreeSWITCH 运行在后台？

    freeswitch -nc
当 FreeSWITCH  运行在后台时，是否有类似 telnet 的客户端能连上去呢？

是的。只要 mod_event_socket 模块已加载，你就可以使用 fs\_cli 连上去。它在 FreeSWITCH 的 bin 目录。

### FreeSWITCH 运行在后台时，我如何停止它呢？

使用命令：
    freeswitch -stop
或在 fs\_cli中，运行
    fs_cli> fsctl shutdown

### 如何让 FreeSWITCH 以更高的优先级运行？
    
    freeswitch -hp
### 如何将 FreeSWITCH 注册为一个 Win32 服务？

在你安装 FreeSWITCH 的路径中，执行
    freeswitch -install
或者，删除该服务
    freeswitch -uninstall
    
现在，该服务安装在“网络服务”项目中，在某些机器上，该项目可能没有足够的权限来运行 FreeSWITCH。在这种情况下，你需要修改它所属的用户。双击服务项目，到“登录”标签，将其修改为一个加合适的用户，如“本地系统账户”或你建立的新账户。

你可以在命令行模式下启动和停止 FreeSWITCH：

    net start freeswitch
    net stop freeswitch

如果使用“freeswitch -install”建立的启动项目不能启动，试试其它的办法，如：<http://sw4me.com/wiki/Winserv>。下载 winserv 并放到某一位置，如“C:\Program Files\winserv”。然后可以使用以下命令安装服务：

    C:\Program Files\winserv\winserv.exe" install FreeSWITCH "C:\Program Files\FreeSWITCH\freeswitch.exe" -nc

### 如何在一台服务器上运行多个 FreeSWITCH 实例？

参见：<http://wiki.freeswitch.org/wiki/Advanced_configuration#Multiple_FreeSWITCH_instances_on_one_box>
              
## 硬件兼容性

### 它是否能运行在 Amazon Elastic Cloud 上？
是的，见：<http://wiki.freeswitch.org/wiki/Amazon_EC2>。

### 它能运行在 Xen 虚拟机里吗？

是的， EC2 就是用的 Xen。

### 它能运行在没有 MMU的机器上吗？比方说 Blackfin ？

现在还不能，可能以后也不能。没有MMU，就不能运行当下流行的操作系统，如Linux等。当然 Blackfin 对 ucLinux 支持得很好，但是 ucLinux 是一个精简的 Linux，它被设计于在没有 MMU 的有限的环境下也能运行。
                                
有别的电话软件已经移植到了基于 Blackfin 的机器上，如 IP04，<http://www.rowetel.com>。如果程序清晰和简单，那么它将会非常好。但是，用户必须非常小心地运行那些不会产生内存碎片的程序。否则的话，就需要经常的进行重启。现在，FreeSWITCH还没有为如此受限的环境开发这么一个版本，所以，也没有人在做往 ucLinux 平台的移植。

## 编译

### 我是否需要下载所有外部的程序库（libs）？

不需要。make install 脚本会根据你选择编译的模块自动下载它所依赖的库。

### 我不想安装到 /usr/local/freeswitch/,如何更改安装路径？

    ./configure --prefix=/your/install/dir

### 我如何选择编译哪些模块？
    
修改源代码目录中的 modules.conf，把你想要编译的模块前面的 # 去掉，把不想编译的模块前面加个 #。在 Windows 系统上你需要使用 Visual Studio 提供的方法在 configuration manager 中修改模块依赖关系。

### 如何使用 Microsoft Visual C++ 2008 Express Edition 编译 FreeSWITCH ？
                                                                 
一定要按照 Microsoft 的 install instructions 要求去做。Visual C++ 页面在 <http://www.microsoft.com/express/vc/>。当 VC++ 2008 Express 安装完成后，打开 solution 文件 Freeswitch.2008.express.sln （如果你看到很多关于不支持的目录的错误，很可能是你打开了 Freeswitch.2008.sln，那个文件是 MS Visual C++ edition 的 solution 文件）。 点击 Build，编译 Solution 并等待编译完成。完成后会在 debug 目录中生成可执行文件 freeswitch.exe 。

注意：我们不再支持 Microsoft Visual C++ 2005 is no longer supported。

### 我在 CentOS（可能其它发行版也会有）上遇到一个问题，提示 "/lib/cpp" failing sanity check？

在 CentOS 4.4 上运行 “./configure” 会出现如下错误： "configure: error: C++ preprocessor "/lib/cpp" fails sanity check"。试试使用
    yum install gcc-c++ compat-gcc-32 compat-gcc-32-c++
检查依赖关系并且同意（如果你同意的话）。

### 运行 make megaclean 时出错

试试用下列顺序执行命令：

    ./bootstrap.sh
    ./configure
    make megaclean
    make installall
    
我没有 Microsoft Visual C++，在 Windows 上 是否有已经编译好的版本呢？. 

有，参见：<http://wiki.freeswitch.org/wiki/Installation_Guide#Precompiled_Binaries>


## SIP
   
### 如何设置 SIP 客户端认证？

参见：<http://wiki.freeswitch.org/wiki/Sofia>

### 如何设置 [Music on Hold (MOH)](http://wiki.freeswitch.org/wiki/Music_on_Hold)？

参见 [Sofia Configuration Files](http://wiki.freeswitch.org/wiki/Music_on_Hold) 中的  hold-music 选项，它可以对每个中继进行设置。或者，也可以通过信道变量 [hold_music](http://wiki.freeswitch.org/wiki/Channel_Variables#hold_music) 在 XML 拨号计划中对每个信道进行设置。
                                                              
### 在长时间收不到 RTP 后可以自动挂断电话吗？

是的。在 sofia profile 有两个参数管这个事。它们是 rtp-timeout-sec 和 rtp-hold-timeout-sec。

### 如果在 FS 控制台上看到 SIP 用户的注册情况？

可以在控制台上使用如下命令。显示 profile 信息和注册信息：

    sofia status profile internal
    
或仅显示注册信息：
    sofia status profile internal reg

## IAX2

如何设置 IAX2 客户端认证？

我们有用户目录，但没时间去修改 libiax2 以支持注册。对于外呼电话可以使用 iax/user:pass@remotehost/exten 以支持注册。要正确地支持所有东西，必须有人从头重写 IAX 协议栈. 

注：自 Asterisk 升级至 1.6 后，协议不再兼容，也没有人再愿意更新，因此 IAX2 也在 FreeSWITCH 代码树中移到 unsupported 目录中。
                                     
### FreeSWITCH 支持模块线路（FXS/FSO）吗？

OpenZAP 支持模拟语音卡。详见 <http://wiki.freeswitch.org/wiki/OpenZAP>。


### FreeSWITCH 支持 ISDN BRI/BRA 线路吗 （S0 Basic Rate Interface）？

初步的支持已经加入了ISDN 模块中（ozmod\_isdn）。支持TE (用户) 和 NT (网络) 模式, 包括NT 模式中的拨号音和交叠接收。 zaptel + bristuff / dahdi （ozmod\_zt） 及一个单口的 HFC-S PCI 卡上测试通过。注意：一些高级特性如（transfer、hold）等 还不支持。

更新：现在可以使用 Sangoma boost 协议栈与Sangoma BRI 卡在 FreeSWITCH 中支持 BRI。另见：<http://wiki.freeswitch.org/wiki/FreeTDM>，

### FreeSWITCH 是否支持 PRI （E1/J1/T1）？

OpenZAP 支持 PRI 卡（以及模块卡）。OpenZAP 代替了 mod\_wanpipe，最初，对 Sangoma PRI cards的支持是加在 mod\_wanpipe中实现的。

## 程序

### 如何在拨号计划中使用 JavaScript（ECMAScript）？

确定 mod\_spidermonkey 模块已经编译并加载，在拨号计划中执行：
    <action application="javascript" data="/tmp/test.js"/>
参见 <http://wiki.freeswitch.org/wiki/Javascript> 文档中 FreeSWITCH 对 javascript 的扩展。

### 如何让 FreeSWITCH 在没有控制台的情况下运行？

    freeswitch -nc  （No Console）
其它选项有：

    freeswitch -hp （High Priority mode）
    freeswitch -vg （valgrind，调试时有用）
    

### 如何在 FreeSWITCH 中发起一个呼叫？

见：API 命令：Originate <http://wiki.freeswitch.org/wiki/Mod_commands#originate>。关于 Sofia sip URL的语法，见 <http://wiki.freeswitch.org/wiki/Sofia>。

### reloadxml 能重载所有 XML 文件吗 ？

它只是将所有 XML 加载到内存，并不意味着所有的改变都生效。拨号计划和用户目录会刷新，它也会触发一个事件（依赖于 ENUM设置）以重载 ENUM。而 sofia profile 的设置不会更新。但你可以使用 sofia 命令使其刷新，有些改变需要重启某个 sofia profile。

会议设置会在下次创建一个会议时生效。当会议正在进行时不会起作用。

## 呼叫路由

### 我如何把 endpoints 放到不同的 context 中， 而不同的 context 又有不同的 extension ？

有几种不同的实现方法：

* 每个 profile 对应一个 context，每一次都需要一个独立的 IP:Port。
* 在注册数据中使用不同的 domain，它会自动路由 context。
* 把所有电话都指到一个公共的 context 中，并使用 execute\_extn 或 transfer 转移到其它地方
* 把它们送到一个 IVR，然后决定下一步去哪里。
* 使用 xml\_curl建立动态的 dialplan，根据你知道的呼叫数据来决定下一步应该做什么

### 如何在整个服务器上使用单一的 domain？

如果你想对所有请求提供服务，并且在单一的 domain 下，你可以找到 sip\_profiles/internal.xml中的 force-register-domain 一行，去掉该行的注释，并在 vars.xml 中设置对应的 domain 即可。在这里我不是十分确信，但你不能在 directory.xml 中设置另一个唯一的 domain，它必须与 vars.xml 中的匹配。如果你想让所有注册用户都能在同一个 domain 中列出来（或者排序），使用 force-register-db-domain 参数，如：

    <param name="force-register-domain" value="domainname"/>
    <param name="force-register-db-domain" value="domainname"/>

## 配置 FreeSWITCH

### 是否有一个配置 FreeSWITCH 的图形界面？

FreePBX 开发者正在开发 FreePBX V3，它支持 FreeSWITCH.现在，你可以获取一个[pre-release 的版本](http://www.freepbx.org/freepbx-v3)。它是一个很有前途的项目，我们鼓励任何对开源 FreeSWITCH GUI 前端感兴趣的人都去支持他们的努力。

FusionPBX，是一个支持多平台，开源的 FreeSWITCH WEB 界面，它基于 BSD 许可证发布。它已证明是一个可定制的、非常灵活的WEB界面。它的后台数据库支持 SQLite、PostgreSQL、MySQL等。它运行起起非常稳定，从小型的到大型的环境中都已经有所应用。

另一个选择是 WikiPBX，它基于 MPL 许可证发布，使用 Python 基于 Django 框架开发。

### XML 糟透了，还有其它选择吗？

是也不是。有其它的选择，但不一定是更好的选择。关于 FreeSWITCH 中 XML 配置的讨论已经足够了，见下面这些资料：

* Anthony 关于为什么选择 XML 的解释 <http://www.freeswitch.org/node/123>
* Anthony 关于创建一个 mod\_yaml 的讨论 <http://lists.freeswitch.org/pipermail/freeswitch-users/2008-June/004021.html>

另外，参见 [mod_dialplan_asterisk](http://wiki.freeswitch.org/wiki/Mod_dialplan_asterisk) 以获得更多关于使用 INI 格式的 extensions.conf 来配置 dialplan 的信息。（说明：它不灵活，并且不如 XML 强大。）

以上的例子都说明，如果 XML 你阻止你尝试 FreeSWTICH 的唯一原因的话，那么我们推荐你还是先用默认的配置试一试。你会感到惊奇，因为仅需修改一点点 XML 就可能干好多好多的事情。并且，你也会由于你能通过修改 XML 而做到的事情令人刮目相看。

另外一种不使用 XML Dianplan 控制呼叫逻辑的方法是通过  mod\_event\_socket 或称 ESL。使用这种它，你就可以不用 XML，而使用编译或解释型的程序语言来控制你的呼叫逻辑。