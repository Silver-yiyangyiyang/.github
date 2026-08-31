# 人工处理材料总表（去敏模板）

跟踪：[`.github` #12](https://github.com/Silver-yiyangyiyang/.github/issues/12)  
关联：隐私收口 [#7](https://github.com/Silver-yiyangyiyang/.github/issues/7)、真机总表 [`REAL_DEVICE_PENDING.md`](REAL_DEVICE_PENDING.md)、计划书 [`SUBMISSION_CHECKLIST.md`](https://github.com/Silver-yiyangyiyang/jbgs-proposal/blob/main/docs/SUBMISSION_CHECKLIST.md)

> 状态基线：**2026-08-31**。项目**尚未宣布冻结**。本表只建去敏索引，**全部为未签署 / 未上传**。  
> 不把口头确认写成已签字。不写入实名、电话、住址、账号、回执原件、密钥或完整设备标识。原件只放受控存储，仓库只登 SHA-256。

## 冻结 SHA（宣布冻结后填写）

| 仓库 | 冻结 `origin/main` | 填写人 | 日期 |
|---|---|---|---|
| `.github` | 待冻结 | | |
| `jbgs-proposal` | 待冻结 | | |
| `jbgs-submission` | 待冻结 | | |
| `elderly-fraud-risk-system` | 待冻结 | | |
| `mobile-fraud-guard` | 待冻结 | | |
| `community-fraud-guard` | 待冻结 | | |
| `home-visit-fraud-guard` | 待冻结 | | |
| `fraud-guard-shared` | 待冻结 | | |
| `silver-fraud-guard` | 待冻结 | | |
| `fraud-guard-clients` | 待冻结 | | |
| `fraud-intervention-agent` | 待冻结 | | |

## 材料台账

状态取值：`未冻结` / `待签` / `已签受控` / `已上传` / `豁免` / `不适用`。

| 编号 | 材料 | 签名或盖章 | 状态 | 原件位置（角色，不写住址） | 去敏副本 SHA-256 | 对应 Issue | 平台回执 |
|---|---|---|---|---|---|---|---|
| H1 | 报名表、成员与指导教师确认 | 需要 | 未冻结 | | | proposal #17 / #13 | |
| H2 | 原创性 / 知识产权 / 无争议声明 | 需要 | 未冻结 | | | proposal #10 | |
| H3 | 最终计划书签字页 | 需要 | 未冻结 | | | proposal #10 | |
| H4 | 答辩稿、演示视频、源码包一致性复核 | 复核签字 | 未冻结 | | | proposal #13 | |
| H5 | 老人/家属/社区书面知情同意与影像授权 | 需要 | 未冻结 | | | .github #7；模板 `ELDER_WRITTEN_CONSENT_TEMPLATE.md` | |
| H6 | 授权拒绝、撤回、删除路径执行记录 | 需要 | 未冻结 | | | .github #7 P7-B/C | |
| H7 | 真机/门前设备/测试账号使用范围确认 | 责任人确认 | 未冻结 | | | .github #4；`REAL_DEVICE_PENDING.md` | |
| H8 | 演示视频逐帧隐私复核 | 复核签字 | 未冻结 | | | proposal #17 材料 2 | |
| H9 | CHARLS/CHFS 与其他受限数据使用范围 | 负责人确认 | 未冻结 | | | elderly 数据登记 | |
| H10 | ASR/模型许可证与禁止再分发范围 | 负责人确认 | 未冻结 | | | shared 许可审核 | |
| H11 | 真实授权训练样本（如纳入）逐项核验 | 需要 | 未冻结 | | | mobile #18 | |
| H12 | 第三方字体/图片/SDK/商标清单 | 许可依据 | 未冻结 | | | 提交包 | |
| H13 | 最终 PDF/PPT/ZIP 去敏抽查 | 两人交叉复核 | 未冻结 | | | jbgs-submission #2 | |
| H14 | 赛事平台上传与复下载核对 | 上传人 + 另一复核人 | 未冻结 | | | .github #12；proposal #13 | |

## 本轮明确不填写

- 签署人真实姓名、证件号、手机号、学校公章扫描件。
- 平台回执编号的完整原件；冻结后只登哈希。
- 任何 `sk-`、AppSecret、accessToken、OpenID、完整序列号。

冻结宣布后按 jbgs-submission #2 的顺序钉 SHA → 重跑测试 → 改字 → 本表逐项改状态。宣布前不要把本表任何一行改成「已签」或「已上传」。
