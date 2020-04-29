[toc]

# 1.下载安装

去官网下载适合自己pc的免安装版本，

# 2.环境变量

M2_HOME------>F:\apache-maven-3.3.3

 path------>%M2_HOME%\bin

# 3.测试是否配置生效

控制台输入：mvn -v

有反应说明装好了

# 4.设置本地仓库

安装成功后，默认的jar包的存放地址是${user.home}/.m2/repository。对于win用户来说就是c盘下的.m2/repository文件夹。很明显这个位置是不合理的，要改到其他位置，这里改到d盘。具体步骤如下：

1. 打开maven目录下的conf中的setting.xml文件
2. 找到被注释掉的localRepository标签，将里面的内容改为你的本地仓库地址然后打开注释，如：
```
<localRepository>D:\environment\mavenRepo</localRepository>
```
# 5.设置国内镜像

maven默认的中央仓库在国外，导致很多jar包在下载的过程中十分缓慢，这里需要设置一下国内的镜像，镜像简单说就是把你的访问请求进行拦截然后重定向的一个组件。这里我们使用阿里的镜像。操作步骤：

1. 打开maven目录下的conf中的setting.xml文件
2. 找到被注释掉的mirror标签，将里面的内容改为你的镜像地址然后打开注释，如：

```
 <mirror>
    <id>nexus-aliyun</id>
    <mirrorOf>*</mirrorOf>
    <name>Nexus aliyun</name>
    <url>http://maven.aliyun.com/nexus/content/groups/public</url>
</mirror>
```
# 6.常规profile设置

setting.xml文件中常规的profile设置，让你的maven项目都自动继承这个配置，这里配置一下jdk的版本和编码。

```
<!-- 全局JDK1.8配置 -->
        <profile>
            <id>jdk1.8</id>
            <activation>
                <activeByDefault>true</activeByDefault>
                <jdk>1.8</jdk>
            </activation>
            <properties>
                <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
                <maven.compiler.source>1.8</maven.compiler.source>
                <maven.compiler.target>1.8</maven.compiler.target>
 <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
            </properties>
		</profile>
```
然后激活这个配置：
```
    <!-- 激活配置 --> 
    <activeProfiles>
        <activeProfile>jdk1.8</activeProfile>
    </activeProfiles>
```

# 7.三处合一

这是在操作的时候踩坑踩出来的一个概念，具体的操作为用户目录，系统默认jar包目录，修改后jar包存放目录三处的setting.xml文件要一致。因为在被第三方软件引用的时候，不一定就以哪个为优先。所以，修改了上述的setting.xml文件之后要三处一致，复制一下就好了。

关于setting.xml文件的配置，推荐一篇好的文章：https://www.cnblogs.com/hepengju/p/11610451.html


