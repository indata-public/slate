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
            "companyName": "百应1", 
            "companyId": 3813
        },
        {
            "companyName": "百应2", 
            "companyId": 2333
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
 code|int | 响应码，详见“ResultModel对象模型”https://api.byrobot.cn/doc/v2/#6af18eb20f |
 data|list(String) |返回结果，详见“ResultModel对象模型”|
 companyName|String | 公司名称 |
 companyId| int | 公司Id |
 resultMsg| String |响应提示，详见“ResultModel响应对象模型” |
 errorStackTrace| String |详见“ResultModel响应对象模型” |

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
 companyId| int| 是 | 公司Id| 3811 |



###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 userPhoneId|int | 主叫号码Id |
 phone| String | 主叫号码 |
 phoneName| String | 主叫号码名称|
 phoneType| int | 主叫号码类型,0:手机号;1:固话;2:无主叫线路 |
 available| Boolean | 无效字段，可忽略 |
 useAvailable| Boolean | 主叫号码是否可用,true可用，false不可用 |
 totalConcurrencyQuota| int | null表示总并发无限制，phoneType为手机号时有总并发限制，其他无限制 |
 usedConcurrencyQuota| int | 已经使用并发数 |
 billPeriod|int|计费周期|
 validityBegin|Date|可用开始时间|
 validityEnd|Date|可用结束时间|
 sceneType|int|应用场景 1:呼入,2:呼出,3:呼入呼出|
 resultMsg| String |提示信息，详见“ResultModel对象模型”，https://api.byrobot.cn/doc/v2/#6af18eb20f |
 errorStackTrace| String |跟踪信息，详见“ResultModel对象模型” |

##获取公司的机器人话术列表接口

###功能说明：

通过接口可以获取指定公司的所有配置完成上线状态的机器人话术 
注意：

1. 本接口可获取 robotDefId:机器人id 等字段，在调用创建任务接口时会使用到

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
 companyId| int| 是 | 公司Id| 3811 |
 robotStatus| int| 否 | 0：所有话术，1：已上线话术，2：查询发布过的话术(包括已上线和上线后重新修改的话术)，默认0| 1 |
 

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel对象模型”，https://api.byrobot.cn/doc/v2/#6af18eb20f |
 data|list(String) |返回结果， 详见“ResultModel对象模型” |
 robotDefId|int | 机器人Id，创建任务时会用到该ID |
 robotName| String  |  机器人名称 |
 sceneDefId| int | 场景Id |
 sceneRecordId| int | 场景录音id |
 sceneRecordName| String | 录音名称 |
 industryOneName|String|一级行业名|
 industryTwoName|String|二级行业名|
 gmtModify|Date|修改时间|
 resultMsg| String |错误信息，详见“ResultModel响应对象模型”说明 |
 errorStackTrace| String |跟踪信息，详见“ResultModel响应对象模型”说明 |
 
##获取公司的短信模版

###功能说明：

通过接口可以获取指定公司的短信模版 

>返回对象示例：

```
{
    "data":{
        "pageNum":1,
        "pageSize":20,
        "size":20,
        "orderBy":null,
        "startRow":0,
        "endRow":19,
        "total":51,
        "pages":3,
        "list":[
            {
                "smsTemplateId":1,
                "companyId":1,
                "name":"测试- 22",
                "smsTemplateSignId":2004,
                "type":1,
                "content":"【浙江百应】亲爱的用户，您的包裹已经顺利清关",
                "status":2,
                "failReason":"百应人工审核通过",
                "smsTemplateSignName":"浙江百应",
                "gmtCreate":"2019-07-22 11:27:00",
                "gmtModified":"2019-07-23 15:11:47"
            },
            {
                "smsTemplateId":2,
                "companyId":2,
                "name":"还呗-龙举106-测试",
                "smsTemplateSignId":2087,
                "type":4,
                "content":"测试模版",
                "status":2,
                "failReason":"百应人工审核通过",
                "smsTemplateSignName":"测试",
                "gmtCreate":"2019-07-23 10:37:04",
                "gmtModified":"2019-07-23 10:37:23"
            }
        ]
    },
    "code":200,
    "msg":"查询成功",
    "success":true
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/sms/template/list

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int| 是 | 公司Id| 1 |
 status| int| 否 | 1-审核中 2-审核通过 3-审核未通过，不传表示查询所有| 1 |
 

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明 |
 data|list |返回结果， 详见“ResultModel响应对象模型”说明 |
 smsTemplateId|int | 机器人Id |
 companyId| int  |  机器人名称 |
 name| String | 场景Id |
 smsTemplateSignId| int | 场景录音id |
 type| int | 录音名称 |
 content|String|一级行业名|
 status|int|二级行业名|
 failReason|String|修改时间|
 smsTemplateSignName|String|修改时间|
 gmtCreate|Date|修改时间|
 gmtModified|Date|修改时间|
 resultMsg| String |错误信息，详见“ResultModel响应对象模型”说明 |
 errorStackTrace| String|跟踪信息，详见“ResultModel响应对象模型”说明|
 
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
 companyId| int | 是 | 公司Id | 3811 |

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应模型”，https://api.byrobot.cn/doc/v2/#6af18eb20f  |
 data|int | 黑名单id |
 resultMsg| String |响应信息，详见“ResultModel对模型”|
 errorStackTrace| String |跟踪信息，详见“ResultModel对象模型” |
 
 
 
 
 ##查询公司的黑名单分组列表接口
 
 ###功能说明：
 
 通过接口可以查询公司的黑名单分组列表
 
 >返回对象示例：
 
 ```
 {
     "code":200,
     "data":[
         {
             "blacklistInfoGroupId":-1,
             "name":"默认分组",
             "publicFlag":true,
             "remark":""
         },
         {
             "blacklistInfoGroupId":357,
             "name":"黑名单1",
             "publicFlag":false,
             "remark":"test"
         },
         {
             "blacklistInfoGroupId":356,
             "name":"黑名单2",
             "publicFlag":false,
             "remark":"test"
         },
         {
             "blacklistInfoGroupId":350,
             "name":"黑名单3",
             "publicFlag":false,
             "remark":null
         }
     ],
     "resultMsg":"查询成功",
     "errorStackTrace":null,
     "requestId":null
 }
 
 ```
 
 ###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/company/blacklist/group/list
 
 ###请求方式：
 
 GET
 
 ###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |------
  companyId| int | 是 | 公司Id | 1 |
 
 ###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码，详见“ResultModel响应对象模型”说明  |
  data|list | 返回数据 |
  blacklistInfoGroupId| int |黑名单分组id，-1为默认分组|
  name| String |黑名单分组名称 |
  publicFlag| boolean |是否公开 |
  remark| string |备注 |
 
 
 
 






##查询公司的黑名单号码列表

###功能说明：

通过接口可以分页查询公司的某个黑名单分组下的黑名单号码列表

>返回对象示例：

```
{
    "code":200,
    "data":{
        "pageNum":1,
        "pageSize":20,
        "total":100,
        "list":[
            {
                "blacklistInfoId":321693,
                "name":"test99",
                "mobile":"13100000099",
                "remark":null,
                "gmtCreate":"2019-08-14 11:07:34"
            },
            {
                "blacklistInfoId":321692,
                "name":"test98",
                "mobile":"13100000098",
                "remark":null,
                "gmtCreate":"2019-08-14 11:07:34"
            }
        ]
    },
    "resultMsg":"查询成功",
    "errorStackTrace":null,
    "requestId":null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/blacklist/info/page

###请求方式：

GET

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int | 是 | 公司Id | 1 |
 blacklistInfoGroupId| int | 是 | 黑名单分组Id | 1 |
 pageNum| int | 否 | 分页页号，默认1 | 1 |
 pageSize| int | 否 | 每页大小，默认20 | 20 |

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明  |
 data| object | 返回数据 |
 pageNum| int | 当前页 |
 pageSize| int | 当前页大小 |
 total| int | 数据总数量 |
 list| list | 黑名单号码信息列表 |
 blacklistInfoId| long | 黑名单号码id |
 name| string |黑名单号码名称 |
 mobile| string |黑名单号码|
 remark| string |备注|
 gmtCreate| string |创建时间|
 

## 创建黑名单分组接口

###功能说明：

通过接口可以创建一个黑名单分组

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/blacklist/group/add

###请求方式：

POST

>请求象示例：

```
{
    "companyId":1,
    "name":"test1",
    "remark":"test123"
}

```

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int | 是 | 公司Id | 1 |
 name| int | 是 | 黑名单分组名称 | 1 |
 remark| string | 否 | 备注 | test |

>返对象示例：

```

{
    "code":200,
    "data":123456,
    "resultMsg":"新增成功",
    "errorStackTrace":null,
    "requestId":null
}

```

###响应参数：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明  |
 data| long | 创建成功的黑名单分组id |





## 批量添加黑名单号码到黑名单分组接口

###功能说明：

通过接口可以批量添加黑名单号码到某个黑名单分组接口

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/addBlackList/batch

###请求方式：

POST

>请求象示例：

```
{
    "blacklist":[
        {
            "mobile":"18900000000",
            "name":"test0",
            "remark":"remark0"
        },
        {
            "mobile":"18900000001",
            "name":"test1",
            "remark":"remark1"
        },
        {
            "mobile":"18900000002",
            "name":"test2",
            "remark":"remark2"
        }
    ],
    "blacklistInfoGroupId":361,
    "companyId":1
}

```

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int | 是 | 公司id | 1 |
 blacklistInfoGroupId| long | 是 | 黑名单分组id | 1 |
 blacklist| list | 是 | 黑名单信息集合| 1 |
 mobile| string | 是 | 黑名单号码 | 18900000001 |
 name| string | 是 | 黑名单名 | test |
 remark| string | 否 | 备注 | test |

>返对象示例：

```

{
    "code":200,
    "data":{
        "requsetNum":3,
        "successNum":3
    },
    "resultMsg":"新增成功",
    "errorStackTrace":null,
    "requestId":null
}

```

###响应参数：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明  |
 data| object | 返回数据 |
 requsetNum| int | 请求数量 |
 successNum| int | 成功数量 |
 
 



## 编辑黑名单分组

###功能说明：

通过接口可以编辑黑名单分组

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/blacklist/group/edit

###请求方式：

POST

>请求象示例：

```
{
    "companyId":1,
    "blacklistInfoGroupId":361,
    "name":"test_edit",
    "remark":"remark_edit"
}

```

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int | 是 | 公司id | 1 |
 blacklistInfoGroupId| long | 是 | 黑名单分组id | 1 |
 name| string | 是 | 黑名单名 | test |
 remark| string | 否 | 备注 | test |

>返对象示例：

```
{
    "code":200,
    "data":true,
    "resultMsg":"修改成功",
    "errorStackTrace":null,
    "requestId":null
}

```

###响应参数：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明  |
 data| boolean | 返回数据 |
 
 
 
 ## 删除一个黑名单号码
 
 ###功能说明：
 
 通过接口可以删除一个黑名单号码
 
 ###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/company/blacklist/info/delete
 
 ###请求方式：
 
 POST
 
 >请求象示例：
 
 ```
 {
     "blacklistInfoGroupId":361,
     "companyId":1,
     "mobile":"18900000000"
 }
 
 ```
 
 ###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |------
  companyId| int | 是 | 公司id | 1 |
  blacklistInfoGroupId| long | 是 | 黑名单分组id | 1 |
  mobile| string | 是 | 黑名单号码 | 18900000000 |
 
 >返对象示例：
 
 ```
 {
     "code":200,
     "data":true,
     "resultMsg":"删除成功",
     "errorStackTrace":null,
     "requestId":null
 }
 
 ```
 
 ###响应参数：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码，详见“ResultModel响应对象模型”说明  |
  data| boolean | 返回数据 |
  
  

## 删除黑名单分组接口

###功能说明：

通过接口可以删除一个黑名单分组(还有号码则报错)

###请求：

URL：http://api.byrobot.cn/openapi/v1/company/blacklist/group/delete

###请求方式：

POST

>请求象示例：

```
{
    "blacklistInfoGroupId":361,
    "companyId":1
}

```

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int | 是 | 公司id | 1 |
 blacklistInfoGroupId| long | 是 | 黑名单分组id | 1 |

>返对象示例：

```
{
    "code":200,
    "data":true,
    "resultMsg":"删除成功",
    "errorStackTrace":null,
    "requestId":null
}

```

###响应参数：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码，详见“ResultModel响应对象模型”说明  |
 data| boolean | 返回数据 |
