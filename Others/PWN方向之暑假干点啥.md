# PWN 方向之暑假干点啥

***建议，仅供参考**

PWN 方向上手比 Web 痛一点，但知识体系收敛——大部分时候你就在跟一个叫 libc 的东西斗智斗勇。暑假两三个月，从零到能独立打比赛问题不大。


## 基础——程序到底怎么跑的

PWN 不是上来就溢出，得先搞明白正常程序长什么样、怎么跑起来的。不搞清楚这个后面每一步都是背板。

- [CTF-Wiki PWN 板块](https://ctf-wiki.org/pwn/readme/) — 跟着顺序读。我始终觉得这是 CTF-Wiki 写得最好的一个板块，别处真找不出比这更系统的 PWN 教程
- **CSAPP 第 3、7、9 章** — 只看汇编、链接、虚拟内存这三章，啃下来 IDA 反汇编出来的东西你才看得懂、PLT/GOT 到底在干嘛你才明白、程序内存长什么样你心里才有数。电子版网上很好找。看不进书就看 [九曲阑干的讲解](https://www.bilibili.com/video/BV1cD4y1D7uR)，讲得挺清楚
- [Pwn.College](https://pwn.college/) — 国外 ASU 的公开课，带习题。全英文，但人家是真的把东西讲透了，能啃下来收益巨大

## 刷题去

PWN 这东西看十道不如调通一道。别一直盯着教程，早点上 [BUUOJ](https://buuoj.cn/) (貌似已经归档)或 [攻防世界](https://adworld.xctf.org.cn/) 动手。通过刷题自己总结模板。

- 栈溢出是后面所有东西的基础，先把这个吃透。从最简单的 ret2text 开始（覆盖返回地址跳到后门函数），到 ret2shellcode（写 shellcode 到栈/bss 再跳过去），到 ret2libc（泄露 libc 基址 → 算 system 和 /bin/sh → 二次 getshell，这是 PWN 的核心技能），再到 ret2syscall（凑 ROP 链调 execve）。BUUOJ 搜 rip、level0、ciscn_2019_c_1，ciscn_2019_c_1 基本是所有人的 ret2libc 入门题，主要就跟着wiki就行
- [B站这篇 PWN 入门视频](https://www.bilibili.com/video/BV1854y1y7Ro) 把上面这条线基本覆盖了，可以跟着走
- 先搞懂 malloc/free 在干什么、chunk 结构长什么样、bin 和 tcache 是什么，然后一个手法一个手法啃：fastbin double free、tcache poisoning、unsorted bin attack、off-by-one、UAF、house of 系列。[how2heap](https://github.com/shellphish/how2heap) 这个仓库每个攻击手法对应一个独立 C 文件，跑起来看效果比光读文字强太多

## 搞清楚这些

- gets 危险在哪，read 就一定安全吗，strcpy 和 strncpy 到底谁更坑、第三个参数写错了照样溢出你信不信？为什么 Canary 最低字节是 \x00，这玩意儿怎么就挡在栈上不被 puts 直接打印出来了？`__stack_chk_fail` 这个函数是干嘛的，能不能把它 GOT 表改了让 Canary 失效？
- ret 指令到底做了什么事，就两件——pop 栈顶到 rip 然后 jmp 过去，所以 ROP 链的本质是不是就是"让 ret 不停弹栈上的地址然后跳"？`pop rdi; ret` 这种 gadget 凭什么能用来给函数传参，x86 和 x64 传参方式有什么不同所以 ROP 链构造也不一样？
- PLT 和 GOT 到底怎么配合的？为什么第一次调 puts 和第二次跳的地方不一样？延迟绑定走了一遍什么流程，dl_runtime_resolve 又干了啥？Full RELRO 和 Partial RELRO 的区别是什么，为什么前者 GOT 就不能改了？
- malloc(0x20) 实际给你分了多大内存？chunk 的 header 长什么样，prev_size 和 size 各是干嘛的？free 掉之后这个 chunk 去了哪，什么时候合并什么时候不合并？fastbin / unsorted bin / tcache 各放什么大小的 chunk？
- gdb 调试时看到的栈地址和打远程时为什么不一样（因为 gdb 默认关 ASLR）？拿到一个泄露的 libc 地址怎么反查远程是哪个版本，用 LibcSearcher 或者 [libc.rip](https://libc.rip/) 输入后三位匹配？patchelf 换了 libc 程序跑不起来是不是 ld 版本不匹配，libc 和 ld 要一起换？

- 把 CTF-Wiki 每章节的例题下下来本地调通、写 writeup。
- 搞个不同 libc 版本的 docker 环境跑题目。比赛给的 libc 版本五花八门（2.23 老题、2.27 / 2.31 最常见），本地和远程不一致 payload 打不通能急死人。glibc-all-in-one + patchelf 或者直接上 [ctf-xinetd](https://github.com/ctFd/ctf-xinetd) docker 模板
- 暑假去打场比赛。ISCC、XCTF 分站赛、各种高校新生赛一堆。别想着拿奖，能做出一两道就赚了，赛后看别人的 wp 才是重点，经常能看到完全没想到的骚套路
- IDA 用熟，动态调式也要会用。

## 也可以瞟瞟别的方向

PWN 不是唯一的选择，暑假有空也可以折腾折腾别的，没准更对你的胃口：

- **区块链安全** — 智能合约审计，现在主流是 Solidity（以太坊）和 Rust（Solana）。合约一个 bug 可能就是几百万美金飞了，所以审计这行挺值钱。漏洞类型和 Web 有点像（重入、整数溢出、权限绕过），但门槛在于得先搞懂链和合约怎么跑。[Ethernaut](https://ethernaut.openzeppelin.com/) 是个不错的闯关式入门
- **模型安全** — 大模型火了之后新冒出来的方向，prompt injection、越狱（jailbreak）、对抗样本这些。新东西意味着没什么成熟的体系，瞎折腾反而容易出成果，适合喜欢蹭热点的人
- 还有 **逆向**（和 PWN 本来就是一家）、**密码学**（数学好可以试试，RSA 那套玩出花了）、**IoT / 固件安全**（路由器、摄像头这些），感兴趣都可以瞟一眼

暑假就是拿来试错的，每个都摸一下，挑一个喜欢的深入。
