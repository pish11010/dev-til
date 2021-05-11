# [TIL] Slack Github 연동 시 Pull Request 관련 메세지 안오는 경우
### 문제 
Slack App Github(Legacy)에서 Github 신규 앱으로 업데이트한 이후 일부 메세지는 정상적으로 날아오는데, PR merge, close, ready for review 메세지가 날아오지 않았다.
### 해결
Github project의 Settings > Integrations > (Installed GitHub Apps) Slack > Configure 에서 권한을 주면 해결된다.
<img width="792" alt="slack github permission" src="https://user-images.githubusercontent.com/8031779/117750169-ef2f1c00-b24d-11eb-989f-a6a15afe30e7.png">
