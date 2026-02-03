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

## 2. 일회용 인증 토큰 요청

OBT 환경 메시지 수신을 위한 일회용 인증 토큰 요청

### Endpoint
- METHOD: GET
- URL: /v2/partner/test/user/token

### Example CURL
```
curl -X GET \
  'https://obt-bizmsg-api.blumn.ai/v2/partner/test/user/token?phoneNumber=01000000000'
```

### Example Success Response
```
{
  "code":"success",
  "data": {
    "expiredAt": "2026-02-03 14:04:13"
  },
  "message":null
}
```

### Example Fail Response
```
{
  "code":" fail",
  "data": null,
  "message": "요청을 처리하는 중 문제가 발생했습니다."
}
```

## 3. 일회용 인증 시도

OBT 환경 메시지 수신을 위한 일회용 인증 시도

### Endpoint
- METHOD: GET
- URL: /v2/partner/test/user/certify

### Example CURL
```
curl -X POST \
  'https://obt-bizmsg-api.blumn.ai/v2/partner/test/user/certify?phoneNumber=01000000000&token=000000'
```

### Example Success Response
```
{
  "code":"success",
  "data": {
    "expiredAt": "2026-02-04 00:00:00"
  },
  "message":null
}
```

### Example Fail Response
```
{
  "code":" fail",
  "data": null,
  "message": "요청을 처리하는 중 문제가 발생했습니다."
}
```
