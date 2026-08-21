# 耄耋反诈智盾统一项目计划

版本：V1.0

状态基线：2026-08-22

计划维护：组织 `.github` 与 `jbgs-proposal` 同步维护；具体实现状态以各仓库 Issue、PR 和 `main` 为准。

## 一、不可变范围

1. `elderly-fraud-risk-system` 是超前预警系统；三个场景仓和 `silver-fraud-guard` 是当前事件采集、即时融合与干预系统。
2. 高风险即时告警必须有当前事件证据；画像只能调整提示表达、干预强度和联络顺序。
3. Home 与 Community 都可以消费住户逐项授权、可撤回、未过期的门前设备事件。Community 没有、也不拥有社区公共区域设备，不进行环境持续监控。
4. Community 不接收原始门前音视频，只消费完成业务核实所需的最小化派生事件或识别结果；单一设备事件不能直接证明诈骗。
5. 未核验训练授权的数据保持 `training_authorization=unverified`，不得进入发布训练；线上请求不得直接触发训练。
6. 合成工程、模拟参与者、历史调查、受控真人和真实部署证据分栏报告。模拟参与者不能写成受控真人，任何本地验证不能写成生产验收。

## 二、2026-08-21 可追溯基线

| 仓库 | `main` 基线 | 当前已证明状态 |
|---|---|---|
| `.github` | `ea5bd8f` | 已有组织架构入口；本计划补充统一任务与证据门禁 |
| `jbgs-proposal` | `a87193d` | V3.2 计划书和 32 页评审 PDF 可生成；最终提交包未完成 |
| `elderly-fraud-risk-system` | `0143efa` | G1-G6 工程机制、画像 v2 与覆盖层消费已进入主线；58 项回归通过 |
| `mobile-fraud-guard` | `ef1094c` | 纯后端、质量门、实验候选、规则兜底和影子模式已进入主线；27 项干净环境回归通过 |
| `community-fraud-guard` | `5aedab4` | 住户授权门前设备消费边界与融合提交已合并；shared 依赖钉到当前提交 |
| `home-visit-fraud-guard` | `cdc3486` | 授权门前证据、Silver 提交、alarmType 落库已进入主线；实体设备回调已真实走通 H2-H5 |
| `fraud-guard-shared` | `418e6ec` | Home/Community 共用门前采集、ASR、场景适配与 Ruff 基线进入主线 |
| `silver-fraud-guard` | `b40d4dc` | 多事件聚合、附件受控入口、生产 API 安全基线进入主线；62 项回归通过 |
| `fraud-guard-clients` | `5799cc8` | Web 社区端与小程序老人端合成 MVP；前端三端重构交给前端负责人 |
| `mobile-fraud-guard` | `d0e7d08` | 纯后端、授权门禁、泄漏审计、影子模式和评估报告（含 CI/失败样本）进入主线 |

## 三、执行队列与依赖

2026-08-22 进展：Community #7/#8 已合并、Silver #11/#17 已 Ranked 关闭、Silver #16 部署与合成 smoke 已完成、Mobile #9 无人值守部分已完成、Home #2 实体设备 H2-H5 已真实走通、mobile/community 的 shared 依赖钉点已回修、Clients #4 已合并。前端三端重构（老人端/家属端/社区端，同小程序按登录身份分老人/家属界面，社区为 Web）已登记为 fraud-guard-clients #8-#11，交由前端负责人实现。

2026-08-22 后端功能进展：Silver 新增登录身份（auth/login+me）、通知契约（notifications）、门外对话（door-talk，family/community，社区需家属授权 scope=community_door_access）；Home 新增看监控（camera snapshot/live，社区同样需家属授权）；fraud-guard-clients 共享 API 客户端已接 login/notifications/door-talk/camera 方法，并整理 FRONTEND_API.md 接口清单。前端三端 UI、真实 ERTC/HLS 媒体传输、微信登录与订阅消息接入仍待前端负责人与真机联调。

