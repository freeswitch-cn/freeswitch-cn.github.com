---
title: Commands
layout: default
---

##简介##
下面的是根据最新的版本r14778（九月九号）中mod_commands模块提供的命令，这些命令可以使用方式有很多种，如下：

### 控制台 ###
具体查看下面内容。
译者注：通过FreeSWITCH控制台使用

### API/事件 接口 ###
通过API或事件接口调用，如：   

* [[mod\_event\_socket]]
* [[mod\_xmpp_event]]
* [[mod\_erlang_event]]
* [[mod\_xml_rpc]]

### 脚本接口 ###
通过脚本进行调用，如下：

* [[mod_perl]]
* [[mod_spidermonkey]]
* [[mod_python]]
* [[mod_lua]]

### 拨号方案调用 ###
通过拨号方案进行调用，例子如下：

	<source lang="xml">
	 <extension name="Make API call from Dialplan">
	   <condition field="destination_number" expression="^(999)$">
	     <!-- next line calls hupall, so be careful! -->
	     <action application="set" data="api_result=${hupall(normal_clearing)}"/>
	   </condition>
	 </extension>
	</source>

其他例子:

	<source lang="xml">
	 <action application="set" data="api_result=${status()}"/>
	 <action application="set" data="api_result=${version()}"/>
	 <action application="set" data="api_result=${strftime()}"/>
	 <action application="set" data="api_result=${expr(1+1)}"/>
	</source>

如果API命令含有多个参数，通常都是以空格隔开。

	<source lang="xml">
	 <action application="set" data="api_result=${sched_api(+5 none avmd ${uuid} start)}"/>
	</source>

API命令依赖于加载的相关模块，从每个模块注册的API命令中都能发现它们的踪影。

想要查看全部API命令列表的话，在cli中输入help或者show api即可。

注：如果你想从拨号方案中调用API命令的话，需要先确认拨号方案自带的dptools里面没有类似的命令。

## 核心命令 ##
主要在http://fisheye.freeswitch.org/browse/freeswitch.git/src/mod/applications/mod_commands/mod_commands.c中实现。

注：一些状态或列表命令的返回结果默认是以逗号进行分隔的列表。一些模块的返回结果可能也会包含逗号，这样就导致针对结果的自动化处理比较困难。一个解决方法是，是在命令的最后加上“as xml”，这样返回的就是xml格式的结果。

###acl###
使用acl列表判断ip地址是否为合法访问。

 Usage: acl <ip> <list_name>

###命令别名alias###
别名:一种针对常用命令的快捷输入方式 

 用法: alias add <别名> <命令> | del [<别名>|*]

例子:

	  freeswitch> alias add reloadall reloadacl reloadxml
	  +OK
	  freeswitch> alias add unreg sofia profile internal flush_inbound_reg
	  +OK

别名在重启后需要重设，如果需要重启后仍然生效，需要使用stickyadd参数，如下：

	  freeswitch> alias stickyadd reloadall reloadacl reloadxml
	  +OK

注：只在mod\_console中起作用，在fs_cli中无效。    
译者注：mod\_console为以前台模式启动的freeswitch的命令输入界面。而fs\_cli指的是freeswitch的客户端。

###bgapi###
用于在线程中执行api命令

    用法: bgapi <api命令>[ <参数>]

###complete###
Complete.

    Usage: complete add <word>|del [<word>|*]

译者注：该命令从没用过，不知道干啥的，知道的童鞋，可以来更新该文档。

###cond###
运算指定的条件，并返回结果。

    用法: cond <条件表达式> ? <true val> : <false val>

条件表达式支持的条件有：

 == 等于   
 < 小于   
 \> 大于

例子:
如果第一个值大于第二个，则返回true

	 cond 5 > 3 ? true : false
	 true

拨号方案中的例子:

	   <action application="set" data="voicemail_authorized=${cond(${sip_authorized} == true ? true : false)}"/>

稍复杂的例子:

	   <action application="set" data="voicemail_authorized=${cond(${sip_acl_authed_by} == domains ? false : ${cond(${sip_authorized} == true ? true : false)})}"/>

###domain_exists###
检查指定的domain是否存在：

 	 用法: domain_exists <domain>

###eval###

Eval (noop). 计算字符串，扩展通道变量.

    用法: eval [uuid:<uuid> ]<expression>

例子:

	 eval ${domain}
	 10.15.0.94
	
	 eval Hello, World!
	 Hello, World!
	
	 eval uuid:e72aff5c-6838-49a8-98fb-84c90ad840d9 ${channel-state}
	 CS_EXECUTE

###expand###
执行变量扩展API。

	 用法: [uuid:<uuid> ]<cmd> <args>

例子:   

 	 expand originate sofia/internal/1001%${domain} 9999   
    
在这个例子中，扩展的变量是${domain}。比如domain的值是192.168.1.1，则扩展后执行的命令为：

  	 originate sofia/internal/1001%192.168.1.1 9999

###fsctl###
发送freeswitch控制消息。
	
	 用法: fsctl [send_sighup |
	               hupall |
	               pause [inbound|outbound] |
	               resume [inbound|outbound] |
	               shutdown [cancel|elegant|asap|restart] |
	               last_sps |
	               sps [num] |
	               sync_clock |
	               sync_clock_when_idle |
	               reclaim_mem |
	               max_sessions |
	               min_dtmf_duration [num] |
	               max_dtmf_duration [num] |
	               default_dtmf_duration [num] |
	               loglevel [level] |
	               verbose_events [on|off]
	              ]

####hupall####
     
用于挂断呼向指定号码的通话。参数为：  
 
    clearing_type dialed_ext <extension number>
    
举个例子来说，杀掉正处于活跃状态、目标号码是1000的通话，命令为：

    fsctl hupall normal_clearing dialed_ext 1000

