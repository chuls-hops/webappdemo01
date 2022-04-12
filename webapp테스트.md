### az cli 로그인 

```
az login
To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code SJA9HBCQS to authenticate.
```

### 구독 설정 
```
az account set --subscription ff597581-bae8-4d02-ab7b-aaa3fd964297
```

### webapp 배포 
- 현재 webapp은 배포 되어있는 상태 webapp이름은 skwinwebapp23, 리소스그룹은 webapp23으로 생성됨



### 패키지 실행사용 설정
```
az webapp config appsettings set --resource-group webapp23 --name skwinwebapp23 --settings WEBSITE_RUN_FROM_PACKAGE="1"

root@user23-bastion-vm1:~/webapp# az webapp config appsettings set --resource-group webapp23 --name skwinwebapp23 --settings WEBSITE_RUN_FROM_PACKAGE="1"
[
  {
    "name": "WEBSITE_RUN_FROM_PACKAGE",
    "slotSetting": false,
    "value": "1"
  }
]
```
#### 패키지 배포 실행
```
az webapp deployment source config-zip --resource-group webapp23 --name skwinwebapp23  --src demo.zip


root@user23-bastion-vm1:~/webapp# az webapp config appsettings set --resource-group webapp23 --name skwinwebapp23 --settings WEBSITE_RUN_FROM_PACKAGE="1"
[
  {
    "name": "WEBSITE_RUN_FROM_PACKAGE",
    "slotSetting": false,
    "value": "1"
  }
]
root@user23-bastion-vm1:~/webapp# az webapp deployment source config-zip --resource-group webapp23 --name skwinwebapp23  --src demo.zip
Getting scm site credentials for zip deployment
Starting zip deployment. This operation can take a while to complete ...
Deployment endpoint responded with status code 202
{
  "active": true,
  "author": "N/A",
  "author_email": "N/A",
  "complete": true,
  "deployer": "Push-Deployer",
  "end_time": "2022-04-12T06:18:38.941891Z",
  "id": "5dfc2bee-7366-450a-8716-e2b6da2a096d",
  "is_readonly": true,
  "is_temp": false,
  "last_success_end_time": "2022-04-12T06:18:38.941891Z",
  "log_url": "https://skwinwebapp23.scm.azurewebsites.net/api/deployments/latest/log",
  "message": "Created via a push deployment",
  "progress": "",
  "received_time": "2022-04-12T06:18:35.8686685Z",
  "site_name": "skwinwebapp23",
  "start_time": "2022-04-12T06:18:37.1767968Z",
  "status": 4,
  "status_text": "",
  "url": "https://skwinwebapp23.scm.azurewebsites.net/api/deployments/latest"
}
root@user23-bastion-vm1:~/webapp# 
```

#### 배포된 웹앱을 브라우저에서 확인

- https://skwinwebapp23.azurewebsites.net

