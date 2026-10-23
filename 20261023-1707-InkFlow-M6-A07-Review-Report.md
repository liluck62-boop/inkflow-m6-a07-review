# InkFlow M6-A07 审查报告

审查日期：2026-10-23（Asia/Shanghai）  
审查范围：本目录内的 Review Package、Signing And Submission Guide、5 份 YAML 模板及 Baseline Manifest。  
审查性质：材料/控制设计审查，不是对真实 GitHub 身份、仓库、Ruleset、Architecture Book 或 Registry 当前状态的独立取证。

## 结论

建议结论：`REVISE`。

当前材料可以作为“待签署的审查包草案”，但不应据此宣布 Founder Mandate、Decision Right、Registry Custodian 或 AUTH-1～4 中任何一项已生效。目录中的模板也没有提供足够证据证明真实人员已经接受任命、具备所需能力、无未解决冲突或完成有效签名。

## 主要发现

### F-01（高）：签名提交 SHA 存在自引用/时序缺口

证据：

- `records/...Founder-One-Time-Invitation-DRAFT.yaml` 的 `ownerDecision.signedCommitSha` 和 `signedCommitUrl` 初始为 `PENDING`，但指南 B1 要求 Owner 提交后再把该 SHA/URL 写入邀请记录（指南第 81–83、106、121–129 行）。
- Role Acceptance、Competence/Conflict Disclosure、Constituting Decision 三个模板都把自身 `signedCommitSha`/`signedCommitUrl` 留在待填状态；指南 B3 要求候选人提交后记录其 commit SHA（指南第 184–192、212–230 行）。
- Registry Receipt 的 `finalReceiptCommitSha` 又规定由“本回执所在的最终 Registry commit”确定（模板第 45–50 行）。

一个 Git commit 的 SHA 由其树、父提交、作者/提交者信息和提交内容决定；把最终 SHA 写回该 commit 会改变其内容并生成新的 SHA。当前流程没有明确区分“被签署的原始提交”和“后续记录该原始提交 SHA 的元数据提交”，因此无法稳定形成可验证证据链。

修复建议：明确采用两阶段模式：

1. 签署提交只包含待签署文书，不在文书内部填写自身 commit SHA；
2. 后续由独立的证据索引/Registry 记录引用该原始 SHA、URL 和文件摘要；
3. 如果必须把 SHA 写入同名文书，则必须定义第二次签署提交，并明确第一提交是签署对象、第二提交只是索引更新；不得把第二提交误称为第一提交的原始签名。

### F-02（高）：构成性授权的来源仍是未经独立证明的 Owner 单方声明

证据：审查包第 1.1 节明确承认 Architecture Book 没有明文建立通用的 `Constituting Approver` 角色，当前路径是对留白的有限解释；Founder 模板要求 Owner 声明个人拥有/控制资产，但 `superiorRightsHolderCheck` 仍为 `PENDING_OWNER_CONFIRMATION`，且 Owner 的证据引用可以只是先前的候选记录。

这会形成核心闭环风险：候选人要审查 Owner 是否有权建立首个 Mandate，但当前包没有给候选人提供已验证的所有权/控制权证据，也没有在存在公司、共同所有人、雇主、合同方或其他上位权利主体时定义“必须先取得并验证何种授权”。单凭 Owner 的签名或 GitHub Verified 只能证明提交签名，不证明资产权利或治理授权。

修复建议：把“来源权利核验”设为硬性前置条件，并增加结构化字段：权利主体类型、覆盖资产、授权文书 URI/摘要、核验人、核验时间、例外和失效条件。若无法证明个人有权，决定必须是 `REVISE`/`DEFER`，不得进入 `APPROVE` 流程。

### F-03（高）：冻结基线中的外部事实没有随包提供可复核证据

证据：Baseline Manifest 将 Registry 分支 HEAD、Ruleset 25699958 的 Active 状态、既有回执及签名验证作为“此前独立核验结果”复用，但本目录没有对应仓库快照、API 输出、Ruleset 导出或签名验证回执；Manifest 自身也规定实际登记时必须重新核验。

因此本次审查最多能确认材料内部的声明和摘要一致，不能确认这些外部事实现在仍成立。尤其是 Registry branch、Ruleset、bypass 配置和远端 commit 状态都是会变化的外部状态。

修复建议：在实际登记前生成只读核验记录，至少包含远端分支 SHA、Ruleset 的完整关键配置、候选人/Owner 原始 commit 的 API 验证结果、读取时间和查询主体；把这些证据作为独立附件引用，而不是仅写“据报”。

### F-04（中高）：受保护分支的“签名合并”流程没有定义可验证的最终提交条件

证据：指南 B4 要求使用 GitHub 的 `Create a merge commit`，同时又要求 Registry PR 中“所有新增 commit”均 Verified，并要求最终回执 commit Verified（第 333、362–378 行）。但流程没有说明 GitHub 生成的 merge commit 如何签名、由谁签名、如何验证，以及若 Ruleset/其他保护规则拒绝该合并时如何改用本地签名合并。

GitHub 官方文档说明，要求签名的规则会检查待更新范围内的 commit 是否有有效签名，PR 合并也会检查测试合并涉及的提交；因此不能仅凭“选择 Create a merge commit”推断最终目标分支上的提交已满足签名要求。[GitHub Ruleset 文档](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets)