####sync_clock####
FreeSWITCH不信任系统时间。当系统第一次启动的时候，从系统时间中获取样本时间，然后以此为基准使用单调时钟（monotonic clock）。你可以使用命令“fsctl sync_clock”将FreeSWITCH与系统时间进行同步。

注：该命令会立即生效，会影响CDR里面的时间统计。如会导致计费超前或延后，或者记录的挂断时间小于拨打时间。举个例子来说，如果FS的时钟比系统时间迟一个月，当进行时间同步后，CDR的呼叫记录里面就会出现有的呼叫持续时间为1个月。

命令**fsctl sync\_clock\_when\_idle**要安全很多，作用和上面一样，但是要到系统中所有通道都空闲的时候才开始时间同步。这种方法不会对CDR产生影响。

####sync\_clock\_when\_idle####
要到系统没有通话的时候才开始时间同步

####sps####
该设置会改变swithch.conf文件中设置的sessions-per-second（每秒并发通话数）属性限制

####last_sps####
查询显示目前生效的sessions-per-second属性。

####pause####
可以使用参数inbound或outbound来暂停创建呼入或呼出通话，如果没有指定参数的话，则呼入呼出都暂停。resume的用法类似。

####min\_dtmf\_duration####

例子:

    fsctl min_dtmf_duration 800

译者注：没看懂，就不翻译出来误导人了！    
This example sets the min_dtmf_duration switch parameter to 100ms. The number is in clock ticks where clockticks / 8 = ms. The min_dtmf_duration specifies the minimum DTMF duration to use on outgoing events. Events shorter than this will be increased in duration to match min_dtmf_duration. You cannot configure a DTMF duration on a profile that is less than this setting. You may increase this value, but cannot set it lower than 400 (the default). This value cannot exceed max_dtmf_duration. This setting can be changed in switch.conf.xml.

It is worth noting that many devices squelch in-band DTMF when sending RFC 2833. Devices that squelch in-band DTMF have a certain reaction time and clamping time which can sometimes reach as high as 40ms, though most can do it in less than 20ms. As the shortness of your DTMF event duration approaches this clamping threshold, the risk of your DTMF being ignored as a squelched event increases. If your call is always IP-IP the entire route, this is likely not a concern. However, when your call is sent to the PSTN, the RFC 2833 must be encoded in the audio stream. This means that other devices down the line (possibly a PBX or IVR you are calling into) might start considering your DTMF event a squelched tone and ignore it entirely. For this reason, it is recommended that you do not send DTMF events shorter than 80ms.

Checking the current value:

 fsctl min_dtmf_duration 0

The code recognizes a duration of 0 as a status check. Instead of setting the value to 0, it simply returns the current value.

====max_dtmf_duration====

Example:

 fsctl max_dtmf_duration 80000

This example sets the max_dtmf_duration switch parameter to 10,000ms (10 seconds). The number is in clock ticks (CT) where CT / 8 = ms. The max_dtmf_duration caps the playout of a DTMF event at the specified duration. Events exceeding this duration will be truncated to this duration. You cannot configure a duration on a profile that exceeds this setting. This setting can be lowered, but cannot exceed 192000 (the default). This setting cannot be set lower than min_dtmf_duration. This setting can be changed in switch.conf.xml.


Checking the current value:

 fsctl max_dtmf_duration 0

The code recognizes a duration of 0 as a status check. Instead of setting the value to 0, it simply returns the current value.

====default_dtmf_duration====

Example:

 fsctl default_dtmf_duration 2000

This example sets the default_dtmf_duration switch parameter to 250ms. The number is in clock ticks (CT) where CT / 8 = ms. The default_dtmf_duration specifies the DTMF duration to use on originated DTMF events or on events that are received without a duration specified. This value can be increased or lowered. This value is lower-bounded by min_dtmf_duration and upper-bounded by max_dtmf_duration. This setting can be changed in switch.conf.xml.


Checking the current value:

 fsctl default_dtmf_duration 0

The code recognizes a duration of 0 as a status check. Instead of setting the value to 0, it simply returns the current value.

====verbose_events====
Enables verbose events. Verbose events have '''every''' channel variable in '''every''' event for a particular channel. Non-verbose events have only the pre-selected channel variables in the event headers.
* This setting can also be set in [[switch.conf.xml]].

###global_getvar###
获取全局变量的值。如果没有提供参数，则返回所有全局变量的值。

    用法: global_getvar <varname>

###global_setvar###
设置全局变量

    用法: global_setvar <varname>=<value>

例子:

    global_setvar foo=bar

