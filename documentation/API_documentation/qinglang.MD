# 业务编码申请接口

## 接口描述

* 描述：用户申请业务编码
* 接口提供方：晴朗网络产品平台
* 接口地址：/ctri/atomdir/applyrgCode
* 请求方式：post
* 请求类型：application/json
* 字符集：utf-8
* SKU：
* SKUID：

##  请求参数

* Header



| 名称       | 参数        | 类型   | 描述                                                         |      |
| ---------- | ----------- | ------ | ------------------------------------------------------------ | ---- |
| 对端系统   | peerApp     | String | 对端系统，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M    |
| 操作人手机 | account     | String | 手机号，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M    |
| 人员姓名   | contactName | String | 人员姓名，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M    |
| 任务id     | jobid       | String | 一般为UUID                                                   | M    |





* Body



| 名称     | 参数         | 类型   | 描述             | 必填M/选填O/条件必填C |
| -------- |------------| ------ | ---------------- | --------------------- |
| 客户名称 | clientname | string | 如上海浦东公安局 | M                     |



* 请求报文实例：

{

​    "policename": "上海浦东公安局"

}

##  回参说明



| 名称         | 参数       | 类型   | 描述         | 必填M/选填O/条件必填C |
| ------------ | ---------- | ------ | ------------ | --------------------- |
| 处理结果标识 | resultCode | String | 处理结果标识 | M                     |
| 返回结果描述 | resultMsg  | String | 返回结果描述 | M                     |



* 响应报文示例：

{

​    "resultCode": "处理结果标识",

​    "resultMsg": "返回结果描述"

}

# 业务规则录入接口

## 接口描述

* 描述：业务规则配置
* 接口提供方：晴朗网络产品平台
* 接口地址：/ctri/atomdir/blackRuleRemove
* 请求方式：post
* 请求类型：application/json
* 字符集：utf-8
* SKU：
* SKUID：

##  请求参数

* Header



| 名称       | 参数        | 类型   | 描述                                                         | 必填M/选填O/条件必填C |
| ---------- | ----------- | ------ | ------------------------------------------------------------ | --------------------- |
| 对端系统   | peerApp     | String | 对端系统，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 操作人手机 | account     | String | 手机号，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 人员姓名   | contactName | String | 人员姓名，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 任务id     | jobid       | String | 一般为UUID                                                   | M                     |

* Body



| 名称                     | 参数             | 类型         | 描述                                                         | 必填M/选填O/条件必填C      |
| ------------------------ | ---------------- | ------------ | ------------------------------------------------------------ | -------------------------- |
| 业务编码                 | rgCode           | string       | 业务编码，如3900501001                                       | M                          |
| ip规则列表               | ipList           | List<Obejct> | Ip规则列表                                                   | C，若urlList不填则此项必填 |
| L34流序号                | >l34flowNbr      | int          |                                                              | M                          |
| IP地址类型标识           | >ipTypeId        | string       | IPV4：五元组类型为IPV4  IPV6：五元组类型为IPV6               | M                          |
| 服务器地址               | >svrIp           | string       |                                                              | O                          |
| 服务器IP地址掩码类型标识 | >svrIpMaskTypeId | string       | IPTYPE：掩码地址类型。   LENGTHTYPE：掩码长度类型。          | C                          |
| 服务器地址掩码长度       | >svrIpMaskLen    | int          | IPv4掩码长度必须大于等于8且不大于32，或者等于0；IPv6掩码长度必须大于等于32且不大于128，或者等于0。 | C                          |
| 服务器地址掩码           | >svrIpMask       | string       |                                                              | C                          |
| 服务器起始端口号         | >svrStartPort    | int          |                                                              | O                          |
| 服务器结束端口号         | >svrEndPort      | int          |                                                              | O                          |
| 用户手机IP               | >msIp            | string       |                                                              | O                          |
| 手机IP地址掩码类型标识   | >msIpMaskTypeId  | string       | IPTYPE：掩码地址类型。   LENGTHTYPE：掩码长度类型。          | C                          |
| 手机IP地址掩码长度       | >msIpMaskLen     | int          | IPv4掩码长度必须大于等于8且不大于32，或者等于0；IPv6掩码长度必须大于等于32且不大于128，或者等于0。 | C                          |
| 手机IP地址掩码           | >msIpMask        | string       |                                                              | C                          |
| 手机起始端口号           | >msStartPort     | int          |                                                              | O                          |
| 手机结束端口号           | >msEndPort       | int          |                                                              | **O**                      |
| url规则列表              | urlList          | List<Obejct> | url规则列表                                                  | C，若ipList不填则此项必填  |
| L7流序号                 | >l7flowNbr       | int          |                                                              | M                          |
| url地址                  | >url             | string       |                                                              | M                          |

 

