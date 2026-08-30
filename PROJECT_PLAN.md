# 耄耋反诈智盾统一项目计划

版本：V1.1

状态基线：2026-08-28

维护规则：组织 `.github` 与 `jbgs-proposal` 同步维护；实现状态以各仓库 `main`、开放 Issue、关联 PR 和可复核证据为准。成熟度区间是管理判断，不是赛事评分或精确完成率。

## 一、参赛主线与不可变边界

参赛叙事固定为：

> 超前脆弱性评估 → 电话/短信或授权门前当前事件 → Silver 同案融合 → 老人/家属/社区分级干预 → 人工审核结果受控回写。

1. `elderly-fraud-risk-system` 负责超前预警；Mobile、Home、Community 提交当前事件；`silver-fraud-guard` 负责统一融合、响应与审计。
2. 高风险即时告警必须有当前事件证据。画像只能调整提示表达、干预强度和联络顺序，不能单独证明诈骗正在发生。
3. Community 没有、也不拥有社区公共区域设备，不进行环境持续监控；仅消费住户逐项授权、可撤回、未过期的门前最小化派生事件，不接收原始门前音视频。
4. 未核验训练授权的数据保持 `training_authorization=unverified`，不得进入发布训练；线上请求不得直接触发训练。
5. 合成工程、历史调查、研究影子、实体设备、受控真人和真实部署证据必须分栏。自动测试不能替代老人可用性、自然场景效果或生产验收。
6. 方言与粤语 ASR 只作为转写鲁棒性和公平性研究支撑，不是独立诈骗声学模型或画像特征；当前不得声明广州音、港音生产效果。

## 二、2026-08-28 可追溯快照

| 仓库 | `main` 基线 | 当前已证明状态 | 仍缺少 |
|---|---:|---|---|
| `.github` | `6cb5c13` | 组织入口、任务池和证据门禁已建立 | 本次计划更新合并后才成为新基线 |
| `jbgs-proposal` | `35d0126` | V3.3 计划书、PDF、隐私清单和提交资料框架存在 | V3.4 同步、演示视频、报名表、答辩与平台回执 |
| `elderly-fraud-risk-system` | `fec59f6` | 画像、问卷入口、subject 绑定与提示覆盖层已进入主线 | 生产变量、真实绑定、真机填写、授权真实样本和即时结果回写证据 |
| `mobile-fraud-guard` | `8222db1` | 电诈后端、授权门禁、候选评估、影子模式与回流治理较成熟 | Issue #18 的授权真实样本完整周期、手机权限/真机和正式模型接受 |
| `community-fraud-guard` | `fc69013` | 登记核实、处置回填与授权门前派生事件消费已形成 | 真实社区流程、自然场景误报/漏报和同案三端复核 |
| `home-visit-fraud-guard` | `6c130b3` | 门前设备、抓拍、派生事件、camera/door-talk 路径有工程证据 | Issue #2 浏览器/小程序观感验收、#27 正式绑定、#28 停留/路人逻辑 |
| `fraud-guard-shared` | `15a20c6` | 通用模型服务、场景适配与基础 ASR 已在主线 | Issue #33 / PR #34 尚未合并；方言/粤语仅研究影子，真实音频授权仍缺 |
| `silver-fraud-guard` | `1767fdd` | 统一事件、同案融合、角色通知、授权和学习回流接口已形成 | Issue #52 微信三端同案回放、#53/#55 正式绑定与失败回退验收 |
| `fraud-guard-clients` | `6960d7b` | 三角色 MVP、共享 API、登录绑定与新 UI 工作存在 | Issue #71 新布局功能尚未完全接线；微信真机、提审和正式发布需人工 |

注：以上 SHA 为 2026-08-28 查询到的 `main` 快照；开放 PR 的能力不计入 `main` 已完成项。

`main` 在 2026-08-29 追加了一段无人值守跨仓进展。其中把 Clients #72/#80 写成已合并，这与当前开放 PR 不符：[Clients #71](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/71) 仍由 [PR #74](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/pull/74) 推进，[#80](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/80) 仍由 [PR #94](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/pull/94) 推进。不要把开放 PR 计入上表已完成项。

## 三、完成度与赛题契合度

| 工作面 | 判断区间 | 结论 | 当前最重要缺口 |
|---|---:|---|---|
| 赛题与架构定位 | 85%–95% | 诈骗方向、双系统、三场景、同案融合与治理边界清晰 | 减少仓库清单式叙述，突出老年用户、当前证据与分级干预 |
| 核心后端与合成工程 | 80%–90% | 多仓核心接口和自动回归较成熟 | 统一一个 `subject_id` / `case_id` 的正式演示链 |
| 模型与 ASR 研究 | 65%–75% | 有冻结评估、失败候选和研究影子结果 | 真实授权样本、正式接受、许可证生产边界与命名口音证据 |
| 设备与多模态集成 | 55%–70% | 门前设备和派生事件已有实质证据 | 正式绑定、异常停留门槛、微信三端回放和完整观感 |
| 正式前端与发布 | 55%–70% | 视觉重构和基础能力存在 | 新 UI 功能接线、真机与提审 |
| 赛事材料与答辩 | 60%–75% | 计划书、离线材料和去敏构建已有基础 | 演示成片、报名表、答辩、平台上传与回执 |
| 真实场景验证 | 20%–35% | 目前主要是合成、历史、设备和研究影子证据 | 书面授权真人、自然场景、撤回记录与真实部署效果 |

结论：项目没有在赛题方向上跑偏，当前主要风险是叙事偏航和证据越级。不得把工程回归写成降低真实受骗率，也不得把设备、ASR、账号绑定等支撑能力平铺成多个彼此竞争的主创新。

