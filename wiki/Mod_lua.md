目录：   
<pre>
* 1 <a href="#jump1">Lua特性</a>  
	* 1.1 <a href="#jump11">可用来写IVR脚本</a>
	* 1.2 <a href="#jump12">可作为事件钩子</a>
	* 1.3 <a href="#jump13">可作为Directory Server(与mod_xml_curl功能相同)</a>  
	* 1.4 <a href="#jump14">可用于发起呼叫</a>   
	* 1.5 <a href="#jump15">轻量级</a>
	* 1.6 <a href="#jump16">高度内嵌</a>
	* 1.7 <a href="#jump17">关于lua学习</a>
	* 1.8 <a href="#jump18">Cli中的lua与luarun</a> 
		* 1.8.1 <a href="#jump181">参数传递</a>   
		
* 2<a href="#jump2"> 配置</a>
	* 2.1<a href="#jump21"> 事件钩子</a>
		* 2.1.1<a href="#jump211"> 事件钩子脚本</a>
	* 2.2<a href="#jump22"> 针对IVR用途的配置</a>
	* 2.3<a href="#jump23"> 针对API呼叫的配置</a>
	* 2.4<a href="#jump24"> 调用其他lua脚本</a>
	* 2.5<a href="#jump25"> 提供配置文件服务</a>
	* 2.6<a href="#jump26"> lua自启动脚本配置</a>

* 3<a href="#jump3"> 拨号方案示例</a>
* 4<a href="#jump4"> 拨号方案示例 - 内嵌扩展</a>
* 5<a href="#jump5"> IVR示例</a>
	* 5.1<a href="#jump51"> Hello Lua示例</a>

* 6<a href="#jump6"> 模式匹配 (正则表达式)</a>
	* 6.1<a href="#jump61"> API函数regex示例</a>
	* 6.2<a href="#jump62"> Lua自带模式匹配</a>

* 7<a href="#jump7"> 杂例</a>
	* 7.1<a href="#jump71"> 运行shell命令</a>

* 8<a href="#jump8"> 更多示例</a>
* 9<a href="#jump9"> FAQ</a>
	* 9.1<a href="#jump91"> 我的debug信息在哪里?</a>
	* 9.2<a href="#jump92"> 如何使用第三方的lua脚本或模块?</a>
	* 9.3<a href="#jump93"> 如何让FreeSWITCH使用系统安装的lua环境？</a>
	* 9.4<a href="#jump94"> 第三方类库</a>
	* 9.5<a href="#jump95"> 怎么让lua通过require函数识别我自己的库？</a>
	* 9.6<a href="#jump96"> 如何通过ODBC访问数据库?</a>
	* 9.7<a href="#jump97"> 如何找出有用但是非正式的Session函数?</a>
	* 9.8<a href="#jump98"> 如何判断文件是否存在?</a>

* 10<a href="#jump10"> API</a>
	* 10.1<a href="#jump101"> Events</a>
		* 10.1.1<a href="#jump1011"> event:addBody</a>
		* 10.1.2<a href="#jump1012"> event:addHeader</a>
		* 10.1.3<a href="#jump1013"> event:delHeader</a>
		* 10.1.4<a href="#jump1014"> event:fire</a>
		* 10.1.5<a href="#jump1015"> event:getBody</a>
		* 10.1.6<a href="#jump1016"> event:getHeader</a>
		* 10.1.7<a href="#jump1017"> event:getType</a>
		* 10.1.8<a href="#jump1018"> event:serialize</a>
		* 10.1.9<a href="#jump1019"> event:setPriority</a>
		* 10.1.10<a href="#jump10110"> Sending an Event</a>

	* 10.2<a href="#jump102"> Sessions</a>
		* 10.2.1<a href="#jump1021"> session:answer</a>
		* 10.2.2<a href="#jump1022"> session:answered</a>
		* 10.2.3<a href="#jump1023"> session:bridged</a>
		* 10.2.4<a href="#jump1024"> session:check_hangup_hook</a>
		* 10.2.5<a href="#jump1025"> session:collectDigits</a>
		* 10.2.6<a href="#jump1026"> session:consoleLog</a>
		* 10.2.7<a href="#jump1027"> session:destroy</a>
		* 10.2.8<a href="#jump1028"> session:execute</a>
		* 10.2.9<a href="#jump1029"> session:executeString</a>
		* 10.2.10<a href="#jump10210"> session:flushDigits</a>
		* 10.2.11<a href="#jump10211"> session:flushEvents</a>
		* 10.2.12<a href="#jump10212"> session:get_uuid</a>
		* 10.2.13<a href="#jump10213"> session:getDigits</a>
		* 10.2.14<a href="#jump10214"> session:getState</a>
		* 10.2.15<a href="#jump10215"> session:getVariable</a>
		* 10.2.16<a href="#jump10216"> session:hangup</a>
		* 10.2.17<a href="#jump10217"> session:hangupCause</a>
		* 10.2.18<a href="#jump10218"> session:hangupState</a>
		* 10.2.19<a href="#jump10219"> session:insertFile</a>
		* 10.2.20<a href="#jump10220"> session:mediaReady</a>
		* 10.2.21<a href="#jump10221"> session:originate</a>
		* 10.2.22<a href="#jump10222"> session:playAndGetDigits</a>
			* 10.2.22.1<a href="#jump102221"> Syntax</a>
			* 10.2.22.2<a href="#jump102222"> Arguments</a>
			* 10.2.22.3<a href="#jump102223"> Discussion</a>
			* 10.2.22.4<a href="#jump102224"> Examples</a>

		* 10.2.23<a href="#jump10223"> session:preAnswer</a>
		* 10.2.24<a href="#jump10224"> session:read</a>
		* 10.2.25<a href="#jump10225"> session:ready</a>
		* 10.2.26<a href="#jump10226"> session:recordFile</a>
		* 10.2.27<a href="#jump10227"> session:sayPhrase</a>
		* 10.2.28<a href="#jump10228"> session:sendEvent</a>
		* 10.2.29<a href="#jump10229"> session:setAutoHangup</a>
		* 10.2.30<a href="#jump10230"> session:setHangupHook</a>
		* 10.2.31<a href="#jump10231"> session:setInputCallback</a>
		* 10.2.32<a href="#jump10232"> session:setVariable</a>
		* 10.2.33<a href="#jump10233"> session:sleep</a>
		* 10.2.34<a href="#jump10234"> session:speak</a>
		* 10.2.35<a href="#jump10235"> session:say</a>
		* 10.2.36<a href="#jump10236"> session:streamFile</a>
		* 10.2.37<a href="#jump10237"> session:transfer</a>
		* 10.2.38<a href="#jump10238"> session:unsetInputCallback</a>
		* 10.2.39<a href="#jump10239"> session:waitForAnswer</a>

	* 10.3<a href="#jump103"> Non-Session API</a>
		* 10.3.1<a href="#jump1031"> freeswitch.API</a>
		* 10.3.2<a href="#jump1032"> freeswitch.bridge</a>
		* 10.3.3<a href="#jump1033"> freeswitch.consoleCleanLog</a>
		* 10.3.4<a href="#jump1034"> freeswitch.consoleLog</a>
		* 10.3.5<a href="#jump1035"> freeswitch.Dbh</a>
		* 10.3.6<a href="#jump1036"> freeswitch.email</a>
		* 10.3.7<a href="#jump1037"> freeswitch.Event</a>
		* 10.3.8<a href="#jump1038"> freeswitch.EventConsumer</a>
		* 10.3.9<a href="#jump1039"> freeswitch.getGlobalVariable</a>
		* 10.3.10<a href="#jump10310"> freeswitch.IVRMenu</a>
		* 10.3.11<a href="#jump10311"> freeswitch.msleep</a>
		* 10.3.12<a href="#jump10312"> freeswitch.Session</a>
		* 10.3.13<a href="#jump10313"> stream:write</a>
			* 10.3.13.1<a href="#jump103131"> API commands</a>
			* 10.3.13.2<a href="#jump103132"> Web page interaction (via mod_xml_rpc)</a>

		* 10.3.14<a href="#jump10314"> Example: Call Control</a>
		* 10.3.15<a href="#jump10315"> Special Case: env object</a>
