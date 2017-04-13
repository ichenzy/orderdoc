
## 接口名称
    获取取消订单原因集合

### 1) 请求地址

>http://oms.xianlife.com/api/order/reasons?shopid=&channel=

### 2) 调用方式：HTTP get

### 3) 接口描述：

* 获取外卖订单的拒绝原因列表

### 4) 请求参数:

#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid||string|Y|店铺id|
|channel||string|Y|渠道编号|

### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
    	"hint":"提示:请与客户沟通一致后取消订单",
        "reasons": [
            {
                "title": "商品已售完",
                "reasonsid": "100"
            },
            {
                "title": "商家代金券",
                "reasonsid": "101"
            },
            {
                "title": "联系不上客户",
                "reasonsid": "102"
            },
            {
                "title": "重复订单",
                "reasonsid": "103"
            }, 
            {
                "title": "其他",
                "reasonsid": "104"
            }
        ]
    }
}

```


### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|title|拒绝标题|string|Y|-|
|reasonsid|拒绝编号|string|Y|-|
***
## 接口名称
    取消订单接口

### 1) 请求地址

>http://oms.xianlife.com/api/order/confirmreason?shopid=&channel=&orderid=&reasonsid=
&reason=

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 取消外卖订单

### 4) 请求参数:

#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid||string|Y|店铺id|
|channel||string|Y|渠道编号|
|orderid||string|Y|订单编号|
|reasonsid||string|Y|取消原因code|
|reason||string|Y|取消原因|

### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
    	"message":"操作成功"
    }
}

```

##  获取店铺的营业状态信息

### 1) 请求地址

>http://oms.xianlife.com/api/store/states?shopid=

### 2) 调用方式：HTTP get

### 3) 接口描述：

* 获取指定店铺的各个渠道的开店状态信息

### 4) 请求参数:

#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid|店铺编号|string|Y| 店铺编号|


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,              
    "result":{
     	  "channels"[
     	   {
     		 "channel":1,
     		 "channelname":"京东",
     		 "state":0
     	   },
     	   {
     		 "channel":1,
     		 "channelname":"美团"
     		  "state":0,
     	   },
     	    {
     		 "channel":2,
     		 "channelname":"饿了吗",
     		  "state":0
     	   }
     	]
    }
}
```


### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|channelname|渠道名称|string|Y|京东、饿了吗、美团等|
|channe|渠道编号|Number|Y|-|
|state|开店状态|Number|Y|1:开店中0：闭店|
***


##  修改店铺的营业状态信息

### 1) 请求地址

>http://oms.xianlife.com/api/store/modifystate?shopid=&channel=&state=

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 修改指定店铺指定渠道的营业状态

### 4) 请求参数:

#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid|店铺编号|string|Y| 店铺编号|
|channel渠道编号|string|Y| 渠道编号|
|state|店铺状态|string|Y| 1:开店中0：闭店|


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
    	"message":"操作成功"
    }
}
```
***

## 修改商品详情订单的商品数量

### 1) 请求地址

>http://oms.xianlife.com/api/order/modifyorder?shopid=&channel=&orderid=&goods=

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 修改指定订单的商品购买的数量，用来商品退款

### 4) 请求参数:

#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid|店铺编号|string|Y| 店铺编号|
|channel渠道编号|string|Y| 渠道编号|
|orderid|订单编号|string|Y| 订单编号|
|goods|修改的商品减的数量数组||Y|结构如下|

```
[
	{
		"goodid":"101001",
		"count":1
	},
	{
		"goodid":"101002",
		"count":2
	},
]

```

### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
    	"message":"操作成功"
    }
}
```

## 接口名称
订单详情接口(更新)

### 1) 请求地址

>http://xloms.com/index.php?orderid=&channelid=

### 2) 调用方式：HTTP get

### 3) 接口描述：

* 订单详情

### 4) 请求参数:

#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|orderid||string|Y|订单ID|
|channelid||string|Y|渠道编号ID|

### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
    	"ismodify":0,
    	"modifystate":0,
    	"ordernote":"多加辣椒",
    	"iscancelorder":0,
        "orderid": "2890380489499",
        "orderid": "2890380489499",
        "ordernum": "#8",
        "shoppaytotal": "¥23.4",
        "channel": "9",
        "channelname": "百度",
        "state": "0",
        "ordertime": "2017-02-20  16:35",
        "subtotal": "¥26",
        "rideritems": {
            "ridername": "张三",
            "ridermobile": "13587628612"
        },
        "customeritems": {
            "customername": "张女士",
            "customermobile": "138123456789",
            "customeraddress": "大西洋新城A1011"
        },
        "goodsitems": [
            {
                "goodsname": "伊利红枣酸牛奶450g",
                "goodscount": "1",
                "goodsamount": "¥6.5"
            },
            {
                "goodsname": "今时代木糖醇酸奶180g",
                "goodscount": "1",
                "goodsamount": "¥3"
            }
        ],
        "otherbilling": [
            {
                "key": "配送费",
                "value": "¥10"
            },
            {
                "key": "商家代金券",
                "value": "- ¥5"
            },
            {
                "key": "支付红包",
                "value": "- ¥5"
            },
            {
                "key": "平台服务费",
                "value": "- ¥2.6"
            }
        ]
    }
}

订单详情获取失败返回结果如下：
{
    "success": true,
    "returntype": 0,
    "result": {
        "success": false,
        "message": "订单详情获取失败"
    }
}
```


### 6) 请求返回结果参数说明（新增字段）:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|ismodify|订单是否允许修改|Number|Y|0：不允许 1：允许|
|modifystate|修改订单的状态|string|Y|0：未修改 1：已经修改过|
|ordernote|订单备注|string|Y|-|
|iscancelorder|是否允许取消订单|string|Y|0:不允许 1：允许|


***
##  获取订单管理接口数据（更新）

### 1) 请求地址

>http://xloms.com/index.php?action=neworderlist&channel=0&pagesize=10&pageindex=0&state=0&shopid=200

### 2) 调用方式：HTTP get

### 3) 接口描述：

* 获取待接单、进行中、已完成、预定单的集合数据，支持懒加载、默认页面

### 4) 请求参数:

