# 真机与人机待验总清单

状态基线：**2026-08-31**  
跟踪 Issue：[`.github` #4](https://github.com/Silver-yiyangyiyang/.github/issues/4)（无声设备走查）  
逐步操作稿：[`jbgs-proposal/docs/REAL_DEVICE_WALKTHROUGH.md`](https://github.com/Silver-yiyangyiyang/jbgs-proposal/blob/main/docs/REAL_DEVICE_WALKTHROUGH.md)

> 本文只登记**仍缺现场证据**的项。工程回归、微信开发者工具、Playwright 和合成 HTTP **不能**把下表勾成已通过，也**不能**据此关闭对应 Issue。  
> 本文不冒充任何未勾选项已经验收。不写入 OpenID、accessToken、AppSecret、完整设备序列号或原始门前媒体。

## 0. 使用规则

1. 对应 Issue 的代码可以进 `main`；**缺本表证据就保持 OPEN**。
2. 勾选时在 Issue 评论留下：日期、角色（老人/家属/社区）、平台（Android/iOS/浏览器）、去敏截图或录屏的 SHA-256（原件放受控证据库）。
3. 开发者工具、模拟器、本机浏览器、`pytest`、`npm run check` 一律记为 L1，不算真机。
4. 已有 L2 指定设备证据的，不要重做；也不要外推成 L3 生产/真实老人效果。

---

## 1. 已经做过、不要重做的 L2（仍不是 L3）

| 范围 | 已证明 | 仍不能写成 |
|---|---|---|
| 门前设备（`.github` #4 已勾选部分） | 指定 CP3 上人形告警、门铃呼叫、HLS 直播、抓拍、门外对话听门外（不发声） | 小程序半屏/直播按钮观感、防拆/离线、正式发布效果 |
| 微信登录与域名（`clients` #3 已关闭） | 指定 Android/iOS 真机登录、合法域名、附件上传、求助订阅主路径 | 正式提审上线、完整老人业务流程、家属 fan-out 送达 |
| 生产服务健康 | 指定服务器上 Silver / Home / Community 可访问 | 当前生产代码已与最新 `main` 逐文件一致 |

详细分栏见 [`DELIVERY_REPORT.md`](DELIVERY_REPORT.md)。书面授权原件、自然场景、真实老人可用性仍为**未收集**。

---

## 2. 微信小程序真机（Android 与 iOS 各至少一台）

开发者工具打不开萤石半屏；门前直播和半屏必须以真机点击为准。

| 缺什么 | 关联 Issue | 工程现状 | 不能用什么代替 |
|---|---|---|---|
| 老人端完整业务流程深度复测 | [clients #46](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/46) | 走查稿已存在 | 模拟器或逐步截图 |
| 正式版功能与新 UI 在真机上的加载/空态/失败回退 | [clients #71](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/71) | 主线已合入；模拟器部分页面可进 | 静态 PSD / 浏览器预览 |
| 口语文案真机观感 | [clients #72](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/72) | 源码已改；模拟器首页口语已见到 | 开发者工具截图 |
| 识别结果按角色进入老人/家属/社区 | [clients #65](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/65) | 契约与页面已接线 | Playwright 工作台 |
| 门前预警走案件审核；事件列表可折叠；老人无「提交审核」 | [clients #64](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/64) | 产品契约要求保留「联系家人 / 录一段 / 把这段话交给家人」 | 代码 diff |
| 老人主动上报后，家属/社区审核文字在真机结果页可见 | [clients #63](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/63) | 模拟器家属+老人见过回传句 | 仅模拟器 |
| 家属/社区勾选是否误报并写回 | [clients #67](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/67) | Playwright：工作台可领取/办结；家属账号写回过老人 GET | 真机三端仍缺 |
| 超前问卷/资料更新画像（真机填写） | [clients #66](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/66)、[elderly #20](https://github.com/Silver-yiyangyiyang/elderly-fraud-risk-system/issues/20) | 模拟器只验证入口；规划文档已进 elderly `main` | 入口存在 ≠ 真机填完并回写 |
| 家属扫码绑定门前设备 | [clients #61](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/61) | 工程入口视实现而定 | 文档或控制台截图 |
| 萤石半屏 / 门前直播按钮点开 | 上列 #71/#64 及 Home 观感 | Home 后端直播/抓拍已 L2 | 开发者工具、HLS 公网 200 单独证明 |
| 高风险提示换成真人录音 | [clients #22](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/22) | 合成 TTS 不是真人 | 本机播放合成音 |
| 微信正式提审与上线 | [clients #45](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/45) | 生产就绪门曾通过；正式审核未做 | 体验版/开发版 |

---

## 3. 订阅消息与三角色通知

| 缺什么 | 关联 Issue | 工程现状 | 不能用什么代替 |
|---|---|---|---|
| 上报通知家属；审核结果通知老人（真机订阅授权+送达） | [silver #51](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/51)、[silver #49](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/49) | 角色路由、过期关系跳过、多家属 fan-out 已合入 `main@3bdfdd5`；求助模板曾有指定真机送达 | 单元测试 14 passed |
| 门前预警落入 Silver 案件后家属审核回传 | [silver #50](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/50) | 融合与审核接口已在主线 | 合成案例号 |
| 三场景同一 `subject_id` / `case_id` 在微信老人、家属和社区 Web 回放 | [silver #52](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/52)、[silver #58](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/58) | 合成联调与赛题对照文档已进仓 | `test_issue52` |
| 老人求助推送、通知已读 | `.github` #4 复核组 | 接口已就绪 | 接口 200 |

现场不要截完整 OpenID。用仓库外的 `provision_identity.py` 把真机微信并入测试户。

---

## 4. `.github` #4 仍未勾选的无声走查

操作步骤见计划书仓 `REAL_DEVICE_WALKTHROUGH.md`。后端接口在 2026-08 已就绪，缺的是真机按钮。

| 分组 | 未勾选项 |
|---|---|
| 老人端主动提交 | 粘贴/转发短信识别；提交社区事件文字；上传图片/截图附件 |
| 复核 / 求助 / 通知 | 老人发起求助；家属/社区复核案例；下发反馈；各端查看通知并标记已读 |
| 授权与登录 | 三角色登录与角色切换的完整走查（登录主路径已在 #3 做过，本行是走查清单未收口）；家属授权社区看监控/对话；各端逐项撤回授权 |

**排除（需说话，不要塞进 #4 无声清单）**：门铃语音转写、门外对话识别对方语音、老人电话语音输入。

---

## 5. 门前设备与萤石智能体（指定设备，默认开关关闭）

| 缺什么 | 关联 Issue | 工程现状 | 不能用什么代替 |
|---|---|---|---|
| 浏览器/小程序看直播、抓拍、门外对话的观感与失败回退 | 原 Home #2 观感缺口；现随 clients 门前页 | 后端 L2 已做过 | 公网 HLS 200、抓拍 JPEG 下载 |
| 授权抓拍后可选调用云端智能体，只出派生行为观察、不改风险 | [home #30](https://github.com/Silver-yiyangyiyang/home-visit-fraud-guard/issues/30)、[shared #39](https://github.com/Silver-yiyangyiyang/fraud-guard-shared/issues/39)、[silver #69](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/69) | 客户端与旁路提醒工程已进仓；默认关闭 | 合成图片、未授权调用 |
| 干预服务真实文本接口 | [intervention #2](https://github.com/Silver-yiyangyiyang/fraud-intervention-agent/issues/2)、[#5](https://github.com/Silver-yiyangyiyang/fraud-intervention-agent/issues/5)、[silver #81](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/81) | `template-v1` 与失败关闭已在 main；真实 Token Switch HTTP **仍关** | 影子适配、本地模板 |

智能体/Token Switch 还依赖人工条款核验，见第 8 节。不要把 Agent ID 或 API Key 写进 Issue。

---

## 6. 手机系统权限与授权样本（在场真机 + 书面授权）

| 缺什么 | 关联 Issue | 说明 |
|---|---|---|
| 授权 / 拒绝 / 撤回三路径 | [mobile #18](https://github.com/Silver-yiyangyiyang/mobile-fraud-guard/issues/18)、`.github` #7 P7-C | 矩阵见 mobile `docs/PHONE_PERMISSION_MATRIX.md`；无系统权限必须保留主动提交回退 |
| 有授权的真实样本跑完模型迭代周期 | mobile #18 | 书面授权、撤回、脱敏、分层、失败案例、独立报告；`training_authorization=unverified` 不得进发布训练 |
| 真机权限撤回与微信授权撤回 | `.github` #7 | 模板已有；实名原件未收集 |

---

## 7. 不要关的 Issue（真机/设备证据仍缺）

查询日 2026-08-31 仍 OPEN，且关闭前至少要完成本表对应行：

| 仓库 | Issue |
|---|---|
| `fraud-guard-clients` | #72 #71 #67 #66 #65 #64 #63 #61 #46 #45 #22 |
| `silver-fraud-guard` | #81 #69 #58 #52 #51 #50 #49 |
| `fraud-guard-shared` | #39 |
| `home-visit-fraud-guard` | #30 |
| `elderly-fraud-risk-system` | #20（规划可继续改文档，真机填写未收集前不关） |
| `mobile-fraud-guard` | #18 |
| `fraud-intervention-agent` | #5 #2（#1/#3 为 Epic/后续，也不因模板测试而关） |
| `.github` | #4 #7 |

`silver` #67（正式模型接入）以模型/条款验收为主，不要用真机走查代替，也不要在未核验训练授权时关闭。

---

## 8. 不是真机、但同样不能关的人工项

这些**不要**记成真机已过；也**不要**在无人值守里勾完。

| 项 | Issue | 现状 |
|---|---|---|
| 萤石 Token Switch / IoT 使用条款与租户契约 | intervention #2/#5 | 清单：`fraud-intervention-agent/docs/EZVIZ_TOKEN_SWITCH_MANUAL_CHECKLIST.md`；`TERMS_VERIFIED` 仍不得改为 true |
| 微信小程序正式提审 | clients #45 | 人工操作微信公众平台 |
| 演示视频实拍、报名表盖章、平台上传回执 | [proposal #17](https://github.com/Silver-yiyangyiyang/jbgs-proposal/issues/17)、[#13](https://github.com/Silver-yiyangyiyang/jbgs-proposal/issues/13)、[#10](https://github.com/Silver-yiyangyiyang/jbgs-proposal/issues/10)、[`.github` #12](https://github.com/Silver-yiyangyiyang/.github/issues/12)、[jbgs-submission #2](https://github.com/Silver-yiyangyiyang/jbgs-submission/issues/2) | 冻结前不要追着 main 改提交包 |
| 六个核心子模块正式中文名 | [proposal #34](https://github.com/Silver-yiyangyiyang/jbgs-proposal/issues/34) | 双名已定；M1–M6 待负责人填写 |
| 书面授权原件、答辩 PPT 上幻灯 | `.github` #7 | 模板与口头口径已有；原件和幻灯未收集 |
| 正式模型接受 / 授权真实样本 | silver #67、mobile #18 | 分栏报告，不把影子写成生产 |

---

## 9. 已经可替代真机、不要再排队做的部分

| 已做 | 结论 |
|---|---|
| 各仓 `origin/main` pytest（2026-08-31）：Silver 217、Shared 156、Home 87（跳过 ASR/视觉重量级）、Community 25、Elderly 86、Mobile 46、Intervention 43 | 只证明合成工程 |
| 模拟器：同一微信补家属身份、家属首页/记录/结果/门铃、口语首页、问卷入口 | 不关 #71/#72/#66 |
| Playwright：社区登录门、居民报告、核验任务领取/办结、审核写回中文 | 不关 #67 |
| 家属测试账号写回后老人 GET 可见「家人回来说」 | 不关 #67/#63 |
| 生产包记录页拉到真实门前/短信案件 | 不关 #65/#46 |

---

## 10. 现场最短路径（有人在场时按此顺序）

1. Android + iOS 各一台，体验版，老人/家属各登一次（不要把账号写进 Git）。
2. 走 `.github` #4 未勾选的提交 / 求助 / 通知 / 撤回。
3. 真机点门前页半屏或直播；失败再 HLS/抓拍，把失败回退拍下来。
4. 同一案件：老人上报 → 家属订阅消息 → 家属写回 → 老人结果页可见。
5. 社区 Web 对同一 `case_id` 复核（可与 Playwright 对照，但仍要人眼看一遍）。
6. 条款核验完成前，不要打开 Token Switch 真实 HTTP，也不要打开 `ENABLE_EZVIZ_AGENT`。

证据命名建议：`walkthrough/YYYY-MM-DD/<组>-<项>-<步骤>-<角色>.png`，原件受控存放，仓库只登 SHA-256。
