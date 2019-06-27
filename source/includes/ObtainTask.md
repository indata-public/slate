#任务信息查询接口

##获取任务列表接口

###功能说明：

通过此接口可以获取指定公司的任务列表

>返回对象示例：

```
{
    "code": 200,
    "data": {
        "pageNum": 2, 
        "pageSize": 2, 
        "size": 2,
        "total": 46, 
        "pages": 23,
        "list": [
            {
                "callJobId": 66, 
                "jobName": "测试任务", 
                "jobType": 2, 
                "startDate": "2017-10-25", 
                "workingStartTime": "09:00:00", 
                "workingEndTime": "21:00:00", 
                "status": 2, 
                "sceneDefId": 1, 
                "remark": "", 
                "totalCount": null, 
                "doneCount": null, 
                "calledCount": null, 
                "rejectedCount": null, 
                "unavailableCount": null,
                "fromUnavailableCount": null,
                "callPhones": null 
            },
            {
                "callJobId": 64,
                "jobName": "测试任务2",
                "jobType": 2,
                "startDate": "2017-10-25",
                "workingStartTime": "09:00:00",
                "workingEndTime": "21:00:00",
                "status": 2,
                "sceneDefId": 1,
                "remark": "",
                "totalCount": null,
                "doneCount": null,
                "calledCount": null,
                "rejectedCount": null,
                "unavailableCount": null,
                "fromUnavailableCount": null,
                "sceneDefName": null,
                "callPhones": null
            }
        ]
    },
    "resultMsg": "操作成功",
    "errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/task/getTasks

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |----------
 companyId| int| 是 | 公司Id| 1 |
 taskName| String| 否 |任务名称| 测试API任务 |
 createDate| String| 否 |创建时间 | "2017-10-19" |
 status| int| 否 | 任务状态枚举| 1 |
 needAll| boolean| 否 |  true:返回所有Job信息包含已打标删除的Job信息，false：只返回未打标删除的Job信息，默认false|false|
 pageNum| int| 否 | 第几页,默认1| 1 |
 pageSize| int| 否 | 页面大小,选填,默认10,最大100,建议不要太大| 10 |



###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 pageNum| int | 当前分页数 |
 pageSize| int | 当前分页数据条数 |
 total| int | 数据总条数 |
 pages| int | 分页总数 |
 callJobId| int | 任务id |
 jobName| String | 任务名称 |
 jobType| int | 任务类型，1-定时，2-手动 |
 startDate| String | 任务开始时间 |
 workingStartTime| String | 可拨打开始时间 |
 workingEndTime| String | 可拨打结束时间 |
 breakStartTime| String | 暂时停止开始时间,对应百应页面创建任务时的不拨打时段的开始时间，到达这个时间点后 任务将会自动暂停 |
 breakEndTime| String | 暂时停止结束时间,对应百应页面创建任务时的不拨打时段的结束时间，到达这个时间点后 任务将会再次启动 |
 status| int | 任务状态枚举|
 remark| String  | 任务注释 |
 totalCount| int | 任务拨打的号码总数 |
 doneCount| int | 任务已完成拨打的号码总数 |
 calledCount| int | 任务已完成呼通的号码总数 |
 rejectedCount| int | 任务呼叫被拒接的号码总数 |
 unavailableCount| int | 任务呼叫无法接通的号码总数 |
 fromUnavailableCount| int | 任务主叫号码不可用的号码总数 |
 callPhones| List | 主叫电话号码列表，格式和getPhones返回结果相同 |
 resultMsg| String | 响应说明 |

##获取任务详情接口

###功能说明：

通过此接口可以获取指定任务的详细信息

>返回对象示例：

```
{
    "code": 200,
    "data": {
        "callJobId": 19, 
        "jobName": "testJob", 
        "jobType": 2, 
        "startDate": "2017-10-19", 
        "workingStartTime": "08:00:00", 
        "workingEndTime": "22:00:00", 
        "status": 2, 
        "sceneDefId": 1, 
        "remark": "testJobx", 
        "totalCount": 2, 
        "doneCount": 2, 
        "calledCount": 0, 
        "rejectedCount": 0, 
        "unavailableCount": 0, 
        "fromUnavailableCount": 2, 
        "robotDefName": "产品电销", 
        "sceneDefName": "金融催缴", 
        "sceneRecordName": "房产电销优化版(张飞)", 
        "durationStat": [
            {
                "name": "<10s", 
                "value": 22
            }
        ],
        "chatRoundStat": [
            {
                "name": "0-9次", 
                "value": 22
            }
        ],
        "resultDefs": [
            {
                "name": "催缴结果", 
                "values": [
                    "成功",
                    "不成功"
                ]
            }
        ],
        "callPhones": [ 
            {
                "jobPhoneId": 26,
                "userPhoneId": 1,
                "callJobId": 19,
                "phone": "13333333333",
                "phoneName": "sim1",
            },
            {
                "jobPhoneId": 27,
                "userPhoneId": 2,
                "callJobId": 19,
                "phone": "18888888888",
                "phoneName": "sim2",
            }
        ],
        "extraStat": {
           "客户意向等级": [ 
               {
                   "name": "较强",
                   "value": 1
               }
           ],
           "客户关注点": [
               {
                   "name": "位置",
                   "value": 1
               },
               {
                   "name": "其他楼盘",
                   "value": 1
               },
               {
                   "name": "商业配套",
                   "value": 1
               },
               {
                   "name": "户型",
                   "value": 1
               },
               {
                   "name": "环境",
                   "value": 1
               },
               {
                   "name": "能否贷款",
                   "value": 1
               },
               {
                   "name": "询问价格",
                   "value": 1
               }
           ]
       }
    },
    "resultMsg": "操作成功",
    "errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/task/getTaskDetail

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |----------
 companyId| int| 是 | 公司Id| 1 |
 taskId| int| 否 |任务Id| 21 |
 

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 callJobId| int | 任务id |
 jobName| String | 任务名称 |
 jobType| int | 任务类型，1-定时，2-手动 |
 startDate| String | 任务开始时间 |
 workingStartTime| String | 可拨打开始时间 |
 workingEndTime| String | 可拨打结束时间 |
 breakStartTime| String | 暂时停止开始时间 |
 breakEndTime| String | 暂时停止结束时间 |
 status| int | 任务状态枚举 |
 remark| String  | 任务注释 |
 totalCount| int | 任务拨打的号码总数 |
 doneCount| int | 任务已完成拨打的号码总数 |
 calledCount| int | 任务已完成呼通的号码总数 |
 rejectedCount| int | 任务呼叫被拒接的号码总数 |
 unavailableCount| int | 任务呼叫无法接通的号码总数 |
 fromUnavailableCount| int | 任务主叫号码不可用的号码总数 |
 robotDefName| String | 机器人名称 |
 sceneDefName| String | 场景名称 |
 sceneRecordName| String | 录音名称 | 
 durationStat| List | 通话时长的统计信息,通话时长统计类型(小于10秒,10-50秒,1分钟-1分59秒,大于等于2分钟)| 
 chatRoundStat| List | 通话轮次的统计信息,通话轮次统计类型(0-2次,3-4次,5-6次,7-9次)| 
 resultDefs| List | 结果分析的枚举,各种类型的分析枚举(A-F级定义)| 
 callPhones| List | 主叫电话号码列表，格式和getPhones返回结果相同 |
 extraStat| List | 任务分析结果统计信息 |
 resultMsg| String | 响应说明 |
 
 durationStat（通话时长的统计信息）
  
 参数名 | 类型 | 描述 
 --------- | ------- |------
 name|String|通话时长统计类型 （小于10秒，10-50秒，1分钟-1分59秒，大于等于2分钟）|
 value|String|统计数量|
 
 chatRoundStat（通话轮次的统计信息）
   
 参数名 | 类型 | 描述 
 --------- | ------- |------
 name|String|通话轮次统计类型（0-2次，3-4次，5-6次，7-9次）|
 value|String|统计数量|
  
 callPhones（通话轮次的统计信息）
     
 参数名 | 类型 | 描述 
 --------- | ------- |------
 jobPhoneId|long | 外呼任务和主叫号码绑定表主键Id|
 userPhoneId|long | 外呼号码Id(对应获取主叫号码列表接口返回的userPhoneId)|
 callJobId|long | 任务Id|
 phone|String | 外呼号码|
 phoneName|String | 外呼号码名|

 
##获取已经完成任务电话号码接口
 
###功能说明：
 
 通过此接口可以获取指定任务中所有已经完成的电话号码
 
 >入参JSON示例
 
 ```
 
{
	"callJobId" : 62, 
	"durationLeft" : 0, 
	"durationRight" : 100, 
	"chatRoundLeft":0, 
	"chatRoundRight":10, 
	"finishStatus" : 1, 
	"pageNum": 1,    
	"pageSize": 10,    
	"resultQueryList" : [ 
		{
			"name" : "客户意向等级",
			"value" : "A级(较强)"
		}
	]
}
 
 ```
 
 >返回对象示例：
 
 ```
 {
     "code": 200,
     "data": {
         "pageNum": 1,
         "pageSize": 2,
         "size": 2,
         "total": 2,
         "pages": 1,
         "list": [
             {
                 "callInstanceId": 493, 
                 "sceneDefId": 1, 
                 "callJobId": 62, 
                 "customerTelephone": "1008", 
                 "customerName": "测试02",  
                 "status": 2, 
                 "finishStatus": 0,
                 "duration": "27秒", 
                 "chatRound": 0, 
                 "startTime": "2017-10-25 11:32:54", 
                 "endTime": "2017-10-25 11:33:22", 
                 "callerPhone": "15868457106", 
                 "luyinOssUrl": "https://jingrobot-dev.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/493.mp3", 
                 "secondaryCallTime": "1970-01-01 11:18:13", 
                 "secondaryCallTimes": 0, 
                 "jobName": "电话任务", 
                 "resultList": [ 
                     {
                         "name": "催缴结果",
                         "value": "成功"
                     }
                 ]
             },
             {
                 "callInstanceId": 489,
                 "sceneDefId": 1,
                 "callJobId": 62,
                 "customerTelephone": "17751279857",
                 "customerName": "不弃",
                 "status": 2,
                 "finishStatus": 0,
                 "duration": "11秒",
                 "chatRound": 0,
                 "startTime": "2017-10-25 11:17:06",
                 "endTime": "2017-10-25 11:17:18",
                 "callerPhone": "15868457106",
                 "luyinOssUrl": "https://jingrobot-dev.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/489.mp3",
                 "secondaryCallTime": "1970-01-01 10:59:23",
                 "secondaryCallTimes": 1,
                 "jobName": "电话任务",
                 "resultList": [
                     {
                         "name": "催缴结果",
                         "value": "成功"
                     }
                 ]
             }
         ]
     },
     "resultMsg": "操作成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/queryDoneTaskPhones
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  callJobId| int| 是 | 任务id| 1 |
  durationLeft| int| 否 |通话时长左值| 0 |
  durationRight| int| 否 |通话时长右值| 100 |
  chatRoundLeft| int| 否 |通话轮次左值| 21 |
  chatRoundRight| int| 否 |通话时长右值| 21 |
  finishStatus| int| 否 |通话实例已完成状态枚举| 1 |
  pageNum| int| 否 |第几页(默认为1)| 1 |
  pageSize| int| 否 |显示数量/页（默认为10），取值1-50| 10 |
  resultQueryList| List| 否 |支持按分析结果作为条件| 10 |
  
  
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  pageNum| int | 第几页 |
  pageSize| int | 每页页面条数 |
  total| int | 数据总条数 |
  pages| int | 页面总数 |
  callInstanceId| long | 通话记录Id |
  sceneDefId| int | 场景id |
  callJobId| int |任务id|
  customerTelephone| String | 被叫客户电话号码 |
  customerName| String | 被叫客户名称 |
  status| String | 任务状态, 0: 未开始，1: 进行中，2: 已完成，3: 二次拨打调度中 |
  finishStatus| String | 通话实例已完成状态枚举|
  duration| int  | 通话时长 |
  chatRound| int | 通话轮次 |
  startTime| String | 开始拨打时间 |
  endTime| String | 结束拨打时间 |
  callerPhone| String | 主叫电话 |
  luyinOssUrl| int | 通话录音（包含用户录音和Ai语音） |
  secondaryCallTime| List | 通话时长的统计信息 | 
  secondaryCallTimes| List | 重试拨打次数 | 
  jobName| List | 任务名称 | 
  resultList| List | 通话分析结果信息 |
  resultMsg| String | 响应说明 |
  
  resultList（通话轮次的统计信息）
       
  参数名 | 类型 | 描述 
  --------- | ------- |------
  name|String|客户意向等级，客户标签等|
  value|String|A级(有明确意向) 等|
  
  
##获取任务未开始的电话列表
 
###功能说明：
 
 通过此接口可以获取任务中还未开始外呼的外呼数据
 查询限制：此查询接口每页不能超过50条
 
 >入参JSON示例
 
 ```
 
{
	"pageNum" : 1, 
	"pageSize" : 20,
	"taskId" : 21767
}
 
 ```
 
 >返回对象示例：
 
 ```
 {
     "code": 200,
     "data": {
         "pageNum": 1,
         "pageSize": 50,
         "list": [
             {
                 "callInstanceId": 493, 
                 "customerName": 测试公司客户1, 
                 "customerTelephone": 1590000xxxx, 
                 "status": 0, 
                 "startTime": 2018-01-01 15:34:20,  
                 "callerPhone": 测试主叫, 
                 "corpName": 测试公司,
                 "calledTimes": 1
                
             },
             {
                 "callInstanceId": 494, 
                 "customerName": 测试公司客户2, 
                 "customerTelephone": 15900000xxxx, 
                 "status": 1, 
                 "startTime": 2018-01-01 15:34:20,  
                 "callerPhone": 测试主叫, 
                 "corpName": 测试公司,
                 "calledTimes":2 
             }
         ]
     },
     "resultMsg": "操作成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/notDialedCustomerList
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  pageNum| int| 否 |第几页(默认为1)| 1 |
  pageSize| int| 否 |显示数量/页（默认为10）单页最大支持50| 10 |
  taskId| int| 是 | 任务Id| 10 |
  
  
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  pageNum| int | 第几页 |
  pageSize| int | 每页页面条数 |
  total| int | 数据总条数 |
  pages| int | 页面总数 |
  callInstanceId| long | 任务实例id（每个被叫电话为一个实例,通话记录Id） |
  customerName| int | 客户名称 |
  customerTelephone| int |被叫客户电话|
  status| String | 通话状态, 0: 未开始，1: 进行中，2: 已完成，3: 二次拨打调度中 |
  startTime| String | 开始时间 |
  callerPhone| String | 主叫号码 |
  corpName| String | 公司名 |
  calledTimes| int  | 已拨打次数 |
  resultMsg| String | 响应说明 |
  errorStackTrace| String | 错误信息 |

##获取一个通话的详情接口
 
###功能说明：
 
 通过此接口可以获取指定通话的详细信息
 
 >返回对象示例：
 
 ```
 {
    "code": 200,
     "data": {
        "phoneLog": {
            "phoneLogs": [ 
                {
                    "sceneInstanceLogId": 1321,
                    "sceneInstanceId": 540, 
                    "speaker": "AI", 
                    "content": "哎，您好，等待2s 哎，您好，拱墅区 中大银泰城边上有个首付50万左右的精装公寓你考虑吗？", 
                    "userMean": null,
                    "userMeanDetail": null,
                    "aiUnknown": 1,
                    "startTime": 0,
                    "endTime": 0
                },
                {
                    "sceneInstanceLogId": 1322,
                    "sceneInstanceId": 540,
                    "speaker": "ME",
                    "content": "喂你好",
                    "userMean": "~",
                    "userMeanDetail": null,
                    "aiUnknown": 0,
                    "startTime": 300,
                    "endTime": 1145
                },
                {
                    "sceneInstanceLogId": 1323,
                    "sceneInstanceId": 540,
                    "speaker": "ME",
                    "content": "哦你好",
                    "userMean": "~",
                    "userMeanDetail": null,
                    "aiUnknown": 0,
                    "startTime": 2330,
                    "endTime": 3565
                }],
          "luyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/540/JYSYDCCHVFYYTMGJKKHJAMHARNNBWEJQ.wav" 
         },
         "sceneInstance": {
             "callInstanceId": 540, 
             "companyId": 1, 
             "callJobId": 31, 
             "customerId": 55, 
             "customerTelephone": "17751279857", 
             "customerName": "不弃", 
             "status": 2, 
             "finishStatus": 0,
             "duration": 87, 
             "chatRound": 18, 
             "startTime": "2018-01-24 20:51:53", 
             "endTime": "2018-01-24 20:53:28", 
             "callerPhone": "18072749353", 
             "luyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/540/JYSYDCCHVFYYTMGJKKHJAMHARNNBWEJQ.wav",
             "userLuyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/540_user.wav",
             "properties": "{}",
             "handlePerson": "房产电销优化版",
             "callType": 1,
             "readStatus": 1,
             "jobName": "buqi新的测试任务",
            "robotDefId": 6,
             "sceneDefId": 11,
             "sceneRecordId": 1,
             "trackResult": null,
             "hangUp": 0,
             "secondaryCallTime": "1970-01-01 13:00:00",
             "secondaryCallTimes": 2
         },
         "taskResult": [ 
             {
                 "sceneInstanceResultId": 188,
                 "companyId": 1,
                 "sceneInstanceId": 540,
                 "resultName": "预约时间",
                 "resultValue": "2018-01-25 08:00",
                 "resultDesc": null
             },
             {
                 "sceneInstanceResultId": 189,
                 "companyId": 1,
                 "sceneInstanceId": 540,
                 "resultName": "客户意向等级",
                 "resultValue": "A级(较强)",
                 "resultDesc": "该客户在通话过程中主动询问了产品细节，有进一步了解产品的意愿。"
             }
         ]
     },
     "resultMsg": "获取成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/phoneLogInfo
 
###请求方法：
 
 GET
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  callInstanceId| long| 是 | 任务实例id,通话记录id| 1 |  
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  phoneLog | String | 对话内容总称|
  phoneLogs| List | 对话内容 |
  sceneInstanceId| long | 任务实例id，callInstanceId |
  speaker| String |角色|
  content| String | 内容 |
  userMean| String |用户说话语义,客户说话内容命中的话术节点分支或知识库问题|
  userMeanDetail| String |用户说话语义详情,客户说话内容命中详情（包括命中的用户说话内容和话术节点分支或知识库分支问题）|
  aiUnknown| int | 是否是ai无法应答的问题，1-是，0-否 |
  luyinOssUrl| String |通话录音|
  sceneInstance | List | 通话信息|
  callInstanceId| long | 通话记录Id |
  companyId| int | 公司id |
  callJobId| int |任务id|
  customerId| int | 客户id,当前通话记录对应的客户Id |
  customerTelephone| String | 客户手机 |
  customerName| String | 客户名称 |
  finishStatus| String | 通话实例已完成状态枚举 |
  status| int |通话状态, 0: 未开始，1: 进行中，2: 已完成，3: 二次拨打调度中 |
  duration| int  | 通话时长 |
  chatRound| int | 通话轮次,AI说话次数 |
  startTime| String | 开始拨打时间 |
  endTime| String | 结束拨打时间 |
  callerPhone| String | 主叫电话 |
  luyinOssUrl| String | 通话录音（包含Ai和客户） |
  userLuyinOssUrl| String | 通话录音（只包含客户） |
  properties | String | 通话记录携带的参数,通过api导入的时候传入properties字段传入的都会从这个字段回传 |
  handlePerson | String | 处理人(一般是话术的话术名) |
  callType| int| 外呼方式，0-手机号,1-固话(默认),2-无主叫线路 |
  readStatus| int | 是否已读，产品中的通话记录已读未读状态 0：未读 1：已读 |
  robotDefId| String | 机器人id |
  sceneDefId| String | 场景ID | 
  sceneRecordId| int | 场景录音id | 
  jobName| String | 任务名称 | 
  hangUp| Integer | 挂机人, 0: AI 1: 用户 |
  taskResult| List | 任务结果分析 |
  sceneInstanceResultId | Long | 通话结果记录id |
  companyId | Integer | 公司Id |
  sceneInstanceId | Long | 通话记录Id |
  resultName | String | 分析结果名(客户意向等级,客户标签) |
  resultValue | String | 分析结果,A级(有明确意向) |
  resultDesc | String | 分析结果描述 |
  resultMsg| String | 响应说明 |
  errorStackTrace| String | 错误信息 |




