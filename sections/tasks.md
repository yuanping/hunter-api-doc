# Tasks

## Get tasks
`GET /tasks.json`

### Params
`updated_since`：取某个更新时间之后的任务

### Response
```json
	{
		"title": "task title",
		"desc": "description",
		"name": "task name",
		"type": "comment_task",
    "reward": 20,
    "parent_id": 5,
    "state": "pending",
    "reviewer": "审核人姓名",
    "review_at": "YYYY-MM-DDTHH:MM:SSZ",
		"created_at": "YYYY-MM-DDTHH:MM:SSZ",
		"updated_at":"YYYY-MM-DDTHH:MM:SSZ"
	}
```

## Post task

`POST /tasks.json` 

### Params

```json
	{
		"title": "task title",
		"desc": "description",
		"name": "task name",
		"type": "comment_task",
		"reward": 20,
		"parent_id": 5
	}
```