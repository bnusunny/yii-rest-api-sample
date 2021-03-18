# yii-rest-api

这是一个Serverless Yii2 Rest API的例子。


## 要求

* 已经安装AWS CLI，并配置管理员权限 - [安装指南](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
* [Docker installed](https://www.docker.com/community-edition)
* [php 7.4](https://www.php.net/manual/en/install.php)
* 已安装SAM CLI - [Install the SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html)
* 已经部署MySQL数据库

## 配置过程

### 1. 取得MySQL数据库的配置

需要获得MySQL的连接地址，端口号，用户名和密码, 以及VPC的子网ID和安全组ID。

### 2. 配置SAM CLI的templete文件

复制template_example.yml为template.yml. 修改其中的MySQL的连接地址，端口号，用户名和密码，以及VPC的子网ID和安全组ID。

### 3. 部署到AWS

运行下面的命令，完成部署

```shell
sam build

sam deploy --guided
```
在sam deploy完成后，可以看到输出的API访问地址。

```shell
Key                 HelloWorldAPI                                                                                                                                                                        
Description         API Gateway endpoint URL for Prod environment for First Function                                                                                                                     
Value               https://el3d9juuv5.execute-api.ap-southeast-1.amazonaws.com/customers
```

访问这个API地址。

```shell
8c85909aaff7:yii-rest-api sunhua$ http https://el3d9juuv5.execute-api.ap-southeast-1.amazonaws.com/customers
HTTP/1.1 200 OK
Apigw-Requestid: cXlVziewyQ0EPIA=
Connection: keep-alive
Content-Length: 136
Content-Type: application/json; charset=UTF-8
Date: Thu, 18 Mar 2021 05:45:21 GMT
X-Debug-Duration: 64
X-Debug-Link: /debug/default/view?tag=6052e8f1dd9c4
X-Debug-Tag: 6052e8f1dd9c4
X-Pagination-Current-Page: 1
X-Pagination-Page-Count: 1
X-Pagination-Per-Page: 20
X-Pagination-Total-Count: 3
X-Powered-By: PHP/7.4.16
link: <http://el3d9juuv5.execute-api.ap-southeast-1.amazonaws.com/customers?page=1>; rel=self, <http://el3d9juuv5.execute-api.ap-southeast-1.amazonaws.com/customers?page=1>; rel=first, <http://el3d9juuv5.execute-api.ap-southeast-1.amazonaws.com/customers?page=1>; rel=last
vary: Accept

[
    {
        "address": "Chongqing",
        "id": 1,
        "name": "Harold"
    },
    {
        "address": "Beijing",
        "id": 2,
        "name": "Eva"
    },
    {
        "address": "Shengzhen",
        "id": 3,
        "name": "Randy"
    }
]
```

恭喜！您已经在AWS上部署了第一个Serverless的Yii2 Rest API！