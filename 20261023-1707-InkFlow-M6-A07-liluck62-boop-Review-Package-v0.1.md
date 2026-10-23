# InkFlow M6-A07 构成性审批人与 AUTH 审查包

**审批包 ID：** INKFLOW-M6-A07-APPROVER-PACKAGE-001  
**版本：** 0.1  
**编制时间：** 2026-10-23 13:57（Asia/Shanghai）  
**状态：** REVIEW_PACKAGE_READY / NO_NEW_AUTHORITY_EFFECTIVE  
**范围：** 为项目治理建立首个授权范围（Mandate），随后为 Windows Desktop / Identity-only / TEST_ONLY 准备 AUTH-1 至 AUTH-4。  
**文件性质：** 本地审查材料，不是已签署任命、Source Mandate、生效 Decision Right、AUTH 批准、Registry 回执、独立意见或 Gate 决定。

本包供项目所有者（Project Owner）邀请真实人员审阅和签署。没有猜填审查人身份、资格、授权范围（Mandate）、签名、批准结论或生效时间。本包不修改受保护的 Registry 分支及其中既有记录。

## 1. 决策与权限判断

### 1.1 架构手册（Architecture Book）的规定

核对的 Book 条款规定了作出治理决定所需的控制，但没有规定某张证书、某个固定职业，或一种普遍适用的“构成性审批人”资格：

| 来源 | 与本事项有关的规则 |
|---|---|
| 1810 §§12–16 | 正式 Governance Body 必须有明确边界的 Mandate 和 Charter。Chartered 表示 Mandate 已获批准；Active 还要求成员、法定人数、Decision Catalog 和记录能力到位。 |
| 1810 §19 | Decision Right 必须绑定 Source Mandate、Role Assignment、风险级别、限制、有效期、所需复核、SoD 约束及撤销规则。职位、仓库权限或签名本身不能授予该权利。 |
| 1810 §30 | 参与者须披露个人、供应商、绩效、合同、实施、调查等重大利益冲突；流程须记录回避或参与限制。 |
| 1810 §47 | Professional Reviewer 只能在其专业范围内提供意见，并说明约束、所需行动、意见有效期和未解决事项。委员会表决不能代替要求的专业意见。 |
| 1810 §§60–65 | 可按风险合并兼容角色；身份和授权等高风险事项需要更强职责分离。直接受益人不能单独批准高风险请求。小团队补偿措施不能变成永久自审批。 |
| 1820 §15 及附录 B | Role Assignment 需明确主体、角色、范围、目的、环境、有效期、来源批准、SoD、复核负责人和复核日期。 |
| 1890 §§16、22、30、58 | 高风险事项需要独立质疑和适用的职责分离；禁止自审批、自验证；关闭验证必须保持适当独立。 |
| 1885 §§110–112 | Git commit 是源代码版本。有效签名证明签署者身份及签署对象完整性，不证明其 Mandate 或决策权。Registry 回执与专业审查是不同控制。 |
| 008 §§14.2、26.2–26.3 | Book 描述了最低 Project/Architecture 参与要求，同时记载正式审批角色和机器可读权限来源尚未建立。Book 本身没有任命 Founder、Approver、Custodian 或 DBA。 |

Book **没有明文授予，也没有明文禁止**个人项目创始人建立项目范围内的首个治理 Mandate。因此，本包采用一条范围狭窄、仅向前生效的构成性路径：由 Owner 依据其对项目资产原始所有权/控制权的声明签发一次性授权，再由另一位真实人员审查，决定是否建立首个有效项目 Mandate 和 Custodian 任命。这是对 Book 留白的有限解释，不是外部法律意见。如果范围内任何资产实际属于公司、共同所有人、合同相对方、信托或其他上位权利主体，必须以该主体的真实授权文件替代个人 Owner 前提。

Book 没有设立名为 Constituting Approver 的通用角色，也没有写明每个首个 Mandate 都必须经第二人批准。本包选择第二人进行一次构成性复核，作为建立项目首条权限链时避免 Owner 单独批准自身初始权限的可审计控制。这是本项目所采用的引导控制，不是声称 Book 存在普遍的“构成性审批人”条款。该一次性初始权利直接来自被声明的项目原始权利主体；不假设此前已经存在 Mandate 或 Registry Custodian。

Founder 可基于其所声明的原始权利邀请并有条件地指定 Approver，但邀请本身不等于 Approver 的 Mandate。受邀人必须接受指定的一次性 Role Assignment、披露冲突，并针对精确的审批包摘要签署决定。不假设已有 Registry Custodian：Founder 以临时提交人身份提交首份材料；只有独立决定获批且签署结果取得 Registry commit/receipt 后，Custodian 任命才开始生效。不追溯登记或补写旧日期。

### 1.2 构成性审批人的最低资格与独立性

候选人接受任命前必须满足以下各项：

