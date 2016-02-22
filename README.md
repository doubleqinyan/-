# -
微信测试账号配置+平台搭建+ngrok小工具

思路：
  1、创建微信测试账号

  2、从https://github.com/cqb325/weixin 这里 download 下代码

  3、在 http://www.ngrok.cc/ 注册账号

环境：
  1、node.js 最新版本

  2、redis 最新版本

  3、express.js 4.x

  4、涉及到前端工具 webstorm

步骤：
  
  1、创建微信测试账号，获得 appId 和 appSecrete；

  2、环境配置

    （1）安装 node.js 最新版本
  
    （2）安装 express.js 4.x
        
          运行下面命令
            cd ××××\weixin-master
            npm install
          
      完成环境配置
    
  3、修改微信信息：config.js

      exports.WX = {
        TOKEN: "xxxxxx",
        APPID: "xxxxxx",
        APPSECRET: "xxxxxx"
      };

      token：自定义, eg. qqy1990 ；
      APPID、APPSECRET：为测试账号的 APPID 和 APPSECRET 
      这个要与申请测试公众号一致
  
  4、启动的端口为 8888
  
     如果要修改端口，在bin\www文件修改
     
  5、运行
  
    （1）启动 redis 服务
    
    （2）运行 npm start
     
    （3）访问 http://localhost:8888/weixin/index.html ，有结果说明ok了

  6、运行一个服务，将本地ip映射到外网
  
    （1）修改配置文件	ngrok.cfg 
  
        server_addr: "server.ngrok.cc:4443"
        auth_token: "×××××"                 /* 在 http://www.ngrok.cc/ 注册的账号所得到的 token */
        tunnels:
        weixin:                             /* "weixin" 是下面配置的唯一标识 */
          subdomain: "qqy"                  /* "qqy" 是自定义的域名，在 http://www.ngrok.cc/ 注册的账号里进行自定义 */
          proto:
        http: 8080

    （2）建一个文本文件，名字和后缀改成 “run.cmd”
          
          复制运行命令至 run.cmd 里： ngrok.exe -config ngrok.cfg start qqy
       
    （3）双击 "run.cmd" ，起服务，则可将本地ip映射至外网（qqy.ngrok.cc），即 http://qqy.ngrok.cc/weixin/index.html
    
  7、验证测试账号 url 和 token
    
      url : http://qqy.ngrok.cc/weixin/index.html
      token : qqy1990 
      
      验证成功，完成本地测试平台搭建。
      
      
  ---------------------------------------------------------------------------
  
  微信开发本地测试：
  
  1、 修改appid
  
  2、写死jssdk ticket（如果涉及分享）
  
  3、修改网页授权URL地址

  4、修改前端页面中的contextPath
  
  5、本地映射到外网（详情见步骤6）







  
       
       
