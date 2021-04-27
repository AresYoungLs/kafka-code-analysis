# Code Analysis
此项目用于Kafka的源码解析

## 项目结构说明
```textmate
kafka-0.10.0
 ├── .gitignore
 ├── .gradle
 ├── .idea
 ├── bin                                                                         //用于存放脚本,直接执行一些命令
 ├── build.gradle                                                                //
 ├── checkstyle                                                                  //用于静态代码的检查
 │   ├── checkstyle.xml                                                          //对于checkstyle的配置
 │   ├── import-control-core.xml                                                 //
 │   └── import-control.xml                                                      //
 ├── clients                                                                     //Kafka的客户端的代码(Java)
 ├── CodeAnalysis.md                                                             //
 ├── config                                                                      //Kafka自己本身的一些配置文件
 │   ├── connect-console-sink.properties                                         //
 │   ├── connect-console-source.properties                                       //
 │   ├── connect-distributed.properties                                          //
 │   ├── connect-file-sink.properties                                            //
 │   ├── connect-file-source.properties                                          //
 │   ├── connect-log4j.properties                                                //
 │   ├── connect-standalone.properties                                           //
 │   ├── consumer.properties                                                     //
 │   ├── log4j.properties                                                        //
 │   ├── producer.properties                                                     //
 │   ├── server.properties                                                       //核心配置文件(详解)
 │   ├── tools-log4j.properties                                                  //
 │   └── zookeeper.properties                                                    //
 ├── connect                                                                     //Kafka的衍生出的新的项目,通过此项目将各种数据源中的数据引入Kafka(core)中
 ├── CONTRIBUTING.md                                                             //
 ├── core                                                                        //Kafka的消息系统(Scala)
 ├── doap_Kafka.rdf                                                              //
 ├── docs                                                                        //文档
 ├── examples                                                                    //提供的Demo
 ├── gradle                                                                      //跟Gradle构建相关的一些
 ├── gradle.properties                                                           //
 ├── gradlew                                                                     //
 ├── gradlew.bat                                                                 //
 ├── HEADER                                                                      //
 ├── kafka-0.10.0.1-src.iml                                                      //
 ├── kafka-0.10.0.1-src.ipr                                                      //
 ├── kafka-0.10.0.1-src.iws                                                      //
 ├── kafka-merge-pr.py                                                           //
 ├── LICENSE                                                                     //
 ├── log4j-appender                                                              //打印日志
 ├── NOTICE                                                                      //
 ├── README.md                                                                   //
 ├── release_notes.py                                                            //
 ├── settings.gradle                                                             //
 ├── streams                                                                     //将通过connect引流入的一些数据,通过此项目去core中消费一些消息,以流式处理的引擎系统进行流式计算(Java)
 ├── tests                                                                       //单元测试 基准测试等
 ├── tools                                                                       //
 ├── vagrant                                                                     //
 ├── Vagrantfile                                                                 //跟云平台相关的一些文件
 └── wrapper.gradle                                                              //
```
## 项目运行准备工作
1. 配置日志输出  
   将 `config` 下的 `log4j.properties` 拷贝到 `src->main->scala` 目录下与 `kafka` 同级
2. 配置Kafka自身的参数  
   在 `config` 下的 `server.properties` 编写配置
3. 在idea中通过源码的方式启动Kafka  
   此外,Kafka的启动类是 `kafka.Kafka` ,他是要读取 `server.properties` 文件的,必须给他制定这个文件的所在位置才可以  
   在上方的菜单栏里,有一个 `Run->Edit Configurations->  `
