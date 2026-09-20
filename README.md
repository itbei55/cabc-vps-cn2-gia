# 搬瓦工加拿大 VPS：温哥华 CABC_1 和 CABC_6 怎么选，能上 CN2 GIA 的套餐和真实价格一文看懂

搜“搬瓦工加拿大 VPS”的人，大致分两类：一类是在加拿大的华人、留学生，想找一台访问国内资源不卡、速度过得去的机器；另一类是想给网站或业务找个北美节点，又希望国内访问别太拉胯。这两类需求最后都会撞上同一个问题——搬瓦工在加拿大到底有几个机房，哪些套餐能用，钱要花多少。

这篇文章把温哥华两个机房的差别、能选加拿大机房的套餐、当前在售价格和优惠方式一次说清楚。数据来自官网在售页面和 2025 年的第三方测评，价格如有变动，以下单页为准。

## 先搞清楚：搬瓦工在加拿大只有温哥华一个城市，但有两个机房

搬瓦工（BandwagonHost）是加拿大 IT7 Networks 旗下的 VPS 商，它的加拿大节点全部部署在温哥华（Vancouver, BC），编号有两个：

| 机房编号 | 线路 | 硬件 | 适合谁 |
| --- | --- | --- | --- |
| CABC_1 | 普通国际线路，无回国直连优化 | 已升级 AMD CPU + NVMe SSD | 预算有限、主要面向北美用户 |
| CABC_6 | CN2 GIA（电信）+ CMIN2（移动）+ CUP（联通优化） | AMD EPYC + NVMe SSD 阵列 | 对国内访问速度有要求 |

两个机房都挂在 Cologix VAN3 机柜里，但走的是完全不同的网络。简单说：**CABC_1 是“便宜大碗”，CABC_6 是“花钱买线路”**。

很多新手的误区是以为买任意套餐都能用上 CN2 GIA 的加拿大机房，实际上 CABC_6 只对 CN2 GIA-E（E-Commerce）系列套餐开放。买错了套餐，就只能落在 CABC_1 的普通线路上。

## CABC_6 的线路到底是什么水平

2025 年搬瓦工对 CABC_6 做了一轮硬件升级，换成了 AMD EPYC（Genoa）处理器和 NVMe SSD 阵列。从 2025 年 7 月的第三方测评数据看：

- Geekbench 6 单核跑分约 1800 分，多核约 7800 分（6 核测试机），比老款 E5 时代的单核性能高出 2 到 3 倍
- 硬盘 4K 随机读写约 326 MB/s，IOPS 超过 8 万
- 本地测速可跑到 7-8 Gbps，iperf3 实测 5 Gbps 以上

线路方面，CABC_6 提供三网回程优化：电信走 CN2 GIA，联通和移动分别走对应的优化链路。到中国大陆的延迟大致在 150-200ms 之间。这里有个细节值得知道：中国电信目前没有在加拿大本地设置 CN2 GIA 的接入节点，所以路由是从温哥华经洛杉矶再回国的。这意味着它的国内访问速度会略逊于搬瓦工洛杉矶 DC6/DC9 机房，但仍然是“加拿大节点里能买到的最好回国线路”。

温哥华还有一个地理优势：它是北美离中国最近的主要城市之一，也是跨太平洋海缆的重要登陆点，物理距离摆在那里，基础延迟天然占便宜。

## 哪些套餐能选加拿大机房

搬瓦工当前在售的套餐分成几个系列，能落温哥华的如下：

- **KVM PROMO（Basic）系列**：可选 CABC_1，年付 $49.99 起，1Gbps 带宽，最便宜的入场券
- **CN2 GIA-E（E-Commerce）系列**：可选 CABC_6，季付 $49.99 起，2.5Gbps 带宽起步，支持在 15 个以上机房之间免费自助迁移
- 其余系列（香港、东京、大阪、新加坡的 CN2 GIA 专属套餐、迪拜系列、洛杉矶 SLA 系列）机房固定或不含加拿大节点

