---
layout: post
title: Mitmproxy
tags: ["bash","mitmproxy","proxy","docker"]
---
Start mitmproxy server by use docker

- use web interface
```bash
sudo docker run --rm -it -v ~/.mitmproxy:/home/mitmproxy/.mitmproxy -p 8080:8080 -p 127.0.0.1:8081:8081 mitmproxy/mitmproxy mitmweb --web-host 0.0.0.0
```
- use console
```bash
sudo docker run --rm -it -v ~/.mitmproxy:/home/mitmproxy/.mitmproxy -p 8080:8080 -p 127.0.0.1:8081:8081 mitmproxy/mitmproxy mitmproxy
```
- modify response of domain vnexpress.net by replacing body element by `<body>test</body>` 
```bash
sudo docker run --net=host --rm -it -v ~/.mitmproxy:/home/mitmproxy/.mitmproxy -p 8080:8080 -p 127.0.0.1:8081:8081 mitmproxy/mitmproxy mitmproxy --ssl-insecure -B "/~d vnexpress.net/<body.*/<body>test</body>"
```

Access the url [http://0.0.0.0:8081/#/flows](http://0.0.0.0:8081/#/flows) to manage your proxy server

Use curl to test your proxy
```bash
curl -x localhost:8080 https://google.com
```

See more:
- [https://github.com/mitmproxy/mitmproxy](https://github.com/mitmproxy/mitmproxy)
- [https://hub.docker.com/r/mitmproxy/mitmproxy/](https://hub.docker.com/r/mitmproxy/mitmproxy/)