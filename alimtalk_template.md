# 알림톡 템플릿 관리 API

## 공통 정보

### Domain
- 운영: https://bizmsg-open-api.blumn.ai
- 개발: https://obt-bizmsg-api.blumn.ai

### 인증 헤더
- userId: {user_id}

---

## 1. 템플릿 카테고리 리스트 조회

### Endpoint
- METHOD: GET
- URL: /v2/template/category/all

### Example CURL
```
curl -X GET \
  -H 'userId: {user_id}' \
  https://bizmsg-open-api.blumn.ai/v2/template/category/all
```

### Example Success Response
```
{
  "code": "success",
  "message": "",
  "data": {
    "firstBusinessType": [
      {
        "parentCode": "",
        "code": "001",
        "groupName": "회원",
        "name": "",
        "inclusion": "",
        "exclusion": ""
      }
    ],
    "secondBusinessType": [
      {
        "parentCode": "001",
        "code": "001",
        "groupName": "회원",
        "name": "회원가입",
        "inclusion": "회원가입 완료 내용의 템플릿이 대상입니다. 가입에 따른 축하적립금/쿠폰을 포함합니다.",
        "exclusion": "상품/서비스가입은 구매 > 상품가입 (002002)로 분류합니다."
      }
    ]
  }
}
```

---

## 2. 템플릿 생성

### Endpoint
- METHOD: POST
- URL: /v2/template/create

### Example CURL (기본형)

```
curl -X POST \
  -H 'userId: {user_id}' \
  -H 'Content-type: application/json' \
  -d '[
  {
    "senderKey": "2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
    "senderKeyType": "S",
    "templateCode": "template_001",
    "templateName": "템플릿 명",
    "templateMessageType": "BA",
    "templateEmphasizeType": "NONE",
    "templateContent": "템플릿 내용",
    "categoryCode": "001001",
    "buttons": [
      {
        "ordering": 1,
        "linkType": "WL",
        "name": "웹링크버튼",
        "linkMo": "http: //www.sweettracker.co.kr"
      },
      {
        "ordering": 2,
        "linkType": "AL",
        "name": "앱링크버튼",
        "linkIos": "daumapps: //open",
        "linkAnd": "daumapps: //open"
      },
      {
        "ordering": 3,
        "linkType": "DS",
        "name": "배송 조회하기"
      }
    ],
    "quickReplies": [
      {
        "name": "봇키워드",
        "linkType": "BK",
        "linkTypeName": "봇키워드"
      },
      {
        "name": "바로가기",
        "linkType": "WL",
        "linkTypeName": "웹링크",
        "linkMo": "http: //daum.net",
        "linkPc": null,
        "linkIos": null,
        "linkAnd": null
      }
    ]
  }
]' \ƒ
  https://bizmsg-open-api.blumn.ai/v2/template/create
```

### Example CURL (아이템 리스트형)

```
curl -X POST \
  -H 'userId: {user_id}' \
  -H 'Content-type: application/json' \
  -d '[
  {
    "senderKey": "2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
    "senderKeyType": "S",
    "templateCode": "template_001",
    "templateName": "템플릿 명",
    "templateMessageType": "BA",
    "templateEmphasizeType": "NONE",
    "templateContent": "템플릿 내용",
    "categoryCode": "001001",
    "templateImageUrl": "{알림톡 상단 이미지 url}",
    "templateHeader": "템플릿헤더",
    "templateItemHighlight": {
      "title": "타이틀",
      "description": "디스크립션",
      "imageUrl": "{알림톡 상단 이미지 url}"
    },
    "templateItem": {
      "list": [
        {
          "title": "아이템 명 1",
          "description": "#{아이템내용 1}"
        },
        {
          "title": "아이템 명 2",
          "description": "#{아이템내용 2}"
        },
        {
          "title": "아이템 명 3",
          "description": "#{아이템내용 3}"
        }
      ],
      "summary": {
        "title": "아이템 명",
        "description": "#{price}"
      }
    },
    "buttons": [
      {
        "ordering": 1,
        "linkType": "WL",
        "name": "웹링크버튼",
        "linkMo": "http://www.sweettracker.co.kr"
      },
      {
        "ordering": 2,
        "linkType": "AL",
        "name": "앱링크버튼",
        "linkIos": "daumapps://open",
        "linkAnd": "daumapps://open"
      },
      {
        "ordering": 3,
        "linkType": "DS",
        "name": "배송 조회하기"
      }
    ],
    "quickReplies": [
      {
        "name": "봇키워드",
        "linkType": "BK",
        "linkTypeName": "봇키워드"
      },
      {
        "name": "바로가기",
        "linkType": "WL",
        "linkTypeName": "웹링크",
        "linkMo": "http://daum.net",
        "linkPc": null,
        "linkIos": null,
        "linkAnd": null
      }
    ]
  }
]' \
  https://bizmsg-open-api.blumn.ai/v2/template/create
```

