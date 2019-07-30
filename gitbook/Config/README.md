环境配置是由Go第三方库viper来实现的。当程序启动时，viper会去读取`yaml`配置文件，以及将环境变量与配置文件中的变量对应起来。

以下是`yaml`配置文件，其中的变量可以被以`CRAWLAB_`为前缀的环境变量所覆盖。

```yaml
api:
  address: "localhost:8000"
mongo:
  host: localhost
  port: 27017
  db: crawlab_test
  username: ""
  password: ""
redis:
  network: tcp
  address: "localhost:6379"
log:
  level: info
  path: "/var/logs/crawlab"
server:
  host: 0.0.0.0
  port: 8000
  master: "N"
  secret: "crawlab"
spider:
  path: "/app/spiders"
task:
  workers: 4
other:
  tmppath: "/tmp"

```

环境变量列表如下。

环境变量 | yaml变量路径 | 描述 | 默认 | 可能值
--- | --- | --- | --- | ---
CRAWLAB_API_PATH | api.path | 前端API地址 | localhost:8000 | 任意
CRAWLAB_MONGO_HOST | mongo.host | MongoDB Host地址 | localhost | 任意
CRAWLAB_MONGO_PORT | mongo.port | MongoDB端口号 | 27017 | 任意
CRAWLAB_MONGO_PORT | mongo.db | MongoDB数据库名 | crawlab_test | 任意
CRAWLAB_MONGO_USERNAME | mongo.username | MongoDB用户名 | 空 | 任意
CRAWLAB_MONGO_PASSWORD | mongo.password | MongoDB密码 | 空 | 任意
CRAWLAB_REDIS_NETWORK | redis.network | Redis网络协议 | tcp | tcp, udp
CRAWLAB_REDIS_ADDRESS | redis.address | Redis地址 | localhost:6379 | 任意
CRAWLAB_LOG_LEVEL | log.level | 日志级别 | info | debug, info, warn, error
CRAWLAB_LOG_PATH | log.path | 任务日志所在目录 | `/var/logs/crawlab` | 任意
CRAWLAB_SERVER_HOST | server.host | 服务器绑定IP | 0.0.0.0 | 任意
CRAWLAB_SERVER_PORT | server.port | 服务器绑定端口 | 8000 | 任意
CRAWLAB_SERVER_MASTER | server.master | 该节点是否为主节点 | N | Y, N
CRAWLAB_SPIDER_PATH | spider.path | 爬虫所在目录 | /app/spiders | 任意
CRAWLAB_TASK_WORKERS | task.workers | 任务并行执行个数 | 4 | 任意数字
CRAWLAB_OTHER_TMPPATH | other.tmppath | 临时文件目录 | /tmp | 任意