| 顺序 | Lifecycle | Priority | 任务与责任仓库 | 进入下一状态的条件 |
|---|---|---|---|---|
| 1 | Pending | P0 | [Community #8](https://github.com/Silver-yiyangyiyang/community-fraud-guard/issues/8)：修正 PR #7 的门前设备消费边界和提交门禁 | 文档/API/测试一致，全仓检查与跨仓合成 HTTP 通过，PR #7 可评审 |
| 2 | Qualified | P0 | [Silver #11](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/11)：完成三场景多事件融合收口 | Community 配套进入 `main`，Home+Community 同一显式 `case_reference` 本地回归通过后 Ranked |
| 3 | Pending/Blocked | P0 | [Silver #16](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/16)：服务器部署与远端合成验收 | Community #8/#7 完成且恢复安全 SSH 登录；记录版本、健康、契约和回滚点 |
| 4 | Pending/Blocked | P1 | [Home #2](https://github.com/Silver-yiyangyiyang/home-visit-fraud-guard/issues/2)：实体门前设备端到端验收 | 恢复服务器/设备访问；使用住户自管门前设备和去敏报告完成回调验收 |
| 5 | Pending | P1 | [Mobile #9](https://github.com/Silver-yiyangyiyang/mobile-fraud-guard/issues/9)：训练授权与独立验证门禁 | 授权登记、不可变 manifest、泄漏审计与独立评估报告通过 |
| 6 | Pending/Requires Human | P1 | [Mobile #10](https://github.com/Silver-yiyangyiyang/mobile-fraud-guard/issues/10)：手机权限与真机安全回退 | 授权/拒绝/撤回三路径真机通过；日志去敏；无权限回退可用 |
| 7 | Pending | P1 | [Silver #17](https://github.com/Silver-yiyangyiyang/silver-fraud-guard/issues/17)：生产 API 安全与数据治理 | 鉴权、越权、速率、重放、撤回/删除、Secret 与部署安全检查通过 |
| 8 | Pending/Requires Human | P1 | [Clients #3](https://github.com/Silver-yiyangyiyang/fraud-guard-clients/issues/3)：微信真机与生产域名 | 真机、合法域名、授权撤回和真实后端连接通过 |
| 9 | Pending/Frontend | P2 | [Mobile #11](https://github.com/Silver-yiyangyiyang/mobile-fraud-guard/issues/11)：交接旧前端 PR #1 | 与 Clients 去重，不携带被 PR #8 替代的后端，PR #1 收口 |
| 10 | WIP | P1 | [Proposal #10](https://github.com/Silver-yiyangyiyang/jbgs-proposal/issues/10)：收口 D1-D6 与最终提交包 | 同版本源码、计划书、报告、清单和自动去敏构建全部通过 |
| 11 | Pending/Requires Human | P1 | [Proposal #13](https://github.com/Silver-yiyangyiyang/jbgs-proposal/issues/13)：答辩材料与平台上传 | PPT、演示脚本、最终复核和赛事平台上传由在场人员完成 |

## 四、阶段计划

### 阶段 A：主线收口（立即）

- Community 负责人完成 #8 并更新 PR #7；不删除门前设备消费能力，也不引入公共区域设备。
- PR #7 合并后复验 Silver #11，满足本地多场景验收即关闭 #11；生产结论继续留给 #16。
- Mobile 前端负责人依据 #11 处理旧 PR #1；后端保持 `backend_only`。

### 阶段 B：真实接入与生产安全（随后）

- 恢复安全 SSH/设备访问，完成 Silver #16 与 Home #2；不得部署未合并分支。
- 并行推进 Mobile #9、#10，训练授权与系统权限任一未通过时保持规则/主动提交回退。
- 在公开部署前完成 Silver #17，再完成 Clients #3 的生产域名与微信真机验收。

### 阶段 C：证据升级与提交锁版

- 模拟参与者只用于可复现机制验证；若后续开展真人测试，必须另行知情同意、即时揭示、无真实转账并单独报告。
- Proposal #10 固定同一提交版本并生成去敏包；Proposal #13 由在场人员完成答辩与平台操作。
- 最终材料逐项引用 commit、PR、测试报告和证据等级，不用“原型存在”代替端到端验收。

## 五、验收门禁

| Gate | 证据 | 允许的完成声明 |
|---|---|---|
| G0 契约与静态检查 | schema、Ruff/构建、secret scan、`git diff --check` | 代码结构可评审 |
| G1 合成无人值守 | 单元/集成测试、真实本地 HTTP、固定合成样本 | 合成工程链路通过 |
| G2 模拟参与者 | 固定种子、分层、区间、失败判据 | 模拟机制结果，不是真人效果 |
| G3 设备/平台 | 住户授权门前设备、手机/微信真机、权限撤回 | 指定设备与平台能力通过 |
| G4 生产部署 | 合并提交、服务健康、远端契约、回滚、去敏报告 | 指定版本生产工程验收通过 |
| G5 最终提交 | 清单、PDF/PPT、演示脚本、平台回执 | 赛事材料提交完成 |

任何任务只有在“实现 + 自动验证 + 边界说明 + 可追溯交付”同时存在时，才能从 WIP 进入 Qualified；只有合并且验收条件满足后才能进入 Ranked 并关闭 Issue。

## 六、计划更新规则

- 架构、优先级或跨仓依赖变化时，同时更新本文件和 `jbgs-proposal/docs/PROJECT_PLAN.md`。
- 正式叙述变化时同步更新 `jbgs-proposal/README.md`、`plan.tex` 和重新编译的 `plan.pdf`。
- 功能细节只在责任仓库维护；总体计划只引用 Issue、PR、commit 和证据等级。
- 未开始工作必须先进入对应仓库 Issue；暂停工作必须留下 Checkpoint，不能只保存在聊天中。
