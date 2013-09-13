---
title: Lua
layout: default
---

# 目录：

	* 1 Lua特性
		* 1.1 写IVR脚本
		* 1.2 写事件钩子
		* 1.3 Serve configs (与mod_xml_curl功能相同)
		* 1.4 从lua中发起API呼叫
		* 1.5 轻量级
		* 1.6 高度内嵌
		* 1.7 关于lua学习
		* 1.8 Cli中的lua与luarun
			* 1.8.1 参数传递

	* 2 配置
		* 2.1 事件钩子
			* 2.1.1 事件钩子脚本
		* 2.2 针对IVR用途的配置
		* 2.3 针对API呼叫的配置
		* 2.4 调用其他lua脚本
		* 2.5 提供配置文件服务
		* 2.6 lua自启动脚本配置

	* 3 拨号方案示例
	* 4 拨号方案示例 - 内嵌扩展
	* 5 IVR示例
		* 5.1 Hello Lua示例

	* 6 模式匹配 (正则表达式)
		* 6.1 API函数regex示例
		* 6.2 Lua自带模式匹配

	* 7 杂例
		* 7.1 运行shell命令

	* 8 更多示例
	* 9 FAQ
		* 9.1 我的debug信息在哪里?
		* 9.2 如何使用第三方的lua脚本或模块?
		* 9.3 如何让FreeSWITCH使用系统安装的lua环境？
		* 9.4 第三方类库
		* 9.5 怎么让lua通过require函数识别我自己的库？
		* 9.6 如何通过ODBC访问数据库?
		* 9.7 如何找出有用但是非正式的Session函数?
		* 9.8 如何判断文件是否存在?

	* 10 API
		* 10.1 Events
			* 10.1.1 event:addBody
			* 10.1.2 event:addHeader
			* 10.1.3 event:delHeader
			* 10.1.4 event:fire
			* 10.1.5 event:getBody
			* 10.1.6 event:getHeader
			* 10.1.7 event:getType
			* 10.1.8 event:serialize
			* 10.1.9 event:setPriority
			* 10.1.10 Sending an Event

		* 10.2 Sessions
			* 10.2.1 session:answer
			* 10.2.2 session:answered
			* 10.2.3 session:bridged
			* 10.2.4 session:check_hangup_hook
			* 10.2.5 session:collectDigits
			* 10.2.6 session:consoleLog
			* 10.2.7 session:destroy
			* 10.2.8 session:execute
			* 10.2.9 session:executeString
			* 10.2.10 session:flushDigits
			* 10.2.11 session:flushEvents
			* 10.2.12 session:get_uuid
			* 10.2.13 session:getDigits
			* 10.2.14 session:getState
			* 10.2.15 session:getVariable
			* 10.2.16 session:hangup
			* 10.2.17 session:hangupCause
			* 10.2.18 session:hangupState
			* 10.2.19 session:insertFile
			* 10.2.20 session:mediaReady
			* 10.2.21 session:originate
			* 10.2.22 session:playAndGetDigits
				* 10.2.22.1 Syntax
				* 10.2.22.2 Arguments
				* 10.2.22.3 Discussion
				* 10.2.22.4 Examples

			* 10.2.23 session:preAnswer
			* 10.2.24 session:read
			* 10.2.25 session:ready
			* 10.2.26 session:recordFile
			* 10.2.27 session:sayPhrase
			* 10.2.28 session:sendEvent
			* 10.2.29 session:setAutoHangup
			* 10.2.30 session:setHangupHook
			* 10.2.31 session:setInputCallback
			* 10.2.32 session:setVariable
			* 10.2.33 session:sleep
			* 10.2.34 session:speak
			* 10.2.35 session:say
			* 10.2.36 session:streamFile
			* 10.2.37 session:transfer
			* 10.2.38 session:unsetInputCallback
			* 10.2.39 session:waitForAnswer

		* 10.3 Non-Session API
			* 10.3.1 freeswitch.API
			* 10.3.2 freeswitch.bridge
			* 10.3.3 freeswitch.consoleCleanLog
			* 10.3.4 freeswitch.consoleLog
			* 10.3.5 freeswitch.Dbh
			* 10.3.6 freeswitch.email
			* 10.3.7 freeswitch.Event
			* 10.3.8 freeswitch.EventConsumer
			* 10.3.9 freeswitch.getGlobalVariable
			* 10.3.10 freeswitch.IVRMenu
			* 10.3.11 freeswitch.msleep
			* 10.3.12 freeswitch.Session
			* 10.3.13 stream:write
				* 10.3.13.1 API commands
				* 10.3.13.2 Web page interaction (via mod_xml_rpc)

			* 10.3.14 Example: Call Control
			* 10.3.15 Special Case: env object
	   * 11 See Also


## Features ##

