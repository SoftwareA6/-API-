
# 政务移动办公API接口 #
[TOC]

appid是应用在政务移动办公系统中的标识，每个应用拥有一个唯一的AppID；

appsecret是应用的凭证密钥；

appid及appsecret由政务移动办公系统分配。

ADDRESS是开发平台提供的接口地址。

##组织架构接口##
### 1.1 获取AccessToken ###

AccessToken是调用政务移动办公API接口的全局唯一票据，调用接口时需携带AccessToken。
AccessToken需要用AppID和AppSecret来换取，不同的AppID会返回不同的AccessToken。正常情况下AccessToken有效期为7200秒。

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/getToken?appid=APP_ID&&appsecret=APP_SECRET</font>

#### 参数说明 ####

| 参数         | 参数类型   | 必须  | 说明           |
| -------      | :-----     | :---- | :----          |
| APP_ID       | String     | 是    | 应用Id         |
| APP_SECRET   | String     | 是    | 应用的凭证密钥 |

#### 返回说明 ####

* 正确的Json返回结果:

-----------
	{
        "retCode": 0,
		"retMessage": "success",
  		"retData": {
    			"token": "ABCD"
  		}
	}

* 错误的Json返回示例

---------------
	{
		"retCode": 33001,
  		"retMessage": "corpId or corpSecret invalid"
	}

### 1.2 获取人员信息 ###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/user/get?userId=1&&access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                                        |
| -------       | :-----     | :---- | :----                                       |
| access_token  | String     | 是    | 企业应用的凭证密钥                          |
| userId        | String     | 是    | 员工在企业内的UserID，用来唯一标识用户的字段|

#### 返回说明 ####

* 正确的Json返回结果:

-----------
	{
  		"retCode": 0,
  		"retMessage": "success",
  		"retData": {
    		"userId": 1,
    		"userName": "张三",
    		"mobile": "13600000000",
    		"stateCode": "86"
    		"tel": "",
    		"workPlace": "",
    		"position": "",
    		"email": "",
    		"isActive": false,
    		"sex": "1",
    		"jobNumber": "",
    		"isSenior": false,
    		"isHide": false,
    		"remark": "",
    		"extFields": {"虚拟网": 12345},
    		"orgList": [
      		100016000
    		],
             "orderInOrgs": {
            	"100016000": 100000000
       		 }
  		}
	}


| 参数          | 说明                                                          |
| -------       | :----                                                         |
| retCode       | 返回码                                                        |
| retMessage    | 返回信息			                                        |
| userId        | 员工唯一标识ID                                                |
| userName      | 员工名称                                                      |
| mobile        | 手机号码                                                      |
| stateCode     | 国家区号                                                      |
| tel           | 分机号                                                        |
| workPlace     | 办公地点                                                      |
| position      | 职位                                                          |
| email         | 电子邮箱                                                      |
| isActive      | 是否激活                                                      |
| sex           | 性别 1:男 2:女                                                |
| jobNumber     | 员工工号                                                      |
| isSenior      | 是否高管模式                                                  |
| isHide        | 是否隐藏                                                      |
| remark        | 备注                                                          |
| extFields     | 扩展属性                                                      |
| orgList       | 员工所属节点编号的列表                                        |
| orderInOrgs  	|部门中人员的排序，order值必须在5千万到1亿之间（50000000-100000000），从大到小进行排序  |

### 1.3 创建人员 ###

#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/create?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| access_token  | String     | 是    | 企业应用的凭证密钥  |


* 请求包结构

-----------
	{
    	"userName": "张三",
    	"mobile": "13012345678",
    	"tel": "057112345678",
    	"workPlace": "浙江省杭州市",
        "position": "科员",
        "email": "zhangsan@dtdream.com",
        "sex": "1",
    	"jobNumber": "123456"，
    	"isSenior": false,
    	"isHide": false,
    	"remark": "",
    	"extFields": {"虚拟网": 12345},
    	"orgList": [100010,100011],
        "orderInOrgs": {
            "100010": 99999994,
            "100011":99999995
        }
  	}

#### 参数说明 ####

| 参数         | 参数类型| 必须 | 说明                                                        |
| -------      | :----   | :--- | :----                                                       |
| userName     | String  | 是   | 员工名称                                                    |
| mobile       | String  | 是   | 手机号码，用来唯一标识用户的字段                            |
| tel          | String  | 否   | 分机号                                                      |
| workPlace    | String  | 否   | 办公地点                                                    |
| email        | String  | 否   | 电子邮箱                                                    |
| position     | String  | 否   | 职位                                                        |
| sex          | String  | 否   | 性别 1：男 2：女                                            |
| jobNumber    | String  | 否   | 员工工号                                                    |
| isSenior     | Boolean | 否   | 是否高管                                                    |
| isHide       | Boolean | 否   | 是否隐藏手机号码                                            |
| remark       | String  | 否   | 备注                                                        |
| orgList      | List    | 是   | 员工所属节点编号的列表                                      |
| extFields     | Map     | 否   | 员工所属节点编号的列表                                     |                                                               |
| orderInOrgs  | Map     | 否   |部门中排序，order值必须在5千万到1亿之间（50000000-100000000），从大到小进行排序|


#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
		"retMessage": "success",
 		"retData": {
    		"userId": "100010614"
  		}
	}
| 参数          | 说明                   |
| -------       | :----                  |
| retCode       | 返回码                 |
| retMessage    | 对返回码的文本描述内容 |
| userid        | 员工id,企业内唯一      |

### 1.4 更新人员 ###

#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/update?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
* 请求包结构

