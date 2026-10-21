# Password and access basics (template)

Six sections from the full policy: scope, composition, multi-factor authentication, privileged access, remote access, and compromise. Decision tokens stay in backticks. Replace them with values you choose. Read NIST Special Publication 800-63B, and check your identity provider's documentation, before you copy a number or a setting name. Mailboxes in the notes use example.com. The filled excerpt names Harbor & Pine Cooperative.

## Purpose and scope

State who receives an account and which systems those accounts can reach. Cover employees and contractors, the identity provider, the applications they sign in to, the office LAN, and any bastion you use for administration. Say that people follow this policy when they choose a password, ask for access, or leave, and that operators follow it when they create accounts and review sign-ins.

Keep the scope list short enough that a new hire can see whether a system is included. Add a system by editing this section, not by a side conversation.
## Password composition

A daily password is at least `ORG_MIN_LENGTH` characters. A privileged password is at least `ORG_ADMIN_MIN_LENGTH` characters. Both are organization choices. Read NIST Special Publication 800-63B before treating either number as a published minimum. Require the identity provider to accept at least 64 characters. Allow spaces. Do not require a mix of character classes.

Allow a password manager and allow paste on the sign-in page. Check new passwords against the identity provider's banned-password list. How that list is loaded is vendor-specific. Check the identity provider's documentation. This template does not name a vendor or an API field.

Sign-in throttling is `ORG_LOCKOUT`. Write the failure count and the lock duration you will configure. Check the IdP docs for the setting name.
## Multi-factor authentication

Require a second factor now for remote access and for every privileged sign-in. Name the factor you actually enroll. The filled example uses an identity-provider app prompt and issues no hardware tokens.

From `ORG_MFA_DATE`, require that second factor for every account, including sign-ins from the office LAN. Check the IdP docs for how the factor is enrolled. This template does not name an enrollment API.
## Privileged access

Privileged work uses the separate admin account. The daily account cannot be added to admin groups. Admin sign-in uses MFA, including from the office LAN.

Create an admin account only after the manager and the policy owner both approve the ticket. The admin password meets `ORG_ADMIN_MIN_LENGTH`. The owner may keep it in a password manager. It does not go into a personal note or a ticket.
## Remote access

Define the office LAN, and say that administration from anywhere else goes through a named bastion and requires MFA. Use an address from your own inventory. The filled example uses the RFC 5737 documentation address 192.0.2.10 and the RFC 1918 LAN 10.8.0.0/24 because the cooperative is fictional.

Admin pages require MFA on the LAN and off it. Ordinary application use follows the date `ORG_MFA_DATE`. Point SSH for administrators through the bastion. Keep host-firewall detail in the host standard.
## Credential compromise

Write the sequence and follow it in order.

1. Disable the account, or disable the service credential's use.
2. Revoke active sessions.
3. Rotate the password and every secret that account could read.
4. Notify the policy owner with the account name and the time the exposure was noticed.
5. Review sign-in logs for the previous 14 days.
6. Leave a service credential disabled until the new secret is stored and the application uses it.

The person whose password was exposed chooses a new one that meets Password composition, and does not reuse one of the last `ORG_HISTORY_DEPTH` passwords. The policy owner decides whether this policy needs an earlier review.
