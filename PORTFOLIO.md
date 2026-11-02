# Google Cybersecurity Professional Certificate — Portfolio
**Haroon Ur Rasheed**

This portfolio logs each completed lab/activity from the Google Cybersecurity Professional Certificate (via Google Skills / Coursera) as portfolio-ready evidence: what was done, the exact commands/tools used, how it was verified, and why it matters for a security analyst role.

Chat dedicated to this portfolio: **Google Cybersecurity Professional Portfolio** (started 2026-11-02)

---

## Completed labs

| # | Date | Lab | Score | Key tools / skills |
|---|------|-----|-------|--------------------|
| 1 | 2026-11-02 | Install software in a Linux distribution | 5 / 5 | APT, sudo, Bash, nload, tcpdump, apt list --installed |
| 2 | 2026-11-02 | Examine input/output in the Linux shell | 3 / 3 | Bash I/O, echo, expr, clear, quoted strings |
| 3 | 2026-11-02 | Find files with Linux commands | 4 / 4 | pwd, ls, cd, cat, head, grep, pipes |
| 4 | 2026-11-02 | Filter with grep | 3 / 3 | grep, pipes (ls \| grep, cat \| grep), quoted multi-word search |
| 5 | 2026-11-02 | Manage files with Linux commands | 6 / 6 | mkdir, rmdir, mv, rm, touch, nano, ls -ltrh |
| 6 | 2026-11-02 | Manage authorization | 4 / 4 | ls -la, chmod (o-w, g-r, u-w/g-w/g+r, g-x), hidden files, least privilege |

---

## Lab index

- [Lab 01 — Install software in a Linux distribution (APT)](labs/lab-01-apt-install-software.md)
- [Lab 02 — Examine input/output in the Linux shell](labs/lab-02-examine-input-output-linux-shell.md)
- [Lab 03 — Find files with Linux commands](labs/lab-03-find-files-linux-commands.md)
- [Lab 04 — Filter with grep](labs/lab-04-filter-with-grep.md)
- [Lab 05 — Manage files with Linux commands](labs/lab-05-manage-files-linux-commands.md)
- [Lab 06 — Manage authorization](labs/lab-06-manage-authorization.md)

## Portfolio documents (course portfolio activities)

- [File permissions in Linux](portfolio-documents/file-permissions-in-linux.md) — from Lab 06 (Manage authorization). Practice assignment due 2026-11-11. Covers project description, `ls -la`, the 10-character permission string, `chmod` on a file, a hidden file, and a directory, and a summary — all 8 self-assessment points.

**Hosting:** GitHub repository (Option 4 in the course reading). Suggested setup: ONE repo named `google-cybersecurity-portfolio` under `le3arn2code` containing this whole folder (README.md is the repo landing page) — not a new repo per lab, given the number of existing course-lab repos.

## Skills demonstrated so far

- Linux package management with APT on a Debian-based system
- Installing, uninstalling, and reinstalling applications with `sudo`
- Verifying installs/uninstalls from the command line (`-h`, `--version`, error output, `apt list --installed`)
- Working with network-monitoring / packet-capture tools: **nload** and **tcpdump**
- Bash input/output fundamentals: `echo` (quoted/unquoted strings), `expr` (integer calculations), `clear`
- Quick analyst triage maths in the shell (false-positive counts, scaling monthly figures to yearly)
- File system navigation and file reading: `pwd`, `ls`, `cd` (relative and absolute paths), `cat`, `head` (including `head -n`)
- Searching log content with `grep` (`-i`, `-c`) and piping command output (`head ... | grep ...`)
- Extracting answers from file data: user/department/employee-ID lookup, warning counts in server logs
- Filtering with `grep` as a primary tool: content search in logs and user files, filename filtering via `ls | grep`, quoted multi-word strings (`grep "Human Resources"`), counting matches (errors, Q1/access files, department additions)
- File/directory management: `mkdir`, `rmdir`, `mv`, `rm`, `touch`, editing with **nano** (save-on-exit flow), detailed listings with `ls -ltrh`, and verify-after-every-change discipline
- Authorization / permissions: reading the 10-character permission string (`ls -la`), symbolic `chmod` for user/group/other (add/remove r/w/x, incl. combined `u-w,g-w,g+r`), hidden-file permissions, directory execute/traverse control, least-privilege fixes

## Evidence

- Lab 01 screenshot (Score: 5/5, terminal history visible): `~/workspace/user/media_library/image/Lab_-_1_Apt_Install_and_Install_apps.png`
- Lab 02 primary screenshot — clean exemplar (Score: 3/3, 11-command history): `~/workspace/user/media_library/image/image-7.png`, copy at `labs/lab-02-exemplar-screenshot.png`. Earlier fuzzy screenshot of his own run (20 commands): `image-6.png` — kept as supporting evidence.
- Lab 03 screenshot — exemplar page (Score: 4/4, 18-command history): `~/workspace/user/media_library/image/image-8.png`, copy at `labs/lab-03-screenshot.png`.
- Lab 04 primary screenshot — clean exemplar (Score: 3/3, 15-command history): `~/workspace/user/media_library/image/image-10.png`, copy at `labs/lab-04-exemplar-screenshot.png`. His own run (history lines 5–36): `image-9.png`, copy at `labs/lab-04-screenshot.png` — kept as supporting evidence.
- Lab 05 screenshot — his own run (Score: 6/6, history lines 2–33): `~/workspace/user/media_library/image/image-11.png`, copy at `labs/lab-05-screenshot.png`.
- Lab 06 screenshot — his own run (Score: 4/4, full 22-command history): `~/workspace/user/media_library/image/image-12.png`, copy at `labs/lab-06-screenshot.png`.

---
*Next lab: send the screenshot + lab text in this chat and it will be added here in the same format.*
