#任务操作接口

##创建任务接口

###功能说明：

通过此接口可以创建新的任务

###注意点
####电话任务外呼时间范围 9：00-20：00
创建任务,只需设置总坐席数,由系统自动分配每个线路的坐席数量。
#####注意：
1. ai坐席数的总数可在crm界面企业账户中看到
2. 创建人默认为公司的主账号
3. 开启重拨需要的枚举：  
  2-无法接通  
  3-外呼失败  
  5-关机  
  6-占线  
  7-停机  
  9-主叫欠费  
  10-呼损  



>入参JSON示例：

```
{
    "companyId":1,
    "taskName":"测试任务",
    "taskType":2,
    "startDate":"2017-10-19",
    "workingStartTime":"08:00",
    "workingEndTime":"22:00",
    "breakStartTime":"12:00",
    "breakEndTime":"13:00",
    "userPhoneIds":[
        1
    ],
    "callType":0,
    "concurrencyQuota":1,
    "robotDefId":1,
    "smsType":1,
    "smsSendLevel":[
        "A级(有明确意向)",
        "B级(可能有意向)"
    ],
    "smsTemplateId":4198,
    "remark":"创建任务",
    "repeatCall":true,
    "defaultIntentionRule":true,
    "repeatCallRule":[
        {
            "phoneStatus":9,
            "times":1,
            "interval":5
        },
        {
            "phoneStatus":10,
            "times":1,
            "interval":5
        }
    ]
}


```

>返回对象示例：