修复建议：明确一种经过验证的合并方式，并在流程中加入：合并前读取 PR commit 列表、合并后读取目标分支新增 commit 列表、逐个验证 `verified=true` 和签名身份；若需要本地生成 merge commit，则要求本地签名后按保护规则提交，并记录最终 SHA。

### F-05（中）：任命生效时点在不同文书中没有完全统一

证据：Role Acceptance 的 `effectiveFrom` 是候选人签署接受且 Owner 邀请已签署/送达之后；Founder 草案又写“Owner 签署并实际送达候选人后，候选人接受时生效”；审查包第 3.3 节则说来源 Mandate 和 Custodian 任命只有在候选人批准且取得 Registry receipt 后才向前生效。

这里至少存在三种“生效”概念：邀请/一次性审查任命生效、候选人的决定可作出、初始 Mandate/Custodian 生效。当前字段没有显式区分，容易让执行者把候选人 Role Assignment 的生效误读成 Mandate 已生效。

修复建议：统一定义状态机，例如 `INVITED -> ACCEPTED_FOR_REVIEW -> DECISION_SIGNED -> REGISTERED -> EFFECTIVE`，并明确只有最后一个状态才授予治理权；每个记录都使用同一套状态枚举和前置条件。

### F-06（中）：冲突、能力和身份披露虽有模板，但没有独立验证标准和失败处理记录

证据：Competence/Conflict 模板允许候选人自行填写经历、范围和冲突，Registry Receipt 只要求布尔式的 `competenceSufficientForScope`、`conflictDispositionComplete` 等核验结果。没有定义谁核验、依据什么核验、核验失败后如何重新指定候选人，也没有将“候选人是否就是 M6-A07 实现者”绑定到可验证证据。

修复建议：增加核验责任人、证据引用、核验结论、回避/替代候选人记录和复核时间。对于身份、实现者独立性和授权范围，应至少记录可复核的非敏感引用，而不是只保留自我声明。

### F-07（中）：利益冲突材料的最小化、保留和删除规则不足

模板要求披露雇佣/汇报、财务、所有权、供应商、绩效和个人利益，但指南又要求把完整记录放进专用仓库。虽然文档禁止写入私钥和敏感身份材料，但没有定义哪些冲突信息必须脱敏、谁可以访问、保存多久、决定完成后如何撤销访问或删除副本。

修复建议：将冲突披露拆成“最小必要公开摘要 + 受限证据引用”，增加访问控制、保留期限、撤销访问和删除/归档规则；不要把无关个人信息写入 Registry。

### F-08（低）：操作指南含有不可直接复用的硬编码路径和环境假设

证据：指南第 70 行使用 `D:\project\InkFlow\...` 作为源目录示例，第 257 行固定使用 `C:\if-m6a07-registry`，并假设 Owner 已有特定 SSH 公钥路径。部分命令有“路径存在则停止”的保护，这是好的，但材料未把这些路径标注为必须替换的占位符。

修复建议：统一使用明确的 `<BUNDLE_PATH>`、`<REGISTRY_TEMP_PATH>` 等占位符，并在执行前做路径、远端、分支和账户校验；不要让示例路径看起来像可直接执行的真实路径。

## 做得较好的部分

- 多处明确写出模板、聊天邀请、GitHub Verified、SHA256、PR Approve 按钮都不能单独产生治理权限。
- 明确禁止代签、伪造回执、追溯生效、覆盖历史、绕过 Ruleset、访问 Production/NewAPI/共享数据库。
- AUTH-1～4 被拆开，并要求分别绑定 Decision Right、Role Assignment、专业意见、冲突处理和 Registry 回执。
- 审查包、Manifest 和模板中的冻结包 SHA256 实际一致；本地计算得到的审查包 SHA256 为 `ECF6356090B99F41C18A0045BE7838E67F869FAFCE2D8A7542CF411F5EDFF6CD`，Manifest SHA256 为 `FF433A1E3662D937A431CB1C66FAC7CD39AB614F2500B21BDEA3D228E7C5DAAB`。

## 放行条件

在以下条件全部满足前，不建议签署 `APPROVE` 或标记 `EFFECTIVE`：

1. 修复 F-01 的两阶段签名/索引模型，并给出一条可重放的端到端示例。
2. 提供并核验 Owner 来源权利及所有上位权利主体授权；没有证据则只能 `REVISE`/`DEFER`。
3. 重新核验远端 Registry branch、Ruleset、bypass 配置和所有相关 commit 的签名状态，并保存只读证据。
4. 统一任命、决定、登记和生效状态机，避免 `ACCEPTED` 与 `EFFECTIVE` 混用。
5. 明确 Registry 合并提交和最终回执的签名方案，并在目标分支读回后逐个验证。
6. 补充身份/能力/冲突核验责任、隐私最小化、访问撤销和保留规则。

## 审查限制

本目录没有实际源代码、ProductBook 原文、Git 仓库历史、远端 Ruleset 导出或真实签名提交，因此本报告没有对 AUTH-1～4 的实现正确性、数据库 DDL、Windows DPAPI 行为或 PostgreSQL 运行结果作出结论。那些内容只能在对应工程工件和独立审查证据到位后再审。
