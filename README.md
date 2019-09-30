### Spring Cloud Stream 使用 RabbitMQ

### 步骤一：创建项目
1. 依赖选择：Cloud Stream、Spring for RabbitMQ
2. 编写文件：com.example.spring_cloud_stream_rabbitmq_demo.SinkReceiver.class

### 步骤二：RabbitMQ 的 docker 镜像使用
1.下载镜像（management版本的才带有web管理界面）
```
docker pull rabbitmq:3.7.18-management
```
2.创建容器（监听端口：5672，web管理界面端口：15672）
```
docker run -p 5672:5672 -p 15672:15672 rabbitmq:3.7.18-management
```
3.使用默认用户名、密码：guest/guest 登陆
```
http://localhost:15672
```

### 步骤三：通过 RabbitMQ 的控制台发送消息，来验证消息消费程序的功能
1. 启动项目，访问网址：http://localhost:15672/#/ ，可以看到Connections、Channels、Exchanges、Queues 等信息。
2. 进入队列的管理页面，通过 Publish Message 功能来发送一条消息到该队列中，填写"hello"，点击"Publish Message"按钮
3. 可以在当前启动的Spring Boot应用程序的控制台中看到类似下面的内容：
```2019-09-30 15:06:02.642  INFO 74347 --- [2YEzu-Mx_Zyg-21] eceiver$$EnhancerBySpringCGLIB$$50b57463 : Received: hello```
:q:
### 参考：
参考资料 | 网址
--- | ---
Spring Cloud构建微服务架构：消息驱动的微服务（入门）【Dalston版】| http://blog.didispace.com/spring-cloud-starter-dalston-7-1/
官方文档 | https://docs.spring.io/spring-cloud-stream/docs/Elmhurst.RELEASE/reference/htmlsingle/#spring-cloud-stream-preface-creating-sample-application