-----------
	{
    	"userId": 100010000,
        "userName": "张三",
        "tel": "057112345678",
        "workPlace": "浙江省杭州市",
        "position": "科员",
        "email": "zhangsan@dtdream.com",
        "sex": "1",
        "jobNumber": "123456"，
        "isSenior": false,
        "isHide": false,
        "remark": "",
        "extFields": {"虚拟网": 12345},
        "orgList": [100010,100011],
        "orderInOrgs": {
            "100010": 99999994,
            "100011":99999995
        }
  	}

#### 参数说明 ####

| 参数         | 参数类型| 必须 | 说明                                                            |
| -------      | :----   | :--- | :----                                                           |
| userId       | String  | 是   | 员工识ID,企业内唯一                                             |
| userName     | String  | 是   | 员工名称                                                    |
| mobile       | String  | 是   | 手机号码，用来唯一标识用户的字段                            |
| tel          | String  | 否   | 分机号                                                      |
| workPlace    | String  | 否   | 办公地点                                                    |
| email        | String  | 否   | 电子邮箱                                                    |
| position     | String  | 否   | 职位                                                        |
| sex          | String  | 否   | 性别 1：男 2：女                                            |
| jobNumber    | String  | 否   | 员工工号                                                    |
| isSenior     | Boolean | 否   | 是否高管                                                    |
| isHide       | Boolean | 否   | 是否隐藏手机号码                                            |
| remark       | String  | 否   | 备注                                                        |
| extFields    | Map     | 否   | 附加属性                                                    |
| orgList      | List    | 是   | 员工所属节点编号的列表                                      |
| orderInOrgs  | Map     | 否   |部门中排序，order值必须在5千万到1亿之间（50000000-100000000），从大到小进行排序|

#### 返回说明 ####

* 返回结果

----------------
	{
  	"retCode": 0,
  	"retMessage": "success"
	}
| 参数          | 说明                   |
| -------       | :----                  |
| retCode       | 返回码                 |
| retMessage    | 对返回码的文本描述内容 |

### 1.5 删除人员 ###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/user/delete?userId=1&&access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                   |
| -------       | :-----     | :---- | :----                  |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥     |
| userId        | String     | 是    | 员工id,用来唯一标识用户|

#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"message": "success"
	}

| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
| message       | 对返回码的文本描述内容|


### 1.6 获取节点信息 ###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/org/get?access_token=ACCESS_TOKEN&&orgId=100016000</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明              |
| -------       | :-----     | :---- | :----             |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥|
| orgId         | String     | 是    | 节点编号          |

#### 返回说明 ####

* 正确的Json返回结果:

-----------
	{
 	 "retCode": 0,
	  "retMessage": "success",
  		"retData": {
    		"orgId": 100016000,
    		"orgName": "互联网+事业部",
    		"type": 1,
    		"parentId": 1,
    		"fullName": "",
    		"postCode": "",
    		"deptHide": false,
    		"deptPerimits": [],
    		"outerDept": false,
    		"outerPermitDepts": [],
    		"createDeptGroup": false,
    		"orgDeptGroupOwner": null,
    		"deptManagerUseridList": [],
    		"order": 0
  		}
	}


| 参数          | 说明             |
| -------       | :----            |
| retCode       | 返回码            |
| orgId         | 节点编号          |
| orgName          | 节点名称          |
| type          | 节点类型，1=地域，2=分类，3=行政区域，4=单位 5=内设机构，6=工作联络，7=虚拟节点   |
| parentId      | 父节点id |
| fullName      | 节点全称 |
| postCode      | 邮编   |
| deptHide    | 节点是否隐藏, true表示隐藏, false表示显示  |
| deptPerimits  | 可以查看指定隐藏部门的其他部门列表，如果部门隐藏，则此值生效，取值为其他的部门id组成的的字符串 |
| outerDept     | 是否本部门的员工仅可见员工自己, 为true时，本部门员工默认只能看到员工自己             |
| outerPermitDepts  | 本部门的员工仅可见员工自己为true时，可以配置额外可见部门，值为部门id组成的的字符串 |
| createDeptGroup   | 是否存在关联此节点的部门群, true表示是, false表示不是             |
| orgDeptGroupOwner | 部门群群主       |
| deptManagerUseridList | 节点的主管列表,取值为由主管的userid组成的字符串  |
| order           |节点的排序                  |


### 1.7 创建节点 ###

#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/org/create?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
    	"orgName": "互联网+事业部",
        "type": "1",
    	"parentId": "100001",
    	"fullName"："杭州数梦工场互联网+中心事业部"
  	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| orgName      | String  | 是   | 节点名称          |
| type         | String  | 是   | 节点类型，1=地域，2=分类，3=行政区域，4=单位 5=内设机构，6=工作联络，7=虚拟节点   |
| parentId     | String  | 是   | 父节点id |
| fullName     | String  | 否   | 节点全称 |

#### 返回说明 ####

* 返回结果

