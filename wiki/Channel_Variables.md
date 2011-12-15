---
layout: default
title: {{ site.com }}
---
##通道变量

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
<span class="toctext">通道变量作用域</span></a></li>
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
#待续......
