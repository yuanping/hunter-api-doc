# TaskTemplates

## Get task templates

`GET /task_templates.json` 得到所有的任务模版。
一页50条记录，如果要取更多记录，需要加参数`&page=2`，`&page=3`以此类推。如果没有新的数据，返回`[]`。

### Description
`name`: 任务模版名称  
`title`: 任务模版标题 
`desc`: 描述  
`detail`: 概览显示时的详细内容
`type`: 类型  


### Params
`updated_since`：取某个更新时间之后的任务模版

### Response

```json
  [
    {
      "name":"住宿评论",
      "title":"添加评论",
      "desc":"真实详尽的评论可以帮助...",
      "type": "comment_task",
      "created_at":"YYYY-MM-DDTHH:MM:SSZ",
      "updated_at":"YYYY-MM-DDTHH:MM:SSZ",
      "resources": [
        {
          "title": "评分",
          "desc": "点击圆圈进行评分",
          "key": "house_raty",
          "type": "RatyResource",
          "list": [1, 2, 3, 4, 5]
        }
      ],
      "state":"pending/submitted/done/rejected"
    }
  ]
```
关于`resources`的定义，参考 [Resources](https://github.com/yuanping/hunter-api-doc/blob/master/sections/resources.md)

