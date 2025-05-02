# web_server
Web服务器框架，轻松部署web网站

> 视频  [部署演示](https://www.bilibili.com/video/BV1RM4m167gK/)  

### 依赖
> 点击了解http协议 [ccoong/ccore](https://github.com/ccoong/ccore)  
> 点击了解数据库的操作 [ccoong/mysqlorm](https://github.com/ccoong/mysqlorm)   

### 基本信息配置文件
````c++
路径：./build/13535_webserve.conf
配置信息：
    "IS_GZIP": 1, 是否开启gzip，1为开启0为关闭，开启后会自动将h5文件压缩为gzip格式的文件
    "WEB_DIR": "html", html文件的路径（项目 build/ 路径下）
    "PORT": 80, 端口号
    "ORIGIN": "*" 白名单，*表示所有链接，多个链接请用 ; 隔开
````

### 日志文件
> *./build/13535.log*
### mode层
> 路径：include/mode/  
> 示例文件: include/mode/dbA1_test.hpp  
> 负责与数据库交互，dbA1_test 表示db_a1数据库，test数据表。通过 dbA1_test::obj().insertF("'小明',20,1") ，可向db_a1数据库的test数据表插入数据，更多介绍请点击[ccoong/mysqlorm](https://github.com/ccoong/mysqlorm)  
### view层
> 路径：build/html/  
> html文件的存放位置
### Route文件
> 路径：include/web_server/Route.hpp  
> 与客户端交互的主入口  
### controller层
> 路径：include/controller/  
> 示例文件: include/controller/Test.hpp  
> 与客户端交互的子入口 比如 post、get 都可以在这个文件夹下面去实现 
> 创建后的子入口需在 Route.hpp 里引入，并对其进行实例化（具体操作请打开 Route.hpp 文件查看）  

### 运行说明：
> 默认端口为80，请确认端口没有被其它程序占用，项目运行后在浏览器地址栏输入 http://localhost 预览
* linux系统部署：  
    1、下载依赖的库，解压到linux系统的 /var 路径下。依赖库请点击右边 Releases 下载；  
    2、下载源码，解压到用户目录，解压后创建 build，然后在build目录下编译并运行项目，示例: 

            git clone https://github.com/ccoong/web_server.git  

            cd web_server  

            mkdir build  

            cd build  

            cmake ..  

            make   
    3、运行与停止；

        ./web_server_run start&  //运行  
        
        ./web_server_run stop   //停止  