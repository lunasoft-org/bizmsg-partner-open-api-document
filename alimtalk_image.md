# 알림톡 이미지 업로드 API

## Domain

- 운영: https://bizmsg-open-api.blumn.ai
- 개발: https://obt-bizmsg-api.blumn.ai

## Authentication Header

- userId: {user_id}

---

## 1. 알림톡 템플릿 이미지 업로드

알림톡 템플릿에서 사용하는 **상단 이미지**를 업로드합니다.

### Endpoint
- METHOD: POST
- URL: /v1/image/alimtalk/template

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 이미지 파일 1개 (jpg, jpeg, png / 최대 500KB) |
| imageNickname | string | N | 이미지 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image=@template.png" \
  -F "imageNickname=template_image_1" \
  https://bizmsg-open-api.blumn.ai/v1/image/alimtalk/template
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageUrl": "https://mud-kage.kakao.com/dn/example/template_image.jpg",
    "imageName": "template.png"
  },
  "message": null
}
```

### Example Fail Response

```json
{
  "code": "fail",
  "data": null,
  "message": "image is required"
}
```

---

## 2. 알림톡 아이템 이미지 업로드

아이템 리스트형 알림톡에서 사용하는 **아이템 하이라이트 이미지**를 업로드합니다.

### Endpoint
- METHOD: POST
- URL: /v1/image/alimtalk/itemHighlight

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 이미지 파일 1개 (jpg, jpeg, png / 최대 500KB) |
| imageNickname | string | N | 이미지 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image=@item.png" \
  -F "imageNickname=item_highlight_1" \
  https://bizmsg-open-api.blumn.ai/v1/image/alimtalk/itemHighlight
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageUrl": "https://mud-kage.kakao.com/dn/example/item_image.jpg",
    "imageName": "item.png"
  },
  "message": null
}
```

### Example Fail Response

```json
{
  "code": "fail",
  "data": null,
  "message": "image is required"
}
```
