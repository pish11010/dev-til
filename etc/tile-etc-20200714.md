# [TIL] 안드로이드 Zendesk SDK 연동 시 Ticket CustomField가 이상할 경우

안드로이드 앱에 Zendesk SDK를 활용하여 유저의 Feedback을 관리할 수 있다.

Zendesk SDK 연동은 [공식 문서](https://developer.zendesk.com/embeddables/docs/android-support-sdk/sdk_add)를 참고하면 쉽게 붙일 수 있다.

연동 이후 Ticket은 정상적으로 들어오지만 CustomField가 안들어오는 증상이 발생했다.
글을 쓴 계기이며 해당 문제에는 2가지 원인이 있었다.

### 1. Proguard 이슈
debug build에서는 정상적으로 들어가지만 release build에서는 생성이 CustomField가 빠져서 들어왔다.

proguard 관련 이슈로 [공식문서의 Use Progruad](https://developer.zendesk.com/embeddables/docs/android-support-sdk/use_proguard)내용을 참고해서 필요한 것들을 추가하면 문제 없이 해결되는 듯 보인다.

### 2. Zendesk Ticket Fields(CustomField) 권한 처리
일부 CustomField는 정상적으로 들어오지만 몇몇 CustomField가 빠져서 기록되었다.

Ticket Field의 자체 Permission 문제로 앱 에서 코드로 처리할 것은 없고 Zendesk 에서 설정해주면 된다.
`zendesk > admin home` 화면에서 `MANAGE - Ticket Fields` 로 이동한다.
Ticket Field 리스트에서 기록되지 않는 Filed를 선택하여 Edit 화면으로 이동하면 Permissions가 있고 아마 `Agent only`로 되어있을 것이다. 이 부분을 `Editable for end users`로 설정하면 된다.

![0_0Ze3c0ynfTG1485r](https://user-images.githubusercontent.com/8031779/117903436-82c62280-b30a-11eb-98fa-f4902435b64f.png)
