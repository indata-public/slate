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
 code|int | 响应码 |
 companyName|String | 公司名称 |
 companyId| int | 公司Id |
 resultMsg| String | 响应说明 |


##获取公司的主叫电话列表接口

###功能说明：

通过接口可以获取指定公司的所有主叫电话的列表
注意：
1.主叫号码列表的PhoneType字段标识外呼线路类型--需要对应新建任务接口的callType字段
2.文档中给出的是常用枚举类型，若特殊用户自用时出现其他枚举类型，只需要遵循注意点1即可
3.不需要对不同主叫类型区分业务使用的情况下，建议对新建任务的callType做成根据主叫id对应的phoneType动态传入，不要写死字段值


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
		"lineAmount": 1.040,
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
		"lineAmount": 1.030,
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
 code|int | 响应码 |
 userPhoneId|int | 主叫号码Id |
 phone| String | 主叫号码 |
 account|String|主叫号码账号|
 phoneName| String | 主叫号码名称 |
 phoneType| int | 主叫号码类型：手机(0, "手机"),阿里云固话(1, "阿里云固话"),无主叫固话(2, "无主叫固话"),sip线路(6,"sip线路") |
 available| Boolean | 是否可用（已使用ai坐席大于可用ai坐席数时会返回false） |
 totalConcurrencyQuota| int | 总并发数 |
 usedConcurrencyQuota| int | 已经使用并发数 |
 billPeriod|int|计费周期|
 validityBegin|Date|可用开始时间|
 validityEnd|Date|可用结束时间|
 sceneType|int|应用场景 1:呼入,2:呼出,3:呼入呼出|
 lineAmount|BigDecimal|线路账户余额|
 resultMsg| String | 响应说明 |

##获取公司的机器人话术列表接口

###功能说明：

通过接口可以获取指定公司的所有配置完成的机器人话术 
注意：
1.本接口主要获取三个重要字段 (用于新建任务) 
    1）robotDefId:话术机器人ID
    2）sceneDefId:话术场景ID
    3）sceneRecordId:话术场景录音Id
2.三个参数一一对应，如果对应错误或误传可能导致外呼失败或者外呼话术不正确问题，请注意！

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



###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 robotDefId|int | 话术机器人Id |
 robotName| String  |  话术机器人名称 |
 sceneDefId| int | 话术场景Id |
 sceneRecordId| int | 话术场景录音id |
 sceneRecordName| String | 话术场景录音名称 |
 industryOneName|String|一级行业名|
 industryTwoName|String|二级行业名|
 gmtModify|Date|修改时间|
 resultMsg| String | 响应说明 |


##公司添加单个黑名单到默认分组

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
 code|int | 响应码 |
 data|int | 黑名单id |
 resultMsg| String | 响应说明 |

