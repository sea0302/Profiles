简介
Clash、Kitsunebi、Mellow、Potatso、Quantumult(X)、Shadowrocket、Pepi(ShadowRay)、Surge 的配置规则文件

规则
规则分为标准版、专业版和回国版

标准版
使用公共 DNS 达到快速、准确、稳定及安全的解析
国内直连、海外加速
Apple 服务加速
海外流媒体（部分）及大陆流媒体面向港澳台限定（部分）服务指定节点
专业版
在标准版的基础上加入：

拦截运营商劫持
拦截臭名昭著的欺诈网站（如思杰马克丁伪造的一系列软件官网、MacKeeper等）
拦截应用广告 ⚠️ 网页广告请使用 Safari 内容拦截器如 ADGuard 或集成去广告功能的浏览器
TikTok 解锁
回国版
国内流媒体服务解锁
拦截应用广告 ⚠️ 网页广告请使用 Safari 内容拦截器如 ADGuard 或集成去广告功能的浏览器
下载
移动设备长按版本名即可「拷贝」链接进行导入
有自定义规则需求方才使用「快捷指令」
导入配置教程
Kitsunebi 配置导入
Quantumult 配置导入
Quantumult X 配置导入
Shadowrocket 配置导入
Surge 配置导入
应用	标准版	专业版	回国版
Clash(ClashX / Clash for Windows)	无	Pro	BacktoCN
Kitsunebi(iOS / Android)	Basic	Pro	BacktoCN
Mellow	无	Pro	无
Potatso	无	Pro	无
Quantumult | 快捷指令	Basic	Pro / Rejection	BacktoCN / Rejection
Quantumult X | Zure 图标组	无	Pro	BacktoCN
Shadowrocket / Pepi | 快捷指令	Basic	Pro	BacktoCN
Surge 2 | 快捷指令	Basic	Pro	BacktoCN
Surge 3+ | 快捷指令	无	Surge3	无
说明
DNS 设置
如果经常使用的网络没有 DNS 劫持问题，则配置为使用系统 DNS 并追加公共 DNS，如：

119.29.29.29,223.5.5.5,system
如果经常使用的网络存在 DNS 劫持问题，则配置为仅使用公共 DNS，如：

119.29.29.29,223.5.5.5
为什么没有海外 DNS
首先目前海外 DNS 基本在国内没有节点会导致 CDN 解析不准确如解析到香港节点（包括腾讯的 119.28.28.28 因运营商没有对路由进行更新所导致）

其次很多人觉得海外公共 DNS 干净，而实际情况是不仅因为解析结果没有指向适合你网络的 CDN 上导致网络卡顿，被污染的域名依旧污染，甚至部分区域的运营商还对海外 DNS 请求完全进行抢答，所以没有意义。

关于 Surge Ruleset 和 Quantumult X Filter Remote 说明
要求排序如下：

Unbreak.list - 用于修正后续规则行为
Advertising.list - 广告、行为分析、隐私追踪（macOS 不建议开启）
Hijacking.list - 劫持（运营商、臭名昭著的诈骗网站或恶意应用）
GlobalMedia(ForeignMedia).list - 国际流媒体
HKMTMedia(DomesticMedia).list - 大陆流媒体面向港澳台限定（可不加）
Global.list - 国际网站/应用
Apple.list - Apple 服务（可不加）
China.list - 国内网站/应用
说明

如若不需要观看哔哩哔哩、爱奇艺面向港澳台的限定内容可不加「HKMTMedia(DomesticMedia).list」。
如若不需要代理 Apple 服务可不加「Apple.list」，若加入必须在「Global.list」和「China.list」之间。
如需细化流媒体如「Youtube.list」需要加在「GlobalMedia(ForeignMedia).list」之前。
如需应用类的如「Telegram.list、Google.list、PayPal.list」需要加在「Global.list」之前。
一般情况下默认引入上述 8 个（如不需要 HKMTMedia(DomesticMedia) 和 Apple 可减至 6 个）即可，那么为什么还有更多的如「Youtube.list、Netflix.list、Spotify.list、Mail.list」？

