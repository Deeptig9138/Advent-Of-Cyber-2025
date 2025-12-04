# 🎄 Advent of Cyber 2025 — Linux CLI: Shells Bells  

## 🎅 Task 1: Introduction

The unthinkable has happened — **McSkidy has been kidnapped**. Without her, Wareville’s defenses are weakening, and Christmas hangs by a thread. The TBFC (The Best Festival Company) team begins scrambling for clues, and their investigation points to **tbfc-web01**, a Linux server processing Christmas wishlists.

Somewhere inside this server may lie:

- traces of McSkidy’s final actions  
- signs of intrusion  
- clues revealing King Malhare’s twisted vision for **EASTMAS**

Your mission begins now.

---

## 🎯 Learning Objectives

- Understand the basics of the **Linux Command-Line Interface (CLI)**  
- Learn how the CLI is used for personal and administrative tasks  
- Apply CLI knowledge to uncover the **mysteries of Christmas**

To begin, click **Start Machine** on TryHackMe. Once the virtual machine loads, you'll access the terminal — your **Linux CLI**.  
You can also SSH into the machine using the provided credentials (if connected through the THM VPN).

---

# ❄️ Task 2: Linux CLI

There is no GUI on this server — but that’s okay! Linux's CLI is powerful enough to manage everything using commands.

Run your first commands:
```
echo "Hello World!"
ls
cat README.txt
```


- `echo` displays text  
- `ls` lists files  
- `cat` shows file contents  

---

## 📁 Navigating the Filesystem

McSkidy left behind a **security guide**, but it seems hidden. Begin by navigating directories:
```
cd Guides
ls
```

Although the directory appears empty… something is hiding.

---

## 👀 Looking for the Hidden Guide

In Linux, files beginning with a dot (`.`) are **hidden**.

Reveal them: `ls -la`
The -a flag shows the hidden files. The -l flag shows the additional details, such as file permissions and file owner.

Read the hidden guide: `cat .guide.txt`

![Output1](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc1.png)
---

## 🔎 Grepping the Logs

McSkidy’s guide mentions `/var/log/`, the home for Linux security logs.

Navigate and inspect failed login attempts:
```
cd /var/log
ls
grep "Failed password" auth.log
```

This reveals multiple failed logins from **HopSec** targeting the `socmas` account. Suspicious…

---

## 🥚 Finding the Files (Egg Hunt)

Look for malicious files left behind: `find /home/socmas -name egg`


This reveals the file: `eggstrike.sh`

![Output2](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc2.png)

---

## 📜 Analyzing the Eggstrike Script

The `eggstrike.sh` script contains commands that:

1. The lines starting with # are just comments and are not the actual commands.
2. The cat wishlist.txt | sort | uniq lists unique items from the wishlist.txt.
3. The command then sends the output (unique orders) to the /tmp/dump.txt file.
4. The rm wishlist.txt deletes the wishlist file (containing Christmas wishes).
5. The mv eastmas.txt wishlist.txt replaces the original file with eastmas.txt.

Carrotbane is sabotaging Christmas wishes!

---

## ⚙️ CLI Features & Special Symbols

| Symbol | Meaning | Example |
|--------|----------|---------|
| `>` / `>>` | Output redirection (overwrite / append) | `echo hi > output.txt` |
| `&&` | Run next command only if previous succeeded | `grep "flag" file && echo "Found"` |
```
`|` - Pipe: send output from one command to another - `cat file | sort` 
```
---

## 🥕 Sir Carrotbane Attacks

You can view the sabotaged wishlist by visiting: `http://10.49.171.49:8080` (from the VM browser)

---

## 🛠️ System Utilities

Useful system commands:
```
uptime - to see how much time your system is running
ip addr - to check your IP address
ps aux - to list all processes
cat /etc/shadow (root only)
```

---

## 👑 Root User

To become root:
```
sudo su
whoami
```

Root has full control of the system — the primary target for attackers.

---

## 📜 Bash History

Every command is saved in the user’s bash history:
```
history
cat .bash_history
```

Check root’s history too (once elevated): `cat /root/.bash_history`

![Output3](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc3.png)

---

# 📝 Questions & Answers  

**Q1) Which CLI command would you use to list a directory?**  
**A:** `ls`

**Q2) What flag did you see inside McSkidy's guide?**  
**A:** `THM{learning-linux-cli}`

**Q3) Which command helped you filter logs for failed logins?**  
**A:** `grep`

**Q4) What flag did you see inside the Eggstrike script?**  
**A:** `THM{sir-carrotbane-attacks}`

**Q5) Which command would you run to switch to the root user?**  
**A:** `sudo su`

**Q6) What flag did Sir Carrotbane leave in the root bash history?**  
**A:** `THM{until-we-meet-again}`

---

# 🗝️ Bonus: Side Quest Access

If you're feeling confident, search for McSkidy’s hidden note: `/home/mcskidy/Documents/`

It contains a key for **Side Quest 1**  
*(Side Quest content will be uploaded in a separate `.md` file once completed.)*

---

🎄 **End of Shells Bells — Good job stepping into the world of Linux CLI!**  

![Linux-CLI](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/Linux-CLI.png)
