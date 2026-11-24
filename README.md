# Go Web 框架对比

对比 Gin、Fiber、Go-Zero、Echo、Beego、Kratos、Iris、Chi、GoFrame、Buffalo、Hertz。只看框架自带能力，外接 GORM、robfig/cron、asynq 不算自带。

微服务的判定：框架自带服务间调用（gRPC / RPC），以及注册发现或治理，才算支持。把 HTTP 服务拆成多个进程，不算支持微服务。

Star、提交总数、最近提交由 shields.io 实时生成。提交总数徽章路径中的 `t` 表示全部提交，只统计默认分支，数字会缩写成 `2k` 这种数量级。最近提交徽章显示相对时间或月份，不显示完整的日期时间。

能力表按 2026-11-24 的 Star 从高到低排列，行序不随徽章后续变化重排。

## 总览

GitHub 会把表格里的图片压到列宽，列一多，Star 数字会被裁掉。徽标图片写了固定宽高。

| 框架 | 仓库 | 文档 | Star | 提交总数 | 最近提交 |
| --- | --- | --- | --- | --- | --- |
| Gin | [gin-gonic/gin](https://github.com/gin-gonic/gin) | [文档](https://gin-gonic.com/zh-cn/docs/) | <img alt="Github stars" src="https://img.shields.io/github/stars/gin-gonic/gin.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/gin-gonic/gin.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/gin-gonic/gin.svg" width="160" height="20"> |
| Fiber | [gofiber/fiber](https://github.com/gofiber/fiber) | [文档](https://docs.gofiber.io/) | <img alt="Github stars" src="https://img.shields.io/github/stars/gofiber/fiber.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/gofiber/fiber.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/gofiber/fiber.svg" width="160" height="20"> |
| Go-Zero | [zeromicro/go-zero](https://github.com/zeromicro/go-zero) | [文档](https://go-zero.dev/zh-cn/) | <img alt="Github stars" src="https://img.shields.io/github/stars/zeromicro/go-zero.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/zeromicro/go-zero.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/zeromicro/go-zero.svg" width="160" height="20"> |
| Echo | [labstack/echo](https://github.com/labstack/echo) | [文档](https://echo.labstack.com/docs) | <img alt="Github stars" src="https://img.shields.io/github/stars/labstack/echo.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/labstack/echo.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/labstack/echo.svg" width="160" height="20"> |
| Beego | [beego/beego](https://github.com/beego/beego) | [文档](https://beegodoc.com/zh/) | <img alt="Github stars" src="https://img.shields.io/github/stars/beego/beego.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/beego/beego.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/beego/beego.svg" width="160" height="20"> |
| Kratos | [go-kratos/kratos](https://github.com/go-kratos/kratos) | [文档](https://go-kratos.dev/zh-cn/docs/) | <img alt="Github stars" src="https://img.shields.io/github/stars/go-kratos/kratos.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/go-kratos/kratos.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/go-kratos/kratos.svg" width="160" height="20"> |
| Iris | [kataras/iris](https://github.com/kataras/iris) | [文档](https://iris-go.com/docs/index.html) | <img alt="Github stars" src="https://img.shields.io/github/stars/kataras/iris.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/kataras/iris.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/kataras/iris.svg" width="160" height="20"> |
| Chi | [go-chi/chi](https://github.com/go-chi/chi) | [文档](https://go-chi.io/) | <img alt="Github stars" src="https://img.shields.io/github/stars/go-chi/chi.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/go-chi/chi.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/go-chi/chi.svg" width="160" height="20"> |
| GoFrame | [gogf/gf](https://github.com/gogf/gf) | [文档](https://goframe.org/docs/micro-service) | <img alt="Github stars" src="https://img.shields.io/github/stars/gogf/gf.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/gogf/gf.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/gogf/gf.svg" width="160" height="20"> |
| Buffalo | [gobuffalo/buffalo](https://github.com/gobuffalo/buffalo) | [文档](https://gobuffalo.io/documentation/) | <img alt="Github stars" src="https://img.shields.io/github/stars/gobuffalo/buffalo.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/gobuffalo/buffalo.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/gobuffalo/buffalo.svg" width="160" height="20"> |
| Hertz | [cloudwego/hertz](https://github.com/cloudwego/hertz) | [文档](https://www.cloudwego.io/zh/docs/hertz/) | <img alt="Github stars" src="https://img.shields.io/github/stars/cloudwego/hertz.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/cloudwego/hertz.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/cloudwego/hertz.svg" width="160" height="20"> |

## 总结对比

数据反射指用反射把结构体与请求参数或数据库记录自动互转。行序与总览表一致。

| 框架 | 定位 | 数据库支持 | 数据反射 | 自带定时任务 | 自带队列 | 微服务 |
| --- | --- | --- | --- | --- | --- | --- |
| Gin | HTTP 路由与中间件 | 无 | 仅 HTTP 绑定 | 无 | 无 | 否 |
| Fiber | Express 风格，基于 fasthttp | 无 | 仅 HTTP 绑定 | 无 | 无 | 否 |
| Go-Zero | API + RPC 与服务治理 | MySQL、PostgreSQL、MongoDB，另有 Redis | HTTP 解析有反射；数据层由 goctl 生成，不做运行时 ORM 反射 | 无框架内 cron，官方文档使用 Kubernetes CronJob | 有。Kafka `kq`、Beanstalkd 延迟队列、RabbitMQ | 是。zRPC、etcd 发现、限流、熔断、降载 |
| Echo | 小核心 HTTP 框架 | 无 | 仅 HTTP 绑定 | 无 | 无 | 否 |
| Beego | 全栈 MVC | MySQL、SQLite、PostgreSQL、Oracle、TiDB | ORM 结构体反射 | 有。`task` 定时 / 周期任务 | 无 | 否 |
| Kratos | protobuf / gRPC + HTTP | 无 | protobuf 代码生成，无 ORM 反射 | 无 | 无 | 是。双协议、注册发现、限流、熔断 |
| Iris | MVC / HTTP 框架 | 无 | MVC 方法参数反射注入 | 无 | 无 | 否 |
| Chi | 贴近标准库的轻量路由 | 无 | 无内置参数绑定 | 无 | 无 | 否 |
| GoFrame | 全栈组件 | MySQL、MariaDB、TiDB、PostgreSQL、SQL Server、SQLite、Oracle、ClickHouse、达梦 | 请求、配置、gdb 全链路反射 | 有。`gcron` | 仅进程内 `gqueue`，无消息队列 | 是。v2.4+ 的 grpcx：gRPC、注册发现、负载均衡、链路追踪 |
| Buffalo | 全栈，自带 pop ORM | PostgreSQL、MySQL、SQLite、CockroachDB | pop model 反射 | 无 | 无 | 否 |
| Hertz | CloudWeGo 高性能 HTTP 框架 | 无 | 仅 HTTP 绑定 | 无 | 无 | 仅 HTTP 层。注册发现与 RPC 治理在 Kitex |

## 性能排序

数据来自 [the-benchmarker](https://web-frameworks-benchmark.vercel.app/frameworks/go/) 2026-11-05、concurrency 64 的空接口吞吐，单位是请求/秒。这项测试衡量 HTTP 框架开销，不含数据库和业务逻辑。Iris、Buffalo、Kratos 未被该基准收录。性能排名按请求/秒从高到低。

| 性能排名 | 框架 | 请求/秒 |
| --- | --- | --- |
| 1 | Fiber | 187,551 |
| 2 | Hertz | 187,380 |
| 3 | Echo | 114,313 |
| 4 | Gin | 111,896 |
| 5 | Chi | 108,537 |
| 6 | GoFrame | 105,504 |
| 7 | Go-Zero | 100,781 |
| 8 | Beego | 97,930 |
| 未收录 | Iris | — |
| 未收录 | Buffalo | — |
| 未收录 | Kratos | — |

## 数据库框架对比

beego orm 没有独立仓库，徽标用 [beego/beego](https://github.com/beego/beego)。gdb 没有独立仓库，徽标用 [gogf/gf](https://github.com/gogf/gf)。database/sql 是 Go 标准库，没有单独的 Star。

### 按 Star 排序

按 2026-11-24 各仓库 Star 从高到低。Star、提交总数、最近提交由 shields.io 实时生成。提交总数只统计默认分支，会缩写成数量级。最近提交显示相对时间或月份。

| 数据库框架 | 仓库 | 文档 | Star | 提交总数 | 最近提交 |
| --- | --- | --- | --- | --- | --- |
| gorm | [go-gorm/gorm](https://github.com/go-gorm/gorm) | [文档](https://gorm.io/zh_CN/docs/) | <img alt="Github stars" src="https://img.shields.io/github/stars/go-gorm/gorm.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/go-gorm/gorm.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/go-gorm/gorm.svg" width="160" height="20"> |
| beego orm | [beego/beego](https://github.com/beego/beego) | [文档](https://beegodoc.com/zh/v2.2.x/orm/) | <img alt="Github stars" src="https://img.shields.io/github/stars/beego/beego.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/beego/beego.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/beego/beego.svg" width="160" height="20"> |
| sqlc | [sqlc-dev/sqlc](https://github.com/sqlc-dev/sqlc) | [文档](https://docs.sqlc.dev/) | <img alt="Github stars" src="https://img.shields.io/github/stars/sqlc-dev/sqlc.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/sqlc-dev/sqlc.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/sqlc-dev/sqlc.svg" width="160" height="20"> |
| sqlx | [jmoiron/sqlx](https://github.com/jmoiron/sqlx) | [文档](https://jmoiron.github.io/sqlx/) | <img alt="Github stars" src="https://img.shields.io/github/stars/jmoiron/sqlx.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/jmoiron/sqlx.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/jmoiron/sqlx.svg" width="160" height="20"> |
| ent | [ent/ent](https://github.com/ent/ent) | [文档](https://entgo.io/zh/docs/getting-started) | <img alt="Github stars" src="https://img.shields.io/github/stars/ent/ent.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/ent/ent.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/ent/ent.svg" width="160" height="20"> |
| pgx | [jackc/pgx](https://github.com/jackc/pgx) | [文档](https://pkg.go.dev/github.com/jackc/pgx/v5) | <img alt="Github stars" src="https://img.shields.io/github/stars/jackc/pgx.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/jackc/pgx.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/jackc/pgx.svg" width="160" height="20"> |
| gdb | [gogf/gf](https://github.com/gogf/gf) | [文档](https://goframe.org/docs/core/gdb) | <img alt="Github stars" src="https://img.shields.io/github/stars/gogf/gf.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/gogf/gf.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/gogf/gf.svg" width="160" height="20"> |
| xorm | [go-xorm/xorm](https://github.com/go-xorm/xorm) | [文档](https://xorm.io/zh/docs/) | <img alt="Github stars" src="https://img.shields.io/github/stars/go-xorm/xorm.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/go-xorm/xorm.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/go-xorm/xorm.svg" width="160" height="20"> |
| bun | [uptrace/bun](https://github.com/uptrace/bun) | [文档](https://bun.uptrace.dev/guide/) | <img alt="Github stars" src="https://img.shields.io/github/stars/uptrace/bun.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/uptrace/bun.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/uptrace/bun.svg" width="160" height="20"> |
| pop | [gobuffalo/pop](https://github.com/gobuffalo/pop) | [文档](https://gobuffalo.io/documentation/database/) | <img alt="Github stars" src="https://img.shields.io/github/stars/gobuffalo/pop.svg" width="104" height="20"> | <img alt="Commits" src="https://img.shields.io/github/commit-activity/t/gobuffalo/pop.svg" width="100" height="20"> | <img alt="Last commit" src="https://img.shields.io/github/last-commit/gobuffalo/pop.svg" width="160" height="20"> |
| database/sql | [golang/go](https://github.com/golang/go/tree/master/src/database/sql) | [文档](https://pkg.go.dev/database/sql) | 标准库 | 标准库 | 标准库 |

### 按性能排序

数字来自 [efectn/go-orm-benchmarks](https://github.com/efectn/go-orm-benchmarks/blob/master/results.md)，2024-10-15 由 GitHub Actions 生成，无缓存。仓库作者注明这套结果有时会不准。排序依据是多行读取 `ReadSlice` 的 ns/op，越低越快。gdb 未进入该基准，放在最后。

反射指查询结果映射到结构体时是否走运行时反射。无反射表示手写 `Scan` 或代码生成。Web 框架一列只写本文对比过的框架里谁在用它。

| 数据库框架 | 类型 | 反射 | 支持的数据库 | 多行 ns/op | Web 框架 |
| --- | --- | --- | --- | --- | --- |
| pgx | 非 ORM | 无 | PostgreSQL | 247,183 | 无 |
| sqlc | 非 ORM | 无 | MySQL、PostgreSQL、SQLite | 259,784 | 无 |
| database/sql | 非 ORM | 无 | 由驱动决定，常见 MySQL、PostgreSQL、SQLite、SQL Server | 296,835 | 均可直接使用 |
| ent | ORM | 无 | MySQL、MariaDB、PostgreSQL、SQLite | 364,374 | Kratos |
| sqlx | 非 ORM | 有 | 由驱动决定，常见 MySQL、PostgreSQL、SQLite、SQL Server | 368,843 | Go-Zero |
| pop | ORM | 有 | PostgreSQL、MySQL、SQLite、CockroachDB | 381,803 | Buffalo |
| bun | ORM | 有 | PostgreSQL、MySQL、MariaDB、SQLite、SQL Server、Oracle | 414,916 | 无 |
| beego orm | ORM | 有 | MySQL、SQLite、PostgreSQL、Oracle、TiDB | 431,007 | Beego |
| gorm | ORM | 有 | MySQL、PostgreSQL、SQLite、SQL Server、TiDB、Oracle、GaussDB | 515,118 | Gin、Echo、Fiber、Chi、Hertz、Iris |
| xorm | ORM | 有 | MySQL、PostgreSQL、SQLite、SQL Server、Oracle | 566,538 | 无 |
| gdb | ORM | 有 | MySQL、MariaDB、TiDB、PostgreSQL、SQL Server、SQLite、Oracle、ClickHouse、达梦 | 未收录 | GoFrame |

0 反射的 pgx、sqlc、database/sql、ent 排在多行读取的前面。其中只有 ent 是 ORM。sqlx 不是 ORM，`StructScan` 有反射。

## 总结

### Web 框架

Star 和空接口吞吐不是同一套顺序。Star 最高的是 Gin，空接口吞吐最高的是 Fiber 和 Hertz，Hertz 的 Star 排在这 11 个框架的最后。GoFrame 的空接口吞吐接近 Chi，高于 Go-Zero 和 Beego。Iris、Buffalo、Kratos 没有进入这次 HTTP 基准。

Gin、Echo、Fiber、Chi、Iris、Hertz 负责路由和中间件，数据库、定时任务、队列和微服务治理要另外接。Beego 和 GoFrame 同时自带数据库反射和定时任务，队列都停在进程内，没有可持久化的消息队列。GoFrame、Go-Zero、Kratos 自带微服务能力。Go-Zero 还带 Kafka、Beanstalkd、RabbitMQ 这一类队列集成，数据访问靠 goctl 生成，不靠运行时 ORM 反射。

要快速做 HTTP 接口，Gin 的生态最大，Fiber 和 Hertz 的空接口更快。要框架自己带上 ORM、定时任务和微服务，GoFrame 更完整。要现成的服务治理和消息队列，Go-Zero 更合适。

### 数据库框架

Star 最高的是 gorm，它用反射做结构体映射。多行读取里更快的是 0 反射的 pgx、sqlc、database/sql，其次是同样 0 反射的 ent。gorm、xorm、beego orm、pop、bun 这些反射 ORM 都排在后面。行数变多时，反射要逐行填字段，耗时和分配会跟着涨。

更偏向 0 反射。查询代码交给 AI 写就行，手写 `Scan` 或让 sqlc、ent 生成类型安全的代码，并不比在反射 ORM 里配 tag 更费事。换来的是多行查询更少的运行时开销，字段和 SQL 在编译期就能对上。PostgreSQL 可以选 pgx 或 sqlc。要同时覆盖 MySQL、PostgreSQL、SQLite，sqlc 和 ent 更合适。ent 仍然是 ORM，只是映射不走运行时反射。database/sql 加上对应驱动，数据库种类最宽，查询仍是 0 反射。

反射 ORM 适合已经大量使用 gorm、gdb 的项目。新写的查询路径，优先 sqlc、ent 或 pgx。
