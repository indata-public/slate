#信息回调接口

## 回调地址说明

通话记录回调与任务完成回调使用不同回调地址，请提前配置。

```
 通话记录回调dataType:CALL_INSTANCE_RESULT
 
 任务完成详情回调dataType:JOB_INFO_RESULT
 
```

##通话记录回调接口

 
###功能说明：
 
 当一次通话完成后，百应机器人会自动调用回调程序向用户配置的回调地址，发送本次通话详情。
 
 如果本次发送由于网络等原因发送失败，机器人会自动发起二次发送。
 
 最多回调10次，每次回调时长按1分钟，2分钟，4分钟，8分钟间隔依次递增，总回调时长可达24小时。回调成功后，处理方应当返回字符串"success"在返回的body体中
  
 <aside class="notice">
 请您在对接接口前，务必配置好回调地址,否则回调将无法成功。 
 </aside>
 
 >返回对象示例:
 
  ```
{
	"code": 200,
	"data": {
		"dataType": "CALL_INSTANCE_RESULT",
		"data": {
			"sceneInstance": {
				"callInstanceId": 1,
				"companyId": 1,
				"callUserId": 1,
				"callJobId": 1,
				"customerId": 1,
				"customerTelephone": "137xxxxxxxx",
				"customerName": "2989",
				"status": 2,
				"finishStatus": 0,
				"duration": 35,
				"chatRound": 3,
				"startTime": "2019-01-12 16:09:32",
				"endTime": "2019-01-12 16:10:11",
				"callerPhone": "测试线路",
				"luyinOssUrl": "https://byrobot-prod.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/11/xxx.wav",
				"userLuyinOssUrl": "https://byrobot-prod.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/11.wav",
				"properties": "{\"csStaffId\":12,\"csStaffMobile\":\"15957182700\",\"csStaffName\":\"123\",\"duration\":20,\"failReason\":\"失败了就是失败了\",\"finishTime\":1546506273268,\"seatGroupId\":1,\"seatGroupName\":\"测试失败\",\"startTime\":1546506263268,\"succTime\":1546506283268,\"success\":false,\"transferMobile\":false,\"useEavesdrop\":false}",
				"handlePerson": "测试线路",
				"callType": 1,
				"callIndex": 0,
				"readStatus": 0,
				"jobName": "GG0112-YX NEW1",
				"robotDefId": 180,
				"sceneDefId": 192,
				"sceneRecordId": 192,
				"corpName": "{\"calledTimes\":1,\"callerId\":887,\"host\":\"byrobot-prod27\",\"ip\":\"172.16.67.198\",\"useAsr\":\"pay\"}",
				"industry": "1540384412_151_1",
				"trackResult": "C级(很少)",
				"bugType": null,
				"hangUp": 1,
				"secondaryCallTime": "1970-01-01 09:00:00",
				"secondaryCallTimes": 0,
				"cost": 0,
				"callbacked": 0,
				"csStaffId": null,
				"gmtCreate": "2019-01-12 10:48:42",
				"gmtModified": "2019-01-12 10:48:42"
			},
			"taskResult": [{
				"sceneInstanceResultId": 1117274388,
				"companyId": 151,
				"callJobId": 362574,
				"sceneInstanceId": 1540384412,
				"resultName": "客户意向等级",
				"resultValue": "C级(很少)",
				"artificialResultValue": "C级(很少)",
				"artificialChanged": null,
				"resultDesc": "命中业务问题 <= 0次 并且 肯定次数 <= 0次",
				"extra": "{\"hitUserLevelConfigExtraId\":327809,\"hitUserLevelConfigId\":6}",
				"analyzeType": "DYNAMIC_ANALYZE_USER_LEVEL",
				"gmtCreate": null,
				"gmtModified": null,
				"resultValueAlias": "C",
				"resultLabels": null,
				"resultValueNew": "C级(明确拒绝)"
			}, {
				"sceneInstanceResultId": 922147427,
				"companyId": 4880,
				"sceneInstanceId": 1223552173,
				"resultName": "客户标签",
				"resultValue": "[1]",
				"artificialResultValue": null,
				"artificialChanged": null,
				"resultDesc": null,
				"extra": null,
				"analyzeType": "DYNAMIC_ANALYZE_USER_LEVEL",
				"resultValueAlias": "",
				"resultLabels": [{
					"key": 200,
					"value": "无效用户"
				}],
				"resultValueNew": "",
				"gmtCreate": "2018-12-14 18:03:00",
				"gmtModified": "2018-12-14 18:03:00"
			}],
			"phoneLog": {
				"phoneLogs": [{
					"sceneInstanceLogId": 1156248612,
					"sceneInstanceId": 1540384412,
					"companyId": 151,
					"robotDefId": 180,
					"decisionId": 10638,
					"speaker": "AI",
					"content": "喂，您好，这里是用户测试电话",
					"userMean": "",
					"userMeanDetail": null,
					"aiUnknown": false,
					"answerStatus": null,
					"studyStatus": null,
					"startTime": 0,
					"endTime": 0,
					"gmtCreate": "2019-01-12 16:09:32",
					"gmtModified": "2019-01-12 16:09:32",
					"knowledgeBaseId": null,
					"correctionContent": null
				}, {
					"sceneInstanceLogId": 1156249713,
					"sceneInstanceId": 1540384412,
					"companyId": 151,
					"robotDefId": 180,
					"decisionId": 10638,
					"speaker": "ME",
					"content": "有什么游戏呀？",
					"userMean": "游戏",
					"userMeanDetail": "[{\"score\":-1,\"answer\":\"游戏\",\"ask\":\"什么游戏\",\"knowledgeBaseId\":5061}]",
					"aiUnknown": false,
					"answerStatus": 1,
					"studyStatus": null,
					"startTime": 8350,
					"endTime": 10570,
					"gmtCreate": "2019-01-12 16:09:44",
					"gmtModified": "2019-01-12 16:09:44",
					"knowledgeBaseId": null,
					"correctionContent": null
				}],
				"luyinOssUrl": "https://byrobot-prod.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/1540384412/20190112-161011_13733105333.wav"
			},
			"jobFinished": false,
			"sign": null,
			"dateTime": "Thu Oct 16 07:13:48 GMT 2014"
		}
	},
	"resultMsg": "成功",
	"errorStackTrace": null
}
 
  ```


