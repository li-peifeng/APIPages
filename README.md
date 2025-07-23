#  iNoi API Token Generator

## 项目说明

用于 iNoi 获取部分网盘API的接口和页面

## 部署方法

### 一键部署

#### EdgeOne Functions
[![使用 EdgeOne Pages 部署](https://cdnstatic.tencentcs.com/edgeone/pages/deploy.svg)](https://edgeone.ai/pages/new?repository-url=https://github.com/li-peifeng/APIPages)

部署完成后，请登录[EdgeOne Functions后台](https://console.tencentcloud.com/edgeone/pages)，修改环境变量，请参考[变量说明](#变量说明)部分


#### EdgeOne Functions 中国站
[![使用 EdgeOne Pages 部署](https://cdnstatic.tencentcs.com/edgeone/pages/deploy.svg)](https://console.cloud.tencent.com/edgeone/pages/new?project-name=oplist-api&repository-url=https://github.com/OpenListTeam/OpenList-APIPages&build-command=npm%20run%20build-eo&install-command=npm%20install&output-directory=public&root-directory=./&env=MAIN_URLS)

部署完成后，请登录[EdgeOne Functions后台](https://console.cloud.tencent.com/edgeone/pages)，修改环境变量，请参考[变量说明](#变量说明)部分


#### Cloudflare Worker
[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/li-peifeng/APIPages)

部署完成后，请登录Cloudflare Worker后台，修改环境变量，请参考[变量说明](#变量说明)部分

### 手动部署

#### 克隆代码

```shell
git clone https://github.com/li-peifeng/APIPages.git
```

#### 修改配置

创建并修改`wrangler.jsonc`

```shell
cp wrangler.example.jsonc wrangler.jsonc
```

修改变量信息：
 - MAIN_URLS：部署回调地址的域名
 - 其他参数?：各个网盘的应用信息
```
  "vars": {
    "MAIN_URLS": "api.example.com",
    "onedrive_uid": "*****************************",
    "onedrive_key": "*****************************",
    "alicloud_uid": "*****************************",
    "alicloud_key": "*****************************",
    "baiduyun_uid": "*****************************",
    "baiduyun_key": "*****************************",
    "baiduyun_ext": "*****************************",
    "cloud115_uid": "*****************************",
    "cloud115_key": "*****************************",
    "googleui_uid": "*****************************",
    "googleui_key": "*****************************",
    "yandexui_uid": "*****************************",
    "yandexui_key": "*****************************",
    "dropboxs_uid": "*****************************",
    "dropboxs_key": "*****************************",
    "quarkpan_uid": "*****************************",
    "quarkpan_key": "*****************************"
  },
```


### Docker部署
#### 拉取镜像
```
docker pull leolitaly/api_server
```
or
```
docker pull ghcr.io/leolitaly/api_server:latest
```
#### 启动项目
```
docker run -d --name api-server \
  -p 3000:3000 \
  -e OPLIST_MAIN_URLS="api.example.com" \
  -e OPLIST_PROXY_API="gts.example.com" \
  -e OPLIST_ONEDRIVE_UID= `#optional` \
  -e OPLIST_ONEDRIVE_KEY= `#optional` \
  -e OPLIST_ALICLOUD_UID= `#optional` \
  -e OPLIST_ALICLOUD_KEY= `#optional` \
  -e OPLIST_BAIDUYUN_UID= `#optional` \
  -e OPLIST_BAIDUYUN_KEY= `#optional` \
  -e OPLIST_BAIDUYUN_EXT= `#optional` \
  -e OPLIST_CLOUD115_UID= `#optional` \
  -e OPLIST_CLOUD115_KEY= `#optional` \
  -e OPLIST_GOOGLEUI_UID= `#optional` \
  -e OPLIST_GOOGLEUI_KEY= `#optional` \
  -e OPLIST_YANDEXUI_UID= `#optional` \
  -e OPLIST_YANDEXUI_KEY= `#optional` \
  -e OPLIST_DROPBOXS_UID= `#optional` \
  -e OPLIST_DROPBOXS_KEY= `#optional` \
  -e OPLIST_QUARKPAN_UID= `#optional` \
  -e OPLIST_QUARKPAN_KEY= `#optional` \
  openlistteam/openlist_api_server:latest 
```
- 可以替换镜像为ghcr:
  ```
  ghcr.io/leolitaly/api_server:latest
  ```
- **请务必根据下面的环境变量，修改你使用的环境变量**

#### 环境变量说明

| 变量名称       | 必要 | 变量类型 | 变量说明                     |
| -------------- | ---- | -------- |--------------------------|
| `OPLIST_MAIN_URLS`    | 是   | string   | 绑定主域名，示例：api.example.com |
| `OPLIST_PROXY_API`    | 否   | string   | 部署在大陆的节点需要指定代理谷歌  |
| `OPLIST_ONEDRIVE_UID` | 否   | string   | OneDrive 客户端ID           |
| `OPLIST_ONEDRIVE_KEY` | 否   | string   | OneDrive 客户端密钥           |
| `OPLIST_ALICLOUD_UID` | 否   | string   | 阿里云盘开发者AppID             |
| `OPLIST_ALICLOUD_KEY` | 否   | string   | 阿里云盘开发者AppKey            |
| `OPLIST_BAIDUYUN_UID` | 否   | string   | 百度网盘应用UID                |
| `OPLIST_BAIDUYUN_KEY` | 否   | string   | 百度网盘应用密钥AppKey           |
| `OPLIST_BAIDUYUN_EXT` | 否   | string   | 百度网盘应用SecretKey          |
| `OPLIST_CLOUD115_UID` | 否   | string   | 115网盘应用ID                |
| `OPLIST_CLOUD115_KEY` | 否   | string   | 115网盘应用密钥                |
| `OPLIST_GOOGLEUI_UID` | 否   | string   | 谷歌客户端ID                  |
| `OPLIST_GOOGLEUI_KEY` | 否   | string   | 谷歌全局API Key              |
| `OPLIST_YANDEXUI_UID` | 否   | string   | Yandex应用ID               |
| `OPLIST_YANDEXUI_KEY` | 否   | string   | Yandex应用密钥               |
| `OPLIST_DROPBOXS_UID` | 否   | string   | Dropboxx应用ID             |
| `OPLIST_DROPBOXS_KEY` | 否   | string   | Dropbox应用密钥              |
| `OPLIST_QUARKPAN_UID` | 否   | string   | 夸克云盘x应用ID                |
| `OPLIST_QUARKPAN_KEY` | 否   | string   | 夸克云盘应用密钥                 |


### 边缘部署

#### 克隆代码

```shell
git clone https://github.com/OpenListTeam/OpenList-APIPages.git
```

#### 修改配置 (CloudFlare才需要)

创建并修改`wrangler.jsonc`

```shell
cp wrangler.example.jsonc wrangler.encrypt.jsonc
```

修改变量信息：
 - MAIN_URLS：部署回调地址的域名
 - 其他参数?：各个网盘的应用信息
```
  "vars": {
    "MAIN_URLS": "api.example.com",
    "PROXY_API": "gts.example.com",
    "onedrive_uid": "*****************************",
    "onedrive_key": "*****************************",
    "alicloud_uid": "*****************************",
    "alicloud_key": "*****************************",
    "baiduyun_uid": "*****************************",
    "baiduyun_key": "*****************************",
    "baiduyun_ext": "*****************************",
    "cloud115_uid": "*****************************",
    "cloud115_key": "*****************************",
    "googleui_uid": "*****************************",
    "googleui_key": "*****************************",
    "yandexui_uid": "*****************************",
    "yandexui_key": "*****************************",
    "dropboxs_uid": "*****************************",
    "dropboxs_key": "*****************************",
    "quarkpan_uid": "*****************************",
    "quarkpan_key": "*****************************"
  },
```

### 变量说明

| 变量名称       | 必要 | 变量类型 | 变量说明              |
| -------------- | ---- | -------- |-------------------|
| `MAIN_URLS`    | 是   | string   | 绑定主域名，示例：api.example.com |
| `PROXY_API`    | 否   | string   | 部署在大陆的节点需要指定代理谷歌  |
| `onedrive_uid` | 否   | string   | OneDrive 客户端ID           |
| `onedrive_key` | 否   | string   | OneDrive 客户端密钥           |
| `alicloud_uid` | 否   | string   | 阿里云盘开发者AppID             |
| `alicloud_key` | 否   | string   | 阿里云盘开发者AppKey            |
| `baiduyun_uid` | 否   | string   | 百度网盘应用ID                |
| `baiduyun_key` | 否   | string   | 百度网盘应用密钥AppKey        |
| `baiduyun_ext` | 否   | string   | 百度网盘应用密钥SecretKey        |
| `cloud115_uid` | 否   | string   | 115网盘应用ID                |
| `cloud115_key` | 否   | string   | 115网盘应用密钥                |
| `googleui_uid` | 否   | string   | 谷歌客户端ID                  |
| `googleui_key` | 否   | string   | 谷歌全局API Key              |
| `yandexui_uid` | 否   | string   | Yandex应用ID               |
| `yandexui_key` | 否   | string   | Yandex应用密钥               |
| `dropboxs_uid` | 否   | string   | Dropboxx应用ID             |
| `dropboxs_key` | 否   | string   | Dropbox应用密钥              |
| `quarkpan_uid` | 否   | string   | 夸克云盘x应用ID                |
| `quarkpan_key` | 否   | string   | 夸克云盘应用密钥                 |


#### 测试代码

```shell
npm install

# 以Cloudflare Worker环境运行 
npm run dev-cf

# 以Edgeone Functions环境运行 
npm run dev-eo

# 以Node Service Work环境运行 
npm run dev-js

```

#### 部署项目

```shell
# 以Cloudflare Worker环境部署
npm run deploy-cf

# 以Edgeone Functions环境部署 
npm run deploy-eo 
```