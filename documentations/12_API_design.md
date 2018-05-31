# 点餐系统API（第一版）
## 返回状态说明
一个请求是否成功是由 HTTP 状态码标明的。一个 2XX 的状态码表示成功，而一个 4XX 表示请求失败。当一个请求失败时响应的主体仍然是一个 JSON 对象，里面包含 code 和 info 这两个字段，分别表示自定义的错误码以及错误信息，便于调试。

比如，请求失败时，一个可能的响应主体如下：

    {
        "code": 0,
        "info": "fail"
    }

### 错误码
以下为错误码及其相关解释：

| code | HTTP Status | 解释 |
|:----:|:-----------:|:---:|
| - | - | - |


## 获取菜式列表
    GET /dishes/list
    
返回对象:

属性|解释|类型
-|-|-
count|菜式总数|int
dishID|菜品的ID的集合|int array

样例：

    {
        "count": 3,
        "dishID": [1,2,3]
    }

## 获取菜品信息
    GET /dishes/info?dishID

样例：

    /dishes/info?dishID=2  获取ID=2的菜品的信息
    
返回对象：

属性|解释|类型
-|-|-
dishID|菜品ID|int
name|菜名|string
price|菜品单价|float
picture|菜品缩略图|string
volume|菜品每月销量|int

样例：

    {
        "dishID": 2,
        "name": "皮蛋瘦肉粥",
        "price": 5.5,
        "picture": "http://somesite.somedirectory/mypics.png",
        "volume": 121
    }
    
## 提交订单
    POST /dishes/order
    
请求参数：

属性|解释|类型
-|-|-
tableID|进行点餐的餐桌号|int
dishID|已点的菜品ID的集合|int array
num|已点的每道菜的份数|int array

返回对象：

属性|解释|类型
-|-|-
tableID|成功点餐的餐桌号|int

## 商家注册
    POST /management/signup
    
请求参数：

属性|解释|类型
-|-|-
name|用户名|string
password|密码|string

返回对象：

属性|解释|类型
-|-|-
name|成功注册的用户名|string

样例：

    {
        name: "vinsm"
    }

## 商家登录
    POST /management/login
    
请求参数：

属性|解释|类型
-|-|-
name|用户名|string
password|密码|string

返回对象：

属性|解释|类型
-|-|-
name|成功登录的用户名|string

## 商家登出
    POST /management/logout
    
请求参数：

属性|解释|类型
-|-|-
name|用户名|string

返回对象：

属性|解释|类型
-|-|-
name|成功登出的用户名|string