* 11<a href="#jump11"> See Also</a>

</pre>


##<a id="jump1">Lua特性</a>##

####<a id="jump11">可用来写IVR脚本</a>####
Lua的语法非常简单易用。查看示例： [Hello Lua](#Hello_Lua) 脚本。   

####<a id="jump12">可作为事件钩子</a>####
你可以定义一个Lua脚本，用于每次特定事件被触发的时候执行。  查看示例: [Event_Hooks](#Mod_lua)

####<a id="jump13">可作为Directory Server(与mod\_xml_curl功能相同)</a>####
Lua可以为xml_curl模块提供配置文件服务，不需要xml_curl去请求web服务器。具体请看：[Serving_Configuration](#Mod_lua)   

####<a id="jump14">可用于发起呼叫</a>####
[Examples](#Make_API_calls)

####<a id="jump15">轻量级</a>####
精简过的mod_lua.so文件只有272k大小。

####<a id="jump16">高度内嵌</a>####
就嵌入能力来说，Python得分2，Perl得分4，JavaScript得分5，而Lua是10！

####<a id="jump17">关于Lua学习</a>####
这里有一份Lua与JavaScript在某些特性方面的对比，详见[Learning Lua From JS](http://phrogz.net/lua/LearningLua_FromJS.html).

####<a id="jump18">Cli中的lua与luarun</a>####
你可以通过使用命令“luarun /path/to/script.lua”，启动一个线程来跑你的lua脚本。“lua”命令用于拨号方案的内联lua，如 ${lua(codehere)}。“luarun”会创建一个进程来异步运行，而“lua”将会阻塞直到代码执行结束。在参数前面加上“~”，会运行单行的lua命令。    
需要注意的是，通过luarun执行的脚本不能通过stream：write API向控制台写入，因为没有stream对象。

#####<a id="jump181">参数传递</a>#####
在向lua传递参数时，是用空格隔开各个参数值，如下：   
 luarun arg1 arg2 arg3

lua中是以argv对象来获取传递进来的参数，如下：   
 my\_first\_var = argv[1];    
 my\_next\_var = argv[2];    
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

##<a id="jump2">配置</a>##

###<a id="jump21"> 事件钩子 </a>###
下面的配置实例将会告诉你如何在每次DETECTED_TONE事件被触发的时候，执行tone\_event.lua脚本。

	<configuration name="lua.conf" description="LUA Configuration">
	  <settings>
	     <param name="script-directory" value="$${base_dir}/scripts/?.lua"/>
	     <hook event="DETECTED_TONE" script="tone_event.lua"/>
	  </settings>
	</configuration>

####<a id="jump211"> 事件钩子脚本 </a>####
这是一个事件钩子脚本示例，通过调用event对象的getHeader()方法来获取事件的相关信息。

	local uuid = event:getHeader("Unique-ID")
	local tone = event:getHeader("Detected-Tone")
	freeswitch.consoleLog("info", uuid .. " detected tone: " .. tone .. "\n")
	

###<a id="jump22"> 针对IVR用途的配置 </a>###

不需要任何配置。

###<a id="jump23"> 针对API呼叫的配置 </a>###
	api = freeswitch.API();
	digits = api:execute("regex", "testing1234|/(\\d+)/|$1");
	-- The returned output of the API call is stored in the variable if you need it.
	freeswitch.consoleLog("info", "Extracted digits: " .. digits .. "\n")
注：请务必对传入的参数进行转义，像上面正则表达式字符串一样。


###<a id="jump24"> 调用其他lua脚本 </a>###

	api = freeswitch.API();
	reply = api:executeString("luarun another.lua");


###<a id="jump25"> 提供配置文件服务 </a>###
FreeSWITH是从静态XML文件中请求并加载配置文件数据，而Lua模块可以替换该操作，使用脚本提供该服务，更多信息详见[Serving\_Configuration]()

###<a id="jump26"> Lua自启动脚本配置 </a>###

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

##<a id="jump3"> 拨号方案示例 </a>##
	
	 <action application="lua" data="helloworld.lua arg1 arg2"/> 

注1：在脚本中，可以通过argv[1]和argv[2]来访问传递进来的参数。
注2：默认到prefix/scripts目录中寻找helloworld.lua文件。

##<a id="jump4"> 拨号方案示例-内嵌扩展 </a>##
	
	 示例1:<action application="set" data="MY_VAR=${lua(helloworld.lua arv1 arg2)}"/>
	 示例2：<action application="set" data="MY_VAR=${lua(helloworld.lua $1)}" />
	 示例3: <action application="set" data="MY_VAR=${lua(helloworld.lua $1 ${caller_id_number})}" />
	 示例4: <action application="set" data="MY_VAR=${lua(helloworld.lua ${caller_id_number})}" inline="true" />

 	 示例5: <condition field="${lua(helloworld.lua arv1 arg2)}" expression="^Hello World$" >	

##<a id="jump5"> IVR示例 </a>##

###<a id="jump51"><span id="Hello_Lua">Hello Lua </span></a>###

	-- 接听来电
	session:answer();
	
	-- 休眠1秒
	session:sleep(1000);
	
	-- 播放语音提示文件
	session:streamFile("/path/to/blah.wav");
	
	-- 挂机
	session:hangup();

##<a id="jump6"> 模式匹配（正则表达式） </a>##

###<a id="jump61"> API函数regex示例 </a>###
通过这种方式，你可以在lua脚本内执行正则表达式条件（感谢 bkw_）。  
  
	session:execute("set", "some_chan_variable=${regex(" .. destination .. "|^([0-9]{10})$)}")

如果destination是一个lua变量，用于存储你拨打的目标号码，同时你的正则表达式是^([0-9]{10})$
在上述命令执行完毕后，匹配的结果将会放入"some\_chan_variable"这个通道变量中，在lua脚本中通过session:getVariable即可获取到结果。

同样，通过下面的命令

	session:execute("set", "some_chan_variable=${regex(" .. destination .. "|^(0\\|61)([2,3,7,8][0-9]{8})$|$2)}")

来匹配并返回捕获到的值。


###<a id="jump62"> Lua自带的模式匹配 </a>###
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

##<a id="jump7"> 杂项 </a>##

###<a id="jump71"> 运行Shell命令 </a>###
当使用session:execute()和api:execute()去执行shell命令（如Bash脚本）的时候，会只返回整型的错误码。   
如果需要获取shell命令的返回值，可以使用io.popen()方法。下面的例子来自http://lua-users.org/wiki/ShellAccess.

	  function shell(c)
	    local o, h
	    h = assert(io.popen(c,"r"))
	    o = h:read("*all")
	    h:close()
	    return o
	  end

##<a id="jump8"> 更多示例 </a>##
* See scripts/lua directory on the file system    
* [[IVR|Example IVRs]] 
* [[Lua MythTV alert example]]
* [[Fakecall responder]] 
* [[Fun Lua Examples]]
* [[Call retry based on hangup cause]]
* [[Bridging two calls with retry]]

##<a id="jump9"> FAQ </a>##
###<a id="jump91"> 我的调试信息在哪里 </a>###
Q:当我使用静态XML或xml\_curl（去执行命令）时，能通过fs_cli和xml\_cdr文件的“application log”节点看到执行的命令日志。但是，当我通过lua脚本去执行命令的时候，去怎么也看不到这些信息。 

A: 在lua脚本中，当你有一个真实可用的呼叫会话时（译者注：比如从拨号方案中转入lua脚本时，可以使用session对象来操作此次呼叫），可以使用session:execute("$application","$data")命令，使用该方法会在fs_cli和xml\_cdr的日志中显示出命令执行情况。    
但如果没有呼叫会话，比如你的lua脚本是在后台运行或从cli启动的，那你只能使用其他不能记录日志的命令。

###<a id="jump92"> 如何使用第三方的lua脚本或模块? </a>###

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

###<a id="jump93"> 怎么让FreeSWITCH使用系统lua环境？ </a>###

Q: 我已经安装好了lua环境，但是mod_lua貌似忽略掉我安装的lua。

A: Lua太小了，以至于整个lua库被静态链接到模块上。

###<a id="jump94"> 第三方类库 </a>###

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


###<a id="jump95"> 怎么让lua通过require函数识别我自己的库？ </a>###
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

###<a id="jump96"> 能通过ODBC访问数据库不? </a>###
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

###<a id="jump97"> 如何找出非正式公布出来的Session函数? </a>###

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


###<a id="jump98"> 如何测试文件是否存在? </a>###

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
	 
	 if reply=="true" then
	     session:consoleLog("info", "file_exists: Initial file found. Playing " .. message"\n")
	 else
	     message = message_location .. "goodbye.wav"
	     session:consoleLog("info", "file_exists: Initial file not found. Playing " .. message"\n")
	 end
	 session:sleep(250) -- making sure that the beginning of the file is not skipped
	 session:execute("playback", message)

##<a id="jump10"> API </a>##
###<a id="jump101"> Events </a>###

下面的这些方法用于生成事件

####<a id="jump1011">event:addBody</a>####

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



####<a id="jump1012">event:addHeader</a>####


####<a id="jump1013">event:delHeader</a>####

####<a id="jump1014">event:fire</a>####
bkw童鞋提供了下面的例子：

	local event = freeswitch.Event("message_waiting");
	event:addHeader("MWI-Messages-Waiting", "no");
	event:addHeader("MWI-Message-Account", "sip:1000@10.0.1.100");
	event:addHeader("Sofia-Profile", "internal");
	event:fire();


####<a id="jump1015">event:getBody</a>####

####<a id="jump1016">event:getHeader</a>####
这是一个常用的API调用。

	event:getHeader("Caller-Caller-ID-Name")

或者，在dialplan.lua中使用该函数获取某些信息：

	params:getHeader("variable_sip_req_uri")


####<a id="jump1017">event:getType</a>####



####<a id="jump1018">event:serialize</a>####
该函数用于向控制台输出所有的头部参数（Headers）。

	-- Print as text
	io.write(params:serialize());
	io.write(params:serialize("text"));
	
	-- Print as JSON
	io.write(params:serialize("json"));
	
或者，作为info日志信息输出，
	
	freeswitch.consoleLog("info",params:serialize())


####<a id="jump1019">event:setPriority</a>####

####<a id="jump10110">Sending an Event</a>####
使用luarun执行下面的命令，以用来控制注册话机MWI灯的开启和关闭。

	local event = freeswitch.Event("message_waiting");                                                                                                              
	event:addHeader("MWI-Messages-Waiting", "no");                                                                                                                 
	event:addHeader("MWI-Message-Account", "sip:1002@10.0.1.100");                                                                                                 
	event:fire();  


###<a id="jump102"> Sessions </a>###
下面的方法适用于存在session对象的lua脚本中。

####<a id="jump1021">session:answer</a>####

接听通话:

	session:answer();


####<a id="jump1022">session:answered</a>####
用于检查会话是否被标记为已接听（只要通话被接听，就总是为true）

####<a id="jump1023">session:bridged</a>####

用于检查当前会话通道是否桥接到其他会话通道。

	if (session:bridged() == true) do
	    -- Do something
	end

####<a id="jump1024">session:check\_hangup_hook</a>####

####<a id="jump1025">session:collectDigits</a>####

####<a id="jump1026">session:consoleLog</a>####

通过session对象，向freeswitch日志记录器写入日志。参数分别为日志级别和日志消息。

	session:consoleLog("info",   "lua rocks\n");
	session:consoleLog("notice", "lua rocks\n");
	session:consoleLog("err",    "lua rocks\n");
	session:consoleLog("debug",  "lua rocks\n");
	session:consoleLog("warning","lua rocks\n");
	
####<a id="jump1027">session:destroy</a>####

该函数用于销毁会话，释放资源。   
当你的脚本执行结束的时候，该方法会被自动调用。      
但是如果你的脚本中包含一个死循环，则需要使用该函数来停止会话。

####<a id="jump1028">session:execute</a>####

session:execute(app, data)

	local mySound = "/usr/local/freeswitch/sounds/music/16000/partita-no-3-in-e-major-bwv-1006-1-preludio.wav"
	
	session:execute("playback", mySound)

注：在execute命令执行过程中，不能执行回调函数（如DTMF监听等各种小伙伴）

####<a id="jump1029">session:executeString</a>####
等同于session:execute(api_string)

	local mySound = "/usr/local/freeswitch/sounds/music/16000/partita-no-3-in-e-major-bwv-1006-1-preludio.wav"
	
	session:executeString("playback "..mySound)

注：在execute命令执行过程中，不能执行回调函数（如DTMF监听等各种小伙伴）

####<a id="jump10210">session:flushDigits</a>####

####<a id="jump10211">session:flushEvents</a>####

####<a id="jump10212">session:get_uuid</a>####

####<a id="jump10213">session:getDigits</a>####
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

####<a id="jump10214">session:getState</a>####

获取通话状态，如“CS_EXECUTE”。全部的状态详见switch_types.h。

	state=session:getState();

####<a id="jump10215">session:getVariable</a>####

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


####<a id="jump10216">session:hangup</a>####

你可以在挂断通话的时候，顺便指明挂机原因（可选），如下：

	session:hangup("USER_BUSY");

当然，还有下面无参数的挂机方式（挂机原因默认为normal_clearing），

	session:hangup(); -- default normal_clearing



####<a id="jump10217">session:hangupCause</a>####

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

####<a id="jump10218">session:hangupState</a>####

####<a id="jump10219">session:insertFile</a>####

 session:insertFile(<orig\_file>, <file\_to_insert>, <insertion\_sample\_point>)

该函数用于将（语音）文件插入到另一个文件中。三个参数是必需的。第三个参数是file\_to_insert中要插入到orig\_file中的样本数。产生的文件将会被以会话的采样率写入，并最终取代orig\_file.

因为需要根据样本数得出插入的位置，你需要知道文件的采样率，正确计算X秒有多少个样本，以便插入文件中。例如，将文件插入到wav文件2秒钟后的位置，目标文件采样率为8000Hz，你需要将insertion\_sample_point这个参数设置为16000。

注意，此方法需要一个活跃的通道和一个有效的session对象，因为需要从session对象中获取采样率和编码信息。

例子：
在一个使用ulaw的通道上，将bar.wav插入到foo.war1秒后的位置：
  session:insertFile("foo.wav", "bar.wav", 8000)

将bar.wav加到foo.wav之前：
  session:insertFile("foo.wav", "bar.wav", 0)

将bar.wav加到foo.wav之后：
  session:insertFile("bar.wav", "foo.wav", 0)

####<a id="jump10220">session:mediaReady</a>####

####<a id="jump10221">session:originate</a>####
session:originate已过时，请使用下面的方法代替：

	new_session = freeswitch.Session("sofia/gateway/gatewayname/18001234567", session);

下面的代码仅作历史保留，请不要使用：（译者注：剩下的就不翻了，有兴趣自己看看，要是闲的蛋有点疼的话）    
''The code below is here for the sake of history only; please do not use it going forward.''

	 -- this usage of originate is deprecated, use freeswitch.Session(dest, session)
	 new_session = freeswitch.Session();
	 new_session.originate(session, dest[, timeout]);

dest - quoted dialplan destination. For example: "sofia/internal/1000@10.0.0.1" or "sofia/gateway/my\_sip\_provider/my\_dest\_number"<br>
timeout - origination timeout in seconds

Note: session.originate expects at least 2 arguments.

####<a id="jump10222">session:playAndGetDigits</a>####

播放一个语音文件，并获取DTMF输入的数字。   
在获取完毕后，将会与正则表达式进行匹配。匹配失败或超时都会触发播放包含错误提示信息的文件。    
可选参数用于在获取失败的时候将通话转到指定的拨号方案上，或者将获取到的数字存储到某个通道变量上。

#####<a id="#jump102221">语法</a>#####

	digits = session:playAndGetDigits (
	          min_digits, max_digits, max_attempts, timeout, terminators,
	          prompt_audio_files, input_error_audio_files,
	          digit_regex, variable_name, digit_timeout,
	          transfer_on_failure)


#####<a id="#jump102222">参数</a>#####

    min_digits   要求输入的最小位数     
    max_digits 	 要求输入的最大位数     
    max_attempts 	函数重复播放提示音乐等待输入的次数    
    timeout 	两次输入之间的时间间隔（单位为毫秒）     
    terminators 	输入终止符（译者注：一般为#之类）    
    prompt_audio_file 	最初播放的语音文件。在播放时，如果用户有按键输入则中止播放。每次等待输入超时后，都会播放该文件，直到播放次数超过max_attempts。    
    input_error_audio_file 	当接受到的数字不符合digit_regex制定的规则的时候，播放该错误提示文件。同时，会清空之前输入的内容。如果不需要播放错误提示文件的话，该属性置空即可。
    digit_regex 	用于匹配输入数字的正则表达式
    variable_name 	（可选）用于存储输入数字的通道变量
    digit_timeout 	(可选) 数字间超市时长。该属性被设置后，会在每次数字输入后重置timeout属性。从而让用户以比较慢的速度输入的时候，不会引起超时。如果没指定，该属性值与timeout属性相同。
    transfer_on_failure (可选) 该属性用于在出现输入异常时将通话转到指定的拨号方案上。语法为"extension-name [dialplan-id [context]]"

#####<a id="#jump102223">注意事项</a>#####

- 当所有超时和重试次数用尽后，这个函数返回一个空字符串。   
- 当允许输入的数字达到最大个数时，函数立即返回，即使还没有输入截止符。   
- 如果用户已经输入完毕，但是忘记输入截止符，在下一个超时结束后函数返回（输入的数字也返回）。   
- 需要通话被answer后，才能接收用户输入。如果通话没被接听，提示语音还是可以播放，但是不会接收不到任何输入


#####<a id="#jump102224">示例</a>#####

例1:

	digits = session:playAndGetDigits(2, 5, 3, 3000, "#", "/prompt.wav", "/error.wav", "\\d+")
	session:consoleLog("info", "Got DTMF digits: ".. digits .."\n")

该例子将会先播放prompt.wav提示音，接收2到5个数字输入，以#作为截止符。如果用户没有任何输入，或输入的不是数字，如*之类，将会播放error.wav文件。播放完毕后，你还剩下两次输入机会。


例2:

	digits = session:playAndGetDigits(1, 1, 3, 3000, "", "/menu.wav", "/error.wav", "[134]", "digits_received", 3, "operator XML default")
	session:consoleLog("info", "Got DTMF digits: ".. digits .."\n")

这次，我们只要求输入一个数字，必须是1、3、4中的一个。如果用户三次输入都不在范围内，则直接转到拨号方案operator XML default上。

如果用户输入正确，则输入的数字会返回给调用者，并保存到通道变量digits_received中。
If the user presses a correct key, that digit is returned to the caller, and the "digits_received" channel variable is set to the same value.

友情提醒: 如果需要在正则表达式中匹配*字符，则需要引用两次，如下：
digits = session:playAndGetDigits(2, 5, 3, 3000, "#", "/sr8k.wav", "", "\\d+|\\*");

####<a id="jump10223">session:preAnswer</a>####

预答会话

	session:preAnswer();


####<a id="jump10224">session:read</a>####

播放语音提示，并获取用户输入数字
	
	digits = session:read(5, 10, "/sr8k.wav", 3000, "#");                                                                                                           
	session:consoleLog("info", "Got dtmf: ".. digits .."\n");         


session:read有5个参数： <min digits> <max digits> <file to play> <inter-digit timeout> <terminators>

####<a id="jump10225">session:ready</a>####
用于检查当前会话是否仍处于活跃状态（在通话开始之后，挂断之前，都是为true）。
如果通话被转移，则session:ready返回false。   
你需要在脚本中循环检查session:ready的值，一旦为false则立即退出。    

	while (session:ready() == true) do                                                                                                                              
	   -- do something here                                                                                                                                              
	end 


####<a id="jump10226">session:recordFile</a>####

语法是session:recordFile(file\_name, max\_len_secs, silence\_threshold, silence\_secs)

silence_secs：在结束录音前，能忍耐的静默语音时长

例子:
	
	function onInputCBF(s, _type, obj, arg)
	    local k, v = nil, nil
	    local _debug = true
	    if _debug then
	        for k, v in pairs(obj) do
	            printSessionFunctions(obj)
	            print(string.format('obj k-> %s v->%s\n', tostring(k), tostring(v)))
	        end
	        if _type == 'table' then
	            for k, v in pairs(_type) do
	                print(string.format('_type k-> %s v->%s\n', tostring(k), tostring(v)))
	            end
	        end
	        print(string.format('\n(%s ## dtmf) and (obj.digit [%s])\n', _type, obj.digit))
	    end
	    if (_type == "dtmf") then
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

####<a id="jump10227">session:sayPhrase</a>####
播放语音短语宏（Play a speech phrase macro）

 session:sayPhrase(macro\_name [,macro\_data] [,language]);

* macro_name - (字符型) 需要播放的语音宏名称
* macro_data - (字符型) 可选. 传递给语音宏的参数
* language - (字符型) 可选.  用于播放宏的语言(如"en"或"fr"). 默认为"en".

要想捕获事件或DTMF输入的话，和session:setInputCallback搭配使用

示例:
	
	 function key_press(session, input_type, data, args)
	   if input_type == "dtmf" then
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

在和setInputCallback一起使用时，返回值介绍如下：   
 
* true or "true" 继续播放提示语音    
* 任何其他的输入，都会打断语音提示   


####<a id="jump10228">session:sendEvent</a>####

####<a id="jump10229">session:setAutoHangup</a>####

默认情况下，当lua脚本执行完的时候会自动挂断。如果你想继续执行拨号方案中lua脚本后面的action语句，则需要将setAutoHangup设置为false。该值默认为true。

	session:setAutoHangup(false)

####<a id="jump10230">session:setHangupHook</a>####

在lua脚本中，可以使用setHangupHook来做指定会话（session）挂断之后回调的函数。

	function myHangupHook(s, status, arg)
	    freeswitch.consoleLog("NOTICE", "myHangupHook: " .. status .. "\n")
	    -- close db_conn and terminate
	    db_conn:close()
	    error()
	end
	
	blah="w00t";
	
	session:setHangupHook("myHangupHook", "blah")

其他退出脚本或抛出错误的方式：
	
	return "exit";
	or
	return "die";
	or
	s:destroy("error message");

####<a id="jump10231">session:setInputCallback</a>####

	function my_cb(s, type, obj, arg)                                                                                                                                  
	                                                                                                                                                                
	   if (arg) then                                                                                                                                                
	      io.write("type: " .. type .. "\n" .. "arg: " .. arg .. "\n");                                                                                             
	   else                                                                                                                                                         
	      io.write("type: " .. type .. "\n");                                                                                                                       
	   end                                                                                                                                                          
	                                                                                                                                                                
	   if (type == "dtmf") then                                                                                                                                     
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

当在streamFile（用于向通道播放语音）之前使用该函数时，返回值“true”或者"undefined"会被认定为true（不打断语音的播放），其他的返回值则被认定为false（将会打断语音播放）。

更多的返回值可以参考文件./src/switch_ivr.c，第3276行“speed”相关选项。

####<a id="jump10232">session:setVariable</a>####
用于设置session的通道变量

	session:setVariable("varname", "varval");

####<a id="jump10233">session:sleep</a>####

	session:sleep(3000); 

使用该函数休眠期间，允许DTMF回调（译者注：即允许接收DTMF输入，触发回调函数），而使用session:execute("sleep", "5000")则不行。

####<a id="jump10234">session:speak</a>####

	session:set_tts_parms("flite", "kal");
	session:speak("Please say the name of the person you're trying to contact");

译者注：使用该函数前需要先安装flite模块

####<a id="jump10235">session:say</a>####
使用预先录制的语音文件播放数字、日期、货币等。
更多了解say函数的话，请参考Misc. Dialplan Tools say

参数: <data><lang><say_type><say_method>

例子:

	session:say("12345", "en", "number", "pronounced");

####<a id="jump10236">session:streamFile</a>####
向session中连续播放语音文件

	session:streamFile("/tmp/blah.wav");

以指定取样数（sample_count）来连续播放文件？（待测试，连wiki都不确定）

	session:streamFile("/tmp/blah.wav", <sample_count>);

####<a id="jump10237">session:transfer</a>####
转移当前通话。参数是extensions, dialplan and context.

	session:transfer("3000", "XML", "default");

该命令执行后，lua脚本会立即结束，如果你不想通话立即断开的话，需要设置session:setAutoHangup(false)。

如果你以session:execute("transfer", "3000 XML default")代替上面的命令来进行转移的话，转移后，lua脚本还是会接着往下执行，即使这个时候对通话已经失去控制了。这个时候执行bridge，最大的可能性就是失败。

####<a id="jump10238">session:unsetInputCallback</a>####

	session:unsetInputCallback()



####<a id="jump10239">session:waitForAnswer</a>####

###<a id="jump103"> Non-Session API </a>###
下面介绍的是一些通用的方法，不再基于session或event对象来使用。举个例子来说，向FreeSWITCH控制台打印日志，不再跟event和session对象有关系。

####<a id="jump1031">freeswitch.API</a>####

	api = freeswitch.API();
	-- get current time in milliseconds
	time = api:getTime()

####<a id="jump1032">freeswitch.bridge</a>####

	session1 = freeswitch.Session("sofia/internal/1001%192.168.1.1");
	session2 = freeswitch.Session("sofia/internal/1002%192.168.1.1");
	freeswitch.bridge(session1, session2);


####<a id="jump1033">freeswitch.consoleCleanLog</a>####

	freeswitch.consoleCleanLog("This Rocks!!!\n");

####<a id="jump1034">freeswitch.consoleLog</a>####

向freeswitch日志系统写入日志。参数为loglevel, message.

	freeswitch.consoleLog("info",   "lua rocks\n");
	freeswitch.consoleLog("notice", "lua rocks\n");
	freeswitch.consoleLog("err",    "lua rocks\n");
	freeswitch.consoleLog("debug",  "lua rocks\n");
	freeswitch.consoleLog("warning","lua rocks\n");


####<a id="jump1035"> freeswitch.Dbh </a>####
用于获取FreeSWITCH中的ODBC或和核心数据库sqlite的数据库操作句柄，执行sql查询。

该方法的好处是它使用FreeSWITCH提供的数据库连接池，比LuaSQL中为每个env:connect()创建一个单独的tcp连接会快很多。

用法如下：

	local dbh = freeswitch.Dbh("dsn","user","pass") -- 当连接ODBC时(已被废弃)
	-- 或者 --
	local dbh = freeswitch.Dbh("core:my_db") -- 当连接sqlite (已被废弃, 如果你必须要用这个方法，需要升级FS)
	-- 或者 --
	local dbh = freeswitch.Dbh("sqlite://my_db") -- 连接位于freeswitch子目录db中的sqlite数据库
	-- 或者 --
	local dbh = freeswitch.Dbh("odbc://my_db:uname:passwd") -- 连接ODBC数据库
	
	assert(dbh:connected()) -- 断言，如果数据库连接失败，则退出脚本
	
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

- freeswitch.Dbh(odbc://my_db:uname:passwd)用于从连接池获取一个ODBC数据库句柄
 
- freeswitch.Dbh("sqlite://my\_db") 用于从连接池中获取核心数据库（sqlite）一个操作句柄 (如果指定的数据库不存在，会先自动创建).
- dbh:connected() 用于检查数据库是否仍处于连接状态，返回true代表连接正常，false则相反。
- dbh:test\_reactive("test\_sql", "drop\_sql", "reactive\_sql")用于执行test_sql语句，如果执行失败，则执行drop\_sql与reactive\_sql语句（方便表的初始化创建）
- dbh:query("query", function()) 第一个参数用于传入sql查询语句，第二个参数是一个可选的lua回调函数，每返回一行数据会被调用一次。
 + 回调函数接收到的参数是每次循环遍历返回的行对象。
访问每行中列数据的方法为：{ ["column\_name_1"] = "value\_1", ["column\_name\_2"] = "value\_2" }.（译者注：该种方法比较古老，根据上面的代码，现在可能已被row.id, row.name这种形式代替，需要验证，至少我还没试过。）
 + (可选)如果你的回调函数返回非0的数字，则会中断循环。
- dbh:affected_rows() 返回最后的操作影响的行数，操作包括INSERT、DELETE和UPDATE，当然，SELECT操作不包括在内。
* （可选）dbh:release()将句柄释放回资源池，以便被其他线程复用。 当dbh超出定义范围，被垃圾回收时（比如脚本执行完毕后），同样会自动释放资源。所以，该函数对那些需要长期执行且快速释放连接的脚本比较有用。

查看Lua_freeswitch_dbh获取更多的例子。

####<a id="jump1036"> freeswitch.email </a>####

用于发送邮件，可以携带转化过的附件。

注意，要想使用该函数，需要在你的服务器上面安装MTA（http://en.wikipedia.org/wiki/Message\_transfer_agent)，同时需要在switch.conf.xml里面配置mailer-app属性。

函数用法如下：

	freeswitch.email(to, from, headers, body, file, convert_cmd, convert_ext)

* ''to'' (必选) 填写对方email地址
* ''from'' (必选) 填写发送方email地址
* ''headers'' (必选) 邮件头，比如"subject: you've got mail!\n"
* ''body'' (可选) 邮件正文
* ''file'' (可选) 邮件附件
* ''convert_cmd'' (可选) 发送前，将文件转为其他格式命令
* ''convert_ext'' (可选) 替换文件的后缀名

比如，
	
	freeswitch.email("receiver@bar.com",
	                 "sender@foo.com",
	                 "subject: Voicemail from 1234\n",
	                 "Hello,\n\nYou've got a voicemail, click the attachment to listen to it.",
	                 "message.wav",
	                 "mp3enc",
	                 "mp3")

接下来将会在添加邮件附件message.mp3前，执行下面的命令：

	mp3enc message.wav message.mp3


####<a id="jump1037">freeswitch.Event</a>####
该函数用于发送自定义事件 my::event。

	local event = freeswitch.Event("custom", "my::event"); 
	event:addHeader("My-Header", "test");
	event:fire();

	--Another one
	function FSMan:fire(nombreHeader, header, body)--Manda un evento MESSAGE a algun receptor
	  local miEvento = freeswitch.Event("MESSAGE");
	  nombreHeader = Utils:trim(nombreHeader); header = Utils:trim(header); body = Utils:trim(body);
	  if (nombreHeader==false ) then nombreHeader="Nombre_Header_Generico" end
	  if (header==false) then header="Header_Generico" end
	  if (body==false) then body="Body_Generico" end
	  miEvento:addHeader(nombreHeader, header);
	  miEvento:addBody(body);
	  miEvento:fire();
	end

####<a id="jump1038">freeswitch.EventConsumer</a>####
订阅处理FreeSWITCH事件

用法:    

	 con = freeswitch.EventConsumer("<event_name>"[,"<subclass type>"]);
	 
	 -- pop() 该函数不断返回事件，如果没有则返回nil    
	 con:pop()
	 
	 -- pop(1) 该函数不断返回事件，如果没有则堵塞，直到新事件到来    
	 con:pop(1)
	 
	 -- pop(1,500) 如果没有事件，则最多堵塞半秒。（译者注：那半秒后呢，继续返回nil？）
	 con:pop(1,500)

例子:

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
	
	-- 你可以订阅指定事件，甚至可以指定事件子类
	con = freeswitch.EventConsumer("CUSTOM");
	con = freeswitch.EventConsumer("CUSTOM","conference::maintenance");
	
	-- 等待指定事件，但只等待500毫秒，超过500毫秒后继续执行
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


####<a id="jump1039">freeswitch.getGlobalVariable</a>####
获取全局变量

	my_globalvar = freeswitch.getGlobalVariable("varname")

####<a id="jump10310">freeswitch.IVRMenu</a>####
	
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


如果跟SAY函数搭配使用，需要另外设置3个变量，否则会报下面的错误：   
 
> [ERR] mod_lua.cpp:182 Error in IVRMenu expected 16..16 args, got 13 stack      traceback:<br>
>[C]: in function 'IVRMenu'<br>
>/usr/local/freeswitch/scripts/ivr.lua:19: in main chunk    

需要设置的变量如下:

    ["tts_engine"]          = "flite",
    ["tts_voice"]           = "rms",
    ["max_timeouts"]        = "2"


####<a id="jump10311">freeswitch.msleep</a>####
该函数用于让脚本休眠指定时长（单位为毫秒）    
警告：不要将该函数用在基于session的脚本中，否则会有一些小小的意外发生哟。

  -- Sleep for 500 milliseconds
  freeswitch.msleep(500);


####<a id="jump10312">freeswitch.Session</a>####
用于创建session对象

	local session = freeswitch.Session("sofia/10.0.1.100/1001");
	session:transfer("3000", "XML", "default"); 

在创建session时，设置execute\_on_answer变量：

	local session = freeswitch.Session("[execute_on_answer=info notice]sofia/10.0.1.100/1001");


####<a id="jump10313">stream:write</a>####
#####<a id="jump103131">API commands</a>#####
你可以使用lua来写FreeSWITCH的API命令，方法是使用lua命令向lua脚本中传入参数并执行。lua脚本中使用session:write写入的值即是该lua命令调用的返回值。    
举例来说，在scripts目录下面存在一个hello.lua文件，内容如下：
	
  stream:write("hello world")

在FreeSWITCH控制台中执行lua hello.lua，将会返回“hello world”。

或者，从拨号方案中调用，如下：

  <action application="set" data="foo=${lua(hello.lua)}"/>

将会将通道变量foo的值设置为"hello world"。

译者注：stream:write我还没成功使用过一次，上面的都试过，直接在控制台中执行会报错。

#####<a id="jump103132">Web层的Lua调用 (通过mod\_xml\_rpc实现)</a>#####

	--
	-- lua/api.lua
	-- 
	-- 调用方式：开启FS中的mod_xml_rpc模块，然后在浏览器中输入http://127.0.0.1:8080/api/lua?lua/api.lua
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


####<a id="jump10314"> Lua示例: 呼叫控制 </a>####
	
	 -- cc.lua
	 -- 使用lua脚本控制呼叫流程
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
	  -- leg A拨打失败
	  freeswitch.consoleLog("NOTICE","It appears that " .. dialA .. " disconnected...\n")
	 else 
	  legB = freeswitch.Session(dialB) 
	  dispoB = "None"
	  while(legA:ready() and legB:ready() and dispoB ~= "ANSWER") do
	    if ( not legA:ready() ) then
	      -- 如果在拨打B的过程中，A主动挂断或被动断开
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
	    -- 如果A与B都挂断，那就各回各家了，不再需要bridge鸟
	   freeswitch.consoleLog("NOTICE","It appears that " .. dialA .. " or " .. dialB .. " disconnected...\n")
	  end
	 end -- outter if legA ready

####<a id="jump10315">特殊对象: env</a>####
当lua脚本被当做hangup hook进行调用的时候，脚本中可以使用env这个特殊对象，该对象中包含刚刚才断开的通道的全部通道变量。

使用步骤：
1、在拨号方案中增加如下规则：

	  <extension name="lua-env-hangup-hook-test">
	    <condition field="destination_number" expression="^(1234)$">
	      <action application="answer"/>
	      <action application="set" data="api_hangup_hook=lua hook-test.lua"/>
	      <action application="set" data="my_custom_var=foobar"/> 
	      <action application="sleep" data="10000"/>
	      <action application="hangup"/>                   
	    </condition>                             
	  </extension>

译者注：上面的配置重点是下面的一句，指明挂断时调用的命令：

	<action application="set" data="api\_hangup\_hook=lua hook-test.lua"/>


2、在freeswitch/scripts/中增加hook-test.lua脚本，内容如下:

	-- hook-test.lua                 
	-- 演示如何使用env对象查看通道变量
	
	-- 查看所有通道变量
	dat = env:serialize()            
	freeswitch.consoleLog("INFO","Here's everything:\n" .. dat .. "\n")
	
	-- 获取指定通道变量
	dat = env:getHeader("uuid")      
	freeswitch.consoleLog("INFO","Inside hangup hook, uuid is: " .. dat .. "\n")                            
	
	-- 将变量输出到日志文件中
	res = os.execute("echo " .. dat .. " >> /tmp/fax.log")
	res = os.execute("echo YOUR COMMAND HERE >> /tmp/fax.log")
	
	-- 获取自定义通道变量
	dat = env:getHeader("my_custom_var")
	freeswitch.consoleLog("INFO","my_custom_var is '" .. dat .. "'\n")
	
打开FS控制台，然后使用软电话拨打1234后挂断，再然后，你会在控制台上看到满屏满屏的通道变量，enjoy吧，少年！

##<a id="jump11"> 参考资料 </a>##
- Lua官网：http://www.lua.org
- [[Category:Dialplan]]
- [[Category:Configuration]]
- [[Category:Modules]]

译后注：本文作为FreeSWITCH中文Wiki的一部分，更多内容请访问[freeswitch.org.cn](http://www.freeswitch.org.cn)。如果需要转载，也请保留该信息，让更多的人参与到中文Wiki中，FreeSWITCH的推广需要你我的共同努力，谢谢。
ps，如果译文有问题，请给我发邮件，地址是jizhask@gmail.com。

