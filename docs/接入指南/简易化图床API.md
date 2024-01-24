# 简易化 图床 API
?> OceanStorage 在基于业务令牌的 API 基础上，尽最大努力提供了一套兼容原 OceanPic 的 **基于 API KEY 的图床 API**，并在最大兼容的基础上砍去了一部分功能。绝大多数基于原 OceanPic 的业务都可以无痛地继续使用本系统。

## 与原 OceanPic 系统的兼容性

| 功能                                 | 兼容性 |
| -------------                       | --------|
| Test 接口                             | ×    |
| API KEY                             | √    |
| 通过文件上传图片                     | √    |
| 通过 base64 编码上传图片               | √    |
| 获取用户图册下所有图片的数量          | √    |
| 获取用户图册下的所有图片（分页查询）   | √    |
| 获取用户图册下的所有图片（非分页查询） | ×    |
| 通过 ID 删除图片                    | √    |
| 上传时智能压缩图片                   | ×    |
| 分发图片到其他站点                   | ×    |
| 获取图片的缩略图版本                 | √    |
| 自动识别并返回图片的WebP版本          | ×    |

## 兼容格式
".JPG", ".JPEG", ".PNG", ".GIF", ".SVG", ".WEBP", ".BMP", ".ICO", ".APNG", ".AVIF", ".TIFF"

缩略图功能兼容格式：
'png', 'jpg', 'jpeg', 'gif', 'bmp'（不兼容的格式将返回原图）


# 接口文档

## POST uploadImg

POST /upload/img

> Body 请求参数

```yaml
img: string

```

### 请求参数

| 名称   | 位置   | 类型           | 必选 | 说明 |
| ------ | ------ | -------------- | ---- | ---- |
| apikey | header | string         | 是   | none |
| body   | body   | object         | 否   | none |
| » img  | body   | string(binary) | 是   | none |

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

| 状态码 | 状态码含义                                              | 说明 | 数据模型 |
| ------ | ------------------------------------------------------- | ---- | -------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功 | Inline   |

### 返回数据结构

## POST uploadImgBase64

POST /upload/imgbase64

> Body 请求参数

```yaml
img: data:image/png;base64,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

```

### 请求参数

| 名称   | 位置   | 类型   | 必选 | 说明 |
| ------ | ------ | ------ | ---- | ---- |
| apikey | header | string | 是   | none |
| body   | body   | object | 否   | none |
| » img  | body   | string | 是   | none |

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

| 状态码 | 状态码含义                                              | 说明 | 数据模型 |
| ------ | ------------------------------------------------------- | ---- | -------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功 | Inline   |

### 返回数据结构

## GET img

GET /image/170591732124461

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

| 状态码 | 状态码含义                                              | 说明 | 数据模型 |
| ------ | ------------------------------------------------------- | ---- | -------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功 | Inline   |

### 返回数据结构

## GET deleteImg

GET /image/delete_img

### 请求参数

| 名称   | 位置   | 类型   | 必选 | 说明 |
| ------ | ------ | ------ | ---- | ---- |
| img_id | query  | string | 是   | none |
| ApiKey | header | string | 是   | none |

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

| 状态码 | 状态码含义                                              | 说明 | 数据模型 |
| ------ | ------------------------------------------------------- | ---- | -------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功 | Inline   |

### 返回数据结构

## GET imgCount

GET /image/get_img_count

### 请求参数

| 名称   | 位置   | 类型   | 必选 | 说明 |
| ------ | ------ | ------ | ---- | ---- |
| ApiKey | header | string | 是   | none |

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

| 状态码 | 状态码含义                                              | 说明 | 数据模型 |
| ------ | ------------------------------------------------------- | ---- | -------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功 | Inline   |

### 返回数据结构

## GET getAllImg

GET /image/get_all_imgs

### 请求参数

| 名称     | 位置   | 类型   | 必选 | 说明 |
| -------- | ------ | ------ | ---- | ---- |
| page     | query  | string | 是   | none |
| pageSize | query  | string | 是   | none |
| ApiKey   | header | string | 是   | none |

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

| 状态码 | 状态码含义                                              | 说明 | 数据模型 |
| ------ | ------------------------------------------------------- | ---- | -------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功 | Inline   |

### 返回数据结构