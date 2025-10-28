# Blue-Whale-Study-List
> This was a sudden idea — to gather and organize everyone’s learning resources in one place. 
>
> Simplicity is the ultimate principle; the best tool is the one you can use right away. So at the beginning, this list will only contain a single README document. Later, it might evolve into a wiki, or maybe an mdBook. Or perhaps it’ll fade away and get lost somewhere in the vast sea of GitHub repositories — that all depends on everyone.

总的来说我也不知道如何将这些知识点分解开来。只能将大家的学习资源统一统一，以后开个留言板分享吧。

# 一些挺有用的网站

- [CTFHUB](https://www.ctfhub.com/#/index)
  一个学习CTF的小站，里面有一个技能树，可以点亮他作为学习的路子。并且很关键他里面会统计最近的比赛，可以和队友组团打一打（之前有社团成员打了这种比赛赢了一个大疆无人机）
- [BUUOJ](https://buuoj.cn/)
  BUU靶场，久负盛名。应该是流传最广的CTF靶场了
- [攻防世界](https://adworld.xctf.org.cn/home/index)
  似乎和XCTF有关系，当初也是当作靶场用的。听说战队大厅还有Blue-Whale，但是不知道负责人是谁
- [BUGKU](https://ctf.bugku.com/)
  靶场，比较喜欢的是这里可以做AWD。做题可以换鼠标垫
- [CTF-WIKI](https://ctf-wiki.org/)
  同样是久负盛名，但是我觉得PWN写的挺好的，但是Web部分写的依托，所以学Web攻防的别看这个了

# Web攻防相关

学Web安全的，该说不说，要应该把OWASP TOP 10漏洞了解下（至少面试官问起来你知道）

- [2025 OWASP TOP 10](https://owasp.org/www-project-top-ten/)

然后就可以去将这些常见漏洞原理和利用方式学一学

- [SQL注入教程-橙子科技](https://www.bilibili.com/video/BV1c34y1h7So/?share_source=copy_web&vd_source=3057a8c490897b7f3dc3311de6aa625f)
  该说不说，橙子科技SSTI讲得不错的
- [SSTI教程-橙子科技](https://www.bilibili.com/video/BV1tj411u7Bx/?spm_id_from=333.1387.upload.video_card.click&vd_source=6ca6bce6ab790fe02889f85c0ef90f8a)

注：卖课的一律不用吊他，白嫖就够了

## 好用的工具

- #### [BurpSuite](https://portswigger.net/burp)
  
  最好用的一集，基本上一个工具能解决所有问题，而且你们可能不知道BurpSuite是有官方学习靶场的：https://portswigger.net/web-security
  
- #### yakit
  
  功能定位：一体化/集成型渗透辅助平台，集成抓包、漏洞检测、fuzzer、插件生态，类似把多种功能“打包”的桌面工具。
  
- #### hackbar
  
- 功能：浏览器插件（或小工具栏），用于快速拼接/测试常见 web payload（编码/解码、SQL、XSS、路径遍历等）。
  
- #### [sqlmap](https://github.com/sqlmapproject/sqlmap)

  sql注入的工具，单纯只会用工具是脚本小子，但是工具都用不熟就很尬了
  
- #### fenjing

  功能定位：针对 Jinja2 SSTI 的自动化绕 WAF/POC 工具，CTF/靶场常见的 SSTI 破解脚本。
  
  常见用途：自动化尝试 Jinja SSTI 绕过与利用、批量测试表单/输入点、在 CTF 中快速验证攻击链。
  
- #### tplmap

  功能：自动化检测并利用 **Server-Side Template Injection（SSTI）/模板注入** 的工具，能自动识别模板引擎并尝试 payload。
  
- #### 蚁剑

  功能：一个中文社区常用的**WebShell 管理器**（图形化管理、文件操作、执行命令、数据库管理等）。
  
- #### Gopherus

  功能：围绕 **gopher 协议** 做攻击利用的工具（在 SSRF/文件写入/远程请求场景里用 gopher 协议触发特殊请求/利用）。
  
- #### PHPstudy

  功能：PHP 本地集成环境（Windows 上常见），包含 Apache/Nginx、PHP、MySQL 等一键安装和配置。
  
- #### fscan

  功能（常见含义）：快速资产/端口/服务指纹扫描工具（社区里有多个名为 fscan 的实现，功能侧重点不同）。
  
- #### dirsearch

  功能：基于字典的 Web 目录/文件发现工具（类似 gobuster、dirb），针对 URL 做快速爆破查找隐藏页面/目录。
  
  



# 二进制安全

## 如何逆向

逆向可以去逆CTF题，但是那不够有趣。用来学习正好，还能找到答案看看别人的先进手法。但是我们是不是也可以找一个社区或者社团内交流。去逆一些病毒或者软件吧（记得用虚拟机）

- [52破解](https://www.52pojie.cn/)
  上古神站，你甚至能找到

## 如何pwn

我始终是觉得pwn专题是CTF-WIKI写得最好的一个板块

# 看些好玩的

别老盯着CTF，安全不只CTF。可以去下面看点技术文章

- [奇安信攻防社区](https://forum.butian.net/)
- [FreeBuf](https://www.freebuf.com/)

待补充

