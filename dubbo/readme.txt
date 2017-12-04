
修改注意：

1) 添加了新的模块，要在POM中maven-shade-plugin的<artifactSet>中添加<include>

2) 添加了新的扩展点，要在POM中maven-shade-plugin加上<transformer>

搜索出 扩展点配置文件 的命令

$ find . -wholename */META-INF/dubbo/* -type f | grep -vF /test/ | awk -F/ '{print $NF}' | sort -u
com.alibaba.dubbo.cache.CacheFactory
com.alibaba.dubbo.common.compiler.Compiler
com.alibaba.dubbo.common.extension.ExtensionFactory
...and so on...


使用操作：
1) 部署在本地
cd dubbo\target
mvn install:install-file -Dfile=F:\fasbit\dubbox-master\dubbo\target\dubbo-2.8.4.jar -DgroupId=com.alibaba -DartifactId=dubbo -Dversion=2.8.4 -Dpackaging=jar

2) 应用到其他工程