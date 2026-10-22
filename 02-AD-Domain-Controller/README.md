# 🏢 Lab 02: Active Directory Domain Services (AD DS) Deployment

> Part of the **Active Directory Home Lab**

## 🎯 Objective
Turn the Windows Server 2016 VM into a domain controller for the domain `khader.local`.

## 🌐 Lab Environment

| Item | Value |
|---|---|
| Server Name | `DC01` |
| Full DNS Name | `DC01.khader.local` |
| Domain | `khader.local` |
| Static IPv4 Address | `172.16.0.10` |
| Subnet Mask | `255.255.0.0` |
| Preferred DNS | `127.0.0.1` (loopback, as shown in the course) |
| Site | Default-First-Site-Name |

## 🛠️ What I Did

1. **Renamed the computer** to `DC01` from Server Manager.
2. **Changed the IP address** from DHCP (automatic) to static, so the server's address never changes.
3. **Set the DNS server** to the loopback address, so the server uses its own DNS service.
4. **Installed the AD DS role** using Server Manager → Manage → Add Roles and Features.
5. **Promoted the server** using *Add a new forest* with the root domain `khader.local`.
6. **Set a DSRM password.** This is a separate recovery password and is not stored here.
7. **Verified the installation** using Active Directory Users and Computers, DNS, and the shared folders.

## ⌨️ Commands Used

**Verify the shared folders:**
```text
Win + R → \\DC01
```
You should see `NETLOGON` and `SYSVOL`.

**Reference only (not run):** The course also shows PowerShell commands for the same job. I did not run these, because the server was already configured.
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```
```powershell
Install-ADDSForest -DomainName "khader.local" -InstallDNS
```

## 🔍 Verification Checklist

- [x] `DC01` appears in Active Directory Users and Computers under `khader.local`.
- [x] The `_ldap` SRV record appears under `_msdcs → dc → _tcp` in DNS Manager.
- [x] `\\DC01` shows `NETLOGON` and `SYSVOL`.

## 📸 Screenshots

| File | What It Shows |
|---|---|
| `assets/01-ADUC-Verification.png` | Active Directory Users and Computers showing `khader.local` |
| `assets/02-DNS-Verification.png` | DNS Manager with the `_ldap` SRV record |
| `assets/03-SYSVOL-NETLOGON.png` | `\\DC01` showing `NETLOGON` and `SYSVOL` |
| `assets/04-ADDS-Role-Assigned.png` | AD DS role selected in the Add Roles wizard |
| `assets/05-ADDS-Installation-Complete.png` | Installation succeeded |
| `assets/06-Domain-Controller-Promotion.png` | Domain Controller Options during promotion |

## 💡 Key Takeaways

- A domain controller needs a static IP. If the address changes, clients can't find the domain.
- The DNS server is what clients use to find the domain controller. Clients should point to the DC's real IP address, not `127.0.0.1`.
- `.local` works for a lab, but real companies usually use a domain they own.
