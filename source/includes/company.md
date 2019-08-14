# 公司信息接口

##获取绑定公司列表接口

###功能说明：

通过此接口可以获取用户isv下绑定所有的公司信息

>返回对象示例：

```
{
    "code": 200,
    "data": [
        {
            "companyName": "阿里巴巴", 
            "companyId": 1 
        },
        {
            "companyName": "网易", 
            "companyId": 2
        }
    ],
    "resultMsg": "获取成功",
    "errorStackTrace": null 
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/getCompanys

###请求方法：

GET


###请求参数:

无



###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明 |
 data|list(String) |返回结果，详见“ResultModel响应对象模型”说明|
 companyName|String | 公司名称 |
 companyId| int | 公司Id |
 resultMsg| String |响应提示，详见“ResultModel响应对象模型”说明 |
 errorStackTrace| String |详见“ResultModel响应对象模型”说明 |

##获取公司的主叫电话列表接口

###功能说明：

通过接口可以获取指定公司的所有线路的列表
注意：

1. 主叫号码列表的PhoneType字段标识外呼线路类型--需要对应新建任务接口的callType字段
2. 文档中给出的是常用枚举类型，若特殊用户自用时出现其他枚举类型，只需要遵循注意点即可
3. 不需要对不同主叫类型区分业务使用的情况下，建议对新建任务的callType做成根据主叫id对应的phoneType动态传入，不要写死字段值


>返回对象示例：

```
{
	"code": 200,
	"data": [{
		"userPhoneId": 0,
		"callerAccountId": null,
		"phone": "1400xxxxxxx",
		"account": null,
		"phoneName": "xxxxx",
		"phoneType": 2,
		"available": true,
		"useAvailable": true,
		"totalConcurrencyQuota": 5,
		"usedConcurrencyQuota": 0,
		"billPeriod": 60,
		"validityBegin": "2018-07-24 00:00:00",
		"validityEnd": "2019-07-27 00:00:00",
		"sceneType": null,
	}, {
		"userPhoneId": 2,
		"callerAccountId": null,
		"phone": "150xxxxxxxx",
		"account": null,
		"phoneName": "2",
		"phoneType": 2,
		"available": true,
		"useAvailable": true,
		"totalConcurrencyQuota": 5,
		"usedConcurrencyQuota": 0,
		"billPeriod": 60,
		"validityBegin": "2018-07-24 00:00:00",
		"validityEnd": "2019-07-27 00:00:00",
		"sceneType": null,
	}],
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/getPhones

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int| 是 | 公司Id| 1 |



###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 userPhoneId|int | 主叫号码Id(线路Id） |
 phone| String | 主叫号码 |
 phoneName| String | 主叫号码（线路）名称 |
 phoneType| int | 主叫号码类型枚举 |
 available| Boolean | 是否可用（已使用ai坐席大于可用ai坐席数时会返回false） |
 totalConcurrencyQuota| int | null表示总并发无限制，phoneType为手机号时有总并发限制，其他无限制 |
 usedConcurrencyQuota| int | 已经使用并发数 |
 billPeriod|int|计费周期|
 validityBegin|Date|可用开始时间|
 validityEnd|Date|可用结束时间|
 sceneType|int|应用场景 1:呼入,2:呼出,3:呼入呼出|
 resultMsg| String |提示信息，详见“ResultModel响应对象模型”说明 |
 errorStackTrace| String |跟踪信息，详见“ResultModel响应对象模型”说明 |

##获取公司的机器人话术列表接口

###功能说明：

通过接口可以获取指定公司的所有配置完成上线状态的机器人话术 
注意：

1. 本接口主要获取三个重要字段 
    - robotDefId:机器人id
    - sceneDefId:场景id
    - sceneRecordId:场景录音id
2. 三个参数一一对应，如果对应错误或误传可能导致外呼失败或者外呼话术不正确问题，请注意！

>返回对象示例：

```
{
	"code": 200,
	"data": [{
		"robotDefId": 14,
		"robotName": "测试话术1",
		"sceneDefId": 34,
		"sceneRecords": [{
			"sceneRecordId": 34,
			"sceneRecordName": "测试场景录音"
		}],
		"industryOneName": "房产类",
		"industryTwoName": "高端住宅",
		"gmtModify": "2018-11-09 10:09:32"
	}, {
		"robotDefId": 38375,
		"robotName": "测试话术2",
		"sceneDefId": 38387,
		"sceneRecords": [{
			"sceneRecordId": 38383,
			"sceneRecordName": "测试录音"
		}],
		"industryOneName": "房产类",
		"industryTwoName": "装修",
		"gmtModify": "2018-11-29 09:06:43"
	}],
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/getRobots

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int| 是 | 公司Id| 1 |
 robotStatus| int| 否 | 0：所有话术，1：已上线话术，默认0| 1 |
 

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明 |
 data|list(String) |返回结果， 详见“ResultModel响应对象模型”说明 |
 robotDefId|int | 机器人Id |
 robotName| String  |  机器人名称 |
 sceneDefId| int | 场景Id |
 sceneRecordId| int | 场景录音id |
 sceneRecordName| String | 录音名称 |
 industryOneName|String|一级行业名|
 industryTwoName|String|二级行业名|
 gmtModify|Date|修改时间|
 resultMsg| String |错误信息，详见“ResultModel响应对象模型”说明 |
 errorStackTrace| String |跟踪信息，详见“ResultModel响应对象模型”说明 |
 
 
 
 ##获取公司AI坐席概况接口
 
 ###功能说明：
 
 通过接口可以获取公司所有的坐席以及已经使用的坐席数量。
 
 >返回对象示例：
 
 ```
 {
  "code":200,
  "data":
   {
     "companyAllCallSeat":2,
     "companyUsingCallSeat":0
   },
  "resultMsg":"查询成功",
  "errorStackTrace":null,
  "requestId":null
 }
 
 ```
 
 ###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/company/seat/statistics
 
 ###请求方式：
 
 GET
 
 
 ###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |------
  companyId| int | 是 | 公司id | 1 |
 
 
 
 ###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  data|Object | 返回结果， 详见“ResultModel响应对象模型”说明
  companyAllCallSeat|int|表示公司所有坐席数量
  companyUsingCallSeat|int|全公司已使用坐席数量
  resultMsg| String | 响应信息，详见“ResultModel响应对象模型”说明 |
  errorStackTrace| String |跟踪信息，详见“ResultModel响应对象模型”说明 |
  requestId| String |跟踪信息id，详见“ResultModel响应对象模型”说明 |




##添加单个黑名单到公司默认黑名单组接口

###功能说明：

通过接口可以导入单个黑名单信息到默认分组中

>返回对象示例：

```
{
	"code": 200,
	"data": 3221,//黑名单id
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/addBlackList

###请求方式：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 name| string | 否 | 客户姓名 | 测试用户 |
 mobile| string | 是 | 手机号 | 159xxxxxxxx |
 remark| string | 否 | 备注 | 备注信息 |
 companyId| int | 是 | 公司Id | 1 |





###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明  |
 data|int | 黑名单id |
 resultMsg| String |响应信息，详见“ResultModel响应对象模型”说明|
 errorStackTrace| String |跟踪信息，详见“ResultModel响应对象模型”说明 |
 
 
 
 
 
 