----------------
	{
  	"retCode": 0,
  	"retMessage": "success",
  	"retData": {
    	"orgId": "100016039"
  		}
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |
| orgId     | 创建的节点编号 |

### 1.8 更新节点 ###

#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/org/update?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
* 请求包结构

-----------
	{
    	"orgId": "100010",
        "orgName"： "互联网+事业部",
        "fullName"："杭州数梦工场互联网+中心事业部",
    	"deptHiding" : true,
        "deptPerimits" : [3,4],
        "outerDept" : true,
        "outerPermitDepts" : [1,2],
        "createDeptGroup": false,
        "orgDeptGroupOwner" : null,
        "order": 0
  	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| orgId    | String  | 是   | 节点编号，节点的唯一标识符          |
| orgName         | String  | 否   | 节点名称 |
| fullName     | String  | 否   | 节点全称 |
| deptHiding   | Boolean | 否   | 节点是否隐藏, true表示隐藏, false表示显示  |
| deptPerimits | String  | 否   | 可以查看指定隐藏部门的其他部门列表，如果部门隐藏，则此值生效，取值为其他的部门id组成的的字符串 |
| outerDept    | Boolean | 否   | 是否本部门的员工仅可见员工自己, 为true时，本部门员工默认只能看到员工自己             |
| outerPermitDepts | String | 否   | 本部门的员工仅可见员工自己为true时，可以配置额外可见部门，值为部门id组成的的字符串 |
| createDeptGroup  | Boolean| 否   | 是否存在关联此节点的部门群, true表示是, false表示不是             |
| orgDeptGroupOwner| String | 否   | 部门群群主       |
| order|节点的排序|否|组织节点是从小到大排序


#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"retMessage": "updated"
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |

### 1.9 删除节点 ###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/org/delete?access_token=ACCESS_TOKEN&&orgId=100010</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
| orgId     | String     | 是    | 节点编号,用来唯一标识节点的字段（注：不能删除根节点；不能删除含有子节点、成员的节点）|

#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"retMessage": "success"
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |

### 1.10 获取子节点列表(当前节点下的单层子节点)###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/org/list_org?access_token=ACCESS_TOKEN&&orgId=100010</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
| orgId         | String     | 是    | 节点编号           |

#### 返回说明 ####

* 正确的Json返回结果:

-----------
    {
    	 "retCode": 0,
  		"retMessage": "success",
  		"retData": [
    		{
      		"orgId": 100016013,
      		"orgName": "测试"
    		},
    		{
      		"orgId": 100016038,
      		"orgName": "测试2"
    		}
  		]
	}


| 参数           | 说明             |
| -------       | :----            |
| retCode       | 返回码            |
|retMessage|对返回码的文本描述内容 |
| orgId     | 节点编号           |
| orgName          | 节点名称          |

### 1.12 获取节点成员列表 ###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/org/list_user?access_token=ACCESS_TOKEN&&orgId=100010</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
| orgId         | String     | 是    | 节点编号            |


#### 返回说明 ####

* 正确的Json返回结果:

-----------
    {
  		"retCode": 0,
  		"retMessage": "success",
  		"retData": [
    		{
      		"userId": 100010610,
      		"userName": "测试"
    		},
    		{
      		"userId": 100010614,
      		"userName": "测试2"
    		}
  		]
	}


| 参数          | 说明                 |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage     |对返回码的文本描述内容 |
| userid        | 人员ID                |
| userName      | 人员名称              |

### 1.13 获取所有根节点列表 ###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/org/getRootOrg?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |


#### 返回说明 ####

* 正确的Json返回结果:

-----------
    {
  		"retCode": 0,
  		"retMessage": "success",
  		"retData": [
    		{
      			"orgId": 1,
      			"orgName": "浙江省"
    		}
  		]
	}


| 参数           | 说明             |
| -------       | :----            |
| retCode       | 返回码            |
| retMessage		|对返回码的文本描述内容 |
| orgId     | 组织ID           |
| orgName          | 组织名称          |


### 1.15 人员排序 ###

#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/updateUserOrder?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
* 请求包结构

-----------
	{
		"orgId": 1,
		"userIdList": [1,2]
	}



#### 返回说明 ####

* 正确的Json返回结果:

-----------
    {
  		"retCode": 0,
  		"retMessage": "success"
	}


| 参数           | 说明             |
| -------       | :----            |
| retCode       | 返回码            |
|retMessage		|对返回码的文本描述内容 |


### 1.16 根据手机号码获取用户Id ###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/user/getUserIdByMobile?access_token=ACCESS_TOKEN&mobile=MOBILE</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
| MOBILE        | String     | 是    | 用户手机号码        |

#### 返回说明 ####

* 正确的Json返回结果:

-----------
    {
  		 "retCode": 0,
         "retMessage": "success",
         "retData": userId
	}


| 参数          | 说明                   |
| -------       | :----                  |
| retCode       | 返回码                 |
|retMessage		|对返回码的文本描述内容  |
|userId         |匹配的用户Id            |


### 1.17 根据手机号码批量获取用户Id ###

#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/batchGetUserIdByMobile?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
* 请求包结构

-----------
	["mobile1","mobile2","mobile3"]



#### 返回说明 ####

* 正确的Json返回结果:

-----------
    {
  		"retCode": 0,
        "retMessage": "success",
        "retData": {
             "mobile1": userId1,
             "mobile2": userId2,
             "mobile3": userId3
        }
	}


| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |
|mobile1        |传入的手机号码         |
|userId1        |对应匹配的用户Id       |


### 1.18 根据DingUserId获取用户Id ###

#### 请求说明 ####
请求方式：GET

<font color=red>ADDRESS/v1/oapi/user/getUserIdByDingUserId?access_token=ACCESS_TOKEN&dingUserId=DINGID</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明                                                               |
| -------       | :-----     | :---- | :----                                                                |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥                                                   |
| DINGID        | String     | 是    | 钉钉中，该用户的id，员工唯一标识ID（不可修改），企业内必须唯一       |

#### 返回说明 ####

* 正确的Json返回结果:

-----------
    {
  		 "retCode": 0,
         "retMessage": "success",
         "retData": userId
	}


| 参数          | 说明                   |
| -------       | :----                  |
|retCode       | 返回码                 |
|retMessage		|对返回码的文本描述内容  |
|userId         |匹配的用户Id            |


### 1.18 根据DingUserId批量获取用户Id ###

#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/batchGetUserIdByDingUserId?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
* 请求包结构

-----------
	["dingUserId1","dingUserId2","dingUserId3"]



#### 返回说明 ####

* 正确的Json返回结果:

-----------
    {
  		"retCode": 0,
        "retMessage": "success",
        "retData": {
             "dingUserId1": userId1,
             "dingUserId2": userId2,
             "dingUserId3": userId3
        }
	}


| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |
|dingUserId     |传入的dingUserId       |
|userId1        |对应匹配的用户Id       |

### 1.19 人员跨地域兼职 ###
人员已经在当前管理员没有权限的地域任职，可以通过此接口将该人员加入到当前管理员有权限的节点
#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/associate?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
* 请求包结构

-----------
	{
		"userId":1,
		"orgId":2
	}
#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| orgId    | Long  | 是   | 节点编号，节点的唯一标识符          |
| userId       |Long   | 是|人员ID                |


#### 返回说明 ####

* 正确的Json返回结果:

-----------
	{
    	"retCode": 0,
    	"retMessage": "success"
	}


| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |

### 1.20 人员跨地域离职 ###
人员在多个地域任职，通过此接口将人员从当前管理员有权限的节点移除
#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/disassociate?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "userId":1,
		"orgId":2
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| orgId    | Long  | 是   | 节点编号，节点的唯一标识符          |
| userId       |Long   | 是|人员ID                |
#### 返回说明 ####

* 正确的Json返回结果:

-----------
	{
    	"retCode": 0,
    	"retMessage": "success"
	}


| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |

### 1.21 人员跨区域调动 ###
#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/crossregion/move?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
    	"userId":1,
    	"fromToken":"token1",
    	"fromOrgId":2,
    	"toToken":"token2",
    	"toOrgId":3
    }

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| userId       |Long   | 是|人员ID                |
| fromToken |   String  |   是   |   调出地企业应用的凭证密钥   |
| fromOrgId    | Long  | 是   | 调出节点编号，节点的唯一标识符          |
| toToken |   String  |   是   |   调入地企业应用的凭证密钥   |
| toOrgId    | Long  | 是   | 调入节点编号，节点的唯一标识符          |
#### 返回说明 ####

* 正确的Json返回结果:

-----------
	{
    	"retCode": 0,
    	"retMessage": "success"
	}


| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |

### 1.22 创建跨区域任职的人员 ###
#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/crossregion/create?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
    	"userUdpParam":
        	{
        	 "userName": "xxx",
             "mobile": "1770644xxxx",
             "tel": "057112345678",
             "workPlace": "浙江省杭州市",
             "position": "科员",
             "email": "xxx@dtdream.com",
             "sex": "1",
             "jobNumber": "123456",
             "isSenior": false,
             "isHide": false,
             "remark": "",
             "orgList": [100010,100011],
              "orderInOrgs": {"100010": 99999994}
        	},
            "crossRegionTokenList":[token1,token2]
    }

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| userName     | String  | 是   | 员工名称                                                    |
| mobile       | String  | 是   | 手机号码，用来唯一标识用户的字段                            |
| tel          | String  | 否   | 分机号                                                      |
| workPlace    | String  | 否   | 办公地点                                                    |
| email        | String  | 否   | 电子邮箱                                                    |
| position     | String  | 否   | 职位                                                        |
| sex          | String  | 否   | 性别 1：男 2：女                                                        |
| jobNumber    | String  | 否   | 员工工号                                                    |
| isSenior     | Boolean | 否   | 是否高管                                                    |
| isHide       | Boolean | 否   | 是否隐藏手机号码                                                    |
| remark       | String  | 否   | 备注                                                    |
| orgList      | List    | 是   | 员工所属节点编号的列表                                      |
| orderInOrgs  | Map     | 否   |部门中排序，order值必须在5千万到1亿之间（50000000-100000000），从大到小进行排序|
| crossRegionTokenList| String | 是  | 员工所属节点涉及的企业应用的凭证密钥列表  |
#### 返回说明 ####