1. 是真实自然人，且不同于 ACTOR-OWNER-1 及 M6-A07 的实现者/执行者。
2. 提供适用于所选签署方式、可核验的非敏感身份引用。本包只记录身份引用和证据 URI，不收集私钥等凭证。
3. 能证明其有能力审查治理/架构权限边界、范围受限的 Mandate、Decision Right、Role Assignment、SoD、冲突披露和受控记录是否充分。Book 没有指定证书；候选人须说明相关经验、依据和能力边界，单独的头衔不构成证明。
4. 对本决定不存在重大财务、所有权、雇佣/汇报、供应商、交付、绩效或个人利益。披露相关关系；独立判断受影响时必须回避。
5. 只接受下文所列的一次性、短期限 Decision Right。该权利不涵盖 AUTH-1～4、技术实现、AUTH-5、AUTH-6、Production、NewAPI 或数据库操作。
6. 审阅准确的 Owner 声明、适用 Book 版本、本审批包、拟议初始 Mandate、Custodian 任命、范围排除项、冲突和 Registry 渠道；记录未解决问题与条件。
7. 由本人选择 APPROVE、REJECT、REVISE 或 DEFER，以本人文字作出决定并亲自签署。Codex 不代填身份、意见或签名。

不预设任何资格。如候选人不能证明治理/架构审查能力、存在利益冲突，或缺少其一次性任命的有效来源，不启用该 Role Assignment；应邀请其他候选人，或取得真正上位权利主体的授权文件。

### 1.3 构成性审批人与 AUTH-5 审查人能否由同一人担任

Book 没有一概禁止同一合格人员担任这两项任命。两者属于不同的决定范围，分别需要 Mandate、Role Assignment、利益冲突检查和签署意见：

- Constituting Approver 审查 Founder 的来源权利声明、初始 Mandate、Decision Right 和首个 Custodian 任命。
- AUTH-5 审查最终实现的精确代码、测试、Schema、协议及获准的 PG 证据；审查人必须不同于实现者，并持有覆盖相应 Identity/Security/Quality 范围的专业 Mandate。

只有在该人员分别满足两种范围的能力和 Mandate 要求、不参与实现或指挥被审工程、无重大利益冲突，并且 AUTH-5 意见不包含对其本人构成性决定的批准/验证时，才可兼任。如果 AUTH-5 范围包含该权限链，必须另由一人验证构成性权限链。建议默认由两人承担：一名 Constituting Approver 和一名 AUTH-5 Reviewer。两种任命均不会自动赋予 AUTH-6 Gate 权限。

## 2. 已冻结证据与基线

以下事实按此前提供并核验的状态复用；不再生成签名验证回执：

- 候选 Registry 分支：governance/decision-registry；据报当前 HEAD 为 855ec80e9fc1f9fba96cb552dcbd868b4f8bfaed。
- Owner 报告 GitHub 对 855ec80... 及其前序 471ee7484ba619265ddefe770d0f1e5c46fbe9cf 显示 verified=true / reason=valid。
- Ruleset 25699958（INKFLOW-DECISION-REGISTRY-INTEGRITY-v1）据报为 Active，要求提交签名、禁止删除和 non-fast-forward，bypass actors 为空，当前用户 bypass 为 never。
- 既有引导记录：docs/operations/test-only/decision-registry/records/registry-bootstrap-receipt-0001.json 和 registry-bootstrap-receipt-0002.json。
- 既有 ledger 明确标记 FOUNDER-ROOT-001 和 MANDATE-ROOT 尚未生效。Owner 先前签署的 FOUNDER-ROOT-001 v0.1 保留为已签署的 Owner 权利声明候选；本包不将其升级或改写为生效记录。

在当前 Ruleset 下，受签名保护的 Registry 分支是追加式证据存储位置，但它本身不是治理 Authority，Bootstrap 回执也不会让提交的决定自动生效。真实人员接受并签署后，应以新文件/新 commit 登记精确材料，保留所有既有文件和回执，不覆盖历史内容。

## 3. 首次构成性决定：待填写的完整文书

以下文书组成一个审批包，供审阅。Owner 和受邀人只填写各自的身份、Mandate 和签名字段。若任何必要来源或声明不属实，应选择 REVISE 或 DEFER，不得为了通过而强填。

### 3.1 Owner 的前瞻性来源与邀请记录

以下 YAML 字段名为机器可读标识，字段值及说明均以中文书写：

~~~yaml
record_type: founder_constitutive_source_and_approver_invitation
record_id: FOUNDER-ROOT-001-v1.0
status_before_signatures: CANDIDATE
issuer_identity_ref: ACTOR-OWNER-1
signer_account_ref: leejaen
source_basis:
  assertion: "本人声明：我个人拥有或控制本记录范围内列明的 InkFlow 项目资产，并有权为这些资产建立治理制度。"
  superior_rights_holders_checked: "签署时填写 true 或 false"
  excluded_or_exceptional_assets: []
  evidence_reference: "FOUNDER-ROOT-001-v0.1 和/或非敏感所有权/控制权证据 URI"
