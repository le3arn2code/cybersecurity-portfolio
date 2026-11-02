# File permissions in Linux

**Portfolio document — Google Cybersecurity Professional Certificate**
**Haroon Ur Rasheed**
Based on the *Manage authorization* lab (completed 2026-11-02, Score 4/4). All commands below are the commands actually run in that lab, as user `researcher2` in `/home/researcher2/projects`.

---

## Project description

I am a security professional working with a research team at a large organization, and part of my role is to make sure team members are authorized with the appropriate permissions on the file system. In this project, I examined the existing permissions on the files and subdirectory in the `projects` directory belonging to the `researcher2` user. Where the permissions did not match the authorization that should be given, I modified them using Linux commands to grant the appropriate users access and remove unauthorized access. This keeps the system secure by applying the principle of least privilege.

## Check file and directory details

To check the permissions on every file in the `projects` directory — including hidden files — I first navigated to the directory and then listed its contents in long format:

```bash
cd projects/
ls -la
```

The `-l` option displays the long format, which includes the permission string, owner, and group for each entry. The `-a` option displays **all** entries, including hidden files whose names begin with a dot (`.`); a plain `ls` or `ls -l` would not show those files at all.

The output showed the following current permissions. All files are owned by the user `researcher2` and the group `research_team`:

```
drwx--x---  2  researcher2  research_team  4096  drafts
-rw-rw-rw-  1  researcher2  research_team    46  project_k.txt
-rw-r-----  1  researcher2  research_team    46  project_m.txt
-rw-rw-r--  1  researcher2  research_team    46  project_r.txt
-rw-rw-r--  1  researcher2  research_team    46  project_t.txt
```

The `ls -la` output also revealed a hidden file, `.project_x.txt`, which is examined in a later section.

## Describe the permissions string

Each line of the `ls -la` output begins with a **10-character string** that describes the file type and its permissions. As an example, the string for `project_k.txt` is:

```
-rw-rw-rw-
```

- **Character 1 — file type:** `-` means this is a regular file. A `d` in this position (as in `drwx--x---` for `drafts`) means the entry is a directory.
- **Characters 2–4 — user (owner) permissions:** `rw-` means the owner, `researcher2`, can **r**ead and **w**rite the file, but cannot e**x**ecute it (`-` = permission not granted).
- **Characters 5–7 — group permissions:** `rw-` means members of the group `research_team` can also read and write the file, but not execute it.
- **Characters 8–10 — other permissions:** `rw-` means **all other users** on the system can read and write the file, but not execute it.

Reading the string this way shows the problem immediately: `project_k.txt` was writable by everyone, including users outside the research team.

## Change file permissions

The organization does not allow *others* to have write access to any files. Checking the permission strings from the step above, `project_k.txt` (`-rw-rw-rw-`) was the file granting write permission to others, so I removed it with `chmod`, the command used to change file permissions:

```bash
chmod o-w project_k.txt
```

In this command, `o` targets the **other** owner type, and `-w` removes the **w**rite permission. I verified the change by listing the directory again:

```bash
ls -la
```

The output confirmed that `project_k.txt` is now `-rw-rw-r--` — others can read the file but can no longer write to it.

*Additional fix from the same audit:* `project_m.txt` is a restricted file that the group should not be able to read or write. Its string `-rw-r-----` showed the group had read access, so I removed it with `chmod g-r project_m.txt` (`g` = group), leaving only the owner with access.

## Change file permissions on a hidden file

The research team has archived `.project_x.txt`, which is why it is a **hidden file** — its name begins with a dot, so it only appears when listing with `ls -la`. An archived file should not have write permissions for anyone, but the user and the group should still be able to read it. Checking its permissions showed that both the user and the group incorrectly had write access, so I corrected them with `chmod`:

```bash
chmod g-w .project_x.txt
chmod u-w,g-w,g+r .project_x.txt
```

In the second command, `u` targets the **user** (owner) and `g` targets the **group**; `-w` removes write from both, and `g+r` confirms the group keeps **r**ead access. (A single `chmod` command can apply several changes at once, separated by commas.) After these changes, verified again with `ls -la`, the file is read-only for the user and the group, and no one can write to it — the correct state for an archived file. Note that when working with a hidden file, the leading dot is part of the filename and must be included in the command.

## Change directory permissions

The files and directories in the `projects` directory belong to `researcher2`, and only `researcher2` should be able to access the `drafts` directory and its contents. Its permission string, `drwx--x---`, showed that the group had **execute** permission (`--x` in the group position). For a directory, execute permission is what allows a user to access the directory and its contents, so the group had unauthorized access. I removed it:

```bash
chmod g-x drafts
```

Here, `g` targets the group and `-x` removes the execute permission. Verified with `ls -la`, the directory is now `drwx------` — only the owner, `researcher2`, has any access to `drafts` and its contents.

## Summary

In this project, I audited the permissions in the `researcher2` user's `projects` directory using `ls -la`, which lists all files — including hidden files — together with their 10-character permission strings, owners, and groups. I then used `chmod` to correct every case where the permissions did not match the required authorization: removing write access for others on `project_k.txt`, removing group read access on the restricted `project_m.txt`, making the archived hidden file `.project_x.txt` read-only for the user and group, and removing group access to the `drafts` directory. After each change, I re-listed the directory to verify the new permission string before moving on. These steps ensure that only authorized users can access or modify the research team's files, which protects sensitive information and maintains the security of the system.

---

## Evidence

- Lab screenshot (Score 4/4, full terminal history of the commands above): [Lab 06 — Manage authorization](../labs/lab-06-manage-authorization.md), screenshot `labs/lab-06-screenshot.png` in this repository.
- Commands are typed in full in each section, as permitted by the activity instructions ("take a screenshot of the Linux command you used, or type this command directly into the template").

## Self-assessment coverage (activity checklist)

| # | Statement | Covered in |
|---|-----------|------------|
| 1 | Screenshots or typed versions of commands | Every section — typed commands throughout, screenshot linked under Evidence |
| 2 | Description of the project at the beginning | Project description |
| 3 | Explanations of commands and their output | Every section |
| 4 | Summary at the end | Summary |
| 5 | Details on using `chmod` to update file permissions | Change file permissions; Change file permissions on a hidden file; Change directory permissions |
| 6 | Details on checking file permissions with `ls -la` | Check file and directory details |
| 7 | Details on interpreting the 10-character permission string | Describe the permissions string |
| 8 | Details on hidden files and directories | Check file and directory details; Change file permissions on a hidden file |
