# nginx-rev_proxy-redis_session
```
                 +---------+
                 |         |
             +---+ tomcat7 +---+   +-------+
             |   |         |   +---+       |
             |   +---------+   |---|  DB   |
             |                 +---+       |
+---------+  |   +---------+   |   +-------+
|         |  |   |         |   |
|  Nginx  +------+ tomcat7 +---+
|         |  |   |         |   |
+---------+  |   +---------+   |
             |                 |   +-------+
             |   +---------+   +---+       |
             |   |         |   |---| redis |
             +---+ tomcat7 +-------+       |
                 |         |       +-------+
                 +---------+

```
### Add ${TOMCAT_HOME}/conf/context.xml
```
<Valve className="com.orangefunction.tomcat.redissessions.RedisSessionHandlerValve" />        
<Manager className="com.orangefunction.tomcat.redissessions.RedisSessionManager" 
    host="localhost"             <!-- Redis地址 -->
    port="6379"                  <!-- Redis端口 -->
    password="123456"            <!-- Redis密碼 -->
    database="0"                 <!-- 存儲Session的Redis庫編號 -->
    maxInactiveInterval="60"     <!-- Session失效的間隔（秒） -->
    />
```
### copy jar to ${TOMCAT_HOME}/lib 
