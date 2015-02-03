# 旅行猎人APP接口文档
这是一个RESTful形式的API，使用JSON序列化和TOKEN认证。

## Request

所有的请求都以`http://hunterapp.fishtrip.cn/api/`开始。

通过请求得到TaskTemplates，在上面的地址后面加上任务模版的Path，比如 http://hunterapp.fishtrip.cn/api/v1/task_templates.json. 可以用curl来测试:

```shell
curl -H 'token: user_token' http://hunterapp.fishtrip.cn/api/v1/task_templates.json
```

要创建一个任务也是一样的，只不过请求的head必须加上`Content-Type: application/json`：

```shell
curl -H 'token: user_token'\
  -H 'Content-Type: application/json' \
  -d '{ "name": "住宿评论", "title": "添加评论" }' \
  http://hunterapp.fishtrip.cn/api/v1/tasks.json
```

## Response

* `200 OK` 修改成功
* `201 Created` 保存成功
* `203 Non-Authoritative Information` 非认证的信息
* `401 Unauthorized` 认证失败
* `403 Forbidden` 没有权限

If API Server is having trouble, you might see a 5xx error. 500 means that the app is entirely down, but you might also see 502 Bad Gateway, 503 Service Unavailable, or 504 Gateway Timeout. It's your responsibility in all of these cases to retry your request later. 

## 通用参数说明

* 所有时间格式都以ISO 8601标准 `YYYY-MM-DDTHH:MM:SSZ` (eg. 2012-05-03T18:01:29+08:00)  
* `since` 取这个时间之后的记录，`until` 取这个时间之前的记录，同时传两个参数取这两个时间之间的记录。  
* `page` 取更多数据，比如一页为50条记录，则`&page=2`取51-100条记录

## 版本
版本在url路径中指定，比如v1版本的url: http://hunterapp.fishtrip.cn/api/v1/task_templates.json


## 使用 JSON格式
我们目前只支持JSON格式来序列话数据。我们的格式没有根节点，属性使用下划线的命名方式。
这意味着当你要发起`POST`或`PUT`请求时，必须要设置`Content-Type: application/json; charset=utf-8`。
我们返回的所有的数据都是以JSON格式，所以API URL都以.json结尾。  
如果你忘记了设置`Content-Type`，会收到`415 Unsupported Media Type`的返回代码。

所有接口支持两种请求方式：json和form表单提交 
注意要设置正确Head的Content-Type值。
比如任务的资源的提交格式： 
Content-Type:application/json => {"resources": [{"key": "bb", "value": "123"}, {"key": "cc", "value": "33"}]} 

# 认证


## 数据接口

* [TaskTemplates](https://github.com/yuanping/hunter-api-doc/blob/master/sections/task_templates.md)
* [Resources](https://github.com/yuanping/hunter-api-doc/blob/master/sections/resources.md)
* [Tasks](https://github.com/yuanping/hunter-api-doc/blob/master/sections/tasks.md)
* [Files](https://github.com/yuanping/hunter-api-doc/blob/master/sections/files.md)

