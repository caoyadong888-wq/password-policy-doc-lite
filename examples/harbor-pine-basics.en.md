# Harbor & Pine password basics

Filled excerpt for the fictional Harbor & Pine Cooperative, effective 2026-03-02. Owner: Mara Chen (security@example.com). These six sections are the cooperative's choices. Lengths are not a reading of NIST Special Publication 800-63B. The office LAN is 10.8.0.0/24. The bastion is 192.0.2.10.

## Purpose and scope

This policy covers employees and contractors who receive a Harbor IdP account, and the systems those accounts can reach. The systems in scope are Harbor IdP, the member portal at https://portal.harbor-pine.example.com, mailboxes at harbor-pine.example.com, the office LAN 10.8.0.0/24, and the documentation bastion 192.0.2.10.

People use the policy when they choose a password, ask for access, or leave. Operators use it when they create accounts, store service credentials, and review sign-ins. It is the cooperative's rule for passwords and access. It is not a certification claim.
## Password composition

A daily password is at least 14 characters. A privileged password is at least 20 characters. Both numbers are Harbor & Pine choices. Read NIST Special Publication 800-63B before treating them as a published minimum. The IdP must accept at least 64 characters. Spaces are allowed. The cooperative does not require a mix of character classes.

People may use a password manager and may paste a password into the IdP sign-in page. Harbor IdP checks new passwords against its banned-password list. How that list is loaded is vendor-specific. Check the identity provider's documentation. This policy does not name a vendor or an API field.

Sign-in throttling is also a Harbor choice: 10 failed password attempts in 15 minutes lock the password for 15 minutes. it-ops@example.com can unlock sooner. Check the IdP docs for the setting name before you configure it.
## Multi-factor authentication

Remote access and every privileged sign-in require a second factor now. The second factor is the Harbor IdP app prompt. From 2026-09-01, every account requires that second factor, including sign-ins from the office LAN 10.8.0.0/24. That date is a Harbor choice.

Harbor & Pine does not issue hardware tokens. There is no token inventory. If that changes, Mara Chen adds the inventory to the next review. Check the IdP docs for how an app prompt is enrolled. This policy does not name an enrollment API.
## Privileged access

Privileged work uses the separate `-admin` account. The daily account cannot be added to admin groups. Admin sign-in always uses MFA, including from the office LAN.

Owen Blake creates an admin account only after the manager and Mara Chen both approve the ticket. The admin password meets the 20-character choice in Password composition. Admin passwords are not stored in a personal note. The owner of the admin account may keep it in a password manager.
## Remote access

The office LAN is 10.8.0.0/24. Administration from anywhere else goes through the bastion at 192.0.2.10, which is an RFC 5737 documentation address used by this fictional lab. That path requires MFA.

Admin pages on https://portal.harbor-pine.example.com require MFA whether the person is on the LAN or not. Ordinary member use of the portal follows the MFA date in Multi-factor authentication. SSH to cooperative hosts is reached through the bastion, then to a loopback admin path on the host. Host firewall details live in the host standard, not in this password policy.
## Credential compromise

When a password or a service secret may be exposed, the sequence is fixed.

1. Disable the IdP account, or disable the service credential's use.
2. Revoke active sessions.
3. Rotate the password and every Harbor Vault secret that account could read.
4. Mail security@example.com with the account name and the time the exposure was noticed.
5. Review sign-in logs for the previous 14 days.
6. Leave a service credential disabled until the new secret is in Harbor Vault and the application has been restarted against it.

Mara Chen decides whether the policy itself needs an earlier review. The person whose password was exposed chooses a new password that meets Password composition. They do not reuse one of the last 5.