###group_call###
返回组呼bridge字符串，组呼定义请参考[[XML User Directory Guide#Groups|call group]]。

 	Usage: group_call group@domain[+F][+A][+E]

+F将会以串行呼叫模式返回组成员（以“|”隔开各成员）.
+A将会以并行呼叫模式返回组成员（以“，”隔开各成员）.
+E将会议呼叫模式返回组成员（以：\_:隔开各成员），关于企业呼叫请参考[[Freeswitch\_IVR\_Originate#Enterprise\_originate|enterprise fashion]].

请注意：如果你需要设置在外呼通道上面设置用户变量，需要确保你的domain或被拨打组的变量列表里面没有设置dial-string和group-dial-string，用设置用户默认组里面的dial-string和group-dial-string来替代。这样的话，group_call将会返回user/101,user/将会设置你的外呼通道变量。

###help###
显示所有API命令的帮助信息。

    用法: help

###host_lookup###

针对指定域名做主机查询(host lookup)。

    用法: host_lookup <hostname>

###hupall###
断开现存通话。

    用法: hupall <cause> [<variable> <value>]

挂断所有含有变量<variable>，并且值为<value>的通话，挂机原因为<cause>。

例子:

	originate {foo=bar}sofia/internal/someone1@server.com,sofia/internal/someone2@server.com &park
	
	hupall normal_clearing foo bar

###in_group###
判断用户是否在指定的组中

    用法: in_group <user>[@<domain>] <group_name>

###is_lan_addr###
判断IP是否为内网地址

    用法: is_lan_addr <ip>

###load###
加载外部模块

    用法: load <mod_name>

###md5###
返回指定数据的MD5值。

    用法: md5 <data>

###module_exists###
检查模块是否存在。

    用法: module_exists <module>

###msleep###
休眠指定毫秒

    用法: msleep <休眠的毫秒数>


###nat_map###

    用法: nat_map [status|reinit|republish] | [add|del] <port> [tcp|udp] [sticky] | [mapping] <enable|disable>

* status - 用于显示NAT类型、外网IP（the external IP）以及当前映射的端口。
* reinit - 重新初始化NAT模块。当你更换路由器或将路由器由NAT切换到UPnP模式的时候，使用该参数。
* republish - 该参数会让FreeSWITCH重新（向路由器等）发布NAT映射信息。 正常情况下，没有必要使用该参数。
* mapping - 该参数用于控制是否向NAT设备发送端口映射请求(可使用-nonatmap参数在系统启动时关闭该功能). 之所以存在该参数，是因为有可能需要通过NAT获取公网IP地址，而不需要通过NAT开启端口。

Note: sticky参数用于将映射信息固化下来，在下次FreeSWITCH重启后映射仍然生效。 

警告: 如果你有多个网卡，并分别配置了使用相同端口的sip profiles。nat_map在映射端口的时候，会被弄昏头的，不需要将端口映射到哪个sip profile上面，千万别干这种挫事！

###regex###
执行正则表达式匹配。该参数会根据是否提供<subst string>参数而实现不同的功能，如下：  
  
* 如果没提供该参数, ''regex'' 将会执行正常的匹配，返回true或者false。
* 如果提供该参数，如果匹配成功的话，会返回指定的子串。如果匹配失败，则返回全部源字符串。

默认的正则表达式分界符是|（管道符）。可以更改为~或者/，只要在字符串的前面加上'm:'。

	Usage: regex <data>|<pattern>[|<subst string>]
	       regex m:/<data>/<pattern>[/<subst string>]
	       regex m:~<data>~<pattern>[~<subst string>]

例子:

	 regex test1234|\d                  <== Returns "true"
	 regex m:/test1234/\d               <== Returns "true"
	 regex m:~test1234~\d               <== Returns "true"
	 regex test|\d                      <== Returns "false"
	 regex test1234|(\d+)|$1            <== Returns "1234"
	 regex sip:foo@bar.baz|^sip:(.*)|$1 <== Returns "foo@bar.baz"
	 regex testingonetwo|(\d+)|$1       <== Returns "testingonetwo" (no match)
	 regex m:~30~/^(10|20|40)$/~$1      <== Returns "30" (no match)
	 regex m:~30~/^(10|20|40)$/~$1~n    <== Returns "" (no match)
	 regex m:~30~/^(10|20|40)$/~$1~b    <== Returns "false" (no match)

版本14727中的逻辑是，如果源字符串匹配匹配到结果，那么条件为false，但是这里仍有一个匹配结果，结果是1001。（这里的翻译是照字面翻译，小伙伴们，你们看懂了没？）      
Logic in revision 14727 if the source string matches the result then the condition was false however there was a match and it is 1001.

    regex 1001|(^\d{4}$)|$1

* See also [[Regular_Expression]]

###reload###

重新加载模块。

 	用法: reload [-f] <mod_name>

###reloadacl###

重新加载ACL规则。

 	用法: reloadacl [reloadxml]

###reloadxml###
重新加载conf/freeswitch.xml的配置信息到内存中。

 	用法: reloadxml

###show###
输出多种（模块）状态报告。

	 用法: show <item>
	  item类型如下:
	  codec
	  endpoint
	  application
	  api
	  dialplan
	  file
	  timer
	  calls [count]
	  channels [count|like <match string>]
	  calls
	  detailed_calls
	  bridged_calls
	  detailed_bridged_calls
	  aliases
	  complete
	  chat
	  management
	  modules
	  nat_map
	  say
	  interfaces
	  interface_types
	  tasks
	  limits
 
XML格式输出: show foo as xml

修改输出分隔符: show foo as delim |

* codec - 列出所有编码
* endpoint - 列出所有endpoint类型模块
* application - 列出所有应用程序
* api - 列出所有api
* dialplan - 列出拨号方案涉及的模块
* file - 列出所有支持的文件类型
* timer - 列出计时器timer模块
* calls - 列出当前的通话[count] 
* channels - 列出当前的通道 [count|like <match string>]    
  注：关于calls与channels的对比，请参考[Channels vs Calls](http://wiki.freeswitch.org/wiki/Channels_vs_Calls)
* bridged_calls - 和"show calls"相同
* detailed_calls - 和"show calls"类似，但是显示字段更多
* detailed_bridged_calls - 和"show calls"类似，但是显示字段更多
* aliases - 列出所有别名（别名干啥用的，暂时未查到）
* complete - list command complete tables
* chat - 列出所有chat模块，包括api、sms、conf等
* management - list management?
* modules - 列出所有模块
* nat_map - 列出地址映射表
* say - 列出有支持语言的say模块
* interfaces - 列出所有接口
* interface_types - 列出所有接口类型
* tasks - 列出任务
* registrations - 列出所有注册用户

#### Tips For Showing Calls and Channels ####
理解show calls/channels真义的最好方式是亲自去尝试。最近（2011.9）又在show命令家族中添加了几位：   

* show detailed_calls
* show bridged_calls
* show detailed\_bridged_calls

这三个命令用于取代简单的"show calls"。    
需要注意的是，"show detailed_calls"取代的是"show distinct\_channels"。命令都是相似的，但是返回信息更多。    
同样需要注意的是，这里并没有"show detailed\_channels"命令，但是使用"show detailed\_calls"会让你得到相同的结果。该命令能让你得到“单腿通话”（one-legged calls）或桥接后的通话信息，所以，少年，习惯这条新命令吧！


小贴士2: 有时，你需要获取某个特定的uuid，可以使用下面的方式。    
假设你设置了通道变量presence_data，那可以使用下面的命令搜索符合条件的通道（即含有foo的通道）：
 show channels like foo

like将会搜索下面的关键字段：

* uuid
* channel name
* caller id name
* caller id number
* presence_data

注: **presence_data** 必须在**bridge**或**originate**期间设置，而不是在通道已经建立完成后才设置。

###shutdown###
Stop the FreeSWITCH program. This only works from the CLI, as an API call, you should be using 'fsctl shutdown'

Warning! Shutdown from the CLI ignores arguments and exits immediately!

 Usage: fsctl shutdown [cancel|elegant|asap|restart|now]
* cancel - discontinue a previous shutdown request.
* elegant - wait for all traffic to stop; do not prevent new traffic.
* asap - wait for all traffic to stop; do not allow new traffic.
* restart - restart FreeSWITCH immediately following the shutdown.
* now - shutdown FreeSWITCH immediately.

When giving "elegant", "asap" or "now" it's also possible to give the restart command:
 Usage: fsctl shutdown [elegant|asap|now] restart

###status###
Show current status

 Usage: status

 freeswitch@internal> status
 UP 0 years, 0 days, 1 hour, 28 minutes, 4 seconds, 208 milliseconds, 305 microseconds
 FreeSWITCH is ready
 4 session(s) since startup
 0 session(s) 0/30                        <- Most channels to create per second .. from switch.conf.xml
 1000 session(s) max                      <- Max number of sessions to allow at any given time .. from switch.conf.xml
 min idle cpu 0.00/100.00                 <- Minimum idle CPU before refusing calls .. from switch.conf.xml if it's enabled.

###strftime_tz###
Displays formatted time, converted to a specific timezone.  See /usr/share/zoneinfo/zone.tab for the standard list of Linux timezones.

 Usage: strftime_tz <timezone> [format_string]

Example: strftime_tz US/Eastern %Y-%m-%d %T

###unload###
Unload external module.

 Usage: unload [-f] <mod_name>

###version###
Show version of the switch

 Usage: version [short]

###xml_locate###

xml_locate root: Will return all XML being used by FreeSWITCH
xml_locate <section>: Will return the XML corresponding to the specified <section>
<pre>
xml_locate directory
xml_locate configuration
xml_locate dialplan
xml_locate phrases
</pre>
 Usage: xml_locate [root | <section> | <section> <tag> <tag_attr_name> <tag_attr_val>]

 Example: xml_locate directory domain name example.com

###xml_wrap###

Wrap another API command in XML.

 Usage: xml_wrap <command> <args>

##Call Management Commands##

###break###
Deprecated. See uuid_break.

###create_uuid###
Creates a new UUID and returns it as a string.

Usage: create_uuid

###originate###
Originate a new call.

    Usage: originate <call_url> <exten>|&<application_name>(<app_args>) 
    [<dialplan>] [<context>] [<cid_name>] [<cid_num>] [<timeout_sec>]


'''Parameters:'''
* <call_url> URL you are calling. <br> For more info on sofia SIP URL syntax see: [[Sofia|FreeSwitch Endpoint Sofia]]
* Destination, one of:
** <exten> Destination number to enter dialplan with
** &<application_name>(<app_args>)
*** "&" indicates what follows is an application name, not an exten
*** (<app_args>) is optional (not all applications require parameters, eg park)
*** Here is a list of valid application names that can be used here: <br>park, bridge, javascript/lua/perl, playback (remove mod_native_file), and many others.
*** Note: Use single quotes to pass arguments with spaces, e.g. '&lua(test.lua arg1 arg2)'
*** Note: There is no space between & and the application name
* <dialplan> Defaults to 'XML' if not specified.
* <context> Defaults to 'default' if not specified.
* <cid_name> CallerID name.
* <cid_num> CallerID number.
* <timeout_sec> Timeout in seconds.

'''Options:'''

These options can be used in curly braces, example: "originate {ignore_early_media=true}sofia/example/user 8334".

Options must be separated by ',', Example: "originate {ignore_early_media=true,originate_timeout=2}sofia/example/user 8334"

* group_confirm_key
* group_confirm_file
* forked_dial
* fail_on_single_reject
* ignore_early_media
* return_ring_ready
* originate_retries
* originate_retry_sleep_ms
* origination_caller_id_name
* origination_caller_id_number
* originate_timeout
* sip_auto_answer

[[Channel_Variables#Originate_related_variables|Description of originate's related variables]]

'''Examples:'''
So you can call a locally registered sip endpoint 300 and park the call like so (Note that the "example" profile used here must be the one your local user you want to call is registered to)

    originate sofia/example/300%pbx.internal &park()

or you could instead connect a remote sip endpoint to extension 8600

    originate sofia/example/300@foo.com 8600

or you could instead connect a remote SIP endpoint to another remote extension

    originate sofia/example/300@foo.com &bridge(sofia/example/400@bar.com)

or you could even run a javascript application test.js

    originate sofia/example/1000@somewhere.com &javascript(test.js)

To run a javascript with arguments you must surround it in quotes.

    originate sofia/example/1000@somewhere.com '&javascript(test.js myArg1 myArg2)'

Setting channel variables before doing the originate

    originate {ignore_early_media=true}sofia/mydomain.com/18005551212@1.2.3.4 15555551212

Setting variable to send to another FS box during originate
    originate {sip_h_X-varA=111,sip_h_X-varB=222}sofia/mydomain.com/18005551212@1.2.3.4 15555551212

Note: you can set any channel variable, even custom ones. Use single quotes to enclose values with spaces, commas, etc. 
    originate {my_own_var=my_value}sofia/mydomain.com/that.ext@1.2.3.4 15555551212
    originate {my_own_var='my value'}sofia/mydomain.com/that.ext@1.2.3.4 15555551212

If you need to fake the ringback to the originated endpoint try this:

    originate {ringback=\'%(2000,4000,440.0,480.0)\'}sofia/example/300@foo.com &bridge(sofia/example/400@bar.com)

If you need to make originate return immediately when the channel is in "Ring-Ready" state try this:
    originate {return_ring_ready=true}sofia/gateway/someprovider/919246461929 &socket(127.0.0.1:8082 async full)
see here for more info on [http://blog.godson.in/2010/12/use-of-returnringready-originate.html return_ring_ready ]

You can even set music on hold for the ringback if you want:

    originate {ringback=\'/path/to/music.wav\'}sofia/gateway/name/number &bridge(sofia/gateway/name/othernumber)

You can originate a call in the background (asynchronously) and playback a message with a 60 second timeout.

    bgapi originate {ignore_early_media=true,originate_timeout=60}sofia/gateway/name/number &playback(message)

You can specify the UUID of an originated call by doing the following:
* Use create_uuid to generate a UUID to use.
* This will allow you to kill an originated call before it is answered by using uuid_kill.
* If you specify origination_uuid it will remain the UUID for answered call leg for the whole session.
     originate {origination_uuid=...}user/100@domain.name.com

Here's an example of originating a call to the echo conference (an external sip URL) and bridging it to a local user's phone:

    originate sofia/internal/9996@conference.freeswitch.org &bridge(user/105@default)

Here's an example of originating a call to an extension in a different context than 'default' (required for the FreePBX which uses context_1, context_2, etc.):

    originate sofia/internal/2001@foo.com 3001 xml context_3

You can also originate to multiple extensions as follows:
    originate user/1001,user/1002,user/1003 &park()

To put an outbound call into a conference at early media, either of these will work (they are effectively the same thing)
    originate sofia/example/300@foo.com &conference(conf_uuid-TEST_CON)
    originate sofia/example/300@foo.com conference:conf_uuid-TEST_CON inline
    
       ( See [[Misc._Dialplan_Tools_InlineDialplan]] for more detail on 'inline' Dialplans )

An example of using loopback and inline on the A-leg can be found [http://lists.freeswitch.org/pipermail/freeswitch-users/2013-January/091769.html here]

###pause###
Pause <uuid> media

Usage: pause <uuid> <on|off>

###uuid_answer###
Answer a channel

Usage: uuid_answer <uuid>

* See Also: [[Misc._Dialplan_Tools_answer]]

###uuid_audio###
Adjust the audio levels on a channel or mute (read/write) via a media bug.

Usage: uuid_audio <uuid> [start [read|write] [mute|level <level>]|stop]

''level'' is in the range from -4 to 4, 0 being the default value.

###uuid_break###
Break out of media being sent to a channel. For example, if an audio file is being played to a channel, issuing uuid_break will discontinue the media and the call will move on in the dialplan, script, or whatever is controlling the call. 

Usage: uuid_break <uuid> [all]

If the '''all''' flag is used then all audio files/prompts/etc. that are queued up to be played to the channel will be removed, whereas without the '''all''' flag only the currently playing file will be discontinued.


###uuid_bridge###
Bridge two call legs together. 

Usage: uuid_bridge <uuid> <other_uuid>

uuid_bridge needs atleast any one leg to be answered.

###uuid_broadcast###
Execute an arbitrary dialplan application on a specific uuid. If a filename is specified then it is played into the channel(s). To execute an application use "app::args" syntax.

Usage: uuid_broadcast <uuid> <path> [aleg|bleg|both]

Execute an application on a chosen leg(s) with optional hangup afterwards:

Usage: uuid_broadcast <uuid> app[![hangup_cause]]::args [aleg|bleg|both]

Examples:

<pre>
 uuid_broadcast 336889f2-1868-11de-81a9-3f4acc8e505e sorry.wav both
 uuid_broadcast 336889f2-1868-11de-81a9-3f4acc8e505e say::en\snumber\spronounced\s12345 aleg
 uuid_broadcast 336889f2-1868-11de-81a9-3f4acc8e505e say!::en\snumber\spronounced\s12345 aleg
 uuid_broadcast 336889f2-1868-11de-81a9-3f4acc8e505e say!user_busy::en\snumber\spronounced\s12345 aleg
 uuid_broadcast 336889f2-1868-11de-81a9-3f4acc8e505e playback!user_busy::sorry.wav aleg
</pre>

###uuid_buglist###
List the media bugs on channel

Usage: uuid_buglist <uuid>

###uuid_chat###

Send a chat message.

 -USAGE: <uuid> <text>

If the endpoint associated with the session <uuid> has a receive_event handler, this message gets sent to that session and is interpreted as an instant message.

###uuid_debug_media###

The command was uuid_debug_audio, been changed into the current name when video options was added.

Debug media

Usage:

 <uuid> <read|write|both|vread|vwrite|vboth> <on|off>

Use "read" or "write" for the audio direction to debug, or "both" for both direction. And prefix with v for video.

#### Read Format ####
"R %s b=%4ld %s:%u %s:%u %s:%u pt=%d ts=%u m=%d\n"

where the values are:
* switch_channel_get_name(switch_core_session_get_channel(session)),
* (long) bytes,
* my_host, switch_sockaddr_get_port(rtp_session->local_addr),
* old_host, rtp_session->remote_port,
* tx_host, switch_sockaddr_get_port(rtp_session->from_addr),
* rtp_session->recv_msg.header.pt, 
* ntohl(rtp_session->recv_msg.header.ts), 
* rtp_session->recv_msg.header.m

#### Write Format ####
"W %s b=%4ld %s:%u %s:%u %s:%u pt=%d ts=%u m=%d\n"

where the values are:
* switch_channel_get_name(switch_core_session_get_channel(session)),
* (long) bytes,
* my_host, switch_sockaddr_get_port(rtp_session->local_addr),
* old_host, rtp_session->remote_port,
* tx_host, switch_sockaddr_get_port(rtp_session->from_addr),
* send_msg->header.pt, 
* ntohl(send_msg->header.ts), 
* send_msg->header.m);

###uuid_deflect###
Deflect an answered SIP call off of FreeSWITCH by sending the REFER method

Usage: uuid_deflect <uuid> <sip URL>

uuid_deflect waits for the final response from the far end to be reported.  It returns the sip fragment from that response as the text in the FreeSWITCH response to uuid_deflect.  If the far end reports the REFER was successful, then FreeSWITCH will issue a bye on the channel.

Example:  
   uuid_deflect 0c9520c4-58e7-40c4-b7e3-819d72a98614 sip:info@example.net

Response:  
   Content-Type: api/response
   Content-Length: 30

   +OK:SIP/2.0 486 Busy Here

###uuid_displace###
Displace the audio for the target <uuid> with the specified audio <file>.

'''Parameters:'''
* uuid = Unique ID of this call (see 'show channels')
* start|stop = Start/Stop this action
* file = path to an audio source (wav, shout, etc...)
* limit = number of seconds before terminating the displacement
* mux = cause the original audio to be mixed together with 'file', i.e. you can still converse with the other party while the file is playing

'''Usage:'''
uuid_displace <uuid> [start|stop] <file> [<limit>] [mux]

'''Examples:'''
<pre>
cli> uuid_displace 1a152be6-2359-11dc-8f1e-4d36f239dfb5 start /sounds/test.wav 60
cli> uuid_displace 1a152be6-2359-11dc-8f1e-4d36f239dfb5 stop /sounds/test.wav
</pre>

###uuid_display###

Updates the display on a phone if the phone supports this.  This works on some SIP phones right now including Polycom and Snom.

 -USAGE: <uuid> [<display>]

This command makes the phone re-negotiate the codec. The SIP -> RTP Packet Size should be 0.020. If it is set to 0.030 on the SPA series phones it causes a DTMF lag. When DTMF keys are pressed on the phone they are can be seen on the fs_cli 4-6 seconds late.

###uuid_dual_transfer###

Transfer each leg of a call to different destinations.

 		-USAGE: <uuid> <A-dest-exten>[/<A-dialplan>][/<A-context>] <B-dest-exten>[/<B-dialplan>][/<B-context>]


###uuid_dump###
Dumps all variable values for a session.

Usage: uuid_dump <uuid> [format]

Format options: XML (any others?)

###uuid_early_ok###
Stops the process of ignoring early media, i.e. if ignore_early_media=true it stops ignoring early media and responds normally.

Usage: uuid_early_ok <uuid>

###uuid_exists###
Checks whether a given UUID exists.

Usage: uuid_exists <uuid>

###uuid_flush_dtmf###
Flush queued DTMF digits

Usage: uuid_flush_dtmf <uuid>

###uuid_fileman###
Manage the audio being played into a channel from a sound file

Usage: uuid_fileman <uuid> <cmd:val>

Commands are:
* speed:<+[step]>|<-[step]>
* volume:<+[step]>|<-[step]>
* pause
* stop
* truncate
* restart
* seek:<+[samples]>|<-[samples]>
Samples are the literally the number of samples in the file to jump forward or backward. In an 8kHz file, 8000 samples would represent one second, in a 16kHz file 16000 samples would be one second, etc.

###uuid_getvar###
Get a variable from a channel.

Usage: uuid_getvar <uuid> <varname>

###uuid_hold###
Place a call on hold.

Usage: 
<pre>
uuid_hold <uuid>           place a call on hold
uuid_hold off <uuid>       switch off on hold
uuid_hold toggle <uuid>    toggles call-state based on current call-state
</pre>

###uuid_kill###
Reset a specific <uuid> channel.

Usage: uuid_kill <uuid> [cause]

###uuid_limit###
Apply or change limit(s) on a specified uuid.

Usage: uuid_limit <uuid> <backend> <realm> <resource> [<max>[/interval]] [number [dialplan [context]]]

See also [[Limit]]

###uuid_media###
Reinvite FreeSWITCH out of the media path:

Usage: uuid_media [off] <uuid>

Reinvite FreeSWITCH back in:

Usage: uuid_media <uuid>

###uuid_media_reneg###
API command to tell a channel to send a re-invite with optional list of new codecs

Usage: uuid_media_reneg <uuid> <codec string>

###uuid_park###
Park call

Usage: uuid_park <uuid>

###uuid_preanswer###
Preanswer a channel.

Usage: uuid_preanswer <uuid>

* See Also: [[Misc._Dialplan_Tools_pre_answer]]

###uuid_preprocess###
Pre-process Channel 

Usage:  uuid_preprocess <>

###uuid_recv_dtmf###

Send DTMF digits to <uuid> set.

 Usage: uuid_recv_dtmf <uuid> <dtmf digits>[@<tone_duration>]

Use the character w for a .5 second delay and the character W for a 1 second delay.

Default tone duration is 2000ms .

###uuid_send_dtmf###

Send DTMF digits.

 Usage: uuid_send_dtmf <uuid> <dtmf digits>[@<tone_duration>]

Use the character w for a .5 second delay and the character W for a 1 second delay.

Default tone duration is 2000ms .

###uuid_send_info###

Send info to the endpoint

 Usage:  uuid_send_info <uuid>

###uuid_session_heartbeat###

 Usage: uuid_session_heartbeat <uuid> [sched] [0|<seconds>]

###uuid_setvar###
Set a variable on a channel. If value is omitted, the variable is unset.

Usage: uuid_setvar <uuid> <varname> [value]

###uuid_setvar_multi###
Set multiple vars on a channel.

Usage: uuid_setvar_multi <uuid> <varname>=<value>[;<varname>=<value>[;...]]

###uuid_simplify###

This command directs FreeSWITCH to remove itself from the SIP signaling path if it can safely do so

Usage:

 uuid_simplify <uuid>

###uuid_transfer###
Transfers an existing call to a specific extension within a <dialplan> and <context>. Dialplan may be "xml" or "directory".

Usage: 

 uuid_transfer <uuid> [-bleg|-both] <dest-exten> [<dialplan>] [<context>]

The optional first argument will allow you to transfer both parties (-both) or only the party to whom <uuid> is talking.(-bleg)

NOTE: if the call has been bridged, and you want to transfer either sides of the call, then you will need to use <action application="set" data="hangup_after_bridge=false"/> (or the API equivalent).  If it's not set, transfer doesn't really work as you'd expect, and leaves calls in limbo.

##Record/Playback Commands##

###uuid_record###

Record the audio associated with the given UUID into a file. The start command causes FreeSWITCH to start mixing all call legs together and saves the result as a file in the format that the file's extension dictates. (if available) The stop command will stop the recording and close the file. If media setup hasn't yet happened, the file will contain silent audio until media is available. Audio will be recorded for calls that are parked. The recording will continue through the bridged call. If the call is set to return to park after the bridge, the bug will remain on the call, but no audio is recorded until the call is bridged again. (TODO: What if media doesn't flow through FreeSWITCH? Will it re-INVITE first? Or do we just not get the audio in that case?)

Usage:

 uuid_record <uuid> [start|stop] <path> [<limit>]

Where limit is the max number of seconds to record.

If the path is not specified on start it will default to the channel variable "sound_prefix" or FreeSWITCH base_dir when the "sound_prefix" is empty.

You may also specify "all" for path when stop is used to remove all for this uuid

"stop" command must be followed by <path> option.

[[Channel_Variables#Call_Recording_Related|See record's related variables]]

##Limit Commands##
###[[Limit#API|limit_reset]]###
Reset a limit backend.
###[[Limit#API|limit_status]]###
Retrieve status from a limit backend.
###[[Limit#API|limit_usage]]###
Retrieve usage for a given resource.
###[[Limit#API|uuid_limit_release]]###
Manually decrease a resource usage by one.
###[[Limit#API|limit_interval_reset]]###
Reset the interval counter to zero prior to the start of the next interval.

##Misc. Commands##

###bg_system###
Execute a system command in the background.

Usage: bg_system <command>


###echo###
Echo input back to the console
 echo This text will appear
 This text will appear

###file_exists###

Tests whether ''filename'' exists.

 file_exists filename

Examples:

 > file_exists /tmp/real_file
 true
 > file_exists /tmp/missing_file
 false

Example dialplan usage:

	 <extension name="play-news-announcements">
	   <condition expression="${file_exists(${sounds_dir}/news.wav)}" expression="true"/>
	     <action application="playback" data="${sounds_dir}/news.wav"/>
	     <anti-action application="playback" data="${soufnds_dir}/no-news-is-good-news.wav"/>
	   </condition>
	 </extension>

'''Note''' this tests whether FreeSWITCH can see the file, but the file may still be unreadable (permissions).

###find_user_xml###

Checks to see if a user exists; Matches user tags found in the directory, similar to [[user_exists]], but returns an XML representation of the user as defined in the directory (like the one shown in [[Mod_commands#user_exists|user_exists]]).

Usage: find_user_xml <key> <user> <domain>

Where key references a key specified in a directory's user tag, user represents the value of the key, and the domain is the domain the user is assigned to.

###list_users###

Lists Users configured in Directory

Usage:
 list_users [group <group>] [domain <domain>] [user <user>] [context <context>]

Example:
<pre>
freeswitch@localhost> list_users group default

userid|context|domain|group|contact|callgroup|effective_caller_id_name|effective_caller_id_number
2000|default|192.168.20.73|default|sofia/internal/sip:2000@192.168.20.219:5060|techsupport|B#-Test 2000|2000
2001|default|192.168.20.73|default|sofia/internal/sip:2001@192.168.20.150:63412;rinstance=8e2c8b86809acf2a|techsupport|Test 2001|2001
2002|default|192.168.20.73|default|error/user_not_registered|techsupport|Test 2002|2002
2003|default|192.168.20.73|default|sofia/internal/sip:2003@192.168.20.149:5060|techsupport|Test 2003|2003
2004|default|192.168.20.73|default|error/user_not_registered|techsupport|Test 2004|2004

+OK
</pre>

Search items can be combined:

<pre>
freeswitch@localhost> list_users group default user 2004

userid|context|domain|group|contact|callgroup|effective_caller_id_name|effective_caller_id_number
2004|default|192.168.20.73|default|error/user_not_registered|techsupport|Test 2004|2004

+OK
</pre>

###sched_api###
Schedule an API call in the future.
Usage:
    sched_api [+@]<time> <group_name> <command_string>

time is the UNIX timestamp at which the command should be executed. If it is prefixed by +, <time> specifies the number of seconds to wait before executing the command. If prefixed by @, it will execute the command periodically every <time> seconds; for the first time it will be executed after <time> seconds.<br/>
group_name will be the value of "Task-Group" in generated events. "none" is the proper value for no group.<br/>
command_string is the command executed<br/>

Scheduled task or group of tasks can be revoked with sched_del or unsched_api. 

You could put "&" symbol at the end of the line to make command to be executed in its own thread.

Example:
    sched_api +1800 none originate sofia/internal/1000%${sip_profile} &echo()
    sched_api @600 check_sched log Periodic task is running...

###sched_broadcast###
Play a <path> file to a specific <uuid> call in the future.
Usage:
    sched_broadcast [+]<time> <uuid> <path> [aleg|bleg|both]

Schedule execution of an application on a chosen leg(s) with optional hangup:
Usage: 
    sched_broadcast [+]<time> <uuid> app[![hangup_cause]]::args [aleg|bleg|both]

time is the UNIX timestamp at which the command should be executed (or if it is prefixed by +, the number of seconds to wait before executing the command)<br/>

Example:
    sched_broadcast +60 336889f2-1868-11de-81a9-3f4acc8e505e commercial.wav both
    sched_broadcast +60 336889f2-1868-11de-81a9-3f4acc8e505e say::en\snumber\spronounced\s12345 aleg

###sched_del###
Removes a prior scheduled group or task ID
Usage:
    sched_del <group_name|task_id>

The one argument can either be a group of prior scheduled tasks or the returned task-id from sched_api.

Example:
    sched_del my_group
    sched_del 2

###sched_hangup###

Schedule a running call to hangup.

Usage: sched_hangup [+]<time> <uuid> [<cause>]

Note:  sched_hangup +0 is the same as uuid_kill

###sched_transfer###

Schedule a transfer for a running call.

Usage: sched_transfer [+]<time> <uuid> <extension> [<dialplan>] [<context>]

###stun###
Executes a STUN lookup.
Usage:
    stun <stunserver>[:port]

Example:
    stun stun.freeswitch.org

###system###

Execute a system command.

Usage: system <command>

The command is passed to the system shell, where it may be expanded or interpreted in ways you don't expect. This can lead to security bugs if you're not careful. For example, the following command is dangerous:

  <action application="system" data="log_caller_name ${caller_id_name}" />

If a malicious remote caller somehow sets their caller ID name to "; rm -rf /", you would unintentionally be executing this shell command:

  log_caller_name; rm -rf /

###time_test###

Time test.

Usage: time_test <mss> [count]

Runs a test to see how bad timer jitter is.  It runs the test count times (default 10) and tries to sleep for mss microseconds.  It returns the actual timer duration along with an average.

Sample:
<pre>
time_test 100 5

test 1 sleep 100 99
test 2 sleep 100 97
test 3 sleep 100 96
test 4 sleep 100 97
test 5 sleep 100 102
avg 98
</pre>

###timer_test###

Timer test.

Usage: timer_test <10|20|40|60|120> [<1..200>] [<timer_name>]

Runs a test to see how bad timer jitter is.  Unlike time_test, this uses the actual freeswitch timer infrastructure to do the timer test and exercises the timers used for call processing.

First argument is the timer interval.
Second is the count.
Third is the timer name ("show timers" will give you a list)

Example:
<pre>
timer_test 20 3

Avg: 16.408ms Total Time: 49.269ms

2010-01-29 12:01:15.504280 [CONSOLE] mod_commands.c:310 Timer Test: 1 sleep 20 9254
2010-01-29 12:01:15.524351 [CONSOLE] mod_commands.c:310 Timer Test: 2 sleep 20 20042
2010-01-29 12:01:15.544336 [CONSOLE] mod_commands.c:310 Timer Test: 3 sleep 20 19928
</pre>

###tone_detect###

Start Tone Detection on a channel.

Usage: tone_detect <uuid> <key> <tone_spec> [<flags> <timeout> <app> <args>] <hits>

###unsched_api###

Unschedule an api command.

Usage: unsched_api <task_id>

###url_decode###

Usage: url_decode <string>

Url decode a string.

###url_encode###

Url encode a string.

Usage: url_encode <string>

###user_data###
Retrieves user information (parameters or variables) as defined in the directory.

Usage:  user_data <user>@<domain> [attr|var|param] <name>

Where user is the user's id, domain is the user's domain, var|param specifies whether the info we're requesting is a variable/parameter, and the name is the name (key) of the variable.

Example:

    user_data 1000@192.168.1.101 param password

will return a result of 1234, and 

    user_data 1000@192.168.1.101 var accountcode

will return a result of 1000 from the example user shown in [[Mod_commands#user_exists|user_exists]], and

    user_data 1000@192.168.1.101 attr id

will return the user's actual alphanumeric ID (i.e. "john") when number-alias="1000" was set as an attribute for that user.

###user_exists###
Checks to see if a user exists; Matches user tags found in the directory and returns either true/false:

Usage: user_exists <key> <user> <domain>

Where key references a key specified in a directory's user tag, user represents the value of the key, and the domain is the domain the user is assigned to.

Example:

    user_exists id 1000 192.168.1.101

will return true where there exists in the directory a user with a key called id whose value equals 1000:
<source lang="xml">
    <user id="1000" randomvar="45">
        <params>
          <param name="password" value="1234"/>
          <param name="vm-password" value="1000"/>
        </params>
        <variables>
          <variable name="accountcode" value="1000"/>
          <variable name="user_context" value="default"/>
          <variable name="effective_caller_id_name" value="Extension 1000"/>
          <variable name="effective_caller_id_number" value="1000"/>
        </variables>
    </user>
</source>
In the above example, we also could have tested for randomvar:

    user_exists randomvar 45 192.168.1.101

And we would have received the same results, but:

    user_exists accountcode 1000 192.168.1.101

or,

    user_exists password 1000 192.168.1.101

Would have returned false.

##See Also##
* [[Channel_Variables|Channel Variables]]

[[Category:Integration]]
[[Category:Configuration]]
[[Category:API]]
[[Category:Modules]]


