---
layout: default_with_fs
title: {{ site.com }}
---
##通道变量

####翻译中...

####翻译:llcxyz

----
<table id="toc" class="toc" summary="Contents">
<tr><td><div id="toctitle"><h2>目录</h2></div>
<ul>
<li class="toclevel-1"><a href="#Introduction"><span class="tocnumber">1</span>
<span class="toctext">简介</span></a>
<ul>
<li class="toclevel-2"><a href="#Channel_Variables_in_the_XML_Dialplan"><span class="tocnumber">1.1</span> 
<span class="toctext">XML 拨号计划中设置通道变量</span></a>
<ul>
<li class="toclevel-3"><a href="#Scoped_Variables"><span class="tocnumber">1.1.1</span>
<span class="toctext">限定作用域的通道变量</span></a></li>
</ul>
</li>
<li class="toclevel-2"><a href="#Channel_Variables_in_Dial_strings"><span class="tocnumber">1.2</span>
<span class="toctext">拨号字符串中设置通道变量</span></a>
<ul>
<li class="toclevel-3"><a href="#Handling_Variables_With_Commas"><span class="tocnumber">1.2.1</span>
<span class="toctext">逗号分隔多个变量</span></a></li>
</ul>
</li>
<li class="toclevel-2"><a href="#Exporting_Channel_Variables_in_Bridge_Operations"><span class="tocnumber">1.3</span>
<span class="toctext">在桥接操作中导出通道变量</span></a></li>

<li class="toclevel-2"><a href="#Using_Channel_Variables_in_Dialplan_Condition_Statements"><span class="tocnumber">1.4</span> <span class="toctext">在拨号计划的Condition语句中使用通道变量</span></a></li>

<li class="toclevel-2"><a href="#Custom_Channel_Variables"><span class="tocnumber">1.5</span> 
<span class="toctext">自定义通道变量</span></a></li>
<li class="toclevel-2"><a href="#Channel_Variable_Manipulation"><span class="tocnumber">1.6</span> 
<span class="toctext">通道变量操作</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Info_Application_Variable_Names_.28variable_xxxx.29"><span class="tocnumber">2</span><span class="toctext">应用Info中的变量名称(variable_xxxx)</span></a></li>

<li class="toclevel-1"><a href="#.24.7Bvariable.7D_vs._.24.24.7Bvariable.7D"><span class="tocnumber">3</span> <span class="toctext">${变量名} vs. $${变量名}</span></a></li>

<li class="toclevel-1"><a href="#CDR_related"><span class="tocnumber">4</span> <span class="toctext">呼叫记录相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#process_cdr"><span class="tocnumber">4.1</span> <span class="toctext">process_cdr</span></a></li>
<li class="toclevel-2"><a href="#accountcode"><span class="tocnumber">4.2</span> <span class="toctext">accountcode</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Hangup_Causes"><span class="tocnumber">5</span> <span class="toctext">挂断原因相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#bridge_hangup_cause"><span class="tocnumber">5.1</span> <span class="toctext">bridge_hangup_cause</span></a></li>
<li class="toclevel-2"><a href="#disable_q850_reason"><span class="tocnumber">5.2</span> <span class="toctext">disable_q850_reason</span></a></li>
<li class="toclevel-2"><a href="#hangup_cause"><span class="tocnumber">5.3</span> <span class="toctext">hangup_cause</span></a></li>
<li class="toclevel-2"><a href="#hangup_cause_q850"><span class="tocnumber">5.4</span> <span class="toctext">hangup_cause_q850</span></a></li>
<li class="toclevel-2"><a href="#sip_hangup_disposition"><span class="tocnumber">5.5</span> <span class="toctext">sip_hangup_disposition</span></a></li>
<li class="toclevel-2"><a href="#proto_specific_hangup_cause"><span class="tocnumber">5.6</span> <span class="toctext">proto_specific_hangup_cause</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#DTMF_Related"><span class="tocnumber">6</span> 
<span class="toctext">DTMF 相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#pass_rfc2833"><span class="tocnumber">6.1</span> <span class="toctext">pass_rfc2833</span></a></li>
<li class="toclevel-2"><a href="#dtmf_type"><span class="tocnumber">6.2</span> <span class="toctext">dtmf_type</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Media_Handling"><span class="tocnumber">7</span> <span class="toctext">媒体处理相关</span></a>
<ul>
<li class="toclevel-2"><a href="#monitor_early_media_fail"><span class="tocnumber">7.1</span> <span class="toctext">monitor_early_media_fail</span></a></li>
<li class="toclevel-2"><a href="#monitor_early_media_ring"><span class="tocnumber">7.2</span> <span class="toctext">monitor_early_media_ring</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Timeout_Related"><span class="tocnumber">8</span> <span class="toctext">超时相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#call_timeout"><span class="tocnumber">8.1</span> <span class="toctext">call_timeout</span></a></li>
<li class="toclevel-2"><a href="#leg_timeout"><span class="tocnumber">8.2</span> <span class="toctext">leg_timeout</span></a></li>
<li class="toclevel-2"><a href="#originate_continue_on_timeout"><span class="tocnumber">8.3</span> <span class="toctext">originate_continue_on_timeout</span></a></li>
<li class="toclevel-2"><a href="#park_timeout"><span class="tocnumber">8.4</span> <span class="toctext">park_timeout</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Music_On_Hold_Related"><span class="tocnumber">9</span> 
<span class="toctext">等待音乐相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#hold_music"><span class="tocnumber">9.1</span> <span class="toctext">hold_music</span></a></li>
<li class="toclevel-2"><a href="#temp_hold_music"><span class="tocnumber">9.2</span> <span class="toctext">temp_hold_music</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Locale_Related"><span class="tocnumber">10</span> <span class="toctext">本地化相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#default_language"><span class="tocnumber">10.1</span> <span class="toctext">default_language</span></a></li>
<li class="toclevel-2"><a href="#timezone"><span class="tocnumber">10.2</span> <span class="toctext">timezone</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Bridge_Related"><span class="tocnumber">11</span> <span class="toctext">桥接相关</span></a>
<ul>
<li class="toclevel-2"><a href="#api_after_bridge"><span class="tocnumber">11.1</span> <span class="toctext">api_after_bridge</span></a></li>
<li class="toclevel-2"><a href="#auto_hunt"><span class="tocnumber">11.2</span> <span class="toctext">auto_hunt</span></a></li>
<li class="toclevel-2"><a href="#bridge_early_media"><span class="tocnumber">11.3</span> <span class="toctext">bridge_early_media</span></a></li>
<li class="toclevel-2"><a href="#bridge_terminate_key"><span class="tocnumber">11.4</span> <span class="toctext">bridge_terminate_key</span></a></li>
<li class="toclevel-2"><a href="#continue_on_fail"><span class="tocnumber">11.5</span> <span class="toctext">continue_on_fail</span></a></li>
<li class="toclevel-2"><a href="#transfer_on_fail"><span class="tocnumber">11.6</span> <span class="toctext">transfer_on_fail</span></a></li>
<li class="toclevel-2"><a href="#enable_file_write_buffering"><span class="tocnumber">11.7</span> <span class="toctext">enable_file_write_buffering</span></a></li>
<li class="toclevel-2"><a href="#failure_causes"><span class="tocnumber">11.8</span> <span class="toctext">failure_causes</span></a></li>
<li class="toclevel-2"><a href="#force_transfer_context"><span class="tocnumber">11.9</span> <span class="toctext">force_transfer_context</span></a></li>
<li class="toclevel-2"><a href="#force_transfer_dialplan"><span class="tocnumber">11.10</span> <span class="toctext">force_transfer_dialplan</span></a></li>
<li class="toclevel-2"><a href="#hangup_after_bridge"><span class="tocnumber">11.11</span> <span class="toctext">hangup_after_bridge</span></a></li>
<li class="toclevel-2"><a href="#hold_hangup_xfer_exten"><span class="tocnumber">11.12</span> <span class="toctext">hold_hangup_xfer_exten</span></a></li>
<li class="toclevel-2"><a href="#last_bridge_to"><span class="tocnumber">11.13</span> <span class="toctext">last_bridge_to</span></a></li>
<li class="toclevel-2"><a href="#loopback_bowout_on_execute"><span class="tocnumber">11.14</span> <span class="toctext">loopback_bowout_on_execute</span></a></li>
<li class="toclevel-2"><a href="#outbound_redirect_fatal"><span class="tocnumber">11.15</span> <span class="toctext">outbound_redirect_fatal</span></a></li>
<li class="toclevel-2"><a href="#originate_timeout"><span class="tocnumber">11.16</span> <span class="toctext">originate_timeout</span></a></li>
<li class="toclevel-2"><a href="#park_after_bridge"><span class="tocnumber">11.17</span> <span class="toctext">park_after_bridge</span></a></li>
<li class="toclevel-2"><a href="#signal_bond"><span class="tocnumber">11.18</span> <span class="toctext">signal_bond</span></a></li>
<li class="toclevel-2"><a href="#sip_jitter_buffer_during_bridge"><span class="tocnumber">11.19</span> <span class="toctext">sip_jitter_buffer_during_bridge</span></a></li>
<li class="toclevel-2"><a href="#uuid_bridge_continue_on_cancel"><span class="tocnumber">11.20</span> <span class="toctext">uuid_bridge_continue_on_cancel</span></a></li>
</ul>
</li>