## 四、ASR 研究结论与边界

- AISHELL-3 普通话研究候选在平衡方言开发集 800 条上，整体规范化 CER 为 `0.091236`，最差方言层为 `0.091758`；数据和候选均保持研究用途、`production_eligible=false`。
- Common Voice 粤语开发集 800 条上，SenseVoiceSmall 规范化 CER 为 `0.066364`；CPU RTF `0.063281`，与 CUDA 输出指标一致，具备研究影子可用性。
- Whisper 粤语中型微调出现重复输出并被质量门拒绝；失败结果保留，不能选择性省略。
- SenseVoice 许可审核只批准本项目本地竞赛演示/研究范围，不授权商业生产、私有化交付或权重再分发。
- 广州与香港命名口音样本和说话人数均不足，元数据尚未人工策展，`ready_for_named_accent_claims=false`。

## 五、当前执行队列

| 顺序 | Lifecycle | Priority | 任务 | 进入下一状态的条件 |
|---|---|---|---|---|
| 1 | WIP | P0 | [.github #9](https://github.com/Silver-yiyangyiyang/.github/issues/9)：同步完成度、赛题主线和计划书 | 两仓文档/PDF更新、检查通过并提交 PR 后进入 Qualified |
| 2 | WIP / User-owned | P0 | [Clients #71](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/71)：新 UI 功能接线 | 老人/家属/社区关键入口使用真实共享 API；加载、空态、失败回退和身份边界可验收 |
| 3 | Pending | P0 | [Silver #52](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/52)：三场景同案三端回放 | 一个显式 `subject_id`、一个 `case_id` 在微信老人/家属及社区 Web 可复核 |
| 4 | Pending | P0 | [Mobile #18](https://github.com/Silver-yiyangyiyang/mobile-fraud-guard/issues/18) / [Shared #36](https://github.com/Silver-yiyangyiyang/fraud-guard-shared/issues/36)：授权真实样本与受控真人最小验证 | 书面授权、撤回、脱敏、分层、失败案例和独立报告齐备 |
| 5 | Qualified / Awaiting review | P1 | [Shared #33](https://github.com/Silver-yiyangyiyang/fraud-guard-shared/issues/33) / [PR #34](https://github.com/Silver-yiyangyiyang/fraud-guard-shared/pull/34)：方言/粤语 ASR 研究门禁 | 人工确认研究价值、许可证边界和非生产表述后决定是否合并 |
| 6 | Pending / Requires human | P1 | [Home #2](https://github.com/Silver-yiyangyiyang/home-visit-fraud-guard/issues/2)、#27、#28：门前正式验收 | 正式绑定、路人/停留门槛、浏览器/小程序观感及失败回退通过 |
| 7 | WIP / Requires human | P1 | [Proposal #10](https://github.com/Silver-yiyangyiyang/jbgs-proposal/issues/10)、#13、#17：锁版与提交 | 同版本 PDF/PPT/源码/报告/清单、演示、报名、平台回执齐备 |

## 六、阶段计划

### 阶段 A：文档与功能收口（立即）

- 完成 `.github #9`，把本文件、计划书 README、正文、PDF 和清单统一到 2026-08-28。
- 随后由用户推进 Clients #71：先接真实功能，再做真机观感；截图或静态页面不等于功能闭环。
- 固定一条演示主线，不再新增独立场景或新模型家族。

### 阶段 B：端到端与真实证据

- 完成 Silver #52 的同一案件三端回放，并把来源、授权、失败回退和证据等级展示在界面中。
- 选择最小、可撤回的授权真实样本/受控真人方案；不进行真实转账，不保存不必要的原始媒体。
- 完成 Home 正式绑定、停留逻辑和微信/浏览器验收。

### 阶段 C：提交锁版

- 对 Shared PR #34 作人工接受或保留决定；无论结果如何，ASR 均保持研究影子表述。
- 固定同一组 commit、PDF、测试报告和去敏源码包；重新生成校验清单。
- 由在场负责人完成报名表、演示视频、答辩、平台上传和回执留存。

## 七、验收门禁

| Gate | 证据 | 允许的完成声明 |
|---|---|---|
| G0 契约与静态检查 | schema、Ruff/构建、secret scan、`git diff --check` | 代码或文档结构可评审 |
| G1 合成工程 | 单元/集成测试、真实本地 HTTP、固定合成样本 | 合成工程链路通过 |
| G2 历史/研究影子 | 冻结切分、分层指标、失败候选、授权/许可边界 | 指定数据和候选的研究结果 |
| G3 设备/受控真人 | 书面授权、设备/真机、撤回、脱敏、失败案例 | 指定设备或受控场景通过 |
| G4 真实部署 | 合并提交、服务健康、远端契约、回滚、自然场景记录 | 指定版本工程部署通过，不自动等于效果显著 |
| G5 最终提交 | PDF/PPT、演示、清单、报名表、平台回执 | 赛事材料提交完成 |

只有“实现 + 自动验证 + 边界说明 + 可追溯交付”同时存在时，任务才可由 WIP 进入 Qualified；只有正式接受、合并且验收条件满足后才能进入 Ranked 并关闭 Issue。

## 八、计划更新规则

- 架构、优先级或跨仓依赖变化时，同时更新本文件和 `jbgs-proposal/docs/PROJECT_PLAN.md`。
- 正式叙述变化时同步更新 `jbgs-proposal/README.md`、`plan.tex` 和重新编译的 `plan.pdf`。
- 功能细节只在责任仓库维护；总体计划只引用 Issue、PR、commit 和证据等级。
- 暂停工作必须在对应 Issue 留下 Checkpoint；聊天不是项目状态的唯一存储。
