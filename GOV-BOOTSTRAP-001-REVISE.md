# GOV-BOOTSTRAP-001 审查决定：REVISE

## 决定

- decision_id: `GOV-BOOTSTRAP-001-DECISION-v1`
- decision: `REVISE`
- reviewed_package: `INKFLOW-M6-A07-APPROVER-PACKAGE-001`, version `0.1`
- scope: 仅审查初始 Mandate、Registry 记录型 Decision Right 和首个 Registry Custodian 任命
- status: `NOT_EFFECTIVE`

本意见表示当前材料需要修订后重新审查。它不是候选人的正式签名决定，不构成 Mandate、Decision Right、Custodian 任命或 AUTH-1～AUTH-4 的生效记录，也不替代真实人员的身份、能力和利益冲突披露。

## 理由与发现

### F-01（高）：签名提交 SHA 存在自引用/时序缺口

Owner、候选人和 Registry Receipt 模板都要求记录自身或后续提交的 SHA，但现行流程没有区分“原始签署提交”和“记录该提交 SHA 的后续索引提交”。将 SHA 写回同一提交会改变提交内容并生成新的 SHA，导致证据链无法稳定验证。

### F-02（高）：构成性授权来源缺少独立权利证明

当前路径依赖 Owner 关于个人拥有或控制项目资产的声明，但上位权利主体检查仍为待填状态。材料没有提供足够证据证明 Owner 有权建立首个 Mandate，也没有为公司、共同所有人、合同方或其他上位权利主体定义完整的授权核验流程。

### F-03（高）：冻结基线中的远端事实无法由当前材料复核

Registry 分支 HEAD、Ruleset Active 状态、bypass 配置、既有回执和远端签名验证均属于外部事实。本目录只保留了摘要和先前核验的文字描述，没有对应的可复核 API 输出、仓库快照或 Ruleset 导出。

### F-04（中高）：受保护分支的签名合并流程不完整

指南要求使用 `Create a merge commit`，同时要求新增提交和最终回执提交均为 Verified，但没有定义合并提交如何签名、由谁签名，以及合并后如何逐个读取并核验目标分支上的提交。

### F-05（中）：任命接受、生效和登记的状态边界不统一

不同文书对 `effectiveFrom` 的定义不同，容易把候选人接受一次性审查任命误读成初始 Mandate 或 Custodian 任命已经生效。应统一状态机并明确只有 Registry receipt 进入受保护目标分支后，治理权才可标记为 `EFFECTIVE`。

### F-06（中）：能力、身份和冲突披露缺少独立核验标准

模板要求候选人自我披露，但没有明确核验责任人、核验依据、实现者独立性证据、失败处理或重新指定候选人的记录方式。

### F-07（中）：冲突材料的隐私和保留规则不足

材料要求披露雇佣、汇报、财务、所有权和个人利益关系，但没有定义最小化披露、访问范围、保存期限、撤销访问和删除/归档流程。

### F-08（低）：操作指南包含硬编码路径和环境假设

指南中存在 `D:\project\InkFlow\...`、`C:\if-m6a07-registry` 和特定 SSH 密钥路径等环境假设，未全部明确标记为必须替换的占位符。

## 修订条件

重新提交 `APPROVE` 前，至少完成以下事项：

1. 采用两阶段签名/索引模型，明确原始签署提交、证据索引提交和最终 Receipt 提交的关系。
2. 提供并核验 Owner 的资产权利及所有上位权利主体授权；无法证明时保持 `DEFER` 或 `REVISE`。
3. 在实际登记前重新核验远端 Registry 分支、Ruleset、bypass 配置和相关 commit 的签名状态，并保存只读证据。
4. 统一 `INVITED -> ACCEPTED_FOR_REVIEW -> DECISION_SIGNED -> REGISTERED -> EFFECTIVE` 等状态及其前置条件。
5. 明确 Registry 合并提交和最终 Receipt 的签名方案，并在目标分支读回后逐项验证。
6. 补充身份/能力/冲突核验责任、隐私最小化、访问撤销和保留规则。
7. 将环境路径改为显式占位符，并在执行前校验路径、远端、分支和账户。

## 剩余风险

- 当前不能确认 Owner 对全部声明资产拥有足够的治理授权。
- 当前不能确认候选人与 M6-A07 实现者完全独立，或不存在未披露的重大利益冲突。
- 当前不能确认远端 Registry 和 Ruleset 状态仍与冻结 Manifest 一致。
- 在上述问题完成前，`FOUNDER-GOV-001`、`DR-REGISTRY-RECORD-001`、`INKFLOW-REGISTRY-CUSTODIAN-001` 以及 AUTH-1～AUTH-4 均保持 `NOT_EFFECTIVE`。

## 签署状态

- candidate_identity_ref: `PENDING_CANDIDATE`
- signed_at: `PENDING_CANDIDATE`
- signing_key_fingerprint: `PENDING_CANDIDATE`
- signed_commit_sha: `PENDING_CANDIDATE`
- registry_receipt_uri: `PENDING_REGISTRY_RECEIPT`
