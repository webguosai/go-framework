# Go Web 框架对比

对比 Gin、Fiber、Go-Zero、Echo、Beego、Kratos、Iris、Chi、GoFrame、Buffalo、Hertz。只看框架自带能力，外接 GORM、robfig/cron、asynq 不算自带。

微服务的判定：框架自带服务间调用（gRPC / RPC），以及注册发现或治理，才算支持。把 HTTP 服务拆成多个进程，不算支持微服务。

Star、提交总数、最近提交由 shields.io 实时生成。提交总数徽章路径中的 `t` 表示全部提交，只统计默认分支，数字会缩写成 `2k` 这种数量级。最近提交徽章显示相对时间或月份，不显示完整的日期时间。

能力表按 2026-11-24 的 Star 从高到低排列，行序不随徽章后续变化重排。

## 总览

| 框架 | Star | 提交总数 | 最近提交 | 仓库 | 文档 | 定位 | 微服务 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Gin | ![Github stars](https://img.shields.io/github/stars/gin-gonic/gin.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/gin-gonic/gin.svg) | ![Last commit](https://img.shields.io/github/last-commit/gin-gonic/gin.svg) | [gin-gonic/gin](https://github.com/gin-gonic/gin) | [文档](https://gin-gonic.com/zh-cn/docs/) | HTTP 路由与中间件 | 否 |
| Fiber | ![Github stars](https://img.shields.io/github/stars/gofiber/fiber.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/gofiber/fiber.svg) | ![Last commit](https://img.shields.io/github/last-commit/gofiber/fiber.svg) | [gofiber/fiber](https://github.com/gofiber/fiber) | [文档](https://docs.gofiber.io/) | Express 风格，基于 fasthttp | 否 |
| Go-Zero | ![Github stars](https://img.shields.io/github/stars/zeromicro/go-zero.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/zeromicro/go-zero.svg) | ![Last commit](https://img.shields.io/github/last-commit/zeromicro/go-zero.svg) | [zeromicro/go-zero](https://github.com/zeromicro/go-zero) | [文档](https://go-zero.dev/zh-cn/) | API + RPC 与服务治理 | 是。zRPC、etcd 发现、限流、熔断、降载 |
| Echo | ![Github stars](https://img.shields.io/github/stars/labstack/echo.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/labstack/echo.svg) | ![Last commit](https://img.shields.io/github/last-commit/labstack/echo.svg) | [labstack/echo](https://github.com/labstack/echo) | [文档](https://echo.labstack.com/docs) | 小核心 HTTP 框架 | 否 |
| Beego | ![Github stars](https://img.shields.io/github/stars/beego/beego.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/beego/beego.svg) | ![Last commit](https://img.shields.io/github/last-commit/beego/beego.svg) | [beego/beego](https://github.com/beego/beego) | [文档](https://beegodoc.com/zh/) | 全栈 MVC | 否 |
| Kratos | ![Github stars](https://img.shields.io/github/stars/go-kratos/kratos.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/go-kratos/kratos.svg) | ![Last commit](https://img.shields.io/github/last-commit/go-kratos/kratos.svg) | [go-kratos/kratos](https://github.com/go-kratos/kratos) | [文档](https://go-kratos.dev/zh-cn/docs/) | protobuf / gRPC + HTTP | 是。双协议、注册发现、限流、熔断 |
| Iris | ![Github stars](https://img.shields.io/github/stars/kataras/iris.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/kataras/iris.svg) | ![Last commit](https://img.shields.io/github/last-commit/kataras/iris.svg) | [kataras/iris](https://github.com/kataras/iris) | [文档](https://iris-go.com/docs/index.html) | MVC / HTTP 框架 | 否 |
| Chi | ![Github stars](https://img.shields.io/github/stars/go-chi/chi.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/go-chi/chi.svg) | ![Last commit](https://img.shields.io/github/last-commit/go-chi/chi.svg) | [go-chi/chi](https://github.com/go-chi/chi) | [文档](https://go-chi.io/) | 贴近标准库的轻量路由 | 否 |
| GoFrame | ![Github stars](https://img.shields.io/github/stars/gogf/gf.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/gogf/gf.svg) | ![Last commit](https://img.shields.io/github/last-commit/gogf/gf.svg) | [gogf/gf](https://github.com/gogf/gf) | [文档](https://goframe.org/docs/micro-service) | 全栈组件 | 是。v2.4+ 的 grpcx：gRPC、注册发现、负载均衡、链路追踪 |
| Buffalo | ![Github stars](https://img.shields.io/github/stars/gobuffalo/buffalo.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/gobuffalo/buffalo.svg) | ![Last commit](https://img.shields.io/github/last-commit/gobuffalo/buffalo.svg) | [gobuffalo/buffalo](https://github.com/gobuffalo/buffalo) | [文档](https://gobuffalo.io/documentation/) | 全栈，自带 pop ORM | 否 |
| Hertz | ![Github stars](https://img.shields.io/github/stars/cloudwego/hertz.svg) | ![Commits](https://img.shields.io/github/commit-activity/t/cloudwego/hertz.svg) | ![Last commit](https://img.shields.io/github/last-commit/cloudwego/hertz.svg) | [cloudwego/hertz](https://github.com/cloudwego/hertz) | [文档](https://www.cloudwego.io/zh/docs/hertz/) | CloudWeGo 高性能 HTTP 框架 | 仅 HTTP 层。注册发现与 RPC 治理在 Kitex |

## 总结对比

数据反射指用反射把结构体与请求参数或数据库记录自动互转。行序与总览表一致。

| 框架 | 数据库支持 | 数据反射 | 自带定时任务 | 自带队列 | 微服务 |
| --- | --- | --- | --- | --- | --- |
| Gin | 无 | 仅 HTTP 绑定 | 无 | 无 | 否 |
| Fiber | 无 | 仅 HTTP 绑定 | 无 | 无 | 否 |
| Go-Zero | MySQL、PostgreSQL、MongoDB，另有 Redis | HTTP 解析有反射；数据层由 goctl 生成，不做运行时 ORM 反射 | 无框架内 cron，官方文档使用 Kubernetes CronJob | 有。Kafka `kq`、Beanstalkd 延迟队列、RabbitMQ | 是 |
| Echo | 无 | 仅 HTTP 绑定 | 无 | 无 | 否 |
| Beego | MySQL、SQLite、PostgreSQL、Oracle、TiDB | ORM 结构体反射 | 有。`task` 定时 / 周期任务 | 无 | 否 |
| Kratos | 无 | protobuf 代码生成，无 ORM 反射 | 无 | 无 | 是 |
| Iris | 无 | MVC 方法参数反射注入 | 无 | 无 | 否 |
| Chi | 无 | 无内置参数绑定 | 无 | 无 | 否 |
| GoFrame | MySQL、MariaDB、TiDB、PostgreSQL、SQL Server、SQLite、Oracle、ClickHouse、达梦 | 请求、配置、gdb 全链路反射 | 有。`gcron` | 仅进程内 `gqueue`，无消息队列 | 是 |
| Buffalo | PostgreSQL、MySQL、SQLite、CockroachDB | pop model 反射 | 无 | 无 | 否 |
| Hertz | 无 | 仅 HTTP 绑定 | 无 | 无 | 仅 HTTP 层 |

## 性能排序

数据来自 [the-benchmarker](https://web-frameworks-benchmark.vercel.app/frameworks/go/) 2026-11-05、concurrency 64 的空接口吞吐，单位是请求/秒。这项测试衡量 HTTP 框架开销，不含数据库和业务逻辑。Iris、Buffalo、Kratos 未被该基准收录。性能排名按请求/秒从高到低。Star 排名是 2026-11-24 这 11 个框架里的名次，Star 数字由 shields.io 实时生成。

| 性能排名 | 框架 | 请求/秒 | Star 排名 | Star |
| --- | --- | --- | --- | --- |
| 1 | Fiber | 187,551 | 2 | ![Github stars](https://img.shields.io/github/stars/gofiber/fiber.svg) |
| 2 | Hertz | 187,380 | 11 | ![Github stars](https://img.shields.io/github/stars/cloudwego/hertz.svg) |
| 3 | Echo | 114,313 | 4 | ![Github stars](https://img.shields.io/github/stars/labstack/echo.svg) |
| 4 | Gin | 111,896 | 1 | ![Github stars](https://img.shields.io/github/stars/gin-gonic/gin.svg) |
| 5 | Chi | 108,537 | 8 | ![Github stars](https://img.shields.io/github/stars/go-chi/chi.svg) |
| 6 | GoFrame | 105,504 | 9 | ![Github stars](https://img.shields.io/github/stars/gogf/gf.svg) |
| 7 | Go-Zero | 100,781 | 3 | ![Github stars](https://img.shields.io/github/stars/zeromicro/go-zero.svg) |
| 8 | Beego | 97,930 | 5 | ![Github stars](https://img.shields.io/github/stars/beego/beego.svg) |
| 未收录 | Iris | — | 7 | ![Github stars](https://img.shields.io/github/stars/kataras/iris.svg) |
| 未收录 | Buffalo | — | 10 | ![Github stars](https://img.shields.io/github/stars/gobuffalo/buffalo.svg) |
| 未收录 | Kratos | — | 6 | ![Github stars](https://img.shields.io/github/stars/go-kratos/kratos.svg) |

## 数据库查询对比

数字来自 [efectn/go-orm-benchmarks](https://github.com/efectn/go-orm-benchmarks/blob/master/results.md)，2024-10-15 由 GitHub Actions 生成，无缓存。仓库作者注明这套结果有时会不准。没有进入该基准的框架不编造名次。Gin、Echo、Fiber、Chi、Hertz、Iris 没有自带查询层，不参与这张表。

反射指查询结果映射到结构体时是否走运行时反射。数据量变大时，反射要按行填字段，耗时和分配会随行数上涨，所以性能排名按多行读取 `ReadSlice` 的 ns/op 从低到高排，性能好的在前。单行读取、插入、更新是同一次基准的附列，不改变行序。

Kratos 没有自带 ORM，这一行的数字是常见选型 ent 的。Go-Zero 这一行的数字是 sqlx 的。GORM 不在这 11 个框架里，Star 排名写「框架榜外」，徽章用它自己的仓库。

| 性能排名 | 数据层 | 框架 | 反射 | 多行 ns/op | 多行 allocs/op | 单行 ns/op | 插入 ns/op | 更新 ns/op | Star 排名 | Star |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | ent | Kratos | 无。代码生成 | 364,374 | 2,036 | 177,505 | 332,290 | 339,315 | 6 | ![Github stars](https://img.shields.io/github/stars/go-kratos/kratos.svg) |
| 2 | sqlx | Go-Zero | 有。StructScan | 368,843 | 1,225 | 319,489 | 445,687 | 314,410 | 3 | ![Github stars](https://img.shields.io/github/stars/zeromicro/go-zero.svg) |
| 3 | pop | Buffalo | 有 | 381,803 | 1,306 | 169,084 | 708,639 | 335,513 | 10 | ![Github stars](https://img.shields.io/github/stars/gobuffalo/buffalo.svg) |
| 4 | beego | Beego | 有 | 431,007 | 3,077 | 153,944 | 300,981 | 306,440 | 5 | ![Github stars](https://img.shields.io/github/stars/beego/beego.svg) |
| 5 | gorm | 外接参照 | 有 | 515,118 | 2,196 | 223,097 | 409,477 | 389,390 | 框架榜外 | ![Github stars](https://img.shields.io/github/stars/go-gorm/gorm.svg) |
| 未收录 | gdb | GoFrame | 有 | — | — | — | — | — | 9 | ![Github stars](https://img.shields.io/github/stars/gogf/gf.svg) |

单行读取里 Beego 最快，多行读取里它落到第 4，分配次数升到 3,077。无运行时反射的 ent 在多行读取里排第 1。sqlx 有反射，多行读取仍紧挨 ent，分配次数少于 ent。GoFrame 的 gdb 同样有反射，没有这套基准的数字，不参与名次。

## 小结

两套排序并不重合。Star 最高的是 Gin，空接口吞吐最高的是 Fiber 和 Hertz，Hertz 的 Star 排在最后。

Gin、Echo、Fiber、Chi、Iris、Hertz 需要自己接入 ORM、定时任务、队列和微服务治理。Beego 与 GoFrame 同时具备数据库反射和定时任务，二者都没有可持久化的消息队列。GoFrame、Go-Zero、Kratos 自带微服务能力。Go-Zero 同时带消息队列集成，数据访问走代码生成。GoFrame 的空接口吞吐接近 Chi，高于 Go-Zero 和 Beego。多行查询里，无运行时反射的 ent 排在最前，GoFrame 的 gdb 没有同基准数字。
