# Files

## 七牛文件存储

七牛的上传策略： 
用uptoken上传时，指定key的值会做为文件名称保存，也可以使用"/",所以如果key设置为"houses/128/house_overview.jpg"的话，访问图片地址则为 http://7u2qiy.com2.z0.glb.qiniucdn.com/houses/128/house_overview.jpg 
经我测试也可以不指定key的值，这样会以hash做为文件名 http://7u2qiy.com2.z0.glb.qiniucdn.com/FrvHpe1RauEy7HY7Ro7ucO81U4QT 
当指定key值时，要保证文件名的唯一性，否则会上传失败或覆盖。 
七牛的返回： 
{ 
hash = FrvHpe1RauEy7HY7Ro7ucO81U4QT; 
key = houses/128/house_overview.jpg; 
}
建议客户端按下面规则生成文件名： 
{user_id}/{task_type}/{task_id}/{resource_key}-n.jpg 
其中n为自然数，当上传三张时，分别为-1,-2,-3。eg. 8/house_overview_task/3/house_overview_image-1.jpg

### 1+1
1+1的情况（一张样例图片，用户上传一张图片），不需要用户输入图片title，这时要把样例图片的title作为value格式中的title上传。  

### 头像
用户头像的更新通过/users/update_info接口的avatar字段，传的是七牛返回的key。key的格式 avatars/{user_id}/{uuid/hash}.jpg
其中uuid/hash表示唯一的字符串就行，当前时间的integer值也行。