### Example Success Response
```
[
  {
    "code":"success",
    "data":"template_001",
    "message":null
  }
]
```

### Example Fail Response
```
[
  {
    "code":"fail",
    "data":"template_001",
    "message":"senderKey is required"
  }
]
```

---

## 3. 템플릿 수정

### Endpoint
- METHOD: POST
- URL: /v2/template/update

### Example CURL
```
curl -X POST \
  -H 'userId: {user_id}' \
  -H 'Content-type: application/json' \
  -d '{
  "senderKey": "2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
  "senderKeyType": "S",
  "templateCode": "template_002",
  "newSenderKey": "2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
  "newTemplateCode": "template_003",
  "newTemplateName": "테스트템플릿",
  "newTemplateMessageType": "BA",
  "newTemplateEmphasizeType": "NONE",
  "newTemplateContent": "템플릿 내용",
  "newButtons": [
    {
      "ordering": 1,
      "linkType": "WL",
      "name": "웹링크버튼",
      "linkMo": "http://www.sweettracker.co.kr"
    },
    {
      "ordering": 2,
      "linkType": "AL",
      "name": "앱링크버튼",
      "linkIos": "daumapps://open",
      "linkAnd": "daumapps://open"
    },
    {
      "ordering": 3,
      "linkType": "DS",
      "name": "배송 조회하기"
    }
  ]
}' \
  https://bizmsg-open-api.blumn.ai/v2/template/update
```

### Example Success Response
```
[
  {
    "code":"success",
    "data":"template_001",
    "message":null
  }
]
```

### Example Fail Response
```
[
  {
    "code":"fail",
    "data":"template_001",
    "message":"senderKey is required"
  }
]
```

---

## 4. 템플릿 조회

### Endpoint
- METHOD: GET
- URL: /v2/template

### Example CURL
```
curl -X GET \
  -H 'userId: {user_id}' \
  'https://bizmsg-open-api.blumn.ai/v2/template?senderKey=2a1ea83fb57b2c21096f994d1ab3091b0dac3c63&templateCode=template_001'
```

### Example Success Response
```
{
  "code": "success",
  "data": {
    "buttonsJson": [
      {
        "ordering": 1,
        "pluginId": null,
        "telNumber": null,
        "name": "웹링크버튼",
        "linkType": "WL",
        "linkTypeName": "웹링크",
        "bizFormId": null,
        "linkMo": "https://google.com",
        "linkPc": null,
        "linkIos": null,
        "linkAnd": null
      },
      {
        "ordering": 2,
        "pluginId": null,
        "telNumber": null,
        "name": "앱링크버튼",
        "linkType": "AL",
        "linkTypeName": "앱링크",
        "bizFormId": null,
        "linkMo": null,
        "linkPc": null,
        "linkIos": "https://google.com",
        "linkAnd": "https://google.com"
      }
    ],
    "quickRepliesJson": [],
    "templateItemHighlightJson": null,
    "templateItemJson": null,
    "buttons": "[\n  {\n    \"ordering\": 1,\n    \"pluginId\": null,\n    \"telNumber\": null,\n    \"name\": \"\\uC6F9\\uB9C1\\uD06C\\uBC84\\uD2BC\",\n    \"linkType\": \"WL\",\n    \"linkTypeName\": \"\\uC6F9\\uB9C1\\uD06C\",\n    \"bizFormId\": null,\n    \"linkMo\": \"https://google.com\",\n    \"linkPc\": null,\n    \"linkIos\": null,\n    \"linkAnd\": null\n  },\n  {\n    \"ordering\": 2,\n    \"pluginId\": null,\n    \"telNumber\": null,\n    \"name\": \"\\uC571\\uB9C1\\uD06C\\uBC84\\uD2BC\",\n    \"linkType\": \"AL\",\n    \"linkTypeName\": \"\\uC571\\uB9C1\\uD06C\",\n    \"bizFormId\": null,\n    \"linkMo\": null,\n    \"linkPc\": null,\n    \"linkIos\": \"https://google.com\",\n    \"linkAnd\": \"https://google.com\"\n  }\n]",
    "quickReplies": "[]",
    "templateItemHighlight": null,
    "templateItem": null,
    "active": true,
    "buttonName": null,
    "buttonType": null,
    "buttonUrl": null,
    "pcFlag": true,
    "inspectDt": "2026-01-14T11:07:21",
    "inspectReqDt": null,
    "senderKey": "bbdd541128e2562d367c2622a1e1a004be5f7585",
    "senderKeyType": "S",
    "templateCode": "template_0.006115688391153951",
    "templateName": "템플릿 명 0.006115688391153951",
    "templateMessageType": "BA",
    "templateEmphasizeType": "NONE",
    "templateContent": "템플릿 내용",
    "inspectionStatus": "APR",
    "createdAt": "2026-01-14 11:07:21",
    "modifiedAt": "2026-01-14 11:15:11",
    "status": "R",
    "block": false,
    "dormant": false,
    "securityFlag": false,
    "categoryCode": "001001",
    "comments": [
      {
        "id": 35734,
        "content": null,
        "userName": "센터 API",
        "createdAt": "2026-01-14 11:07:22",
        "status": "APR",
        "attachment": []
      }
    ]
  },
  "message": ""
}
```