* 正确的Json返回结果:

-----------
	{
    	"retCode": 0,
        "retMessage": "success",
        "retData": {
           "userId": "1000106"
        }
	}


| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |
| userId    | 员工id,用来唯一标识用户 |

### 1.23 更新跨区域兼职人员 ###
#### 请求说明 ####
请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/crossregion/update?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
    	"userUdpParam":
        	{
        	 "userId": 100010000,
        	 "userName": "xxx",
             "mobile": "1770644xxxx",
             "tel": "057112345678",
             "workPlace": "浙江省杭州市",
             "position": "科员",
             "email": "xxx@dtdream.com",
             "sex": "1",
             "jobNumber": "123456",
             "isSenior": false,
             "isHide": false,
             "remark": "",
             "orgList": [100010,100011],
              "orderInOrgs": {"100010": 99999994}
        	},
            "crossRegionTokenList":[token1,token2]
    }

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| userId       | String  | 是   | 员工识ID,企业内唯一                                             |
| userName     | String  | 是   | 员工名称                                                    |
| mobile       | String  | 是   | 手机号码，用来唯一标识用户的字段                            |
| tel          | String  | 否   | 分机号                                                      |
| workPlace    | String  | 否   | 办公地点                                                    |
| email        | String  | 否   | 电子邮箱                                                    |
| position     | String  | 否   | 职位                                                        |
| sex          | String  | 否   | 性别 1：男 2：女                                                        |
| jobNumber    | String  | 否   | 员工工号                                                    |
| isSenior     | Boolean | 否   | 是否高管                                                    |
| isHide       | Boolean | 否   | 是否隐藏手机号码                                                    |
| remark       | String  | 否   | 备注                                                    |
| orgList      | List    | 是   | 员工所属节点编号的列表                                      |
| orderInOrgs  | Map     | 否   |部门中排序，order值必须在5千万到1亿之间（50000000-100000000），从大到小进行排序|
| crossRegionTokenList| String | 是  | 员工所属节点涉及的企业应用的凭证密钥列表  |
#### 返回说明 ####