###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型  | 描述  
 --------- | ------- | ------ 
  code| String | 回调类型 |
  |||
  callInstanceId| int | 通话记录Id |
  companyId| int |公司ID|
  callUserId| int | 主叫用户ID |
  callJobId| int | 任务Id |
  customerId| int |客户Id|
  customerTelephone|String|客户手机号|
  customerName|String|客户名称|
  status| int | 电话实例状态 0：未开始 1：进行中 2：已完成 3：二次拨打调度中 |
  finishStatus| int | 通话状态 0：已接通，1：拒绝 2：无法接通 3：主叫号码不可用 4：空号 5：关机 6：占线 7：停机 8：未接 9：主叫欠费 10：呼损 11：黑名单|
  duration| int |通话时长|
  chatRound| int | 通话轮次 |
  startTime| Date | 通话开始时间
  endTime| Date | 通话结束时间 |
  callerPhone| String | 主叫号码 |
  luyunOssUrl| String |通话录音（包含Ai和客户）|
  userLuyinOssUrl| String | 通话录音（只包含客户） |
  properties| String |通话记录携带的参数(json字符串)|
  handlePerson| String  | 话术名 |
  callType| int | 主叫号码类型 |
  callIndex| int | 通话实例索引 |
  readStatus| int | 是否已读 0：未读 1：已读 |
  jobName| String | 电话任务名称 |
  robotDef| int |话术机器人Id|
  sceneDefId| int |话术场景Id|
  sceneRecordId| int | 话术场景录音Id |
  industry| String | 所属行业 | 
  trackResult| String | bug追踪结果 | 
  bugType| String | 缺陷类型 | 
  hangUp| int | 挂机人 0：AI 1：用户 | 
  secondaryCallTime| Date |二次拨打时间| 
  secondaryCallTimes| int | 二次拨打次数 为0后不进行外呼 |
  cost| int|通话费用，单位（分）|
  callbacked|int|是否回调完成 0：未回调 1：已回调|
  csStaffId|int|人工坐席Id|
  gmtCreate|Date|创建时间|
  gmtModified|Date|修改时间|
   |||
  sceneInstanceResultId|int|通话记录结果Id|
  companyId|int|公司Id|
  sceneInstanceId|int|通话记录Id(对应callInstanceId)|
  resultName|String|通话记录结果类型名|
  resultValue|String|通话记录结果值|
  artificialResultValue|String|通话结果人工标注值（一般指人工标注意向等级）|
  artificialChanged|int|是否进行过人工标注修改 0:没有 1:有|
  resultDesc|String|结果描述|
  extra|String|额外信息|
  analyzeType|String|场景对应的结构化数据分析类型|
  resultValueAlias|String|分析结果别名(resultName为【客户意向等级】时标注值为意向级别 A,B,C,D,E,F)|
  resultLabels|List<IntegerStringBO>|IntegerStringBO对象中存储一个int类型参数，一个String类型参数，resultName为【客户标签】时存储客户标签|
  resultValueNew|String|客户意向等级的表述（文案与crm对应）|
  gmtCreate|Date|创建时间|
  gmtModified|Date|修改时间|
  |||
  sceneInstanceLogId|Long|通话记录日志Id|
  sceneInstanceId|Long|通话记录Id（对应callInstanceId）|
  companyId|int|公司Id|
  robotDefId|int|话术机器人Id|
  decisionId|int|对应决策Id|
  speaker|String|说话人 ME：用户  AI:机器人|
  content|String|说话内容|
  userMean|String|用户说话语义|
  userMeanDetail|String|用户说话语义详情|
  aiUnknown|int|是否是ai无法应答的问题，1-是，0-否|
  answerStatus|int|回答问题状态：0-分支，1-问题|
  studyStatus|int|学习状态：0-未学习，1-已学习|
  startTime|int|说话的开始时间|
  endTime|int|说话的结束时间|
  gmtCreate|Date|创建时间|
  gmtModified|Date|修改时间|
  knowledgeBaseId|int|知识点ID|
  correctionContent|String|通话记录纠错内容|
  |||
  luyinOssUrl|String|通话记录录音|
  |||
  jobFinished|boolean|任务是否已完成|
  sign|String|回调签名（需联系开通）|
  dateTime|String|GMT格式日期（签名计算-需联系开通）|
  
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 |
  resultMsg| String | 响应说明 |