scope:
  project: InkFlow
  work_package: M6-A07
  environment: TEST_ONLY
  product_scope: Windows Desktop / Identity-only
  assets: "项目治理记录及项目自有的 TEST_ONLY 源码工件"
  explicit_exclusions: [Production, NewAPI, 共享/既有数据库, 客户数据, 生产凭证, 未授权外部资源]
one_time_appointment:
  assignment_id: GOV-BOOTSTRAP-001-v1
  decision_right_id: DR-GOV-BOOTSTRAP-001-v1
  appointee_identity_ref: "候选人真实接受邀请后由 Owner 填写"
  allowed_decision: "仅可批准、拒绝、要求修订或暂缓本包中的初始 Mandate、Registry 指定及首个 Custodian 任命"
  not_delegable: true
  expiry: "候选人接受之日起 30 个日历日，或在决定作出/任命撤销时提前终止"
  limits: "不授予 AUTH-1..4、工程实现、AUTH-5、AUTH-6、Production 或资源操作权限"
governing_book:
  versions_and_digests: "签署前记录准确的源文件版本及摘要"
  applicable_sections: [1810:12-16, 1810:19, 1810:30, 1810:63-65, 1820:15, 1890:16, 1890:22, 1890:30, 1885:110-112, 008:14.2, 008:26.2-26.3]
decision_package_digest: "被审阅的准确审批包规范化内容的 SHA256"
owner_signature: "由 Owner 本人实际签署，不得代填"
signed_at: "实际签署时间及时区"
registry_commit_and_uri: "实际提交并收到回执后填写"
~~~

**Owner 的准确声明（签署时仍属实才可签署）：**“本人是 InkFlow 项目的个人 Project Owner，并声明我个人拥有或控制本文件范围内的 InkFlow 资产，有权为这些资产建立项目范围内的治理流程。我已列明任何上位权利主体、共同所有人、合同或外部约束。本文件只向前生效、仅限该项目和 TEST_ONLY 工作，不创设任何法律实体权限，也不免除独立审查或专业审批。我仅为本包所述的一次性审查任命所列候选人；任命按所列条件到期，不授予工程实现或 AUTH 权限。”

### 3.2 候选人接受及 Role Assignment

~~~yaml
record_type: role_assignment_and_acceptance
assignment_id: GOV-BOOTSTRAP-001-v1
principal_identity_ref: "候选人填写非敏感且稳定的身份引用"
principal_type: natural_person
role: Constituting Approver (one-time)
role_version: 1
scope: "仅限 GOV-BOOTSTRAP-001、准确的审批包摘要及项目自有 M6-A07 TEST_ONLY 治理"
purpose: "独立审查首个 Mandate、Registry 指定及首个仅限记录职责的 Custodian 任命"
environment: TEST_ONLY governance records
source_approval: "FOUNDER-ROOT-001-v1.0、Owner 签名及实际记录 URI"
effective_from: "候选人接受时间；不得早于 Owner 签署"
effective_until: "接受之日起 30 个日历日，或更早的决定/撤销时间"
allowed_outcomes: [APPROVE, REJECT, REVISE, DEFER]
prohibited: [AUTH-1, AUTH-2, AUTH-3, AUTH-4, 工程实现, AUTH-5, AUTH-6, Production, 数据库/资源准入]
competence_evidence: "候选人简述相关经验/证据及能力边界"
mandate_source: "Owner 签署的构成性来源记录中的一次性明确授权；附记录 URI"
conflict_disclosure: "候选人填写利益、先前参与、汇报/财务关系，或声明无相关冲突"
sod: "候选人不同于 ACTOR-OWNER-1 和实现者，也不是后续技术权限的受益人"
review_owner: "ACTOR-OWNER-1 仅行政跟踪到期/撤销；此项不构成自我复核或自我续任权"
review_at: "不晚于到期日"
acceptance: "候选人本人签署的接受声明"
signature_identity_ref: "候选人可核验的签署身份引用"
signed_at: "实际时间"
~~~

本任命为有条件任命：只有 Owner 签署、候选人接受并通过实际受控渠道提交后，任命才生效。候选人作出本次决定、被拒绝/撤销或任命到期时，任命即终止。候选人不得续期或转授权。

### 3.3 拟供批准的初始 Mandate、Decision Right 与 Custodian 任命

候选人审查并可批准/拒绝/要求修订/暂缓以下完整且有边界的方案：

**初始来源 Mandate：FOUNDER-GOV-001-v1。** 为所有权声明范围内的 InkFlow 项目资产建立并维护版本化治理记录；只有在记录中明确授权时，才可创建项目 TEST_ONLY 范围的 Decision Right 和 Role Assignment；保存冲突、异议、证据、到期、撤销和复核信息。不产生公司、法律实体、Production、客户数据、NewAPI、外部资源、专业专家或 AUTH 决策权限。

**Decision Right：DR-REGISTRY-RECORD-001-v1。** 批准后，允许指定的 Registry Custodian 向现有 Registry 提交已获批准的记录、维护索引和链接证据引用。该权利不得批准决定、证明他人的 Mandate、将未批准结果标记为生效、改写历史内容、绕过 Ruleset、出具专业意见或决定 Gate。

**初始 Role Assignment：INKFLOW-REGISTRY-CUSTODIAN-001-v1。**

| 字段 | 拟议值 |
|---|---|
| 主体 | ACTOR-OWNER-1 / 账户 leejaen；身份与密钥绑定仍需独立证据 |
| 角色 | Interim Registry Custodian，仅负责记录、索引和链接 |
| 范围 | INKFLOW-DECISION-REGISTRY-001，M6-A07 TEST_ONLY 治理记录 |
| 来源 | FOUNDER-GOV-001-v1 和已签署的独立 GOV-BOOTSTRAP-001 决定 |
| 有效期 | 从批准决定的实际 Registry commit receipt 起至 30 个日历日；不得追溯生效 |
| 复核负责人 | 初始期限内由 Constituting Approver 复核 |
| SoD 排除项 | 不得批准自身任命；不得批准 AUTH；不得担任 AUTH-5；不得决定 AUTH-6；不得自我验证；不得改写历史或绕过保护规则 |
| 撤销 | 通过新的有权签署决定撤销；签名密钥或 Ruleset 完整性丧失时立即暂停 |

批准此方案的是独立 Approver 的决定，而不是 Custodian 的提交动作。只有决定为正面批准且取得实际回执后，来源 Mandate 和任命才从该回执时间开始向前生效。REVISE、REJECT 或 DEFER 均不会建立来源 Mandate 或 Custodian 权限。

### 3.4 构成性决定表单——仅由候选人填写

~~~yaml
record_type: constituting_approval_decision
decision_id: GOV-BOOTSTRAP-001-DECISION-v1
candidate_identity_ref: "候选人填写"
role_assignment: "GOV-BOOTSTRAP-001-v1 的 URI/摘要"
mandate_source: "FOUNDER-ROOT-001-v1.0 的 URI/摘要及 Owner 准确的来源权利声明"
reviewed_package_digest: "SHA256"
book_versions_and_digests: "准确版本和摘要"
conflict_disclosure_and_recusal: "候选人填写"
competence_scope_and_limits: "候选人填写"
decision: APPROVE | REJECT | REVISE | DEFER
reasoning: "候选人的本人意见"
conditions_or_findings: []
residual_unknowns: []
effective_scope: "仅限第 3.3 节所列完整方案"
signed_at: "实际时间及时区"
signature_identity_ref: "候选人可核验的签署身份引用"
signature: "候选人本人 GitHub-verified SSH 签名 commit；仅在签署渠道仍有效时使用"
registry_commit_receipt_uri: "填写实际回执 URI；不得把占位内容视为回执"
~~~

候选人必须先审阅已填写的 Owner 来源权利声明、准确 Book 摘要、无冲突披露和审批包准确内容，之后才可签署 APPROVE。任何人不得代替候选人填写决定字段。

## 4. 后续记录的 Registry 提交与校验

沿用第 2 节冻结的现有受保护分支和 Ruleset，不另建 Registry，也不另造技术验证回执。本包所需的 Registry 处理仅包括以下新建且不可覆盖的文件：

1. Owner 签署的前瞻性来源/邀请记录。
2. 候选人接受的一次性 Role Assignment，以及冲突和能力声明。
3. 候选人签署且绑定准确审批包摘要的决定。
4. 只有候选人有效批准后，Custodian 才可出具回执/更新索引。此回执仅确认存储和链接，不批准决定。

每份记录均须核验：规范化内容及摘要；签名覆盖该 commit/工件且 GitHub 将其识别为预期签署身份的 Verified；身份引用对应实际主体；来源 Mandate 已存在，且在适用情况下早于任命或与任命同时生效；任命的范围、时间和接受记录覆盖该决定；冲突披露/回避完整；不存在自我批准；决定列明准确证据摘要；决定结果和条件可解析；生效时间不早于所有前置条件和 Registry 回执；没有覆盖任何既有记录。任何一项核验失败，状态均为未生效。SHA256、Verified、Git commit 或存储回执单独存在均不足以证明治理权限。

如果 GitHub 签名密钥、账户绑定、Ruleset、分支或签名要求发生变化，必须通过项目已批准的流程重新确认后再依赖该渠道。不得伪造签名、回执或时间，不得追溯补写 Role Assignment。

