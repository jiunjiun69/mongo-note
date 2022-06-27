# Windows 安裝&操作 MongoDB 之筆記
這是為大學學弟妹整理 MongoDB 安裝跟簡易操作的筆記，做教學用，有錯誤的話可以通知我更正，感謝
## 需安裝項目
[MongoDB Community Server](https://www.mongodb.com/try/download/community) MongoDB伺服器

[MongoDB Compass](https://www.mongodb.com/try/download/compass) MongoDB 視覺化互動界面

## MongoDB Community Server 安裝
1. 在第一個載點點擊![](https://i.imgur.com/Mpcy0Zl.png)下載 MongoDB Community Server
2. ![](https://i.imgur.com/YAtbCHX.png)![](https://i.imgur.com/YAtbCHX.png)後按<span class="btn">Complete</span>完整安裝，再按![](https://i.imgur.com/YAtbCHX.png)
```
MongoDB預設安裝在C:\Program Files\MongoDB\Server\版本號

Data 預設在C:\Program Files\MongoDB\Server\版本號\data\
Log  預設在C:\Program Files\MongoDB\Server\版本號\log\
```
3. 如果想要使用其他圖形管理工具，可以取消勾選:white_check_mark:Install MongoDB Compass，就不會安裝 MongoDB Compass 圖形管理工具，繼續按![](https://i.imgur.com/YAtbCHX.png)
4. 按<span class="btn">Install</span> 
5. 等待安裝完按![](https://i.imgur.com/PgjNzPF.png)

## MongoDB 簡易操作
1. 打開 cmd(命令提示字元) 切換到 C:\Program Files\MongoDB\Server\版本號\bin (這邊以目前我的版本號5.0為範例)
```
cd C:\Program Files\MongoDB\Server\5.0\bin
```
2. 啟動 MongoDB Shell 
```
mongo
```
3. 簡易操作
```
show dbs 查詢資料庫
use local 使用資料庫 local
exit 關閉資料庫
help 查詢指令
```
以下為關閉資料庫
```
use admin
db.shutdownServer()
```
4. MongoDB 服務啟用&關閉
使用系統管理員身分開啟 cmd(命令提示字元)
```
啟用服務：
net start MongoDB

關閉服務：
net stop MongoDB
```

5. MongoDB Shell 之 CRUD:建立(create)、讀取(read)、更新(update)、刪除(delete)
```
C
db.collection.insert()
db.collection.insertOne()
db.collection.insertMany()

R
db.collection.find()

U
db.collection.update()
db.collection.updateOne() 
db.collection.updateMany() 
db.collection.replaceOne() 

D
db.collection.remove()
db.collection.deleteOne()
db.collection.deleteMany()
```
## MongoDB Shell 指令新增資料庫
這邊以django為資料庫名稱，因為學弟妹後續應該會串接django框架
```
use django    create django 資料庫
db            查看目前資料庫
```
沒新增資料的話 show dbs 不會顯示
因此新增一筆資料到 django collections
```
db.data.insert({"name": "hello", "price": 87})
```
查看 collections 裡的資料
```
db.data.find()
```

---

## MongoDB Compass 安裝
![](https://i.imgur.com/zejfNDx.png)

安裝 [MongoDB Compass](https://www.mongodb.com/try/download/compass) 視覺化界面

!!剛剛沒有取消勾選Install MongoDB Compass的話，就會一併跟MongoDB Community Server一起安裝好了，就不用再特地安裝

1. 點擊![](https://i.imgur.com/Mpcy0Zl.png)下載安裝檔
2. 安裝好後使用預設的URI(mongodb://localhost:27017)連接，按 ![](https://i.imgur.com/28XduOp.png)
3. 連接成功後，有出現剛剛新增的 Collection 就成功了

---
## 更改 MongoDB default ip跟port
可以參考[官方文件](https://www.mongodb.com/docs/manual/reference/configuration-options/)
1. 管理員身份打開CMD命令提示符，切換到MongoDB安裝目錄的bin資料夾
2. 在想要的地方創建配置文件mongod.conf，本文範例是在MongoDB安裝目錄的bin資料夾的conf/下創建
3. 使用--config <配置文件路徑> 運行配置文件
```
範例
mongod --config /conf/mongod.conf
```
```
mongod.conf範例

systemLog:
   destination: file
   path: c:\Program Files\MongoDB\Server\5.0\log
   logAppend: true
storage:
   journal:
      enabled: true
processManagement:
   fork: true
net:
   bindIp: 自己的IP
   port: 想要的port號
setParameter:
   enableLocalhostAuthBypass: false
```
4. 之後設置這些配置
```
mongod --config "conf\mongod.cfg" --install
```
加上--install才不會卡執行續






:u5272:
