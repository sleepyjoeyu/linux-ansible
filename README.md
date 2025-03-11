# linux-ansible 

## 注意事項
1. 所有測試以RHEL做為標的，如果有不同系統，對應指令可能需要替換
2. 所有playbook預設以root身份執行，如需利用一般user+sudo提權，需再做調整
3. 請注意Playbook以蒐集系統資訊為主，可以任意下載、使用或調整，但也無後續支援擔保

## 目錄說明

demo-videos： Ansible Automation Platform template執行playbook的展示影片 </br>
samples： 執行playbook後的產出文件範例

## Playbooks 說明
package-check.yaml
- 功用：輸入關鍵字，搜尋Linux系統中有無符合之RPM套件與程序，並將結果整理為一文檔傳出
- 變數：
    - target: "關鍵字"
    -  package_store_file: "整理文檔"
    - store_host: "傳到那一主機上"
- 指令範例：
   - `ansible-playbook  -i ../hosts-local package-check.yml -e target=ssh -e store_host=node1`

svc-check.yml
- 功用：給一串服務清單，透過systemctl檢查Linux系統有無啟用，並將"未"啟用服務紀錄於一文檔傳出
- 變數：
   - services_list: "服務1 服務2 服務N"
   - svc_store_file: "整理文檔"
   - store_host: "傳到那一主機上"
- 指令範例：
    - `ansible-playbook  -i ../hosts-local svc-check.yml -e 'services_list="httpd sshd vsftpd nothing"' -e store_host=node1 -v
`
      
user-check.yml
- 功用：搜尋Linux系統中，UID=0(Root)與UID>=1000(後面添加User)，並將結果整理為一文檔傳出
- 變數：
    - user_store_file: "整理文檔"
    - store_host: "傳到那一主機上"
- 指令範例：
  - `ansible-playbook  -i ../hosts-local user-check.yml -e store_host=node1`    


machine-check.yml
- 功用：蒐集主機基本資訊，包含主機CPU, RAM, Disks, Network, OS與Kernel版本，並將結果整理為一文檔傳出
- 變數：
    - machine_store_file: "整理文檔"
    - store_host: "傳到那一主機上"
- 指令範例：
  - `ansible-playbook  -i ../hosts-local machine-check.yml -e store_host=node1`    

health-check.yml
- 功用：蒐集系統基本檢康資訊，包含last reboot, 當日errlog, 現在disk free，並將結果整理為一文檔傳出
- 變數：
    - health_store_file: "整理文檔"
    - store_host: "傳到那一主機上"
- 指令範例：
  - `ansible-playbook  -i ../hosts-local health-check.yml -e store_host=node1`    