## 5. AUTH-1 至 AUTH-4：待签技术决定附件

Owner 先前在聊天中对展示的技术方案选择了 APPROVE；目前只能记录为决定意图。以下内容保留为后续正式决定的精确范围。在正式记录生效前，不得实现相关路由、迁移、加密 Envelope 或 PG 实例。

### 5.1 AUTH-1——刷新结果恢复协议（Refresh Result Recovery）

**所需 Decision Right：** Architecture Owner 与 Identity Domain Owner。来源 Mandate 和 Role Assignment 必须明确覆盖 Identity refresh/recovery 及 Windows Desktop TEST_ONLY。设备证明和重放控制还需 Security 复核。Owner 先前的聊天答复不构成这些权限。

**拟议协议：**

- Client 生成高熵 operation identifier，并在发送 Parent refresh credential 前持久化受保护的 pending record。记录绑定 operation digest、Parent digest、Session、Device、token Generation 和创建时间；不得在普通文件或日志中保存/记录原始 Parent 或 Child。
- Rotation 在一个事务中仅消费一次 Parent，并创建一个逻辑 Child。同一 operation 且绑定信息完全一致的重试只能取回同一个 Child；重复使用 operation 但 Parent、Session、Device、Generation 或参数不同则拒绝。不得生成第二个 Child 或造成 Family 分叉。
- Recovery challenge 使用新鲜、基于 server nonce 的一次性挑战，并由已登记设备私钥签名。验证有效 Device 公钥绑定及有效 Session/Family/Generation。Operation ID 不能单独作为取回凭证。未知设备、签名无效、挑战过期/重放、绑定不一致、Session 失效或 operation 改变均须拒绝。
- Recovery 窗口为 Rotation 成功后 120 秒。窗口内最多成功返回同一 Child 三次；过期后不得 Recovery。首次 Rotation 响应不计入 Recovery 返回次数。
- Client 先把 Child 持久化到批准的受保护凭证存储，再发送 ACK。ACK 为幂等操作；服务端收到 ACK 后清除加密 Child Envelope。若清除后 ACK 响应丢失，之后的 Recovery 只能报告已确认/不可用，不得重新生成 Child。
- TTL 到期仍未 ACK 时，清除密文并撤销受影响的 Family；不得恢复 Parent、延长 Parent 有效期或静默签发替代 Child。明确撤销时清除密文并使待处理 operation 失效。审计记录只包含标识符、摘要和结果，不包含 Token 或密钥。
- 状态机：ROTATED_RESULT_STORED -> RECOVERY_ALLOWED -> ACKED；TTL 到期时 RECOVERY_ALLOWED -> EXPIRED_AND_FAMILY_REVOKED；发生适用的安全撤销时进入 REVOKED_AND_CLEARED。终态 ACKED、EXPIRED_AND_FAMILY_REVOKED 和 REVOKED_AND_CLEARED 均不得返回 Child 字节。

**授权后必须测试：** 初次响应丢失后取回相同 Child；三次返回和 120 秒边界；挑战重放/签名无效；跨 Device、Session、Family、Generation 和变更 operation 的拒绝；并发 Recovery；ACK 幂等和 ACK 响应丢失；ACK/过期/撤销时清除密文；到期撤销 Family；不得恢复 Parent 或分叉 Child；网络前 Client pending record 已持久化、ACK 前 Child 已安全保存，以及各状态边界的崩溃/重启行为。

### 5.2 AUTH-2——TEST_ONLY 结果信封（Envelope）与密钥边界

**所需 Decision Right：** Security/Crypto 角色，且具备明确覆盖本 TEST_ONLY 加密决定的有效 Mandate。现有七项角色兼任说明并未建立 Crypto/KMS 专项 Mandate。

**聊天中先前选择的精确方案：** AES-256-GCM；每个 Envelope 使用唯一的 96-bit nonce 和 128-bit tag；规范化 AAD 绑定协议/版本、operation ID、Session、Device、Family、Generation、用途及到期时间；缺少或重排任一字段都必须导致认证失败。每个获准测试任务使用新的随机密钥。在 Windows 上通过 DPAPI CurrentUser 保护任务密钥；不得宣称其具备 Production KMS/HSM 或多用户保护能力。只存储密文、nonce、tag 和必需的有界元数据。不接入生产 Secret Manager/KMS/HSM。任务结束或密钥疑似泄露时销毁任务密钥；源码、日志、数据库明文字段、证据及聊天中不得出现密钥或 Token。

必须检查：nonce 唯一性；AAD 篡改/跨上下文替换；tag 校验失败；密钥不可用；进程/用户边界；任务结束后密钥删除/不可用；TTL/ACK/撤销后的密文销毁。如果当前 Book 或加密实现约束与 AES-GCM/DPAPI 冲突，签署人必须选择 REVISE，不得静默替换算法。

### 5.3 AUTH-3——候选数据库结构（Schema）与迁移（Migration）决定

**所需 Decision Right：** Architecture Owner 与具备实际范围 Mandate 的 DBA/DB Owner；Security/Crypto 复核静态加密边界。目前未核实 DBA/DB Owner Mandate。

**候选结构：** 不新增表；现有源 Schema 包含 identity.devices（00012）及 identity.refresh_tokens（00004，经 00009 调整）。拟议 Goose Migration 编号为 00114，但只有在授权时通过只读 Migration 清单确认该编号仍可用后，才可使用。

拟议 identity.devices 可空字段：

| 字段 | 用途/拟议规则 |
|---|---|
| recovery_signing_key_id TEXT | 稳定密钥引用/指纹标识；不存储私钥材料。 |
| recovery_signing_public_key BYTEA | 验证新鲜 Recovery challenge 的设备公钥；算法及编码由正式批准的设备签名方案固定。 |
| recovery_signing_key_bound_at TIMESTAMPTZ | 登记/绑定时间。 |
| recovery_signing_key_revoked_at TIMESTAMPTZ | 撤销标记；密钥撤销后不得再用于持有证明。 |

拟议写入已消费 Parent 行的 identity.refresh_tokens 字段：

| 字段 | 用途/拟议规则 |
|---|---|
| token_generation BIGINT NOT NULL DEFAULT 1 | 现有 Family 链中的正数 Generation；只有验证既有链路后，才能将历史行安全回填为 1。 |
| recovery_operation_id UUID | 稳定 operation 标识；仅 Recovery-enabled Rotation 结果存在。 |
| recovery_device_id BIGINT REFERENCES identity.devices(id) ON DELETE RESTRICT | 绑定结果/挑战的 Device。 |
| recovery_parent_digest BYTEA | 将 operation 绑定到已消费 Parent 的摘要；不存储 Parent Token。 |
| recovery_envelope_key_id TEXT | 任务专用密钥引用，不存储密钥材料。 |
| recovery_envelope_nonce BYTEA | 12-byte AES-GCM nonce。 |
| recovery_envelope_ciphertext BYTEA | 仅存储加密的 Child 结果。 |
| recovery_envelope_tag BYTEA | 16-byte AES-GCM tag。 |
| recovery_result_created_at TIMESTAMPTZ | Envelope 结果提交时间，用于确定短时 Recovery 窗口。 |
| recovery_expires_at TIMESTAMPTZ | 绝对到期时间，最迟为成功 Rotation 后 120 秒。 |
| recovery_delivery_count SMALLINT NOT NULL DEFAULT 0 | 成功 Recovery 返回次数，限制为 0–3。 |
| recovery_acknowledged_at TIMESTAMPTZ | 幂等 ACK 终态时间；ACK 时清除密文、nonce、tag 和密钥引用。 |
| recovery_terminal_reason TEXT | 有界原因，例如 acked、expired_family_revoked、security_revoked；不得包含秘密数据。 |

**候选完整性规则：** 创建部分唯一索引 ux_refresh_tokens_recovery_operation，在 recovery_operation_id 非 NULL 时以 (token_family_id, recovery_operation_id) 唯一；创建仅覆盖仍有有效密文行的 recovery_expires_at 清理部分索引；token_generation 必须为正数；delivery count 限制在 0 至 3；Envelope 字段必须全部完整或全部为空（nonce 正好 12 字节、tag 正好 16 字节，cipher/key/创建时间/到期时间同时存在）；recovery_expires_at 必须晚于 recovery_result_created_at，且不晚于其后 120 秒；ACK/过期/撤销终态不得保留密文、nonce、tag 或密钥引用；operation ID 必须同时绑定 Device ID 和 Parent digest；返回前在事务内验证链路、Session 和 Device 所有权。Rotation 并发必须保持既有 replaced_by_token_id 的单 Child 链。每个 Family/operation 不得产生两个结果；不同 Generation 可使用新的 operation。Token、密钥或明文结果不得进入日志/审计。

只允许先新增可空字段，再做验证后的安全回填；不得给历史 Recovery 字段添加非空默认值。在将 token_generation 改为 NOT NULL 或添加唯一/检查约束前，须证明历史链路正确，并在单独获准的合成数据测试中发现/处理重复值。确切 DDL、约束名称、索引语义，以及 Generation 应置于 Parent 行还是 Child 行，均须由签署人在确认实际 Refresh Rotation 模型后决定。本包没有批准任何 DDL。

**Down/保留规则：** 只要仍有有效/未到期 Recovery 结果或非终态 operation，Down 必须以明确异常停止。所有记录都变为 ACKED/EXPIRED/REVOKED 且证据/历史按批准的保留规则留存后，Down 才能删除本次新增的 Recovery 字段和索引。Migration 不得删除既有 Device、Refresh Token、撤销、安全历史或审计行。独立签署人必须检查确切 DDL、约束、锁顺序、回填、Migration 清单/HEAD、清理查询、保留期限和回滚前置条件。

