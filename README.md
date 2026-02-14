## Script Descriptions

### AD-First5.ps1
**Target System:** `svc-ad-01` (Domain Controller)

Purpose:
- Identify unauthorized privileged users
- Detect persistence mechanisms
- Review recent domain activity
- Enable authentication auditing

---

### WIN-Harden.ps1
**Target System:** `cell-win-03` (Secondary Windows Server)

Purpose
- Detect persistence mechanisms
- Reduce attack surface
- Ensure firewall protection
- Review recent login activity

---

## Requirements

Both scripts require:

- Local Administrator privileges
- PowerShell access
- Active Directory module installed (for `AD-First5.ps1`)

---

## How to Run

### Step 1 — Open Administrator PowerShell

On the target machine:

Search for **PowerShell**

Right-click → **Run as Administrator**

---

### Step 2 — Allow Script Execution (Temporary)

Run: Set-ExecutionPolicy Bypass -Scope Process


This allows the script to run without permanently modifying system policy.

---

### Step 3 — Execute Script

#### On svc-ad-01

Navigate to script location and run: PowerShell -ExecutionPolicy Bypass -File AD-First5.ps1


---

#### On cell-win-03

Navigate to script location and run: PowerShell -ExecutionPolicy Bypass -File WIN-Harden.ps1

---

## Output Interpretation

If the script displays:

- Unknown admin users → escalate immediately  
- Recently created accounts → review legitimacy  
- Suspicious scheduled tasks → investigate  
- Unexpected automatic services → investigate  

The scripts do **not remove anything automatically**.  
All remediation decisions are left to the operator.

---

## Safety Notes

These scripts are:

- Idempotent (safe to run multiple times)
- Non-destructive
- Designed for visibility first, enforcement second

They will not:

- Remove users
- Disable domain functionality
- Patch systems
- Reboot machines

---

## When to Use

Run immediately:

- After initial login
- After password rotation
- Before deep investigation
- Before applying patches or major changes

---

## Troubleshooting

If the script fails, check:

- Administrator privileges
- Active Directory module availability (for AD script)
- PowerShell execution policy