```
{
    "code": 200,
    "data": 67, //返回刚刚创建的任务ID
    "resultMsg": "操作成功",
    "errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/task/createTask

###请求方法：

POST

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |----------
 companyId| int| 是 | 公司Id| 3811 |
 taskName| String| 是 |任务名称| 测试API任务 |
 taskType| int| 是 | 任务类型, 1-定时,2-手动| 1 |
 startDate| String| 否 | 任务开始日期（定时任务必填）| "2017-10-19"  |˙
 workingStartTime| String| 否 | 可拨打开始时间| 08:00 |
 workingEndTime| String| 否 | 可拨打结束时间| 22:00 |
 breakStartTime| String| 否 | 暂时停止开始时间,对应百应页面创建任务时的不拨打时段的开始时间,到达这个时间点后,任务将会自动暂停| 12:00 |
 breakEndTime| String| 否 | 暂时停止结束时间,对应百应页面创建任务时的不拨打时段的结束时间,到达这个时间点后,任务将会再次启动| 13:00 |
 userPhoneIds| List| 是 | 主叫号码Id,获取主叫电话列表接口可获取到| [20123] |
 robotDefId| int| 是 | 机器人id，获取机器人话术列表接口可获取| 83754 |
 callType| int| 是 | 外呼方式，对应主叫号码(线路)类型：2、1、0| 2|
 smsType| int |否| 是否发送挂机短信：0-否，1-是 |
 smsSendLevel| List<String> | 否 | 发送短信的意向等级，固定值：A级(有明确意向)、B级(可能有意向)、C级(明确拒绝)、D级(用户忙)、E级(拨打失败)、F级(无效客户)
 smsTemplateId| int | 否 | 短信模版id，只能使用不含变量的短信模版
 concurrencyQuota| int| 否 | ai坐席数,默认1,一个坐席对应一个机器人| 1 |
 phoneNum| int| 否 | 多并发数 | 1 |
 remark| String| 否 | 备注| 测试|
 repeatCall|boolean|否|是否开启重拨 默认false 关闭 |
 repeatCallRule|list|否|重拨详细规则|重拨详细规则，请看json入参
 phoneStatus|int|否|通话状态枚举,参考本文 3. 开启重拨需要的枚举|
 times|int|否|重拨次数(1-5)|
 interval|int|否|间隔时间(0-120min)|
 defaultIntentionRule|boolean|否|是否使用默认客户分配规则,传入true，不传默认false|true
 openElasticity|boolean|是否开启弹性,默认false|false|
 



###响应：

参数名 | 类型 | 描述
--------- | ------- |------
 code|int | 响应码 |
 data|int | 刚刚创建的任务ID |
 resultMsg| String | 响应说明 |

##启动任务接口

###功能说明：

通过此接口可以启动指定的任务

>返回对象示例：

```
{
    "code": 200,
    "data": null,
    "resultMsg": "启动成功",
    "errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/task/start

###请求方法：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |----------
 taskId| int| 是 | 任务Id| 13487 |


###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 resultMsg| String | 响应说明 |
 
##暂停任务接口
 
###功能说明：
 
 通过此接口可以暂停指定的任务,暂停任务后，会释放主叫号码和AI坐席
 
 >返回对象示例：
 
 ```
 {
     "code": 200,
     "data": null,
     "resultMsg": "执行成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/pause
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  taskId| int| 是 | 任务Id| 13487|
 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |

##停止任务接口
 
###功能说明：
 
 通过此接口可以停止指定的任务,停止任务后，会释放主叫号码和AI坐席
 
 >返回对象示例：
 
 ```
 {
     "code": 200,
     "data": null,
     "resultMsg": "执行成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/stop
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  taskId| int| 是 | 任务Id| 13487 |
 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |
  
##删除任务
  
###功能说明：
  
通过调用此接口可以删除任务信息，删除任务后，会释放主叫号码和AI坐席
>入参JSON示例

```
{
  "taskId": "13487"
}
```
>返回对象示例：

```
{
    "code": 200,
    "data": null,
    "resultMsg": "删除成功",
    "errorStackTrace": null
}

```
  
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/delete
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  taskId| String| 是 | 删除任务| 13487 |  
###响应：
 
 参数名 | 类型 | 描述 |
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |

##向任务中导入客户接口
 
###功能说明：
 
 通过此接口可以向指定的任务导入客户信息，用于拨打电话,同一个任务，电话号码不能重复，重复号码自动去重。</br>
 单次导入最大10000条
 
 
 >入参JSON示例:
 
  ```
 
{
	"taskId":10000,
	"companyId":2000,
	"customerInfoList":[
		{
			"name":"测试0",
			"phone":"18311110000",
			"properties":{"还款金额":"888","user_id":"33542"
			}
		},
			{
			"name":"测试0",
			"phone":"18311110000",
			"properties":{"还款金额":"888","user_id":"33542"
			}
		}
	]
} 
  
  ```
  
 >返回对象示例：
 
 ```
 v1b版：
 {
     "code": 200,
     "data": null,
     "resultMsg": "操作成功",
     "errorStackTrace": null
 }
 
 v2版：
 {
     "code":200,
     "data":{
         "msg":"本次导入：3个客户，预计导入成功：3个客户，成功导入：3个客户，重复：0个客户，话术变量错误：0个客户",
         "successNum":3,
         "repeatNum":0,
         "placeFailNum":0
     },
     "resultMsg":"操作成功",
     "errorStackTrace":null,
     "requestId":null
 }
 
 ```
 
###请求：
 
 - v1版URL：http://api.byrobot.cn/openapi/v1/task/importTaskCustomer
 - v2版URL：http://api.byrobot.cn/openapi/v2/task/importTaskCustomer

 **PS：v1版接口已过期，不推荐使用，请使用v2版接口。**


###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  companyId| int| 是 | 公司id| 3212 |
  taskId| int| 是 | 任务Id| 13487 |
  name| String| 是 | 客户名称| 张三 |
  phone| String| 是 | 客户电话| 13998987676 |
  properties| Map<String,String>| 否 |话术变量;自定义信息|{"还款金额":"888","user_id":"33542"}|
  
  <aside class="success">
   1、properties 当机器人话术含变量时（除 客户名称、联系方式 这两个默认变量外）,如$还款金额，需要通过该字段入参 ; 同时该字段也支持传入自定义参数如user_id
   |{"还款金额":"888","user_id":"33542"}|
   
   话术变量可通过“查询话术变量 task/getSceneVariables” 接口 查到
  </aside>
 

 
###响应：
 v1版：
 
  参数名 | 类型 | 描述 
  --------- | ------- |------
   code|int | 响应码 |
   resultMsg| String | 响应说明 |
   data | String | 响应数据 |
 
 v2版：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |String
  resultMsg| String | 响应说明 |
  data | object | 响应数据 |
  msg | String | 结果文字消息 |
  successNum | int |成功条数 |
  repeatNum | int | 重复条数 |
  placeFailNum | int | 话术变量错误条数 |

  

##修改任务

###功能说明：

通过接口可以更改AI坐席数量，功能同crm端编辑话术时修改外呼号码的AI坐席数

>入参JSON示例

```
{
  //公司Id
  "companyId": 123,
  //任务Id
  "taskId":1669,
  //任务名称
  "taskName":"test",
  //任务类型 详见枚举
  "taskType":1,
  //外呼号码列表，当有多个外呼号码时可以用[,]分隔
  "userPhoneIds":1,
  //外呼类型 详见枚举
  "callType":1,
  //并发数(ai坐席数)
  "concurrencyQuota":2,
  //多并发数(专业版及以上,最大100，并发数不能超过坐席的2倍)
  "concurrencyPhone":4,
  //外呼开始日期
  "startDate":"2018-12-12",
  //任务开始时间
  "workingStartTime":"09:00",
  //任务结束实际
  "workingEndTime":"20:00",
  //午休开始时间
  "breakStartTime":"12:00",
  //午休结束时间
  "breakEndTime":"14:00",
  "repeatCall": true,
  	"repeatCallRule": [{
  			"phoneStatus": 9,
  			"times": 1,
  			"interval": 5
  		},
  		{
  			"phoneStatus": 10,
  			"times": 1,
  			"interval": 5
  		}
  	]
}

```

>返回对象示例：

```
{
    "code": 200,
    "data": null,
    "resultMsg": "修改成功",
    "errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/task/update

###请求方法：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int| 是 | 公司Id| 3212 |
 taskId| int| 是 | 任务Id| 13487 |
 taskName| String| 是 | 任务名称| test |
 taskType| int| 是 | 任务类型| 1 |
 userPhoneIds| int| 是 | 主叫号码Id| 1 |
 callType| int| 是 | 外呼方式，对应主叫号码类型枚举| 1 |
 concurrencyQuota| int| 是 | 坐席数| 1 |
 smsType| int |否| 是否发送挂机短信：0-否，1-是 |
 smsSendLevel| List<String> | 否 | 发送短信的意向等级，固定值：A级(有明确意向)、B级(可能有意向)、C级(明确拒绝)、D级(用户忙)、E级(拨打失败)、F级(无效客户)
 smsTemplateId| int | 否 | 短信模版id 
 concurrencyPhone| int| 否 | 并发量 | 1|
 startDate| String|否|开始日期|"2018-12-13"|
 workingStartTime|String|否|任务开始时间|"09:00"|
 workingEndTime|String|否|任务结束时间|"20:00"|
 breakStartClose|boolean|否|是否关闭不拨打时间 true:关闭，false:维持原状态，默认false |
 breakStartTime|String|否|暂时停止开始时间,对应百应页面创建任务时的不拨打时段的开始时间,到达这个时间点后,任务将会自动暂停|"12:00"|
 breakEndTime|String|否|暂时停止结束时间,对应百应页面创建任务时的不拨打时段的结束时间，到达这个时间点后 任务将会再次启动|"14:00"|
 repeatCall|boolean|否|是否开启重拨 默认false 关闭 |
 repeatCallRule|list|否|重拨详细规则，请看json入参|
 openElasticity|boolean|是否开启弹性,默认false|false|


###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 resultMsg| String | 响应说明 |

##查询话术变量
  
###功能说明：
  
通过调用此接口可以查询到话术内使用的变量

>返回对象示例：

```
{
    "code":200,
    "data":[
        "变量名1",
        "变量名2",
        "变量名3"
    ],
    "resultMsg":"获取成功",
    "errorStackTrace":null
}

```
  
###请求：
 
 URL： http://api.byrobot.cn/openapi/v1/task/getSceneVariables
 
###请求方法：
 
 GET
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  companyId| int| 是 | 公司Id| 3421 |  
  sceneDefId| int | 是 | 场景Id|22341|
 
###响应：
 
 参数名 | 类型 | 描述 |
 --------- | ------- |------
  code|int | 响应码 |
  data|list(String) | 话术变量集合|
  resultMsg| String | 响应说明 |
