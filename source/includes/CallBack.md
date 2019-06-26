#信息回调接口

## 回调说明

通话记录回调与任务完成回调使用不同回调地址，请提前配置。

<aside class="notice">
 请您在对接接口前，务必配置好回调地址,否则回调将无法成功。 
 </aside>

```
 通话记录回调dataType:CALL_INSTANCE_RESULT
 
 任务完成详情回调dataType:JOB_INFO_RESULT
 
```
### 回调服务器IP 
回调服务器IP ： 120.55.46.3
请确保回调服务器IP已加入白名单中，否则无法完成回调。

### 回调时间

最多回调27次，回调总时常共26小时46分，前16次回调间隔时间如下，超过16次，每次重试间隔2小时。
  
第几次重试 | 与上次重试的间隔时间 | 第几次重试    | 与上次重试的间隔时间
------    | ------            | ------        |  ------
     1       | 10 秒              | 9           | 7 分钟
     2       | 30 秒              | 10          | 8 分钟
     3       | 1 分钟             | 11           | 9 分钟
     4       | 2 分钟             | 12           | 10 分钟
     5       | 3 分钟             | 13           | 20 分钟
     6       | 4 分钟             | 14           | 30 分钟
     7       | 5 分钟             | 15           | 1 小时
     8       | 6 分钟             | 16           | 2 小时
  
### 回调返回
回调成功后，处理方应当返回字符串success在返回的body体中，百应才会认为回调成功，否则认为回调失败。

##通话记录回调接口

 
###功能说明：
 
 当一次通话完成后，百应机器人会自动调用回调程序向用户配置的回调地址，发送本次通话详情。
 
 
 >请求对象示例:
 
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
				"industry": "1540384412_151_1",
				"trackResult": "C级(很少)",
				"bugType": null,
				"hangUp": 1,
				"secondaryCallTime": "1970-01-01 09:00:00",
				"secondaryCallTimes": 0,
				"cost": 0,
				"callbacked": 0,
				"csStaffId": null
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
				"analyzeType": "DYNAMIC_ANALYZE_USER_LEVEL",
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
				"analyzeType": "DYNAMIC_ANALYZE_USER_LEVEL",
				"resultValueAlias": "",
				"resultLabels": [{
					"key": 200,
					"value": "无效用户"
				}],
				"resultValueNew": ""
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
 
HttpMethod : post  
Content-Type : application/json;charset=utf-8
 
 
###请求参数:
 
 参数名 | 类型  | 描述  
 --------- | ------- | ------ 
  code| String | 回调类型 |
  |||
  callInstanceId| long | 通话记录Id |
  companyId| int |公司ID|
  callUserId| int | 主叫用户ID |
  callJobId| int | 任务Id |
  customerId| int |客户Id|
  customerTelephone|String|客户手机号|
  customerName|String|客户名称|
  status| int | 电话实例状态 2：已完成 |
  finishStatus| int | 通话状态 0：已接通，1：拒绝 2：无法接通 3：主叫号码不可用 4：空号 5：关机 6：占线 7：停机 8：未接 9：主叫欠费 10：呼损 11：黑名单|
  duration| int |通话时长|
  chatRound| int | 通话轮次 |
  startTime| Date | 通话开始时间
  endTime| Date | 通话结束时间 |
  callerPhone| String | 主叫号码 |
  luyinOssUrl| String |通话录音（包含Ai和客户）|
  userLuyinOssUrl| String | 通话录音（只包含客户） |
  properties| String |通话记录携带的参数(json字符串)，包含话术变量和自定义参数，用户可以传入自己的变量，我们回调会传回给用户|
  handlePerson| String  | 话术名 |
  callType| int | 主叫号码类型 |
  callIndex| int | 通话实例索引 |
  readStatus| int | 是否已读，产品中的通话记录已读未读状态 0：未读 1：已读 |
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
  sceneInstanceResultId|long|通话记录结果Id|
  companyId|int|公司Id|
  sceneInstanceId|long|通话记录Id(对应callInstanceId)|
  resultName|String|通话记录结果类型名|
  resultValue|String|通话记录结果值|
  artificialResultValue|String|通话结果人工标注值（一般指人工标注意向等级）|
  artificialChanged|int|是否进行过人工标注修改 0:没有 1:有|
  resultDesc|String|结果描述|
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
  decisionId|int|对应决策Id,话术的节点Id|
  speaker|String|说话人 ME：用户  AI:机器人|
  content|String|说话内容|
  userMean|String|用户说话语义,客户说话内容命中的话术节点分支或知识库问题|
  userMeanDetail|String|用户说话语义详情,客户说话内容命中详情（包括命中的用户说话内容和话术节点分支或知识库分支问题）|
  aiUnknown|int|是否是ai无法应答的问题，1-是，0-否|
  answerStatus|int|回答问题状态：0-分支，1-问题，2-忽略|
  studyStatus|int|学习状态：0-未学习，1-已学习|
  startTime|Date|说话的开始时间|
  endTime|Date|说话的结束时间|
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
 
 `success`