* 请求报文示例：

{

  "rgCode": "3900501001",

  "ipList": [

​    {

​      "l34flowNbr": "1",

​      "ipTypeId": "IPV4",

​      "svrIp": "17.242.212.1",

​      "svrIpMaskTypeId": "LENGTHTYPE",

​      "svrIpMaskLen": "24"

​    },

​    {

​      "l34flowNbr": "2",

​      "ipTypeId": "IPV4",

​      "svrIp": "17.242.212.2",

​      "svrIpMaskTypeId": "LENGTHTYPE",

​      "svrIpMaskLen": "24"

​    }

  ],

  "urlList": []

}

##    回参说明



| 名称         | 参数       | 类型   | 描述         | 必填M/选填O/条件必填C |
| ------------ | ---------- | ------ | ------------ | --------------------- |
| 处理结果标识 | resultCode | String | 处理结果标识 | M                     |
| 返回结果描述 | resultMsg  | String | 返回结果描述 | M                     |

 

* 响应报文示例：

{

​    "resultCode": "处理结果标识",

​    "resultMsg": "返回结果描述"

}

 

# 业务规则删除接口

##  接口描述

*  描述：业务规则删除
*  接口提供方：晴朗网络产品平台
*  接口地址：/ctri/atomdir/unsubscribeblack
* 请求方式：post
* 请求类型：application/json
* 字符集：utf-8
* SKU：
* SKUID：

 

##  请求参数

* Header



| 名称       | 参数        | 类型   | 描述                                                         | 必填M/选填O/条件必填C |
| ---------- | ----------- | ------ | ------------------------------------------------------------ | --------------------- |
| 对端系统   | peerApp     | String | 对端系统，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 操作人手机 | account     | String | 手机号，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 人员姓名   | contactName | String | 人员姓名，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 任务id     | jobid       | String | 一般为UUID                                                   | M                     |

* Body



| 名称           | 参数        | 类型         | 描述                                           | 必填M/选填O/条件必填C      |
| -------------- | ----------- | ------------ | ---------------------------------------------- | -------------------------- |
| 业务编码       | rgCode      | string       | 业务编码，如3900501001                         | M                          |
| ip规则列表     | ipList      | List<Obejct> | Ip规则列表                                     | C，若urlList不填则此项必填 |
| L34流序号      | >l34flowNbr | int          |                                                | M                          |
| IP地址类型标识 | >ipTypeId   | string       | IPV4：五元组类型为IPV4  IPV6：五元组类型为IPV6 | M                          |
| url规则列表    | urlList     | List<Obejct> | url规则列表                                    | C，若ipList不填则此项必填  |
| L7流序号       | >l7flowNbr  | int          |                                                | M                          |
| url地址        | >url        | string       |                                                | M                          |



* 请求报文示例：

{

​    "rgCode": "3900501001",

​    "isdnList": [

​        "8613300000000",

​        "8614400000000"

​    ]

}

##  回参说明



