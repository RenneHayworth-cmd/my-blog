# My Blog

这是一个本地 WordPress 博客项目。WordPress 用 Docker 在本地运行，GitHub 用来保存文章草稿、配置说明、自定义主题和自定义插件代码。

## 本地运行

确认已经安装 Docker Desktop 或 Docker Engine，然后在项目目录执行：

```bash
cp .env.example .env
docker compose up -d
```

访问地址：

- 博客前台：http://localhost:8080
- WordPress 后台：http://localhost:8080/wp-admin
- phpMyAdmin：http://localhost:8081

第一次打开 `http://localhost:8080` 时，按页面提示完成 WordPress 初始化。

## 默认数据库配置

本地开发默认账号只用于本机：

```text
Database: wordpress
User: wordpress
Password: wordpress
Root password: wordpress_root
Host: db
```

正式部署时不要沿用这些密码。

## 项目结构

```text
my-blog/
├── docker-compose.yml       # 本地 WordPress + MySQL + phpMyAdmin
├── README.md                # 项目说明
├── content/
│   ├── drafts/              # Markdown 草稿
│   ├── published/           # 已发布文章备份
│   └── ideas.md             # 选题池
├── wordpress/
│   └── config-notes.md      # WordPress 配置记录
├── wp-content/
│   ├── themes/              # 自定义主题
│   ├── plugins/             # 自定义插件
│   └── mu-plugins/          # 必须启用插件
├── assets/
│   └── images/              # 文章图片和素材
└── docs/
    ├── deployment.md        # 部署记录
    └── maintenance.md       # 维护说明
```

## 推荐写作流程

1. 在 `content/drafts/` 里写 Markdown 草稿。
2. 修改完成后复制到 WordPress 后台发布。
3. 发布后的最终版归档到 `content/published/`。
4. 主题、插件和配置变化记录到仓库。

## 适合提交到 GitHub 的内容

- `README.md`
- `docker-compose.yml`
- `content/`
- `docs/`
- `wordpress/`
- `assets/images/`
- `wp-content/themes/` 中自己的主题
- `wp-content/plugins/` 中自己的插件

## 不适合提交到 GitHub 的内容

- 数据库文件
- `.env` 和任何密码
- WordPress 核心文件
- `wp-content/uploads/` 中的运行时上传文件
- 缓存、日志和备份包

## 常用命令

启动：

```bash
docker compose up -d
```

停止：

```bash
docker compose down
```

查看运行状态：

```bash
docker compose ps
```

查看日志：

```bash
docker compose logs -f wordpress
```

如果要连数据库，可以打开：

```text
http://localhost:8081
```
