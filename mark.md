
#1.2第二版新增接口
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
    拒绝订单接口

### 1) 请求地址

>http://oms.xianlife.com/api/order/confirmreason?shopid=&channel=&orderid=&reasonsid=
&reason=

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 拒绝外卖订单

### 4) 请求参数:

#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid||string|Y|店铺id|
|channel||string|Y|渠道编号|
|orderid||string|Y|订单编号|
|reasonsid||string|Y|拒绝原因code|
|reason||string|Y|拒绝原因|

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
|shopid|店铺编号|NSString|Y| 店铺编号|


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

#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid|店铺编号|NSString|Y| 店铺编号|
|channel渠道编号|NSString|Y| 渠道编号|
|state|店铺状态|NSString|Y| 1:开店中0：闭店|


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

#1.0第二版新增接口
##  登录接口

### 1) 请求地址

>http://xloms.com/index.php?action=login

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 提供手机号和验证码方式的登录，需要调用发送短信的接口

### 4) 请求参数:

mobilephone=18678850909&code=2016


#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|mobilephone|手机号|string|Y|-|
|code|手机验证码|string|Y|-|


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
   		 "token":"sdsf2343sd23445sd"
   		 
    }
}
```

### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|token|服务器返回的会话标识|string|Y|客户端会存在本地，放在head里面|

***

##  登出接口

### 1) 请求地址

>http://xloms.com/index.php?action=logout

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 用户登出系统，head请求里面会带会话标识

### 4) 请求参数:

暂无


#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|暂无|-|-|-|-|


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
   		 "message":"登出成功"
   		 
    }
}
```

### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|token|服务器返回的会话标识|string|Y|客户端会存在本地，放在head里面|

***


##  发送短信验证码接口

### 1) 请求地址

>http://xloms.com/index.php?action=getcode

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 获取登录短信验证码，需要先判断手机号是否已经注册，未注册直接返回未注册用户就可以

### 4) 请求参数:

mobilephone=18678850909


#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|mobilephone|手机号|string|Y||


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
   		 "message":"验证码发送成功"
   		 
    }
}
```

### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|message|服务器返回的操作信息|string|Y|-|

***

##  获取店铺信息

### 1) 请求地址

>http://xloms.com/index.php?action=userinfo

### 2) 调用方式：HTTP get

### 3) 接口描述：

* head请求里面会带token信息，服务器根据token返回用户管理的店铺信息和支持的平台信息

### 4) 请求参数:
暂无


#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|暂无|-|-|-||


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": [
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
      {
    	"shopid":"101",
     	"shopname":"朝阳大悦城店",
     	"channels"[
     	   {
     		 "channel":0,
     		 "channelname":"全部"
     	   },
     	   {
     		 "channel":1,
     		 "channelname":"京东到家"
     	   },
     	    {
     		 "channel":2,
     		 "channelname":"饿了吗"
     	   }
     	]
      }
    ]
}
```

### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid|店铺的编号|Number|Y|-|
|shopname|店铺的名称|string|Y|-|
|channel|渠道编号|string|Y|-|
|channelname|渠道名称|string|Y|-|


***
##  获取订单管理接口数据

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


### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid|店铺的编号|Number|Y|-|
|shopname|店铺的名称|string|Y|-|
|customername|下单人姓名|string|Y|-|
|customermobile|下单人手机号|string|Y|-|
|customeraddress|配送的地址|string|Y|-|
|ordernum|订单序号|Number|Y|-|
|orderid|订单编号|string|Y|-|
|channelname|订单来源平台名称|string|Y|-|
|channe|订单平台编号|Number|Y|-|
|ordertime|订单下单时间|string|Y|-|
|shoppaytotal|店铺所收订单金额|string|Y|-|
|hasmore|是否还有更多数据|string|Y|YES:分页还有数据 NO:暂无更多数据|
|statemessage|订单状态信息|string|Y|-|
|ridername|骑手的姓名|string|Y|-|
|riderphone|骑手的电话|string|Y|-|
|deliverytime|预订单的配送时间|string|Y|返回这个字端时，按预定单处理|

***

##  接受订单

### 1) 请求地址

>http://xloms.com/index.php?action=acceptorder

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 获取待接单、进行中、已完成、预定单的集合数据，支持懒加载、默认页面

### 4) 请求参数:

channel=0&orderid=2890380489499


#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|channel|订单的渠道来源|Number|Y|0:全部 1:京东 2:美团 |
|orderid|订单编号|string|Y|-|


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


### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|message|操作的结果返回|string|Y|-|

***

##  取消订单

### 1) 请求地址

>http://xloms.com/index.php?action=cancelorder

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 用于取消订单操作

### 4) 请求参数:

channel=0&orderid=2890380489499


#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|channel|订单的渠道来源|Number|Y|-|
|orderid|订单编号|string|Y|-|


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


### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|message|操作的结果返回|string|Y|-|

***
##  历史订单接口

### 1) 请求地址

>http://xloms.com/index.php?action=historyorder

### 2) 调用方式：HTTP get

### 3) 接口描述：

* 获取某个店铺的历史订单信息

### 4) 请求参数:

shopid=200&channel=0&pagesize=10&pageindex=0


