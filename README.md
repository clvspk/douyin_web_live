﻿抖音web直播间([live.douyin.com](https://live.douyin.com))弹幕抓取
--

**屏幕效果截图**

![enter image description here](https://github.com/gll19920817/tiktok_live/blob/main/WX20211129-144919@2x.png?raw=true)

**项目思路**

1. Selenium detach模式打开live直播间
2. mitmproxy 捕获live.douyin.com http请求并保存响应为指定目录下文件
3. watchdog监控步骤2指定目录下文件变化后反序列化文件(application/protobuf格式)
4. 反序列化弹幕消息分类后terminal输出

**使用方法**

1. 安装[python3](https://www.python.org/downloads/)
2. clone本项目，terminal进入项目目录，执行 `pip install requirements.txt`
3. 安装[mitmproxy](https://mitmproxy.org/) terminal执行`mitmproxy -s scripts/mitmproxy.py` (scripts/mitmproxy.py见项目)
4. terminal执行 `python3 main.py 直播间链接(https://live.douyin.com/******)`

**注意事项**

1. 本源代码自行改动仅可作学习目的！！！
2. 少刷抖音，他人美好生活皆虚幻，一切卷的不行，你懂得！！！
3. 切记浏览器打开直播间弹幕可能不完整，所以做数据统计还是算了

需安装 mongo
需安装 chromedriver

https://docs.mitmproxy.org/stable/concepts-certificates/#using-a-client-side-certificate

证书问题：
curl on the command line:
curl --proxy 127.0.0.1:8080 --cacert ~/.mitmproxy/mitmproxy-ca-cert.pem https://example.com/
wget on the command line:
wget -e https_proxy=127.0.0.1:8080 --ca-certificate ~/.mitmproxy/mitmproxy-ca-cert.pem https://example.com/
macOS
macOS (automated): sudo security add-trusted-cert -d -p ssl -p basic -k /Library/Keychains/System.keychain ~/.mitmproxy/mitmproxy-ca-cert.pem

mac执行这句话就行 sudo security add-trusted-cert -d -p ssl -p basic -k /Library/Keychains/System.keychain ~/.mitmproxy/mitmproxy-ca-cert.pem