CN2 GIA-E 系列的核心卖点是“可迁移”：付款后在 KiwiVM 面板里可以随时把机器切换到洛杉矶 DC6/DC9、东京、大阪、新加坡、圣何塞、纽约、温哥华等节点，数据不丢、迁移免费。所以如果你买 GIA-E 是冲着加拿大去的，之后想换洛杉矶试一周再换回来，也不产生额外费用。这一点是 KVM PROMO 套餐没有的——促销类套餐绑定所选机房，不支持自由迁移。

## 全套餐价格对比（官网当前在售）

先说明两点：所有价格均为美元，优惠码可在此基础上再打折（后面讲）；标“固定机房”的套餐只能落在指定位置，不可迁移。

**KVM PROMO（Basic）系列 — 可选温哥华 CABC_1**

| 套餐 | 配置 | 价格 | 计费周期 | 购买 |
| --- | --- | --- | --- | --- |
| Basic 20G | 2核 / 1GB / 20GB SSD / 1TB流量 @1Gbps | $49.99 | 年付 | [ 购买 Basic 20G 年付套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=44) |
| Basic 40G | 3核 / 2GB / 40GB SSD / 2TB流量 @1Gbps | $52.99 / $99.99 | 半年付 / 年付 | [ 购买 Basic 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=45) |
| Basic 80G | 4核 / 4GB / 80GB SSD / 3TB流量 @1Gbps | $19.99 起，年付 $199.99 | 月付起 | [ 购买 Basic 80G](https://bit.ly/BandwagonHost) |
| Basic 160G | 5核 / 8GB / 160GB SSD / 4TB流量 @1Gbps | $39.99 起，年付 $399.99 | 月付起 | [ 购买 Basic 160G](https://bit.ly/BandwagonHost) |
| Basic 320G | 6核 / 16GB / 320GB SSD / 5TB流量 @1Gbps | $79.99 起，年付 $799.99 | 月付起 | [ 购买 Basic 320G](https://bit.ly/BandwagonHost) |
| Basic 480G | 7核 / 24GB / 480GB SSD / 6TB流量 @1Gbps | $119.99 起，年付 $1199.99 | 月付起 | [ 购买 Basic 480G](https://bit.ly/BandwagonHost) |

**CN2 GIA-E（E-Commerce）系列 — 可选温哥华 CABC_6，支持 15+ 机房迁移**

| 套餐 | 配置 | 价格 | 计费周期 | 购买 |
| --- | --- | --- | --- | --- |
| E-Commerce 20G | 2核 / 1GB / 20GB / 1TB @2.5Gbps | $49.99 / $169.99 | 季付 / 年付 | [ 购买 CN2 GIA-E 20G 季付套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=87) |
| E-Commerce 40G | 3核 / 2GB / 40GB / 2TB @2.5Gbps | $89.99 / $299.99 | 季付 / 年付 | [ 购买 CN2 GIA-E 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=88) |
| E-Commerce 80G | 4核 / 4GB / 80GB / 3TB @2.5Gbps | $56.99 / $549.99 | 月付 / 年付 | [ 购买 CN2 GIA-E 80G](https://bandwagonhost.com/aff.php?aff=79616&pid=89) |
| E-Commerce 160G | 6核 / 8GB / 160GB / 5TB @5Gbps | $86.99 / $879.99 | 月付 / 年付 | [ 购买 CN2 GIA-E 160G](https://bandwagonhost.com/aff.php?aff=79616&pid=90) |
| E-Commerce 320G | 8核 / 16GB / 320GB / 8TB @5Gbps | $159.99 / $1599.99 | 月付 / 年付 | [ 购买 CN2 GIA-E 320G](https://bandwagonhost.com/aff.php?aff=79616&pid=91) |
| E-Commerce 640G | 10核 / 32GB / 640GB / 10TB @10Gbps | $289.99 / $2759.99 | 月付 / 年付 | [ 购买 CN2 GIA-E 640G](https://bandwagonhost.com/aff.php?aff=79616&pid=92) |
| E-Commerce 1280G | 12核 / 64GB / 1280GB / 12TB @10Gbps | $549.99 / $5399.99 | 月付 / 年付 | [ 购买 CN2 GIA-E 1280G](https://bandwagonhost.com/aff.php?aff=79616&pid=93) |
| E-Commerce 1280G 高流量版 | 12核 / 64GB / 1280GB / 15TB @10Gbps | $679 / $6790 | 月付 / 年付 | [ 购买 1280G 高流量版](https://bandwagonhost.com/aff.php?aff=79616&pid=160) |
| E-Commerce 1280G 20TB版 | 12核 / 64GB / 1280GB / 20TB @10Gbps | $899 / $8999 | 月付 / 年付 | [ 购买 1280G 20TB版](https://bandwagonhost.com/aff.php?aff=79616&pid=161) |
| E-Commerce 1280G 高CPU版 | 24核 / 64GB / 1280GB / 12TB @10Gbps | $749.99 / $7599.00 | 月付 / 年付 | [ 购买 1280G 高CPU版](https://bandwagonhost.com/aff.php?aff=79616&pid=148) |

**ECOMMERCE SLA 系列 — 固定洛杉矶，99.99% 在线率协议**

| 套餐 | 配置 | 价格 | 计费周期 | 购买 |
| --- | --- | --- | --- | --- |
| SLA 20G | 2核AMD / 1GB ECC / 20GB NVMe / 1TB @2.5Gbps | $65.89 / $239.99 | 季付 / 年付 | [ 购买 SLA 20G](https://bandwagonhost.com/aff.php?aff=79616&pid=164) |
| SLA 40G | 3核AMD / 2GB ECC / 40GB NVMe / 2TB @2.5Gbps | $116.99 / $399.99 | 季付 / 年付 | [ 购买 SLA 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=165) |
| SLA 80G | 4核AMD / 4GB ECC / 80GB NVMe / 3TB @2.5Gbps | $69.99 起，年付 $699.99 | 月付起 | [ 购买 SLA 80G](https://bit.ly/BandwagonHost) |
| SLA 160G | 6核AMD / 8GB ECC / 160GB NVMe / 5TB @5Gbps | $109.99 起，年付 $1099.99 | 月付起 | [ 购买 SLA 160G](https://bit.ly/BandwagonHost) |

**香港 / 东京 CN2 GIA 系列 — 固定机房**

| 套餐 | 配置 | 价格（月付 / 年付） | 购买 |
| --- | --- | --- | --- |
| 香港 CN2 GIA 40G | 2核 / 2GB / 40GB / 500GB @1Gbps | $89.99 / $899.99 | [ 购买香港 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=95) |
| 香港 CN2 GIA 80G | 4核 / 4GB / 80GB / 1TB @1Gbps | $155.99 / $1559.99 | [ 购买香港 80G](https://bandwagonhost.com/aff.php?aff=79616&pid=96) |
| 香港 CN2 GIA 160G | 6核 / 8GB / 160GB / 2TB @1Gbps | $299.99 / $2999.99 | [ 购买香港 160G](https://bit.ly/BandwagonHost) |
| 香港 CN2 GIA 320G | 8核 / 16GB / 320GB / 4TB @1Gbps | $589.99 / $5899.99 | [ 购买香港 320G](https://bit.ly/BandwagonHost) |
| 香港 CN2 GIA 640G | 10核 / 32GB / 640GB / 6TB @1Gbps | $989.99 / $9989.99 | [ 购买香港 640G](https://bit.ly/BandwagonHost) |
| 香港 CN2 GIA 1280G | 12核 / 64GB / 1280GB / 8TB @1Gbps | $1889.99 / $18989.99 | [ 购买香港 1280G](https://bit.ly/BandwagonHost) |
| 东京 CN2 GIA 40G | 2核 / 2GB / 40GB / 500GB @1.2Gbps | $89.99 / $899.99 | [ 购买东京 40G](https://bit.ly/BandwagonHost) |
| 东京 CN2 GIA 80G | 4核 / 4GB / 80GB / 1TB @1.2Gbps | $155.99 / $1559.99 | [ 购买东京 80G](https://bit.ly/BandwagonHost) |
| 东京 CN2 GIA 160G | 6核 / 8GB / 160GB / 2TB @1.2Gbps | $299.99 / $2999.99 | [ 购买东京 160G](https://bit.ly/BandwagonHost) |
| 东京 CN2 GIA 320G | 8核 / 16GB / 320GB / 4TB @1.2Gbps | $589.99 / $5899.99 | [ 购买东京 320G](https://bit.ly/BandwagonHost) |
| 东京 CN2 GIA 640G | 10核 / 32GB / 640GB / 6TB @1.2Gbps | $989.99 / $9989.99 | [ 购买东京 640G](https://bit.ly/BandwagonHost) |
| 东京 CN2 GIA 1280G | 12核 / 64GB / 1280GB / 8TB @1.2Gbps | $1889.99 / $18989.99 | [ 购买东京 1280G](https://bit.ly/BandwagonHost) |

**大阪 / 新加坡 CN2 GIA 系列 — 固定机房**

| 套餐 | 配置 | 价格（月付 / 年付） | 购买 |
| --- | --- | --- | --- |
| 大阪 CN2 GIA 40G | 2核 / 2GB / 40GB / 500GB @1.5Gbps | $49.99 / $499.99 | [ 购买大阪 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=134) |
| 大阪 CN2 GIA 80G | 4核 / 4GB / 80GB / 1TB @1.5Gbps | $86.99 / $869.99 | [ 购买大阪 80G](https://bandwagonhost.com/aff.php?aff=79616&pid=135) |
| 大阪 CN2 GIA 160G | 6核 / 8GB / 160GB / 2TB @1.5Gbps | $165.99 / $1665.99 | [ 购买大阪 160G](https://bit.ly/BandwagonHost) |
| 大阪 CN2 GIA 320G | 8核 / 16GB / 320GB / 4TB @1.5Gbps | $329.99 / $3199.00 | [ 购买大阪 320G](https://bit.ly/BandwagonHost) |
| 大阪 CN2 GIA 640G | 10核 / 32GB / 640GB / 6TB @1.5Gbps | $549.99 / $5549.99 | [ 购买大阪 640G](https://bit.ly/BandwagonHost) |
| 大阪 CN2 GIA 1280G | 12核 / 64GB / 1280GB / 8TB @1.5Gbps | $1059.99 / $10559.99 | [ 购买大阪 1280G](https://bit.ly/BandwagonHost) |
| 新加坡 CN2 GIA 40G | 2核 / 2GB / 40GB / 500GB @1.5Gbps | $49.99 / $499.99 | [ 购买新加坡 40G](https://bit.ly/BandwagonHost) |
| 新加坡 CN2 GIA 80G | 4核 / 4GB / 80GB / 1TB @1.5Gbps | $86.99 / $869.99 | [ 购买新加坡 80G](https://bit.ly/BandwagonHost) |
| 新加坡 CN2 GIA 160G | 6核 / 8GB / 160GB / 2TB @2.5Gbps | $165.99 / $1665.99 | [ 购买新加坡 160G](https://bit.ly/BandwagonHost) |
| 新加坡 CN2 GIA 320G | 8核 / 16GB / 320GB / 4TB @2.5Gbps | $329.99 / $3199.00 | [ 购买新加坡 320G](https://bit.ly/BandwagonHost) |
| 新加坡 CN2 GIA 640G | 10核 / 32GB / 640GB / 6TB @5Gbps | $549.99 / $5549.99 | [ 购买新加坡 640G](https://bit.ly/BandwagonHost) |
| 新加坡 CN2 GIA 1280G | 12核 / 64GB / 1280GB / 8TB @5Gbps | $1059.99 / $10559.99 | [ 购买新加坡 1280G](https://bit.ly/BandwagonHost) |

**迪拜（ECOMMERCE）系列 — 支持迁移机房**

| 套餐 | 配置 | 价格（月付 / 年付） | 购买 |
| --- | --- | --- | --- |
| 迪拜 20G | 2核 / 1GB / 20GB / 500GB @1Gbps | $19.99 / $169.99 | [ 购买迪拜 20G](https://bit.ly/BandwagonHost) |
| 迪拜 40G | 3核 / 2GB / 40GB / 1TB @1Gbps | $32.99 / $299.99 | [ 购买迪拜 40G](https://bit.ly/BandwagonHost) |
| 迪拜 80G | 4核 / 4GB / 80GB / 2TB @1Gbps | $56.99 / $549.99 | [ 购买迪拜 80G](https://bit.ly/BandwagonHost) |
| 迪拜 160G | 6核 / 8GB / 160GB / 3TB @1Gbps | $86.99 / $879.99 | [ 购买迪拜 160G](https://bit.ly/BandwagonHost) |
| 迪拜 320G | 8核 / 16GB / 320GB / 4TB @1Gbps | $159.99 / $1599.99 | [ 购买迪拜 320G](https://bit.ly/BandwagonHost) |
| 迪拜 640G | 10核 / 32GB / 640GB / 5TB @1Gbps | $289.99 / $2759.99 | [ 购买迪拜 640G](https://bit.ly/BandwagonHost) |
| 迪拜 1280G | 12核 / 64GB / 1280GB / 6TB @1Gbps | $549.99 / $5399.99 | [ 购买迪拜 1280G](https://bit.ly/BandwagonHost) |

所有套餐都包含：独立 IPv4 一个、IPv6 /64 路由子网、免费自动备份、免费快照、KiwiVM 面板（重装系统、控制台、rDNS、机房迁移等）、99.95% 在线率保障（SLA 系列为 99.99%）。

另外还有一个值得盯着的**限量款**：THE PLAN，年付 $99 美元，2核/2GB/40GB SSD/1TB 流量，可以在 18 个机房（含香港）之间随意切换，长期处于缺货状态，补货时经常被秒光。如果只是想低成本玩转多机房，看到补货就别犹豫，同配置的常规 GIA-E 套餐年付要 $299.99。可以随时 [👉 查看搬瓦工各套餐最新库存和补货情况](https://bit.ly/BandwagonHost)。

## 优惠码：大多数时候能省 6.77%

搬瓦工的优惠码体系比较稳定：常年有效的是一个 **6.77% 循环折扣码**，社区里流传最广的是 `BWHCGLUKKB`，近期也有用户使用 `BWH3HYATVBJW`。循环的意思是续费同样打折，不是只优惠首单。

以 CN2 GIA-E 20G 年付 $169.99 为例，6.77% 折扣后约 $158.49，一年省 11 美元出头；KVM 20G 年付 $49.99 折后约 $46.60。降幅不算惊人，但架不住是永久循环的。

比优惠码更大的省钱窗口是**双十一和黑色星期五**这两个固定促销节点，官方通常会放出力度更大的全场折扣码。如果不急，把购买计划放在这两个时间点附近更划算。结账时直接 [👉 进入搬瓦工购买页面并使用可用优惠码](https://bit.ly/BandwagonHost) 即可，优惠码在购物车页面填写，折扣实时生效。

## 购买流程和支付方式

整个购买过程对国内用户很友好，不需要外币信用卡：

1. 选定套餐和计费周期（GIA-E 系列记得季付起买，KVM 促销款只有年付）
2. 注册账户，填写邮箱和基本信息
3. 购物车页面填优惠码
4. 选择支付方式：支持支付宝、微信支付、PayPal 和信用卡
5. 付款后几分钟内开机，登录 KiwiVM 面板选机房或迁移

买 GIA-E 套餐想落温哥华的，开机后进 KiwiVM 的迁移选项选 CABC_6 就行；买了 KVM 促销款则在下单时直接选 CABC_1。

## 用它建站的几个实际问题

**免备案**：搬瓦工所有机房都在境外，网站放温哥华不需要备案，域名也不受注册商限制。

**性能有上限**：所有套餐都有 CPU 使用积分限制，不能长期跑满 CPU。轻量建站、博客、个人项目完全够用；持续高负载的计算任务要掂量一下，这也是它价格能压下来的原因之一。

**完全自管理**：没有托管服务，系统装什么、安全怎么配都自己来。好处是给的是完整 root 权限的 KVM 虚拟化，支持 AlmaLinux、Debian、Ubuntu、RockyLinux 等主流发行版，也能自己挂 ISO 安装。

**IP 质量**：温哥华节点分配的是北美原生 IP 段。流媒体解锁因 IP 段而异，谁也不能保证某个段一定能看某家平台，这方面别抱太高预期，IP 不满意可以在面板里按周期更换（SLA 系列每两周免费换一次）。

## 退款政策：30 天内可以反悔

搬瓦工有 30 天退款窗口，但条件不少，下单前最好确认自己符合：

- 账户创建不超过 30 天
- 此前没有申请过退款
- 账户下 VPS 少于 3 台，累计支付金额低于 100 美元，付款次数少于 10 次
- 分配的 IP 未被封禁、未因滥用被更换过

满足条件的退款是全额原路退回。换句话说，首次购买最便宜套餐试水，不满意在一个月内退掉，这条路是通的。

## 常见问题

**搬瓦工加拿大 VPS 延迟多少？** CABC_6 到国内三网大约 150-200ms，路由经洛杉矶回程；CABC_1 走普通线路，延迟和稳定性看运气。

**能从别的机房迁到温哥华吗？** GIA-E 系列可以，KiwiVM 面板自助操作，免费且不丢数据；KVM 促销款不支持。

**年付和季付怎么选？** GIA-E 系列小配置（20G/40G）季付门槛最低，$49.99 就能起步，先跑一段时间确认线路满意，续费时再考虑年付。

**香港套餐为什么贵这么多？** 香港 40G 月付就要 $89.99，一年近 $900，是 GIA-E 同类配置的五倍以上。亚洲 CN2 GIA 带宽采购成本本来就高，这个定价反映的是成本，不是溢价。

**个人信息放在上面安全吗？** 搬瓦工是正规运营多年的商家，但 VPS 是自管理服务，数据安全取决于你自己的配置习惯，面板提供的免费备份和快照建议开启。

## 选购建议

把几条核验过的事实放在一起，选择其实不难：

- 只是要一台便宜的北美机器，不在乎回国速度：KVM Basic 20G，年付 $49.99，用码后约 $46.6，可选温哥华 CABC_1
- 在加拿大，经常访问国内资源，或者国内用户要访问你的服务：CN2 GIA-E 20G 季付 $49.99 起步，落到 CABC_6，这是加拿大节点能买到的最好线路，外加 15+ 机房随时迁移的灵活性
- 需要极低延迟服务国内用户：加预算看香港 CN2 GIA（月付 $89.99 起），或者用 GIA-E 迁到洛杉矶 DC6/DC9
- 想低成本多机房切换：等 THE PLAN 补货，$99/年换 18 个机房的自由

搬瓦工的配置参数在云主机市场里从来不是最亮的，它卖的核心是线路和自由迁移机制。加拿大 VPS 这个需求恰好踩在它的长处上——温哥华 CABC_6 是市面上少见的、能用 CN2 GIA 优化线路的加拿大节点。预算对得上的话，这台机器大概率不会让你后悔。