<li class="toclevel-1"><a href="#Conference_Related"><span class="tocnumber">12</span> <span class="toctext">会议相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#conference_auto_outcall_announce"><span class="tocnumber">12.1</span> <span class="toctext">conference_auto_outcall_announce</span></a></li>
<li class="toclevel-2"><a href="#conference_auto_outcall_caller_id_name"><span class="tocnumber">12.2</span> <span class="toctext">conference_auto_outcall_caller_id_name</span></a></li>
<li class="toclevel-2"><a href="#conference_auto_outcall_caller_id_number"><span class="tocnumber">12.3</span> <span class="toctext">conference_auto_outcall_caller_id_number</span></a></li>
<li class="toclevel-2"><a href="#conference_auto_outcall_flags"><span class="tocnumber">12.4</span> <span class="toctext">conference_auto_outcall_flags</span></a></li>
<li class="toclevel-2"><a href="#conference_auto_outcall_prefix"><span class="tocnumber">12.5</span> <span class="toctext">conference_auto_outcall_prefix</span></a></li>
<li class="toclevel-2"><a href="#conference_auto_outcall_timeout"><span class="tocnumber">12.6</span> <span class="toctext">conference_auto_outcall_timeout</span></a></li>
<li class="toclevel-2"><a href="#conference_auto_outcall_maxwait"><span class="tocnumber">12.7</span> <span class="toctext">conference_auto_outcall_maxwait</span></a></li>
<li class="toclevel-2"><a href="#conference_controls"><span class="tocnumber">12.8</span> <span class="toctext">conference_controls</span></a></li>
<li class="toclevel-2"><a href="#conference_enter_sound"><span class="tocnumber">12.9</span> <span class="toctext">conference_enter_sound</span></a></li>
<li class="toclevel-2"><a href="#conference_last_matching_digits"><span class="tocnumber">12.10</span> <span class="toctext">conference_last_matching_digits</span></a></li>
<li class="toclevel-2"><a href="#last_transferred_conference"><span class="tocnumber">12.11</span> <span class="toctext">last_transferred_conference</span></a></li>
<li class="toclevel-2"><a href="#conference_member_id"><span class="tocnumber">12.12</span> <span class="toctext">conference_member_id</span></a></li>
<li class="toclevel-2"><a href="#conference_uuid"><span class="tocnumber">12.13</span> <span class="toctext">conference_uuid</span></a></li>
<li class="toclevel-2"><a href="#hangup_after_conference"><span class="tocnumber">12.14</span> <span class="toctext">hangup_after_conference</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Code_Execution_Related"><span class="tocnumber">13</span> <span class="toctext">脚本执行相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#api_hangup_hook"><span class="tocnumber">13.1</span> <span class="toctext">api_hangup_hook</span></a></li>
<li class="toclevel-2"><a href="#bridge_pre_execute_aleg_app"><span class="tocnumber">13.2</span> <span class="toctext">bridge_pre_execute_aleg_app</span></a></li>
<li class="toclevel-2"><a href="#bridge_pre_execute_aleg_data"><span class="tocnumber">13.3</span> <span class="toctext">bridge_pre_execute_aleg_data</span></a></li>
<li class="toclevel-2"><a href="#bridge_pre_execute_bleg_app"><span class="tocnumber">13.4</span> <span class="toctext">bridge_pre_execute_bleg_app</span></a></li>
<li class="toclevel-2"><a href="#bridge_pre_execute_bleg_data"><span class="tocnumber">13.5</span> <span class="toctext">bridge_pre_execute_bleg_data</span></a></li>
<li class="toclevel-2"><a href="#exec_after_bridge_app"><span class="tocnumber">13.6</span> <span class="toctext">exec_after_bridge_app</span></a></li>
<li class="toclevel-2"><a href="#exec_after_bridge_arg"><span class="tocnumber">13.7</span> <span class="toctext">exec_after_bridge_arg</span></a></li>
<li class="toclevel-2"><a href="#The_execute_on_family"><span class="tocnumber">13.8</span> <span class="toctext">The execute_on family</span></a>
<ul>
<li class="toclevel-3"><a href="#execute_on_answer"><span class="tocnumber">13.8.1</span> <span class="toctext">execute_on_answer</span></a></li>
<li class="toclevel-3"><a href="#execute_on_media"><span class="tocnumber">13.8.2</span> <span class="toctext">execute_on_media</span></a></li>
<li class="toclevel-3"><a href="#execute_on_preanswer"><span class="tocnumber">13.8.3</span> <span class="toctext">execute_on_preanswer</span></a></li>
<li class="toclevel-3"><a href="#execute_on_ring"><span class="tocnumber">13.8.4</span> <span class="toctext">execute_on_ring</span></a></li>
</ul>
</li>
<li class="toclevel-2"><a href="#failed_xml_cdr_prefix"><span class="tocnumber">13.9</span> <span class="toctext">failed_xml_cdr_prefix</span></a></li>
<li class="toclevel-2"><a href="#fail_on_single_reject"><span class="tocnumber">13.10</span> <span class="toctext">fail_on_single_reject</span></a></li>
<li class="toclevel-2"><a href="#intercept_unbridged_only"><span class="tocnumber">13.11</span> <span class="toctext">intercept_unbridged_only</span></a></li>
<li class="toclevel-2"><a href="#intercept_unanswered_only"><span class="tocnumber">13.12</span> <span class="toctext">intercept_unanswered_only</span></a></li>
<li class="toclevel-2"><a href="#session_in_hangup_hook"><span class="tocnumber">13.13</span> <span class="toctext">session_in_hangup_hook</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Caller_ID_Related"><span class="tocnumber">14</span> <span class="toctext">主叫标识相关</span></a>
<ul>
<li class="toclevel-2"><a href="#caller_id_name"><span class="tocnumber">14.1</span> <span class="toctext">caller_id_name</span></a></li>
<li class="toclevel-2"><a href="#caller_id_number"><span class="tocnumber">14.2</span> <span class="toctext">caller_id_number</span></a></li>
<li class="toclevel-2"><a href="#effective_caller_id_name"><span class="tocnumber">14.3</span> <span class="toctext">effective_caller_id_name</span></a></li>
<li class="toclevel-2"><a href="#effective_caller_id_number"><span class="tocnumber">14.4</span> <span class="toctext">effective_caller_id_number</span></a></li>
<li class="toclevel-2"><a href="#sip_cid_type"><span class="tocnumber">14.5</span> <span class="toctext">sip_cid_type</span></a></li>
<li class="toclevel-2"><a href="#effective_sip_cid_in_1xx"><span class="tocnumber">14.6</span> <span class="toctext">effective_sip_cid_in_1xx</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Callee_ID_Related"><span class="tocnumber">15</span> <span class="toctext">被叫标识相关</span></a>
<ul>
<li class="toclevel-2"><a href="#sip_callee_id_name"><span class="tocnumber">15.1</span> <span class="toctext">sip_callee_id_name</span></a></li>
<li class="toclevel-2"><a href="#sip_callee_id_number"><span class="tocnumber">15.2</span> <span class="toctext">sip_callee_id_number</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Call_Recording_Related"><span class="tocnumber">16</span> <span class="toctext">呼叫录音相关</span></a>
<ul>
<li class="toclevel-2"><a href="#Audio_File_Metadata"><span class="tocnumber">16.1</span> <span class="toctext">音频文件属性</span></a>
<ul>
<li class="toclevel-3"><a href="#RECORD_TITLE"><span class="tocnumber">16.1.1</span> <span class="toctext">RECORD_TITLE</span></a></li>
<li class="toclevel-3"><a href="#RECORD_COPYRIGHT"><span class="tocnumber">16.1.2</span> <span class="toctext">RECORD_COPYRIGHT</span></a></li>
<li class="toclevel-3"><a href="#RECORD_SOFTWARE"><span class="tocnumber">16.1.3</span> <span class="toctext">RECORD_SOFTWARE</span></a></li>
<li class="toclevel-3"><a href="#RECORD_ARTIST"><span class="tocnumber">16.1.4</span> <span class="toctext">RECORD_ARTIST</span></a></li>
<li class="toclevel-3"><a href="#RECORD_COMMENT"><span class="tocnumber">16.1.5</span> <span class="toctext">RECORD_COMMENT</span></a></li>
<li class="toclevel-3"><a href="#RECORD_DATE"><span class="tocnumber">16.1.6</span> <span class="toctext">RECORD_DATE</span></a></li>
<li class="toclevel-3"><a href="#RECORD_STEREO"><span class="tocnumber">16.1.7</span> <span class="toctext">RECORD_STEREO</span></a></li>
</ul>
</li>
<li class="toclevel-2"><a href="#record_fill_cng"><span class="tocnumber">16.2</span> <span class="toctext">record_fill_cng</span></a></li>
<li class="toclevel-2"><a href="#RECORD_HANGUP_ON_ERROR"><span class="tocnumber">16.3</span> <span class="toctext">RECORD_HANGUP_ON_ERROR</span></a></li>
<li class="toclevel-2"><a href="#RECORD_DISCARDED"><span class="tocnumber">16.4</span> <span class="toctext">RECORD_DISCARDED</span></a></li>
<li class="toclevel-2"><a href="#record_post_process_exec_api"><span class="tocnumber">16.5</span> <span class="toctext">record_post_process_exec_api</span></a></li>
<li class="toclevel-2"><a href="#record_post_process_exec_app"><span class="tocnumber">16.6</span> <span class="toctext">record_post_process_exec_app</span></a></li>
<li class="toclevel-2"><a href="#record_restart_limit_on_dtmf"><span class="tocnumber">16.7</span> <span class="toctext">record_restart_limit_on_dtmf</span></a></li>
<li class="toclevel-2"><a href="#record_sample_rate"><span class="tocnumber">16.8</span> <span class="toctext">record_sample_rate</span></a></li>
<li class="toclevel-2"><a href="#record_waste_resources"><span class="tocnumber">16.9</span> <span class="toctext">record_waste_resources</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Codec_Related"><span class="tocnumber">17</span> <span class="toctext">编解码相关</span></a>
<ul>
<li class="toclevel-2"><a href="#absolute_codec_string"><span class="tocnumber">17.1</span> <span class="toctext">absolute_codec_string</span></a></li>
<li class="toclevel-2"><a href="#codec_string"><span class="tocnumber">17.2</span> <span class="toctext">codec_string</span></a></li>
<li class="toclevel-2"><a href="#inherit_codec"><span class="tocnumber">17.3</span> <span class="toctext">inherit_codec</span></a></li>
<li class="toclevel-2"><a href="#read_codec"><span class="tocnumber">17.4</span> <span class="toctext">read_codec</span></a></li>
<li class="toclevel-2"><a href="#write_codec"><span class="tocnumber">17.5</span> <span class="toctext">write_codec</span></a></li>
<li class="toclevel-2"><a href="#passthru_ptime_mismatch"><span class="tocnumber">17.6</span> <span class="toctext">passthru_ptime_mismatch</span></a></li>
<li class="toclevel-2"><a href="#conference_enforce_security"><span class="tocnumber">17.7</span> <span class="toctext">conference_enforce_security</span></a></li>
<li class="toclevel-2"><a href="#suppress-cng"><span class="tocnumber">17.8</span> <span class="toctext">suppress-cng</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#IVR_related"><span class="tocnumber">18</span> <span class="toctext">自动语音应答(IVR)相关</span></a>
<ul>
<li class="toclevel-2"><a href="#ivr_menu_terminator"><span class="tocnumber">18.1</span> <span class="toctext">ivr_menu_terminator</span></a></li>
<li class="toclevel-2"><a href="#detect_speech_result"><span class="tocnumber">18.2</span> <span class="toctext">detect_speech_result</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#SIP_related_variables"><span class="tocnumber">19</span> <span class="toctext">SIP协议相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#disable_hold"><span class="tocnumber">19.1</span> <span class="toctext">disable_hold</span></a></li>
<li class="toclevel-2"><a href="#sip_acl_authed_by"><span class="tocnumber">19.2</span> <span class="toctext">sip_acl_authed_by</span></a></li>
<li class="toclevel-2"><a href="#sip_acl_token"><span class="tocnumber">19.3</span> <span class="toctext">sip_acl_token</span></a></li>
<li class="toclevel-2"><a href="#sip_copy_multipart"><span class="tocnumber">19.4</span> <span class="toctext">sip_copy_multipart</span></a></li>
<li class="toclevel-2"><a href="#sip_invite_domain"><span class="tocnumber">19.5</span> <span class="toctext">sip_invite_domain</span></a></li>
<li class="toclevel-2"><a href="#sip_invite_from_params"><span class="tocnumber">19.6</span> <span class="toctext">sip_invite_from_params</span></a></li>
<li class="toclevel-2"><a href="#sip_network_destination"><span class="tocnumber">19.7</span> <span class="toctext">sip_network_destination</span></a></li>
<li class="toclevel-2"><a href="#sip_auth_username"><span class="tocnumber">19.8</span> <span class="toctext">sip_auth_username</span></a></li>
<li class="toclevel-2"><a href="#sip_auth_password"><span class="tocnumber">19.9</span> <span class="toctext">sip_auth_password</span></a></li>
<li class="toclevel-2"><a href="#sip_auto_simplify"><span class="tocnumber">19.10</span> <span class="toctext">sip_auto_simplify</span></a></li>
<li class="toclevel-2"><a href="#sip_callee_id_name_2"><span class="tocnumber">19.11</span> <span class="toctext">sip_callee_id_name</span></a></li>
<li class="toclevel-2"><a href="#sip_callee_id_number_2"><span class="tocnumber">19.12</span> <span class="toctext">sip_callee_id_number</span></a></li>
<li class="toclevel-2"><a href="#sip_force_audio_fmtp"><span class="tocnumber">19.13</span> <span class="toctext">sip_force_audio_fmtp</span></a></li>
<li class="toclevel-2"><a href="#sip_invite_req_uri"><span class="tocnumber">19.14</span> <span class="toctext">sip_invite_req_uri</span></a></li>
<li class="toclevel-2"><a href="#sip_invite_to_uri"><span class="tocnumber">19.15</span> <span class="toctext">sip_invite_to_uri</span></a></li>
<li class="toclevel-2"><a href="#sip_ignore_reinvites"><span class="tocnumber">19.16</span> <span class="toctext">sip_ignore_reinvites</span></a></li>
<li class="toclevel-2"><a href="#sip_has_crypto"><span class="tocnumber">19.17</span> <span class="toctext">sip_has_crypto</span></a></li>
<li class="toclevel-2"><a href="#sip_secure_media"><span class="tocnumber">19.18</span> <span class="toctext">sip_secure_media</span></a></li>
<li class="toclevel-2"><a href="#timer_name"><span class="tocnumber">19.19</span> <span class="toctext">timer_name</span></a></li>
<li class="toclevel-2"><a href="#ignore_display_updates"><span class="tocnumber">19.20</span> <span class="toctext">ignore_display_updates</span></a></li>
<li class="toclevel-2"><a href="#deny_refer_requests"><span class="tocnumber">19.21</span> <span class="toctext">deny_refer_requests</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#SDP_Manipulation"><span class="tocnumber">20</span> <span class="toctext">会话描述协议(SDP) 处理</span></a>
<ul>
<li class="toclevel-2"><a href="#sdp_m_per_ptime"><span class="tocnumber">20.1</span> <span class="toctext">sdp_m_per_ptime</span></a></li>
<li class="toclevel-2"><a href="#switch_r_sdp"><span class="tocnumber">20.2</span> <span class="toctext">switch_r_sdp</span></a></li>
<li class="toclevel-2"><a href="#switch_l_sdp"><span class="tocnumber">20.3</span> <span class="toctext">switch_l_sdp</span></a></li>
<li class="toclevel-2"><a href="#switch_m_sdp"><span class="tocnumber">20.4</span> <span class="toctext">switch_m_sdp</span></a></li>
<li class="toclevel-2"><a href="#sip_append_audio_sdp"><span class="tocnumber">20.5</span> <span class="toctext">sip_append_audio_sdp</span></a></li>
<li class="toclevel-2"><a href="#sip_ignore_183nosdp"><span class="tocnumber">20.6</span> <span class="toctext">sip_ignore_183nosdp</span></a></li>
<li class="toclevel-2"><a href="#verbose_sdp"><span class="tocnumber">20.7</span> <span class="toctext">verbose_sdp</span></a></li>
<li class="toclevel-2"><a href="#sip_local_sdp_str"><span class="tocnumber">20.8</span> <span class="toctext">sip_local_sdp_str</span></a></li>
<li class="toclevel-2"><a href="#sip_enable_soa"><span class="tocnumber">20.9</span> <span class="toctext">sip_enable_soa</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#FIFO_related_variables"><span class="tocnumber">21</span> <span class="toctext">FIFO(先进先出)模块 相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#fifo_bridged"><span class="tocnumber">21.1</span> <span class="toctext">fifo_bridged</span></a></li>
<li class="toclevel-2"><a href="#fifo_caller_consumer_import"><span class="tocnumber">21.2</span> <span class="toctext">fifo_caller_consumer_import</span></a></li>
<li class="toclevel-2"><a href="#fifo_consumer_caller_import"><span class="tocnumber">21.3</span> <span class="toctext">fifo_consumer_caller_import</span></a></li>
<li class="toclevel-2"><a href="#fifo_manual_bridged"><span class="tocnumber">21.4</span> <span class="toctext">fifo_manual_bridged</span></a></li>
<li class="toclevel-2"><a href="#fifo_position"><span class="tocnumber">21.5</span> <span class="toctext">fifo_position</span></a></li>
<li class="toclevel-2"><a href="#fifo_role"><span class="tocnumber">21.6</span> <span class="toctext">fifo_role</span></a></li>
<li class="toclevel-2"><a href="#transfer_after_bridge"><span class="tocnumber">21.7</span> <span class="toctext">transfer_after_bridge</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Playback_related_variables"><span class="tocnumber">22</span> <span class="toctext">语音回放相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#playback_terminators"><span class="tocnumber">22.1</span> <span class="toctext">playback_terminators</span></a></li>
<li class="toclevel-2"><a href="#sound_prefix"><span class="tocnumber">22.2</span> <span class="toctext">sound_prefix</span></a></li>
<li class="toclevel-2"><a href="#playback_terminator_used"><span class="tocnumber">22.3</span> <span class="toctext">playback_terminator_used</span></a></li>
<li class="toclevel-2"><a href="#playback_ms"><span class="tocnumber">22.4</span> <span class="toctext">playback_ms</span></a></li>
<li class="toclevel-2"><a href="#playback_samples"><span class="tocnumber">22.5</span> <span class="toctext">playback_samples</span></a></li>
<li class="toclevel-2"><a href="#playback_sleep_val"><span class="tocnumber">22.6</span> <span class="toctext">playback_sleep_val</span></a></li>
<li class="toclevel-2"><a href="#playback_delimiter"><span class="tocnumber">22.7</span> <span class="toctext">playback_delimiter</span></a></li>
<li class="toclevel-2"><a href="#sleep_eat_digits"><span class="tocnumber">22.8</span> <span class="toctext">sleep_eat_digits</span></a></li>
<li class="toclevel-2"><a href="#playback_timeout_sec"><span class="tocnumber">22.9</span> <span class="toctext">playback_timeout_sec</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Originate_related_variables"><span class="tocnumber">23</span> <span class="toctext">外呼相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#execute_on_originate"><span class="tocnumber">23.1</span> <span class="toctext">execute_on_originate</span></a></li>
<li class="toclevel-2"><a href="#leg_delay_start"><span class="tocnumber">23.2</span> <span class="toctext">leg_delay_start</span></a></li>
<li class="toclevel-2"><a href="#originate_disposition"><span class="tocnumber">23.3</span> <span class="toctext">originate_disposition</span></a></li>
<li class="toclevel-2"><a href="#originate_retries"><span class="tocnumber">23.4</span> <span class="toctext">originate_retries</span></a></li>
<li class="toclevel-2"><a href="#originate_retry_sleep_ms"><span class="tocnumber">23.5</span> <span class="toctext">originate_retry_sleep_ms</span></a></li>
<li class="toclevel-2"><a href="#originate_timeout_2"><span class="tocnumber">23.6</span> <span class="toctext">originate_timeout</span></a></li>
<li class="toclevel-2"><a href="#originating_leg_uuid"><span class="tocnumber">23.7</span> <span class="toctext">originating_leg_uuid</span></a></li>
<li class="toclevel-2"><a href="#origination_channel_name"><span class="tocnumber">23.8</span> <span class="toctext">origination_channel_name</span></a></li>
<li class="toclevel-2"><a href="#origination_caller_id_name"><span class="tocnumber">23.9</span> <span class="toctext">origination_caller_id_name</span></a></li>
<li class="toclevel-2"><a href="#origination_caller_id_number"><span class="tocnumber">23.10</span> <span class="toctext">origination_caller_id_number</span></a></li>
<li class="toclevel-2"><a href="#origination_cancel_key"><span class="tocnumber">23.11</span> <span class="toctext">origination_cancel_key</span></a></li>
<li class="toclevel-2"><a href="#origination_privacy"><span class="tocnumber">23.12</span> <span class="toctext">origination_privacy</span></a></li>
<li class="toclevel-2"><a href="#origination_uuid"><span class="tocnumber">23.13</span> <span class="toctext">origination_uuid</span></a></li>
<li class="toclevel-2"><a href="#originator"><span class="tocnumber">23.14</span> <span class="toctext">originator</span></a></li>
<li class="toclevel-2"><a href="#originator_codec"><span class="tocnumber">23.15</span> <span class="toctext">originator_codec</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#RTP.2Fmedia_related_variables"><span class="tocnumber">24</span> <span class="toctext">RTP(媒体实时传输协议)/媒体 相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#bypass_media"><span class="tocnumber">24.1</span> <span class="toctext">bypass_media</span></a></li>
<li class="toclevel-2"><a href="#bypass_media_after_bridge"><span class="tocnumber">24.2</span> <span class="toctext">bypass_media_after_bridge</span></a></li>
<li class="toclevel-2"><a href="#proxy_media"><span class="tocnumber">24.3</span> <span class="toctext">proxy_media</span></a></li>
<li class="toclevel-2"><a href="#rtp_autoflush"><span class="tocnumber">24.4</span> <span class="toctext">rtp_autoflush</span></a></li>
<li class="toclevel-2"><a href="#rtp_autoflush_during_bridge"><span class="tocnumber">24.5</span> <span class="toctext">rtp_autoflush_during_bridge</span></a></li>
<li class="toclevel-2"><a href="#disable_rtp_auto_adjust"><span class="tocnumber">24.6</span> <span class="toctext">disable_rtp_auto_adjust</span></a></li>
<li class="toclevel-2"><a href="#progress_timeout"><span class="tocnumber">24.7</span> <span class="toctext">progress_timeout</span></a></li>
<li class="toclevel-2"><a href="#bridge_answer_timeout"><span class="tocnumber">24.8</span> <span class="toctext">bridge_answer_timeout</span></a></li>
<li class="toclevel-2"><a href="#ignore_early_media"><span class="tocnumber">24.9</span> <span class="toctext">ignore_early_media</span></a></li>
<li class="toclevel-2"><a href="#ringback"><span class="tocnumber">24.10</span> <span class="toctext">ringback</span></a></li>
<li class="toclevel-2"><a href="#instant_ringback"><span class="tocnumber">24.11</span> <span class="toctext">instant_ringback</span></a></li>
<li class="toclevel-2"><a href="#transfer_ringback"><span class="tocnumber">24.12</span> <span class="toctext">transfer_ringback</span></a></li>
<li class="toclevel-2"><a href="#disable_hold_2"><span class="tocnumber">24.13</span> <span class="toctext">disable_hold</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#RTCP_Related"><span class="tocnumber">25</span> <span class="toctext">RTCP(媒体实时传输控制协议) 相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#rtcp_packet_count"><span class="tocnumber">25.1</span> <span class="toctext">rtcp_packet_count</span></a></li>
<li class="toclevel-2"><a href="#rtcp_octet_count"><span class="tocnumber">25.2</span> <span class="toctext">rtcp_octet_count</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Camp-on_related_variables"><span class="tocnumber">26</span> <span class="toctext">Camp-on related variables</span></a>
<ul>
<li class="toclevel-2"><a href="#campon"><span class="tocnumber">26.1</span> <span class="toctext">campon</span></a></li>
<li class="toclevel-2"><a href="#campon_retries"><span class="tocnumber">26.2</span> <span class="toctext">campon_retries</span></a></li>
<li class="toclevel-2"><a href="#campon_timeout"><span class="tocnumber">26.3</span> <span class="toctext">campon_timeout</span></a></li>
<li class="toclevel-2"><a href="#campon_sleep"><span class="tocnumber">26.4</span> <span class="toctext">campon_sleep</span></a></li>
<li class="toclevel-2"><a href="#campon_fallback_exten"><span class="tocnumber">26.5</span> <span class="toctext">campon_fallback_exten</span></a></li>
<li class="toclevel-2"><a href="#campon_fallback_dialplan"><span class="tocnumber">26.6</span> <span class="toctext">campon_fallback_dialplan</span></a></li>
<li class="toclevel-2"><a href="#campon_fallback_context"><span class="tocnumber">26.7</span> <span class="toctext">campon_fallback_context</span></a></li>
<li class="toclevel-2"><a href="#campon_hold_music"><span class="tocnumber">26.8</span> <span class="toctext">campon_hold_music</span></a></li>
<li class="toclevel-2"><a href="#campon_stop_key"><span class="tocnumber">26.9</span> <span class="toctext">campon_stop_key</span></a></li>
<li class="toclevel-2"><a href="#campon_announce_sound"><span class="tocnumber">26.10</span> <span class="toctext">campon_announce_sound</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Answer_confirmation_variables"><span class="tocnumber">27</span> <span class="toctext">呼叫确认应答相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#group_confirm_file"><span class="tocnumber">27.1</span> <span class="toctext">group_confirm_file</span></a></li>
<li class="toclevel-2"><a href="#group_confirm_key"><span class="tocnumber">27.2</span> <span class="toctext">group_confirm_key</span></a></li>
<li class="toclevel-2"><a href="#group_confirm_cancel_timeout"><span class="tocnumber">27.3</span> <span class="toctext">group_confirm_cancel_timeout</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Voicemail_Related_Variables"><span class="tocnumber">28</span> <span class="toctext">语音邮件相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#voicemail_alternate_greet_id"><span class="tocnumber">28.1</span> <span class="toctext">voicemail_alternate_greet_id</span></a></li>
<li class="toclevel-2"><a href="#voicemail_greeting_number"><span class="tocnumber">28.2</span> <span class="toctext">voicemail_greeting_number</span></a></li>
<li class="toclevel-2"><a href="#vm_message_ext"><span class="tocnumber">28.3</span> <span class="toctext">vm_message_ext</span></a></li>
<li class="toclevel-2"><a href="#vm_cc"><span class="tocnumber">28.4</span> <span class="toctext">vm_cc</span></a></li>
<li class="toclevel-2"><a href="#skip_greeting"><span class="tocnumber">28.5</span> <span class="toctext">skip_greeting</span></a></li>
<li class="toclevel-2"><a href="#skip_instructions"><span class="tocnumber">28.6</span> <span class="toctext">skip_instructions</span></a></li>
<li class="toclevel-2"><a href="#voicemail_authorized"><span class="tocnumber">28.7</span> <span class="toctext">voicemail_authorized</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#Events"><span class="tocnumber">29</span> <span class="toctext">事件相关</span></a>
<ul>
<li class="toclevel-2"><a href="#fire_asr_events"><span class="tocnumber">29.1</span> <span class="toctext">fire_asr_events</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#System_Related_Variables"><span class="tocnumber">30</span> <span class="toctext">系统相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#base_dir"><span class="tocnumber">30.1</span> <span class="toctext">base_dir</span></a></li>
</ul>
</li>
<li class="toclevel-1"><a href="#OpenZap_Related_Variables"><span class="tocnumber">31</span> <span class="toctext">OpenZap 相关变量</span></a>
<ul>
<li class="toclevel-2"><a href="#openzap_span_number"><span class="tocnumber">31.1</span> <span class="toctext">openzap_span_number</span></a></li>
<li class="toclevel-2"><a href="#openzap_chan_number"><span class="tocnumber">31.2</span> 
<span class="toctext">openzap_chan_number</span></a></li>
</ul>
</li>
</ul>
</td></tr></table>

------


<a name="Introduction" id="Introduction"></a><h2> 
<span class="mw-headline"> 简介</span></h2>
<p>在拨号计划或者你的应用中可以设置很多个通道变量，用来设置呼叫参数.或者控制呼叫流程
</p>
<a name="Channel_Variables_in_the_XML_Dialplan" id="Channel_Variables_in_the_XML_Dialplan"></a><h3> 
<span class="mw-headline"> 在XML拨号计划中设置通道变量 </span></h3>
<p>使用应用<i>set</i> 来设置通道变量:
</p>
<pre>&lt;action application="set" data="var_name=var value"/&gt;
</pre>
<p>引用通道变量，需要使用${} 语法:
</p>
<pre>&lt;action application="log" data="INFO The value in the var_name chan var is ${var_name}"/&gt;
</pre>

