# 人工处理材料总表（去敏模板）

跟踪：[`.github` #12](https://github.com/Silver-yiyangyiyang/.github/issues/12)  
关联：隐私收口 [#7](https://github.com/Silver-yiyangyiyang/.github/issues/7)、真机总表 [`REAL_DEVICE_PENDING.md`](REAL_DEVICE_PENDING.md)、计划书 [`SUBMISSION_CHECKLIST.md`](https://github.com/Silver-yiyangyiyang/jbgs-proposal/blob/main/docs/SUBMISSION_CHECKLIST.md)

> 状态基线：**2026-09-03**。已宣布**竞赛功能开发完成冻结**，进入拍摄演示视频与人工提交收口。本表只建去敏索引；签字/盖章/上传仍为**待签 / 待上传**，不得把口头确认写成已签字。  
> 不写入实名、电话、住址、账号、回执原件、密钥或完整设备标识。原件只放受控存储，仓库只登 SHA-256。

## 冻结 SHA（功能冻结快照；录成片/上传前再钉最终提交）

| 仓库 | 冻结 `origin/main`（短 SHA） | 填写人 | 日期 |
|---|---|---|---|
| `.github` | `d4796f9`→本轮 V2.0 计划更新后另钉 | agent | 2026-09-03 |
| `jbgs-proposal` | `46dbba8`→本轮 V3.5 后另钉 | agent | 2026-09-03 |
| `jbgs-submission` | `5191a73` | agent | 2026-09-03 |
| `elderly-fraud-risk-system` | `ae752c0` | agent | 2026-09-03 |
| `mobile-fraud-guard` | `8222db1` | agent | 2026-09-03 |
| `community-fraud-guard` | `bbb27aa` | agent | 2026-09-03 |
| `home-visit-fraud-guard` | `10a500c` | agent | 2026-09-03 |
| `fraud-guard-shared` | `d7d3ab7` | agent | 2026-09-03 |
| `silver-fraud-guard` | `377931c` | agent | 2026-09-03 |
| `fraud-guard-clients` | `8006cda` | agent | 2026-09-03 |
| `fraud-intervention-agent` | （开放 #3 方案 C；非本阶段主线） | agent | 2026-09-03 |
| `fraud-guard-showcase` | `e9f4a47` | agent | 2026-09-03 |

## 材料台账

状态取值：`未冻结` / `待签` / `已签受控` / `已上传` / `豁免` / `不适用`。

| 编号 | 材料 | 签名或盖章 | 状态 | 原件位置（角色，不写住址） | 去敏副本 SHA-256 | 对应 Issue | 平台回执 |
|---|---|---|---|---|---|---|---|
| H1 | 报名表、成员与指导教师确认 | 需要 | 待签 | | | proposal #17 / #13 | |
| H2 | 原创性 / 知识产权 / 无争议声明 | 需要 | 待签 | | | proposal #10 | |
| H3 | 最终计划书签字页 | 需要 | 待签 | | | proposal #10 | |
| H4 | 答辩稿、演示视频、源码包一致性复核 | 复核签字 | 待签 | | | proposal #13 | |
| H5 | 老人/家属/社区书面知情同意与影像授权 | 需要 | 待签 | | | .github #7；模板 `ELDER_WRITTEN_CONSENT_TEMPLATE.md` | |
| H6 | 授权拒绝、撤回、删除路径执行记录 | 需要 | 待签 | | | .github #7 P7-B/C | |
| H7 | 真机/门前设备/测试账号使用范围确认 | 责任人确认 | 待签 | | | .github #4；`REAL_DEVICE_PENDING.md` | |
| H8 | 演示视频逐帧隐私复核 | 复核签字 | 待签 | | | proposal #17 材料 2；**当前主任务：成片** | |
| H9 | CHARLS/CHFS 与其他受限数据使用范围 | 负责人确认 | 待签 | | | elderly 数据登记 | |
| H10 | ASR/模型许可证与禁止再分发范围 | 负责人确认 | 待签 | | | shared 许可审核 | |
| H11 | 真实授权训练样本（如纳入）逐项核验 | 需要 | 待签 | | | mobile #18 | |
| H12 | 第三方字体/图片/SDK/商标清单 | 许可依据 | 待签 | | | 提交包 | |
| H13 | 最终 PDF/PPT/ZIP 去敏抽查 | 两人交叉复核 | 待签 | | | jbgs-submission #2 | |
| H14 | 赛事平台上传与复下载核对 | 上传人 + 另一复核人 | 待签 | | | .github #12；proposal #13 | |

## 本轮明确不填写

- 签署人真实姓名、证件号、手机号、学校公章扫描件。
- 平台回执编号的完整原件；冻结后只登哈希。
- 任何 `sk-`、AppSecret、accessToken、OpenID、完整序列号。

功能已冻结。下一步：按 jbgs-submission 演示视频脚本拍成片 → 钉最终 SHA → 重跑去敏打包 → 本表逐项改「已签受控 / 已上传」。未取得平台回执前不得宣称赛事提交完成。