#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|channel|订单的渠道来源|Number|Y|0:全部 1:京东 2:美团 |
|pagesize|分页的页块大小|Number|Y|默认大小10|
|pageindex|分页的页码|Number|Y|从0开始|
|state|订单的状态|Number|Y|0:待接单 1:进行中 2:已完成 3:预定单|
|shopid|店铺的编号|Number|Y|-|


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,              
    "result":{
      "shopinfo":  
       {
    	  "shopid":"100",
     	  "shopname":"常营天街店",
     	  "channels"[
     	   {
     		 "channel":0,
     		 "channelname":"全部"
     	   },
     	   {
     		 "channel":1,
     		 "channelname":"美团"
     	   },
     	    {
     		 "channel":2,
     		 "channelname":"饿了吗"
     	   }
     	]
      },
      "orders": [
      	{
          "customeritems": {
           	 "customername": "张女士",
             "customermobile": "138123456789",
             "customeraddress": "大西洋新城A1011"
          },
         "ordernote":"多加辣椒",
    	 "iscancelorder":0,
         "ordernum":"#1",
         "orderid":"2890380489499",
         "channelname":"美团",
         "channe":0,
         "ordertime":"2017-3-1 15:30",
         "shoppaytotal":"¥75.61",
         "statemessage":"骑手未接单",
         "ridername":"",
         "riderphone":"",
         "deliverytime":"2017-7-20 15:30"
      	},
       	{
         "customeritems": {
            "customername": "张女士",
            "customermobile": "138123456789",
            "customeraddress": "大西洋新城A1011"
         },
         "ordernote":"多加辣椒",
    	 "iscancelorder":0,
         "ordernum":"#1",
         "orderid":"2890380489499",
         "channelname":"美团",
         "channe":0,
         "ordertime":"2017-3-1 15:30",
         "shoppaytotal":"¥75.61",
         "statemessage":"骑手已接单",
         "ridername":"张三",
         "riderphone":"18778789999"
       }
      ]
       "hasmore":false,
    }
}
```


### 6) 请求返回结果参数说明新增）:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|ordernote|订单备注|string|Y|-|
|iscancelorder|是否允许取消订单|string|Y|0:不允许 1：允许|

***
##  获取售后管理订单接口

### 1) 请求地址

>http://xloms.com/index.php?action=salesorderlist&channel=0&pagesize=10&pageindex=0&state=0&shopid=200

### 2) 调用方式：HTTP get

### 3) 接口描述：

* 获取未处理、已处理的售后订单

### 4) 请求参数:

#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|channel|订单的渠道来源|Number|Y|0:全部 1:京东 2:美团 |
|pagesize|分页的页块大小|Number|Y|默认大小10|
|pageindex|分页的页码|Number|Y|从0开始|
|state|订单的状态|Number|Y|0:未处理 1:已处理|
|shopid|店铺的编号|Number|Y|-|


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,              
    "result":{
      "orders": [
      	{
          "customeritems": {
           	 "customername": "张女士",
             "customermobile": "138123456789",
             "customeraddress": "大西洋新城A1011"
          },
          "reasons":[
          	{
          		"reason":"用户申请取消订单",
          		"datetime":"于2017-4-8 14:15"
          	},
          	{
          		"reason":"商家已同意取消订单",
          		"datetime":"于2017-4-8 14:20"
          	}
          ]
         "systemreason":"15：00内未处理，将自动取消订单"，
         "ordernote":"多加辣椒",
    	 "iscancelorder":0,
         "ordernum":"#1",
         "orderid":"2890380489499",
         "channelname":"美团",
         "channe":0,
         "ordertime":"2017-3-1 15:30",
         "shoppaytotal":"¥75.61",
         "statemessage":"骑手未接单",
         "ridername":"",
         "riderphone":"",
         "deliverytime":"2017-7-20 15:30"
      	},
       	{
         "customeritems": {
            "customername": "张女士",
            "customermobile": "138123456789",
            "customeraddress": "大西洋新城A1011"
         },
         "ordernote":"多加辣椒",
    	 "iscancelorder":0,
         "ordernum":"#1",
         "orderid":"2890380489499",
         "channelname":"美团",
         "channe":0,
         "ordertime":"2017-3-1 15:30",
         "shoppaytotal":"¥75.61",
         "statemessage":"骑手已接单",
         "ridername":"张三",
         "riderphone":"18778789999"
       }
      ]
       "hasmore":false,
    }
}
```


### 6) 请求返回结果参数说明新增）:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|ordernote|订单备注|string|Y|-|
|iscancelorder|是否允许取消订单|string|Y|0:不允许 1：允许|
|reason|状态提示|string|Y|-|
|datetime|状态变更时间|string|Y|0:不允许 1：允许|
|systemreason|系统自动取消订单提示|string|Y|0:不允许 1：允许|

***
## 接口名称
 *   用户发起的 同意取消订单接口

### 1) 请求地址

>http://oms.xianlife.com/api/order/usercancelorderaccess?shopid=&channel=&orderid=

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 同意用户发起的取消订单接口

### 4) 请求参数:

#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid||string|Y|店铺id|
|channel||string|Y|渠道编号|
|orderid||string|Y|订单编号|

### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
    	"message":"操作成功"
    }
}

```

***
## 接口名称
 *   用户发起的 拒绝取消订单接口

### 1) 请求地址

>http://oms.xianlife.com/api/order/usercancelorderreject?shopid=&channel=&orderid=&reason=

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 拒绝用户发起的取消订单接口

### 4) 请求参数:

#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid||string|Y|店铺id|
|channel||string|Y|渠道编号|
|orderid||string|Y|订单编号|
|reason||string|Y|拒绝的原因|

### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
    	"message":"操作成功"
    }
}

```

