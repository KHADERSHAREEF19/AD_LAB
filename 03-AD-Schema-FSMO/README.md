# 🧬 Lab 03: AD Schema and FSMO Roles

> Part of the **Active Directory Home Lab**

## 🎯 Objective
Learn how Active Directory defines its objects (the schema), and check which domain controller holds the key admin roles (FSMO).

## 📖 Concepts

- **Schema:** The blueprint of Active Directory. It defines classes (User, Computer, Group) and attributes (phone number, email, and so on).
- **OID (Object Identifier):** A unique ID that every schema object needs.
- **FSMO roles:** Five special roles that only one domain controller can hold at a time.

## 🛠️ What I Did

1. Registered the schema snap-in so it can be added to MMC.
2. Opened MMC and added **Active Directory Schema**.
3. Explored the **Classes** and **Attributes** folders.
4. Checked an attribute's properties, including the *Replicate this attribute to the Global Catalog* option.
5. Checked which server holds the FSMO roles.
6. Walked through the course's attribute creation demo, but did not keep any custom attribute in the lab.

## ⌨️ Commands Used

**Register the schema snap-in** (run in Command Prompt as Administrator):
```cmd
regsvr32 schmmgmt.dll
```
*Plain English:* Registers the Schema snap-in so MMC can load it. A success message means it worked.

**Open MMC:**
```cmd
mmc
```
*Plain English:* Opens the Microsoft Management Console, where you add snap-ins.

**Check the FSMO role holders:**
```cmd
netdom query fsmo
```
*Plain English:* Lists which domain controller holds each of the five FSMO roles.

## 📊 FSMO Role Results

| Role | Holder |
|---|---|
| Schema Master | `DC01.khader.local` |
| Domain Naming Master | `DC01.khader.local` |
| PDC Emulator | `DC01.khader.local` |
| RID Master | `DC01.khader.local` |
| Infrastructure Master | `DC01.khader.local` |

With only one domain controller, it holds all five roles.

## 📸 Screenshots

| File | What It Shows |
|---|---|
| `assets/01-AD-Schema-Overview.png` | Schema snap-in showing Classes and Attributes |
| `assets/02-FSMO-Roles.png` | `netdom query fsmo` output |
| `assets/03-Attribute-Creation-1.png` | Course demo of creating a schema attribute |
| `assets/04-Attribute-Creation-2.png` | Course demo of attribute details |

## 💡 Key Takeaways

- Schema changes affect the entire forest and can't be undone easily. Take a VM snapshot before changing the schema.
- Every custom schema attribute needs a unique OID. Random numbers won't work.
- Keep the Schema Master role on a well-protected domain controller in production.
