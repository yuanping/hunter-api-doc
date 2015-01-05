# Resources

## Resource

资源是样例与猎人提交的内容（包括图片，文本）的抽象。`type`如果是`TextExample`or`ImageExample`表示样例，其它类型表示猎人提交的内容。 

### Description
一般都会有`title`, `desc`, `key`, `type`, `value`，样例没有`key`。 `title`， `desc`等都可以为空，根据UI进行选择性显示。  
`title`: 字段的Label  
`desc`: 描述  
`key`: 资源的标识  
`type`: 标识UI的展示类型  
`value`: 默认值  
`placehold`: 占位显示说明  
`step`: 属于任务第几步显示的资源，没有此字段时，表示任务只有一步  

### 文本

```json
    {
      "title": "优点",
      "desc": "请填写房间的优点",
      "key": "house_benefit",
      "type": "TextResource",
      "placehold": "优点"
    }
```

### 选择

```json
    {
      "title": "旅行类型",
      "desc": "请选择出行的类型",
      "key": "travel_type",
      "type": "SelectResource",
      "list": [{"home_travel": "家庭游", "business": "商务"}],
      "value": "home_travel"
    }
```

### 图片选择

```json
    {
      "title": "大厅照片",
      "desc": "请按样例拍大厅",
      "key": "house_image",
      "type": "ImageResource",
      "list": ["example_url"],
      "limit": 3
    }
```
`limit`: 用户上传照片的数量

### 评分
```json
    {
      "title": "评分",
      "desc": "点击圆圈进行评分",
      "key": "house_raty",
      "type": "RatyResource",
      "list": [1, 2, 3, 4, 5]
    }
```

### 日期
```json
    {
      "title": "入住日期",
      "desc": "入住日期",
      "key": "checkin_date",
      "type": "DateResource",
      "since": "YYYY-MM-DDTHH:MM:SSZ",
      "until": "YYYY-MM-DDTHH:MM:SSZ"
    }
```
`since`,`until`表示日期可选择的范围，没有值表示没有限制

### 时间
```json
    {
      "title": "早餐时间",
      "desc": "早餐开始时间",
      "key": "breakfast_begin_time",
      "type": "TimeResource"
    }
```
提交格式:"HH:MM:SSZ"


### 坐标
```json
    {
      "title": "地点",
      "desc": "在坐标中选择精准的位置",
      "key": "house_coordinate",
      "type": "CoordinateResource"
    }
```
按此格式提交`(123.4,222.2)`，英文圆括号，英文逗号分隔

### 文本样例
```json
    {
      "title": "title",
      "desc": "desc",
      "type": "TextExample"
    }
```

### 图片样例
```json
    {
      "title": "title",
      "desc": "desc",
      "type": "ImageExample",
      "list": ["image_url"]
    }
```
