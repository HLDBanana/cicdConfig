# 持续交付中心项目配置库

## 简述
   项目配置库是持续交付设施的重要组成部分。它对业务服务在持续交付过程所需参数进行集中配置的区域，使参数与项目代码分离，避免重复构建，且可对参数配置执行版本化、权限化管理。

## 目录结构
1. 【cert.d】目录   
    目录下是存放产物仓库自签证书，证书需要存放在对应域名文件夹，证书名称必须为ca.crt（区分大小写）。   
    若存在证书文件，则产物以自签证书的方式进行部署相关操作。若不存在文件ca.crt，则以公有证书的方式进行部署相关操作。
2. 【cicd-config】目录   
    该目录下是业务项目在持续交付各阶段使用到的参数配置文件（*.groovy）。以下文件需以服务为单位一一对应，建议使用服务名命名文件。
 * 【dev】目录，存放各业务线中开发阶段发使用的参数配置文件   
 * 【test】目录，存放各业务线中测试阶段使用的参数配置文件   
 * 【release】目录，存放各业务线中发布阶段使用的参数配置文件   
 * 【production】目录，存放各业务线中生产部署使用的参数配置文件   
 * 【CommEnv.groovy】文件，业务线中多个服务公用的参数配置，如：产物仓库、静态检查地址、私服URL、信息接受者等
3. 【nginx-conf】目录    
    前端项目使用nginx作为web服务器，此处用于放置用户自定义的nginx配置文件，若未放置，则使用持续交付的默认配置。
