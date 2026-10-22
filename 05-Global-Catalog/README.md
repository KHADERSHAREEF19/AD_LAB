# 👤 Lab 05: AD User Creation and Authentication Test

> Part of the **Active Directory Home Lab**

## 🎯 Objective
Create a domain user in Active Directory, then confirm the user can sign in with domain credentials.

## 👥 User Details

| Field | Value |
|---|---|
| Full Name | Elon Musk |
| User Logon Name | `Emusk` |
| UPN | `Emusk@khader.local` |
| Pre-Windows 2000 Logon | `KHADER\Emusk` |
| Account Expires | Never |

## 🛠️ What I Did

1. Opened **Active Directory Users and Computers** from Server Manager → Tools.
2. Right-clicked `khader.local → Users → New → User`.
3. Entered the user details and set a password.
4. Checked the account properties to confirm the logon names and expiry settings.
5. Tried to sign in as `KHADER\Emusk` on DC01. Windows blocked it, because standard users can't log on locally to a domain controller by default.
6. **Lab-only workaround:** Added `Emusk` to the **Allow log on locally** policy in the Default Domain Controllers Policy, then ran `gpupdate /force`.
7. Signed in as `KHADER\Emusk` and confirmed the account with `whoami`.
8. **Cleanup:** Removed `Emusk` from the workaround policy after testing.

## ⌨️ Commands Used

**Open Group Policy Management:**
```cmd
gpmc.msc
```
*Plain English:* Opens the Group Policy Management console.

**Apply policy changes right away:**
```cmd
gpupdate /force
```
*Plain English:* Forces the computer to reload its Group Policy settings immediately.

**Confirm the logged-in user:**
```cmd
whoami
```
*Plain English:* Shows the account you are currently signed in with. The expected output is `khader\emusk`.

## 🔍 Verification Checklist

- [x] User `Emusk` exists in `khader.local → Users`.
- [x] `whoami` shows `khader\emusk` after sign-in.
- [ ] Domain join on a separate Windows 10/11 Pro client VM (**pending**).

## 📸 Screenshots

| File | What It Shows |
|---|---|
| `assets/01-AD-User-Creation.png` | User properties for `Emusk` |
| `assets/03-Domain-User-Authentication.png` | `whoami` output showing `khader\emusk` |

## 💡 Key Takeaways

- Normal domain users should sign in to client computers, not domain controllers.
- Allowing local logon on a domain controller is a security risk. Use it only in an isolated lab, and remove it afterward.
- The correct test is joining a client VM to the domain and signing in there. That is the next step for this lab.