* 正确的Json返回结果:

-----------
	{
    	"retCode": 0,
        "retMessage": "success",
	}
| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |



### 1.24 获取DingUserId ###
#### 请求说明 ####
Https请求方式：GET

<font color=red>ADDRESS/v1/oapi/user/singleGetDingUserIdByUserId?userId=USER_ID&&access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
| USER_ID  | Long     | 是    | 用户userId  |

* 正确的Json返回结果:

-----------
	{
        "retCode": 0,
        "retMessage": "success",
        "retData": "040120633624157777"
    }
| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |

### 1.25 批量获取dingUserId ###
#### 请求说明 ####
Https请求方式：POST

<font color=red>ADDRESS/v1/oapi/user/batchGetDingUserIdByUserId?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	[100020011,100010621]

* 正确的Json返回结果:

-----------
	{
        "retCode": 0,
        "retMessage": "success",
        "retData": {
            "100020011": "040120633624157777",
            "100010621": "040120633624157888"
        }
    }
| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |

### 1.26 获取DingOrgId ###
#### 请求说明 ####
Https请求方式：GET

<font color=red>ADDRESS/v1/oapi/org/getDingOrgIdByOrgId?orgNumber=ORGNUMBER&&access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明                |
| -------       | :-----     | :---- | :----               |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
| ORGNUMBER  | Long     | 是    | 组织id  |


* 正确的Json返回结果:

-----------
	{
        "retCode": 0,
        "retMessage": "success",
        "retData": "58088971"
    }
| 参数          | 说明                  |
| -------       | :----                 |
| retCode       | 返回码                |
|retMessage		|对返回码的文本描述内容 |


## 组织架构变更事件回调 ##

在使用回调接口之前您需要了解的是，

首先您需要准备好，

* URL:注册事件回调接口填写的接收推送的地址

政务移动办公系统服务器会向回调url推送事件变更。

假设您提供的回调URL是

https://127.0.0.1/dingding/receive

当组织架构发生变化，并且事件类型包含在注册时填写的“call_back_tag”中时，比如call_back_tag字段为“[“user_add_org”,“user_modify_org”]”，那么当发生了“用户增加”和“用户更改”时，政务移动办公系统服务器会向url推送事件。

目前可以监听的事件类型分别为:

* user_add_org    : 用户增加
* user_modify_org : 用户更改
* user_leave_org  : 用户删除
* org_dept_create ： 节点创建
* org_dept_modify ： 节点修改
* org_dept_remove ： 节点删除

###2.1 注册事件回调接口####

#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/call_back/regist?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
    	"url": "www.baidu.com",
    	"call_back_tag": [
      	"user_add_org",
      	"user_modify_org"
    	]
 	 }
* 注：
回调服务端接口开发要求：
 1. method：POST, content\_type : application/json ,编码:UTF-8
 2. 具体请求如下：
    政务移动办公收到相关事件通知后会通过HTTP, POST 的方式调用call\_back\_url地址,参数内容为"[ {'call\_back\_tag':'user\_add\_org','id':'1'},
		{'call\_back\_tag':'user\_modify\_org','id':'2'} ]" //json
  其中参数类型为json,而call\_back\_tag对应上面的监听事件, id为流水号; 同时当tag  为"user\_"开头的,id应解析为user\_id，"org\_"开头的解析为org\_id。

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| url      | String  | 是   | 接收事件回调的地址   |
| call\_back\_tag | Array[String]  | 是   | 需要监听的事件类型，有6种，“user\_add\_org”, “user\_modify\_org”, “user\_leave\_org”, “org\_admin\_remove”, “org\_dept\_create”, “org\_dept_modify”, “org\_dept\_remove”   |

#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"retMessage": "ok"
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |

###2.2 查询事件回调接口####

#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/call_back/get?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |


#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"retMessage": "ok",
    	"url":"https://127.0.0.1/dingding/receive"
    	"call_back_tag": ["user_add_org", "user_modify_org", "user_leave_org"],
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| url           | 接收事件回调的url   |
| call_back_tag | 需要监听的事件类型，有6种，“user_add_org”, “user_modify_org”, “user_leave_org”, “org_dept_create”, “org_dept_modify”, “org_dept_remove”   |


###2.3 更新事件回调接口####

#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/call_back/update?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |


* 请求包结构

----------------
		{
    	"url": "http://192.168.0.63:8004/test/call_back",
    	"call_back_tag": [
      	"user_add_org",
      	"user_modify_org",
      	"user_leave_org",
      	"org_dept_create",
      	"org_dept_modify",
      	"org_dept_remove"
    	]
  	}
#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明             |
| -------      | :----   | :--- | :----            |
| url      | String  | 是   | 接收事件回调的地址   |
| call_back_tag| Array[String]  | 是   | 需要监听的事件类型，有6种，“user\_add\_org”, “user\_modify\_org”, “user\_leave\_org”,“org\_dept\_create”, “org\_dept_modify”, “org\_dept\_remove”   |

#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"retMessage": "ok"
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |

###2.4 删除事件回调接口####

#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/call_back/delete?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |


* 请求包结构

----------------
		无

#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"retMessage": "ok"
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |


## 政务移动办公消息 ###
员工可以通过政务移动办公系统的消息接口发送钉钉消息到同企业的人

###3.1 发送消息接口####
#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/message/send?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
    	"sender": userId1,
    	"toUsers": [userId100, userId101, userId102],
    	"remindType": 1,
        "textContent":"正文"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                  |