<a name="Scoped_Variables" id="Scoped_Variables"></a><h4> 
<span class="mw-headline"> 限定作用域的通道变量 </span></h4>
<p>- 之前，通道变量对会话是全局的.也就是说，通道变量只要设置一次，便可存在于整个会话中.<br />
- 使用限定作用域的通道变量, 你可以让通道变量只存在于单个应用和该应用下任何后续的应用执行期间.<br />
- 应用可以利用这个特性使用已经命名的输入参数<br />
<br />
从 2011年 6月15日 (git commit b2c3199f) 后， 你应该可以使用限定作用域的通道变量了，它只会在某一个给定的拨号计划应用执行期间有效.
也就是说，当这个应用执行完成，该变量将失效.
请看以下例子:
</p>
<pre>
&lt;action application=&quot;log&quot; data=&quot;INFO myvar is '${myvar}'&quot;/&gt;
&lt;action application=&quot;log&quot; data=&quot;%[myvar=Hello]INFO myvar is '${myvar}'&quot;/&gt;
&lt;action application=&quot;log&quot; data=&quot;INFO myvar is '${myvar}'&quot;/&gt;
&lt;action application=”myapp” data=”%[var1=val1,var2=val2]mydata”/&gt;
</pre>
<a name="Channel_Variables_in_Dial_strings" id="Channel_Variables_in_Dial_strings"></a><h3> <span class="mw-headline"> Channel Variables in Dial strings </span></h3>
<p>The syntax of using { } versus [] is explained below.
</p>
<ul><li>{foo=bar} is <b>only</b> valid at the beginning of the dial string. It will set the same variables on <b>every</b> channel.
</li><li>[foo=bar] goes before each individual dial string and will set the variable values specified for only this channel.
</li></ul>
<ul><li>The following example sets the foo variable for all channels implemented and chan=1 is specific to blah, while chan=2 is specific to blah2
</li></ul>
<pre>{foo=bar}[chan=1]sofia/default/blah@baz.com,[chan=2]sofia/default/blah2@baz.com
</pre>
<ul><li>Setting multiple variables can be accomplished by comma delimiting:
</li></ul>
<pre>[var1=abc,var2=def,var3=ghi]sofia/default/blah@baz.com&lt;/pre&gt;
</pre>
<ul><li>If you would like to have variables in [] override the same variables set in {}, you may set 'local_var_clobber=true' inside {}. For example:
</li></ul>
<pre>{local_var_clobber=true,sip_secure_media=true}sofia/default/blah1@baz.com|sofia/default/johndoe@example.com|[sip_secure_media=false]sofia/default/janedoe@acme.com
</pre>
<p>In this example, the legs for blah1@baz.com and johndoe@example.com would be set to offer SRTP (RTP/SAVP) while janedoe@acme.com would not receive an SRTP offer (she would see RTP/AVP instead).
</p>
<a name="Handling_Variables_With_Commas" id="Handling_Variables_With_Commas"></a><h4> <span class="mw-headline"> Handling Variables With Commas </span></h4>
<p>Since commas are the default delimiter inside of {} and [] it is necessary to have an alternate means of delimiting values that actually contain commas.
</p><p>To set a variable with a "," inside of it (e.g. the absolute_codec_string), you must tell FreeSWITCH what delimiter to use instead for THIS value.
</p><p>The syntax is to put a prefix of ^^: at the start of the value and replace the <i>commas in the value</i> with ":". Then, FreeSWITCH will substitute commans back in when setting the value for the channel.
</p><p>You can use any (almost) character you like though, it uses the one after the initial "^^"
</p>
<pre>{absolute_codec_string=^^:PCMA@8000h@20i@64000b:PCMU@8000h@20i@64000b:G729@8000h@20i@8000b,leg_time_out=10,process_cdr=b_only}
</pre>
<a name="Exporting_Channel_Variables_in_Bridge_Operations" id="Exporting_Channel_Variables_in_Bridge_Operations"></a><h3> <span class="mw-headline"> Exporting Channel Variables in Bridge Operations </span></h3>
<p>You can export a variable from one call leg (A) to the other call leg (B) by using the 'export_vars' variable which is a comma separated list of variables that you wish to propagate across calls.
Usage:
</p>
<pre>&lt;action application="set" data="export_vars=myvar,myvar2,foo,bar"/&gt;
</pre>
<p>You can also set a variable on the (A) leg and add it to the export list in one step with the export application:
</p>
<pre>&lt;action application="export" data="myvar=true"/&gt;
</pre>
<a name="Using_Channel_Variables_in_Dialplan_Condition_Statements" id="Using_Channel_Variables_in_Dialplan_Condition_Statements"></a><h3> <span class="mw-headline"> Using Channel Variables in Dialplan Condition Statements </span></h3>
<p>Channel variables can be used in conditions:
</p>
<ul><li> See <a href="/wiki/Dialplan_XML#Condition" title="Dialplan XML">this</a> page for specifics.
</li><li> Keep in mind that some channel variables may not be set during the dialplan parsing phase. See <a href="/wiki/Dialplan_XML#Inline_Actions" title="Dialplan XML">inline actions</a> section of <a href="/wiki/Dialplan_XML" title="Dialplan XML">Dialplan_XML</a> for more information.
</li></ul>
<a name="Custom_Channel_Variables" id="Custom_Channel_Variables"></a><h3> <span class="mw-headline"> Custom Channel Variables </span></h3>
<p>Additionally, you may set any number of unique channel variables for your own purposes and even elect to log them to the CDR records.  In order to set any channel variable, use the application "set" to effect the setting.  You can also set channel variables on the command issued via XML-RPC or Event Socket by adding {myvar=myval,myvar1=myval1} i.e.,
</p>
<pre>originate {ignore_early_media=true}sofia/mydomain.com/18005551212@1.2.3.4 15555551212</pre>
<p>If the value you are setting has a space in it then you will need to enclose the value in quotes.  An example of this is
</p>
<pre>originate {fax_ident=1231231234,fax_header='Fax Test'}sofia/gateway/outbound.fax/1004 &amp;txfax(/tmp/fax.tiff)</pre>
<a name="Channel_Variable_Manipulation" id="Channel_Variable_Manipulation"></a><h3> <span class="mw-headline"> Channel Variable Manipulation </span></h3>
<p>Channel variables can be manipulated for varied results. For example, you can trim bits and pieces of a channel variable, perhaps to get the first three digits of a phone number. See <a href="/wiki/Manipulating_Channel_Variables" title="Manipulating Channel Variables">Manipulating Channel Variables</a> for more information.
</p>
<a name="Info_Application_Variable_Names_.28variable_xxxx.29" id="Info_Application_Variable_Names_.28variable_xxxx.29"></a><h2> <span class="mw-headline"> Info Application Variable Names (variable_xxxx) </span></h2>
<p>Some variables, as shown from the info app, may have variable_ in front of their names.  For example, if you pass a header variable called 'type' from the proxy server, it will get displayed as 'variable_sip_h_type' in FreeSWITCH. 
To access that variable, you should strip off the variable_, and just do ${sip_h_type}. Other variables shown in the info app are prepended with channel, which should be stripped as well. The example below show a list of info app variables and the corresponding channel variable names:
</p>
<table cellspacing="0" cellpadding="0">
  <tr>
    <td height="17" width="250"><strong>Info variable name</strong></td>
    <td width="181"><strong>channel variable name</strong></td>
    <td width="250"><strong>Description</strong></td>
  </tr>
  <tr>
    <td height="17">Channel-State</td>
    <td>state</td>
    <td>Current <a href="/wiki/Channel_States" title="Channel States">state</a> of the call</td>
  </tr>
  <tr>
    <td height="17">Channel-State-Number</td>
    <td>state_number</td>
    <td>Integer</td>
  </tr>
  <tr>
    <td height="17">Channel-Name</td>
    <td>channel_name</td>
    <td>Channel name</td>
  </tr>
  <tr>
    <td height="17">Unique-ID</td>
    <td>uuid</td>
    <td>uuid of this channel's <a href="/wiki/Call_Legs" title="Call Legs">call leg</a></td>
  </tr>
  <tr>
    <td height="17">Call-Direction</td>
    <td>direction</td>
    <td>Inbound or Outbound</td>
  </tr>
  <tr>
    <td height="17">Answer-State</td>
    <td>state</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Channel-Read-Codec-Name</td>
    <td>read_codec</td>
    <td>the read codec variable mean the source codec</td>
  </tr>
  <tr>
    <td height="17">Channel-Read-Codec-Rate</td>
    <td>read_rate</td>
    <td>the source rate</td>
  </tr>
  <tr>
    <td height="17">Channel-Write-Codec-Name</td>
    <td>write_codec</td>
    <td>the destination codec same to write_codec if not transcoded</td>
  </tr>
  <tr>
    <td height="17">Channel-Write-Codec-Rate</td>
    <td>write_rate</td>
    <td>destination rate same to read rate if not transcoded</td>
  </tr>
  <tr>
    <td height="17">Caller-Username</td>
    <td>username</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Dialplan</td>
    <td>dialplan</td>
    <td>user dialplan like xml, lua, enum, lcr</td>
  </tr>
  <tr>
    <td height="17">Caller-Caller-ID-Name</td>
    <td>caller_id_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Caller-ID-Number</td>
    <td>caller_id_number</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-ANI</td>
    <td>ani</td>
    <td>ANI of caller, frequently the same as caller ID number</td>
  </tr>
  <tr>
    <td height="17">Caller-ANI-II</td>
    <td>aniii</td>
    <td>ANI II Digits (OLI - Originating Line Information), if available.   Refer to:  <a href="http://www.nanpa.com/number_resource_info/ani_ii_digits.html" class="external free" title="http://www.nanpa.com/number_resource_info/ani_ii_digits.html" rel="nofollow">http://www.nanpa.com/number_resource_info/ani_ii_digits.html</a></td>
  </tr>
  <tr>
    <td height="17">Caller-Network-Addr</td>
    <td>network_addr</td>
    <td>IP address of calling party</td>
  </tr>
  <tr>
    <td height="17">Caller-Destination-Number</td>
    <td>destination_number</td>
    <td>Destination (dialed) number</td>
  </tr>
  <tr>
    <td height="17">Caller-Unique-ID</td>
    <td>uuid</td>
    <td>This channel's uuid</td>
  </tr>
  <tr>
    <td height="17">Caller-Source</td>
    <td>source</td>
    <td>Source module, i.e. mod_sofia, mod_openzap, etc.</td>
  </tr>
  <tr>
    <td height="17">Caller-Context</td>
    <td>context</td>
    <td>Dialplan context</td>
  </tr>
  <tr>
    <td height="17">Caller-RDNIS</td>
    <td>rdnis</td>
    <td>Redirected DNIS info. See <a href="/wiki/Misc._Dialplan_Tools_transfer" title="Misc. Dialplan Tools transfer">transfer</a> application</td>
  </tr>
  <tr>
    <td height="17">Caller-Channel-Name</td>
    <td>channel_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Profile-Index</td>
    <td>profile_index</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Channel-Created-Time</td>
    <td>created_time</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Channel-Answered-Time</td>
    <td>answered_time</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Channel-Hangup-Time</td>
    <td>hangup_time</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Channel-Transfer-Time</td>
    <td>transfer_time</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Screen-Bit</td>
    <td>screen_bit</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Privacy-Hide-Name</td>
    <td>privacy_hide_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">Caller-Privacy-Hide-Number</td>
    <td>privacy_hide_number</td>
    <td>This variable tells you if the inbound call is asking for CLIR[Calling Line ID
presentation Restriction] (either with anonymous method or Privacy:id method)</td>
  </tr>
  <tr>
    <td height="17">variable_sip_received_ip</td>
    <td>sip_received_ip</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_received_port</td>
    <td>sip_received_port</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_authorized</td>
    <td>sip_authorized</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_mailbox</td>
    <td>sip_mailbox</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_auth_username</td>
    <td>sip_auth_username</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_auth_realm</td>
    <td>sip_auth_realm</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_mailbox</td>
    <td>mailbox</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_user_name</td>
    <td>user_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_domain_name</td>
    <td>domain_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_record_stereo</td>
    <td>record_stereo</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_accountcode</td>
    <td>accountcode</td>
    <td>Accountcode for the call. This is an arbitrary value. It can be defined in the user variables in the directory, or it can be set/modified from dialplan. The accountcode may be used to force a specific CDR CSV template for the call.</td>
  </tr>
  <tr>
    <td height="17">variable_user_context</td>
    <td>user_context</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_effective_caller_id_name</td>
    <td>effective_caller_id_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_effective_caller_id_number</td>
    <td>effective_caller_id_number</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_caller_domain</td>
    <td>caller_domain</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_from_user</td>
    <td>sip_from_user</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_from_uri</td>
    <td>sip_from_uri</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_from_host</td>
    <td>sip_from_host</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_from_user_stripped</td>
    <td>sip_from_user_stripped</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_from_tag</td>
    <td>sip_from_tag</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sofia_profile_name</td>
    <td>sofia_profile_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sofia_profile_domain_name</td>
    <td>sofia_profile_domain_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_full_route</td>
    <td>sip_full_route</td>
    <td>The complete contents of the Route: header.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_full_via</td>
    <td>sip_full_via</td>
    <td>The complete contents of the Via: header.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_full_from</td>
    <td>sip_full_from</td>
    <td>The complete contents of the From: header.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_full_to</td>
    <td>sip_full_to</td>
    <td>The complete contents of the To: header.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_req_params</td>
    <td>sip_req_params</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_req_user</td>
    <td>sip_req_user</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_req_uri</td>
    <td>sip_req_uri</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_req_host</td>
    <td>sip_req_host</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_to_params</td>
    <td>sip_to_params</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_to_user</td>
    <td>sip_to_user</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_to_uri</td>
    <td>sip_to_uri</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_to_host</td>
    <td>sip_to_host</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_contact_params</td>
    <td>sip_contact_params</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_contact_user</td>
    <td>sip_contact_user</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_contact_port</td>
    <td>sip_contact_port</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_contact_uri</td>
    <td>sip_contact_uri</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_contact_host</td>
    <td>sip_contact_host</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_invite_domain</td>
    <td>sip_invite_domain</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_channel_name</td>
    <td>channel_name</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_call_id</td>
    <td>sip_call_id</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_user_agent</td>
    <td>sip_user_agent</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_via_host</td>
    <td>sip_via_host</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_via_port</td>
    <td>sip_via_port</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_via_rport</td>
    <td>sip_via_rport</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_presence_id</td>
    <td>presence_id</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_h_P-Key-Flags</td>
    <td>sip_h_p-key-flags</td>
    <td>This will contain the optional  P-Key-Flags header(s) that may be received from calling endpoint.</td>
  </tr>
  <tr>
    <td height="17">variable_switch_r_sdp</td>
    <td>switch_r_sdp</td>
    <td>The whole SDP received from calling endpoint.</td>
  </tr>
  <tr>
    <td height="17">variable_remote_media_ip</td>
    <td>remote_media_ip</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_remote_media_port</td>
    <td>remote_media_port</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_write_codec</td>
    <td>write_codec</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_write_rate</td>
    <td>write_rate</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_endpoint_disposition</td>
    <td>endpoint_disposition</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_dialed_ext</td>
    <td>dialed_ext</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_transfer_ringback</td>
    <td>transfer_ringback</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_call_timeout</td>
    <td>call_timeout</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_hangup_after_bridge</td>
    <td>hangup_after_bridge</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_continue_on_fail</td>
    <td>continue_on_fail</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_dialed_user</td>
    <td>dialed_user</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_dialed_domain</td>
    <td>dialed_domain</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_redirect_contact_user_0</td>
    <td>sip_redirect_contact_user_0</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_redirect_contact_host_0</td>
    <td>sip_redirect_contact_host_0</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_h_Referred-By</td>
    <td>sip_h_referred-by</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_refer_to</td>
    <td>sip_refer_to</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_max_forwards</td>
    <td>max_forwards</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_originate_disposition</td>
    <td>originate_disposition</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_read_codec</td>
    <td>read_codec</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_read_rate</td>
    <td>read_rate</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_open</td>
    <td>open</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_use_profile</td>
    <td>use_profile</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_current_application</td>
    <td>current_application</td>
    <td>.</td>
  </tr>
  <tr>
    <td height="17">variable_ep_codec_string</td>
    <td>ep_codec_string</td>
    <td>This variable is only available if late negotiation is enabled on the profile. It's a readable string containing all the codecs proposed by the calling endpoint. This can be easily parsed in the dialplan.</td>
  </tr>
  <tr>
    <td height="17">variable_disable_hold</td>
    <td>disable_hold</td>
    <td>This variable when set will disable the hold feature of the phone.</td>
  </tr>
  <tr>
    <td height="17">variable_sip_acl_authed_by</td>
    <td>sip_acl_authed_by </td>
    <td>This variable holds what ACL rule allowed the call.</td>
  </tr>
  <tr>
    <td height="17">variable_curl_response_data</td>
    <td>curl_response_data</td>
    <td>This variable stores the output from the last curl made.</td>
  </tr>