授权后的 PG 测试包括：全新 Up/Down；合成历史行升级；重复 operation/Parent 并发竞争；唯一性/状态约束失败；事务回滚；清理不越界；存在有效行时 Down 被阻止、终态清空后 Down 才通过；保持现有 Token Family/撤销不变量。

### 5.4 AUTH-4——隔离的 PostgreSQL 16 测试准入

**所需 Decision Right：** Operations Owner 与对本地测试资源具有实际授权的 DBA/DB Owner。仅有 Owner 角色名称并不自动赋予任意本地/远程引擎或资源的访问权。

**精确请求边界：** 一个任务专属、可销毁的 PostgreSQL 16 容器；仅 loopback 随机端口；无出站网络；workers=0；Identity-only 测试 Harness；CPU 1 核；内存和 swap 各不超过 2 GiB；shared memory 256 MiB；PIDs 不超过 200；最长运行 60 分钟；只能使用本机已存在且可核验的镜像；独立合成数据库和一次性凭证；只销毁本任务精确创建的容器/数据库/凭证。不得访问、停止、清理或配置 NewAPI、既有/共享数据库、Production 服务、CVM 或外部资源。如主机策略拒绝某操作，不得绕过。

启动前准入清单须签署：主机和 Docker context；镜像摘要；全新唯一任务标签；可用 loopback 端口；资源限制确实生效；网络禁用；worker 数为零；不改变其他资源的预检清单；获准创建/检查/销毁的精确资源 ID；清理负责人和截止时间；证据脱敏规则。本清单只是准入方案，不证明资源已创建或授权已授予。

## 6. 后续 AUTH 记录字段与 Registry 状态规则

创建四份独立记录，不得把四项决定合并为一个布尔值。每份记录都必须包含：

~~~yaml
auth_id: AUTH-1 | AUTH-2 | AUTH-3 | AUTH-4
decision_id: "稳定的唯一 ID 和版本"
object: M6-A07 / Windows Desktop / Identity-only / TEST_ONLY
technical_spec_digest: "准确附件/DDL/资源范围的 SHA256"
alternatives_and_rationale: "已审阅并记录的替代方案及理由"
source_mandate_uri_and_version: "实际生效的来源"
decision_right_and_role_assignment_uri: "主体、范围、环境、期限、来源及 SoD"
required_specialist_opinions: "实际角色及意见范围，或明确写出不适用依据"
conflicts_and_recusals: "实际披露与处理结果"
decision: APPROVE | REJECT | REVISE | DEFER
conditions_limits_and_expiry: "准确条件、限制和到期时间"
signer_identity_reference: "已核验映射；不得包含秘密"
signed_at: "实际时间及时区"
signature_verification_reference: "真实的已验证工件 URL/SHA"
registry_receipt: "实际回执 URI、记录版本和 commit"
effective_at: "所有前置条件及回执齐备后才填写"
status: "所有必需权限核验通过前均为 NOT_EFFECTIVE"
~~~

AUTH-1 需 Architecture + Identity 权限及设备证明/Security 复核；AUTH-2 需 Security/Crypto 权限；AUTH-3 需 Architecture + DBA/DB Owner 权限及 Security 存储复核；AUTH-4 需 Operations + DBA/DB Owner 资源权限。各项互不继承批准。AUTH-5 仍须在实现后由真实独立人员完成工程审查；AUTH-6 仍须由有权人员作出独立 DEC-06/Gate 决定并取得实际 Registry 回执。

## 7. 端到端工程测试计划（当前不实施）

所需决定生效后，实现者可直接依此计划工作，无须另开 Prompt 轮次。以下仅为计划；本包没有新增或运行这些测试。

1. **协议单元/状态测试：** 所有状态转换；operation 绑定不一致；签名证明/nonce 重放；重试次数/TTL 边界；ACK/到期/撤销；错误结果确定性；不得恢复 Parent、分叉 Child 或记录秘密。
2. **Backend 事务测试：** Parent 消费、Child 创建和加密结果存储原子性；竞争请求；相同重试返回同一逻辑 Child；不同参数拒绝；回滚不留下部分 Rotation/Recovery 状态；audit/security history 原子提交。
3. **Desktop 持久化测试：** 网络请求前 pending operation 已持久化；受保护凭证存储；本地写入失败；服务端提交后/响应前崩溃；重启取回；ACK 前 Child 已持久化；ACK 丢失；不得恢复过期 Principal 或明文持久化 Token。
4. **Schema 测试：** 编号前核对准确 Migration HEAD；干净 Up/Down；代表性安全回填；约束/索引竞争测试；清理范围；存在有效记录时 Down 防护；保持既有 Refresh 和撤销不变量。
5. **PG16 集成/故障注入：** 仅在 AUTH-4 生效后，使用新建任务专属本地实例、workers=0、合成主体、规定资源上限并按要求清理。测试提交成功但响应丢失、并发 Rotation、审计失败回滚、ACK/TTL/撤销、重启和资源销毁。
6. **证据/审查：** 只保存脱敏断言和 trace ID、工件摘要、准确环境/镜像摘要，不包含凭证、Token 或密钥字节。真实 AUTH-5 Reviewer 获得准确 commit/baseline 和证据清单，记录发现/条件/未解决风险，不实现被审代码或签署自己生成的证据。取得另一项有效 DEC-06 Authority 和回执前，Gate 保持待定。

