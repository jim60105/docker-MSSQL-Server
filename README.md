# MSSQL on Docker + 手動、定時備份

## 設定

> 如果備份位置在網坊，請使用CIFS分支

1. 請參考 `*.env_sample` 建立 `*.env`
   - `SA_PWD`: 您的資料庫SA密碼
   - `CIFS_OPTION`: user=您網路芳鄰的帳號,password=您網路芳鄰的密碼 (此為CIFS分支才會用的設定)
   - `BACKUP_FOLDER`: 資料庫同步目錄路徑，必須是絕對位置\
     例 `D:\docker-MSSQL-Server\backup`、`//192.168.0.1/backup`
1. 編輯 `docker-compose.yml`
   - 如果要備份，把下方的backup service取消註解
   - 如果要還原，把下方的restore service取消註解
1. ```docker-compose up -d```

## 手動執行備份、還原

backup、restore container在執行完畢就會停掉，只要start container就會執行作業

- 查看container名稱並啟動\
  ```docker ps -a```\
  ```docker start docker-mssql-server_backup_1```\
  ```docker start docker-mssql-server_restore_1```

- 由Windows Docker Desktop啟動
![2021-06-21 11 53 10](https://user-images.githubusercontent.com/16995691/122706292-2d2a5180-d28a-11eb-823d-ef62172104f8.png)
