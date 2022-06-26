# Windows 安裝&操作 local 端 MongoDB 之筆記
這是我為大學學弟妹整理 MongoDB 安裝跟簡易操作的筆記，做教學用，有錯誤的話可以通知我更正，感謝
## 需安裝項目
[MongoDB Community Server](https://www.mongodb.com/try/download/community) MongoDB伺服器

[MongoDB Compass](https://www.mongodb.com/try/download/compass) MongoDB 視覺化互動界面

## MongoDB Community Server 安裝
1. 在第一個載點點擊<span class="btn">Download</span>下載 MongoDB Community Server
2. <span class="btn">Next</span><span class="btn">Next</span>後按<span class="btn">Complete</span>完整安裝，再按<span class="btn">Next</span>
```
MongoDB預設安裝在C:\Program Files\MongoDB\Server\版本號

Data 預設在C:\Program Files\MongoDB\Server\版本號\data\
Log  預設在C:\Program Files\MongoDB\Server\版本號\log\
```
3. 取消勾選 <input type="checkbox" checked="checked"><span> Install MongoDB Compass</span>，先不同時安裝 MongoDB Compass 圖形管理工具，避免無法順利安裝，繼續按<span class="btn">Next</span>
4. 按<span class="btn">Install</span>
5. 等待安裝完按<span class="btn">Finish</span>

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
安裝 [MongoDB Compass](https://www.mongodb.com/try/download/compass) 視覺化界面

1. 點擊<span class="btn">Download</span>下載安裝檔
2. 安裝好後使用預設的URI(mongodb://localhost:27017)連接，按 <span class="btn btn-success">Connect</span>
3. 連接成功後，有出現剛剛新增的 Collection 就成功了
