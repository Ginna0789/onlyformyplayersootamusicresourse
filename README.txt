跑团 BGM · 10 首（网易云 128kbps，已下载并校验 ID3）
=========================================================

文件名全为纯 ASCII，合计 29.5 MB。

中英对照
---------------------------------------------------------
8AM_Tune.mp3                早八的小曲            Whirling-In-Rags, 8 AM（Sea Power）
Tense.mp3                   紧张                  Tiger King（Sea Power）
Oppressive_Tension.mp3      压抑紧张              Your Body Betrays Your Degeneracy（Sea Power）
Area_X_Tension.mp3          X区域紧张             End Titles (Alt Version)（Ben Salisbury / Geoff Barrow）
Fishfolk_Chant.mp3          鱼人低吟              奉神御詠歌（柚楽弥衣）
Hyped_Battle_Electro.mp3    热血沸腾激昂战斗电音   FCKD（Hyper）
Battle_But_Funk.mp3         战斗但是放克          HERE I COME（ANT / QUE）
Socket_Calibration.mp3      插座校准              Socket Calibration（Mike Klubnika）
Corpse_Nest_I.mp3           屍人ノ巣Ⅰ             屍人ノ巣Ⅰ（冷水ひとみ）— 无备注，意译
Siren_Alarm.mp3             塞壬警报              The Siren（冷水ひとみ）

为什么要走这一步
---------------------------------------------------------
网易云 outer/url 的 302 响应不带 Access-Control-Allow-Origin，
而 obr.dnd.center 音乐板把 audio.crossOrigin 写死为 "anonymous"，
所以网易云链接在音乐板里永远播不了（CORS 拦死）。

网易云 CDN 实链虽然带 ACAO，但签名只有约 2 小时有效期，
跑团跑一半就全变 403，不可用。

=> 唯一能同时满足「淡入淡出 + 永久 + 玩家能听」的办法：
   把 mp3 放到带 CORS 的静态托管上，用永久链接喂给音乐板。

为什么选 jsDelivr（已实测）
---------------------------------------------------------
- access-control-allow-origin: *          → 音乐板能过 CORS
- 206 Partial Content + content-range     → 支持拖动进度条
- Content-Type: audio/mpeg                → 浏览器正常识别
- Cache-Control: immutable, max-age=31536000 → 永久缓存
- 国内有 CDN 节点                         → 玩家端加载快

上传步骤（GitHub 网页版，不需要装任何东西）
---------------------------------------------------------
1. 打开 https://github.com/new
2. Repository name 随便填，比如 bgm
3. 选 Public（jsDelivr 只认公开仓库）
4. 勾 Add a README file，点 Create repository
5. 进入仓库，点 Add file → Upload files
6. 把本目录下 10 个 mp3 全部拖进去（README.txt / jsdelivr-links.txt 不用传）
7. 点最下方 Commit changes

传完之后打开 jsdelivr-links.txt，替换 <USER> 和 <REPO> 即可。

链接格式
---------------------------------------------------------
https://cdn.jsdelivr.net/gh/<用户名>/<仓库名>@main/<文件名>

注意
---------------------------------------------------------
- 仓库必须是 Public
- 这些是商业 OST，放公开仓库严格说有版权风险；
  个人跑团自用一般没人管，但别拿去公开分发
