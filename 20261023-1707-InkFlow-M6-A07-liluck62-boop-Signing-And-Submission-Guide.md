# 致 liluck62-boop：InkFlow M6-A07 构成性审查与签署操作说明

**适用候选人：** GitHub 用户 liluck62-boop  
**审批范围：** 仅审查 FOUNDER-GOV-001 初始 Mandate、Decision Right 和 Registry Custodian 任命；不包括 AUTH-1～4 工程批准、AUTH-5 工程审查或 AUTH-6 Gate。  
**审查包版本：** 0.1  
**审查包 SHA256：** ECF6356090B99F41C18A0045BE7838E67F869FAFCE2D8A7542CF411F5EDFF6CD  
**本说明状态：** 操作指南；不代表 Owner 已签邀请、候选人已接受/批准或 Mandate 已生效。

> 此文件可由 Owner 转发给候选人。候选人的邮箱地址不写入仓库记录；通过 Owner 已掌握的联系渠道转发即可。

## A. 需要审阅的冻结材料

请核对收到的审查包文件：

- 文件：20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Package-v0.1.md
- SHA256：ECF6356090B99F41C18A0045BE7838E67F869FAFCE2D8A7542CF411F5EDFF6CD
- 版本：0.1

Windows PowerShell 校验命令：

~~~powershell
$reviewPackage = Join-Path $PWD '20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Package-v0.1.md'
if (-not (Test-Path -LiteralPath $reviewPackage)) { throw "找不到冻结审查包：$reviewPackage" }
Get-FileHash -LiteralPath $reviewPackage -Algorithm SHA256
~~~

摘要不匹配时停止；不要自行改写、重新排版或签署不同版本。模板中记录的摘要必须与上面的值完全相同。

## B. 首选交付路径：只使用专用小型私有审查仓库

此路径不需要候选人访问 UltraImageViewer 源码仓库。专用仓库只放冻结审查包、Owner 邀请和本包中的签署记录。Owner 在 GitHub 网页中创建一个新的 Private 仓库，例如：

- Owner：leejaen
- Repository：InkFlow-M6-A07-Admission-liluck62-boop
- Visibility：Private
- 创建时不勾选添加 README、.gitignore 或 License（保持空仓库）

随后 Owner 仅将 liluck62-boop 加入该专用仓库的 Collaborators。此操作是给这个只含审查材料的小仓库写权限，不需要给候选人访问源码。Owner 当前已在 UltraImageViewer 添加的 Collaborator 权限不由本工作流变更；如该权限仅为本审批而添加，Owner 应自行评估是否仍需保留。

专用仓库准备/转发的文件应为：

- 冻结审查包快照；
- Owner 一次性邀请与来源授权记录；
- Role Assignment Acceptance 模板；
- 专业能力、独立性及利益冲突披露模板；
- Constituting Decision 模板；
- 本操作说明。

### B1. Owner 本人签署邀请与一次性授权来源

Owner 必须先亲自填写并检查 Founder 邀请记录，然后用自己的 GitHub 账号/签名密钥提交。聊天邀请、仓库 Collaborator 权限或本指南都不是有效 Mandate。Owner 记录中必须如实声明资产所有权/控制权及上位权利主体检查；有共同所有人、实体、合同或其他上位授权时，先补入真实来源文件。

在 GitHub 建立上述空的 Private 专用仓库后，Owner 在自己的 Windows 机器执行以下命令。先确认目标临时目录不存在；此命令不会接触当前 InkFlow dirty worktree：

~~~powershell
$ErrorActionPreference = 'Stop'
$repoPath = Join-Path $env:TEMP 'InkFlow-M6-A07-Admission-liluck62-boop'
if (Test-Path -LiteralPath $repoPath) { throw "路径已存在，停止且不要覆盖：$repoPath" }
New-Item -ItemType Directory -Path $repoPath | Out-Null
Set-Location $repoPath
git init -b main
git remote add origin 'https://github.com/leejaen/InkFlow-M6-A07-Admission-liluck62-boop.git'
~~~

将本目录中的冻结审查包和模板复制到这个空目录，并放在 records 子目录。Owner 只填写 Founder 邀请记录中的 Owner 字段，不能填写候选人的接受、能力、冲突或决定字段。

使用以下精确源路径复制材料；如果目标路径已有同名文件，停止，不要覆盖：

