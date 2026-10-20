# ZNote - LazyCat App

[ZNote](https://github.com/helloxz/znote)（小而美的纯笔记应用，原生支持 Markdown 所见即所得）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`helloz/znote` 镜像经 `docker.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 semver tag，发现新版本自动构建发布。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 说明

- 单容器（Bun + SQLite），笔记数据 `/lzcapp/var/znote:/app/data`
- 首次访问引导创建管理员账号；多用户最多 5 人，注册开关在部署参数（`ZNOTE_ALLOW_REGISTER`）
- 忘记管理员密码：在数据卷 `touch data/reset.txt` 后重启，重置端点开启一次
- 健康检查 `/`

## 设置向导参数

| 参数 | 说明 |
| --- | --- |
| 开放注册 | 是否允许新用户注册（默认关闭，仅管理员创建的账号可登录） |

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

AGPL-3.0（上游）