| sender       | Long  | 是    | 钉钉消息发送者           |
| tousers      | Array[Long]  | 是   |  钉钉消息接受者,不可超过1000个    |
| remindType   | Integer  | 是   | 提醒类型: 1-应用内钉, 2-短信|
| textContent  | String  | 是   | 钉钉消息正文|

#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"retMessage": "ok"
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |


###3.2 发送消息接口####
#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/message/send_on_mobile?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
    	"sender": "mobile",
    	"toUsers": ["mobile1", "mobile1"],
    	"remindType": 1,
        "textContent":"正文"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                  |
| sender       | String  | 是    | 钉钉消息发送者           |
| toUsers      | Array[String]  | 是   |  钉钉消息接受者手机号,不可超过1000个    |
| remindType   | Integer  | 是   | 提醒类型: 1-应用内钉, 2-短信|
| textContent  | String  | 是   | 钉钉消息正文|

#### 返回说明 ####

* 返回结果

----------------
	{
    	"retCode": 0,
    	"retMessage": "ok"
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |


### 3.3 政务移动办公发送企业会话消息接口 ##
员工可以通过政务移动办公系统的发送企业会话消息接口发送钉钉企业会话消息到同企业的人

#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/ent_message/send?&&access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	   "agentId":"XXXXX",
    	"toUser": "UserId1|UserId2",
    	"toDept": "PartyId1|PartyId2",
    	"msgType": "text",
       "context":"消息内容"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                  |
| toUser       | String  | 否    | userId列表（消息接收者，多个接收者用\|分隔）          |
| toDept      | String  | 否   |  orgId列表，多个接收者用\|分隔。touser或者toparty 二者有一个必填   |
| msgType   | String  | 是   | 消息类型，此时固定为：text |
| context  | String  | 是   | 消息内容   |
|agentId|String|是|微应用ID号|
#### 返回说明 ####

* 返回结果

----------------
	{
  	"retCode": 0,
  	"retMessage": "success",
  	"retData": {
    	"invaliduser": "",
    	"invalidparty": "",
    	"errorparty": "",
    	"erroruser": ""
  		}
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |
| invalidUser        | 无效的userid |
| invalidDept        | 无效的部门id |
| errorUser|错误的部门id|
| errorDept|错误的userid|


### 3.4 政务移动办公发送企业会话消息接口 ##
通过手机号发送企业消息

#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/ent_message/send_on_mobile?&&access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	   "agentId":"XXXXX",
    	"toUser": "mobile1|mobile1",
    	"toDept": "PartyId1|PartyId2",
    	"msgType": "text",
       "context":"消息内容"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                  |
| toUser       | String  | 否    | 手机号列表（消息接收者，多个接收者用\|分隔）          |
| toDept      | String  | 否   |  orgId列表，多个接收者用\|分隔。touser或者toparty 二者有一个必填   |
| msgType   | String  | 是   | 消息类型，此时固定为：text |
| context  | String  | 是   | 消息内容   |
|agentId|String|是|微应用ID号|
#### 返回说明 ####

* 返回结果

----------------
	{
  	"retCode": 0,
  	"retMessage": "success",
  	"retData": {
    	"invaliduser": "",
    	"invalidparty": "",
    	"errorparty": "",
    	"erroruser": ""
  		}
	}
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage        | 对返回码的文本描述内容 |
| invalidUser        | 无效的userid |
| invalidDept        | 无效的部门id |
| errorUser|错误的部门id|
| errorDept|错误的userid|

### 3.5 政务移动办公消息统计接口 ##
查询政务移动办公消息统计
#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/msg_stats/getDingMsg?access_token=ACCESS_TOKEN&&sender=SENDER&&startTime=STARTTIME&&endTime=ENDTIME&&remindType=REMINDTYPE</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
| SENDER        | String     | 是    | 人员的UserId  |
| STARTTIME     | Long   | 是    | Unix时间戳(毫秒)  |
| ENDTIME       | Long   | 否    | Unix时间戳(毫秒)  |
| REMINDTYPE      | Integer| 否 | 提醒类型: 1-应用内钉, 2-短信型,0或不指定-全部类型  |

#### 返回说明 ####

* 返回结果

----------------
    {
    "retCode": 0,
    "retMessage": "ok",
    "retData": [
        {
            "msgCount": 3,
            "remindType": 2,
            "timeStamp": 1500523922000
        },
        {
            "msgCount": 3,
            "remindType": 2,
            "timeStamp": 1500523874000
        },
        ...
    ]
    }
| 参数           | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| msgCount      | 发送的消息数量 |
| remindType    | 消息类型 |
| timeStamp     | 消息发送的时间，时间戳(毫秒) |


###3.6 企业消息统计接口 ##
查询发送的企业消息统计信息
#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/msg_stats/getDeptMsg?access_token=ACCESS_TOKEN&&agentId=AGENTID&&startTime=STARTTIME&&endTime=ENDTIME&&remindType=REMINDTYPE</font>

#### 参数说明 ####

| 参数          | 参数类型   | 必须  | 说明              |
| -------       | :-----     | :---- | :----             |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥|
| AGENTID       | String     | 是    | 微应用ID号        |
| STARTTIME     | Long       | 是    | Unix时间戳(毫秒)  |
| ENDTIME       | Long       | 否    | Unix时间戳(毫秒)  |
| REMINDTYPE    | String     | 否    | 参考3.2中的msgtype,不指定-全部类型  |


#### 返回说明 ####

* 返回结果

----------------
	{
    "retCode": 0,
    "retMessage": "ok",
    "retData": [
        {
            "userCount": 3,
            "deptCount": 1,
            "remindType": "1",
            "timeStamp": 1500508982000
        },
        {
            "userCount": 3,
            "deptCount": 1,
            "remindType": "1",
            "timeStamp": 1500508913000
        }
        ...
    ]
    }
| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| userCount     | 发送的人员数量 |
| deptCount     | 发送的企业数量 |
| remindType    | 消息类型 |
| timeStamp     | 消息发送的时间，时间戳(毫秒) |


## 标签 ##
###4.1 创建标签 ###
创建标签，创建的标签只属于该应用，只有该应用可以增删标签的成员。
#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/apptag/create?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "agentId":"XXXXX",
        "tagName": "XXXXX"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| agentId  | String  | 否   | 应用id，应用的标识，全局唯一   |
| tagName  |String|是|标签名称，长度限制为32个字符，应用内标签名称不可重复|

#### 返回说明 ####

* 返回结果

----------------
	{
     "retCode": 0,
     "retMessage": "success",
     "retData": 1001
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| retData       | 标签id，非负整型|

###4.2 更新标签名称 ##
更新标签名称
#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/apptag/update?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
		  "agentId": "XXXXX",
			"tagId": "XXXXX",
		  "tagName": "XXXXX"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| agentId  | String  | 否   | 应用id，应用的标识，全局唯一   |
| tagId  | String  | 是   | 标签id，非负整型   |
| tagName  |String|是|标签名称，长度限制为32个字符，应用内标签名称不可重复|

#### 返回说明 ####

* 返回结果

----------------
	{
     "retCode": 0,
     "retMessage": "success"
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |

### 4.3 增加标签成员 ##
增加标签的成员
#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/apptag/add_member?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "agentId":"XXXXX",
        "tagId": "XXXXX",
        "userList":[user1,user2],
        "orgList":[org1,org2]
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| agentId  | String  | 否   | 应用id，应用的标识，全局唯一   |
| tagId  | String  | 是   | 标签id，非负整型   |
| userList  | String  | 是   | 人员id列表   |
| orgList  | String  | 是   | 组织节点id列表   |
注意：userList和orgList不能同时为空，单次请求人员列表长度不超过100

#### 返回说明 ####

* 返回结果

----------------
	{
     "retCode": 0,
     "retMessage": "success"
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |

###4.4 删除标签成员 ##
删除标签的成员
#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/apptag/delete_member?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "agentId":"XXXXX",
        "tagId": "XXXXX",
        "userList":[user1,user2],
        "orgList":[org1,org2]
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| agentId  | String  | 否   | 应用id，应用的标识，全局唯一   |
| tagId  | String  | 是   | 标签id，非负整型   |
| userList  | String  | 是   | 人员id列表   |
| orgList  | String  | 是   | 组织节点id列表   |
注意：userList和orgList不能同时为空，单次请求人员列表长度不超过100

#### 返回说明 ####

* 返回结果

----------------
	{
     "retCode": 0,
     "retMessage": "success"
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |



### 4.5 获取标签成员 ##
获取标签的成员
#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/apptag/list_member?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "agentId":"XXXXX",
        "tagId": "XXXXX"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| agentId  | String  | 否   | 应用id，应用的标识，全局唯一   |
| tagId  | String  | 是   | 标签id，非负整型   |

#### 返回说明 ####

* 返回结果

----------------
    {
        "retCode": 0,
        "retMessage": "success",
        "retData": {
        	"userList": ["100","101","102"],
            "orgList": ["1000","1001","1002"],
        }
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| userList    | 人员id列表 |
| orgList    | 组织节点id列表 |


### 4.6 获取标签列表 ##
获取当前应用的标签列表
#### 请求说明 ####

请求方式: GET

<font color=red>ADDRESS/v1/oapi/apptag/list?access_token=ACCESS_TOKEN&agentId=AGENT_ID</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |
| agentId  | String  | 否   | 应用id，应用的标识，全局唯一   |


#### 返回说明 ####

* 返回结果

----------------
    {
        "retCode": 0,
        "retMessage": "success",
        "retData": {
        	"tagList": [
						"tagid1"："tagname1",
						"tagid2"："tagname2"
					]
        }
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| tagList    | 标签列表，返回标签id和标签名称的列表 |

##待办##
### 5.1 注册待办事宜 ##
“四个平台”移动应用在使用待办事宜功能之前要进行注册。
#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/backlog/register?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "agentId":"XXXXX",
	    "orgName":"中小企业服务",
	    "type":"0",
	    "urlPrefix":"www.zjszw.com"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| agentId  | int  | 是   | 应用id，应用的标识，全局唯一   |
| orgName| String  | 是   | 应用名称   |
| type| String  | 否   | 应用类型（默认为“APP”类型, 可以不传,0为app,1为其他）  |
| urlPrefix| String  | 否   | 应用首页地址前缀,用于跳转应用,若不填写需在发布待办事宜中填写完整跳转路径   |

#### 返回说明 ####

* 返回结果

----------------
    {
        "retCode": 0,
        "retMessage": "success"
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |

### 5.2 发布待办事宜 ##
针对用户发布新的待办事宜
#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/backlog/publish?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "title":"大学生运动会",
	    "sponsorUserId":"100010610",
	    "level":"0",
	    "startTime":"1504840278000",
	    "endTime":"1504840278000",
	    "handleUserIdList":[100010611,100010612],
	    "callbackUrl":"sport/sport-manage"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| title| String| 是   | 待办事宜的标题   |
| sponsorUserId| Long| 是   | 待办发起人ID   |
| level| Int| 是   | 待办事宜级别(0-普通，1-紧急)|
| startTime| Long| 是   | 待办的发起时间(使用时间戳,具体到毫秒)   |
| endTime| Long| 是   | 待办的截止时间(使用时间戳,具体到毫秒)  |
| handleUserIdList| List| 否   | 处理人ID列表   |
| callbackUrl| String  | 是   | 应用审批地址后缀(urlPrefix + callbackUrl組成完整跳转路径)   |
#### 返回说明 ####

* 返回结果

----------------
    {
        "retCode": 0,
        "retMessage": "success",
        "retData": 102416071
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| retData| 待办事宜id |

### 5.3 更新待办事宜 ##
移动应用可以更新待办事宜基本属性
#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/backlog/update?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "backLogId":"102416071",
	    "title":"全国大学生运动会",
	    "level":"1",
	    "endTime":"1504840278000"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| backLogId| Long| 是   | 待办事宜的id   |
| title| String| 是   | 待办事宜的标题   |
| level| Int| 是   | 待办事宜级别(0-普通，1-紧急)|
| endTime| Long| 是   | 待办的截止时间(使用时间戳,具体到毫秒)  |
#### 返回说明 ####

* 返回结果

----------------
    {
        "retCode": 0,
        "retMessage": "success",
        "retData": true
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| retData| 操作是否成功 |

### 5.3 完成待办事宜 ##
移动应用可以更新用户待办事宜完成状态
#### 请求说明 ####

请求方式: POST

<font color=red>ADDRESS/v1/oapi/backlog/finish?access_token=ACCESS_TOKEN</font>

#### 参数说明 ####

| 参数           | 参数类型    | 必须  | 说明              |
| -------       | :-----     | :---- | :----            |
| ACCESS_TOKEN  | String     | 是    | 企业应用的凭证密钥  |

* 请求包结构

-----------
	{
	    "handleUserId":"100010611",
	    "backLogId":"102416071"
	}

#### 参数说明 ####

| 参数          | 参数类型 | 必须  | 说明                    |
| -------      | :----   | :--- | :----                      |
| handleUserId| Long| 是   | 用户的id   |
| backLogId| String| 是   | 待办事宜的id   |
#### 返回说明 ####

* 返回结果

----------------
    {
        "retCode": 0,
        "retMessage": "success",
        "retData": true
    }

| 参数          | 说明               |
| -------       | :----              |
| retCode       | 返回码              |
| retMessage    | 对返回码的文本描述内容 |
| retData| 操作是否成功 |
## 附录 ####
###全局返回码说明 ####

|   参数  |   说明  |
|   ------- |   :-----  |
|   -3  |   未知原因    |
|   -1  |   失败  |
|   0   |   成功  |
|   33001   |   AppId或AppSecret无效   |
|   33002   |   timestamp不存在  |
|   33003   |   timestamp无效   |
|   33004   |   access_token无效  |
|   33005   |   access_token失效  |
|   33006   |   获取access_token失败    |
|   33007   |   API调用频率超过限制 |
|   33008   |   MD5加密失败         |
|   33009   |   OApiRole创建失败    |
|   33010   |   OApiRole删除失败    |
|   34001   |   用户已存在   |
|   34002   |   查无此人     |
|   34003   |   用户查询失败  |
|   34004   |   人员所在组织不能超过20个   |
|   34005   |   创建人员失败  |
|   34006   |   不允许修改属性 |
|   34007   |   更新人员失败  |
|   34008   |   不能删除有通讯录的用户 |
|   34009   |   修改用户排序失败    |
|   34010   |   用户处在高管模式    |
|   34011   |   发送消息失败  |
|   34012   |   发DING人数超过限制 |
|   34013   |   发DING消息字数超过限制   |
|   34014   |   发送者未同步至手机端  |
|   34015   |   部分接收人员未同步至手机端   |
|   34016   |   发送者不存在  |
|   34017   |   接收人员不存在 |
|   34018   |   不允许修改手机号    |
|   34019   |   对xx发送DING消息过多,请稍后再试 |
|   34020   |   用户删除失败  |
|   34021   |   接收者中存在无权限人员 |
|   34022   |   用户不属于该组织    |
|   35001   |   组织已存在  |
|   35002   |   获取组织人数失败    |
|   35003   |   组织人数超出限制    |
|   35004   |   获取组织ID失败    |
|   35005   |   组织信息获取失败或不存在    |
|   35006   |   组织信息添加失败    |
|   35007   |   组织信息更新失败    |
|   35008   |   组织信息删除失败    |
|   35009   |   获取组织下用户失败   |
|   35010   |   组织名已存在  |
|   35011   |   接收部门不存在 |
|   36001   |   参数不合法   |
|   36002   |   手机号不合法  |
|   36003   |   手机号检查失败 |
|   36004   |   用户手机号已存在    |
|   36005   |   邮箱检查失败  |
|   36006   |   邮箱已存在   |
|   36007   |   分机号检查失败 |
|   36008   |   分机号已存在  |
|   36009   |   用户所在组织未授权   |
|   36010   |   用户所在组织类型不能有人员   |
|   36011   |   用户未授权   |
|   36012   |   用户排序应在(50000000,100000000)之间    |
|   37001   |   回调事件获取失败    |
|   37002   |   回调事件注册失败    |
|   37003   |   回调事件更新失败    |
|   37004   |   回调事件删除失败    |
|39001|待办事务注册参数不合法|
|39002|待办事务注册失败|
|39003|待办事务创建参数不合法|
|39004|用户未授权|
|39005|待办事务创建失败|
|39006|获取待办事务失败|
|39007|待办事务不存在|
|39008|完成待办事务失败|
|39009|获取注册待办事务应用失败|
|39010|获取注册待办事务参数无效|
|39011|接口未授权|
