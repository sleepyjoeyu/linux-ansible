# linux-ansible
package-check.yaml
- 功用：輸入關鍵字，搜尋Linux系統中有無符合之RPM套件與程序，並將結果整理為一文檔傳出
- 變數：
    - target: "關鍵字"
    - store_file: "整理文檔"
    - store_host: "傳到那一主機上"

svc-check.yml
- 功用：給一串服務清單，透過systemctl檢查Linux系統有無啟用，並將"未"啟用服務紀錄於一文檔傳出
- 變數：
   - services_list: "服務1 服務2 服務N"
   - store_file: "整理文檔"
   - store_host: "傳到那一主機上"

user-check.yml
- 功用：搜尋Linux系統中，UID=0(Root)與UID>=1000(後面添加User)，並將結果整理為一文檔傳出
- 變數：
    - store_file: "整理文檔"
    - store_host: "傳到那一主機上"