##任务状态回调

 
###功能说明：
 
 任务运行中动态状态变更回调，包含如下状态：手动暂停，自动暂停 ，线路欠费 ，短信欠费 ，任务完成
 需另外开通和配置
 
 如果本次发送由于网络等原因发送失败，机器人会自动发起二次发送。
 
 最多回调10次，每次回调时长按1分钟，2分钟，4分钟，8分钟间隔依次递增，总回调时长可达24小时。回调成功后，处理方应当返回字符串success在返回的body体中
  
 <aside class="notice">
 请您在对接接口前，务必配置好回调地址。否则回调将无法成功。
 </aside>
 
 >返回对象示例:
 
  ```
 {
 	"code": 200,
 	"data": {
 		"dataType": "JOB_INFO_RESULT",
 		"data": {
 			"callJobId": 535,
 			"companyId": 243,
 			"jobName": "测试-问题学习",
 			"jobType": 2,
 			"startDate": "2018-04-25",
 			"endDate": "2018-04-25",
 			"workingStartTime": "09:00:00",
 			"workingEndTime": "20:00:00",
 			"breakStartTime": null,
 			"breakEndTime": null,
 			"status": 2,
 			"callType": 1,
 			"robotDefId": 278,
 			"sceneDefId": 283,
 			"sceneRecordId": 280,
 			"remark": "",
 			"smsType": 0,
 			"smsCondition": null,
 			"smsTemplateId": null,
 			"userId": 241,
 			"userName": "步婉",
 			"ip": "172.16.67.104",
 			"hostName": "byrobot-daily",
 			"version": 1,
 			"secondaryStartTime": "09:00:00",
 			"jobIsDelete": false,
 			"gmtCreate": "2018-04-25 11:11:45",
 			"gmtModified": "2018-04-25 11:17:19"
 		}
 	},
 	"resultMsg": "执行成功",
 	"errorStackTrace": null
 }
 
  ```


###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型  | 描述  
 --------- | ------- | ------ 
  dataType| String | 回调数据类型 |
  callJobId| List | 外呼任务Id |
  companyId| int | 公司id |
  jobName| String |任务名称|
  jobType| int | 任务类型：1-定时，2-手动 |
  startDate| String | 任务开始时间 |
  endDate| String |任务结束时间|
  workingStartTime| String | 可拨打起始时间 |
  workingEndTime| String | 可拨打结束时间 |
  breakStartTime| int |午休起始时间|
  breakEndTime| int | 午休结束时间 |
  status| String | 状态, 0:未开始,1:进行中,2:已完成,3:调度中,4:手动暂停,5:自动暂停,6:已终止,7:排队中,8:AI到期,9:账户欠费 |
  callType| int | 主叫号码类型:0-手机号,1-固话,2-无主叫 |
  robotDefId| int |关联的机器人id|
  sceneDefId| int | 场景id |
  sceneRecordId| int |关联的录音id|
  remark| String  | 备注 |
  smsType| int | 是否发送挂机短信：0-否，1-是 |
  smsCondition| String | 发送挂机短信条件，json格式 |
  smsTemplateId| String | 发送挂机短信的模板 |
  userId| int | 创建人id |
  userName| String | 创建人名称 |
  ip| int |任务执行IP|
  hostName| int |任务执行主机|
  version| int | 锁版本号 |
  secondaryStartTime| String | 二次启动job的时间 | 
  jobIsDelete| Boolean | job是否已经删除 false：没有删除 true：已经删除 | 

  

 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |



##手动修改客户意向等级回调接口

 
###功能说明：
 
 当在crm端手动修改客户意向等级后，百应机器人会自动调用回调程序向用户配置的回调地址，发送本次通话详情。
   
 <aside class="notice">
 请您在对接接口前，务必配置好回调地址,否则回调将无法成功。 
 </aside>
 
 >返回对象示例:
 
  ```
{
	"code": 200,
	"data": {
		"dataType": "CALL_INSTANCE_RESULT",
		"data": {
			"taskResult": [{
				"companyId": 241,
				"sceneInstanceId": 2016,
				"resultName": "客户意向等级",
				"resultValue": "B"
			}]
		}
	},
	"resultMsg": "成功",
	"errorStackTrace": null
}
 
  ```


###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型  | 描述  
 --------- | ------- | ------ 
  sceneInstanceId| int | 任务实例id |
  taskResult| String | 任务结果分析 |
  resultName|String|客户意向等级名
  resultValue|String|客户意向等级值
  

 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |
