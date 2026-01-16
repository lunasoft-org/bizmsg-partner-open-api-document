# 개발 제공 API

## Domain

- 개발: https://obt-bizmsg-api.blumn.ai

## Authentication Header

- userId: {user_id}

---

## 1. 알림톡 템플릿 승인

심사중인 알림톡 템플릿을 승인상태로 변경합니다.

### Endpoint
- METHOD: GET
- URL: /v2/partner/test/template/approve

### Example CURL
```
curl -X GET \
  -H 'userId: {user_id}' \
  'https://obt-bizmsg-api.blumn.ai/v2/partner/test/template/approve?senderKey=2a1ea83fb57b2c21096f994d1ab3091b0dac3c63&templateCode=template_001
```

### Example Success Response
```
{
  "code":"success",
  "data":"template_001",
  "message":null
}
```

### Example Fail Response
```
{
  "code":"fail",
  "data":"template_001",
  "message":"senderKey is required"
}
```
