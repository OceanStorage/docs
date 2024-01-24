# OpenOceanStorage 开放 API 文档

Base URLs:

* <a href="http://storage.codesocean.top">OceanStorage环境: http://storage.codesocean.top</a>

## GET 获取所有容器

GET /api/v2/resource/getContainers

### Params

| Name          | Location | Type    | Required | Description |
| ------------- | -------- | ------- | -------- | ----------- |
| ServiceKey | header   | string | yes      | none        |
| startId       | query    | integer | no       | none        |
| rows          | query    | integer | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## GET 通过ID获取容器信息

GET /api/resource/getContainerInfoById

> Body Parameters

```yaml
{}

```

### Params

| Name          | Location | Type   | Required | Description |
| ------------- | -------- | ------ | -------- | ----------- |
| ServiceKey | header   | string | yes      | none        |
| containerId   | query    | string | yes      | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## GET 通过容器ID获取所有资源

GET /api/resource/getResourcesByContainerId

> Body Parameters

```yaml
{}

```

### Params

| Name          | Location | Type   | Required | Description |
| ------------- | -------- | ------ | -------- | ----------- |
| ServiceKey | header   | string | yes      | none        |
| containerId   | query    | string | yes      | none        |
| startId       | query    | string | yes      | none        |
| rows          | query    | string | yes      | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## POST 上传资源到容器

POST /api/resource/upload

> Body Parameters

```yaml
file: file://C:\Users\RicePaste\Pictures\图片1.png

```

### Params

| Name          | Location | Type           | Required | Description  |
| ------------- | -------- | -------------- | -------- | ------------ |
| ServiceKey | header   | string | no      | none        |
| container     | query    | string         | yes      | none         |
| rename        | query    | string         | no       | 不需要后缀名 |
| » file        | body     | string(binary) | yes      | none         |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## GET 通过ID下载资源

GET /api/resource/download/{resourceId}

> Body Parameters

```yaml
{}

```

### Params

| Name       | Location | Type   | Required | Description |
| ---------- | -------- | ------ | -------- | ----------- |
| ServiceKey | header   | string | no      | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## GET 通过ID获取资源（直接嵌入到页面中）

GET /api/resource/get/{resourceId}

> Body Parameters

```yaml
{}

```

### Params

| Name       | Location | Type   | Required | Description |
| ---------- | -------- | ------ | -------- | ----------- |
| ServiceKey | header   | string | no      | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## POST 新建容器

POST /api/resource/createNewContainer

> Body Parameters

```yaml
containerName: string
permissionLevel: string

```

### Params

| Name              | Location | Type   | Required | Description |
| ----------------- | -------- | ------ | -------- | ----------- |
| ServiceKey | header   | string | yes      | none        |
| » containerName   | body     | string | no       | none        |
| » permissionLevel | body     | string | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## POST 编辑容器信息

POST /api/resource/editContainerInfo

> Body Parameters

```yaml
containerId: string
containerName: string
permissionLevel: string

```

### Params

| Name              | Location | Type   | Required | Description |
| ----------------- | -------- | ------ | -------- | ----------- |
| ServiceKey | header   | string | yes      | none        |
| » containerId     | body     | string | no       | none        |
| » containerName   | body     | string | no       | none        |
| » permissionLevel | body     | string | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## POST 重命名资源

POST /api/resource/rename/{resourceId}

> Body Parameters

```yaml
rename: 测试

```

### Params

| Name          | Location | Type   | Required | Description  |
| ------------- | -------- | ------ | -------- | ------------ |
| » rename      | body     | string | yes      | 不需要后缀名 |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema

## POST 删除资源

POST /api/resource/delete/{resourceId}

> Body Parameters

```yaml
{}

```

### Params

| Name          | Location | Type   | Required | Description |
| ------------- | -------- | ------ | -------- | ----------- |
| ServiceKey | header   | string | yes      | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | 成功        | Inline      |

### Responses Data Schema