</table>
<a name=".24.7Bvariable.7D_vs._.24.24.7Bvariable.7D" id=".24.7Bvariable.7D_vs._.24.24.7Bvariable.7D"></a><h2> <span class="mw-headline">${variable} vs. $${variable}</span></h2>
<p>${variables} are channel variables that may be set in the dialplan, application or directory that effect progress or settings for the call.
</p><p>$${variables} are expanded when the master freeswitch.xml is compiled. This happens when you start FreeSWITCH, or when <i>reloadxml</i> is called.
</p><p>The key is that $${variables} are evaluated once by the preprocessor, and ${variables} are evaluated fresh each time they are executed (for example when a call connects).
</p>
<a name="CDR_related" id="CDR_related"></a><h2> <span class="mw-headline"> CDR related </span></h2>
<a name="process_cdr" id="process_cdr"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_process_cdr" title="Variable process cdr"> process_cdr</a> </span></h3>
<p><b>Indicates how to process CDR records.</b>
</p><p>Can be undefined or set to "false", "true", "a_only", "b_only"
</p>
<ul><li> false - indicates to not process the record.<br />
</li><li> true - or undefined indicates the default behavior which is to process all CDR records.<br />
</li><li> a_only - indicates to only process CDR records on the inbound leg of a call.<br />
</li><li> b_only - indicates to only process CDR records on the outbound leg of a call.<br />
</li></ul>
<p><i>This variable is unconditionally exported</i>
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="process_cdr=a_only"/&gt;
</pre>
<p><br />
</p>
<a name="accountcode" id="accountcode"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_accountcode" title="Variable accountcode"> accountcode</a> </span></h3>
<p>Account code is mostly an arbitrary value that you can assign on a per leg basis. An important feature of <i>accountcode</i> is that if its value matches one of the CDR CSV templates defined in <b>cdr_csv.conf.xml</b> then that CDR template will be used when generating a CSV CDR.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="accountcode=custom"/&gt;
</pre>
<p><br />
</p>
<a name="Hangup_Causes" id="Hangup_Causes"></a><h2> <span class="mw-headline"> Hangup Causes </span></h2>
<a name="bridge_hangup_cause" id="bridge_hangup_cause"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_bridge_hangup_cause" title="Variable bridge hangup cause"> bridge_hangup_cause</a> </span></h3>
<p>This is set to the hangup cause of the last bridged B leg of the call. If you have continue_on_fail=true and hangup_after_bridge=false you can do checks on this to see what "really" happened to the call. You can for instance do execute_extension after bridge, do a condition check on ${bridge_hangup_cause} to see if it contains MEDIA_TIMEOUT and then trigger a redial of the call or transfer to a cell phone. For a list of hangup causes, see <a href="/wiki/Hangup_Causes" title="Hangup Causes">Hangup Causes</a>.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="log" data="1 B-leg hangup cause: ${bridge_hangup_cause}"/&gt;
</pre>
<p><br />
</p>
<a name="disable_q850_reason" id="disable_q850_reason"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_disable_q850_reason" title="Variable disable q850 reason"> disable_q850_reason</a> </span></h3>
<p>When set to true, this disables sending of the Reason header, which includes the Q.850 reason code, in responses and BYEs. For a list of hangup causes and their Q.850 codes, see <a href="/wiki/Hangup_Causes" title="Hangup Causes">Hangup Causes</a>. This is available as of revision 15850 committed 12/8/2009.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="disable_q850_reason=true"/&gt;
</pre>
<p><br />
</p>
<a name="hangup_cause" id="hangup_cause"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_hangup_cause" title="Variable hangup cause"> hangup_cause</a> </span></h3>
<p>This is set to the hangup cause of the A leg of the call (note that as such it doesn't make much sense before the end of the call). Often this will take the hangup cause from the B leg of the call, if there is one. For a list of hangup causes, see <a href="/wiki/Hangup_Causes" title="Hangup Causes">Hangup Causes</a>.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="log" data="1 A-leg hangup cause: ${hangup_cause}"/&gt;
</pre>
<p><br />
</p>
<a name="hangup_cause_q850" id="hangup_cause_q850"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_hangup_cause_q850" title="Variable hangup cause q850"> hangup_cause_q850</a> </span></h3>
<p>This is set to the Q850 numeric code of the hangup cause of the A leg of the call (note that as such it doesn't make much sense before the end of the call). Often this will take the hangup cause from the B leg of the call, if there is one. For a list of hangup causes, see <a href="/wiki/Hangup_Causes" title="Hangup Causes">Hangup Causes</a>.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="log" data="1 A-leg hangup Q850 cause: ${hangup_cause_q850}"/&gt;
</pre>
<p><br />
</p>
<a name="sip_hangup_disposition" id="sip_hangup_disposition"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_hangup_disposition" title="Variable sip hangup disposition"> sip_hangup_disposition</a> </span></h3>
<p>This variable contains the value of who sent the SIP BYE message. Some examples from XML CDRs:
</p>
<pre>&lt;sip_hangup_disposition&gt;send_bye&lt;/sip_hangup_disposition&gt;
&lt;sip_hangup_disposition&gt;recv_bye&lt;/sip_hangup_disposition&gt;
&lt;sip_hangup_disposition&gt;send_refuse&lt;/sip_hangup_disposition&gt;
&lt;sip_hangup_disposition&gt;send_cancel&lt;/sip_hangup_disposition&gt;
</pre>
<p>Interpretation of these values differs on incoming and outgoing calls since FreeSWITCH is at different ends of the session.
</p>
<table>
<tr>
<th> Value
</th><th> Incoming
</th><th> Outgoing
</th></tr>
<tr>
<td>send_bye
</td><td> FS sent BYE to the caller (we hung up)
</td><td> FS sent BYE to the endpoint (we hung up)
</td></tr>
<tr>
<td>recv_bye
</td><td> FS received BYE from the caller (they hung up)
</td><td> FS received BYE from the endpoint (they hung up)
</td></tr>
<tr>
<td>send_refuse
</td><td> FS rejected the call (e.g. 4xx or 5xx)
</td><td> Endpoint rejected the call (e.g. 4xx or 5xx)
</td></tr>
<tr>
<td>send_cancel
</td><td> <i>n/a</i>
</td><td> FS aborted the call (we sent CANCEL)
</td></tr></table>
<p><b>Usage:</b>
</p>
<pre>Look in CDR for the value; only valid after call has ended.
</pre>
<p><br />
</p>
<a name="proto_specific_hangup_cause" id="proto_specific_hangup_cause"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_proto_specific_hangup_cause" title="Variable proto specific hangup cause"> proto_specific_hangup_cause</a> </span></h3>
<p>This variable will cause FreeSWITCH to force the SIP response code to a specific setting when hanging up a call. The example below is one where all possible extensions have been tested and failed and you want FreeSWITCH to generate and respond with a specific code. (This is not a passthrough example).
</p><p>By the way, you'll be unable to rewrite the hangup cause for a bridge that gets a 180 or 183 packet from the gateway before getting a 4xx, 5xx or 6xx packet (because those bridges don't 'fail').  This happens with SIP providers that give a 183 Session Progress before a 404 Not Found if the PSTN number dialled doesn't exist.
</p><p><b>Usage:</b>
</p>
<pre>&lt;extension name="nothing_left" continue="true"&gt;
  &lt;condition break="always"&gt;
    &lt;action application="set" data="proto_specific_hangup_cause=sip:503"/&gt;
    &lt;action application="hangup"/&gt;
  &lt;/condition&gt;
&lt;/extension&gt;
</pre>
<p><b>Example:</b><br />
SIP Response Map
</p>
<pre>   &lt;extension name="from_gw_to_internal"&gt;
     &lt;condition field="destination_number" expression="^(.*)$"&gt;
       &lt;action application="set" data="hangup_after_bridge=true"/&gt;
       &lt;action application="set" data="continue_on_fail=19"/&gt;
       &lt;action application="bridge" data="{sip_cid_type=none}sofia/gateway/gw/$1"/&gt;
       &lt;action application="transfer" data="480to503"/&gt;
     &lt;/condition&gt;
   &lt;/extension&gt;
</pre>
<pre>   &lt;extension name="480to503"&gt;
     &lt;condition field="${proto_specific_hangup_cause}" expression="&lt;a href="sip:480"&gt;sip:480"&gt;
       &lt;action application="set" data="sip_ignore_remote_cause=true"/&gt;
       &lt;action application="respond" data="503"/&gt;
       &lt;action application="hangup" data="NORMAL_CIRCUIT_CONGESTION"/&gt;
     &lt;/condition&gt;
   &lt;/extension&gt;
</pre>
<p><br />
</p>
<a name="DTMF_Related" id="DTMF_Related"></a><h2> <span class="mw-headline"> DTMF Related </span></h2>
<a name="pass_rfc2833" id="pass_rfc2833"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_pass_rfc2833" title="Variable pass rfc2833"> pass_rfc2833</a> </span></h3>
<p>If set it passes <a href="http://tools.ietf.org/html/rfc2833" class="external" title="http://tools.ietf.org/html/rfc2833">RFC 2833</a> DTMF's from one side of a bridge to the other untouched. 
If unset, it decodes and re-encodes them before passing them on.
</p><p>Note: this has no effect when bypass_media or proxy_media is set.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="pass_rfc2833=true"/&gt;
</pre>
<p><br />
</p>
<a name="dtmf_type" id="dtmf_type"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_dtmf_type" title="Variable dtmf type"> dtmf_type</a> </span></h3>
<p>For inband DTMF, <a href="/wiki/Misc._Dialplan_Tools_start_dtmf" title="Misc. Dialplan Tools start dtmf">Misc. Dialplan Tools start_dtmf</a> must be used in the dialplan.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="dtmf_type=info"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="dtmf_type=rfc2833"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="dtmf_type=none"/&gt;
</pre>
<p><br />
</p>
<a name="Media_Handling" id="Media_Handling"></a><h2> <span class="mw-headline"> Media Handling </span></h2>
<a name="monitor_early_media_fail" id="monitor_early_media_fail"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_monitor_early_media_fail" title="Variable monitor early media fail"> monitor_early_media_fail</a> </span></h3>
<p>Monitors early media for failure conditions, such as a busy signal. This allows faster processing of failed calls when ignoring early media.
</p><p>The sytax is a series of&nbsp;! delimited early media conditions in the following format:
</p><p>condition_name:number_of_hits:tone_detect_frequencies
</p>
<table border="1" width="80%">

<tr>
<td> condition_name
</td><td>
<p>user defined name for the error condition
</p>
</td></tr>
<tr>
<td> number_of_hits
</td><td>
<p>the number of times the tone must be heard before considering it a fail
</p>
</td></tr>
<tr>
<td> tone_detect_frequencies
</td><td>
<p>the frequencies to listen for (delimited by + instead of ,). See <a href="/wiki/Misc._Dialplan_Tools_tone_detect" title="Misc. Dialplan Tools tone detect"> tone_detect</a>
</p>
</td></tr></table>
<p>NOTE: this variable only works when ignore_early_media is set to true.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="{ignore_early_media=true,monitor_early_media_fail=user_busy:2:480+620!destination_out_of_order:2:1776.7}sofia/dial/string"/&gt;
</pre>
<p><br />
</p>
<a name="monitor_early_media_ring" id="monitor_early_media_ring"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_monitor_early_media_ring" title="Variable monitor early media ring"> monitor_early_media_ring</a> </span></h3>
<p>Monitors early media for a user specific ring tone. Each time the tone is heard, the switch will increment an internal counter for that leg. If the counter reaches<a href="/wiki/Variable_monitor_early_media_ring_total" title="Variable monitor early media ring total"> monitor_early_media_ring_total</a> (or this variable has not been set) then call will fail [if it is not answered].
</p><p>The syntax is a series of&nbsp;! delimited early media conditions in the following format:
</p><p>condition_name:number_of_hits:tone_detect_frequencies
</p>
<table border="1" width="80%">

<tr>
<td> condition_name
</td><td>
<p>user defined name for the error condition
</p>
</td></tr>
<tr>
<td> number_of_hits
</td><td>
<p>the number of times the tone must be heard before considering it a fail
</p>
</td></tr>
<tr>
<td> tone_detect_frequencies
</td><td>
<p>the frequencies to listen for (delimited by + instead of ,). See <a href="/wiki/Misc._Dialplan_Tools_tone_detect" title="Misc. Dialplan Tools tone detect"> tone_detect</a>
</p>
</td></tr></table>
<p>NOTE: this variable only works when ignore_early_media is set to true.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="{ignore_early_media=true,monitor_early_media_ring_total=3,monitor_early_media_ring=us_ring:1:440.0+480.0!uk_ring:2:400+450}sofia/dial/string"/&gt;
</pre>
<p>Monitors early media for a user specific ring tone. Each time the tone is heard, the switch will increment an internal counter for that leg. Once the counter reaches<a href="/wiki/Variable_monitor_early_media_ring_total" title="Variable monitor early media ring total"> monitor_early_media_ring_total</a> (or this variable has not been set) then the early media will be sent.
</p><p>The syntax is a series of&nbsp;! delimited early media conditions in the following format:
</p><p>condition_name:number_of_hits:tone_detect_frequencies
</p>
<table border="1" width="80%">

<tr>
<td> condition_name
</td><td>
<p>Optional? user defined name for the error condition
</p>
</td></tr>
<tr>
<td> number_of_hits
</td><td>
<p>the number frequencies for the tone detector to find before considering it a hit. 1:400.0+480.0 means the ring count is incremented if 400hz OR 480hz is detected. 2:400.0+480.0 means the ring count is incremented if 400 hz AND 40 hz are detected.
</p>
</td></tr>
<tr>
<td> tone_detect_frequencies
</td><td>
<p>the frequencies to listen for (delimited by + instead of ,). Examples are 400.0+480.0 [for a US Ring] See <a href="/wiki/Misc._Dialplan_Tools_tone_detect" title="Misc. Dialplan Tools tone detect"> tone_detect</a>
</p>
</td></tr></table>
<p>NOTE: this variable only works when ignore_early_media is not present.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="{monitor_early_media_ring_total=3,monitor_early_media_ring=usring:1:440.0+480.0!ukring:2:400+450}sofia/gateway/yourgateway/1239@conference.freeswitch.org"/&gt;
</pre>
<p><br />
</p>
<a name="Timeout_Related" id="Timeout_Related"></a><h2> <span class="mw-headline"> Timeout Related </span></h2>
<a name="call_timeout" id="call_timeout"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_call_timeout" title="Variable call timeout"> call_timeout</a> </span></h3>
<p>Controls how long (in seconds) to ring the B leg of a call when using the bridge application. The timeout is set on the A leg, and applies to any bridges that happen in the channel.
</p><p>If you need to set a timeout on a call that has no A leg, use <a href="/wiki/Variable_originate_timeout" title="Variable originate timeout"> originate_timeout</a>
</p><p>If you need to set the timeout on a per leg basis (i.e., a different timeout for each destination), use the <a href="/wiki/Variable_leg_timeout" title="Variable leg timeout"> leg_timeout</a> variable.<br />
</p><p>Default Value: 60
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="call_timeout=20"/&gt;
</pre>
<p><br />
</p>
<a name="leg_timeout" id="leg_timeout"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_leg_timeout" title="Variable leg timeout"> leg_timeout</a> </span></h3>
<p>Timeout for each leg in an originate dialstring. Can be used in per-leg [], but not in global {} for the dialstring.
</p><p>You can also use leg_progress_timeout to specify the maximum time we will wait before we get media (whether its early media, ringing or answer), allowing you to avoid going to voicemail for a particular line.
</p><p>If you are using group confirm then you can cancel the timeout by using the <a href="/wiki/Channel_Variables#group_confirm_cancel_timeout" title="Channel Variables">group_confirm_cancel_timeout</a> channel variable.  If leg_delay_start is also used, leg_timeout will not start the timeout counter until after the extension starts to be bridged to.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="[leg_timeout=15]user/hastoanswerquickly/some.domain.com,[leg_timeout=60]user/hasaminutetoanswer@some.domain.com"/&gt;
</pre>
<p><br />
</p>
<a name="originate_continue_on_timeout" id="originate_continue_on_timeout"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_originate_continue_on_timeout" title="Variable originate continue on timeout"> originate_continue_on_timeout</a> </span></h3>
<p>Controls wether or not a bridge should continue after timing out. Default value is false. This variable resets the timeout after each | default is to die on first timeout
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="originate_continue_on_timeout=true"/&gt;
</pre>
<p><br />
</p>
<a name="park_timeout" id="park_timeout"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_park_timeout" title="Variable park timeout"> park_timeout</a> </span></h3>
<p>When set, a parked call will disconnect after the timeout has occurred. Timeout is specified in seconds. If no park_timeout value is set then the parked call will be held indefinitely or until it is removed with a uuid_transfer.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="park_timeout=30"/&gt;
&lt;action application="park"/&gt;
</pre>
<p>You can also specify which hangup_cause you need when the channel is hangup by park_timeout.
</p><p><b>Usage:</b>
&lt;action application="set" data="park_timeout=30:MEDIA_TIMEOUT"/&gt;
</p><p><br />
</p>
<a name="Music_On_Hold_Related" id="Music_On_Hold_Related"></a><h2> <span class="mw-headline"> Music On Hold Related </span></h2>
<a name="hold_music" id="hold_music"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_hold_music" title="Variable hold music"> hold_music</a> </span></h3>
<p>Per-channel hold music. Supports all audio formats and audio streams.
The hold_music variable can also be set globally at vars.xml.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="hold_music=/sounds/holdmusic.wav" /&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="hold_music=silence" /&gt;
</pre>
<p><br />
For multi-tenant environment, if you want to have a separate MOH for the phone with hold button (like Polycom) that utilizes RE-INVITE with no media ip addr (0.0.0.0) for hold, you can override the hold-music values in the sip profile parameter similar to the following example:
</p>
<pre>&lt;action application="bridge_export" data="hold_music=$${sounds_dir}/music/company-a.mp3"/&gt;
</pre>
<p><br />
</p>
<a name="temp_hold_music" id="temp_hold_music"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_temp_hold_music" title="Variable temp hold music"> temp_hold_music</a> </span></h3>
<p>This variable specifies a hold music value that gets played to a caller only until they get transferred. After the transfer, the hold_music variable will apply.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="temp_hold_music=local_stream://alternate_moh"/&gt;
</pre>
<p><br />
</p>
<a name="Locale_Related" id="Locale_Related"></a><h2> <span class="mw-headline"> Locale Related </span></h2>
<a name="default_language" id="default_language"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_default_language" title="Variable default language"> default_language</a> </span></h3>
<p>Controls the default language the Say Phrase engine will use when no language is explicitly specified in the API call. This permits you to easily support multiple languages by only changing a single variable at call time.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="default_language=fr"/&gt;
</pre>
<p><br />
</p>
<a name="timezone" id="timezone"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_timezone" title="Variable timezone"> timezone</a> </span></h3>
<p>Sets the timezone for this particular call. Can be used, e.g., to set the timezone for a caller who is checking his/her voicemail. The value is expressed in Linux timezone format (ex. America/New_York -- see /usr/share/zoneinfo/zone.tab for the standard list of Linux timezones).
</p><p>Note that this channel variable is only respected by the phrase layer -- ie, if you're using the 'say' application to announce times, this will work fine.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="timezone=GMT0"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="timezone=America/New_York"/&gt;
</pre>
<p><br />
</p>
<a name="Bridge_Related" id="Bridge_Related"></a><h2> <span class="mw-headline"> Bridge Related </span></h2>
<a name="api_after_bridge" id="api_after_bridge"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_api_after_bridge" title="Variable api after bridge"> api_after_bridge</a> </span></h3>
<p>Execute an API command after bridge.
</p><p><br />
<b>Usage:</b>
</p>
<pre>Paging to PA System via Portaudio (w/ chime before and after announcement) <a href="http://wiki.freeswitch.org/wiki/Mod_portaudio#PA_System_w.2F_Chime" class="external autonumber" title="http://wiki.freeswitch.org/wiki/Mod_portaudio#PA_System_w.2F_Chime" rel="nofollow">[1]</a>
</pre>
<p><br />
</p>
<a name="auto_hunt" id="auto_hunt"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_auto_hunt" title="Variable auto hunt"> auto_hunt</a> </span></h3>
<p>Setting auto_hunt to "true" will alter the normal sequential processing of dialplan extensions. auto_hunt will cause the dialplan to 'jump' to a specific <b>extension name</b>, not processing any other extension. The destination_number and extension name must be the same in order for this to work. The condition must still match, but the extension name is the operative element. 
</p><p>In the example below, there is no way to reach extension 333 without auto_hunt.
</p><p><b>Usage:</b>
In vars.xml:
</p>
<pre>&lt;X-PRE-PROCESS cmd="set" data="auto_hunt=true"/&gt;
</pre>
<p><b>Example:</b>
</p>
<pre>&lt;extension name="do_xfer"&gt;
  &lt;condition field="destination_number" expression="^.*$"&gt;
    &lt;action application="set" data="auto_hunt=true"/&gt;
    &lt;action application="transfer" data="333"/&gt;
  &lt;/condition&gt;
&lt;/extension&gt;

&lt;extension name="333"&gt;
  &lt;condition field="destination_number" expression="^333$"&gt;
    &lt;action application="info"/&gt;
  &lt;/condition&gt;
&lt;/extension&gt;
</pre>
<p><br />
</p>
<a name="bridge_early_media" id="bridge_early_media"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_bridge_early_media" title="Variable bridge early media"> bridge_early_media</a> </span></h3>
<p>By default this is false.  Set to true, this makes the bridge use the live audio from the b-leg as ringback to the a-leg. Setting bridge_early_media=true means the early media will be buffered.
</p><p>Consider setting this to true if you are using a loopback channel to execute a bridge to an endpoint which sends back early media and the
received early media's audio is degraded. The buffering resulting from setting bridge_early_media=true brings with it a higher resource cost
(than bridge_early_media=false), but may improve the sound quality of the early media.
</p><p><b>Usage:</b>
Set bridge_early_media before the bridge, or in the dial string for the bridge.
</p><p><br />
</p>
<a name="bridge_terminate_key" id="bridge_terminate_key"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_bridge_terminate_key" title="Variable bridge terminate key"> bridge_terminate_key</a> </span></h3>
<p>Allows you to bind a key and the bridge will terminate if the dtmf matches
</p><p><b>Usage:</b>
you can set bridge_terminate_key on either or both legs which will end the bridge, if it hangs up or not is decided by hangup_after_bridge=false or what is next in your dp
</p><p><br />
</p>
<a name="continue_on_fail" id="continue_on_fail"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_continue_on_fail" title="Variable continue on fail"> continue_on_fail</a> </span></h3>
<p>Controls what happens when the called party can not be reached (busy/offline). If "true" the dialplan continues to be processed. If "false" the dialplan will stop processing.
Can contain the return messages that will continue on fail also.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="continue_on_fail=true"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="continue_on_fail=NORMAL_TEMPORARY_FAILURE,USER_BUSY,NO_ANSWER,NO_ROUTE_DESTINATION"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="continue_on_fail=3,17,18,27"/&gt;
</pre>
<p><br />
</p>
<a name="transfer_on_fail" id="transfer_on_fail"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_transfer_on_fail" title="Variable transfer on fail"> transfer_on_fail</a> </span></h3>
<p>Allows you to tranfer call flow when a called party can not be reached for specific reasons ( unallocated_number, etc )
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="transfer_on_fail= UNALLOCATED_NUMBER"/&gt;
</pre>
<p>in this example, if you were to attempt a bridge that resulted in "UNALLOCATED_NUMBER" , the call flow would be "transferred" to the "UNALLOCATED_NUMBER" destination in your current dialplan ( probably default xml dialplan )
</p><p>or,
</p>
<pre>&lt;action application="set" data="transfer_on_fail=&lt;hangupcauses&gt; &lt;destination&gt; &lt;dialplan&gt; &lt;context&gt;"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="transfer_on_fail=1"/&gt;
</pre>
<p><br />
</p>
<a name="enable_file_write_buffering" id="enable_file_write_buffering"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_enable_file_write_buffering" title="Variable enable file write buffering"> enable_file_write_buffering</a> </span></h3>
<p>Enable file buffering when recording a file, defaults to true if not set.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="enable_file_write_buffering=true"/&gt; 
</pre>
<p><br />
</p>
<a name="failure_causes" id="failure_causes"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_failure_causes" title="Variable failure causes"> failure_causes</a></span></h3>
<p>Controls which failure causes will be considered as a failure to the bridge(s). This will change the values for which <a href="/wiki/Variable_continue_on_fail" title="Variable continue on fail">continue_on_fail</a> will fail by default unless <a href="/wiki/Variable_continue_on_fail" title="Variable continue on fail">continue_on_fail</a> is set to true.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="failure_causes=USER_BUSY,NO_ANSWER"/&gt;
</pre>
<p><br />
</p>
<a name="force_transfer_context" id="force_transfer_context"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_force_transfer_context" title="Variable force transfer context"> force_transfer_context</a> </span></h3>
<p>When handling transfer/REFER FreeSWITCH normally inherits the context from the original channel.  This variable forces the context in which to handle the transfer/REFER
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="{force_transfer_context=some_context}sofia/gateway/gw_name/12345"/&gt;
</pre>
<p><br />
</p>
<a name="force_transfer_dialplan" id="force_transfer_dialplan"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_force_transfer_dialplan" title="Variable force transfer dialplan"> force_transfer_dialplan</a> </span></h3>
<p>When handling transfer/REFER FreeSWITCH normally inherits the diaplan from the original channel.  This variable forces the dialplan in which to handle the transfer/REFER
</p><p><b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="hangup_after_bridge" id="hangup_after_bridge"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_hangup_after_bridge" title="Variable hangup after bridge"> hangup_after_bridge</a> </span></h3>
<p>Controls what happens to a calling (A) party when in a bridge state and the called (B) party hangs up. If "true" the dialplan will stop processing and the A leg will be terminated when the B leg terminates. If "false" (default) the dialplan continues to be processed after the B leg terminates. This is checked after <a href="/wiki/Variable_park_after_bridge" title="Variable park after bridge">park_after_bridge</a> and <a href="/wiki/Variable_transfer_after_bridge" title="Variable transfer after bridge">transfer_after_bridge</a>.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="hangup_after_bridge=true"/&gt;
</pre>
<p><br />
</p>
<a name="hold_hangup_xfer_exten" id="hold_hangup_xfer_exten"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_hold_hangup_xfer_exten" title="Variable hold hangup xfer exten"> hold_hangup_xfer_exten</a> </span></h3>
<p>Controls what happens to a calling (A) party when in a bridge state and the bridge ends while the called (B) party is on hold.  If not set on leg B (ie. the default), then A leg is hung up.  If it is set on leg B, then leg A is transferred to the given extension, as per <a href="/wiki/Variable_transfer_after_bridge" title="Variable transfer after bridge">transfer_after_bridge</a>.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="hold_hangup_xfer_exten=1000:XML:default"/&gt;
</pre>
<p><br />
</p>
<a name="last_bridge_to" id="last_bridge_to"></a><h3> <span class="mw-headline"> <a href="/index.php?title=Variable_last_bridge_to&amp;action=edit&amp;redlink=1" class="new" title="Variable last bridge to (page does not exist)"> last_bridge_to</a> </span></h3>
<p><a href="/index.php?title=Variable_last_bridge_to&amp;action=edit&amp;redlink=1" class="new" title="Variable last bridge to (page does not exist)">Variable last bridge to</a>
</p>
<a name="loopback_bowout_on_execute" id="loopback_bowout_on_execute"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_loopback_bowout_on_execute" title="Variable loopback bowout on execute"> loopback_bowout_on_execute</a> </span></h3>
<p>Set to true to have one-legged loopback channels "bow out" of the call.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="loopback_bowout_on_execute=true"/&gt;
</pre>
<p><br />
</p>
<a name="outbound_redirect_fatal" id="outbound_redirect_fatal"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_outbound_redirect_fatal" title="Variable outbound redirect fatal"> outbound_redirect_fatal</a> </span></h3>
<p>When doing a simultaneous call to multiple endpoints, a 302 redirect can cause all the endpoints to stop ringing and the call will follow the redirect. When this channel variable is set it causes an endpoint that sends back a 302 redirect to be removed from the call list and the other endpoints continue to ring.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="outbound_redirect_fatal=true"/&gt; 
</pre>
<p><br />
</p>
<a name="originate_timeout" id="originate_timeout"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_originate_timeout" title="Variable originate timeout"> originate_timeout</a> </span></h3>
<p>Determines how long a bridge or originate action action will stay in the "originate" state. In effect, it is a way to control the timeout for a bridge/originate consisting of multiple endpoints. Default value is 60.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="{originate_timeout=10}[leg_timeout=5]sofia/default/foo1@bar1|[leg_timeout=5]sofia/default/foo2@bar2"/&gt;
</pre>
<p><br />
<b>Example</b>
</p>
<pre>
&lt;action application=&quot;bridge&quot; data=&quot;{originate_timeout=24}${group_call(sales@$${domain})}&quot;/&gt;
</pre>
<a name="park_after_bridge" id="park_after_bridge"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_park_after_bridge" title="Variable park after bridge"> park_after_bridge</a> </span></h3>
<p>If set to true, it will <a href="/wiki/Misc._Dialplan_Tools_park" title="Misc. Dialplan Tools park">park</a> the call after <a href="/wiki/Misc._Dialplan_Tools_bridge" title="Misc. Dialplan Tools bridge">bridge</a> returns. This is checked before <a href="/wiki/Variable_transfer_after_bridge" title="Variable transfer after bridge">transfer_after_bridge</a> and <a href="/wiki/Variable_hangup_after_bridge" title="Variable hangup after bridge">hangup_after_bridge</a>.
</p><p>Default: false
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="park_after_bridge=true"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="signal_bond" id="signal_bond"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_signal_bond" title="Variable signal bond"> signal_bond</a> </span></h3>
<p>UUID of the channel this channel is bridged/bonded to. Not present on a one-legged call.
</p><p><b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><b>See also:</b>
</p><p><br />
</p><p><br />
</p>
<a name="sip_jitter_buffer_during_bridge" id="sip_jitter_buffer_during_bridge"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_jitter_buffer_during_bridge" title="Variable sip jitter buffer during bridge"> sip_jitter_buffer_during_bridge</a> </span></h3>
<p>Enables/disables the jitter buffer during bridge.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="sip_jitter_buffer_during_bridge=true"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="sip_jitter_buffer_during_bridge=false"/&gt;
</pre>
<p><br />
</p>
<a name="uuid_bridge_continue_on_cancel" id="uuid_bridge_continue_on_cancel"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_uuid_bridge_continue_on_cancel" title="Variable uuid bridge continue on cancel"> uuid_bridge_continue_on_cancel</a> </span></h3>
<p>When set to <i>true</i> causes the system to move on in the dialplan if it hits a bad b-leg. Default is <i>false</i> because this behavior is probably not recommended.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="uuid_bridge_continue_on_cancel=true"/&gt;
</pre>
<p><br />
</p>
<a name="Conference_Related" id="Conference_Related"></a><h2> <span class="mw-headline"> Conference Related </span></h2>
<a name="conference_auto_outcall_announce" id="conference_auto_outcall_announce"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_auto_outcall_announce" title="Variable conference auto outcall announce"> conference_auto_outcall_announce</a> </span></h3>
<p>Description needed! Please contribute one.
</p><p><b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="conference_auto_outcall_caller_id_name" id="conference_auto_outcall_caller_id_name"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_auto_outcall_caller_id_name" title="Variable conference auto outcall caller id name"> conference_auto_outcall_caller_id_name</a> </span></h3>
<p>Description needed! Please contribute one.
</p><p><b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="conference_auto_outcall_caller_id_number" id="conference_auto_outcall_caller_id_number"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_auto_outcall_caller_id_number" title="Variable conference auto outcall caller id number"> conference_auto_outcall_caller_id_number</a> </span></h3>
<p>Description needed! Please contribute one.
</p><p><b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="conference_auto_outcall_flags" id="conference_auto_outcall_flags"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_auto_outcall_flags" title="Variable conference auto outcall flags"> conference_auto_outcall_flags</a> </span></h3>
<p>Description needed! Please contribute one.
</p><p><b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="conference_auto_outcall_prefix" id="conference_auto_outcall_prefix"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_auto_outcall_prefix" title="Variable conference auto outcall prefix"> conference_auto_outcall_prefix</a> </span></h3>
<p>The value of conference_auto_outcall_prefix is prepended to each of conference_set_auto_outcall values, of which there can be more than one.
</p><p><b>Usage:</b>
</p>
<pre>  &lt;extension name="mad_boss_intercom"&gt;
    &lt;condition field="destination_number" expression="^0911$"&gt;
      &lt;action application="set" data="conference_auto_outcall_caller_id_name=Mad Boss1"/&gt;
      &lt;action application="set" data="conference_auto_outcall_caller_id_number=0911"/&gt;
      &lt;action application="set" data="conference_auto_outcall_timeout=60"/&gt;
      &lt;action application="set" data="conference_auto_outcall_flags=mute"/&gt;
      &lt;action application="set" data="conference_auto_outcall_prefix={sip_auto_answer=true,execute_on_answer='bind_meta_app 2 a s1 transfer::intercept:${uuid} inline'}"/&gt;
      &lt;action application="set" data="sip_exclude_contact=${network_addr}"/&gt;
      &lt;action application="conference_set_auto_outcall" data="${group_call(sales)}"/&gt;
      &lt;action application="conference" data="madboss_intercom1@default+flags{endconf|deaf}"/&gt;
    &lt;/condition&gt;
  &lt;/extension&gt;
</pre>
<p><br />
</p>
<a name="conference_auto_outcall_timeout" id="conference_auto_outcall_timeout"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_auto_outcall_timeout" title="Variable conference auto outcall timeout"> conference_auto_outcall_timeout</a> </span></h3>
<p>Description needed! Please contribute one.
</p><p><b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="conference_auto_outcall_maxwait" id="conference_auto_outcall_maxwait"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_auto_outcall_maxwait" title="Variable conference auto outcall maxwait"> conference_auto_outcall_maxwait</a> </span></h3>
<p>Description needed! Please contribute one.
</p><p><b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="conference_controls" id="conference_controls"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_controls" title="Variable conference controls"> conference_controls</a> </span></h3>
<p>Set this variable to specify which conference controls profile to use when transferring a caller into a conference. This allows you, for example, to have a profile for the conference moderator and another profile for regular conference members. The profile for the moderator could include the ability to mute/kick people, etc.
</p><p>NOTE: You must create the conference controls profile. Also, if this is not set then the <i>default</i> conference profile is used for the conference member.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="conference_controls=moderator"/&gt;
</pre>
<p><br />
</p>
<a name="conference_enter_sound" id="conference_enter_sound"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_enter_sound" title="Variable conference enter sound"> conference_enter_sound</a> </span></h3>
<p>When set, this channel variable will override the enter-sound param on conference profile for any conferences into which the call leg is transferred.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="conference_enter_sound=silence_stream://10"/&gt;
</pre>
<p><br />
</p>
<a name="conference_last_matching_digits" id="conference_last_matching_digits"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_last_matching_digits" title="Variable conference last matching digits"> conference_last_matching_digits</a> </span></h3>
<p>Contains the last matching digits that the user on this channel sent into the conference.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="log" data="INFO Last digits sent by this user: ${conference_last_matching_digits}"/&gt;
</pre>
<p><br />
</p>
<a name="last_transferred_conference" id="last_transferred_conference"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_last_transferred_conference" title="Variable last transferred conference"> last_transferred_conference</a> </span></h3>
<p>Contains the name of the last conference that this channel was connected to. 
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="log" data="INFO Last conference this person visited was [${last_transferred_conference}]"/&gt;
</pre>
<p><br />
</p>
<a name="conference_member_id" id="conference_member_id"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_member_id" title="Variable conference member id"> conference_member_id</a> </span></h3>
<p>Contains the conference_member_id value for any conference to which the channel may be connected.
</p><p><br />
<b>Usage:</b>
</p>
<pre>N/A
</pre>
<p><br />
</p>
<a name="conference_uuid" id="conference_uuid"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_conference_uuid" title="Variable conference uuid"> conference_uuid</a> </span></h3>
<p>Every instance of a conference has its own UUID. This channel variable stores the conference UUID for the most recent conference in which the channel was a member. It is set as soon as the channel enters the conference, and will show up in XML CDRs and uuid_dump calls, as well as any events that show channel variables.
</p><p><b>Usage:</b>
</p>
<pre>N/A
</pre>
<p><br />
</p>
<a name="hangup_after_conference" id="hangup_after_conference"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_hangup_after_conference" title="Variable hangup after conference"> hangup_after_conference</a> </span></h3>
<p>Controls what happens to a calling (A) party when in a conference and the conference ends (e.g. endconf flag set and moderator leaves). If "true" (default) the dialplan will stop processing and the A leg will be terminated. If "false" the dialplan continues to be processed after the end of conference.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="hangup_after_conference=false"/&gt;
</pre>
<p><br />
</p>
<a name="Code_Execution_Related" id="Code_Execution_Related"></a><h2> <span class="mw-headline"> Code Execution Related </span></h2>
<a name="api_hangup_hook" id="api_hangup_hook"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_api_hangup_hook" title="Variable api hangup hook"> api_hangup_hook</a> </span></h3>
<p>Execute an API command on hangup.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="api_hangup_hook=jsrun cleanup.js ${uuid}"/&gt; 
</pre>
<p><b>See also:</b><br />
</p>
<ul><li> session_in_hangup_hook
</li><li> api_reporting_hook - like api_hangup_hook but after reporting state (both honor session_in_hangup_hook)
</li></ul>
<p><br />
</p>
<a name="bridge_pre_execute_aleg_app" id="bridge_pre_execute_aleg_app"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_bridge_pre_execute_aleg_app" title="Variable bridge pre execute aleg app"> bridge_pre_execute_aleg_app</a> </span></h3>
<p>Command or api to be executed on the A leg before bridging the two channels.
</p><p>Note: this is executed AFTER the call is setup but BEFORE the media (audio) is bridged.
</p><p><br />
<b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="bridge_pre_execute_aleg_data" id="bridge_pre_execute_aleg_data"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_bridge_pre_execute_aleg_data" title="Variable bridge pre execute aleg data"> bridge_pre_execute_aleg_data</a> </span></h3>
<p>Arguments to be used with bridge_pre_execute_aleg_app.
</p><p><br />
<b>Usage:</b>
</p>
<pre>Example needed! Please contribute one.
</pre>
<p><br />
</p>
<a name="bridge_pre_execute_bleg_app" id="bridge_pre_execute_bleg_app"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_bridge_pre_execute_bleg_app" title="Variable bridge pre execute bleg app"> bridge_pre_execute_bleg_app</a> </span></h3>
<p>Command or api to be executed on the B leg before bridging the two channels. Useful when originating a call from the event socket, CLI or XML-RPC.
</p><p>It could for instance be used to do a HTTP GET with a script or mod_http to the IP address of a Snom phone to increase the ringer volume if you need to do a wakeup call.
</p><p>Can also be used to bind a dtmf to an app on the b leg of a call so that it can survive a transfer.
</p><p>Note: this is executed AFTER the call is setup but BEFORE the media (audio) is bridged.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="bridge_pre_execute_bleg_app=bind_meta_app"/&gt;
&lt;action application="set" data="bridge_pre_execute_bleg_data=1 a s att_xfer::sofia/profile/destination"/&gt;
</pre>
<p><br />
</p>
<a name="bridge_pre_execute_bleg_data" id="bridge_pre_execute_bleg_data"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_bridge_pre_execute_bleg_data" title="Variable bridge pre execute bleg data"> bridge_pre_execute_bleg_data</a> </span></h3>
<p>Arguments to be used with bridge_pre_execute_bleg_app
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="bridge_pre_execute_bleg_app=bind_meta_app"/&gt;
&lt;action application="set" data="bridge_pre_execute_bleg_data=1 a s att_xfer::sofia/profile/destination"/&gt;
</pre>
<p><br />
</p>
<a name="exec_after_bridge_app" id="exec_after_bridge_app"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_exec_after_bridge_app" title="Variable exec after bridge app"> exec_after_bridge_app</a> </span></h3>
<p>Execute an application command after the bridge has been terminated. To be used with <a href="/wiki/Variable_exec_after_bridge_arg" title="Variable exec after bridge arg"> exec_after_bridge_arg</a>. By contrast, to execute when the bridge has been established use <a href="/wiki/Variable_execute_on_answer" title="Variable execute on answer"> execute_on_answer</a>
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="exec_after_bridge_app=transfer"/&gt;
&lt;action application="set" data="exec_after_bridge_arg=2102"/&gt;
</pre>
<p><br />
</p>
<a name="exec_after_bridge_arg" id="exec_after_bridge_arg"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_exec_after_bridge_arg" title="Variable exec after bridge arg"> exec_after_bridge_arg</a> </span></h3>
<p>Argument passed to <a href="/wiki/Variable_exec_after_bridge_app" title="Variable exec after bridge app"> exec_after_bridge_app</a>.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="exec_after_bridge_app=transfer"/&gt;
&lt;action application="set" data="exec_after_bridge_arg=2102"/&gt;
</pre>
<p><br />
</p>
<a name="The_execute_on_family" id="The_execute_on_family"></a><h3> <span class="mw-headline"> The execute_on family </span></h3>
<p>The execute_on_xx variables will execute dialplan applications on various conditions. As of April 1, 2011 these variables support a new syntax that allows multiple applications for a single condition. Example:
</p>
<pre>&lt;action application="set" data="execute_on_answer_1=app1 arg"/&gt;
&lt;action application="set" data="execute_on_answer_2=app2 arg"/&gt;
&lt;action application="set" data="execute_on_answer_3=app3 arg"/&gt;
</pre>
<p>Note: please be careful not to abuse this feature! There are cases where you could end up blocking the session thread and bad things could happen. If you find that you are trying to do lots and lots of things with these then consider using an execute_extension app and doing your stuff in a dialplan extension.
</p>
<a name="execute_on_answer" id="execute_on_answer"></a><h4> <span class="mw-headline"> <a href="/wiki/Variable_execute_on_answer" title="Variable execute on answer"> execute_on_answer</a> </span></h4>
<p>Execute an application (not an api) when the called party answers. To set an api, use <a href="/wiki/Variable_api_on_answer" title="Variable api on answer"> api_on_answer</a>. execute_on_answer will also allow for more control when dealing with no answer conditions in cases where you cannot ignore early media.
</p><p>The command is executed only on channels that are not already answered. Just use export or export with nolocal: prefix to make sure it is executed when b-leg answers.
</p><p>In the second usage example below, we have originated an outbound call to a local extension, where we will wait 30 seconds while manually ignoring media. In this case we use 'set' and not 'export'.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="export" data="nolocal:execute_on_answer=lua incrInUse.lua ${uuid}"/&gt;
</pre>
<p>or, to wait 30 seconds for an answer while 'manually' ignoring early media
</p>
<pre>originate {ignore_early_media=true}sofia/gateway/my_gateway/5551212 885551212
</pre>
<pre>&lt;extension name="exe_on_ans"&gt;
  &lt;condition field="destination_number" expression="^88(\d+)$"&gt;
    &lt;action application="set" data="execute_on_answer=transfer ANSWEREDCALL XML default"/&gt;
    &lt;action application="log" data="INFO Waiting 30 seconds for $1 to answer..."/&gt;
    &lt;action application="sleep" data="30000"/&gt;
    &lt;action application="log" data="INFO Call to $1 was not answered, taking alternative action..."/&gt;
    &lt;action application="transfer" data="UNANSWEREDCALL XML default"/&gt;
  &lt;/condition&gt;
&lt;/extension&gt;
</pre>
<p><br />
</p>
<a name="execute_on_media" id="execute_on_media"></a><h4> <span class="mw-headline"> <a href="/wiki/Variable_execute_on_media" title="Variable execute on media"> execute_on_media</a> </span></h4>
<p>Execute an application when the far end sends media, i.e. ringing or 183/SDP.
</p><p>The command is executed only on channels that are not already answered. Just use export or export with nolocal: prefix to make sure it is executed when b-leg answers.
</p><p>In the second usage example below, we have originated an outbound call to a local extension, where we will wait 30 seconds without ignoring media. In this case we use 'set' and not 'export'.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="export" data="nolocal:execute_on_media=lua incrInUse.lua ${uuid}"/&gt;
</pre>
<p>or, to wait 30 seconds for an answer without ignoring early media
</p>
<pre>originate sofia/gateway/my_gateway/5551212 885551212
</pre>
<pre>&lt;extension name="exe_on_ans"&gt;
  &lt;condition field="destination_number" expression="^88(\d+)$"&gt;
    &lt;action application="set" data="execute_on_media=transfer ANSWEREDCALL XML default"/&gt;
    &lt;action application="log" data="INFO Waiting 30 seconds for $1 to answer..."/&gt;
    &lt;action application="sleep" data="30000"/&gt;
    &lt;action application="log" data="INFO Call to $1 was not answered, taking alternative action..."/&gt;
    &lt;action application="transfer" data="UNANSWEREDCALL XML default"/&gt;
  &lt;/condition&gt;
&lt;/extension&gt;
</pre>
<p><br />
</p>
<a name="execute_on_preanswer" id="execute_on_preanswer"></a><h4> <span class="mw-headline"> <a href="/wiki/Variable_execute_on_preanswer" title="Variable execute on preanswer"> execute_on_preanswer</a> </span></h4>
<p>Execute an application (not an api) when the called party "preanswers" - that is, when some form of early media is coming or the far end sends a 180 Ringing. 
</p><p>The command is executed only on channels that are not already answered. Just use export or export with nolocal: prefix to make sure it is executed when b-leg answers.
</p><p>In the second usage example below, we have originated an outbound call to a local extension, where we will wait 30 seconds without ignoring media. In this case we use 'set' and not 'export'.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="export" data="nolocal:execute_on_preanswer=lua incrInUse.lua ${uuid}"/&gt;
</pre>
<p>or, to wait 30 seconds for an answer without ignoring early media
</p>
<pre>originate sofia/gateway/my_gw/5551212 885551212
</pre>
<pre>&lt;extension name="exe_on_preans"&gt;
  &lt;condition field="destination_number" expression="^88(\d+)$"&gt;
    &lt;action application="set" data="execute_on_preanswer=transfer ANSWEREDCALL XML default"/&gt;
    &lt;action application="log" data="INFO Waiting 30 seconds for $1 to answer..."/&gt;
    &lt;action application="sleep" data="30000"/&gt;
    &lt;action application="log" data="INFO Call to $1 was not answered, taking alternative action..."/&gt;
    &lt;action application="transfer" data="UNANSWEREDCALL XML default"/&gt;
  &lt;/condition&gt;
&lt;/extension&gt;
</pre>
<p><br />
</p>
<a name="execute_on_ring" id="execute_on_ring"></a><h4> <span class="mw-headline"> <a href="/wiki/Variable_execute_on_ring" title="Variable execute on ring"> execute_on_ring</a> </span></h4>
<p>Execute a command when the called party rings.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="nolocal:execute_on_ring=lua markring ${uuid}"/&gt;
</pre>
<p><br />
</p>
<a name="failed_xml_cdr_prefix" id="failed_xml_cdr_prefix"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_failed_xml_cdr_prefix" title="Variable failed xml cdr prefix"> failed_xml_cdr_prefix</a> </span></h3>
<p>If you set that on the A leg and any and all failed B originates generate a full XML CDR report and set it as a variable, this includes during a forked dial.
</p><p>So say you try to call sofia/profile/a@xxxxxxx,sofia/profile/b@xxxxxxx
</p><p>And it fails completely, before you make the call you set failed_xml_cdr_prefix to "bad_call"
</p><p>Then you end up with ${bad_call_1} and ${bad_call_2} which are each a full XML report including all the vars etc.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="failed_xml_cdr_prefix=failinggw" /&gt;	
</pre>
<p><br />
</p>
<a name="fail_on_single_reject" id="fail_on_single_reject"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_fail_on_single_reject" title="Variable fail on single reject"> fail_on_single_reject</a> </span></h3>
<p>This is useful when using the "," AND operator in the DATA field of a bridge. The AND operator notifies a list of destinations, bridging to the first destination that accepts the call. Typically if a destination in the list rejects the call, the bridge will continue to be attempted until either another destination accepts the call, or a timeout occurs.
</p><p>This variable allows one to terminate the bridging attempt on a single rejection of the call. This means the bridge attempt would fail, and if continue_on_fail has not been set, the call is terminated. This variable would be set within a condition before a bridge application. When used in conjunction with the continue_on_fail variable, one can perform operations such as rolling over a rejected caller to an answering machine application.
</p><p>The default setting is FALSE, meaning a single rejection will not terminate the bridging attempt.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="fail_on_single_reject=true"/&gt;
&lt;action application="bridge" data="sofia/$${profile}/$${kitchen}%$${domain},sofia/$${profile}/$${dining}%$${domain}"/&gt;
&lt;action application="javascript" data="answermachine.js"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="fail_on_single_reject=true"/&gt;
</pre>
<p><br />
</p>
<a name="intercept_unbridged_only" id="intercept_unbridged_only"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_intercept_unbridged_only" title="Variable intercept unbridged only"> intercept_unbridged_only</a> </span></h3>
<p>If set to true, the leg will only be <a href="/wiki/Misc._Dialplan_Tools_intercept" title="Misc. Dialplan Tools intercept">intercepted</a> if the channel is not <a href="/wiki/Misc._Dialplan_Tools_bridge" title="Misc. Dialplan Tools bridge">bridged</a> to anyone.
</p><p>Default: false
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="intercept_unbridged_only=true"/&gt;
&lt;action application="intercept" data="myUUID"/&gt;
</pre>
<p><br />
</p>
<a name="intercept_unanswered_only" id="intercept_unanswered_only"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_intercept_unanswered_only" title="Variable intercept unanswered only"> intercept_unanswered_only</a> </span></h3>
<p>If set to true, the leg will only be <a href="/wiki/Misc._Dialplan_Tools_intercept" title="Misc. Dialplan Tools intercept">intercepted</a> if the channel is not answered.
</p><p>Default: false
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="intercept_unanswered_only=true"/&gt;
&lt;action application="intercept" data="myUUID"/&gt;
</pre>
<p><br />
</p>
<a name="session_in_hangup_hook" id="session_in_hangup_hook"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_session_in_hangup_hook" title="Variable session in hangup hook"> session_in_hangup_hook</a> </span></h3>
<p>Allows channel variables to be accessible in the api_hangup_hook that gets executed for the channel.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="session_in_hangup_hook=true"/&gt;
</pre>
<p><br />
See <a href="/wiki/Lua#Special_Case:_env_object" title="Lua" class="mw-redirect">Lua#Special_Case:_env_object</a> for an example of how to use this.
</p><p><br />
</p>
<a name="Caller_ID_Related" id="Caller_ID_Related"></a><h2> <span class="mw-headline"> Caller ID Related </span></h2>
<a name="caller_id_name" id="caller_id_name"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_caller_id_name" title="Variable caller id name"> caller_id_name</a> </span></h3>
<p>The caller id name set by the inbound call, not a real variable. Practically it is read only.
</p><p><br />
</p>
<a name="caller_id_number" id="caller_id_number"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_caller_id_number" title="Variable caller id number"> caller_id_number</a> </span></h3>
<p>The caller id phone number set by the inbound call, not a real variable. Practically it is read only.
</p><p><br />
</p>
<a name="effective_caller_id_name" id="effective_caller_id_name"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_effective_caller_id_name" title="Variable effective caller id name"> effective_caller_id_name</a> </span></h3>
<p>Sets the effective callerid name. This is automatically exported to the B-leg; however, it is not valid in an origination string. In other words, set this before calling bridge, otherwise use <a href="/wiki/Variable_origination_caller_id_name" title="Variable origination caller id name"> origination_caller_id_name</a>
</p>
<div style="float:left; width:100%;">
<div class="floatleft"><a href="/wiki/File:Info.png" class="image" title="Informational Tip"><img alt="Informational Tip" src="/images/thumb/b/b3/Info.png/64px-Info.png" width="64" height="64" border="0" /></a></div>
<div style="float:left; width:90%;"><hr />
<p><b>For Snom 370/820 users:</b>
</p><p>If you want to display LEG A's name (if available) as soon as LEG B (here the local Snom) rings, you have to set origination_caller_id_name or effective_caller_id_name as described. Otherwise, in LEG B's display, you gonna see LEG A's number during ringing and switching to LEG A's name after picking up the call by LEG B.
</p>
<hr /></div>
</div>
<p>&nbsp;
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="effective_caller_id_name=Bob Smith"/&gt;
</pre>
<p><br />
</p>
<a name="effective_caller_id_number" id="effective_caller_id_number"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_effective_caller_id_number" title="Variable effective caller id number"> effective_caller_id_number</a> </span></h3>
<p>Sets the effective callerid number. This is automatically exported to the B-leg; however, it is not valid in an origination string. In other words, set this before calling bridge, otherwise use <a href="/wiki/Variable_origination_caller_id_number" title="Variable origination caller id number"> origination_caller_id_number</a>
</p><p><br />
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="effective_caller_id_number=9185551212"/&gt;
</pre>
<p><br />
</p>
<a name="sip_cid_type" id="sip_cid_type"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_cid_type" title="Variable sip cid type"> sip_cid_type </a></span></h3>
<ul><li> Modify how the Caller ID will show up in SIP header of the outbound leg. <br />
</li></ul>
<p><b>Examples:</b>
</p><p>Send no extra caller id info (Caller ID will be in the SIP From):
</p>
<pre>{sip_cid_type=none}sofia/default/user@example.com
</pre>
<p><i>Note: for gateways (rather than sip calls on a profile), this will not work. You need <a href="/wiki/Authentication" title="Authentication">caller-id-in-from=true</a> in the gateway settings.</i>
</p><p>Send Remote-Party-ID (default)
</p>
<pre>{sip_cid_type=rpid}sofia/default/user@example.com
</pre>
<p>Send P-Asserted-Identity
</p>
<pre>{sip_cid_type=pid}sofia/default/user@example.com
</pre>
<p><i><b>Note</b>: you must set privacy flag, otherwise will be inserted P-Preferred-Identity instead of P-Asserted-Identity</i>
</p><p><br />
Send Remote-Party-ID with chosen content
</p>
<pre>{sip_cid_type=rpid,origination_caller_id_name=test,origination_caller_id_number=1234}sofia/default/user@example.com
</pre>
<a name="effective_sip_cid_in_1xx" id="effective_sip_cid_in_1xx"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_cid_in_1xx" title="Variable sip cid in 1xx"> effective_sip_cid_in_1xx</a> </span></h3>
<p>Prevents FreeSWITCH when it receives 183 from leg-B to automatically insert RPID before sending 183 to leg-A.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="sip_cid_in_1xx=false"/&gt;
</pre>
<p><br />
</p>
<a name="Callee_ID_Related" id="Callee_ID_Related"></a><h2> <span class="mw-headline"> Callee ID Related </span></h2>
<a name="sip_callee_id_name" id="sip_callee_id_name"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_callee_id_name" title="Variable sip callee id name">sip_callee_id_name</a> </span></h3>
<p>Set on the inbound leg to control what caller ID name appears in the calling phone's display.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="sip_callee_id_name=Reginald" /&gt;
&lt;action application="set" data="sip_callee_id_number=2332" /&gt;
&lt;action application="bridge" data="sofia/gateway/provider/&lt;Reginald's cellphone number&gt;" /&gt;
</pre>
<p><br />
</p>
<a name="sip_callee_id_number" id="sip_callee_id_number"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_callee_id_name" title="Variable sip callee id name">sip_callee_id_number</a> </span></h3>
<p>Set on the inbound leg to control what caller ID number appears in the caller phone's display.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="sip_callee_id_name=Reginald" /&gt;
&lt;action application="set" data="sip_callee_id_number=2332" /&gt;
&lt;action application="bridge" data="sofia/gateway/provider/&lt;Reginald's cellphone number&gt;" /&gt;
</pre>
<p>If you find using <i><a href="/wiki/Misc._Dialplan_Tools_set" title="Misc. Dialplan Tools set">set</a></i> doesn't work, try using <i><a href="/wiki/Misc._Dialplan_Tools_export" title="Misc. Dialplan Tools export">export</a></i> instead.
</p><p><br />
</p>
<a name="Call_Recording_Related" id="Call_Recording_Related"></a><h2> <span class="mw-headline"> Call Recording Related </span></h2>
<p>These variables all relate to call recording. See also <a href="/wiki/Misc._Dialplan_Tools_record_session" title="Misc. Dialplan Tools record session">Misc._Dialplan_Tools_record_session</a>
</p>
<a name="Audio_File_Metadata" id="Audio_File_Metadata"></a><h3> <span class="mw-headline"> Audio File Metadata </span></h3>
<a name="RECORD_TITLE" id="RECORD_TITLE"></a><h4> <span class="mw-headline"> RECORD_TITLE </span></h4>
<a name="RECORD_COPYRIGHT" id="RECORD_COPYRIGHT"></a><h4> <span class="mw-headline"> RECORD_COPYRIGHT </span></h4>
<a name="RECORD_SOFTWARE" id="RECORD_SOFTWARE"></a><h4> <span class="mw-headline"> RECORD_SOFTWARE </span></h4>
<a name="RECORD_ARTIST" id="RECORD_ARTIST"></a><h4> <span class="mw-headline"> RECORD_ARTIST </span></h4>
<a name="RECORD_COMMENT" id="RECORD_COMMENT"></a><h4> <span class="mw-headline"> RECORD_COMMENT </span></h4>
<a name="RECORD_DATE" id="RECORD_DATE"></a><h4> <span class="mw-headline"> RECORD_DATE </span></h4>
<a name="RECORD_STEREO" id="RECORD_STEREO"></a><h4> <span class="mw-headline"> RECORD_STEREO </span></h4>
<a name="record_fill_cng" id="record_fill_cng"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_record_fill_cng" title="Variable record fill cng"> record_fill_cng</a> </span></h3>
<p>Description need please.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="record_fill_cng=1200"/&gt;
</pre>
<p><br />
</p>
<a name="RECORD_HANGUP_ON_ERROR" id="RECORD_HANGUP_ON_ERROR"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_RECORD_HANGUP_ON_ERROR" title="Variable RECORD HANGUP ON ERROR"> RECORD_HANGUP_ON_ERROR</a> </span></h3>
<p>When set to <i>true</i> this channel variable will cause the call to hangup if there is an error when trying to record the call. This is not a common feature, however in cases where a call MUST be recorded it makes it impossible to have calls that are not recorded. (Useful in some business scenarios.)
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="RECORD_HANGUP_ON_ERROR=true"/&gt;
</pre>
<p><br />
</p>
<a name="RECORD_DISCARDED" id="RECORD_DISCARDED"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_RECORD_DISCARDED" title="Variable RECORD DISCARDED"> RECORD_DISCARDED</a> </span></h3>
<p>If a recording gets dropped or discarded then this channel variable is set to true. Useful for diagnostics.
</p><p><b>Usage:</b>
</p>
<pre>N/A
</pre>
<p><br />
</p>
<a name="record_post_process_exec_api" id="record_post_process_exec_api"></a><h3> <span class="mw-headline">record_post_process_exec_api</span></h3>
<p>and
</p>
<a name="record_post_process_exec_app" id="record_post_process_exec_app"></a><h3> <span class="mw-headline">record_post_process_exec_app</span></h3>
<p>These two variables allow the postprocessing of recorded audio.  The reason this is required is if the A leg hangs up first in a call, the dialplan stops being processed, and then you aren't able to take action on the file that was recorded.  These variables take the form of:
</p>
<pre>&lt;action application="set" data="record_post_process_exec_api=some_api_app:api_app args" /&gt;
</pre>
<a name="record_restart_limit_on_dtmf" id="record_restart_limit_on_dtmf"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_record_restart_limit_on_dtmf" title="Variable record restart limit on dtmf"> record_restart_limit_on_dtmf</a> </span></h3>
<p><a href="/index.php?title=Record_restart_limit_on_dtmf&amp;action=edit&amp;redlink=1" class="new" title="Record restart limit on dtmf (page does not exist)">Record restart limit on dtmf</a>
</p>
<a name="record_sample_rate" id="record_sample_rate"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_record_sample_rate" title="Variable record sample rate"> record_sample_rate</a> </span></h3>
<p>Specify the sampling rate of the recorded file.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="record_sample_rate=8000"/&gt;
</pre>
<p><br />
</p>
<a name="record_waste_resources" id="record_waste_resources"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_record_waste_resources" title="Variable record waste resources"> record_waste_resources</a> </span></h3>
<p>By default record doesn't send RTP packets. This is generally acceptable, but for longer recordings or depending on the RTP timer of your gateway, your channel may hangup with cause MEDIA_TIMEOUT. Setting this variable will 'waste' bandwidth by sending RTP even during recording. The value can be true/false/&lt;desired silence factor&gt;. By default the silence factor is 1400 if you set record_waste_resources=true.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="record_waste_resources=true"/&gt;
</pre>
<p><br />
</p>
<a name="Codec_Related" id="Codec_Related"></a><h2> <span class="mw-headline"> Codec Related </span></h2>
<a name="absolute_codec_string" id="absolute_codec_string"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_absolute_codec_string" title="Variable absolute codec string"> absolute_codec_string</a> </span></h3>
<p>Sets the absolute codec string to use (nothing will be appended).
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="absolute_codec_string=PCMU,GSM"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="codec_string" id="codec_string"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_codec_string" title="Variable codec string"> codec_string</a> </span></h3>
<p>Sets the base codec string to use.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="codec_string=PCMU,GSM"/&gt;
</pre>
<p><br />
</p>
<a name="inherit_codec" id="inherit_codec"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_inherit_codec" title="Variable inherit codec"> inherit_codec</a> </span></h3>
<p>If late negotiation is on, and you set inherit_codec=true on the A leg, the negotiated codec of the B leg will be forced onto the A leg.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="inherit_codec=true"/&gt;
</pre>
<p><br />
</p>
<a name="read_codec" id="read_codec"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_read_codec" title="Variable read codec"> read_codec</a> </span></h3>
<p>Read only. The negotiated codec of the inbound call leg.
</p><p><br />
</p>
<a name="write_codec" id="write_codec"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_write_codec" title="Variable write codec"> write_codec</a> </span></h3>
<p>Read only. The negotiated codec of the outbound call leg.
</p><p><br />
</p>
<a name="passthru_ptime_mismatch" id="passthru_ptime_mismatch"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_passthru_ptime_mismatch" title="Variable passthru ptime mismatch"> passthru_ptime_mismatch</a> </span></h3>
<p>If ptime from leg A and leg B don't match and if mod_com_g729 is used, the call would normally use the codec to re-packetize the RTP stream.
</p><p>With this parameter, mod_com_g729 will re-packetize without decoding/encoding, as mod_g729 would do.
</p><p><br />
<b>Usage:</b>
</p><p>This has to be set in {} before bridging. 
That will probably not work if set using export before bridging.
</p>
<pre>&lt;action application="bridge" data="{passthru_ptime_mismatch=true}sofia/gateway/trunk/$1"/&gt;
</pre>
<p>Note: It may also be set globally in vars.xml.
</p><p><br />
</p>
<a name="conference_enforce_security" id="conference_enforce_security"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_conference_enforce_security" title="Variable conference enforce security"> conference_enforce_security</a> </span></h3>
<p>Allows the conference security to be overridden. This applies in two different scenarios, one for inbound and one for outbound. By default, conference security is always applied to inbound calls and is always skipped for outbound calls. This channel variable allows the behavior to be modified.
</p><p><br />
<b>Usage:</b>
</p><p>Inbound
</p>
<pre>&lt;action application="set" data="conference_enforce_security=false"/&gt;
&lt;action application="conference" data="3000"/&gt;
</pre>
<p>Outbound
</p>
<pre>originate {conference_enforce_security=true}sofia/internal/1001 &amp;conference(3000)
</pre>
<p><br />
</p>
<a name="suppress-cng" id="suppress-cng"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_suppress-cng" title="Variable suppress-cng"> suppress-cng</a> </span></h3>
<p>Sets a=silenceSupp: off in the sdp to disable silence suppression while making an outbound call.
</p><p>Usage:
&lt;param name="suppress-cng" value="true"/&gt;
<br />
</p><p><br />
</p>
<a name="IVR_related" id="IVR_related"></a><h2> <span class="mw-headline"> IVR related </span></h2>
<a name="ivr_menu_terminator" id="ivr_menu_terminator"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_ivr_menu_terminator" title="Variable ivr menu terminator"> ivr_menu_terminator</a> </span></h3>
<p>You can set to none or the dtmf chars you want to terminate input.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="ivr_menu_terminator=#"/&gt;
</pre>
<p><br />
</p>
<a name="detect_speech_result" id="detect_speech_result"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_detect_speech_result" title="Variable detect speech result"> detect_speech_result</a> </span></h3>
<p>The result of <a href="/wiki/Misc._Dialplan_Tools_play_and_detect_speech" title="Misc. Dialplan Tools play and detect speech">play_and_detect_speech</a>.
</p><p><b>Usage:</b>
</p><p>This value is read-only. 
</p><p><br />
</p><p><br />
</p>
<a name="SIP_related_variables" id="SIP_related_variables"></a><h2> <span class="mw-headline"> SIP related variables </span></h2>
<a name="disable_hold" id="disable_hold"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_disable_hold" title="Variable disable hold"> disable_hold</a> </span></h3>
<p>When set to true the user may not put the call on hold.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="disable_hold=true"/&gt;
</pre>
<p><br />
</p>
<a name="sip_acl_authed_by" id="sip_acl_authed_by"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_acl_authed_by" title="Variable sip acl authed by"> sip_acl_authed_by</a> </span></h3>
<p>Contains the name of the ACL node that authorized this call.
</p><p><br />
</p><p><b>Usage:</b>
</p>
<pre>None.
</pre>
<p><br />
</p>
<a name="sip_acl_token" id="sip_acl_token"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_acl_token" title="Variable sip acl token"> sip_acl_token</a> </span></h3>
<p>Contains the ACL auth token for the current call.
</p><p><br />
</p><p><b>Usage:</b>
</p>
<pre>N/A
</pre>
<p><br />
</p>
<a name="sip_copy_multipart" id="sip_copy_multipart"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_copy_multipart" title="Variable sip copy multipart"> sip_copy_multipart</a> </span></h3>
<p>FreeSWITCH supports INVITEs with multipart bodies.  Typically SIP bodies only have one MIME part with an SDP using MIME type application/sdp.  The SIP spec allows for multiple bodies defined with MIME type multipart/mixed.  In this case FreeSWITCH will do it's best to find the MIME part with the SDP and parse that as it normally does.  However, you can change FreeSWITCH behavior with multipart bodies and bridge using this variable.
</p><p><br />
</p><p><b>Usage:</b>
</p><p>To have FreeSWITCH keep the multiple MIME parts intact when using bridge (default):
</p>
<pre>&lt;action application="set" data="sip_copy_multipart=true"/&gt;
</pre>
<p>NOTE: FreeSWITCH will "do the right thing" and attach an application/sdp type generated by FreeSWITCH (per your settings) for the B leg as it normally would.  The other non-SDP MIME parts just pass through.
</p><p>To have FreeSWITCH strip the multiple MIME parts when using bridge:
</p>
<pre>&lt;action application="set" data="sip_copy_multipart=false"/&gt;
</pre>
<p><br />
</p>
<a name="sip_invite_domain" id="sip_invite_domain"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_invite_domain" title="Variable sip invite domain"> sip_invite_domain</a> </span></h3>
<p>Set the from domain in leg (B).
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="{sip_invite_domain=${sip_from_host}}sofia/gateway/gw1/$1@domain.org"/&gt;
</pre>
<p><br />
</p>
<a name="sip_invite_from_params" id="sip_invite_from_params"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_invite_from_params" title="Variable sip invite from params"> sip_invite_from_params</a> </span></h3>
<p>Sets the from parameters on the B-leg of the call. The from parameters come after user@host:port and before '&gt;'. The initial semi-colon is added after the port.
</p><p><b>Usage:</b>
</p>
<pre>{sip_invite_from_params=otg=mytrunk}sofia/gateway/sonus/$1
</pre>
<p>Result:
</p>
<pre>From: &lt;sip:5552345678@sonus:5060;otg=mytrunk&gt;;tag=blah
</pre>
<p><br />
</p>
<a name="sip_network_destination" id="sip_network_destination"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_network_destination" title="Variable sip network destination"> sip_network_destination</a> </span></h3>
<p>It is intended for use with devices registering behind a NAT where the Request-URI should contain the contact that was bound to the AOR during the registration request while the request itself should be sent to the public IP and port number of the NAT "pinhole". It does not add a Route header field to the request like the&nbsp;;fs_path= or the sip_route_uri options do. 
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="{sip_network_destination=sip:5551234567@66.243.109.243:10005}sofia/external/5551234567@172.16.110.45:5060"/&gt;
</pre>
<p><br />
</p>
<a name="sip_auth_username" id="sip_auth_username"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_auth_username" title="Variable sip auth username"> sip_auth_username</a> </span></h3>
<p>For mod_sofia answer auth challenges without defining a full gateway. Used in tandem with <a href="/wiki/Variable_sip_auth_password" title="Variable sip auth password"> sip_auth_password</a>. Also indicates the SIP username a device successfully registered to FreeSWITCH with.
</p><p><br />
<b>Usage:</b>
</p>
<pre>originate {sip_auth_username=&lt;your_user_name&gt;,sip_auth_password=&lt;your_password&gt;}sofia/external/1xxxxxxx@12.34.56.78 &amp;echo
</pre>
<p><br />
</p>
<a name="sip_auth_password" id="sip_auth_password"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_auth_password" title="Variable sip auth password"> sip_auth_password</a> </span></h3>
<p>For mod_sofia use with sip_auth_username to answer auth challenges without defining a full gateway.
</p><p><br />
<b>Usage:</b>
</p>
<pre>originate {sip_auth_username=&lt;your_user_name&gt;,sip_auth_password=&lt;your_password&gt;}sofia/external/1xxxxxxx@12.34.56.78 &amp;echo
</pre>
<p><br />
</p>
<a name="sip_auto_simplify" id="sip_auto_simplify"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_auto_simplify" title="Variable sip auto simplify"> sip_auto_simplify </a> </span></h3>
<p>When set, this directs FreeSWITCH to remove itself from the SIP signaling path if it can safely do so.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="sip_auto_simplify=true"/&gt;
</pre>
<p><br />
</p>
<a name="sip_callee_id_name_2" id="sip_callee_id_name_2"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_callee_id_name" title="Variable sip callee id name"> sip_callee_id_name</a> </span></h3>
<p>Set on the inbound leg to control what caller ID name appears in the calling phone's display.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="sip_callee_id_name=Reginald" /&gt;
&lt;action application="set" data="sip_callee_id_number=2332" /&gt;
&lt;action application="bridge" data="sofia/gateway/provider/&lt;Reginald's cellphone number&gt;" /&gt;
</pre>
<p><br />
</p>
<a name="sip_callee_id_number_2" id="sip_callee_id_number_2"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_callee_id_number" title="Variable sip callee id number"> sip_callee_id_number</a> </span></h3>
<p>Set on the inbound leg to control what caller ID number appears in the caller phone's display.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="sip_callee_id_name=Reginald" /&gt;
&lt;action application="set" data="sip_callee_id_number=2332" /&gt;
&lt;action application="bridge" data="sofia/gateway/provider/&lt;Reginald's cellphone number&gt;" /&gt;
</pre>
<p>If you find using <i><a href="/wiki/Misc._Dialplan_Tools_set" title="Misc. Dialplan Tools set">set</a></i> doesn't work, try using <i><a href="/wiki/Misc._Dialplan_Tools_export" title="Misc. Dialplan Tools export">export</a></i> instead.
</p><p><br />
</p>
<a name="sip_force_audio_fmtp" id="sip_force_audio_fmtp"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_force_audio_fmtp" title="Variable sip force audio fmtp"> sip_force_audio_fmtp </a> </span></h3>
<p>Set the audio fmtp.
</p><p><b>Usage:</b>
</p>
<pre>Please add example if you have one.
</pre>
<p><br />
</p>
<a name="sip_invite_req_uri" id="sip_invite_req_uri"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_invite_req_uri" title="Variable sip invite req uri"> sip_invite_req_uri</a> </span></h3>
<p>Sets the uri in the header Request-Line INVITE when calling bridge or originate.
</p><p>NOTE: <a href="http://tools.ietf.org/html/rfc3261" class="external" title="http://tools.ietf.org/html/rfc3261">RFC 3261</a> specifies that compliant endpoints SHOULD route based on the Request URI, not the URI in To:
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="bridge" data="{sip_invite_req_uri=sip:11112222@test1.com}sofia/external/33334444%192.168.4.6"/&gt;
</pre>
<p>Result:
</p>
<pre> INVITE sip:11112222@test1.com SIP/2.0
 From: "" &lt;sip:0000000000@192.168.2.7&gt;;tag=N6K579y4g6j0D
 To: &lt;sip:33334444@192.168.4.6&gt;
</pre>
<p><br />
</p>
<a name="sip_invite_to_uri" id="sip_invite_to_uri"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_invite_to_uri" title="Variable sip invite to uri"> sip_invite_to_uri</a> </span></h3>
<p>Sets the uri in the header To when calling bridge or originate.
</p><p><b>Usage:</b>
</p>
<pre> originate {sip_invite_to_uri=&lt;sip:11112222@test1.com&gt;}sofia/internal/33334444@192.168.4.6 &amp;park
</pre>
<p>Result:
</p>
<pre> INVITE sip:33334444@192.168.4.6 SIP/2.0
 From: "" &lt;sip:0000000000@192.168.2.7&gt;;tag=N6K579y4g6j0D
 To: &lt;sip:11112222@test1.com&gt;
</pre>
<p>Alternatively, if you need to set just the username in the header To, you can pass it at the end of the dial string:
</p>
<pre> originate sofia/internal/33334444@192.168.4.6^11112222 &amp;park
</pre>
<p>Result:
</p>
<pre> INVITE sip:33334444@192.168.4.6 SIP/2.0
 From: "" &lt;sip:0000000000@192.168.2.7&gt;;tag=Qr6pB00BBrZ5m
 To: &lt;sip:11112222@@192.168.4.6&gt;
</pre>
<p><br />
</p>
<a name="sip_ignore_reinvites" id="sip_ignore_reinvites"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_ignore_reinvites" title="Variable sip ignore reinvites"> sip_ignore_reinvites</a> </span></h3>
<p>Tells FreeSWITCH to accept/ignore re-INVITEs from remote end.
</p><p><b>Usage:</b>
</p><p>Don't allow any re-INVITEs once bridged.
</p>
<pre>&lt;action application="set" data="sip_ignore_reinvites=true"/&gt;
</pre>
<p><br />
</p>
<a name="sip_has_crypto" id="sip_has_crypto"></a><h3> <span class="mw-headline"> <a href="/index.php?title=Variable_sip_has_crypto&amp;action=edit&amp;redlink=1" class="new" title="Variable sip has crypto (page does not exist)"> sip_has_crypto</a> </span></h3>
<p><a href="/index.php?title=Variable_sip_has_crypto&amp;action=edit&amp;redlink=1" class="new" title="Variable sip has crypto (page does not exist)">Variable sip has crypto</a>
</p>
<a name="sip_secure_media" id="sip_secure_media"></a><h3> <span class="mw-headline"> <a href="/index.php?title=Variable_sip_secure_media&amp;action=edit&amp;redlink=1" class="new" title="Variable sip secure media (page does not exist)"> sip_secure_media</a> </span></h3>
<p><a href="/index.php?title=Variable_sip_secure_media&amp;action=edit&amp;redlink=1" class="new" title="Variable sip secure media (page does not exist)">Variable sip secure media</a>
</p>
<a name="timer_name" id="timer_name"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_timer_name" title="Variable timer name"> timer_name</a> </span></h3>
<p>If set will make playback and speak use a timer to clock the audio instead of the read.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="timer_name=soft"/&gt;
</pre>
<p><br />
</p><p><br />
</p>
<a name="ignore_display_updates" id="ignore_display_updates"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_ignore_display_updates" title="Variable ignore display updates"> ignore_display_updates</a> </span></h3>
<p>See link
</p>
<a name="deny_refer_requests" id="deny_refer_requests"></a><h3> <span class="mw-headline"> <a href="/index.php?title=Variable_deny_refer_requests&amp;action=edit&amp;redlink=1" class="new" title="Variable deny refer requests (page does not exist)"> deny_refer_requests</a> </span></h3>
<p>If this variable is set to true on either leg of a bridged SIP call, and the other end sends a REFER request, this will be denied by FreeSWITCH.
</p>
<a name="SDP_Manipulation" id="SDP_Manipulation"></a><h2> <span class="mw-headline">SDP Manipulation</span></h2>
<p>When set, these variable change the SDP headers. (not for the faint of heart)
</p>
<a name="sdp_m_per_ptime" id="sdp_m_per_ptime"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sdp_m_per_ptime" title="Variable sdp m per ptime"> sdp_m_per_ptime</a> </span></h3>
<p>Adds a new m= line for each distinct ptime in codec list.
</p><p>When this variable is not set:
</p>
<ul><li> When mixing codecs with various ptime in a codec list, they will now be allowed to co-exist in the sdp but it will send no ptime attr. This means the ptime preferences on the offer will be ignored when mixing codecs with various ptimes. When receiving a codec list with no ptime attr, the ptime will be chosen from local preference instead of assuming 20ms. This means if offer contains PCMU with no ptime and FS has PCMU@40i
</li></ul>
<ul><li>Dynamic payloads will now start at 98 and increment per additional dynamic codec per call. So now you can add CELT@32000h,CELT@48000h and each one will be auto-assigned a dynamic payload type. 
</li></ul>
<p>Is now implied to be true, if you don't like this set it to false but its going to be undefined behaviour. This basically means if you call in with ptime 30 then you have a bunch of ptime 20 codecs in your outbound list that there will be one m= line with 30 and the original inbound codec and more m= lines for each discinct ptime in your list. This is, of course, will depend on disable_trancoding or absolute_codec_string as well 
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="sdp_m_per_ptime=true"/&gt;
</pre>
<p><br />
</p>
<a name="switch_r_sdp" id="switch_r_sdp"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_switch_r_sdp" title="Variable switch r sdp"> switch_r_sdp</a> </span></h3>
<p>Read only. This variable holds the remote SDP for the current leg/channel.
</p><p><br />
<b>Usage:</b>
</p><p>Rewriting SDP:
</p>
<pre>
&lt;action application=&quot;set&quot;&gt;
&lt;![CDATA[switch_r_sdp=(sdp here)
 ]]&gt;
&lt;/action&gt;
</pre>
<p><br />
</p>
<a name="switch_l_sdp" id="switch_l_sdp"></a><h3> <span class="mw-headline">switch_l_sdp</span></h3>
<ul><li> (Local SDP)
</li><li> Although this variable is defined in switch_types.h it is not used anywhere in the FreeSwitch code. (It should be removed for the source and from this page.)
</li></ul>
<a name="switch_m_sdp" id="switch_m_sdp"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_switch_m_sdp" title="Variable switch m sdp"> switch_m_sdp</a> </span></h3>
<p>The B-leg remote SDP.
</p><p><br />
<b>Usage:</b>
</p>
<ul><li> Used to store the remote SDP used by the other leg/channel of a call. (In the A-leg that will be the remote SDP of the B-leg.)
</li><li> This variable is set, but never used, by FreeSWITCH. ("read-only")
</li></ul>
<p><br />
</p>
<a name="sip_append_audio_sdp" id="sip_append_audio_sdp"></a><h3> <span class="mw-headline">sip_append_audio_sdp</span></h3>
<p>This may be used to append audio parameters to the SDP sent to B-leg.
</p><p>It should/must be set before bridging.
</p><p>Usage:
</p>
<pre>&lt;action application="export" data="sip_append_audio_sdp=a=fmtp:18 annexb=no"/&gt;
</pre>
<a name="sip_ignore_183nosdp" id="sip_ignore_183nosdp"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_Sip_ignore_183nosdp" title="Variable Sip ignore 183nosdp">sip_ignore_183nosdp</a></span></h3>
<p>Ignoring 183 w/o SDP.  This option is not for normal basic call flow.
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="sip_ignore_183nosdp=true"/&gt;
</pre>
<a name="verbose_sdp" id="verbose_sdp"></a><h3> <span class="mw-headline"><a href="/index.php?title=Variable_Verbose_sdp&amp;action=edit&amp;redlink=1" class="new" title="Variable Verbose sdp (page does not exist)">verbose_sdp</a></span></h3>
<p>The RFCs require an rtpmap for IANA dynamic payload types.  An rtpmap with codec name and payload type is not required for well known static payloads - (PCMU, PCMA, G729, etc).
</p><p>By default FreeSWITCH sets verbose_sdp=false which doesn't include an rtpmap for static payload types.  If your equipment doesn't support this (shame on them) set verbose_sdp=true which will include rtpmaps for any static payload types (previous default behavior).
</p>
<a name="sip_local_sdp_str" id="sip_local_sdp_str"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_sip_local_sdp_str" title="Variable sip local sdp str"> sip_local_sdp_str </a> </span></h3>
<p>Description goes here
</p><p><br />
<b>Usage:</b>
</p><p>Example needed.
</p><p><br />
</p>
<a name="sip_enable_soa" id="sip_enable_soa"></a><h3> <span class="mw-headline"> <a href="/index.php?title=Variable_sip_enable_soa&amp;action=edit&amp;redlink=1" class="new" title="Variable sip enable soa (page does not exist)"> sip_enable_soa </a> </span></h3>
<p>For per call basis which can be set to false to disable SIP SOA from sofia and most likely result in untouched exchange of SDP.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="bypass_media=true"/&gt;
&lt;action application="export" data="sip_enable_soa=false"/&gt;
</pre>
<p><br />
</p>
<a name="FIFO_related_variables" id="FIFO_related_variables"></a><h2> <span class="mw-headline">FIFO related variables</span></h2>
<a name="fifo_bridged" id="fifo_bridged"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_fifo_bridged" title="Variable fifo bridged"> fifo_bridged</a></span></h3>
<p>Description goes here
</p><p><br />
</p><p><b>Usage:</b>
</p>
<pre>Example needed
</pre>
<p><br />
</p>
<a name="fifo_caller_consumer_import" id="fifo_caller_consumer_import"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_fifo_caller_consumer_import" title="Variable fifo caller consumer import"> fifo_caller_consumer_import</a></span></h3>
<p>Import list of variables from the caller to the consumer.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="fifo_caller_consumer_import=var1,var2"/&gt;
</pre>
<p><br />
</p>
<a name="fifo_consumer_caller_import" id="fifo_consumer_caller_import"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_fifo_consumer_caller_import" title="Variable fifo consumer caller import"> fifo_consumer_caller_import</a></span></h3>
<p>Import list of variables from the consumer to the caller
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="fifo_consumer_caller_import=var1,var2"/&gt;
</pre>
<p><br />
</p>
<a name="fifo_manual_bridged" id="fifo_manual_bridged"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_fifo_manual_bridged" title="Variable fifo manual bridged"> fifo_manual_bridged</a></span></h3>
<p>Description goes here
</p><p><br />
</p><p><b>Usage:</b>
</p>
<pre>Example needed
</pre>
<p><br />
</p>
<a name="fifo_position" id="fifo_position"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_fifo_position" title="Variable fifo position"> fifo_position</a></span></h3>
<p>Description goes here
</p><p><br />
</p><p><b>Usage:</b>
</p>
<pre>Example needed
</pre>
<p><br />
</p>
<a name="fifo_role" id="fifo_role"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_fifo_role" title="Variable fifo role"> fifo_role</a> </span></h3>
<p>For reporting purposes, i.e. in the CDRs, the variable will contain "consumer" or "caller" depending upon the call leg. 
</p><p><br />
</p><p><b>Usage:</b>
</p>
<pre>None
</pre>
<p><br />
</p>
<a name="transfer_after_bridge" id="transfer_after_bridge"></a><h3> <span class="mw-headline"><a href="/wiki/Variable_transfer_after_bridge" title="Variable transfer after bridge"> transfer_after_bridge</a> </span></h3>
<p>This variable can control what happens when a call is hang up. This can be used in conjunction with <a href="/wiki/Mod_fifo" title="Mod fifo">mod_fifo</a> to control the "agent", possibly sending them back to an agent queue. This is checked after <a href="/wiki/Variable_park_after_bridge" title="Variable park after bridge">park_after_bridge</a> and before <a href="/wiki/Variable_hangup_after_bridge" title="Variable hangup after bridge">hangup_after_bridge</a>.
</p><p><b>Usage:</b>
</p>
<pre>&lt;action application="set" data="transfer_after_bridge=1000"/&gt;
</pre>
<p>or,
</p>
<pre>&lt;action application="set" data="transfer_after_bridge=1000:XML:default"/&gt;
</pre>
<p>(Note the&nbsp;: separator)
</p><p><br />
</p>
<a name="Playback_related_variables" id="Playback_related_variables"></a><h2> <span class="mw-headline">Playback related variables</span></h2>
<a name="playback_terminators" id="playback_terminators"></a><h3> <span class="mw-headline">playback_terminators</span></h3>
<p>Allows you to set which DTMF tones, if pressed during the playback of a file, will stop it.  The default terminator is *.  Keyword 'none' disables on-key termination.
</p>
<pre> &lt;action application="set" data="playback_terminators=#*"/&gt;
</pre>
<a name="sound_prefix" id="sound_prefix"></a><h3> <span class="mw-headline">sound_prefix</span></h3>
<p>Directory prefix where the sounds lives.
</p>
<a name="playback_terminator_used" id="playback_terminator_used"></a><h3> <span class="mw-headline">playback_terminator_used</span></h3>
<p>Contains the digit that the caller used to terminate a playback.
Is undef when a new playback is called.
</p>
<a name="playback_ms" id="playback_ms"></a><h3> <span class="mw-headline">playback_ms</span></h3>
<p>Contains the number of milliseconds of the length of the audio file just played back.
</p>
<a name="playback_samples" id="playback_samples"></a><h3> <span class="mw-headline">playback_samples</span></h3>
<p>Contains the number of samples in the audio file just played back.
</p>
<a name="playback_sleep_val" id="playback_sleep_val"></a><h3> <span class="mw-headline">playback_sleep_val</span></h3>
<p>How long to pause after a file is played.  Default is 250 milliseconds.
</p><p>To play a list of short files one right after the other, with no pause in between:
</p>
<pre> &lt;action application="set" data="playback_sleep_val=0"/&gt;
</pre>
<a name="playback_delimiter" id="playback_delimiter"></a><h3> <span class="mw-headline">playback_delimiter</span></h3>
<p>When set allows playback of multiple files in sequence, by separating them with the delimiter.
</p><p>For example, setting playback_delimiter to the following:
</p>
<pre> &lt;action application="set" data="playback_delimiter=&amp;"/&gt;
</pre>
<p>Permits the streaming of files foo.wav and bar.wav one right after the other:
</p>
<pre> &lt;action application="playback" data="foo.wav&amp;bar.wav"/&gt;
</pre>
<a name="sleep_eat_digits" id="sleep_eat_digits"></a><h3> <span class="mw-headline">sleep_eat_digits</span></h3>
<p>When set to true, the sleep application will consume DTMFs which will, for example, prevent a caller from exiting out of an IVR. The default behavior is not to eat DTMF digits. NOTE: this is a change in default behavior as the <a href="/wiki/Misc._Dialplan_Tools_sleep" title="Misc. Dialplan Tools sleep">sleep</a> application previously ate DTMFs without exception. Be sure to set <b>sleep_eat_digits</b> to <i>true</i> in order to preserve the previous behavior.
</p>
<pre> &lt;action application="set" data="sleep_eat_digits=true"/&gt;
</pre>
<p>This variable was added in SVN rev 14102.
</p>
<a name="playback_timeout_sec" id="playback_timeout_sec"></a><h3> <span class="mw-headline">playback_timeout_sec</span></h3>
<p>Set timeout for playback. This is very useful if you want to play short excerpts of a file that could be very long.
</p>
<pre> &lt;action application="set" data="playback_timeout_sec=10"/&gt;
</pre>
<a name="Originate_related_variables" id="Originate_related_variables"></a><h2> <span class="mw-headline">Originate related variables</span></h2>
<a name="execute_on_originate" id="execute_on_originate"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_execute_on_originate" title="Variable execute on originate"> execute_on_originate</a> </span></h3>
<p>Executes code on successful origination. Use the '&lt;app&gt; &lt;arg&gt;' format to execute in the origination thread or use '&lt;app&gt;::&lt;arg&gt;' to execute asynchronously.
</p><p>Successful origination means the remote server responds, NOT when the call is actually answered.
</p><p><b>Usage:</b>
</p>
<pre>originate {ignore_early_media=true,execute_on_originate='cng_plc'}sofia/gateway/foo/123456789 9664
</pre>
<pre>originate {ignore_early_media=true,execute_on_originate='my_app::my_arg'}sofia/gateway/foo/123456789 9664
</pre>
<p><br />
</p>
<a name="leg_delay_start" id="leg_delay_start"></a><h3> <span class="mw-headline">leg_delay_start</span></h3>
<p>Specifies a wait time in seconds before each leg is called in a forked dial scenario. Can be used in per-leg [], but not in global {} for the dialstring.<br />
Usage:
</p>
<pre>&lt;action application="bridge" data="sofia/profile/dest1,[leg_delay_start=10]sofia/profile/dest2,[leg_delay_start=15]sofia/profile/dest3"/&gt;
</pre>
<a name="originate_disposition" id="originate_disposition"></a><h3> <span class="mw-headline">originate_disposition</span></h3>
<p>This is the originate disposition or hangup cause that is returned. (LEG B)
</p><p>The value is updated after every bridge attempt, if the bridge is not successful.
</p>
<a name="originate_retries" id="originate_retries"></a><h3> <span class="mw-headline">originate_retries</span></h3>
<p>Number of retries before giving up on originating a call (default is 0).
</p>
<a name="originate_retry_sleep_ms" id="originate_retry_sleep_ms"></a><h3> <span class="mw-headline">originate_retry_sleep_ms</span></h3>
<p>This will set how long FreeSWITCH is going to wait between sending invite messages to the receiving gateway.
</p>
<pre>&lt;action application="set" data="originate_retry_sleep_ms=500"/&gt;
</pre>
<p>Using the value of 500 FreeSWITCH will wait 500ms between sending invite messages to the called gateway.
</p>
<a name="originate_timeout_2" id="originate_timeout_2"></a><h3> <span class="mw-headline">originate_timeout</span></h3>
<p>Determines how long FreeSWITCH is going to wait for a response from the invite message sent to the gateway.
</p>
<pre>&lt;action application="set" data="originate_timeout=2"/&gt;
</pre>
<p>This is very useful if you are using multiple gateways within your dial plan.. so if your dial string is:
</p>
<pre>&lt;action application="bridge" data="sofia/default/$1@192.168.1.4|sofia/default/$1@192.168.1.5"/&gt;
</pre>
<p>In this example FreeSWITCH will wait 2 seconds for the 192.168.1.4 to respond to the invite message before trying the next gateway.
</p>
<a name="originating_leg_uuid" id="originating_leg_uuid"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_originating_leg_uuid" title="Variable originating leg uuid"> originating_leg_uuid</a> </span></h3>
<p>Shows the uuid of the originating leg on an outbound channel
</p><p><b>Usage:</b>
</p><p>In A-leg CDR:
</p>
<pre>&lt;uuid&gt;cb5f5b90-75a0-11e0-873b-d1cba9e0f1b8&lt;/uuid&gt;
&lt;call_uuid&gt;cb5f5b90-75a0-11e0-873b-d1cba9e0f1b8&lt;/call_uuid&gt;</pre>
<p>In B-leg CDR:
</p>
<pre>&lt;uuid&gt;cb8633aa-75a0-11e0-873d-d1cba9e0f1b8&lt;/uuid&gt;
&lt;call_uuid&gt;cb5f5b90-75a0-11e0-873b-d1cba9e0f1b8&lt;/call_uuid&gt;
&lt;originating_leg_uuid&gt;cb5f5b90-75a0-11e0-873b-d1cba9e0f1b8&lt;/originating_leg_uuid&gt;</pre>
<p>Note that the leg uuid's are different. The call_uuid matches the two legs together, but the originating_leg_uuid can do so as well.
</p><p><br />
</p>
<a name="origination_channel_name" id="origination_channel_name"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_origination_channel_name" title="Variable origination channel name"> origination_channel_name</a> </span></h3>
<p>Set this in the {} when doing an originate to create a custom channel name
</p><p><b>Usage:</b>
</p>
<pre>originate {origination_channel_name='this_is_my_channel_name'}loopback/9664 9195
</pre>
<p><br />
</p>
<a name="origination_caller_id_name" id="origination_caller_id_name"></a><h3> <span class="mw-headline">origination_caller_id_name</span></h3>
<p>Sets the origination callerid name (LEG A).
</p><p>If you want to set the Caller ID on an origination call you should add this inside the {} brackets before the dialstring.
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="origination_caller_id_name=Uncle Sam"/&gt;
</pre>
<a name="origination_caller_id_number" id="origination_caller_id_number"></a><h3> <span class="mw-headline">origination_caller_id_number</span></h3>
<p>Sets the origination callerid number. (LEG A)
</p><p>If you want to set the Caller ID on an origination call you should add this inside the {} brackets before the dialstring.
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="origination_caller_id_number=9185551212"/&gt;
</pre>
<p>But, if you want to relay the Caller ID Number of an incoming PSTN call via FXO gateway, comment out this variable.
</p>
<a name="origination_cancel_key" id="origination_cancel_key"></a><h3> <span class="mw-headline">origination_cancel_key</span></h3>
<p><i>Implemented in revision 14650</i>
Used with attended transfer function. Allows you to set a DTMF key that will cancel the att_xfer and re-connect to the call on hold.
</p><p>It'll also cancel a bridge that hasn't been bridged as yet (and thus can't be terminated with a bridge_terminate_key)
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="origination_cancel_key=#"/&gt;
</pre>
<a name="origination_privacy" id="origination_privacy"></a><h3> <span class="mw-headline">origination_privacy</span></h3>
<p>Sets privacy profile for caller. Options are "screen", "hide_name", "hide_number".
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="origination_privacy=hide_name"/&gt;
</pre>
<a name="origination_uuid" id="origination_uuid"></a><h3> <span class="mw-headline">origination_uuid</span></h3>
<p>You can specify the uuid of an originated call using origination_uuid.  This way you can hang up the call before it is answered, since you know the uuid.
Just remember you need to use the create_uuid command to generate the uuid as 2 calls with the same uuid == bad!
</p>
<pre>originate [origination_uuid=....]sofia/&lt;profile&gt;/&lt;extension&gt;</pre>
<p>Bridge also uses the origination syntax so you can also pre-allocate the UUID for the new channel resulting from a bridge by using the {}/[] syntax and specifying origination_uuid there, too.
</p>
<a name="originator" id="originator"></a><h3> <span class="mw-headline">originator</span></h3>
<p>Holds the UUID of the channel that originated the call. It's used to notify a parent channel that the state of its child has changed, hence interrupting any blocking reads on the parent. It's automatically set and read by FreeSWITCH internals. Usually, the user won't want to set it.
</p>
<a name="originator_codec" id="originator_codec"></a><h3> <span class="mw-headline">originator_codec</span></h3>
<p>Sets the codec for calls originated from LEG A (setting the codec for LEG B)
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="originator_codec=PCMU"/&gt;
</pre>
<a name="RTP.2Fmedia_related_variables" id="RTP.2Fmedia_related_variables"></a><h2> <span class="mw-headline">RTP/media related variables</span></h2>
<a name="bypass_media" id="bypass_media"></a><h3> <span class="mw-headline">bypass_media</span></h3>
<p>When set, the media (RTP) from the originating endpoint is sent directly to the destination endpoint and vice versa. The signaling (SIP) for both endpoints still goes through FreeSWITCH, but the media is point-to-point.
</p>
<pre>&lt;action application="set" data="bypass_media=true"/&gt;
</pre>
<p>See also: <a href="/wiki/Bypass_Media" title="Bypass Media">Bypass Media Overview</a>
</p>
<a name="bypass_media_after_bridge" id="bypass_media_after_bridge"></a><h3> <span class="mw-headline">bypass_media_after_bridge</span></h3>
<p>Same as bypass_media but will handle media for a call until it has reached the answered state (and has processed a few RTP frames.)  At this point FreeSWITCH will use a ReInvite to take itself out of the media path.  This helps reduce audio latency and take some load off FreeSWITCH.  Especially useful for UACs behind Coned NAT as it gives RTP Auto-Adjust enough time to determine the correct ports to avoid one-way audio.
</p>
<a name="proxy_media" id="proxy_media"></a><h3> <span class="mw-headline">proxy_media</span></h3>
<p>Proxy Media mode puts Freeswitch in a "transparent proxy mode" for the RTP streams. The RTP streams still pass through freeswitch (unlike bypass media mode), however it is lighter on the CPU because freeswitch never even parses the packets or processes them in any way, it simply forwards them onwards.
</p><p>Note: <a href="/wiki/Codec_negotiation" title="Codec negotiation" class="mw-redirect">Late negotiation</a> (&lt;param name="inbound-late-negotiation" value="true"/&gt;
) must be enabled in sip profile for this to work in the dialplan
</p>
<pre> &lt;action application="set" data="proxy_media=true"/&gt;
</pre>
<p>See also: <a href="/wiki/Proxy_Media" title="Proxy Media">Proxy Media</a>
</p>
<a name="rtp_autoflush" id="rtp_autoflush"></a><h3> <span class="mw-headline">rtp_autoflush</span></h3>
<p>When set to true (default if not present), it will skip timer waits when the socket already has data on read.
When set to false, it will always sleep one timer interval. When a packet is too late with this setting, it would be saved for next time in the udp stack and we would place a filler packet into the core to keep it moving that is flagged as CNG so you know there is no audio in it. If you have it set to false, you end up with delay if the other side is sending the audio at a different speed (can be tiny difference but it would build up).
</p><p>It is worth it to set to true if you have crappy network conditions where you are hearing hiccups it's related to jitter. Sometimes you have the other side sending audio too fast, then this option set to false will smooth it out but if you have it set to false in jitter conditions it tricks it into moving too fast.
</p>
<a name="rtp_autoflush_during_bridge" id="rtp_autoflush_during_bridge"></a><h3> <span class="mw-headline">rtp_autoflush_during_bridge</span></h3>
<p>The same as rpt_autoflush, but is set during the bridge.
</p>
<a name="disable_rtp_auto_adjust" id="disable_rtp_auto_adjust"></a><h3> <span class="mw-headline">disable_rtp_auto_adjust</span></h3>
<p>Disable rtp auto adjust if it not behaves as you expected.
</p><p>It stops the switch from rewriting the RTP destination based on the source
</p><p>When RTP Auto-Adjust is ON FreeSWITCH will change the destination RTP address to match the source of the incoming packets, this doesn't work if the other end is really wanting to send and receive on a different addr.
</p><p>Usage:
</p>
<pre>Add {disable_rtp_auto_adjust=true} in your dial string.
</pre>
<a name="progress_timeout" id="progress_timeout"></a><h3> <span class="mw-headline">progress_timeout</span></h3>
<p>This is the maximum time we will wait before we get media (wether its early media, ringing or answer)
</p><p>Usage
</p>
<pre> &lt;action application="set" data="progress_timeout=20"/&gt;
</pre>
<p>See also <a href="/wiki/Early_Media" title="Early Media">Early Media</a>
</p>
<a name="bridge_answer_timeout" id="bridge_answer_timeout"></a><h3> <span class="mw-headline">bridge_answer_timeout</span></h3>
<ul><li>Introduced in build 15057 
</li></ul>
<p>Timeout in seconds how long to tolerate a bridge that is in early media without being answered (can be set on either leg)
</p><p>Usage
</p>
<pre> &lt;action application="set" data="bridge_answer_timeout=20"
</pre>
<p>See also <a href="/wiki/Early_Media" title="Early Media">Early Media</a>
</p>
<a name="ignore_early_media" id="ignore_early_media"></a><h3> <span class="mw-headline">ignore_early_media</span></h3>
<p>Controls if the call returns on early media or not.  Default is false. 
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="ignore_early_media=true"/&gt;
</pre>
<p>You may also specify a value for ignore_early_media in the argument to the bridge application, using the { } syntax. (ignore_early_media may not be specified on a per-leg basis, using the [ ] syntax, as it specifically is a global variable to the originate session.)
</p>
<pre>&lt;action application="bridge" data="{ignore_early_media=true}sofia/test-int/1001@somebox,sofia/test-int/1000@somehost"/&gt;
</pre>
<p>Setting the value to "ring_ready" will work the same as ignore_early_media=true but also send a SIP 180 to the inbound leg when the first SIP 183 is caught.
</p>
<pre> &lt;action application="set" data="ignore_early_media=ring_ready"/&gt;
</pre>
<p>See also <a href="/wiki/Early_Media" title="Early Media">Early Media</a>
</p>
<a name="ringback" id="ringback"></a><h3> <span class="mw-headline">ringback</span></h3>
<p>This will specify the audio to play to the A leg on unanswered aka (early media) calls. The following example uses the US ring tone defined in ~/vars.xml
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="ringback=${us-ring}"/&gt;
</pre>
<a name="instant_ringback" id="instant_ringback"></a><h3> <span class="mw-headline">instant_ringback</span></h3>
<p>When set, ringback will not wait for indication before sending ringback tone to calling party
</p><p>Usage:
</p>
<pre>&lt;action application="set" data="instant_ringback=true"/&gt;
</pre>
<a name="transfer_ringback" id="transfer_ringback"></a><h3> <span class="mw-headline">transfer_ringback</span></h3>
<p>This will set the ring tone for answered calls. This is any call that has been setup. One example would be the tone to play during transfer. The following example uses the French ringtone definte in ~/vars.xml
</p><p>Usage: 
</p>
<pre>&lt;action application="set" data="transfer_ringback=${fr-ring}"/&gt;
</pre>
<a name="disable_hold_2" id="disable_hold_2"></a><h3> <span class="mw-headline">disable_hold</span></h3>
<p>This is the channel variable for disable-hold.
</p><p>See <a href="http://wiki.freeswitch.org/wiki/Sofia.conf.xml#disable-hold" class="external free" title="http://wiki.freeswitch.org/wiki/Sofia.conf.xml#disable-hold" rel="nofollow">http://wiki.freeswitch.org/wiki/Sofia.conf.xml#disable-hold</a>.
</p><p>Usage: 
</p>
<pre>&lt;action application="set" data="disable_hold="true"/&gt;
</pre>
<p><br />
</p>
<a name="RTCP_Related" id="RTCP_Related"></a><h2> <span class="mw-headline">RTCP Related</span></h2>
<a name="rtcp_packet_count" id="rtcp_packet_count"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_rtcp_packet_count" title="Variable rtcp packet count"> rtcp_packet_count</a> </span></h3>
<p>Contains number of RTCP packets collected during the call.
</p><p><b>Usage:</b>
</p>
<pre>N/A
</pre>
<p><br />
</p>
<a name="rtcp_octet_count" id="rtcp_octet_count"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_rtcp_octet_count" title="Variable rtcp octet count"> rtcp_octet_count</a> </span></h3>
<p>Contains number of RTCP octets collected during the call.
</p><p><b>Usage:</b>
</p>
<pre>N/A
</pre>
<p><br />
</p>
<a name="Camp-on_related_variables" id="Camp-on_related_variables"></a><h2> <span class="mw-headline">Camp-on related variables</span></h2>
<p>Camping is used when bridging a call. It will basically park (aka camp) your channel to music on hold while it attempts to bridge the call.
</p>
<a name="campon" id="campon"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon" title="Variable campon"> campon</a> </span></h3>
<p>Controls whether camping is enabled or not.
</p><p>Default: false
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon=true"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_retries" id="campon_retries"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_retries" title="Variable campon retries"> campon_retries</a> </span></h3>
<p>Controls how many times the bridge will be retried while camping.
</p><p>Default: 100
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon=true"/&gt;
&lt;action application="set" data="campon_retries=13"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_timeout" id="campon_timeout"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_timeout" title="Variable campon timeout"> campon_timeout</a> </span></h3>
<p>This variable controls how long to attempt each bridge before timing out. It works exactly like <a href="/wiki/Variable_call_timeout" title="Variable call timeout"> call_timeout</a> but only applies to camping.
</p><p>Default: 10
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon=true"/&gt;
&lt;action application="set" data="campon_timeout=20"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_sleep" id="campon_sleep"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_sleep" title="Variable campon sleep"> campon_sleep</a> </span></h3>
<p>Controls how long to wait before starting a retry.
</p><p>Default: 10
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon=true"/&gt;
&lt;action application="set" data="campon_sleep=30"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_fallback_exten" id="campon_fallback_exten"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_fallback_exten" title="Variable campon fallback exten"> campon_fallback_exten</a> </span></h3>
<p>Controls camping during bridge app (testing needed)
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_fallback_dialplan" id="campon_fallback_dialplan"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_fallback_dialplan" title="Variable campon fallback dialplan"> campon_fallback_dialplan</a> </span></h3>
<p>Controls camping during bridge app (testing needed)
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_fallback_context" id="campon_fallback_context"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_fallback_context" title="Variable campon fallback context"> campon_fallback_context</a> </span></h3>
<p>Controls camping during bridge app (testing needed)
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_hold_music" id="campon_hold_music"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_hold_music" title="Variable campon hold music"> campon_hold_music</a> </span></h3>
<p>If you don't set the <a href="/wiki/Variable_hold_music" title="Variable hold music"> hold_music</a> variable, this variable controls hold music while camping.
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon=true"/&gt;
&lt;action application="set" data="campon_hold_music=/data/campmusic/RelaxingCampSounds.wav"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_stop_key" id="campon_stop_key"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_stop_key" title="Variable campon stop key"> campon_stop_key</a> </span></h3>
<p>DTMF digit that breaks the campon loop and skips directly to fallback extension 
</p><p>Default: none
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon=true"/&gt;
&lt;action application="set" data="campon_stop_key=1"/&gt;
&lt;action application="set" data="campon_announce_sound=press_one_to_stop.wav"/&gt;
&lt;action application="set" data="campon_fallback_exten=1000"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="campon_announce_sound" id="campon_announce_sound"></a><h3> <span class="mw-headline"> <a href="/wiki/Variable_campon_announce_sound" title="Variable campon announce sound"> campon_announce_sound</a> </span></h3>
<p>File to play back after the first bridge fails (rg to announce what key to press to skip to fallback extension)
</p><p>Default: none
</p><p><br />
<b>Usage:</b>
</p>
<pre>&lt;action application="set" data="campon=true"/&gt;
&lt;action application="set" data="campon_stop_key=1"/&gt;
&lt;action application="set" data="campon_announce_sound=press_one_to_stop.wav"/&gt;
&lt;action application="bridge" data="sofia/gateway/myprovider/5551231234"/&gt;
</pre>
<p><br />
</p>
<a name="Answer_confirmation_variables" id="Answer_confirmation_variables"></a><h2> <span class="mw-headline">Answer confirmation variables</span></h2>
<a name="group_confirm_file" id="group_confirm_file"></a><h3> <span class="mw-headline">group_confirm_file</span></h3>
<p>This variable is used together with group_confirm_key.  In group_confirm_file, you specify the wav file you want to play when the called party picks up the call.  In the group_confirm_key variable, you define the DTMF that the called party should send to FS to bridge the call.  If a wrong DTMF or no DTMF is sent, the called won't be bridged and the wav file will be repeated.  
</p>
<pre>
&lt;action application=&quot;set&quot; data=&quot;group_confirm_file=/usr/local/freeswitch/sounds/take_call_question.wav&quot; /&gt;
&lt;action application=&quot;set&quot; data=&quot;group_confirm_key=1&quot; /&gt;
</pre>
<p>Through this is the standard usage of these variables (group_confirm_key and group_confirm_file), they can be used in a more flexible manner. Please see <a href="/wiki/Freeswitch_IVR_Originate#Answer_confirmation" title="Freeswitch IVR Originate">Freeswitch_IVR_Originate#Answer_confirmation</a>.
</p>
<a name="group_confirm_key" id="group_confirm_key"></a><h3> <span class="mw-headline">group_confirm_key</span></h3>
<p>see group_confirm_file
</p>
<a name="group_confirm_cancel_timeout" id="group_confirm_cancel_timeout"></a><h3> <span class="mw-headline">group_confirm_cancel_timeout</span></h3>
<p>If set, cancels a leg timeout after the call is answered.
</p><p>More detail:
</p><p>When using group confirm, a call passes through three phases:
</p>
<ol><li>Call is ringing
</li><li>Call is answered, waiting to be confirmed
</li><li>Call is confirmed and bridged
</li></ol>
<p>Normally, a timeout on the leg will apply to phases 1 and 2.
</p><p>However, if you do
</p>
<pre> &lt;action application="set" data="group_confirm_cancel_timeout=1"/&gt;
</pre>
<p>then the timeout will only apply to phase 1. So, once the phase 1 is crossed, leg_timeout counter stops.
</p><p>See Also:
</p>
<ul><li> <a href="/wiki/Channel_Variables#group_confirm_file" title="Channel Variables">group_confirm_file</a>
</li><li> <a href="/wiki/Channel_Variables#leg_timeout" title="Channel Variables">leg_timeout</a>
</li></ul>
<a name="Voicemail_Related_Variables" id="Voicemail_Related_Variables"></a><h2> <span class="mw-headline">Voicemail Related Variables</span></h2>
<a name="voicemail_alternate_greet_id" id="voicemail_alternate_greet_id"></a><h3> <span class="mw-headline"><a href="/wiki/Mod_voicemail#vm-alternate-greet-id_.28voicemail_alternate_greet_id.29" title="Mod voicemail">voicemail_alternate_greet_id</a></span></h3>
<a name="voicemail_greeting_number" id="voicemail_greeting_number"></a><h3> <span class="mw-headline"><a href="/wiki/Mod_voicemail#voicemail_greeting_number" title="Mod voicemail">voicemail_greeting_number</a></span></h3>
<a name="vm_message_ext" id="vm_message_ext"></a><h3> <span class="mw-headline"><a href="/wiki/Mod_voicemail#vm_message_ext" title="Mod voicemail">vm_message_ext</a></span></h3>
<a name="vm_cc" id="vm_cc"></a><h3> <span class="mw-headline"><a href="/wiki/Mod_voicemail#vm_cc" title="Mod voicemail">vm_cc</a></span></h3>
<a name="skip_greeting" id="skip_greeting"></a><h3> <span class="mw-headline"><a href="/wiki/Mod_voicemail#skip_greeting" title="Mod voicemail">skip_greeting</a></span></h3>
<a name="skip_instructions" id="skip_instructions"></a><h3> <span class="mw-headline"><a href="/wiki/Mod_voicemail#skip_instructions" title="Mod voicemail">skip_instructions</a></span></h3>
<a name="voicemail_authorized" id="voicemail_authorized"></a><h3> <span class="mw-headline"><a href="/wiki/Mod_voicemail#voicemail_authorized" title="Mod voicemail">voicemail_authorized</a></span></h3>
<a name="Events" id="Events"></a><h2> <span class="mw-headline">Events</span></h2>
<a name="fire_asr_events" id="fire_asr_events"></a><h3> <span class="mw-headline">fire_asr_events</span></h3>
<p>If set, fire an event when speech is detected.
</p>
<a name="System_Related_Variables" id="System_Related_Variables"></a><h2> <span class="mw-headline">System Related Variables</span></h2>
<a name="base_dir" id="base_dir"></a><h3> <span class="mw-headline">base_dir</span></h3>
<p>This variable is used to leverage the installation directory in order to avoid hard-coding it the xml.  
</p><p><b>Usage:</b>
</p>
<pre>
&lt;action application=&quot;system&quot; data=&quot;$${base_dir}/scripts/my_script.sh&quot;/&gt;
</pre>
<p><br />
</p>
<a name="OpenZap_Related_Variables" id="OpenZap_Related_Variables"></a><h2> <span class="mw-headline"><a href="/wiki/OpenZap" title="OpenZap" class="mw-redirect">OpenZap</a> Related Variables</span></h2>
<a name="openzap_span_number" id="openzap_span_number"></a><h3> <span class="mw-headline">openzap_span_number</span></h3>
<p>openzap span number
</p>
<a name="openzap_chan_number" id="openzap_chan_number"></a><h3> <span class="mw-headline">openzap_chan_number</span></h3>
<p>openzap channel number
</p>