#### 写IVR脚本 ####
Lua的语法非常简单易用。查看示例： [Hello Lua](#Hello_Lua) 脚本。

#### 写事件钩子 ####
你可以定义一个Lua脚本，用于每次特定事件被触发的时候执行。  查看示例: [Event_Hooks](#Mod_lua)

#### Serve configs (与mod_xml_curl功能相同) ####
Lua可以为xml_curl模块提供配置文件服务，不需要xml_curl去请求web服务器。具体请看：[Serving_Configuration](#Mod_lua)

#### 从lua中发起API呼叫 ####
[Examples](#Make_API_calls)

#### 轻量级 ####
精简过的mod_lua.so文件只有272k大小。

#### 高度内嵌 ####
就嵌入能力来说，Python得分2，Perl得分4，JavaScript得分5，而Lua是10！

#### 关于Lua学习 ####
这里有一份Lua与JavaScript在某些特性方面的对比，详见[Learning Lua From JS](http://phrogz.net/lua/LearningLua_FromJS.html).

#### Cli中的lua与luarun ####
你可以通过使用命令“luarun /path/to/script.lua”，启动一个线程来跑你的lua脚本。“lua”命令用于拨号方案的内联lua，如 ${lua(codehere)}。“luarun”会创建一个进程来异步运行，而“lua”将会阻塞直到代码执行结束。在参数前面加上“~”，会运行单行的lua命令。
需要注意的是，通过luarun执行的脚本不能通过stream：write API向控制台写入，因为没有stream对象。

##### 参数传递 #####
在向lua传递参数时，是用空格隔开各个参数值，如下：
 luarun arg1 arg2 arg3

lua中是以argv对象来获取传递进来的参数，如下：
 my_first_var = argv[1];
 my_next_var = argv[2];
以此类推。。。

	 freeswitch@DVORAK> lua ~print(string.find("1234#5678", "(%d+)#(%d+)"))
	 1       9       1234    5678
	 freeswitch@DVORAK> luarun ~print(string.find("1234#5678", "(%d+)#(%d+)"))
	 +OK
	 1       9       1234    5678
	 freeswitch@DVORAK> luarun ~stream:write("1234#5678")
	 +OK
	 2011-06-20 13:35:35.274782 [ERR] mod_lua.cpp:191 [string "line"]:1: attempt to index global 'stream' (a nil value)
	 stack traceback:
	        [string "line"]:1: in main chunk
	 freeswitch@DVORAK> lua ~stream:write("1234#5678")
	 1234#5678

##配置 ##

### 事件钩子 ###
下面的配置实例将会告诉你如何在每次DETECTED_TONE事件被触发的时候，执行tone\_event.lua脚本。

	<configuration name="lua.conf" description="LUA Configuration">
	  <settings>
	     <param name="script-directory" value="$${base_dir}/scripts/?.lua"/>
	     <hook event="DETECTED_TONE" script="tone_event.lua"/>
	  </settings>
	</configuration>

#### 事件钩子脚本 ####
这是一个事件钩子脚本示例，通过调用event对象的getHeader()方法来获取事件的相关信息。

	local uuid = event:getHeader("Unique-ID")
	local tone = event:getHeader("Detected-Tone")
	freeswitch.consoleLog("info", uuid .. " detected tone: " .. tone .. "\n")


### 针对IVR用途的配置 ###

不需要任何配置。

### 针对API呼叫的配置 ###
	api = freeswitch.API();
	digits = api:execute("regex", "testing1234|/(\\d+)/|$1");
	-- The returned output of the API call is stored in the variable if you need it.
	freeswitch.consoleLog("info", "Extracted digits: " .. digits .. "\n")
注：请务必对传入的参数进行转义，像上面正则表达式字符串一样。


### 调用其他lua脚本 ###

	api = freeswitch.API();
	reply = api:executeString("luarun another.lua");


### 提供配置文件服务 ###
FreeSWITH是从静态XML文件中请求并加载配置文件数据，而Lua模块可以替换该操作，使用脚本提供该服务，更多信息详见[Serving\_Configuration]()

### Lua自启动脚本配置 ###

下面是最小的Lua配置文件：

	<configuration name="lua.conf" description="LUA Configuration">
	  <settings>
	    <!--
		The following options identifies a lua script that is launched
		at startup and may live forever in the background.
		You can define multiple lines, one for each script you
		need to run.
	    -->
	    <!--<param name="startup-script" value="startup_script_1.lua"/>-->
	    <!--<param name="startup-script" value="startup_script_2.lua"/>-->
	  </settings>
	</configuration>

参数startup-script用于配置在FreeSWITCH启动时，加载的lua脚本文件（位于scripts/目录下）。
这些脚本分别运行在各自独立的线程中。你可以利用这些脚本处理一些简单的任务（处理完就关闭），或者让这些脚本处于死循环中，进行监控事件、发起呼叫等操作。

## 拨号方案示例 ##

	 <action application="lua" data="helloworld.lua arg1 arg2"/>

注1：在脚本中，可以通过argv[1]和argv[2]来访问传递进来的参数。
注2：默认到prefix/scripts目录中寻找helloworld.lua文件。

## 拨号方案示例-内嵌扩展 ##

	 示例1:<action application="set" data="MY_VAR=${lua(helloworld.lua arv1 arg2)}"/>
	 示例2：<action application="set" data="MY_VAR=${lua(helloworld.lua $1)}" />
	 示例3: <action application="set" data="MY_VAR=${lua(helloworld.lua $1 ${caller_id_number})}" />
	 示例4: <action application="set" data="MY_VAR=${lua(helloworld.lua ${caller_id_number})}" inline="true" />

 	 示例5: <condition field="${lua(helloworld.lua arv1 arg2)}" expression="^Hello World$" >

## IVR示例 ##

###<span id="Hello_Lua">Hello Lua </span>###

	-- 接听来电
	session:answer();

	-- 休眠1秒
	session:sleep(1000);

	-- 播放语音提示文件
	session:streamFile("/path/to/blah.wav");

	-- 挂机
	session:hangup();

## 模式匹配（正则表达式） ##

### API函数regex示例 ###
通过这种方式，你可以在lua脚本内执行正则表达式条件（感谢 bkw_）。

	session:execute("set", "some_chan_variable=${regex(" .. destination .. "|^([0-9]{10})$)}")

如果destination是一个lua变量，用于存储你拨打的目标号码，同时你的正则表达式是^([0-9]{10})$
在上述命令执行完毕后，匹配的结果将会放入"some_chan_variable"这个通道变量中，在lua脚本中通过session:getVariable即可获取到结果。

同样，通过下面的命令

	session:execute("set", "some_chan_variable=${regex(" .. destination .. "|^(0\\|61)([2,3,7,8][0-9]{8})$|$2)}")

来匹配并返回捕获到的值。


### Lua自带的模式匹配 ###
Lua支持一种简单但同样强大的模式匹配语法。虽然没有PCRE强大，但是却能处理脚本中绝大部分模式匹配问题。
下面是一个简单脚本，可以通过fs_cli中的luarun运行，主要用来展示字符串捕获：

	-- pattern.lua
	data = "1234#5678";
	_,_,var1,var2 = string.find(data,"(%d+)#(%d+)");
	freeswitch.consoleLog("INFO","\ndata: " .. data .. "\nvar1: " .. var1 .. "\nvar2: " .. var2 .. "\n");

	Output:
	freeswitch@internal> luarun pattern.lua
	+OK

	2011-04-18 08:28:49.242080 [INFO] switch_cpp.cpp:1197
	data: 1234#5678
	var1: 1234
	var2: 5678

其他资料:
* FreeSWITCH书149-151页
* http://www.lua.org/pil/20.2.html 和 http://www.lua.org/pil/20.3.html
* http://www.lua.org/manual/5.1/manual.html#5.4.1

## 杂项 ##

### 运行Shell命令 ###
当使用session:execute()和api:execute()去执行shell命令（如Bash脚本）的时候，会只返回整型的错误码。
如果需要获取shell命令的返回值，可以使用io.popen()方法。下面的例子来自http://lua-users.org/wiki/ShellAccess.

	  function shell(c)
	    local o, h
	    h = assert(io.popen(c,"r"))
	    o = h:read("*all")
	    h:close()
	    return o
	  end

## 更多示例 ##
* See scripts/lua directory on the file system
* [[IVR|Example IVRs]]
* [[Lua MythTV alert example]]
* [[Fakecall responder]]
* [[Fun Lua Examples]]
* [[Call retry based on hangup cause]]
* [[Bridging two calls with retry]]

## FAQ ##
### 我的调试信息在哪里 ###
Q:当我使用静态XML或xml\_curl（去执行命令）时，能通过fs_cli和xml\_cdr文件的“application log”节点看到执行的命令日志。但是，当我通过lua脚本去执行命令的时候，去怎么也看不到这些信息。

A: 在lua脚本中，当你有一个真实可用的呼叫会话时（译者注：比如从拨号方案中转入lua脚本时，可以使用session对象来操作此次呼叫），可以使用session:execute("$application","$data")命令，使用该方法会在fs_cli和xml\_cdr的日志中显示出命令执行情况。
但如果没有呼叫会话，比如你的lua脚本是在后台运行或从cli启动的，那你只能使用其他不能记录日志的命令。

### 如何使用第三方的lua脚本或模块? ###

Q: 我需要把自己的lua文件放到什么地方，以便让FreeSWITCH能读取到。
我正在运行一个/scripts目录下面的lua脚本，但是它需要包含另一个lua文件。

A: 答案是/usr/local/share/lua/5.1/
或者，你可以安装系统lua环境（通过apt-get或yum），freeswitch内嵌的lua会到插件目录中去查找库文件。

（下面的英文暂不翻译，没开发好，翻译有个毛用！）
To do this in the mod_lua.conf file (currently not possible), the following development would be needed.

 * Install them to a nonstandard.
 * Push a nonstandard place into the path of where it looks.

'''NOTE:''' Assuming you have <param name="module-directory" value="$${base_dir}/scripts/?.so"/> in lua.conf.xml, in the scripts, require statements in the form of:

 require "luasql.mysql"

This will look for the shared object ${base_dir}/scripts/luasql/mysql.so

'''NOTE:''' The native MySQL driver for Lua has a very bad memory leak. Do not use it.

### 怎么让FreeSWITCH使用系统lua环境？ ###

Q: 我已经安装好了lua环境，但是mod_lua貌似忽略掉我安装的lua。

A: Lua太小了，以至于整个lua库被静态链接到模块上。

### 第三方类库 ###

Q : 能对FreeSWITCH使用luarocks吗?

A : 可以，luarocks是lua的包库管理器。它可以将库安装到系统目录中，然后你就可以通过FreeSWITCH中的lua来引用它们。为了能正常安装luarocks，你同样需要在系统中安装lua环境。

举例来说，如果你想在Ubuntu 12.04上面使用LuaXML库，则需要如下操作：

	sudo apt-get install lua-5.1 luarocks
	luarocks install luaxml

然后，编辑/usr/local/freeswitch/conf/autoload_configs/lua.conf.xml文件，取消下面的注释，如下：

    <param name="module-directory" value="/usr/lib/lua/5.1/?.so"/>
    <param name="module-directory" value="/usr/local/lib/lua/5.1/?.so"/>

现在，FreeSWITCH中的lua脚本就可以使用XML相关的方法了，示例如下：

    require("LuaXml")
    local xobj = xml.eval('<Cmd Message="Hello"/>')
    freeswitch.consoleLog("INFO","The message in the XML is "..xobj["Message"].."\n")


### 怎么让lua通过require函数识别我自己的库？ ###
Q: 在FreeSWITCH的lua脚本中，我能通过require函数将其他lua库包含进来不？

A: 你可以通过修改环境变量LUA_PATH，以便告诉FreeSWITCH的内置Lua如何找到你的库。
下面是一个简单的实现脚本：

	 #!/bin/bash
	 export LUA_PATH=/usr/local/freeswitch/scripts/?.lua\;\;
	 ulimit -s 240
	 screen /usr/local/freeswitch/bin/freeswitch

默认的路径为/usr/local/share/lua/5.1/，需要根据情况修改。

还有一种方式，是使用‘dofile’命令，如下：
eg. dofile("/home/fred/scripts/fredLuaFunctions.lua")

注：dofile只是把文件中包含的命令，当做一条命令来执行，和创建lua模块不一样。

### 能通过ODBC访问数据库不? ###
可以。有两种方式来访问，分别是自带的freeswitch.Dbh和luaSQL模块。这里主要介绍第二种方法。

通过LuaSQL，你不仅可以访问ODBC数据源，还可以访问PostgreSQL, Oracle和MySQL。LuaSQL自己实现了对这些数据库的连接。
想了解更多的话，查看http://www.keplerproject.org/luasql/

下面是安装LuaSQL的简短说明。
提醒下，在X64_86平台上面，配置文件要稍作更改。

	http://luaforge.net/frs/download.php/2686/luasql-2.1.1.tar.gz
	tar xfvz luasql-2.1.1.tar.gz
	cd luasql-2.1.1/

配置文件分成三个部分：
1、数据库名称
2、指向不同库的路径设置
3、执行数据库相关库的路径设置

第一步，根据操作系统类型，调整路径的设置方式
第二步，选择一种数据库驱动进行编译（每次只能编译一个驱动）。如编译MySQL，需要取消配置文件#1和#3中关于MySQL的注释，其他配置行需要注释掉。

注：在RHEL/CentOS中，LuaSQL默认的指向MySQL的libs和include的路径，不是真实路径，需要做如下调整：

	DRIVER_LIBS= -L/usr/lib/mysql -lmysqlclient -lz
	DRIVER_INCS= -I/usr/include/mysql

示例: 连接Microsoft SQL Server配置，

	sed -i 's/#T= odbc/T= odbc/g' config
	sed -i 's/T=sqlite3/#T=sqlite3/g' config

	DRIVER_LIBS= -L/usr/lib64 -lodbc
	DRIVER_INCS= -DUNIXODBC -I/usr/include

根据真实安装环境设置LUA_LIBDIR, LUA_DIR , LUA_INC , DRIVER_LIBS, DRIVER_INCS

为了编译顺利，修改如下：

	sed -i 's/WARN= /WARN= -fPIC /g' config


编译...

	make
	make install

你要先下载安装Lua，然后下载LuaSQL，针对你要的数据库模块进行编译安装。下一步就是收获的时候了，用法如下：

	#!/usr/local/bin/lua
	require "luasql.mysql"

	env = assert (luasql.mysql())
	con = assert (env:connect("database","username","password","localhost"))
	cur = assert (con:execute"SELECT * FROM table")
	row = cur:fetch ({}, "a")

	session:setVariable("varname", tostring(row.column));

	cur:close()
	con:close()
	env:close()


对于配置ODBC，你需要编辑odbc.ini和odbcinst.ini文件（RHEL默认在/etc/目录下）。
以MySQL为例，

	File: odbcinst.ini
	# Driver from the MyODBC package
	# Setup from the unixODBC package
	[MySQL]
	Description     = ODBC for MySQL
	Driver          = /usr/lib/libmyodbc.so
	Setup           = /usr/lib/libodbcmyS.so
	FileUsage       = 1

注：需要确保lib目录中有libmyodbc.so和libodbcmyS.so文件

	File: odbc.ini
	[mydsn]
	Driver     = MySQL
	SERVER     = localhost
	PORT       = 3306
	DATABASE   = mydatabase
	OPTION     = 67108864
	SOCKET     = /var/lib/mysql/mysql.sock

注1：为了让脚本正常执行，你还得设置一些环境变量，

	echo export LUA_PATH=/usr/local/freeswitch/scripts/?.lua >> /etc/bashrc
	echo export LUA_CPATH=/usr/local/freeswitch/scripts/?.so >> /etc/bashrc
	echo export PATH=$PATH:/usr/local/freeswitch/bin >> ~/.bashrc

注2：你需要将共享库，如mysql.so，符号连接到/usr/local/lib/lua/5.1/luasql/mysql.so

警告：该修改打破了原先外部lua模块的加载方式
http://fisheye.freeswitch.org:8081/changelog/FreeSWITCH?cs=9605

注3： 上述修改已被修复，http://fisheye.freeswitch.org:8081/changelog/FreeSWITCH?cs=10306

### 如何找出非正式公布出来的Session函数? ###

有时会发生这样的情况，增加了新函数，但是没有更新文档。下面的脚本可能会给你些帮助：

	-- This function simply tells us what function are available in Session
	--   It just prints a list of all functions.  We may be able to find functions
	--   that have not yet been documented but are useful.  I did :)
	function printSessionFunctions( session )

	   metatbl = getmetatable(session)
	   if not metatbl then return nil end

	   local f=metatbl['.fn'] -- gets the functions table
	   if not f then return nil end

	   print("\n***Session Functions***\n")
	   for k,v in pairs(f) do print(k,v) end
	   print("\n\n")

	end

	new_session = freeswitch.Session() -- create a blank session

	printSessionFunctions(new_session)


在freeswitch版本16256上，该脚本输出如下：

	process_callback_result function: 0x79b380
	flushDigits     function: 0x798db0
	execute function: 0x798ed0
	setAutoHangup   function: 0x798de0
	collectDigits   function: 0x798c30
	mediaReady      function: 0x7993d0
	speak   function: 0x79b2d0
	setHangupHook   function: 0x799510
	getDigits       function: 0x798c60
	check_hangup_hook       function: 0x799380
	playAndGetDigits        function: 0x798cf0
	getState        function: 0x79b1e0
	hangupState     function: 0x79b4e0
	say     function: 0x79b150
	recordFile      function: 0x79b210
	waitForAnswer   function: 0x798ea0
	sleep   function: 0x798d50
	setEventData    function: 0x798f30
	setPrivate      function: 0x79b540
	setLUA  function: 0x7995d0
	begin_allow_threads     function: 0x799320
	setInputCallback        function: 0x7994e0
	unsetInputCallback      function: 0x799470
	run_dtmf_callback       function: 0x799400
	get_cb_args     function: 0x799020
	read    function: 0x798cc0
	getPrivate      function: 0x79b570
	answer  function: 0x79b450
	setVariable     function: 0x79b510
	getXMLCDR       function: 0x798f60
	originate       function: 0x799570
	destroy function: 0x7992f0
	answered        function: 0x798e70
	set_tts_parms   function: 0x79b300
	sendEvent       function: 0x798f00
	ready   function: 0x799540
	preAnswer       function: 0x79b4b0
	streamFile      function: 0x798d20
	hangupCause     function: 0x79b1b0
	setDTMFCallback function: 0x79b2a0
	getVariable     function: 0x79b350
	transfer        function: 0x798c90
	get_uuid        function: 0x798ff0
	hangup  function: 0x79b480
	end_allow_threads       function: 0x799350
	flushEvents     function: 0x798d80
	sayPhrase       function: 0x79b180


### 如何测试文件是否存在? ###

在Lua中,你可以使用API命令中的file_exists来判断文件是否存在。

下面的例子用来检查hello.wav文件是否存在于/usr/local/freeswitch/sounds/messages目录中。
如果存在，使用playback函数向主叫播放该语音文件。
如果不存在，则播放goodbye.wav文件。

	 local message_location = "/usr/local/freeswitch/sounds/messages/"
	 local message = "hello.wav"

	 message = message_location .. message
	 session:consoleLog("debug", "file_exists: Check for message1: ".. message .."\n")

	 api = freeswitch.API(); -- create API-session
	 reply = api:executeString("file_exists " .. message); -- execute file_exists with message and return result in reply

	 if reply ## "true" then
	     session:consoleLog("info", "file_exists: Initial file found. Playing " .. message"\n")
	 else
	     message = message_location .. "goodbye.wav"
	     session:consoleLog("info", "file_exists: Initial file not found. Playing " .. message"\n")
	 end
	 session:sleep(250) -- making sure that the beginning of the file is not skipped
	 session:execute("playback", message)

## API ##
### Events ###

下面的这些方法用于生成事件

####event:addBody####

	--Create Custom event

	custom_msg = 	"dial_record_id: " .. dial_record_id .. "\n" ..
			"call_disposition: " .. Disposition .. "\n" ..
			"campaign_number: "  .. Campaign .. "\n" ..
			"called_number: "    .. dial_num .."\n"  ;
			local e = freeswitch.Event("custom", "dial::dial-result");


	e:addBody(custom_msg);
	e:fire();

在事件体body中，随你添加需要的内容。在上面的例子中，定义了4个条目来发送。

结果如下：

	[Content-Length] => 555
	    [Content-Type] => text/event-plain
	    [Body] => Array
	        (
	            [Event-Subclass] => dial::dial-result
	            [Event-Name] => CUSTOM
	            [Core-UUID] => 2dc7cc50-b157-4868-ae16-04e5f4b95dae
	            [FreeSWITCH-Hostname] => pp6.noble.co.uk
	            [FreeSWITCH-IPv4] => 192.168.0.106
	            [FreeSWITCH-IPv6] => ::1
	            [Event-Date-Local] => 2009-02-17 23:15:49
	            [Event-Date-GMT] => Tue, 17 Feb 2009 23:15:49 GMT
	            [Event-Date-Timestamp] => 1234912549610060
	            [Event-Calling-File] => switch_cpp.cpp
	            [Event-Calling-Function] => fire
	            [Event-Calling-Line-Number] => 297
	            [Content-Length] => 85
	            [Body] => Array
	                (
	                    [dial_record_id] => 1234
	                    [call_disposition] => AA
	                    [campaign_number] => 20
	                    [called_number] => 7777777
	                )

	        )

	)



####event:addHeader####


####event:delHeader####

####event:fire####
bkw童鞋提供了下面的例子：

	local event = freeswitch.Event("message_waiting");
	event:addHeader("MWI-Messages-Waiting", "no");
	event:addHeader("MWI-Message-Account", "sip:1000@10.0.1.100");
	event:addHeader("Sofia-Profile", "internal");
	event:fire();


####event:getBody####

####event:getHeader####
这是一个常用的API调用。

	event:getHeader("Caller-Caller-ID-Name")

或者，在dialplan.lua中使用该函数获取某些信息：

	params:getHeader("variable_sip_req_uri")


####event:getType####



####event:serialize####
该函数用于向控制台输出所有的头部参数（Headers）。

	-- Print as text
	io.write(params:serialize());
	io.write(params:serialize("text"));

	-- Print as JSON
	io.write(params:serialize("json"));

或者，作为info日志信息输出，

	freeswitch.consoleLog("info",params:serialize())


####event:setPriority####

####Sending an Event####
使用luarun执行下面的命令，以用来控制注册话机MWI灯的开启和关闭。

	local event = freeswitch.Event("message_waiting");
	event:addHeader("MWI-Messages-Waiting", "no");
	event:addHeader("MWI-Message-Account", "sip:1002@10.0.1.100");
	event:fire();


### Sessions ###
下面的方法适用于存在session对象的lua脚本中。

####session:answer####

接听通话:

	session:answer();


####session:answered####
用于检查会话是否被标记为已接听（只要通话被接听，就总是为true）

####session:bridged####

用于检查当前会话通道是否桥接到其他会话通道。

	if (session:bridged() == true) do
	    -- Do something
	end

####session:check_hangup_hook####

####session:collectDigits####

####session:consoleLog####

通过session对象，向freeswitch日志记录器写入日志。参数分别为日志级别和日志消息。

	session:consoleLog("info",   "lua rocks\n");
	session:consoleLog("notice", "lua rocks\n");
	session:consoleLog("err",    "lua rocks\n");
	session:consoleLog("debug",  "lua rocks\n");
	session:consoleLog("warning","lua rocks\n");

####session:destroy####

该函数用于销毁会话，释放资源。
当你的脚本执行结束的时候，该方法会被自动调用。
但是如果你的脚本中包含一个死循环，则需要使用该函数来停止会话。

####session:execute####

session:execute(app, data)

	local mySound = "/usr/local/freeswitch/sounds/music/16000/partita-no-3-in-e-major-bwv-1006-1-preludio.wav"

	session:execute("playback", mySound)

注：在execute命令执行过程中，不能执行回调函数（如DTMF监听等各种小伙伴）

####session:executeString####
等同于session:execute(api_string)

	local mySound = "/usr/local/freeswitch/sounds/music/16000/partita-no-3-in-e-major-bwv-1006-1-preludio.wav"

	session:executeString("playback "..mySound)

注：在execute命令执行过程中，不能执行回调函数（如DTMF监听等各种小伙伴）

####session:flushDigits####

####session:flushEvents####

####session:get_uuid####

####session:getDigits####
获取DTMF输入：
* 函数有三个参数：
  Get digits: 最大数, 终止键, 超时时长
* 最大数: 最多能收到几个DTMF信号（即最多能接到的按键数）
* 终止键: 当接收到字符后，停止DTMF收取
* 超时时长: 收取DTMF输入的最大时间（单位毫秒）
* 返回值：收到的DTMF输入字符串

该方法会处于堵塞状态，直到出现终止条件（如出现终止键或超时）

	digits = session:getDigits(5, "#", 3000);
	session:consoleLog("info", "Got dtmf: ".. digits .."\n");

####session:getState####

获取通话状态，如“CS_EXECUTE”。全部的状态详见switch_types.h。

	state=session:getState();

####session:getVariable####

用于获取系统变量，如${hold_music}

		local moh = session:getVariable("hold_music")
		--[[ events obtained from "switch_channel.c"
		 regards Monroy from Mexico
		]]
	    session:getVariable("context");
		session:getVariable("destination_number");
		session:getVariable("caller_id_name");
		session:getVariable("caller_id_number");
		session:getVariable("network_addr");
		session:getVariable("ani");
		session:getVariable("aniii");
		session:getVariable("rdnis");
		session:getVariable("source");
		session:getVariable("chan_name");
		session:getVariable("uuid");


####session:hangup####

你可以在挂断通话的时候，顺便指明挂机原因（可选），如下：

	session:hangup("USER_BUSY");

当然，还有下面无参数的挂机方式（挂机原因默认为normal_clearing），

	session:hangup(); -- default normal_clearing



####session:hangupCause####

通过该函数，可以获取到已接听通话的挂机原因，或获取发起的呼叫没有成功的原因。
具体挂机原因详见[[Hangup causes]].

	-- Initiate an outbound call

	obSession = freeswitch.Session("sofia/192.168.0.4/1002")

	-- Check to see if the call was answered

	if obSession:ready() then
	    -- Do something good here

	else    -- This means the call was not answered ... Check for the reason

	    local obCause = obSession:hangupCause()

	    freeswitch.consoleLog("info", "obSession:hangupCause() = " .. obCause )

	    if ( obCause == "USER_BUSY" ) then              -- SIP 486
	       -- For BUSY you may reschedule the call for later
	    elseif ( obCause == "NO_ANSWER" ) then
	       -- Call them back in an hour
	    elseif ( obCause == "ORIGINATOR_CANCEL" ) then   -- SIP 487
	       -- May need to check for network congestion or problems
	    else
	       -- Log these issues
	    end
	end

####session:hangupState####

####session:insertFile####

 session:insertFile(<orig_file>, <file_to_insert>, <insertion_sample_point>)

Inserts one file into another.  All three arguments are required.  The third argument is in samples, and is the number of samples into orig_file that you want to insert file_to_insert.  The resulting file will be written at the sample rate of the session, and will replace orig_file.

Because the position is given in samples, you'll need to know the sample rate of the file to properly calculate how many samples are X seconds into the file.  For example, to insert a file two seconds into a .wav file that has a sample rate of 8000Hz, you would use 16000 for the insertion_sample_point argument.

Note that this method requires an active channel with a valid session object, as it needs the sample rate and the codec info from the session.

Examples:

On a ulaw channel, insert bar.wav one second into foo.wav:
  session:insertFile("foo.wav", "bar.wav", 8000)

Prepend bar.wav to foo.wav:
  session:insertFile("foo.wav", "bar.wav", 0)

Append bar.wav to foo.wav:
  session:insertFile("bar.wav", "foo.wav", 0)

####session:mediaReady####

####session:originate####
session:originate is deprecated, use the following construct instead:

 new_session = freeswitch.Session("sofia/gateway/gatewayname/18001234567", session);

''The code below is here for the sake of history only; please do not use it going forward.''

<pre>
 -- this usage of originate is deprecated, use freeswitch.Session(dest, session)
 new_session = freeswitch.Session();
 new_session.originate(session, dest[, timeout]);
</pre>

dest - quoted dialplan destination. For example: "sofia/internal/1000@10.0.0.1" or "sofia/gateway/my_sip_provider/my_dest_number"<br>
timeout - origination timeout in seconds

Note: session.originate expects at least 2 arguments.

####session:playAndGetDigits####

Plays a file and collects DTMF digits.   Digits are matched against a regular expression.  Non-matching digits or a timeout can trigger the playing of an  audio file containing an error message.  Optional arguments allow you to transfer to an extension on failure, and store the entered digits into a channel variable.

#####Syntax#####

<pre>digits = session:playAndGetDigits (
          min_digits, max_digits, max_attempts, timeout, terminators,
          prompt_audio_files, input_error_audio_files,
          digit_regex, variable_name, digit_timeout,
          transfer_on_failure)
</pre>

#####Arguments#####
<blockquote>
{| valign="top"
|<tt>min_digits</tt> || The minimum number of digits required.
|- valign="top"
|<tt>max_digits</tt> || The maximum number of digits allowed.
|- valign="top"
|<tt>max_attempts</tt> || The number of times this function waits for digits and replays the <tt>prompt_audio_file</tt> when digits do not arrive.
|- valign="top"
|<tt>timeout</tt> || The time (in milliseconds) to wait for a digit.
|- valign="top"
|<tt>terminators</tt> || A string containing a list of digits that cause this function to terminate.
|- valign="top"
|<tt>prompt_audio_file</tt> || The initial audio file to play.  Playback stops if digits arrive while playing.  This file is replayed after each timeout, up to <tt>max_attempts</tt>.
|- valign="top"
|<tt>input_error_audio_file</tt> || The audio file to play when a digit not matching the <tt>digit_regex</tt> is received.  Received digits are discarded while this file plays. Specify an empty string if this feature is not used.
|- valign="top"
|<tt>digit_regex</tt> || The regular expression used to validate received digits.
|- valign="top"
|<tt>variable_name</tt> || '''(Optional)''' The channel variable used to store the received digits.
|- valign="top"
|<tt>digit_timeout</tt> || '''(Optional)''' The inter-digit timeout (in milliseconds).  When provided, resets the <tt>timeout</tt> clock after each digit is entered, thus giving users with limited mobility the ability to slowly enter digits without causing a timeout.  If not specified, <tt>digit_timeout</tt> is set to <tt>timeout</tt>.
|- valign="top"
|<tt>transfer_on_failure</tt> || '''(Optional)''' In the event of a failure, this function will transfer the session to an extension in the dialplan.  The syntax is "''extension-name'' <tt>[</tt>''dialplan-id'' [''context'']]".
|}
</blockquote>
#####Discussion#####

*This function returns an empty string when all timeouts and retry counts are exhausted.
*When the maximum number of allowable digits is reached, the function returns immediately, even if a terminator was not entered.
*If the user forgets to press one of the terminators, but has made a correct entry, the digits are returned after the next timeout.
*The session has to be answered before any digits can be processed.  If you do not answer the call you, the audio will still play, but no digits will be collected.

#####Examples#####

Example 1:

<blockquote>
<pre>
digits = session:playAndGetDigits(2, 5, 3, 3000, "#", "/prompt.wav", "/error.wav", "\\d+")
session:consoleLog("info", "Got DTMF digits: ".. digits .."\n")
</pre>

This example causes freeswitch to play ''prompt.wav'' and listen for between 2 and 5 digits, ending with the <tt>#</tt> key.  If the user enters nothing (or something other than a digit, like the <tt>*</tt> key) ''error.wav'' is played, and the process is repeated another two times.
</blockquote>

Example 2:

<blockquote>
<pre>
digits = session:playAndGetDigits(1, 1, 3, 3000, "", "/menu.wav", "/error.wav", "[134]", "digits_received", 3, "operator XML default")
session:consoleLog("info", "Got DTMF digits: ".. digits .."\n")
</pre>
This time, we require only one digit, and it must be <tt>1</tt>, <tt>3</tt> or <tt>4</tt>.  If the user does not comply after three attempts, they are transferred to the operator extension in the "default" XML dial plan.

If the user presses a correct key, that digit is returned to the caller, and the "digits_received" channel variable is set to the same value.
</blockquote>

Reminder: If you need to match the * key in the regular expression, you will have to quote it twice:

<pre>
digits = session:playAndGetDigits(2, 5, 3, 3000, "#", "/sr8k.wav", "", "\\d+|\\*");
</pre>

####session:preAnswer####

Pre answer the session:

<pre>
session:preAnswer();
</pre>

####session:read####

Play a file and get digits.

<pre>
digits = session:read(5, 10, "/sr8k.wav", 3000, "#");
session:consoleLog("info", "Got dtmf: ".. digits .."\n");
</pre>

session:read has 5 arguments: <min digits> <max digits> <file to play> <inter-digit timeout> <terminators>

####session:ready####
- checks whether the session is still active (true anytime between call starts and hangup)<br>
- also session:ready will return false if the call is being transferred.  Bottom line is you should always be checking session:ready on any loops and periodicly throughout your script and exit asap if it returns false.

See [[#session:hangupCause]] for more detail on if NOT ready.

<pre>
while (session:ready() ## true) do
   -- do something here
end
</pre>

####session:recordFile####

syntax is session:recordFile(file_name, max_len_secs, silence_threshold, silence_secs)

silence_secs is the amount of silence to tolerate before ending the recording.

Example:
<pre>

function onInputCBF(s, _type, obj, arg)
    local k, v = nil, nil
    local _debug = true
    if _debug then
        for k, v in pairs(obj) do
            printSessionFunctions(obj)
            print(string.format('obj k-> %s v->%s\n', tostring(k), tostring(v)))
        end
        if _type ## 'table' then
            for k, v in pairs(_type) do
                print(string.format('_type k-> %s v->%s\n', tostring(k), tostring(v)))
            end
        end
        print(string.format('\n(%s ## dtmf) and (obj.digit [%s])\n', _type, obj.digit))
    end
    if (_type ## "dtmf") then
        return 'break'
    else
        return ''
    end
end

recording_dir = '/tmp/'
filename = 'myfile.wav'
recording_filename = string.format('%s%s', recording_dir, filename)

if session:ready() then
    session:setInputCallback('onInputCBF', '');
    -- syntax is session:recordFile(file_name, max_len_secs, silence_threshold, silence_secs)
    max_len_secs = 30
    silence_threshold = 30
    silence_secs = 5
    test = session:recordFile(recording_filename, max_len_secs, silence_threshold, silence_secs);
    session:consoleLog("info", "session:recordFile() = " .. test )
end
</pre>

####session:sayPhrase####
Play a speech phrase macro.

 session:sayPhrase(macro_name [,macro_data] [,language]);

* macro_name - (string) The name of the say macro to speak.
* macro_data - (string) Optional. Data to pass to the say macro.
* language - (string) Optional.  Language to speak macro in (ie. "en" or "fr").  Defaults to "en".

To capture events or DTMF, use it in combination with [[Mod_lua#session:setInputCallback|session:setInputCallback]]

Example:

 function key_press(session, input_type, data, args)
   if input_type ## "dtmf" then
     session:consoleLog("info", "Key pressed: " .. data["digit"])
     return "break"
   end
 end
 if session:ready() then
   session:answer()
   session:execute("sleep", "1000")
   session:setInputCallback("key_press", "")
   session:sayPhrase("voicemail_menu", "1:2:3:#", "en")
 end

When used with setInputCallback, the return values and meanings are as follows:

* true or "true" - Causes prompts to continue speaking.
* Any other string value interrupts the prompt.

####session:sendEvent####

####session:setAutoHangup####

By default, lua script hangs up when it is done executing.  If you need to run the next action in your dialplan after the lua script, you will need to setAutoHangup to false.  The default value is true.

<pre>
session:setAutoHangup(false)
</pre>

####session:setHangupHook####

In your lua code, you can use setHangupHook to define the function to call when the session hangs up.

<pre>
function myHangupHook(s, status, arg)
    freeswitch.consoleLog("NOTICE", "myHangupHook: " .. status .. "\n")
    -- close db_conn and terminate
    db_conn:close()
    error()
end

blah="w00t";

session:setHangupHook("myHangupHook", "blah")
</pre>

Other possibilities to exit the script (and throwing an error)

<pre>
return "exit";
or
return "die";
or
s:destroy("error message");
</pre>

####session:setInputCallback####
<pre>
function my_cb(s, type, obj, arg)

   if (arg) then
      io.write("type: " .. type .. "\n" .. "arg: " .. arg .. "\n");
   else
      io.write("type: " .. type .. "\n");
   end

   if (type ## "dtmf") then
      io.write("digit: [" .. obj['digit'] .. "]\nduration: [" .. obj['duration'] .. "]\n");
   else
      io.write(obj:serialize("xml"));

      e = freeswitch.Event("message");
      e:add_body("you said " .. obj:get_body());
      session:sendEvent(e);
   end
end

blah="w00t";

session:answer();
session:setInputCallback("my_cb", "blah");
session:streamFile("/tmp/swimp.raw");
</pre>

When used outside of streaming a file to a channel the return values "true" or "undefined" are accepted as true(which continues the audio stream I believe), anything else will be evaluated as false(which would stop the stream).

Additional return values can be located in the file ./src/switch_ivr.c around line 3276 with the option for "speed". TODO: someone needs to get the list and document it.

####session:setVariable####

Set a variable on a session:
<pre>
session:setVariable("varname", "varval");
</pre>

####session:sleep####
<pre>
session:sleep(3000);
</pre>

* '''This will allow callbacks to DTMF to occur''' and session:execute("sleep", "5000"), won't.

####session:speak####
<pre>
session:set_tts_parms("flite", "kal");
session:speak("Please say the name of the person you're trying to contact");
</pre>

####session:say####
Plays pre-recorded sound files for things like numbers, dates, currency, etc.
Refer to [[Misc. Dialplan Tools say]] for info about the say application.

Arguments: <data><lang><say_type><say_method>

Example:
<pre>
session:say("12345", "en", "number", "pronounced");
</pre>

####session:streamFile####

Stream a file endless to the session

<pre>
session:streamFile("/tmp/blah.wav");
</pre>

Stream a file endless to the session starting at sample_count?
<pre>
session:streamFile("/tmp/blah.wav", <sample_count>);
</pre>

####session:transfer####

Transfer the current session.  The arguments are extensions, dialplan and context.
<pre>
session:transfer("3000", "XML", "default");
</pre>
execution of your lua script will immediately stop, make sure you set session:setAutoHangup(false) if you don't want your call to disconnect


If instead you do session:execute("transfer", "3000 XML default") then the execution of the LUA script continues even though the call is mostly out of your control now, and bridges most likely will fail.

####session:unsetInputCallback####

<pre>
session:unsetInputCallback()
</pre>


####session:waitForAnswer####

### Non-Session API ###
These methods are generic in that they do not apply to a session or an event. For example, printing data to the FreeSWITCH console is neither event- nor session-specific.
####freeswitch.API####
<pre>
api = freeswitch.API();
-- get current time in milliseconds
time = api:getTime()
</pre>

####freeswitch.bridge####
<pre>
session1 = freeswitch.Session("sofia/internal/1001%192.168.1.1");
session2 = freeswitch.Session("sofia/internal/1002%192.168.1.1");
freeswitch.bridge(session1, session2);
</pre>

####freeswitch.consoleCleanLog####

<pre>
freeswitch.consoleCleanLog("This Rocks!!!\n");
</pre>

####freeswitch.consoleLog####

Log something to the freeswitch logger.  Arguments are loglevel, message.

<pre>
freeswitch.consoleLog("info",   "lua rocks\n");
freeswitch.consoleLog("notice", "lua rocks\n");
freeswitch.consoleLog("err",    "lua rocks\n");
freeswitch.consoleLog("debug",  "lua rocks\n");
freeswitch.consoleLog("warning","lua rocks\n");
</pre>

#### freeswitch.Dbh ####
Get an ODBC or core (sqlite) database handle from FreeSWITCH and perform an SQL query through it.

Advantage of this method is that it makes use of connection pooling provided by FreeSWITCH which gives a nice increase in speed when compared to creating a new TCP connection for each LuaSQL env:connect().

It works as follows:

<pre>
local dbh = freeswitch.Dbh("dsn","user","pass") -- when using ODBC (deprecated)
-- OR --
local dbh = freeswitch.Dbh("core:my_db") -- when using sqlite (deprecated, if you have to use this to make it work you should upgrade your FS installation)
-- OR --
local dbh = freeswitch.Dbh("sqlite://my_db") -- sqlite database in subdirectory "db"
-- OR --
local dbh = freeswitch.Dbh("odbc://my_db:uname:passwd") -- connect to ODBC database

assert(dbh:connected()) -- exits the script if we didn't connect properly

dbh:test_reactive("SELECT * FROM my_table",
                  "DROP TABLE my_table",
                  "CREATE TABLE my_table (id INTEGER(8), name VARCHAR(255))")

dbh:query("INSERT INTO my_table VALUES(1, 'foo')") -- populate the table
dbh:query("INSERT INTO my_table VALUES(2, 'bar')") -- with some test data

dbh:query("SELECT id, name FROM my_table", function(row)
  stream:write(string.format("%5s : %s\n", row.id, row.name))
end)

dbh:query("UPDATE my_table SET name = 'changed'")
stream:write("Affected rows: " .. dbh:affected_rows() .. "\n")

dbh:release() -- optional
</pre>

* ''freeswitch.Dbh(odbc://my_db:uname:passwd)'' gets an ODBC db handle from the pool.
* ''freeswitch.Dbh("sqlite://my_db")'' gets a core db (sqlite) db handle from the pool (this automatically creates the db if it didn't exist yet).
* ''dbh:connected()'' checks if the handle is still connected to the database, returns true if connected, false otherwise.
* ''dbh:test_reactive("test_sql", "drop_sql", "reactive_sql")'' performs test_sql and if it fails performs drop_sql and reactive_sql (handy for initial table creation purposes)
* ''dbh:query("query", function())'' takes the query as a string and an optional Lua callback function that is called on each row returned by the db.
** The callback function is passed a table representation of the current row for each iteration of the loop. <br>Syntax of each row is: { ["column_name_1"] = "value_1", ["column_name_2"] = "value_2" }.
** If you (optionally) return a number other than 0 from the callback-function, you'll break the loop.
* ''dbh:affected_rows()'' returns the number of rows affected by the last run INSERT, DELETE or UPDATE on the handle. It does not respond to SELECT operations.
* ''dbh:release()'' (optional) releases the handle back to the pool so it can be re-used by another thread. This is also automatically done when the dbh goes out of scope and is garbage collected (for example when your script returns). Useful for long-running scripts to release the connection sooner.

Take a look [[Lua_freeswitch_dbh|here]] for some examples.

#### freeswitch.email ####

Send an email with optional (converted) attachment.

Note that for this to work you have to have an [http://en.wikipedia.org/wiki/Message_transfer_agent MTA] installed on your server, you also need to have 'mailer-app' configured in your [[switch.conf.xml]].

You can use freeswitch.email as follows:

<pre>
freeswitch.email(to, from, headers, body, file, convert_cmd, convert_ext)
</pre>

* ''to'' (mandatory) a valid email address
* ''from'' (mandatory) a valid email address
* ''headers'' (mandatory) for example "subject: you've got mail!\n"
* ''body'' (optional) your regular mail body
* ''file'' (optional) a file to attach to your mail
* ''convert_cmd'' (optional) convert file to a different format before sending
* ''convert_ext'' (optional) to replace the file's extension

For example:

<pre>
freeswitch.email("receiver@bar.com",
                 "sender@foo.com",
                 "subject: Voicemail from 1234\n",
                 "Hello,\n\nYou've got a voicemail, click the attachment to listen to it.",
                 "message.wav",
                 "mp3enc",
                 "mp3")
</pre>

then the following system command will be executed before attaching "message.mp3" to the mail and send it on its way:

<pre>
mp3enc message.wav message.mp3
</pre>

####freeswitch.Event####
This is firing a custom event my::event.

<pre>
local event = freeswitch.Event("custom", "my::event");
event:addHeader("My-Header", "test");
event:fire();
--Another one
function FSMan:fire(nombreHeader, header, body)--Manda un evento MESSAGE a algun receptor
  local miEvento = freeswitch.Event("MESSAGE");
  nombreHeader = Utils:trim(nombreHeader); header = Utils:trim(header); body = Utils:trim(body);
  if (nombreHeader ## false ) then nombreHeader="Nombre_Header_Generico" end
  if (header ## false) then header="Header_Generico" end
  if (body ## false) then body="Body_Generico" end
  miEvento:addHeader(nombreHeader, header);
  miEvento:addBody(body);
  miEvento:fire();
end
</pre>

####freeswitch.EventConsumer####
Consumes events from FreeSWITCH.

Usage:
 con = freeswitch.EventConsumer("<event_name>"[,"<subclass type>"]);

 -- pop() returns an event or nil if no events
 con:pop()

 -- pop(1) blocks until there is an event
 con:pop(1)

 -- pop(1,500) blocks for max half a second until there is an event
 con:pop(1,500)

Examples:
<pre>
con = freeswitch.EventConsumer("all");
session = freeswitch.Session("sofia/default/dest@host.com");
while session:ready() do
   session:execute("sleep", "1000");
   for e in (function() return con:pop() end) do
      print("event\n" .. e:serialize("xml"));
   end
end

-- or
while session:ready() do
    for e in (function() return con:pop(1,1000) end) do
        print("event\n" .. e:serialize("xml"))
    end
end

-- You may subscribe to specific events if you want to, and even subclasses
con = freeswitch.EventConsumer("CUSTOM");
con = freeswitch.EventConsumer("CUSTOM","conference::maintenance");

-- wait for a specific event but continue after 500 ms
function poll()
    -- create event and listener
    local event = freeswitch.Event("CUSTOM", "ping::running?")
    local con = freeswitch.EventConsumer("CUSTOM", "ping::running!")

    -- add text ad libitum
    event:addHeader("hi", "there")
    -- fire event
    event:fire()
    -- and wait for reply but not very long
    if con:pop(1, 500) then
        print("reply received")
        return true
    end
    print("no reply")
    return false
end

</pre>

####freeswitch.getGlobalVariable####
Retrieves a global variable

<pre>
my_globalvar = freeswitch.getGlobalVariable("varname")
</pre>
####freeswitch.IVRMenu####
<pre>
hash = {
   ["main"] = undef,
   ["name"] = "top",
   ["greet_long"] = "phrase:demo_ivr_main_menu",
   ["greet_short"] = "phrase:demo_ivr_main_menu_short",
   ["invalid_sound"] = "ivr/ivr-that_was_an_invalid_entry.wav",
   ["exit_sound"] = "voicemail/vm-goodbye.wav",
   ["confirm_macro"] = "undef",
   ["confirm_key"] = "undef",
   ["confirm_attempts"] = "3",
   ["inter_digit_timeout"] = "2000",
   ["digit_len"] = "1",
   ["timeout"] = "10000",
   ["max_failures"] = "3"
}

top = freeswitch.IVRMenu(hash["main"],
                         hash["name"],
                         hash["greet_long"],
                         hash["greet_short"],
                         hash["invalid_sound"],
                         hash["exit_sound"],
                         hash["confirm_macro"],
                         hash["confirm_key"],
                         hash["confirm_attempts"],
                         hash["inter_digit_timeout"],
                         hash["digit_len"],
                         hash["timeout"],
                         hash["max_failures"]);

top:bindAction("menu-exec-app", "playback /tmp/swimp.raw", "2");
top:execute(session, "top");

</pre>


When using SAY, 3 additional variables have to be set or you will get the following error:

> [ERR] mod_lua.cpp:182 Error in IVRMenu expected 16..16 args, got 13 stack traceback:<br>
>        [C]: in function 'IVRMenu'<br>
>        /usr/local/freeswitch/scripts/ivr.lua:19: in main chunk

These variables are:
<pre>
    ["tts_engine"]          = "flite",
    ["tts_voice"]           = "rms",
    ["max_timeouts"]        = "2"
</pre>

####freeswitch.msleep####
Tells script to sleep for a specified number of milliseconds.<br/>
'''NOTE:''' Do '''not''' use this on a session-based script or bad things will happen.

<pre>
  -- Sleep for 500 milliseconds
  freeswitch.msleep(500);
</pre>

####freeswitch.Session####
Create a new session.

<pre>
local session = freeswitch.Session("sofia/10.0.1.100/1001");
session:transfer("3000", "XML", "default");
</pre>

Create a new session with execute_on_answer variable set.

<pre>
local session = freeswitch.Session("[execute_on_answer=info notice]sofia/10.0.1.100/1001");
</pre>

####stream:write####
#####API commands#####
You can write FreeSWITCH API commands *in Lua* by using the lua FreeSWITCH API command to run a script and pass the arguments in, then whatever you write with the stream object is what you get as a reply to that command.  For example, given a script in the scripts directory called hello.lua with the following content:

  stream:write("hello world")

Running 'lua hello.lua' from the FreeSWITCH console would return back "hello world".

Or calling it from the dialplan like so:

  <action application="set" data="foo=${lua(hello.lua)}"/>

Would set the channel variable "foo" to "hello world".

#####Web page interaction (via mod_xml_rpc)#####
<pre>
--
-- lua/api.lua
--
-- enable mod_xml_rpc and try http://127.0.0.1:8080/api/lua?lua/api.lua in your webbrowser
--
stream:write("Content-Type: text/html\n\n");
stream:write("<title>FreeSWITCH Command Portal</title>");
stream:write("<h2>FreeSWITCH Command Portal</h2>");
stream:write("<form method=post><input name=command size=40> ");
stream:write("<input type=submit value=\"Execute\">");
stream:write("</form><hr noshade size=1><br>");

command = env:getHeader("command");

if (command)  then
   api = freeswitch.API();
   reply = api:executeString(command);

   if (reply) then
      stream:write("<br><B>Command Result</b><br>" .. reply .. "\n");
   end

end

env:addHeader("cool", "true");
stream:write(env:serialize() .. "\n\n");
</pre>

#### Example: Call Control ####
 -- cc.lua
 -- call control lua script
 --
  dialA = "sofia/gateway/fs1/9903"
  dialB = "user/1001"
  legA = freeswitch.Session(dialA)
  dispoA = "None"
 while(legA:ready() and dispoA ~= "ANSWER") do
  dispoA = legA:getVariable("endpoint_disposition")
  freeswitch.consoleLog("INFO","Leg A disposition is '" .. dispoA .. "'\n")
  os.execute("sleep 1")
 end -- legA while
 if( not legA:ready() ) then
  -- oops, lost leg A handle this case
  freeswitch.consoleLog("NOTICE","It appears that " .. dialA .. " disconnected...\n")
 else
  legB = freeswitch.Session(dialB)
  dispoB = "None"
  while(legA:ready() and legB:ready() and dispoB ~= "ANSWER") do
    if ( not legA:ready() ) then
      -- oops, leg A hung up or got disconnected, handle this case
      freeswitch.consoleLog("NOTICE","It appears that " .. dialA .. " disconnected...\n")
    else
      os.execute("sleep 1")
      dispoB = legB:getVariable("endpoint_disposition")
      freeswitch.consoleLog("NOTICE","Leg B disposition is '" .. dispoB .. "'\n")
    end -- inner if legA ready
  end -- legB while
  if ( legA:ready() and legB:ready() ) then
    freeswitch.bridge(legA,legB)
  else
    -- oops, one of the above legs hung up, handle this case
   freeswitch.consoleLog("NOTICE","It appears that " .. dialA .. " or " .. dialB .. " disconnected...\n")
  end
 end -- outter if legA ready

####Special Case: env object####
When lua is called as the hangup hook there will be a special '''env''' object that contains all the channel variables from the channel that just disconnected.

Add an extension to test this feature:
  <extension name="lua-env-hangup-hook-test">
    <condition field="destination_number" expression="^(1234)$">
      <action application="answer"/>
      <action application="set" data="api_hangup_hook=lua hook-test.lua"/>
      <action application="set" data="my_custom_var=foobar"/>
      <action application="sleep" data="10000"/>
      <action application="hangup"/>
    </condition>
  </extension>

Then add freeswitch/scripts/hook-test.lua:
<pre>
-- hook-test.lua
-- demonstrates using env to look at channel variables in hangup hook script

-- See everything
dat = env:serialize()
freeswitch.consoleLog("INFO","Here's everything:\n" .. dat .. "\n")

-- Grab a specific channel variable
dat = env:getHeader("uuid")
freeswitch.consoleLog("INFO","Inside hangup hook, uuid is: " .. dat .. "\n")

-- Drop some info into a log file...
res = os.execute("echo " .. dat .. " >> /tmp/fax.log")
res = os.execute("echo YOUR COMMAND HERE >> /tmp/fax.log")

-- If you created a custom variable you can get it also...
dat = env:getHeader("my_custom_var")
freeswitch.consoleLog("INFO","my_custom_var is '" .. dat .. "'\n")

</pre>

Watch the FS console and dial 1234 and then hangup. You'll see all your channel variables!

## See Also ##
* [http://www.lua.org Lua.org Web site]
* [[Which scripting language should I use%3F]]

[[Category:Dialplan]]
[[Category:Configuration]]
[[Category:Modules]]
