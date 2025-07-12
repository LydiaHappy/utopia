# utopia
家里游戏云说明手册，告君哥书。

### 前景提要
我已经装好了steamcmd以及需要的包。

### 游戏server下载/更新

```
steamcmd
login anonymous
app_update 2394010 validate # 安装+更新
quit
```

所以同理，如果要设置服务器定时更新，写个crontab在每天指定时间运行以下指令即可：
steamcmd + login anonymous + app_update 2394010 validate + quit + 服务器重启脚本

所有能用steamcmd开服的游戏都同理，只是app id不同。

### 启动服务器

开服脚本默认位置：
```
~/.local/share/Steam/steamapps/common/PalServer/PalServer.sh
```
由于咱们（暂时）没有公网ip，需要把服务器注册到帕鲁官方的community server列表里以便大家能够搜到。
需要如下参数：
```
./PalServer.sh -publiclobby
```

### 存档位置

服务器默认位置：
```
~/.local/share/Steam/steamapps/common/PalServer/Pal/Saved
```
由于steam平台在win和linux有不同的id，有些游戏在平台之间倒存档会导致人物角色丢失。
如何转移帕鲁存档：
https://billing.piglinhost.com/index.php?rp=/knowledgebase/108/How-can-i-upload-and-use-my-own-Palworld-world-save.html


### 创建轮椅
最好用screen创建一个自动重启+启动脚本，丢在用户根目录下，以便一键开关机。
类似于我用来重启饥荒的这个：
```
screen -dr dst_server1 -X quit
steamcmd.sh +login anonymous +force_install_dir /home/dst/server_dst +app_update 343050 validate +quit
sleep 10
sh start_server.sh
```

### 注意事项

目前我启动./PalServer.sh之后能在大厅列表搜到，但试图进入的时候服务器无响应。
大概率是由于没设置端口转发的缘故，根据reddit需要以下几个端口：
> 8211 (UDP), 27015-27017 (TCP+UDP)

还有少熬夜，多睡觉。

Enjoy yourself.
