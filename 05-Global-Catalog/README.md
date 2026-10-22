# 🌍 Lab 05: Global Catalog Verification

> Part of the **Active Directory Home Lab**

## 🎯 Objective
Check that the domain controller hosts the Global Catalog (GC).

## 📖 Concepts

The **Global Catalog** is a searchable index of objects across every domain in the forest. It helps with:
- Searching for users and objects across domains
- Resolving universal group memberships during logon
- Logging on with a user principal name (UPN), such as `user@khader.local`

## 🛠️ What I Did

1. Opened **Active Directory Sites and Services** from Server Manager → Tools.
2. Expanded: `Sites → Default-First-Site-Name → Servers → DC01`.
3. Right-clicked **NTDS Settings** and opened **Properties**.
4. Confirmed that **Global Catalog** is checked.

I also confirmed the DC type in the server's properties: **Global Catalog**.

## ⌨️ Commands Used

No commands were needed. This check was done through the GUI.

## 📸 Screenshots

| File | What It Shows |
|---|---|
| `assets/01-Global-Catalog-Enabled.png` | NTDS Settings showing Global Catalog enabled on `DC01` |

## 💡 Key Takeaways

- In a single-DC lab, `DC01` must be a Global Catalog server. Otherwise domain logons can fail.
- Don't uncheck the Global Catalog option on the only domain controller.