对于一些「进阶玩家」来说其拥有专用于观看流媒体的线路，比如观看限定区域的 Netflix、Hulu、HBO 等，所以引入相关 .list 建立一个策略组设置相应服务区节点线路。但对于普通用户来说，那些「Youtube.list、Hulu.list」来说都是集成在「GlobalMedia(ForeignMedia).list」中不需要额外引入。
对于一些「机场」来说为了避免有恶意用户利用节点线路滥发垃圾邮件，所以对服务器相关邮件端口进行了屏蔽，这时候可以引入「Mail.list」指定一个可收发邮件对节点。
对于一些「进阶玩家」来说其拥有高速的新加坡节点线路，为了提升 Telegram 使用体验所以会引入「Telegram.list」指定一些节点。
综上所述、以此类推，独立的 .list 一般都集成在了默认的 6 条 .list 文件中，如果你没有进阶的定制化需求是不 需 要引入那么多的，根据需求使用才是 Ruleset/Filter 的灵活用法，规则不是越多越好。

获取更多 list

Surge：https://github.com/ConnersHua/Profiles/tree/master/Surge/Ruleset

Quantumult X：https://github.com/ConnersHua/Profiles/tree/master/Quantumult/X/Filter

.list 文件真实地址点击「Raw」获得，直接复制网页地址如「 https://github.com/ConnersHua/Profiles/blob/master/Quantumult/X/Filter/Advertising.list 」是错误的，确保你引用的地址是「 https://raw.githubusercontent.com/ 」开头

常见问题
0.什么是白名单和黑名单模式？该使用哪个？

⚠️ 注意：仅推荐使用白名单模式，除非你有特殊需求。

简单的说，除了规则以外的请求，都走代理就是白名单模式，都走直连就是黑名单模式。

那么，是不是白名单模式应该把全中国的网址都写进规则？

不是，仅是该代理还是直连的问题上使用 GeoIP 规则就可以解决绝大多数的中国网站直连。

1.遇到连接公共场所 Wi-Fi 时验证页面无法显示？

暂时关闭待验证成功后再开启，或者如校园网运营商客户端的可将相关域名或 IP 地址加入到「skip-proxy」中（Surge、Shadowrocket、Pepi(ShadowRay) 支持）。

2.iOS 12 上 Siri 无法正常使用

#55 （仅）iOS 12 的 Bug，尝试多次重启直至正常。

3.关于知乎避免强制「App 内打开」

此功能目前仅 Surge 用户可用，若想使用桌面版网页的知乎（但会影响 App）可以在「Header Rewrite」加入复写规则：

^https?://www\.zhihu\.com header-replace User-Agent Mozilla/5.0  (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, like  Gecko) Version/12.0.2 Safari/605.1.15
4.如何解锁 TikTok？

仅支持 Surge 和 Quantumult(X) 专业版规则。另外，复写规则默认设置的 TikTok 为日本区，若想切换到其他地区，在软件里的复写设置中将「JP」修改成其他地区英文缩写即可。

5.Apple News 具体怎么使用

副作用为 macOS 及 iOS 12 以前的系统地图会变成海外 TOMTOM 版。

关于解锁 Apple News 区域限制

6.Clash 连接不上内网服务器

移除掉配置内的 DNS 配置。

7.打开「淘宝」等阿里巴巴系应用时遇到「访问被拒绝」、「请检查是否使用了代理」等提示

部分「阿里云」节点会导致此问题，如遇此问题主节点换成其他的。

8.关于 Speedtest 想直连/代理？

规则对于 Speedtest 不是绝对的直连也不是绝对的代理，对于国内测速点是直连，对于国外测速点是代理。

默认打开 Speedtest 会自动选择适用于代理服务器节点的国外测速节点，若要进行国内网速测试手动修改「测速点」搜索你所在城市或省会的拼音然后选择运营商即可。

关于去广告
⚠️ 为什么 Youtube、知乎、微博等应用（存在于 MitM 域名列表）无法使用？
开启「HTTPS 解密(MitM)」功能
安装证书
到系统「设置 > 通用 > 关于本机」中底部的「证书信任设置」中信任所安装的证书！
为什么某应用还是有广告
1.缓存

