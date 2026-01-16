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

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 이미지 파일 1개 (jpg, jpeg, png / 최대 500KB) |
| imageNickname | string | N | 이미지 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image=@sample.png" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/default
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageName": "sample.png",
    "imageNickname": "",
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

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 와이드 이미지 1개 |
| imageNickname | string | N | 이미지 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image=@wide.png" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/wide
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageName": "wide.png",
    "imageNickname": "",
    "imageUrl": "https://..."
  },
  "message": ""
}
```

---

## 3. 와이드 리스트 타입 첫 번째 이미지 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/wideItemList/first

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image | file | Y | 대표 이미지 1개 |
| imageNickname | string | N | 이미지 닉네임 |

### Example CURL

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image=@first.png" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/wideItemList/first
```

### Example Success Response

```json
{
  "code": "success",
  "data": {
    "imageName": "first.png",
    "imageNickname": "",
    "imageUrl": "https://..."
  },
  "message": ""
}
```

---

## 4. 와이드 리스트 타입 이미지 리스트 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/wideItemList

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image_1 | file | Y | 이미지 파일 1 |
| imageNickname_1 | string | N | 이미지 1 닉네임 |
| image_2 | file | N | 이미지 파일 2 |
| imageNickname_2 | string | N | 이미지 2 닉네임 |
| image_3 | file | N | 이미지 파일 3 |
| imageNickname_3 | string | N | 이미지 3 닉네임 |

### Example CURL (2개 요청)

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image_1=@item1.png" \
  -F "image_2=@item2.png" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/wideItemList
```

### Example Success Response (부분 성공)

```json
{
  "code": "success",
  "data": {
    "success": [
      {
        "formField": "image_1",
        "imgName": "item1.png",
        "imageNickname": "",
        "imageUrl": "https://..."
      }
    ],
    "failure": [
      {
        "formField": "image_2",
        "imgName": "item2.png",
        "imageNickname": "",
        "message": "invalid image file"
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

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image_1 | file | Y | 캐러셀 이미지 |
| imageNickname_1 | string | N | 이미지 닉네임 |
| image_2 | file | N | 캐러셀 이미지 |
| imageNickname_2 | string | N | 이미지 닉네임 |
| ... | ... | ... | 최대 image_10 까지 가능 |

### Example CURL (2개 요청)

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image_1=@carousel1.png" \
  -F "image_2=@carousel2.png" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/carouselFeed
```

### Example Success Response (부분 성공)

```json
{
  "code": "success",
  "data": {
    "success": [
      {
        "formField": "image_1",
        "imgName": "carousel1.png",
        "imageNickname": "",
        "imageUrl": "https://..."
      }
    ],
    "failure": [
      {
        "formField": "image_2",
        "imgName": "carousel2.png",
        "imageNickname": "",
        "message": "invalid image file"
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

## 6. 캐러셀 커머스 타입 이미지 업로드

### Endpoint
- METHOD: POST
- URL: /v1/direct/image/carouselCommerce

### Request Body

| 키 | 데이터 타입 | 필수 | 설명 |
|----|------------|------|------|
| image_1 | file | Y | 커머스 이미지 |
| imageNickname_1 | string | N | 이미지 닉네임 |
| image_2 | file | N | 커머스 이미지 |
| imageNickname_2 | string | N | 이미지 닉네임 |
| ... | ... | ... | 최대 image_10 까지 가능 |

### Example CURL (2개 요청)

```bash
curl -X POST \
  -H "userId: {user_id}" \
  -F "image_1=@commerce1.png" \
  -F "image_2=@commerce2.png" \
  https://bizmsg-open-api.blumn.ai/v1/direct/image/carouselCommerce
```

### Example Success Response (부분 성공)

```json
{
  "code": "success",
  "data": {
    "success": [
      {
        "formField": "image_1",
        "imgName": "commerce1.png",
        "imageNickname": "",
        "imageUrl": "https://..."
      }
    ],
    "failure": [
      {
        "formField": "image_2",
        "imgName": "commerce2.png",
        "imageNickname": "",
        "message": "invalid image file"
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