## 8. 必须由另一位真实人员完成的最小动作

建立首个 Mandate 和 Custodian 任命至少需要一位独立人员完成以下动作：

1. 收到准确审批包和 Book 条款；核验 Owner 已签署的来源权利声明、范围、上位权利主体检查结果及准确审批包摘要。
2. 提供非敏感身份引用、能力/经验及其边界、利益冲突披露，以及其真实 Mandate 来源（Owner 签署的一次性邀请/任命；若存在上位权利主体，则使用该主体的真实授权文件）。
3. 接受一次性 GOV-BOOTSTRAP-001-v1 Role Assignment；亲自审阅完整方案；以本人实际时间填写 APPROVE、REJECT、REVISE 或 DEFER，并写明理由/条件。
4. 以本人已验证签署身份对准确审阅摘要签署决定。Owner 和 Codex 均不得代签。
5. 如批准，允许指定的记录型 Custodian 提交新记录和回执；核验回执指向准确的已签决定。只有此后，有限 Mandate/任命才向前生效。

若同一人后续担任 AUTH-5，还须单独证明工程/Security/Quality Mandate、与实现者独立且无冲突，审查准确工程证据并签署独立意见；不得自我验证其构成性决定。否则由第二位合格人员担任 AUTH-5。AUTH-6 始终需要真实的有权 Gate 决定和 Registry 回执；第一位审批人不会自动成为 Gate。

## 9. 当前状态

| 项目 | 当前状态 |
|---|---|
| Founder 已签署的 v0.1 Owner 权利声明候选 | 保留；根据既有 ledger 尚未生效 |
| Registry 分支与 Ruleset 技术证据 | 按第 2 节冻结并复用；不重复生成回执 |
| Constituting Approver 身份、能力、冲突声明和接受的任命 | 尚未提供；未猜填姓名或结论 |
| 初始 Mandate / Decision Right / Custodian 任命 | 已在本包中准备；尚未生效 |
| AUTH-1 至 AUTH-4 技术选择 | 保留为先前聊天决定意图；尚无正式生效 AUTH 记录 |
| 产品实现 / Migration / PG16 测试 | 本包未实施 |
| AUTH-5 独立审查 / AUTH-6 Gate | 仍是独立后续事项，等待真实合格权限和证据 |

本包可以交给 Owner 邀请的真实候选人审阅。下一步需取得候选人的非敏感身份引用、能力说明和独立性/冲突声明；不要把私密凭证或敏感个人文件放入仓库。候选人确定后，应以新版本/副本填写其真实披露，并由候选人本人审阅和签署。不得修改先前签署的 Founder 文件或既有 Registry 回执。

## 10. 来源文件

- ProductBook/180-Governance-and-Compliance/1810-Governance-Bodies-Decision-Rights-Accountability-and-RACI.md §§5、12–20、30、47、60–65、112、114。
- ProductBook/180-Governance-and-Compliance/1820-Administrative-Roles-Separation-of-Duties-Approval-and-Break-Glass.md §15 及附录 B。
- ProductBook/180-Governance-and-Compliance/1885-Document-Version-Freeze-Supersession-and-Publishing-Governance.md §§110–112。
- ProductBook/180-Governance-and-Compliance/1890-Governance-and-Compliance-Architecture-Freeze.md §§16、22、30、58。
- ProductBook/008-Architecture-Freeze-Register.md §§14.2、26.2–26.3。
- docs/support3system/20261023-1047-InkFlow-M6-A07-Founder-Governance-Bootstrap-Authority-And-Engineering-OneShot-Plan.md（引导条件及 AUTH 工程边界）。
- docs/support3system/20261023-0949-InkFlow-M6-A07-Owner-Admission-And-Final-Closure-Contract.md（AUTH-1 至 AUTH-6 的职责分离和退出要求）。
- docs/operations/test-only/20261023-1351-InkFlow-M6-A07-Founder-Mandate-Bootstrap-Authority-Resolution.md（先前权限解释，属于分析材料，不是生效记录）。
- docs/operations/test-only/decision-registry/records/bootstrap-ledger-v1.json 及既有两份 Registry 引导回执（当前未生效状态与证据存储边界）。