~~~powershell
$bundle = 'D:\project\InkFlow\docs\operations\test-only\decision-registry\admissions\20261023-1707-InkFlow-M6-A07-liluck62-boop'
$recordsPath = Join-Path $repoPath 'records'
New-Item -ItemType Directory -Path $recordsPath | Out-Null
Copy-Item -LiteralPath (Join-Path $bundle '20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Package-v0.1.md') -Destination $repoPath
Copy-Item -LiteralPath (Join-Path $bundle '20261023-1707-InkFlow-M6-A07-liluck62-boop-Signing-And-Submission-Guide.md') -Destination $repoPath
Copy-Item -LiteralPath (Join-Path $bundle 'records\20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Baseline-Manifest.yaml') -Destination $recordsPath
Copy-Item -LiteralPath (Join-Path $bundle 'records\20261023-1707-InkFlow-M6-A07-liluck62-boop-Founder-One-Time-Invitation-DRAFT.yaml') -Destination $recordsPath
Copy-Item -LiteralPath (Join-Path $bundle 'records\20261023-1707-InkFlow-M6-A07-liluck62-boop-Role-Assignment-Acceptance-TEMPLATE.yaml') -Destination $recordsPath
Copy-Item -LiteralPath (Join-Path $bundle 'records\20261023-1707-InkFlow-M6-A07-liluck62-boop-Competence-And-Conflict-Disclosure-TEMPLATE.yaml') -Destination $recordsPath
Copy-Item -LiteralPath (Join-Path $bundle 'records\20261023-1707-InkFlow-M6-A07-liluck62-boop-Constituting-Decision-TEMPLATE.yaml') -Destination $recordsPath
Copy-Item -LiteralPath (Join-Path $bundle 'records\20261023-1707-InkFlow-M6-A07-liluck62-boop-Registry-Admission-Receipt-TEMPLATE.yaml') -Destination $recordsPath
$ownerInvite = Join-Path $recordsPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Founder-One-Time-Invitation.yaml'
if (Test-Path -LiteralPath $ownerInvite) { throw 'Owner 邀请目标已存在；停止，不覆盖。' }
Copy-Item -LiteralPath (Join-Path $recordsPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Founder-One-Time-Invitation-DRAFT.yaml') -Destination $ownerInvite
Get-FileHash -LiteralPath (Join-Path $repoPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Package-v0.1.md') -Algorithm SHA256
~~~

Owner 签名设置仅作用于此小仓库：

~~~powershell
$ownerPub = Join-Path $env:USERPROFILE '.ssh\id_ed25519_inkflow_signing.pub'
$expectedOwnerFp = 'SHA256:MNWMACWT/Eb8IRvAM1qie5wRA1LLCor8yqnrwKBBdSg'
if (-not (Test-Path -LiteralPath $ownerPub)) { throw "找不到 Owner 公钥：$ownerPub" }
$ownerKeyInfo = ssh-keygen -lf $ownerPub -E sha256
if ($LASTEXITCODE -ne 0) { throw '读取 Owner 公钥指纹失败。' }
$ownerFp = ($ownerKeyInfo -split '\s+')[1]
if ($ownerFp -ne $expectedOwnerFp) { throw "Owner 指纹不匹配：$ownerFp" }
git config --local user.name 'leejaen'
git config --local user.email '<填入 Owner GitHub 账户中显示的已验证或 noreply 邮箱>'
git config --local gpg.format ssh
git config --local user.signingkey $ownerPub
git config --local commit.gpgsign true
git config --local core.longpaths true
git config --local --show-origin --get-regexp '^(gpg\.format|user\.signingkey|commit\.gpgsign|core\.longpaths)$'
~~~

将占位邮箱替换为 Owner 在 GitHub Settings → Emails 页面选择用于 commit 的地址；不要把邮箱或任何密钥秘密写进记录。接着只暂存本次邀请包：

~~~powershell
git status --short
git add '20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Package-v0.1.md'
git add '20261023-1707-InkFlow-M6-A07-liluck62-boop-Signing-And-Submission-Guide.md'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Baseline-Manifest.yaml'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Founder-One-Time-Invitation-DRAFT.yaml'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Founder-One-Time-Invitation.yaml'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Role-Assignment-Acceptance-TEMPLATE.yaml'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Competence-And-Conflict-Disclosure-TEMPLATE.yaml'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Constituting-Decision-TEMPLATE.yaml'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Registry-Admission-Receipt-TEMPLATE.yaml'
git diff --cached --check
git diff --cached --name-only
git commit -S -m 'governance: owner one-time M6-A07 approver invitation'
if ($LASTEXITCODE -ne 0) { throw 'Owner 签名提交失败；停止，不要推送。' }
git show --show-signature --no-patch HEAD
git rev-parse HEAD
git push -u origin main
if ($LASTEXITCODE -ne 0) { throw 'Owner 签名提交推送失败。' }
~~~

推送后，Owner 在 GitHub 的该专用仓库提交页确认签名显示 Verified，记下 commit SHA、URL 和 Owner signing-key 指纹；随后才邀请 liluck62-boop 加入这个专用仓库。Owner 的邀请记录中填写 Owner 提交 SHA/URL。Candidate 不得修改 Owner 邀请文件。

### B2. 候选人配置本人 SSH Signing Key

候选人只使用本人控制的 GitHub 账户 liluck62-boop 和本人私钥。不要使用 Owner 的 SSH key、共享账号或由他人代签。不要发送私钥、口令、Token 或恢复码。

1. 在本人 Windows PowerShell 中检查 Git 版本（SSH commit signing 要求 Git 2.34 或更新版本），并检查本机已有公钥指纹；命令只输出公钥指纹：

~~~powershell
git --version
ssh -V
Get-ChildItem (Join-Path $env:USERPROFILE '.ssh') -Filter '*.pub' -ErrorAction SilentlyContinue |
  ForEach-Object { ssh-keygen -lf $_.FullName -E sha256 }
~~~

2. 打开 https://github.com/settings/keys，以 liluck62-boop 登录。在 SSH and GPG keys 页面检查 Signing keys 区域。若已有本人控制且可用于本项目的 Signing Key，优先复用并核对本机对应公钥指纹；若没有，才创建专用密钥。不要把只用于 Trusted devices 的密钥误加到 Signing keys。

3. 没有合适密钥时，在本人设备上创建 ED25519 签名密钥。系统提示时设置本人可记住的密钥口令；私钥只留在本机：

~~~powershell
$keyBase = Join-Path $env:USERPROFILE '.ssh\id_ed25519_inkflow_constituting_signing'
if ((Test-Path -LiteralPath $keyBase) -or (Test-Path -LiteralPath "$keyBase.pub")) {
  throw "目标密钥文件已存在；停止，不要覆盖：$keyBase"
}
ssh-keygen -t ed25519 -C 'InkFlow M6-A07 Constituting Approver signing' -f $keyBase
if ($LASTEXITCODE -ne 0) { throw '密钥创建失败。' }
ssh-keygen -lf "$keyBase.pub" -E sha256
~~~

4. 在 GitHub Settings → SSH and GPG keys → New SSH key 中，将 Key type 选为 Signing Key；Title 可填 InkFlow M6-A07 Constituting Approver。只复制 .pub 公钥文件内容到 GitHub 表单，绝不复制私钥。保存后确认该指纹出现在 Signing keys。

5. 将下方 $candidatePub 设置为本人实际公钥路径；确认输出的 SHA256 与 GitHub Signing keys 页面对应。若身份或指纹不一致，停止。

~~~powershell
$candidatePub = Join-Path $env:USERPROFILE '.ssh\id_ed25519_inkflow_constituting_signing.pub'
if (-not (Test-Path -LiteralPath $candidatePub)) { throw "找不到本人公钥：$candidatePub" }
$candidateKeyInfo = ssh-keygen -lf $candidatePub -E sha256
if ($LASTEXITCODE -ne 0) { throw '读取本人公钥指纹失败。' }
$candidateFingerprint = ($candidateKeyInfo -split '\s+')[1]
$candidateKeyInfo
~~~

### B3. 候选人检出小仓库、填写并签署决定

候选人接受专用仓库邀请后，打开新 PowerShell 窗口执行：

~~~powershell
$ErrorActionPreference = 'Stop'
$reviewRepo = Join-Path $env:USERPROFILE 'InkFlow-M6-A07-Admission'
if (Test-Path -LiteralPath $reviewRepo) { throw "目录已存在，停止且不要覆盖：$reviewRepo" }
git clone 'https://github.com/leejaen/InkFlow-M6-A07-Admission-liluck62-boop.git' $reviewRepo
if ($LASTEXITCODE -ne 0) { throw '克隆专用审查仓库失败。' }
Set-Location $reviewRepo
git switch -c 'review/liluck62-boop/GOV-BOOTSTRAP-001'
$recordsPath = Join-Path $reviewRepo 'records'
$roleAcceptance = Join-Path $recordsPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Role-Assignment-Acceptance.yaml'
$disclosure = Join-Path $recordsPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Competence-And-Conflict-Disclosure.yaml'
$decision = Join-Path $recordsPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Constituting-Decision.yaml'
foreach ($target in @($roleAcceptance, $disclosure, $decision)) {
  if (Test-Path -LiteralPath $target) { throw "候选人记录目标已存在，停止且不要覆盖：$target" }
}
Copy-Item -LiteralPath (Join-Path $recordsPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Role-Assignment-Acceptance-TEMPLATE.yaml') -Destination $roleAcceptance
Copy-Item -LiteralPath (Join-Path $recordsPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Competence-And-Conflict-Disclosure-TEMPLATE.yaml') -Destination $disclosure
Copy-Item -LiteralPath (Join-Path $recordsPath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Constituting-Decision-TEMPLATE.yaml') -Destination $decision
~~~

先重算审查包 SHA256。候选人只填写自己的 Role Assignment Acceptance、Competence/Conflict Disclosure 和 Constituting Decision 三份文件。APPROVE、REVISE、REJECT、DEFER 均由候选人亲自选择；理由、条件、未解决风险和签署时间都不得预填或代写。Owner 邀请文件保持原样。

在小仓库设置本地签名。将电子邮件占位值替换为 GitHub Settings → Emails 中本人选用的已验证地址或 GitHub noreply 地址；不要使用 Owner 的邮箱：

~~~powershell
$candidatePub = Join-Path $env:USERPROFILE '.ssh\id_ed25519_inkflow_constituting_signing.pub'
$candidateFingerprint = (ssh-keygen -lf $candidatePub -E sha256 | ForEach-Object { ($_ -split '\s+')[1] })
if ($LASTEXITCODE -ne 0 -or -not $candidateFingerprint) { throw '无法确认本人签名密钥。' }
git config --local user.name 'liluck62-boop'
git config --local user.email '<填入候选人 GitHub 账户中显示的已验证或 noreply 邮箱>'
git config --local gpg.format ssh
git config --local user.signingkey $candidatePub
git config --local commit.gpgsign true
git config --local core.longpaths true
git config --local --show-origin --get-regexp '^(gpg\.format|user\.signingkey|commit\.gpgsign|core\.longpaths)$'
~~~

核对本次只提交候选人的三份记录，然后创建新签名提交。不要 amend、rebase、force-push 或重写签署后的提交：

~~~powershell
git status --short
git diff --check
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Role-Assignment-Acceptance.yaml'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Competence-And-Conflict-Disclosure.yaml'
git add 'records/20261023-1707-InkFlow-M6-A07-liluck62-boop-Constituting-Decision.yaml'
git diff --cached --check
git diff --cached --name-only
git commit -S -m 'governance: liluck62-boop constituting decision M6-A07'
if ($LASTEXITCODE -ne 0) { throw '候选人签名提交失败；停止，不要推送。' }
git show --show-signature --format=fuller HEAD
git rev-parse HEAD
git push -u origin 'review/liluck62-boop/GOV-BOOTSTRAP-001'
if ($LASTEXITCODE -ne 0) { throw '候选人分支推送失败。' }
~~~

候选人记录 commit SHA，并在 GitHub 打开其 commit URL，确认页面显示 Verified 且签署账号为 liluck62-boop。然后在专用仓库打开 Pull requests → New pull request：

- base：main
- compare：review/liluck62-boop/GOV-BOOTSTRAP-001
- 标题：M6-A07 constituting decision — liluck62-boop
- 描述：列出审查包 SHA256、候选人签署提交 SHA、决定结果及记录文件路径；不要在 PR 描述中粘贴敏感身份材料。

Owner 只核对身份映射、签名状态、摘要和文件完整性，不替候选人作决定。Owner 合并时选 Create a merge commit，保留候选人原始签名提交；不得使用 squash、rebase、amend 或 cherry-pick 冒充候选人签名。合并后再核对原始候选人 commit 仍在历史中且仍显示 Verified。

Owner 可在已登录 GitHub CLI 的 PowerShell 中用只读 API 再核对该原始提交：

~~~powershell
$candidateSha = '<候选人提供的 40 位完整 commit SHA>'
gh api "repos/leejaen/InkFlow-M6-A07-Admission-liluck62-boop/commits/$candidateSha" --jq '{sha:.sha, account:.author.login, verified:.commit.verification.verified, reason:.commit.verification.reason}'
if ($LASTEXITCODE -ne 0) { throw 'GitHub 未能返回候选人提交验证信息。' }
~~~

预期 account 为 liluck62-boop、verified 为 true、reason 为 valid。若 API 返回 null/false 或身份不是候选人，暂停登记并查明原因。SHA256 公钥指纹由候选人提供并与其本人 GitHub Signing keys 页面核对；GitHub Verified 本身不能证明资格或任命。

### B4. Owner 将真实决定登记到受保护 Registry

候选人原始签署提交保留在专用审查仓库中，不重签、不改写。Owner 在 Registry 中登记原始 commit SHA/URL、候选人签名身份、候选人三份文件的 SHA256、冻结审查包 SHA256、Owner 邀请记录 SHA256、审查结果和实际条件。将文件内容逐字节复制到 Registry 的新路径；不得更改候选人签署的三个文件。

Owner 使用短路径临时克隆，避免触碰当前 dirty worktree：

~~~powershell
$ErrorActionPreference = 'Stop'
$registryPath = 'C:\if-m6a07-registry'
if (Test-Path -LiteralPath $registryPath) { throw "临时路径已存在，停止且不要覆盖：$registryPath" }
git -c core.longpaths=true clone --single-branch --branch 'governance/decision-registry' 'https://github.com/leejaen/UltraImageViewer.git' $registryPath
if ($LASTEXITCODE -ne 0) { throw '克隆 Registry 分支失败。' }
git -C $registryPath config core.longpaths true
git -C $registryPath status --short
git -C $registryPath rev-parse HEAD
git ls-remote 'https://github.com/leejaen/UltraImageViewer.git' 'refs/heads/governance/decision-registry'
~~~

只有本地 HEAD 与远端 Registry branch SHA 一致且工作树干净时继续。由 Owner 创建未占用的新分支，导入签署快照/记录并增加 Registry Admission Receipt 模板。Owner 作为临时提交人签署记录提交并开 PR：

~~~powershell
Set-Location $registryPath
$registryBranch = 'governance/constituting-admission-liluck62-boop-20261023'
$existing = git ls-remote --heads origin "refs/heads/$registryBranch"
if ($LASTEXITCODE -ne 0) { throw '检查 Registry 提交分支失败。' }
if ($existing) { throw "分支已存在，停止且不要覆盖：$registryBranch" }
git switch -c $registryBranch
$ownerPub = Join-Path $env:USERPROFILE '.ssh\id_ed25519_inkflow_signing.pub'
git config --local user.name 'leejaen'
git config --local user.email '<填入 Owner GitHub 已验证或 noreply 邮箱>'
git config --local gpg.format ssh
git config --local user.signingkey $ownerPub
git config --local commit.gpgsign true
git config --local core.longpaths true
~~~

在 Owner 运行完上方 B1 的 PowerShell 窗口内，变量 `$repoPath` 指向专用审查仓库的本地克隆。若已关闭窗口，先在新窗口定义并校验该路径。登记目标使用一次性全新目录；当前示例已占用时停止并选择新的版本化目录名，不得覆盖：

~~~powershell
$evidencePath = Join-Path $env:USERPROFILE 'InkFlow-M6-A07-Admission-liluck62-boop'
if (-not (Test-Path -LiteralPath (Join-Path $evidencePath '.git'))) { throw "找不到已合并的专用审查仓库克隆：$evidencePath" }
git -C $evidencePath status --short
git -C $evidencePath rev-parse HEAD
$sourceRecords = Join-Path $evidencePath 'records'
$admissionTarget = Join-Path $registryPath 'docs\operations\test-only\decision-registry\records\admissions\FOUNDER-GOV-BOOTSTRAP-001\20261023-1707-liluck62-boop-v1'
if (Test-Path -LiteralPath $admissionTarget) { throw "登记目标已存在，停止且不要覆盖：$admissionTarget" }
New-Item -ItemType Directory -Path $admissionTarget | Out-Null
Copy-Item -LiteralPath (Join-Path $evidencePath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Package-v0.1.md') -Destination $admissionTarget
Copy-Item -LiteralPath (Join-Path $evidencePath '20261023-1707-InkFlow-M6-A07-liluck62-boop-Signing-And-Submission-Guide.md') -Destination $admissionTarget
Copy-Item -LiteralPath (Join-Path $sourceRecords '20261023-1707-InkFlow-M6-A07-liluck62-boop-Review-Baseline-Manifest.yaml') -Destination $admissionTarget
Copy-Item -LiteralPath (Join-Path $sourceRecords '20261023-1707-InkFlow-M6-A07-liluck62-boop-Founder-One-Time-Invitation.yaml') -Destination $admissionTarget
Copy-Item -LiteralPath (Join-Path $sourceRecords '20261023-1707-InkFlow-M6-A07-liluck62-boop-Role-Assignment-Acceptance.yaml') -Destination $admissionTarget
Copy-Item -LiteralPath (Join-Path $sourceRecords '20261023-1707-InkFlow-M6-A07-liluck62-boop-Competence-And-Conflict-Disclosure.yaml') -Destination $admissionTarget
Copy-Item -LiteralPath (Join-Path $sourceRecords '20261023-1707-InkFlow-M6-A07-liluck62-boop-Constituting-Decision.yaml') -Destination $admissionTarget
Get-ChildItem -LiteralPath $admissionTarget -File | Get-FileHash -Algorithm SHA256
~~~

在填写 receipt 前，以 Owner 账户对两个原始提交做只读 API 核验。将 Owner 邀请提交 SHA 和候选人提交 SHA 替换为实际 40 位值：

~~~powershell
$ownerSourceSha = '<Owner 已 Verified 邀请提交的完整 SHA>'
$candidateSha = '<候选人原始签名提交的完整 SHA>'
gh api "repos/leejaen/InkFlow-M6-A07-Admission-liluck62-boop/commits/$ownerSourceSha" --jq '{sha:.sha, account:.author.login, verified:.commit.verification.verified, reason:.commit.verification.reason}'
if ($LASTEXITCODE -ne 0) { throw '读取 Owner 来源提交验证信息失败。' }
gh api "repos/leejaen/InkFlow-M6-A07-Admission-liluck62-boop/commits/$candidateSha" --jq '{sha:.sha, account:.author.login, verified:.commit.verification.verified, reason:.commit.verification.reason}'
if ($LASTEXITCODE -ne 0) { throw '读取候选人提交验证信息失败。' }
~~~

预期 Owner account 为 `leejaen`、候选人 account 为 `liluck62-boop`，两者均 `verified: true`、`reason: valid`，且各自提交页显示 Verified。将原始 commit SHA/URL、提交验证信息、签名 key 指纹及实际文件摘要记录进 Owner 的 Registry 登记记录。若任何字段不符或无法核实，停止，不登记为有效。核对目录中三份候选人签署文件字节未变；登记复制不会重新签署或改变候选人原始 commit。此时才继续填写该登记记录（不改写候选人文件），然后仅 stage 新 admission 目录。不得 stage 其他 dirty 内容：

~~~powershell
git status --short
git diff --check
git add 'docs/operations/test-only/decision-registry/records/admissions/FOUNDER-GOV-BOOTSTRAP-001/20261023-1707-liluck62-boop-v1/'
git diff --cached --name-only
git diff --cached --check
git commit -S -m 'governance: register M6-A07 constituting decision evidence'
if ($LASTEXITCODE -ne 0) { throw 'Registry 登记签名提交失败；停止，不要推送。' }
git show --show-signature --no-patch HEAD
git rev-parse HEAD
git push -u origin $registryBranch
if ($LASTEXITCODE -ne 0) { throw 'Registry 登记分支推送失败。' }
~~~

在 GitHub 创建 PR：base 选 governance/decision-registry，compare 选上述登记分支。PR 只登记有效审查证据和引用，不宣称生效。合并前检查候选人原始提交、Owner 来源授权提交和本 PR 新增的所有提交均 Verified；目标 Ruleset 仍 Active 且无绕过。使用 Create a merge commit 保留提交历史。若 GitHub 无法在现有规则下安全合并，停止并报告原因；禁止绕过、force-push、删除/重建目标分支。

Owner 可用 GitHub CLI 创建该 Registry PR；若 CLI 不可用，则在 GitHub 仓库 Pull requests → New pull request 页面使用相同 base/head：

~~~powershell
gh pr create --repo 'leejaen/UltraImageViewer' --base 'governance/decision-registry' --head $registryBranch --title 'Register M6-A07 constituting decision evidence' --body '登记候选人本人签署的构成性决定和冻结审查证据。候选人原始 commit SHA/URL、Verified 状态及材料摘要在新增 Registry 记录中。此 PR 本身不使 Mandate 生效。'
if ($LASTEXITCODE -ne 0) { throw '创建 Registry PR 失败；使用 GitHub 页面检查状态，不要绕过规则。' }
~~~

登记 PR 合并且目标分支已读回后，再通过第二个 Owner 签名 PR 提交最终 Registry Admission Receipt。可按以下命令建立新回执分支：

~~~powershell
git fetch origin 'refs/heads/governance/decision-registry:refs/remotes/origin/governance/decision-registry'
if ($LASTEXITCODE -ne 0) { throw '更新 Registry 远端引用失败。' }
$receiptBranch = 'governance/constituting-receipt-liluck62-boop-20261023'
$receiptExisting = git ls-remote --heads origin "refs/heads/$receiptBranch"
if ($LASTEXITCODE -ne 0 -or $receiptExisting) { throw '回执分支已存在或远端查询失败；停止，不覆盖。' }
git switch -c $receiptBranch 'origin/governance/decision-registry'
~~~

将 Receipt 模板复制到同一 admission 目录的新记录文件；依据 Registry 已合并的决定记录和 GitHub 实际远端状态填写，不得预填未观察到的事实：

~~~powershell
$receiptTemplate = Join-Path $sourceRecords '20261023-1707-InkFlow-M6-A07-liluck62-boop-Registry-Admission-Receipt-TEMPLATE.yaml'
$receiptFile = Join-Path $admissionTarget '20261023-1707-InkFlow-M6-A07-liluck62-boop-Registry-Admission-Receipt.yaml'
if (Test-Path -LiteralPath $receiptFile) { throw '回执目标已存在；停止，不覆盖。' }
Copy-Item -LiteralPath $receiptTemplate -Destination $receiptFile
~~~

若候选人决定不是 APPROVE，或任一权限/身份/冲突/签名核验未通过，回执结论必须为 NOT_EFFECTIVE。只有全部核验通过、候选人决定为 APPROVE 且内容已准确填写时，回执记录才可写入 EFFECTIVE；此时仍须保持该记录只存在于 PR 分支，直到它实际进入受保护目标分支后才生效。Owner 以临时提交人身份签署并推送回执，不因此提前取得 Custodian 权限：

~~~powershell
git status --short
git add 'docs/operations/test-only/decision-registry/records/admissions/FOUNDER-GOV-BOOTSTRAP-001/20261023-1707-liluck62-boop-v1/20261023-1707-InkFlow-M6-A07-liluck62-boop-Registry-Admission-Receipt.yaml'
git diff --cached --check
git commit -S -m 'governance: receipt M6-A07 constituting decision registration'
if ($LASTEXITCODE -ne 0) { throw 'Registry 回执签名提交失败。' }
git show --show-signature --no-patch HEAD
git rev-parse HEAD
git push -u origin $receiptBranch
if ($LASTEXITCODE -ne 0) { throw 'Registry 回执分支推送失败。' }
gh pr create --repo 'leejaen/UltraImageViewer' --base 'governance/decision-registry' --head $receiptBranch --title 'Record M6-A07 constituting decision receipt' --body '此 PR 仅在所有权来源、候选人任命与签署、审查结论和验证均通过时，登记最终回执。'
if ($LASTEXITCODE -ne 0) { throw '创建回执 PR 失败；不要绕过保护规则。' }
~~~

回执 PR 合并后，使用 GitHub commit 页面或只读 API 确认最终目标分支 SHA、回执文件内容、Ruleset Active 和 GitHub Verified。将最终回执 commit URL/SHA 作为实际 Registry receipt。只有此回执已在受保护目标分支且全部前置条件仍通过时，FOUNDER-GOV-001 和 Custodian 任命才生效；AUTH-1～4 仍为 NOT_EFFECTIVE。

### B5. 验证清单

Owner 必须逐项验证并记录实际结果：

1. 候选人登录身份是 liluck62-boop；候选人在候选人记录中接受精确的一次性任命。
2. GitHub 候选人签署提交 URL/SHA 与其报告一致，commit 页面显示 Verified，签署账号显示 liluck62-boop；候选人报告的 SHA256 公钥指纹与其 GitHub Signing Key 绑定一致。
3. 候选人的签名 commit SHA、三个文件 SHA256 和冻结审查包 SHA256 已写入 Registry 新记录；候选人原始提交未 amend、cherry-pick 或伪装成 Owner 提交。
4. 候选人能力声明只记录其本人提供的事实、范围和限制；冲突披露完整；若披露冲突则已按规则回避或重新指定。
5. 决定文件由候选人本人填写；结果、理由、条件、剩余风险和审查材料摘要齐全；结果不是由聊天或 PR 的“Approve”按钮替代。
6. Owner 来源邀请有真实 Owner 签名和可核验提交；超越项目个人资产范围时已附真实上位授权文件。
7. 现有 Ruleset 25699958 仍 Active，要求签名、禁止删除/非快进、bypass 为空；新登记 PR 中所有待合并 commit 均 Verified。
8. 最终 Registry receipt 指向准确候选人记录、原始签名 commit、Owner 来源文件、包摘要及目标 Registry commit；receipt commit 自身也 Verified。
9. 只有以上各项全部成立且候选人决定为 APPROVE，才把 FOUNDER-GOV-001 与 Custodian 任命标为 EFFECTIVE。AUTH-1～4 仍未生效，除非之后分别完成各自授权。

## C. 备选路径：UltraImageViewer Collaborator + 直接 PR

此方式会让候选人访问私有源码仓库。候选人目前已被 Owner 添加为 Collaborator；本备选仅在 Owner 明确选择使用该访问范围时采用。此路径不改变现有权限设置。

候选人在本人 Windows 设备上克隆仓库，基于受保护 Registry branch 创建独立分支。请先确认本机没有同名目录：

~~~powershell
$ErrorActionPreference = 'Stop'
$repoPath = Join-Path $env:USERPROFILE 'UltraImageViewer-M6-A07-Approval'
if (Test-Path -LiteralPath $repoPath) { throw "目录已存在，停止且不要覆盖：$repoPath" }
git -c core.longpaths=true clone --single-branch --branch 'governance/decision-registry' 'https://github.com/leejaen/UltraImageViewer.git' $repoPath
if ($LASTEXITCODE -ne 0) { throw '克隆 Registry 分支失败。' }
git -C $repoPath config core.longpaths true
Set-Location $repoPath
git switch -c 'governance/constituting-liluck62-boop-20261023'
~~~

候选人按 B2 配置本人的 GitHub SSH Signing Key，按 B3 只填写自己的三份文件；先把 Owner 已签邀请和冻结包复制到新的 admission 子目录。提交前确认工作区只含 admission 包，不提交源码改动：

~~~powershell
git status --short
git add 'docs/operations/test-only/decision-registry/records/admissions/FOUNDER-GOV-BOOTSTRAP-001/'
git diff --cached --name-only
git diff --cached --check
git commit -S -m 'governance: liluck62-boop constituting decision M6-A07'
if ($LASTEXITCODE -ne 0) { throw '候选人签名提交失败；停止，不要推送。' }
git show --show-signature --format=fuller HEAD
git rev-parse HEAD
git push -u origin 'governance/constituting-liluck62-boop-20261023'
if ($LASTEXITCODE -ne 0) { throw '候选人分支推送失败。' }
~~~

候选人在 GitHub 打开 Pull requests → New pull request：base 为 governance/decision-registry，compare 为 governance/constituting-liluck62-boop-20261023。PR 中所有新增 commit 必须显示 Verified。Owner 检查原始 commit SHA 和文件摘要后，可合并 Create a merge commit。禁止 squash/rebase、amend、force-push、直接推送 Registry 目标分支及绕过规则。若已有无关/未签名 commit 混入候选人分支，应关闭 PR 并从正确 Registry HEAD 重建干净分支；不要重写候选人的已签署提交。

## D. 候选人独立签名与 Registry 身份的限制

- GitHub Verified 说明 GitHub 能将 commit 签名验证到某个账号/密钥；它不证明候选人具备专业能力、无利益冲突、接受了任命或有 Mandate。
- 候选人必须在自己的 GitHub 账号内添加本人控制的公钥为 Signing Key。Owner 和 Codex 不持有、读取、接收或代用候选人私钥。
- Owner 的 GitHub Verified commit 不能替代候选人签署；候选人的 commit URL/原始 SHA 应留存为证据引用。
- SHA256 是完整性摘要，不是签名、审批、权限来源或 Registry 回执。
- PR 中“Approve”按钮只表示代码审查动作；治理结论必须写入候选人签署的 Constituting Decision 文件。
- 未取得实际有效 Registry 回执前，FOUNDER-GOV-001、初始 Decision Right 和 Registry Custodian 任命均不得标为 EFFECTIVE；AUTH-1～4 仍为 NOT_EFFECTIVE。

## E. GitHub 官方签署资料

- SSH 签署与 Verified 说明：https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification
- 配置 Git 签名密钥：https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key
- GitHub Ruleset 的 Require signed commits 行为：https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets
- 当前 Registry Ruleset 页面：https://github.com/leejaen/UltraImageViewer/settings/rules/25699958