##任务状态回调

 
###功能说明：
 
 任务运行中动态状态变更回调，包含如下状态：手动暂停，自动暂停 ，线路欠费 ，短信欠费 ，任务完成
 需另外开通和配置
 
 
 >请求对象示例:
 
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
 		}
 	},
 	"resultMsg": "执行成功",
 	"errorStackTrace": null
 }
 
  ```


###请求方法：
 
HttpMethod : post  
Content-Type : application/json;charset=utf-8
 
 
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
  breakStartTime| int |对应百应页面创建任务时的不拨打时段的开始时间，到达这个时间点后 任务将会自动暂停|
  breakEndTime| int | 对应百应页面创建任务时的不拨打时段的结束时间，到达这个时间点后 任务将会再次启动 |
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

  

 
 
###响应：
 
 `success`


##手动修改客户意向等级回调接口

 
###功能说明：
 
 当在crm端手动修改客户意向等级后，百应机器人会自动调用回调程序向用户配置的回调地址，发送本次通话详情。
   
 
 >请求对象示例:
 
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
 
HttpMethod : post  
Content-Type : application/json;charset=utf-8
 
 
###请求参数:
 
 参数名 | 类型  | 描述  
 --------- | ------- | ------ 
  sceneInstanceId| long | 任务实例id |
  taskResult| String | 任务结果分析 |
  resultName|String|客户意向等级名
  resultValue|String|客户意向等级值
  
###响应：
 
`success`
  
  
  
##呼入回调接口

###功能说明：
当一次通话完成后，百应机器人会自动调用回调程序向用户配置的回调地址，发送本次通话详情。
呼入回调数据格式与外呼格式保持高度一致，仅个别字段名称有所变更,  http://api.byrobot.cn/doc/v2/#3e45815d37
 
 >请求对象示例:
  
   ```
 {
     "code": 200,
     "data": {
         "dataType": "INBOUND_CALL_INSTANCE_RESULT",
         "data": {
             "sceneInstance": {
                 "inboundInstanceId": 1091,
                 "companyId": 1,
                 "callJobId": 98,
                 "customerId": 22142595,
                 "customerTelephone": "1010",
                 "customerName": "未知呼入客户",
                 "status": 2,
                 "finishStatus": 0,
                 "duration": 27,
                 "chatRound": 3,
                 "startTime": "2019-01-24 15:27:39",
                 "endTime": "2019-01-24 15:28:09",
                 "calleePhone": "057126881788",
                 "luyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/InboundRobotCommunicate/1091/20190124-152809_1010.wav",
                 "userLuyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/InboundRobotCommunicate/1091_user.wav",
                 "properties": "{}",
                 "readStatus": null,
                 "robotDefId": 1155,
                 "sceneDefId": 1165,
                 "sceneRecordId": 1149,
                 "transferStatus": null,
                 "transferInfo": null,
                 "userLevel": null,
                 "hangUp": 1,
                 "callbacked": null,
                 "propertiesMap": {
                     "客户名称": "未知呼入客户",
                     "联系方式": "1010"
                 }
             },
             "taskResult": [
                 {
                     "sceneInstanceResultId": 459,
                     "companyId": 1,
                     "callJobId": null,
                     "sceneInstanceId": 1091,
                     "resultName": "客户意向等级",
                     "resultValue": "B级(一般)",
                     "artificialResultValue": "B级(一般)",
                     "artificialChanged": false,
                     "resultDesc": "拒绝次数 <= 1 次 并且 命中业务问题 >= 1",
                     "analyzeType": "DYNAMIC_ANALYZE_USER_LEVEL",
                     "resultValueAlias": "B",
                     "resultLabels": null,
                     "resultValueNew": "B级(可能有意向)"
                 },
                 {
                     "sceneInstanceResultId": 460,
                     "companyId": 1,
                     "callJobId": null,
                     "sceneInstanceId": 1091,
                     "resultName": "客户关注点",
                     "resultValue": "位置",
                     "artificialResultValue": "位置",
                     "artificialChanged": false,
                     "resultDesc": null,
                     "analyzeType": "DYNAMIC_ANALYZE_USER_LEVEL",
                     "resultValueAlias": null,
                     "resultLabels": null,
                     "resultValueNew": null
                 },
                 {
                     "sceneInstanceResultId": 461,
                     "companyId": 1,
                     "callJobId": null,
                     "sceneInstanceId": 1091,
                     "resultName": "客户标签",
                     "resultValue": "[7,8,9]",
                     "artificialResultValue": null,
                     "artificialChanged": false,
                     "resultDesc": null,
                     "analyzeType": "DYNAMIC_ANALYZE_USER_LEVEL",
                     "resultValueAlias": null,
                     "resultLabels": [],
                     "resultValueNew": null
                 }
             ],
             "phoneLog": {
                 "phoneLogs": [
                     {
                         "sceneInstanceLogId": 1693,
                         "sceneInstanceId": 1091,
                         "companyId": 1,
                         "robotDefId": 1155,
                         "decisionId": 502993,
                         "speaker": "AI",
                         "content": "哎，您好，拱墅区 中大银泰城边上有个首付50万左右的精装公寓你考虑吗？",
                         "userMean": "",
                         "userMeanDetail": null,
                         "aiUnknown": false,
                         "answerStatus": null,
                         "studyStatus": null,
                         "startTime": 0,
                         "endTime": 0,
                         "knowledgeBaseId": null,
                         "correctionContent": null
                     },
                     {
                         "sceneInstanceLogId": 1694,
                         "sceneInstanceId": 1091,
                         "companyId": 1,
                         "robotDefId": 1155,
                         "decisionId": 502993,
                         "speaker": "ME",
                         "content": "呃，不考虑",
                         "userMean": "拒绝",
                         "userMeanDetail": "[{\"score\":-1,\"answer\":\"拒绝\",\"ask\":\"不考虑\",\"knowledgeBaseId\":33230}]",
                         "aiUnknown": false,
                         "answerStatus": 1,
                         "studyStatus": null,
                         "startTime": 6830,
                         "endTime": 7950,
                         "knowledgeBaseId": null,
                         "correctionContent": null
                     }
                 ],
                 "luyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/InboundRobotCommunicate/1091/20190124-152809_1010.wav"
             },
             "sign": null,
             "dateTime": "Thu, 24 Jan 2019 07:28:09 GMT"
         }
     },
     "resultMsg": "成功",
     "errorStackTrace": null
 }
   ```  

###请求方法：
  
HttpMethod : post
Content-Type : application/json;charset=utf-8
  
### 请求参数:
1.dataType: "INBOUND_CALL_INSTANCE_RESULT" (固定，标识是呼入回调),
2.sceneInstance： (通话记录相关元数据) 
   

参数名 | 类型 | 描述 
 --------- | ------- |------
inboundInstanceId|long|通话记录id
companyId|int|公司ID
customerId|long|客户Id
customerTelephone|String|客户手机号
customerName|String|客户名称
status|int|电话实例状态 0：未开始 1：进行中 2：已完成
finishStatus|int|通话状态 0：已接通，1：拒绝 2：无法接通 3：主叫号码不可用 4：空号 5：关机 6：占线 7：停机 8：未接 9：主叫欠费 10：呼损 11：黑名单
duration|int|通话时长
chatRound|int|通话轮次
startTime|Date|通话开始时间
endTime|Date|通话结束时间
calleePhone|String|被叫号码
luyinOssUrl|String|通话录音（包含Ai和客户）
userLuyinOssUrl|String|通话录音（只包含客户）
robotDefId|int|话术机器人Id
sceneDefId|int|话术场景Id
sceneRecordId|int|话术场景录音Id
transferStatus|int|转人工状态:0-无转接,1-成功,2-失败
transferInfo|String|转人工详情
callbacked|int|是否回调
hangUp|int|挂机人 0：AI 1：用户


 3.taskResult（通话分析的结果）
 
 参数名 | 类型 | 描述 
  --------- | ------- |------
sceneInstanceResultId|long|通话记录结果Id
sceneInstanceId|long|通话记录Id(对应inboundInstanceId)
resultName|String|通话记录结果类型名
resultValue|String|通话记录结果值
artificialResultValue|String|通话结果人工标注值（一般指人工标注意向等级）
artificialChanged|boolean|是否进行过人工标注修改
resultDesc|String|结果描述
resultValueAlias|String|分析结果别名(resultName为【客户意向等级】时标注值为意向级别 A,B,C,D,E,F)
resultLabels|List|IntegerStringBO对象中存储一个int类型参数，一个String类型参数，resultName为【客户标签】时存储客户标签


 4.phoneLog（对话详情）
 
 参数名 | 类型 | 描述 
--------- | ------- |------
sceneInstanceLogId|long|通话记录日志Id
decisionId|int|对应决策Id
speaker|String|说话人 ME：用户 AI:机器人
content|String|说话内容
userMean|String|用户说话语义,客户说话内容命中的话术节点分支或知识库问题
userMeanDetail|String|用户说话语义详情,客户说话内容命中详情（包括命中的用户说话内容和话术节点分支或知识库分支问题）
aiUnknown|int|是否是ai无法应答的问题，1-是，0-否
answerStatus|int|回答问题状态：0-分支，1-问题，2-忽略，表示命中流程分支或者知识库问题
studyStatus|int|学习状态：0-未学习，1-已学习，在问题学习板块里面的问题学习状态（默认为空）
startTime|Date|说话的开始时间,本句话在录音中的开始时间
endTime|Date|说话的结束时间,本句话在录音中的结束时间
correctionContent|String|通话记录纠错内容，通话记录中的人工纠错功能的纠错内容
luyinOssUrl|String|通话记录录音
sign|String|回调签名（需联系开通）
dateTime|String|GMT格式日期（签名计算-需联系开通）

###响应：
 
`success`

##查询回调失败记录

###功能说明：
通过接口可以查询时间段内调用用户回调接口失败的记录

>返回对象示例:
 
  ```
{
    "code":200,
    "data":{
        "pageNum":1,
        "pageSize":1000,
        "total":5,
        "pages":1,
        "list":[
            {
                "customerTelephone":"13777482716",
                "callInstanceId":13,
                "callJobId":9,
                "callerTime":"2019-03-20 11:22:33"
            },
            {
                "customerTelephone":"13777482716",
                "callInstanceId":12,
                "callJobId":9,
                "callerTime":"2019-03-20 11:22:33"
            },
            {
                "customerTelephone":"13777482716",
                "callInstanceId":11,
                "callJobId":9,
                "callerTime":"2019-03-20 11:22:33"
            },
            {
                "customerTelephone":"18767114326",
                "callInstanceId":101705174,
                "callJobId":29463,
                "callerTime":"2019-03-20 17:20:58"
            },
            {
                "customerTelephone":"18767114326",
                "callInstanceId":101705181,
                "callJobId":29465,
                "callerTime":"2019-03-20 17:28:57"
            }
        ]
    },
    "resultMsg":"查询成功",
    "errorStackTrace":null,
    "requestId":null
}
 
  ```

###请求：

URL：http://api.byrobot.cn/openapi/v1/callBack/queryUnCallBack

###请求方法：

GET

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |----------
 companyId| int| 是 | 公司Id| 1 |
 callJobId| int| 否 | 任务ID，如果不传该字段查询该公司下所有回调失败的记录 | 1 |
 dataType| int| 是 | 回调类型， 0：呼出结果回调，1：呼入结果回调 | 0 |
 startDate| Date| 是 | 查询开始时间 | "2017-10-19" |
 endDate| Date| 是 | 查询结束时间 | "2017-10-19" |
 pageNum| int| 否 | 第几页,默认1| 1 |
 pageSize| int| 否 | 页面大小,选填,默认100，取值范围1-500| 10 |

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 pageNum| int | 当前分页数 |
 pageSize| int | 当前分页数据条数 |
 total| int | 数据总条数 |
 pages| int | 分页总数 |
 list | list | 查询结果集 |
 callJobId| int | 任务id |
 customerTelephone | String | 客户手机号 |
 callInstanceId| long | 通话记录ID |
 callerTime| time | 拨打时间 |

###响应：
 
`success`
