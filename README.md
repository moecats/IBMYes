1.安装
```
wget --no-check-certificate -O install.sh https://raw.githubusercontent.com/moecats/IBMYes/master/install.sh && chmod +x install.sh  && ./install.sh
```
2.配置

Actions:
```
IBM_ACCOUNT // IBM Cloud的登录邮箱和密码
IBM_APP_NAME // 应用的名称
REGION_NUM // 区域编码
RESOURSE_ID // 资源组ID
```

区域编码
```
#1. au-syd
#2. in-che
#3. jp-tok
#4. kr-seo
#5. eu-de
#6. eu-gb
#7. us-south
#8. us-east
```

获取ACCOUNT/RESOURSE_ID
```
ibmcloud login			IBM_ACCOUNT
ibmcloud resource groups	RESOURSE_ID
```
3.反代

cloudflare Workers:
```
addEventListener(
"fetch",event => {
let url=new URL(event.request.url);
url.hostname="ibmyes.us-south.cf.appdomain.cloud";
let request=new Request(url,event.request);
event. respondWith(
fetch(request)
)
}
)
```

