# Lab 01 — Install software in a Linux distribution

**Program:** Google Cybersecurity Professional Certificate — Google Skills
**Date completed:** 2026-11-02
**Score:** 5 / 5
**Level / duration:** Introductory, 1 hour (completed with ~28–29 min left)
**Environment:** Debian-based Linux VM, Bash shell, user `analyst`

## Objective

Use the Advanced Package Tool (APT) with `sudo` to install, uninstall, and reinstall network security applications, and verify each state from the command line.

## Tasks completed

1. **Ensure APT is installed** — ran `apt` and confirmed version/usage output.
2. **Install and uninstall nload** — installed it, verified it, removed it, and verified removal.
3. **Install tcpdump** — installed the packet-capture tool via APT.
4. **List installed applications** — used `apt list --installed` and located tcpdump in the output; nload correctly absent after uninstall.
5. **Reinstall nload** — reinstalled it and confirmed both nload and tcpdump appear in the installed list.

## Commands used (from terminal history in evidence screenshot)

```bash
apt
sudo apt install nload
nload --version
nload -h
nload -a 4
whatis nload
sudo apt remove nload
nload -h            # verified removal: /usr/bin/nload: No such file or directory
sudo apt install tcpdump
tcpdump --version
apt list --installed
sudo apt install nload -y
apt list --installed   # confirmed: nload and tcpdump both installed
history
```

## Verification

- nload install: `nload -h` / `--version` returned version and usage info (v0.7.4 in lab reference).
- nload uninstall: same command returned “No such file or directory” — removal confirmed, not assumed.
- Final state: `apt list --installed` showed both:
  - `nload/oldstable,now 0.7.4-2+b1 amd64 [installed]`
  - `tcpdump/oldstable,now 4.9.3-1~deb10u2 amd64 [installed]` (version per lab reference)
- All 5 lab checks passed: **Score 5 / 5**.

## Why this matters for a security analyst

Analysts work on Linux systems they do not own the install process for. Being able to add, remove, and *prove* the state of tools — especially traffic tools like tcpdump (packet capture) and nload (bandwidth/traffic monitoring) — is baseline SOC work: tool readiness before an investigation, and clean removal/verification afterwards.

## Portfolio blurb (copy-ready)

> Completed a hands-on Linux lab (5/5) using APT and sudo on a Debian system to install, uninstall, verify, and reinstall nload and tcpdump. Verified each change from the CLI using version/help output, expected error output after removal, and `apt list --installed` — not just installer messages.

## Evidence

- Screenshot: `~/workspace/user/media_library/image/Lab_-_1_Apt_Install_and_Install_apps.png` — Google Skills page showing Score: 5/5, Conclusion section, and full terminal `history`.
