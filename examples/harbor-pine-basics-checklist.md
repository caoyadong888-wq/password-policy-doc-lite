# Harbor & Pine basics checklist

Filled for Harbor & Pine Cooperative. Mailboxes are at example.com. The LAN is 10.8.0.0/24 and the bastion is 192.0.2.10.

# Harbor & Pine 基础检查单

为 Harbor & Pine Cooperative 填好。邮箱在 example.com。局域网是 10.8.0.0/24，堡垒机是 192.0.2.10。

| ID | Check | 检查 | Status | Evidence |
| --- | --- | --- | --- | --- |
| C01 | The policy names who it covers and which systems it covers. | 策略写明覆盖的人员和系统。 | Yes | Employees and contractors. Harbor IdP, portal.harbor-pine.example.com, LAN 10.8.0.0/24, bastion 192.0.2.10. |
| C04 | Minimum lengths are explicit organization choices, and NIST SP 800-63B is named as reading. | 最短长度是明确的组织决定，并指出应阅读 NIST SP 800-63B。 | Yes | Daily 14 and admin 20 are Harbor choices. The policy tells the reader to read NIST Special Publication 800-63B and does not attribute those numbers to it. |
| C06 | Remote access and privileged access require more than one factor. | 远程访问和特权访问需要多于一种因素。 | Yes | Remote and privileged sign-ins use the Harbor IdP app prompt now. Every account uses it from 2026-09-01. |
| C08 | Privileged work uses a separate account from daily work. | 特权操作使用与日常账号分开的账号。 | Yes | Privileged work uses the -admin account. The daily account cannot hold admin groups. |
| C10 | Administration from outside the office LAN uses the named bastion and MFA. | 从办公局域网以外进行管理时，走指定的堡垒机并使用多因素。 | Yes | Outside 10.8.0.0/24, administration uses bastion 192.0.2.10 and MFA. Portal admin is https://portal.harbor-pine.example.com. |
| C15 | Credential compromise has a sequence: disable, revoke, rotate, notify, review. | 凭证失陷有顺序：停用、撤销会话、轮换、通知、复核。 | Yes | Disable, revoke sessions, rotate the password and readable Harbor Vault secrets, mail security@example.com, review the previous 14 days. |
