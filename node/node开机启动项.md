# 删除文件、文件夹.md

### 1.安装pm2
```
sudo npm install pm2 -g
```


### 2.开机启动

```
pm2 start /api/server.js --name="nodeServer"
```

### 3.将pm2设置为开机启动
```
pm2 startup
```