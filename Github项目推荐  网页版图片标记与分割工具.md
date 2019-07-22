## Github项目推荐 | 网页版图片标记与分割工具

AI研习社 [AI研习社](javascript:void(0);) *前天*

[![img](https://mmbiz.qpic.cn/mmbiz_jpg/bicdMLzImlibRiboYcgtAAFwZvvLPUlRkFmiaQ8aCfWBsYib2ic7uVBLAHBtL8m8gYWxDLRdVWaAoASYXjjYclph6NlQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)](http://mp.weixin.qq.com/s?__biz=MjM5ODU3OTIyOA==&mid=2650677584&idx=2&sn=cad260b9870b44f040600b527eadf2a1&chksm=bec21c2389b595352ab71a3d755111109fca556b6c397b548ec7bdaaa97d1346eaee2e23ef8b&scene=21#wechat_redirect)

**Image Labeling Tool - Web application for image labeling and segmentation**

by **Slava Kim**

**Github项目地址：**

[https://github.com/Slava/label-tool](https://mp.weixin.qq.com/s?__biz=MjM5ODU3OTIyOA==&mid=2650677590&idx=2&sn=bff0fb0b210c14dadd8516978f4be2ed&chksm=bec21c2589b595338bbbd304f1eb6f32dd878b8e32019a3d653a90f8a78ac93041f6d1f99baa&mpshare=1&scene=1&srcid=0722M2G5AAxJwUgbeoa6LgBI&key=6eec20dd63b3d5ee0dc501c7071ec3cd68169f1946326af6c8a22995150976d40ad20955b9ab111bd5974e8a4608235838a6f5ea27c3ff07066959a0758632bc9466dfa118af828a5a6a32bb5c595434&ascene=1&uin=MjMzNDA2ODYyNQ%3D%3D&devicetype=Windows+10&version=62060833&lang=zh_CN&pass_ticket=GDeHx9Ce48mp4IDEFfst0hfy2PrnOV8UJpgPCei8dZe%2BX%2F%2FgYF3Hfke%2BPMt02FlY)

用于图像标记和分割的Web应用程序。

**Demo：**http://slv.io/label-tool/demo/



## **图像标签工具**

这个Web应用程序将允许你标记图像，绘制边界框、形状，使用下拉列表、复选框和输入框收集表单中的信息。

标签UI提供了许多用于绘制多边形形状的功能，使用基于边缘的自动跟踪或外部机器学习模型进行辅助跟踪来编辑它们。

当你需要自己或按组分割和标记多个图像时，建议使用本工具。 它可以轻松收集并在稍后以一种能与LabelMe兼容的格式导出数据。你可以使用本工具来替代LabelMe、js-segment-annotator等自托管工具或 LabelBox等托管服务。



## **标签工具 Demo**

标签接口的演示，所有数据都是静态提供的（刷新后数据就会恢复）。

Demo：http://slv.io/label-tool/demo/



## **效果截图**

### **1.边界框标签：**

![1562746070637832.gif](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibTVwIeibUCyDYQYB8MdiaL1qkUKCVB5gk1Gia9qKMr9IqrqhibgI0icEKDDD29fFZhKbomC7qorF60ib16Q/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

### **2.使用多边形进行分割：**

![1562746272440558.gif](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibTVwIeibUCyDYQYB8MdiaL1qkESZ5zqhNLxGmNv7XicdF7GAInNDsuyqMMLEOSFzibicXVgSVrwn3cDWvw/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

### **3.自动跟踪：**

![1562746296760007.gif](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibTVwIeibUCyDYQYB8MdiaL1qkKcpSpuDcaES9JxHuPO9iayAwmvuNHeeNCUDiayBfCjnWpK0rTL0KaiarQ/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

### **4.使用Tensor Flow服务辅助分割：**

![1562746334889173.gif](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

### **5.项目配置和自定义标签UI：**

![1562746352150493.png](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)



## **开发**

给客户端，服务器和顶级文件夹安装npm包：



- 
- 
- 

```
yarn installcd server && yarn install && cd ..cd client && yarn install && cd ..
```

如果数据库文件不存在，服务器将在第一次运行时运行数据库迁移。

请在开发模式下运行：

- 

```
env PORT=3000 API_PORT=3001 yarn start
```



## **为生产而构建**

构建客户端应用程序：

- 

```
cd client && yarn run build && cd ..
```

现在，你可以在prod模式下运行服务器应用程序，为客户端构建服务：

- 

```
env PORT=80 NODE_ENV=production node server/src/index.js
```



## **配置**

可以调整以下环境变量：

- PORT  - 应用程序服务的部分（dev，prod）
- API_PORT  - 区分API运行的端口（应该只在dev中使用）
- UPLOADS_PATH  - 应用程序存储上传图像的绝对路径，默认为服务器文件夹的“uploads”
- DATABASE_FILE_PATH  - 应用程序存储SQLite数据的文件的绝对路径。 默认为服务器文件夹中的database.sqlite
- ADMIN_PASSWORD  - 为所有非标记器操作设置一个简单密码（以hased形式存储）。



## **在Docker中运行**

默认的Dockerfile指向/uploads和/db/db.sqlite。若想获取持久化数据，请确保提前准备这些数据以进行挂载。 以下是安装本地主机目录的示例：



- 
- 
- 

```
mkdir ~/containersmnt/mkdir ~/containersmnt/db/mkdir ~/containersmnt/uploads/
```

**构建容器：**

- 

```
docker build -t imslavko/image-labeling-tool .
```

运行附加安装：

- 

```
docker run -p 5000:3000 -u $(id -u):$(id -g) -v ~/containersmnt/uploads:/uploads -v ~/containersmnt/db:/db -d imslavko/image-labeling-tool
```

使用 localhost:5000 访问该站点。



### **使用docker-compose运行**

- 查看docker-compose.yml以获取详细配置。
- 在运行之前，请先设置和导出环境变量CURRENT_UID。



- 
- 
- 
- 
- 

```
# if it needs to build the docker image,CURRENT_UID=$(id -u):$(id -g) docker-compose up -d --build# if it only needs to run,CURRENT_UID=$(id -u):$(id -g) docker-compose up -d
```



## **关于本项目**

本项目是我在2019年初在 NCSOFT  Vision AI实验室实习的一部分。



![img](https://mmbiz.qpic.cn/mmbiz_png/bicdMLzImlibTwZibDGwbc506Utic6M0ENDXuRib8vsl24HUiccK5JcxV9uiba1HQRib1Q8LSxlCGXtzWKrb5GIwqlEMow/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**你可能还想看**

![img](https://mmbiz.qpic.cn/mmbiz_jpg/bicdMLzImlibRaG1nQYOWDDjLntJBsBkAUAyFnRHMPnYF8Ncd3UmFa9WiciaqFdEohQJqnOJnjBfftt0BXSCGZRryQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![img](https://mmbiz.qpic.cn/mmbiz_png/bicdMLzImlibSF5RSIA4QLmWoq0zgibxrJmYoRbH2X4rMx1J9O1SAg5brnichddyuoTSOhsbsfTlXPvJVJ8wEyAzxw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**![img](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibRAS3Tao2nfeJk00qqxX3axIgPV3yia4NPESGdUJEM9vsfw1O4Dg1iat7lVNAmbCMY65ia2pzfBXm5kg/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)** 点击**阅读原文**，查看更多开源项目推荐

[阅读原文](https://mp.weixin.qq.com/s?__biz=MjM5ODU3OTIyOA==&mid=2650677590&idx=2&sn=bff0fb0b210c14dadd8516978f4be2ed&chksm=bec21c2589b595338bbbd304f1eb6f32dd878b8e32019a3d653a90f8a78ac93041f6d1f99baa&mpshare=1&scene=1&srcid=0722M2G5AAxJwUgbeoa6LgBI&key=6eec20dd63b3d5ee0dc501c7071ec3cd68169f1946326af6c8a22995150976d40ad20955b9ab111bd5974e8a4608235838a6f5ea27c3ff07066959a0758632bc9466dfa118af828a5a6a32bb5c595434&ascene=1&uin=MjMzNDA2ODYyNQ%3D%3D&devicetype=Windows+10&version=62060833&lang=zh_CN&pass_ticket=GDeHx9Ce48mp4IDEFfst0hfy2PrnOV8UJpgPCei8dZe%2BX%2F%2FgYF3Hfke%2BPMt02FlY##)





![img](https://mp.weixin.qq.com/mp/qrcode?scene=10000004&size=102&__biz=MjM5ODU3OTIyOA==&mid=2650677590&idx=2&sn=bff0fb0b210c14dadd8516978f4be2ed&send_time=)

微信扫一扫
关注该公众号