| 名称         | 参数       | 类型   | 描述         | 必填M/选填O/条件必填C |
| ------------ | ---------- | ------ | ------------ | --------------------- |
| 处理结果标识 | resultCode | String | 处理结果标识 | M                     |
| 返回结果描述 | resultMsg  | String | 返回结果描述 | M                     |



* 响应报文示例：

{

​    "resultCode": "处理结果标识",

​    "resultMsg": "返回结果描述"

}

 

# 业务签约接口

## 接口描述

*  描述：业务签约
*  接口提供方：晴朗网络产品平台
*  接口地址：/ctri/atomdir/ subscribeblack
*  请求方式：post
*  请求类型：application/json
*  字符集：utf-8
*  SKU：
*  SKUID：

 

##  请求参数

* Header



| 名称       | 参数        | 类型   | 描述                                                         | 必填M/选填O/条件必填C |
| ---------- | ----------- | ------ | ------------------------------------------------------------ | --------------------- |
| 对端系统   | peerApp     | String | 对端系统，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 操作人手机 | account     | String | 手机号，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 人员姓名   | contactName | String | 人员姓名，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 任务id     | jobid       | String | 一般为UUID                                                   | M                     |

* Body



| 名称       | 参数     | 类型         | 描述                   | 必填M/选填O/条件必填C |
| ---------- | -------- | ------------ | ---------------------- | --------------------- |
| 业务编码   | rgCode   | string       | 业务编码，如3900501001 | M                     |
| 手机号列表 | isdnList | List<Obejct> | 签约手机号列表         | M                     |



* 请求报文示例：

{

​    "rgCode": "3900501001",

​    "isdnList": [

​        "8613300000000",

​        "8614400000000"

​    ]

}

 

##  回参说明



| 名称         | 参数       | 类型   | 描述         | 必填M/选填O/条件必填C |
| ------------ | ---------- | ------ | ------------ | --------------------- |
| 处理结果标识 | resultCode | String | 处理结果标识 | M                     |
| 返回结果描述 | resultMsg  | String | 返回结果描述 | M                     |



* 响应报文示例：

{

​    "resultCode": "处理结果标识",

​    "resultMsg": "返回结果描述"

}

 

# 业务解约接口

##  接口描述

*  描述：业务解约
*  接口提供方：晴朗网络产品平台
* 接口地址：/ctri/atomdir/unsubscribeblack
*  请求方式：post
*  请求类型：application/json
*  字符集：utf-8
* SKU：
* SKUID：

 

##  请求参数

* Header



| 名称       | 参数        | 类型   | 描述                                                         | 必填M/选填O/条件必填C |
| ---------- | ----------- | ------ | ------------------------------------------------------------ | --------------------- |
| 对端系统   | peerApp     | String | 对端系统，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 操作人手机 | account     | String | 手机号，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 人员姓名   | contactName | String | 人员姓名，需使用  URLEncoder.encode("String","UTF-8")方法进行编码 | M                     |
| 任务id     | jobid       | String | 一般为UUID                                                   | M                     |

* Body



| 名称       | 参数     | 类型         | 描述                   | 必填M/选填O/条件必填C |
| ---------- | -------- | ------------ | ---------------------- | --------------------- |
| 业务编码   | rgCode   | string       | 业务编码，如3900501001 | M                     |
| 手机号列表 | isdnList | List<Obejct> | 签约手机号列表         | M                     |





* 请求报文示例：

{

​    "rgCode": "3900501001",

​    "isdnList": [

​        "8613300000000",

​        "8614400000000"

​    ]

}

 

##  回参说明



| 名称         | 参数       | 类型   | 描述         | 必填M/选填O/条件必填C |
| ------------ | ---------- | ------ | ------------ | --------------------- |
| 处理结果标识 | resultCode | String | 处理结果标识 | M                     |
| 返回结果描述 | resultMsg  | String | 返回结果描述 | M                     |



* 响应报文示例：

{

​    "resultCode": "处理结果标识",

​    "resultMsg": "返回结果描述"

}



 

 
