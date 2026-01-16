# 브랜드 메시지 이미지 업로드 API

## Domain

- 운영: https://bizmsg-open-api.blumn.ai
- 개발: https://obt-bizmsg-api.blumn.ai

## Authentication Header

- userId: {user_id}

---

## 1. 기본 이미지 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/default

### Request Header
- Content-Type: multipart/form-data

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 이미지 파일 (jpg, jpeg, png / 최대 500KB) |
| imageNickname | string | Y | 이미지 식별용 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image=@sample.png" \
  -F "imageNickname=sample" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/default
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageName": "sample.png",
    "imageNickname": "sample",
    "imageUrl": "https://..."
  },
  "message": ""
}
```

### Example Fail Response

```json
{
  "code": "fail",
  "data": "",
  "message": "image is required"
}
```

---

## 2. 와이드 이미지 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/wide

### Request Header
- Content-Type: multipart/form-data

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 와이드 이미지 파일 |
| imageNickname | string | Y | 이미지 식별용 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image=@wide.png" \
  -F "imageNickname=wide" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/wide
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageName": "wide.png",
    "imageNickname": "wide",
    "imageUrl": "https://..."
  },
  "message": ""
}
```

### Example Fail Response

```json
{
  "code": "fail",
  "data": "",
  "message": "image is required"
}
```

---

## 3. 와이드 리스트 타입 첫 번째 이미지 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/wideItemList/first

### Request Header
- Content-Type: multipart/form-data

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 와이드 리스트 대표 이미지 |
| imageNickname | string | Y | 이미지 식별용 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image=@item1.png" \
  -F "imageNickname=item1" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/wideItemList/first
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageName": "item1.png",
    "imageNickname": "item1",
    "imageUrl": "https://..."
  },
  "message": ""
}
```

### Example Fail Response

```json
{
  "code": "fail",
  "data": "",
  "message": "image is required"
}
```

---

## 4. 와이드 리스트 타입 이미지 리스트 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/wideItemList

### Request Header
- Content-Type: multipart/form-data

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image_1 | file | Y | 이미지 파일 #1 |
| imageNickname_1 | string | Y | 이미지 #1 닉네임 |
| image_2 | file | N | 이미지 파일 #2 |
| imageNickname_2 | string | N | 이미지 #2 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image_1=@item1.png" \
  -F "imageNickname_1=item1" \
  -F "image_2=@item2.png" \
  -F "imageNickname_2=1234567890123456789012345678901" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/wideItemList
```

### Example Success Response  
(image_1 성공, image_2 실패)

```json
{
  "code": "success",
  "data": {
    "success": [
      {
        "formField": "image_1",
        "imgName": "item1.png",
        "imageNickname": "item1",
        "imageUrl": "https://..."
      }
    ],
    "failure": [
      {
        "formField": "image_2",
        "imgName": "item2.png",
        "imageNickname": "1234567890123456789012345678901",
        "message": "imageNickname is invalid.(len = 31)"
      }
    ]
  },
  "message": ""
}
```

### Example Fail Response

```json
{
  "code": "fail",
  "data": "",
  "message": "image is required"
}
```

---

## 5. 캐러셀 피드 타입 이미지 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/carouselFeed

### Request Header
- Content-Type: multipart/form-data

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image_1 | file | Y | 캐러셀 피드 이미지 |
| imageNickname_1 | string | Y | 이미지 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image_1=@carousel.png" \
  -F "imageNickname_1=carousel" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/carouselFeed
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "success": [
      {
        "formField": "image_1",
        "imgName": "carousel.png",
        "imageNickname": "carousel",
        "imageUrl": "https://..."
      }
    ],
    "failure": []
  },
  "message": ""
}
```

### Example Fail Response

```json
{
  "code": "fail",
  "data": "",
  "message": "image is required"
}
```

---

## 6. 캐러셀 커머스 타입 이미지 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/carouselCommerce

### Request Header
- Content-Type: multipart/form-data

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image_1 | file | Y | 커머스 이미지 #1 |
| imageNickname_1 | string | Y | 이미지 #1 닉네임 |
| image_2 | file | N | 커머스 이미지 #2 |
| imageNickname_2 | string | N | 이미지 #2 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image_1=@commerce1.png" \
  -F "imageNickname_1=commerce1" \
  -F "image_2=@commerce2.png" \
  -F "imageNickname_2=commerce2" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/carouselCommerce
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "success": [
      {
        "formField": "image_1",
        "imgName": "commerce1.png",
        "imageNickname": "commerce1",
        "imageUrl": "https://..."
      }
    ],
    "failure": []
  },
  "message": ""
}
```

### Example Fail Response

```json
{
  "code": "fail",
  "data": "",
  "message": "image is required"
}
```