### Example Fail Response
```
{
  "code":"fail",
  "data":null,
  "message":"존재하지 않는 템플릿 코드입니다."
}
```

---

## 5. 템플릿 검수 요청

### Endpoint
- METHOD: POST
- URL: /v2/template/request

### Example CURL
```
curl -X POST \
  -H 'userId: {user_id}' \
  -H 'Content-type: application/json' \
  -d '[
    {
      "senderKey":"2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
      "templateCode":"template_001",
      "senderKeyType":"S"
    }
  ]' \
  https://bizmsg-open-api.blumn.ai/v2/template/request
```

### Example Success Response
```
[
  {
    "code":"success",
    "data":"template_001",
    "message":null
  }
]
```

### Example Fail Response
```
[
  {
    "code":"fail",
    "data":"template_001",
    "message":"요청을 처리할 수 있는 상태가 아님"
  }
]
```

---

## 6. 템플릿 검수 요청 (파일 첨부)

### Endpoint
- METHOD: POST
- URL: /v2/template/request_with_file

### Example CURL
```
curl -X POST \
  -H 'userId: {user_id}' \
  -F 'senderKey=2a1ea83fb57b2c21096f994d1ab3091b0dac3c63' \
  -F 'senderKeyType=S' \
  -F 'templateCode=template_001' \
  -F 'comment=해당 템플릿은 회원가입 인증 시 발송되는 메시지 입니다.' \
  -F 'attachment=@/증빙자료1.jpg' \
  -F 'attachment=@/증빙자료2.pdf' \
  https://bizmsg-open-api.blumn.ai/v2/template/request_with_file
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
  "message":"png, jpg, jpeg, gif, pdf, hwp, doc, docx 파일만 첨부할 수 있습니다."
}
```

---

## 7. 템플릿 검수 요청 취소

### Endpoint
- METHOD: POST
- URL: /v2/template/cancel_request

### Example CURL
```
curl -X POST \
  -H 'userId: {user_id}' \
  -H 'Content-type: application/json' \
  -d '[
    {
      "senderKey":"2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
      "templateCode":"template_001",
      "senderKeyType":"S"
    }
  ]' \
  https://bizmsg-open-api.blumn.ai/v2/template/cancel_request
```

### Example Success Response
```
[
  {
    "code":"success",
    "data":"template_001",
    "message":null
  }
]
```

### Example Fail Response
```
[
  {
    "code":"fail",
    "data":"template_001",
    "message":"요청을 처리할수 있는 상태가 아님"
  }
]
```

---

## 8. 템플릿 삭제

### Endpoint
- METHOD: POST
- URL: /v2/template/delete

### Example CURL
```
curl -X POST \
  -H 'userId: {user_id}' \
  -H 'Content-type: application/json' \
  -d '[
    {
      "senderKey":"2a1ea83fb57b2c21096f994d1ab3091b0dac3c63",
      "templateCode":"template_001",
      "senderKeyType":"S"
    }
  ]' \
  https://bizmsg-open-api.blumn.ai/v2/template/delete
```

### Example Success Response
```
[
  {
    "code":"success",
    "data":"template_001",
    "message":null
  }
]
```

### Example Fail Response
```
[
  {
    "code":"fail",
    "data":"template_001",
    "message":"삭제할 수 없는 상태입니다."
  }
]
```

---

## 9. 최근 수정된 템플릿 조회

### Endpoint
- METHOD: GET
- URL: /v2/template/last_modified

### Example CURL
```
curl -X GET \
  -H 'userId: {user_id}' \
  'https://bizmsg-open-api.blumn.ai/v2/template/last_modified?since=2025-01-01 00:00:00&page=1'
```

### Example Success Response
```
{
  "code":"success",
  "data":[
    {
      "templateCode":"template_001",
      "modifiedAt":"2025-01-10 14:22:11"
    }
  ],
  "message":null
}
```

### Example Fail Response
```
{
  "code":"fail",
  "data":null,
  "message":"잘못된 요청입니다."
}
```
