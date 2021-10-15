# Linux 系統生存課
###### tags: `cosbi`
Linux 指的是 [**Linux Kernel**](https://github.com/torvalds/linux) 作業系統核心，只包含系統層級的基礎元件/功能，而我們使用電腦系統必須還要有 UI(使用者介面)和一些管理程式等等。Linux distributions 則是基於 Linux Kernel 開發的作業系統，不同的 distributions 會預載不同的使用者軟體。
[10 Top Most Popular Linux Distributions of 2021](https://www.tecmint.com/top-most-popular-linux-distributions/), 這是 [TecMint](https://www.tecmint.com/) 2021 年統計的受歡迎 Linux distributions 排行榜。我自己有用過 Keli, CentOS, Ubuntu, Fedora，一般新手我推薦使用基於 [RHEL](https://zh.wikipedia.org/wiki/Red_Hat_Enterprise_Linux) 發展的 [CentOS](https://zh.wikipedia.org/zh-tw/CentOS) 和基於 [Debian](https://zh.wikipedia.org/zh-tw/Debian) 發展的 [Ubuntu](https://zh.wikipedia.org/zh-tw/Ubuntu)，前者使用 yum 後者使用 apt 進行軟體套件管理。

## 大綱
[ToC]
## 安裝
- 下載 [Ubuntu 20.04 Desktop](https://ubuntu.com/download/desktop/thank-you?version=20.04.3&architecture=amd64)
- 下載 [Rufus](https://rufus.ie/zh_TW/) 製作開機 USB
    - 選擇你的 USB 硬碟和上面下載的 .iso 映像檔案，其他保留預設就好
    ![rufus](https://i.imgur.com/kAEEFUT.png =50%x)

- 如果你要 Windows + Ubuntu 雙系統 需進行 [磁碟分割](https://www.asus.com/tw/support/FAQ/1044688/)，想純粹安裝 Ubuntu 者略過
- 重開電腦狂點 Del 進入 bios 選擇 usb 開機 (每個電腦廠牌進入點選的按鈕和 bios 設定不同 可上網查)
- 開始安裝 (只列出需要注意的步驟，其他沒列就做直觀的選擇就好 e.g. Continue)
    - 得安裝英文版的，中文版資料夾路徑會產生問題，輸入法也先選英文就好，保留預設值不動
        ![](https://i.imgur.com/tARX2iR.png)
    - 如果要 Windows + Ubuntu 會看到 Install Ubuntu alongside Windows 10 的選項(得先安裝 Windows 再安裝 Ubuntu )
        ![](https://i.imgur.com/qAQCQzv.png)


## 指令操作
- Linux 系統預設使用 `/bin/bash` 作為使用者登入 Shell
- 不知道指令怎麼下參數的話可以加入 `--help` or `-h` 查詢
### 基本
- 檔案操作: `ls`, `ll`, `cat`, `file`, `head`, `tail`, `rm`, `cp`, `stat`
- 目錄操作: `cd`, `mkdir`, `rm -r`, `pwd`, `cp -r`
- 列出 Command 歷史: `history`
- 列出時間資訊: `date`, `timedatectl`
- 自訂指令名稱: `alias`
- 指令手冊: `man`
### 進階
- 檔案權限操作: `chmod`, `chown`, `chgrp`
    ![](https://i.imgur.com/eQwwlnx.png =50%x)

- 壓縮/解壓縮: `zip`, `unzip`, `tar`
- 查看磁碟: `lsblk`, `df -h`
- 監控系統: `ps`, `htop`, `kill`
- 輸入/輸出導向, 管線操作: `|`, `>`, `>>`
- bash script
- 排程任務: `cron`


## 軟體工具
在 Ubuntu 下 9.9 成軟體可以使用 apt 套件管理程式來安裝，原理是系統預設寫好每個軟體的來源(IP)，當你下指令系統會去對應的網路來源下載軟體並安裝，因為是系統預設好的所以不同系統版本(Ubuntu 14.04 , 16.04, 18.04 ..etc)的預設來源可能不同，有些太新的軟體甚至沒有，這時候可以使用 `sudo apt update` 做來源更新，或是上網搜尋找安裝方法加入新的來源列表。
### Python
使用 Linux 開發 Python 幾乎一定會用到的軟體工具
```bash=
sudo apt install -y git tree python3-pip python3-venv
```
### Network
```bash=
sudo apt install -y net-tools curl 
```
網路偵錯工具:`ping`, `netstat`, `traceroute`, `dig`
### Vim 
![](https://i.imgur.com/KyoxsOV.png)

```bash=
sudo apt install -y vim
```
**特色**
- 高度客製化和擴充彈性
- 讓你 Coding 速度 **最快**

**Multiple operating mode**
- Normal 
- Insert
- Replace
- Visual
- Command-line

Cheat sheet:
![](https://i.imgur.com/TgsRyWm.png)

Original Vim:
![](https://i.imgur.com/DD3Sph8.png =50%x)

After configuration:
![](https://i.imgur.com/c7CqhBu.png)


可以使用我的設定檔: https://github.com/Msiciots/term-conf

### Tmux
```bash=
sudo apt install -y tmux
```
- Client / Server model
- Keep running while SSH disconnect
- Share sessions between multi-user 

Tmux 主要用來分割 Terminal , 還有在多個 Terminal 間切換
![](https://i.imgur.com/0fke4iB.png)




我寫 Code 幾乎都用這兩個工具，當然你也可以用 [VSCode](https://code.visualstudio.com/)
## 創建 Django 網站
建立 Python 虛擬環境，可在任意資料夾下創建
```bash=
python3 -m venv djenv
```
啟用虛擬環境，已經進入虛擬環境後執行指令用 python3, python 都可以
```bash=
source ./djenv/bin/activate
```
安裝 Django 還有任何你網站會用到的 Python 套件
```bash=
pip install Django
```
**創建 Django project** (跟暑假上課教的一樣,稍微提到)
```bash=
django-admin startporject web_project
cd ./web_project
python manage.py startapp mainPage
```
**執行網站**
```bash=
python manage.py runserver
```
離開虛擬環境
```bash=
deactivate
```
刪除虛擬環境，直接刪除虛擬環境資料夾即可
```bash=
rm -rf ./djenv
```
### 讓外部連線
一般創建完 Django project 可以直接使用 localhost:8000 在瀏覽器查看網站，但並不能讓其他電腦連線進來，得做特別設定。

查看目前電腦 IP, 下面輸出中的 `inet` 就是你的目前電腦IP，如果是 140.116 開頭可以直接讓別台電腦連線，如果像我是 192.168 開頭代表這是 **虛擬IP** 我的電腦上面有路由器存在，須做 **Port forwarding** 設定，這個設定是 case by case 我得透過實際操作才能教你
```bash=
ifconfig

## 以下為輸出
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.3  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::39b4:6cf0:35c5:8b96  prefixlen 64  scopeid 0x20<link>
        ether 98:ee:cb:41:99:03  txqueuelen 1000  (Ethernet)
        RX packets 589357  bytes 392667026 (392.6 MB)
        RX errors 0  dropped 696  overruns 0  frame 0
        TX packets 502163  bytes 99188643 (99.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xdf000000-df020000
```
到 `settings.py` 設定能允取外部連線的IP位置
```python=
# 對所有電腦內網卡 IP 開放連線
ALLOWED_HOSTS = ['*']
```
在啟動時加入參數
```bash=
# 0.0.0.0 代表監聽所有本機上的網卡連線
python manage.py runserver 0.0.0.0:8000
```
當已經設定好後輸入你目前網域的 **Public IP**(140.116....)加上對應的 **Port** 就可以讓外部連線
假設我的 Public IP 是 140.116.214.151
那我在任何裝置的瀏覽器上輸入 http://140.116.214.151:8000 就能連到我的網站

### Model
一般資料庫是使用 SQL 指令來存取資料，但在 Django 中是使用 Object Relational Mapping (ORM) 方式來存取資料。透過建立抽象化的 model ，將資料視為一種「物件」，就可以用 python 的方式來處理資料，而不用擔心底層的資料設定。

使用 model 時，我們必須先進入 models.py 中設計每個資料表的 class，再利用以下指令把虛擬層的 class 寫入真的資料庫 ( SQLite ) 中：
``` bash
$ python manage.py makemigrations #產生 class 描述檔案，位置在 app/migrations 中
$ python manage.py migrate #根據描述檔來變更資料庫設定
```

如果要讓 Django 預設的 admin 介面能夠讀取資料庫 ( 實際上是讀取虛擬層的 model )，就必須另外在 admin.py 中啟用剛剛設計好的 model ( 請參考下個段落 )。

如果要讓 views.py 順利讀取資料庫，除了透過 SQL 語法，也可以直接透過 ORM 的方式來進行操作，例如：
``` python
table1 = models.Table.objects.all() #取得此 Table 的全部資料
table2 = models.Table.objects.get(id='001') #取得此 Table 的某筆資料
table3 = models.Table.objects.filter(num<10) #篩選此 Table 的某些資料
```

### SQLite
Django 預設使用的資料庫檔案系統, 有內建的後端程式會幫忙處理資料庫溝通，且內建一個管理介面 ( Django admin )，可以直接增加、刪除、搜尋資料。

#### Django admin
首先建立 superuesr，請打以下指令：
```bash=\
$ python manage.py migrate #之前如果沒做過，記得加上這行
$ python manage.py createsuperuser #在db中創建管理員帳號
```
按照步驟設定完帳密後，確認 urls.py 中應該有預設好路徑：
```python=
urlpatterns = [
    path('admin/', admin.site.urls), #<-這個！
    ...
]
```
接著登入你的網站，後面加上 admin 路徑（如 http://localhost:8000/admin/ )，即可登入資料庫管理頁面。可以遠端查看、新增、刪除資料，但是無法直接匯入資料表。

![](https://i.imgur.com/O3kRBdc.png)

請注意，每在 models.py 中新增一個 class，就必須去你 APP 下的 admin.py 中讀入這個 class，才可以順利在管理介面看到你的資料，相關設定可以參考 [教學文件](https://developer.mozilla.org/zh-TW/docs/Learn/Server-side/Django/Admin_site)。
```python=
# admin.py
from <your_app> import models

class <your_admin_class>(admin.ModelAdmin): #客製化你的 admin 介面
    list_display = ('',...) #要顯示的欄位
    search_fields = ('',...) #能夠被搜尋的欄位
    list_filter = ('',...) #很難用的 filter，只適合種類不多時
    ordering = ('',...) #讓資料表用某個欄位預先排序
    
admin.site.register(models.<your_class>,<your_admin_class>) #這行一定要寫才能抓你的 model class，如果資料表很多的話可以改用 decorator 的方式
```
另外，網站實際上線到工作站的 Apache 上時，會無法順利讀取 admin 介面的 css，這是因為 Apache 需要透過 wsgi 讀取你的 Django project，但是 settings.py 中預設只去讀取 static 中的檔案。解決辦法，可以將虛擬環境中的 Django 套件中的 static 路徑找出來，丟進去你 project 的 static。

路徑一般會在 django/contrib/admin/static 中，如果不知道你的 Django 套件路徑在哪，請輸入以下指令:
```bash
$ python -c "import django; print(django.__path__)"
```

#### 匯入資料表
匯入資料表有幾種方式，第一是不使用資料庫，直接透過 pandas 來讀取資料；第二是使用第三方應用程式，例如 [DB Browser](https://sqlitebrowser.org/) 圖形化介面來存取資料庫；第三是利用 sqlite3 來下 SQL 指令。

#### [DB Browser](https://sqlitebrowser.org/) 方法
因為 CSV 本身沒有 data type 的描述，只有用 comma 來區分資料，所以如果直接用 DB Browser 來讀取，預設都會是 string。如果格式偵測失敗，就需要另外修改資料格式。

直接在 Database Structure 按下資料表，選擇 Modify Table，就可以修改特定 field 的名稱與格式。
![](https://i.imgur.com/GNBFqPN.png)

![](https://i.imgur.com/tSa4R95.png)

請注意，如果要將資料表給 Django 使用，必須設定 primary key 。只要選擇任一個 unique 欄位（ 或自己創建 index ），將 PK 欄位打勾就行。

![](https://i.imgur.com/Lgnr5XY.png)

匯入資料表後，如果要在 Django 使用 ORM 語法，我們還必須將欄位寫入 models.py 中。可以直接利用以下指令來自動完成 model：
```bash
$ python manage.py inspectdb > <your_app>/models.py
```

**注意：** 有人反應 inspectdb 會讀取資料格式失敗，特別是發生在 primary key 上。請在執行 inspectdb 後自己檢查一下所有 models.py 的設定都正確。

**補充：** 如果不自行設定 primary key，Django 會在某些 ORM 操作中失敗。可以透過 makemigrations、migrate 來產生資料庫設定檔，Django 會自己創一個欄位 id 作為 primary key。

#### [sqlite3](https://www.sqlite.org/cli.html) 方法
如果只想在 local 端匯入與設定資料庫，DB Browser 就夠用了。但如果要遠端連線，就必須另外學如何使用 SQL 指令。
- 安裝 sqlite3, ubuntu 下的 sqlite 管理程式, [sqlite3 官方說明文件](https://www.sqlite.org/cli.html)
    ```bash
    sudo apt install sqlite3
    ```
    操作方式, 匯入 csv 表格
    ```bash
    sqlite3 ./db.sqlite3
    ### 已進入 sqlite shell
    
    ### 可以直接匯入 .csv 但是所有欄位資料格式會是 TEXT
    sqlite> .mode csv
    sqlite> .import ./domain_map_id.csv domain_map_id
    
    ### 先建立 Table 再匯入, 可自訂欄位資料型態
    sqlite> CREATE TABLE domain_map_id(
              "domain_name" TEXT,
              "count" INTEGER,
              "systematic_name" TEXT,
              "domain_source" TEXT,
              "domain_description" TEXT,
              "interpro_id" TEXT
            );
    sqlite> .mode csv
    sqlite> .import ./domain_map_id.csv domain_map_id
    
    
    # 列出所有 table
    sqlite> .tables
    
    # 查看 table 內容
    sqlite> select * from table_name;
    
    # 查看 table 欄位
    sqlite> .schema table_name
    
    # 刪除 table 
    sqlite> drop table table_name;
    ```
- sqlite3 原生沒有支援改動欄位資料型態的指令，請參考 [ALTER TABLE Statement](https://www.techonthenet.com/sqlite/tables/alter_table.php)
#### [sqlite-web](https://github.com/coleifer/sqlite-web) 方法
可以透過網頁方式 GUI 介面管理 SQLite 資料庫
使用方式：
```bash=
sqlite_web /path/to/database.db
```
從本機端電腦建立 SSH Local Port Forwarding 連線到遠端電腦上
```bash=
ssh -L 8080:127.0.0.1:8080 cosbi20@140.116.214.151 -N
```
可以新建表格, 先自行添加欄位名稱和資料型態, 然後 import csv
![](https://i.imgur.com/kP56gZ5.png)

我通常只用來瀏覽資料頁面, 匯入資料表推薦用 `sqlite3`
![](https://i.imgur.com/kuZ7z45.png)

:::danger
建議大家不要用開放外部電腦連線進來的方式, 怕 SQLite 資料庫內容被亂搞
:::
### MySQL 
在網站跟資料庫都在同一台電腦上的情況，我建議用 Django 預設的 SQLite 就好，它是 local 端的資料庫檔案，內建在專案目錄底下 `db.sqlite3`。因為我們實驗室傳統用 MySQL，我特別講一下在自己電腦上該怎麼建立，如果要用 SQLite 的話可以自己去查教學，比 MySQL 步驟簡單很多。

在你的電腦安裝 MySQL
```bash=
sudo apt install -y mysql-server
```
安裝 MySQL 跟 Python 溝通用的工具
```bash=
sudo apt-get install -y python3-dev default-libmysqlclient-dev build-essential
```
在你的 Django 環境裡安裝 MySQL 連線工具
```bash=
pip install mysqlclient 
```
#### 創建 MySQL 使用者,資料庫,匯入資料表
進入 mysql shell
```bash=
sudo mysql -u root
```
創建使用者
```bash=
CREATE USER 'username'@'localhost' IDENTIFIED BY 'yourpassword';
```
建立 Database
```bash=
CREATE DATABASE my_db;

# 查看
show databases;
```
授予使用者存取資料庫權限
```bash=
GRANT ALL PRIVILEGES ON my_db.* TO 'username'@'localhost';
```
匯入資料表格，要懂每個參數的意義不然很容易出錯
```bash=
USE my_db;

# 先創建一個 table 欄位需要特別設定
CREATE TABLE table_name (
            id INT NOT NULL AUTO_INCREMENT,
            column_1 VARCHAR(255) NOT NULL,
            column_2 DATE NOT NULL,
            column_3 DECIMAL(10 , 2 ) NULL,
            column_4 INTEGER,
            PRIMARY KEY (id)
);

# 匯入資料表檔案到上面創建的 table 中
LOAD DATA INFILE '/home/cosbi/export_file.csv'
INTO TABLE table_name
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '/n'
IGNORE 1 ROWS;

# 查看資料表內容
SELECT * FROM table_name;
```
到 `settings.py` 加入 Database 設定
```python=
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql', 
        'NAME': 'my_db',
        'USER': 'username',
        'PASSWORD': 'yourpassword',
        'HOST': 'localhost',   # Or an IP Address that your DB is hosted on
        'PORT': '3306',
    }
}
```
匯入 MySQL 資料庫內容到 django models
```bash=
python manage.py inspectdb > ./mainPage/models.py
```
這樣終於可以透過 Django 的 model 操作資料庫了 :upside_down_face:
##### phpMyAdmin
可以讓你在網頁上透過圖形操作管理 MySQL 資料庫,上面教學是透過 MySQL command shell 操作

安裝教學: https://www.javahelps.com/2018/10/install-mysql-with-phpmyadmin-on-ubuntu.html
## SSH 連線
讓你在任何電腦都可以透過 Terminal 連線進你的實驗室電腦(在家連回實驗室好用)

- 設定跟 [讓外部連線](###讓外部連線) 一樣，得取得電腦 **Public IP** 還有 **Port** 對應
- SSH 的預設 port 是 22, 假設電腦上曾有 Router 必須設定對應到電腦的 port 22
- 這時候就看到 Tmux + Vim 的強大了，可以直接用 Terminal coding 和多種操作，不需要在其他電腦特別安裝文字編輯器，不會被裝置限制

安裝 SSH Server
```bash=
sudo apt install -y openssh-server 
```
連線方式(在其他電腦上)
```bash=
ssh username@140.116.214.151
```

### [FileZilla](https://filezilla-project.org/)
讓你在別台電腦存取實驗室電腦上檔案，跟暑假課程連實驗室 Server 方式一樣
- 連線方式記得選 sftp

### [VSCode Remote SSH](https://code.visualstudio.com/docs/remote/ssh)
你可能還是覺得 Vim 用起來超卡，違反人類直覺。其實 VSCode 也能透過遠端連線編輯別台電腦上的檔案，同步檔案內容。連結在標題裡了，直接安裝就好。
## Jupyter 
Jupyter notebook/lab 應用在資料處理上非常方便, 有很好的視覺化和執行部份程式碼 Debug 功能
Python 安裝:
```bash=
# 安裝 jupyter lab
pip install jupyterlab
# 安裝 jupyter notebook
pip install notebook
```
直接到想要開啟的資料夾下命令`jupyter`就開啟了 jupyter server, 如果要遠端連線的話必須透過 SSH Local Port Forwarding 
從遠端電腦下指令,把本機的 port 8888 跟遠端電腦的 port 8888 建立加密連線通道:
```bash=
ssh -L 8888:127.0.0.1:8888 cosbi20@140.116.214.151 -N
```
:::danger
建議大家不要自己嘗試 jupyter server 的遠端 http 連線功能, 沒有經過加密連線電腦很容易被入侵
:::
## 使用成大 SSL VPN 服務
老師要求每台電腦只開放成大網域連線(非成大網域無法連進實驗室電腦)，在家要使用成大網域連線得透過 VPN

https://cc.ncku.edu.tw/p/412-1002-7637.php?Lang=zh-tw
注意: 已在成大網域內無法使用

可用軟體登入, 也能用成大網頁登入
![](https://i.imgur.com/L36BvxW.png =50%x)

![](https://i.imgur.com/bONuQjd.png)

檢查是否連線成功:
![](https://i.imgur.com/0MH1mbm.png =70%x)

## 設定防火牆 (建議在本機端執行)
防火牆是使用ubuntu內建的ufw，這個大家的ubuntu裡都有但應該都沒有啟動，所以先下指令啟動
```bash=
sudo ufw enable
```
此時防火牆就會啟動，因為我是先啟動防火牆才安裝openssh，所以防火牆規則會自動加入，後啟動的不確定會發生什麼事，先看一下防火牆規則
```bash=
sudo ufw status verbose
```
此時應該會看到類似這樣的畫面
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22                         ALLOW IN    Anywhere                           
22 (v6)                    ALLOW IN    Anywhere (v6)
```
22是ssh預設的port，如果沒有的話也沒關係，等等會重寫規則。
首先先設定預設連線，我們先預設拒絕所有的外部連線，輸入
```bash=
sudo ufw default deny
```
再來設定port 22只允許校內網路登入，依序下指令
```bash=
#先允許校內ip可以連線到ssh port(22)
sudo ufw allow from 140.116.0.1/16 to any port 22
#再來禁止所有對ssh port(22)的存取
sudo ufw deny 22
```
這樣如果使用校外網路登入就會沒有回應，再來要使用django開放別人進入網站的話需要開放http/https，所以輸入指令
```bash=
#先開http就好
sudo ufw allow http
#https
sudo ufw allow https
```
如果都添加完成的話你的規則應該會像
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    140.116.0.0/16            
22                         ALLOW IN    140.116.0.0/16            
80/tcp                     ALLOW IN    Anywhere                  
443/tcp                    ALLOW IN    Anywhere                  
22/tcp                     DENY IN     Anywhere                  
80/tcp (v6)                ALLOW IN    Anywhere (v6)             
443/tcp (v6)               ALLOW IN    Anywhere (v6)             
22/tcp (v6)                DENY IN     Anywhere (v6)             

```
Port 80是http，port 443是https，要開放哪些port取決於你自己的軟體或服務，比如jupyter的預設port是8000或8888。

最後教一下刪除規則，假如有規則想要取消可以先透過指令來檢視規則的編號
```bash=
sudo ufw status numbered
```
會看到防火牆的規則跟編號，例如：
```
     To                         Action      From
     --                         ------      ----
[ 1] Anywhere                   ALLOW IN    140.116.0.0/16            
[ 2] 22                         ALLOW IN    140.116.0.0/16 
```
此時在下刪除指令並輸入規則編號
```bash=
sudo ufw delete 2
```
刪除前會再確認一次你的規則，輸入y後就會刪除
```
Deleting:
 allow from 140.116.0.0/16 to any port 22
Proceed with operation (y|n)?
```
防火牆的設定大概就到這樣

## WSL 使用
WSL (Windows Subsystem for Linux) 是 Windows 內建的簡易版 Linux，對於想練習 Linux 但又不想放棄 Windows 的人來說是個好選擇。

請用系統管理員身分開啟 cmd，輸入 `wsl.exe --install`，安裝完後重啟電腦，即可使用 WSL。
要使用 WSL，可以直接在 cmd 中輸入 `wsl` 來登入 Ubuntu，或是直接使用安裝好的 Ubuntu 應用程式（會是一個 Ubuntu Shell）。

在 WSL 中，你的 Windows 預設路徑會在 `/mnt/c/Users/<your_name>` ；在 Windows 中，你的 Ubuntu 路徑 **可能** 會在：
```
C:\Users\<your_name>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\LocalState\rootfs\home\<your_name>
```
路徑有點長，建議把它存起來，這樣就可以直接在 Windows 上開發你的專案。

### WSL 防火牆設定
在 WSL 中無法使用 ufw，你需要設定 Windows 的防火牆規則。
請在搜尋列中尋找「Windows Defender 防火牆」，按左邊的「進階設定」，打開「具有進階安全性的 Windows Defender 防火牆」。

點選「輸入規則」，再點選「新增規則」：
![](https://i.imgur.com/3Dqt95V.jpg)

點選「連接埠」
![](https://i.imgur.com/FB9X7IO.png)

設定你的 Port（例如 Django 預設使用 8000）
![](https://i.imgur.com/OJFUB6O.png)

之後都按照預設，選「允許連線」，並全部套用規則，再自行命名這個規則的名稱即可。
這樣就會讓這個 Port 對外打開。如果要限定學校 IP，需要進一步作設定。

請找到剛剛的新規則，點進去後，選擇「領域」，在「遠端 IP 位址」輸入允許的 IP（例如：140.116.0.0/16），按下確定。
![](https://i.imgur.com/ighKlJJ.png)

這樣就能順利擋下成大以外的 IP 。

**補充：** 如果你發現不論怎麼封鎖 IP，都還是擋不住，可能是防火牆中有其他規則覆蓋了你的設定。以我上面的例子，有一個規則叫 python3.8（我用來 runserver 的程式），它預設對外全部開啟，把它關閉後即可。

## Ubuntu 缺點
- Libre Office 難用, 可能習慣了 PowerPoint
- 沒有 Line , 可以裝 Chrome extension
## 網路資源
- [鳥哥私房菜 - Linux 基礎學習篇訓練教材](https://linux.vbird.org/linux_basic_train/centos8/)