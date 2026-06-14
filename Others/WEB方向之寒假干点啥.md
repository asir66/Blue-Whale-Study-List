# WEB 方向之寒假干点啥

***建议，仅供参考**

WEB 方向的基础多而杂，实在没有很系统的资料可以对着学，但是自己动手多实践在实践中学习是不亏的

- 去阿里云/腾讯云等云服务器提供商用学生优惠租台云服务器，理想情况下一分钱不用花，装个 linux 自己折腾一些小网站或者跑些程序
  - https://university.aliyun.com/
  - https://developer.aliyun.com/plan/student
  - https://cloud.tencent.com/act/campus
  - https://www.huaweicloud.com/special/ecs-xsfwq.html
- 不知道服务器搞来之后用来干什么
  - 搭博客写点生活感想（动态：WordPress 等，静态：hexo 或直接用 nginx 给静态文件拉出去）
    - 可以参考以下社团优秀成员的博客
    - https://aidaip.github.io/life/2023/06/04/%E8%B5%9E%E7%BE%8E%E9%A3%9F%E5%A0%82.html
    - https://surager.pub/_posts/2023-04-17-%E4%B8%8E%E8%82%AF%E5%BE%B7%E5%9F%BA%E7%BB%9D%E4%BA%A4%E4%B9%A6/
    - https://lonelyuan.github.io/p/%E4%BF%9D%E7%A0%94%E6%97%A5%E8%AE%B0/
  - 跑自己的游戏服务器
    - ⚪神私服 https://github.com/Grasscutters/Grasscutter
    - PalWorld （最近爆火的帕鲁世界，一看好友人人都在玩就我没有）
    - Minecraft
    - 云服务器性能不够可以尝试用 frp 或者 rathole 等反向代理工具给自己的电脑代理到公网上
  - 写个爬虫（学习研究用途，注意控制爬取频率！）
    - B站评论区（较容易），知乎回答（较不容易）等
    - 爬取内容可以是针对某个搜索关键词的视频/提问下面的评论/回答
    - 把数据存下来，然后做点可视化，可以做成网页给别人秀秀
- **搞清楚上面这些东西的原理（这是重点！）**
  - WordPress 是什么语言写的，曾经甚至现在有什么漏洞？什么是静态网站？动态网站如何实现？Nginx/Apache 在其中有什么用？PHP 如何对外提供服务？php-cgi 与 php-fpm 存在哪些不同及 CGI 背后的历史？
  - 不要在网站备案之类的鸡毛蒜皮事情上多花时间，中国大陆内的服务器 HTTP 服务请往高端口开、配置 HTTPS，如有必要可租大陆之外的服务器避开法律法规限制
  - 为什么 Windows 上的 .exe 不能在 linux 上跑，精确的原理？有什么解决方案？怎么 Java 打出来的 .jar 就可以跨平台？Python 之类的呢？
  - 为什么我家用的网开了游戏/网站等服务器外面访问不了？NAT 具体有哪些可以“打洞”？反向代理的原理是什么？暴露内网有哪些可能的风险？
  - 我该如何给服务器的日常工作做得方便点或者实现自动化？比如 PalWorld 服务端不停的漏内存搞得系统内存吃满了，怎么定时/定内存配额给它进程杀掉重启？学会 shell 和多几个脚本语言的使用（不是C语言考试那种学会，查着资料能看懂就行）
  - 怎么实现爬虫？从单纯的 API 调用到 beautifulsoup 或类似的 DOM selector 再到无头浏览器，这些玩意分别解决了爬虫的哪些需求？数据如何存储，是直接 .csv 文件存还是写个巨大的 JSON；提高效率往数据库里塞时数据库如何设计。做数据可视化网页时的技术栈选择？以及一套流程走下来你的程序中存在什么漏洞或者不妥？从爬取频率过高给拉黑名单到爬取内容不易解析，再到数据存储时可能存在的escape，或者SQL查询的注入等问题。同时从反向思考如何防止别人去爬自己的内容
  - **搞不懂就去搜索引擎查**
- 研究下列软件和它们已经发现的漏洞
  - [Casdoor](https://github.com/casbin/casdoor) 搞清楚这个软件是干啥的，支持的验证方式分别是啥、如何工作
    - 比较新的洞有个任意文件读取的，试着定位到修复前后的 commit，看看是哪出了问题怎么修
    - 老生常谈的 SQL 注入漏洞看懂就行
  - [GitLab](https://gitlab.com/gitlab-org/gitlab) 搞清楚它新鲜的 [CVE-2023-7028](https://nvd.nist.gov/vuln/detail/CVE-2023-7028) 漏洞是怎么出现的。为什么采用了 MVC 架构且 Model 部分使用了 ORM 仍然出现了类似 SQL 注入的问题，定位修复前后 _版本_ 的 commit，看懂其逻辑
  - 你这发的玩意一个是 Go 写的一个是 Ruby 都啥啊看不懂
    - 我也不会，但实际比赛中给你塞个要你挖漏洞的项目用的是啥语言就天知道了，主要是学会编程语言的通性，然后靠猜就能猜得八九不离十
    - 可以查找相关文档和使用 GPT 之类的工具帮助理解
- 速成选手请至 [buuoj](https://buuoj.cn/) 等在线 oj 网站刷题
