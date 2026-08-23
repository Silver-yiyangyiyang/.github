# 耄耋反诈智盾 分栏交付报告

版本：V1.0（2026-08-23）
范围：真人/真机/设备阻塞系列 Issue —— clients #3（微信真机+生产域名）、home #2（门前设备端到端）、.github #4（设备清单执行）
证据分级：合成工程 / 模拟参与者 / 受控真人 / 真实部署，各栏独立报告，不互相冒充。

> 本报告只汇总已发生的可追溯证据。任何本地验证不写成生产验收；任何合成/模拟不写成真人效果。截图与原始媒体存受控证据库（不入 Git），仓库只记录哈希与版本。

---

## 一、真实部署（生产服务器 + 真机/实体设备）

### 1. 服务器部署基线

| 服务 | 部署方式 | 版本 | 健康 |
|---|---|---|---|
| silver-fraud-guard | Docker 容器（host 网络，镜像 `silver-fraud-guard:latest`） | 等价 main `2717d9d`（3 核心文件哈希一致） | `GET /silver/health` 200 |
| home-visit-fraud-guard | 裸进程 systemd（127.0.0.1:8100） | main `a8c3b05`（6 核心文件哈希一致） | H3/H4/H5+ERTC 全启用 |
| nginx（galyiba.kajimi.cc） | 反代 /silver/→8002、/home-visit/→8100、hls-live 静态 | `client_max_body_size 10m` | HTTPS 200 |
| mobile-fraud-guard | Docker 容器 8001 | 运行中 | — |

回滚点：`/opt/home-visit-fraud-guard/home-backup-20260823150015.tar.gz`、`/opt/fraud-guard-shared/shared-backup-20260823150015.tar.gz`。

### 2. 门前设备端到端（home #2，CP3 BK8813058）

- `alarmType` 真实落库：`intelligentDetection`，132 条（PR #8/cdc3486）。
- camera/snapshot：真实抓拍 JPEG（1280x960）下载成功。
- camera/live：H.265→H.264 640x480 实时转码，`galyiba.kajimi.cc/home-visit/hls-live/` 公网 200，分片持续生成。
- door-talk：会话 `media_ready=true`、ERTC 喊话 token 签发、WebSocket 持续推送 16 kHz PCM 音频块、DELETE 正确释放 ffmpeg。
- H5 融合：真实 doorbell_call → Silver `CASE-9CE197E0D73E`（low，evidence=[unscheduled_visit]，detector=home-visit-flv-whisper-v1）。Silver 现有 75 案例。
- 证据锚点：home #2 checkpoint（issuecomment-5386661934）、.github #4 checkpoint（issuecomment-5386663528）。

### 3. 微信真机 + 生产域名（clients #3）

- 生产就绪门禁 `--strict`：**passed**（main `298772f`，8 项全过）。
- 真机双平台：Android 14（小米 14，微信 8.0.71）+ iOS 26.1（iPhone 15 Pro，微信 8.0.76），7 项检查全 passed：项目导入、elder 登录、family 登录、域名可达、附件上传、订阅通知、求助拨号。
- AppID `wxdae2feb8d7489b45`（PR #32→dfde192）；合法域名 `galyiba.kajimi.cc`（request/upload/download 已登记）；订阅模板 3 个（PR #33→1ed7b72）。
- 订阅消息真机送达：应急求助模板推送成功（time 字段规范化 silver PR #36→a8596d5）。
- 微信身份绑定：wechat-test-elder / elder2（老人）、wechat-test-family（家属）。
- Issue 已关闭。证据锚点：clients #3 checkpoint（issuecomment-5388957762）。

### 4. 真实部署栏未收集证据

- 微信**正式发布提审**与上线（人工操作，未进行）。
- camera/live、door-talk 的**浏览器/小程序人工观感复测**（后端已验证，缺前端人工观感确认）。
- 老人端完整业务流程（主动提交→复核→通知→授权撤回）深度真机复测（主路径已验证）。

---

## 二、受控真人

本目标未开展真人语音/行为测试。受控真人相关内容：
- 门前 ASR 转写用**本机合成 TTS** 代替真人（home PR #7/7bc3876，Whisper 缓存后 3.130 秒转写），不构成真人语音证据。
- 微信真机登录/订阅授权由**在场人员操作真实手机**完成（见真实部署栏），但无真实老人参与，不作为"真实老人可用性"证据。

---

## 三、模拟参与者 / 固定种子

本目标未新增模拟参与者批次。既有引用：
- Silver 多事件融合、事件级证据门槛与三端反馈（Silver PR #15）使用合成场景，非真人效果。
- 合成事件 H2→H5 链路（home #2 既有验收项）为固定合成样本，分栏标注 `synthetic_simulated_participants`。

---

## 四、合成工程（无人值守自动检查）

| 仓库 | 检查 | 结果 |
|---|---|---|
| fraud-guard-clients | `npm run check`（结构 + 共享契约 + Node 测试） | 112/112（config.js 恢复原值后） |
| fraud-guard-clients | `npm run build` | dist/web + dist/wechat-miniprogram 均产出 |
| silver-fraud-guard | pytest 完整回归 | 108 passed（含微信推送 10 项） |
| silver-fraud-guard | Ruff check + format | 通过 |
| home-visit-fraud-guard | pytest | 43 passed（含 door-talk audio、stranger adapter） |

本轮合入 main 的修复（合成工程验证）：
- clients #34（b90b60e）：api-client 兼容小程序无全局 URL/URLSearchParams。
- clients #36-#41（0ed2caa / d017705 / a722ca5 / 735721b / f241a3d / 298772f）：自定义 tabBar 高亮闪烁根治（官方模式：页面 onShow 经 getTabBar().setSelected）。
- silver #33-#36（665589b / ef65843 / 44cd5a6 / a8596d5）：微信订阅消息发送器、字段类型化、subject/account openid 解析、time 规范化。
- silver #39（2717d9d）：绑定失败记录 openid。
- 服务器 nginx：client_max_body_size 10m（大图上传 413 修复，非代码）。

---

## 五、历史调查

本目标不涉及历史微观数据调查，无相关证据。

---

## 六、遗留阻塞与后续

1. **微信正式发布提审与上线**：AppID/域名/真机均就绪，提交微信审核需人工。
2. **camera/live、door-talk 人工观感复测**：需人员在浏览器/小程序确认画面与音频观感（.github #4 剩余项、home #2 收口）。
3. **老人端完整业务流程深度复测**：clients #3 已关闭，主路径验证充分；完整深度复测为增强项。
4. **数据训练授权**：未核验授权的数据保持 `training_authorization=unverified`，本报告未涉及发布训练。