有些应用会将广告缓存，如果在使用规则前应用就已经缓存了广告，所以你需要：

应用内设置里清除缓存。
但有的应用并不会清除广告的缓存，所以需要将应用删除重装。
⚠️ 广告加载是实时的，这就意味着：

需要实时开着类 Surge 应用托管网络
即便一直开着，但在遇到信号断开重连、蜂窝数据和 Wi-Fi 网络切换时会有一些网络请求先于类 Surge 应用加载导致广告出现，怎么办？看上面两步。
2.功能

广告阻止不仅于使用 [Rule] 规则，有的广告需要 [URL Rewrite] 和 [MITM]，这就意味着：

Surge 虽然支持 [URL Rewrite] 和 [MITM]，但无法处理 TUN 的广告。
Quantumult 虽然支持 [URL Rewrite] 和 [MITM]，但需要在「更多 > 附加功能」中开启「激进阻止」以更全面的支持（X 版本默认带此功能）否则同 Surge 效果一样，但 Quantumult 对于 IP 不会进行 MitM，所以有的广告不能如 Surge 一般去除。
Shadowrocket 的 [MITM] 功能不稳定影响正常功能，已从规则配置中移除，不再支持。
Kitsunebi 不支持 [URL Rewrite] 和 [MITM]。
Surfboard 仅支持 [URL Rewrite] 且仅支持 302 没有阻止功能。
3.规则不是万能的

不是所有广告都能简单的依靠规则阻止。

4.其他

Youtube 去广告会造成以下问题

网页版可能无法正常播放
YouTube Premium 用户无法正常播放
Quantumult 遇到片头广告时可能会卡黑屏
所以默认并没有启用，如果仍需启用需在「HTTPS 解密(MitM)」的「主机名」列表中添加：

*.googlevideo.com
各应用的差异性
前面有略微提到有的功能在这个应用上但在另一个应用上没有，首先希望大家能明白，一个功能的有无并不能说明什么，这里面涉及到系统的限制和应用作者对于功能实现的一些考量，那么差异性大致有哪些：

比如说 Surfboard：从 Android 7 开始不支持 MitM 所以没法支持 MitM 和 USER-AGENT 规则类型（但支持 PROCESS-NAME 规则类型）

比如说 Kitsunebi：在一众类似 Surge 应用里它可以说是最不一样的，因为这是一个基于 v2ray-core 的图形界面客户端，那么 v2ray-core 不支持的功能它也不支持是合乎情理的。

比如说 Quantumult：

不支持 IP ServerName 的 MitM 是考虑到无法确认上游自签名的服务器是否有被人 MitM 目前只能如此折中处理。
Quantumult 的 USER-AGENT 规则类型的优先级不像 Surge 一类应用那么高，所以 Unbreak 中的一些以 UA 规则来修正行为的策略是无效的。
不同于其他软件以最前面的生效，一些重复的规则以最后出现的规则设定生效。
比如说 Quantumult X：

因为一些软件的 User-Agent 的名字是同名的，所以降低了 USER-AGENT 规则类型的优先级到了一个基本不能用的状态。

host-keyword 的优先级没有其他 host 规则类型高，也就是说你如果有如下这样的规则

host-keyword, baidu, reject
host-suffix, baidu.com, direct
不管规则在 remote 还是 local、不管规则顺序先后，host-keyword, baidu, reject 都是不生效的。

比如说 Surge：Rewrite 和 MitM 不能如 Ruleset 规则那样远程管理，不能处理 TUN 的广告。

还有一些不同没有说明，这里主要挑些经常会遇到的，以上差异化说明仅是为了方便选择购买和使用应用时的注意事项，一个应用的某个功能的缺失，并不能说明这个应用不好而是不符合你的需求，你需要了解你的需求和你想要购买的产品，根据需求选择产品也是这些年 Apple 及其员工一直在给我的理念。

最后
Good Luck Have Fun

感谢
lhie1
Lison Bin
linjiacheng
Booui
liceva
JO2EY
Choler
xream
gkeyes
许可
MIT License
