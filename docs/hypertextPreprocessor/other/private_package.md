通常情况下, packagist.org上的包是开源托管到github上的, 
如果公司想发布内部的插件,托管到自己的服务器上,并且还想通过composer安装, 怎么办呢?
参考:https://docs.phpcomposer.com/articles/handling-private-packages-with-satis.html

关键文件(satis.json)说明:
repositories中的url是私有仓库地址
require内的包名,是私有仓库内的composer.json的name值!!
```json

{
  "name": "My Repository",
  "homepage": "http://127.0.0.1:8080",
  "repositories": [
    {
    "type": "vcs", 
    "url": "https://gitee.com/ccc.../testpri.git"
    }
  ],
  "require":{
    "fen...g/te...ri":"*"
  },
  "archive":{
    "directory":"dist",
    "format":"tar",
    "prefix-url":"http://127.0.0.1:8080/",
    "skip-dev":true
  }
}


```