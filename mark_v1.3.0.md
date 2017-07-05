

## 接口名称
订单详情接口(更新)

### 1) 请求地址

>http://oms.xianlife.com/api/order/find?channel=8&orderid=1209946781166005403

### 2) 调用方式：HTTP get

### 3) 接口描述：

* 订单详情

### 4) 请求参数:

#### GET参数:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|orderid||string|Y|订单ID|
|channel||string|Y|渠道编号ID|

### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
        "ismodify": 0,
        "modifystate": 0,
        "ordernote": "",
        "iscancelorder": 1,
        "orderid": "1209946781166005403",
        "ordernum": "#3",
        "shoppaytotal": "39.50",
        "channel": "8",
        "channelname": "饿了么",
        "state": "1",
        "ordertime": "2017-07-05 17:31:26",
        "deliverytime": "",
        "subtotal": "44.50",
        "statemessage": "骑士已接单",
        "rideritems": {
            "ridername": "王恩朋",
            "ridermobile": "17610701209"
        },
        "customeritems": {
            "customername": "李翔(先生)",
            "customermobile": "15110193096",
            "customeraddress": "芍药居5号院对外经贸东门 5号楼1门203"
        },
        "paymessage": "其他支付",
        "goodsitems": [
            {
                "goodsname": "呀！土豆里脊牛排味薯条70g",
                "goodscount": "1",
                "upccode": "123456",
                "cgoodsid": "548221304",
                "goodsamount": "6.50",
                "goodstotal": "6.50"
            },
            {
                "goodsname": "薯愿香烤原味104g",
                "goodscount": "1",
                "upccode": "123456",
                "cgoodsid": "548218721",
                "goodsamount": "9.50",
                "goodstotal": "9.50"
            },
            {
                "goodsname": "薯愿番茄味104g",
                "goodscount": "1",
                "upccode": "123456",
                "cgoodsid": "548218738",
                "goodsamount": "9.50",
                "goodstotal": "9.50"
            },
            {
                "goodsname": "十月初五迷你鸡仔饼100g",
                "goodscount": "1",
                "upccode": "123456",
                "cgoodsid": "545364152",
                "goodsamount": "10.50",
                "goodstotal": "10.50"
            },
            {
                "goodsname": "井村屋可思甜乐原味蛋糕80g",
                "goodscount": "1",
                "upccode": "123456",
                "cgoodsid": "545359892",
                "goodsamount": "8.50",
                "goodstotal": "8.50"
            }
        ],
        "otherbilling": [
            {
                "key": "运费",
                "value": "6.00"
            },
            {
                "key": "红包",
                "value": "-5.00"
            },
            {
                "key": "店铺承担活动费用",
                "value": "-6.00"
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
|upccode|商品UPC码|Number|Y|-|

***
##  获取订单管理接口数据（更新）

### 1) 请求地址

>http://oms.xianlife.com/api/order/list?shopid=309&state=2&channel=0

### 2) 调用方式：HTTP get

### 3) 接口描述：

* 获取待接单、待拣货、待配送、正在配送、已完成、已取消的集合数据，可以预留懒加载

### 4) 请求参数:

#### GET参数(修改请求参数):
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|

|state|订单的状态|Number|Y|1:待接单2.待拣货3.待配送4.正在配送5.已完成6.已取消|


### 5) 请求返回结果:

```
{
    "success": true,
    "returntype": 0,
    "result": {
        "hint": "提示:您还有24个售后订单未处理",
        "shopinfo": {
            "shopid": "309",
            "shopname": "鲜驿站-芍药居店",
            "channels": [
                {
                    "channel": "0",
                    "channelname": "全部"
                },
                {
                    "channel": "1",
                    "channelname": "京东到家"
                },
                {
                    "channel": "2",
                    "channelname": "美团"
                },
                {
                    "channel": "9",
                    "channelname": "百度"
                },
                {
                    "channel": "8",
                    "channelname": "饿了么"
                }
            ]
        },
        "orders": [
            {
                "customeritems": {
                    "customername": "李翔(先生)",
                    "customermobile": "15110193096",
                    "customeraddress": "芍药居5号院对外经贸东门 5号楼1门203"
                },
                "ordernote": "",
                "iscancelorder": 1,
                "paymessage": "其他支付",
                "goodsitems": [
                    {
                        "goodsname": "呀！土豆里脊牛排味薯条70g",
                        "goodscount": "1",
                        "goodsamount": "6.50",
                        "goodstotal": "6.50"
                    },
                    {
                        "goodsname": "薯愿香烤原味104g",
                        "goodscount": "1",
                        "goodsamount": "9.50",
                        "goodstotal": "9.50"
                    },
                    {
                        "goodsname": "薯愿番茄味104g",
                        "goodscount": "1",
                        "goodsamount": "9.50",
                        "goodstotal": "9.50"
                    },
                    {
                        "goodsname": "十月初五迷你鸡仔饼100g",
                        "goodscount": "1",
                        "goodsamount": "10.50",
                        "goodstotal": "10.50"
                    },
                    {
                        "goodsname": "井村屋可思甜乐原味蛋糕80g",
                        "goodscount": "1",
                        "goodsamount": "8.50",
                        "goodstotal": "8.50"
                    }
                ],
                "ordernum": "#3",
                "orderid": "1209946781166005403",
                "state": "1",
                "channelname": "饿了么",
                "channel": "8",
                "ordertime": "2017-07-05 17:31:26",
                "shoppaytotal": "39.50",
                "subtotal": "44.50",
                "statemessage": "骑士已接单",
                "ridername": "张艳彬",
                "riderphone": "18811332401",
                "deliverytime": "",
                "otherbilling": [
                    {
                        "key": "运费",
                        "value": "6.00"
                    },
                    {
                        "key": "红包",
                        "value": "-5.00"
                    },
                    {
                        "key": "店铺承担活动费用",
                        "value": "-6.00"
                    }
                ]
            }
        ],
        "hasmore": false
    }
}
```


### 6) 请求返回结果参数说明新增）:
|字段名称       |字段说明         |类型            |必填            |备注     |
| -------------|:--------------:|:--------------:|:--------------:| ------:|
|ordernote|订单备注|string|Y|-|
|iscancelorder|是否允许取消订单|string|Y|0:不允许 1：允许|
|hint|订单管理的未处理订单的浮层提示文本|string|Y|没有的时候返回空|
