# Maven入门



Maven翻译是专家，内行的意思，em，是跨平台的项目管理工具

Maven主要服务于给予Java平台的项目构建，依赖管理，项目信息管理。



#### 项目构建流程：

清理项目 -> 编译项目 -> 测试项目 -> 生成测试报告 -> 打包项目 -> 部署项目





#### 项目信息管理

- 工程版本控制系统消息
- 缺陷跟踪系统消息
- 开发者信息
- 许可证信息
- Javadoc
- 测试覆盖
- 代码静态分析报告
- 单元测试覆盖率



#### Maven目录结构

- bin： 含有mvn运行的脚本
- boot：含有plexus-classworlds类加载器框架
- conf：含有settings.xml配置文件
- lib：含有Maven运行时所需要的java类库
- LICENSE.txt,NOTICE.txt,README.txt针对Maven版本，第三方软件等简要介绍



#### Maven项目的目录约定

MavenProjectRoot(项目根目录)

|--------src

|			|--------main

|			|			|--------java——存放项目的.java文件

|			|			|--------resource——存放项目资源文件，如spring，hibernate

配置文件

|			|--------test

|			|			|--------java——存放所有测试.java文件，如JUnit测试类

|			|			|--------resource——存放项目资源文件，如Spring，hibernate

配置文件

|--------target——项目输出位置

|--------pom.xml——用于标识该项目是一个Maven项



#### Maven使用命令自动构建Java Project项目

1. 使用mvn archetype:generate,命令如下

   ```shell
   mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=myapp -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
   ```

   



#### 命令：

编译执行：

mvn compile

清除编译结果，也就是把编译生成的target文件夹删掉：

mvn clean