#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|shopid|店铺的编号|Number|Y|-|
|channel|渠道编号|string|Y|-|
|pagesize|分页的页块大小|Number|Y|默认大小10|
|pageindex|分页的页码|Number|Y|从0开始|


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
         "ordernum":"#1",
         "orderid":"2890380489499",
         "channelname":"美团",
         "channe":0,
         "ordertime":"2017-3-1 15:30",
         "shoppaytotal":"¥75.61",
         "statemessage":"骑手未接单",
         "deliverytime":"2017-7-20 15:30",
         "ridername":"张三",
         "riderphone":"18778789999",
         "deliverytime":"2017-7-20 15:30"          
      	},
       	{
         "customeritems": {
            "customername": "张女士",
            "customermobile": "138123456789",
            "customeraddress": "大西洋新城A1011"
         },
         "ordernum":"#1",
         "orderid":"2890380489499",
         "channelname":"美团",
         "channe":0,
         "ordertime":"2017-3-1 15:30",
         "shoppaytotal":"¥75.61",
         "statemessage":"订单已完成"
       }
      ]
       "hasmore":false,
    }
}
```


### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|customername|下单人姓名|string|Y|-|
|customermobile|下单人手机号|string|Y|-|
|customeraddress|配送的地址|string|Y|-|
|ordernum|订单序号|Number|Y|-|
|orderid|订单编号|string|Y|-|
|channelname|订单来源平台名称|string|Y|-|
|channe|订单平台编号|Number|Y|-|
|ordertime|订单下单时间|string|Y|-|
|shoppaytotal|店铺所收订单金额|string|Y|-|
|hasmore|是否还有更多数据|string|Y|YES:分页还有数据 NO:暂无更多数据|
|statemessage|订单状态信息|string|Y|-|
|ridername|骑手的姓名|string|Y|-|
|riderphone|骑手的电话|string|Y|-|
|deliverytime|预订单的配送时间|string|Y|返回这个字端时，按预定单处理|

***
##  搜索订单接口

### 1) 请求地址

>http://xloms.com/index.php?action=searchorder

### 2) 调用方式：HTTP post

### 3) 接口描述：

* 用户可以按订单编号、手机号、配送地址、收货人姓名检索订单信息

### 4) 请求参数:

keyword=长楹天街&shopid=200&channel=0


#### POST参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|keyword|搜索的信息|string|Y|-|
|shopid|店铺的编号|Number|Y|-|
|channel|渠道编号|string|Y|-|


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
         "ordernum":"#1",
         "orderid":"2890380489499",
         "channelname":"美团",
         "channe":0,
         "state":0,
         "ordertime":"2017-3-1 15:30",
         "shoppaytotal":"¥75.61",
         "statemessage":"骑手未接单",
         "ridername":"张三",
         "riderphone":"18778789999",
         "deliverytime":"2017-7-20 15:30"       
      	},
       	{
         "customeritems": {
            "customername": "张女士",
            "customermobile": "138123456789",
            "customeraddress": "大西洋新城A1011"
         },
         "ordernum":"#1",
         "orderid":"2890380489499",
         "channelname":"美团",
         "channe":0,
         "orderstate":0,
         "ordertime":"2017-3-1 15:30",
         "shoppaytotal":"¥75.61",
         "statemessage":"订单已完成",
         "ridername":"张三",
         "riderphone":"18778789999"
       }
      ]
       "hasmore":false,
    }
}
```


### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|customername|下单人姓名|string|Y|-|
|customermobile|下单人手机号|string|Y|-|
|customeraddress|配送的地址|string|Y|-|
|ordernum|订单序号|Number|Y|-|
|orderid|订单编号|string|Y|-|
|channelname|订单来源平台名称|string|Y|-|
|channe|订单平台编号|Number|Y|-|
|state|订单的状态|Number|Y|0:待接单 1:进行中 2:已完成 3:预定单|
|ordertime|订单下单时间|string|Y|-|
|shoppaytotal|店铺所收订单金额|string|Y|-|
|hasmore|是否还有更多数据|string|Y|YES:分页还有数据 NO:暂无更多数据|
|ridername|骑手的姓名|string|Y|-|
|riderphone|骑手的电话|string|Y|-|
|deliverytime|预订单的配送时间|string|Y|返回这个字端时，按预定单处理|
***
## 接口名称
    订单详情接口

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


### 6) 请求返回结果参数说明:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|ordernum|订单序号|Number|Y|-|
|orderid|订单编号|string|Y|-|
|channelname|订单来源平台名称|string|Y|-|
|channe|订单平台编号|Number|Y|-|
|state|订单的状态|Number|Y|0:待接单 1:进行中 2:已完成 3:预定单|
|ordertime|订单下单时间|string|Y|-|
|subtotal|商品的总价|string|Y|-|
|shoppaytotal|店铺实际收到的店铺金额|string|Y|-|
|customername|下单人姓名|string|Y|-|
|customermobile|下单人手机号|string|Y|-|
|customeraddress|配送的地址|string|Y|-|
|returntype||int|Y|0:成功;1:失败|
|subtotal||string|Y|小计|
|otherbilling||array|Y|其它计费|





