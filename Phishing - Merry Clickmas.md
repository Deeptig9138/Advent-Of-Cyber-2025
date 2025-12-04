# 🎄 Advent of Cyber 2025 — **Phishing: Merry Clickmas**

## 🧵 Task 1: Introduction

Recent cyber threats against **The Best Festival Company (TBFC)** have prompted the local red team to conduct multiple penetration tests. Their goal: assess employee awareness regarding **phishing attacks**.

In this challenge, you will join the TBFC red team—working alongside Recon McRed, Exploit McRed, and Pivot McRed—to plan and execute a realistic phishing campaign. Your task is to determine whether more cybersecurity training is needed before EASTMAS.

---

## 🎯 Learning Objectives

- Understand **social engineering**
- Learn different types of **phishing**
- Explore how red teams build **fake login portals**
- Use the **Social-Engineer Toolkit (SET)** to send a phishing email

---

## 🖥️ Setting Up Your Virtual Environment

To successfully complete this room, you'll need to set up your virtual environment. This involves starting both your AttackBox (if you're not using your VPN) and Target Machines, ensuring you're equipped with the necessary tools and access to tackle the challenges ahead:

- **Target VM** → via the **Start Machine** button  
- **AttackBox** → via the **Start AttackBox** button  

If split view doesn’t appear, click **Show Split View**.

---

# 🪤 Task 2: Phishing Exercise for TBFC

## 🧠 Social Engineering

**Social engineering** involves manipulating a human into making a mistake. These mistakes may include:

- giving away a password  
- opening a malicious file  
- approving a fraudulent payment  

Attackers use psychological triggers such as **urgency**, **curiosity**, and **authority**. This is why social engineering is often called **“human hacking.”**

---

## 🎣 What is Phishing?

**Phishing** is a form of social engineering using messages as the attack vector.  
It can occur via:

- Email  
- SMS (**smishing**)  
- Voice calls (**vishing**)  
- QR codes (**quishing**)  
- Social media DMs  

TBFC teaches two S.T.O.P. mnemonics:

### **S.T.O.P. — All Things Secured**
- **Suspicious?**  
- **Telling me** to click something?  
- **Offering me** a deal?  
- **Pushing me** to act urgently?

### **S.T.O.P — TBFC Awareness**
- **Slow down**  
- **Type the address manually**  
- **Open nothing unexpected**  
- **Prove the sender**

---

## 🕸️ Building the Trap — Fake TBFC Login Page

To conduct the phishing test, the red team needs:

1. A **fake login portal**  
2. A way to **capture credentials**  
3. A method to **deliver the phishing email**

The AttackBox already contains a ready-to-use fake login server.

**Navigate to:**

```
cd ~/Rooms/AoC2025/Day02
./server.py
```

**Output:**

![output](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc4.png)

**View the phishing login page using Firefox:** `http://10.49.114.64:8000 (Target IP)` or `http://127.0.0.1:8000`

![page](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc5.png)

---

## 📬 Sending the Phishing Email Using SET

**Start SET:** `setoolkit`
```
Choose the following options:

1) Social-Engineering Attacks
5) Mass Mailer Attack
1) E-Mail Attack Single Email Address
```

**Then fill out:**

- Send email to	factory@wareville.thm
- Delivery method	Use your own server / open relay
- From address updates@flyingdeer.thm
- From name	Flying Deer
- SMTP server	MACHINE_IP
- Port	25
- High priority?	no
- Attach a file?	n
- Inline file?	n
- Subject	Shipping Schedule Changes
- Body Include the phishing URL: http://10.49.114.64:8000

![setoolkit](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc6.png)

**Example message body:**
```
Dear elves,
Kindly note that there have been significant changes to the shipping schedules due to increased shipping orders.
Please confirm the new schedule by visiting http://10.49.114.64:8000
Best regards,
Flying Deer
END
```

**SET will confirm:** `[*] SET has finished sending the emails`

---

## 🔐 Capturing Credentials

Check the terminal where server.py is running.
Within 1–2 minutes, captured credentials will appear if the target falls for the phishing attempt.

The red team successfully harvested one working credential, meaning TBFC employees remain vulnerable to phishing.

![server](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc7.png)

---

# **📝 Questions & Answers**
**Q1: What is the password used to access the TBFC portal?**

**A:** unranked-wisdom-anthem

![page](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc8.png)

**Q2: What is the total number of toys expected for delivery? Browse to http://MACHINE_IP, log in as factory using the harvested admin password.**

**A:** 1984000

![inside](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/aoc9.png)

---

🎄 **End of Merry Clickmas — You’ve completed the phishing operation!**

![Phishing](https://github.com/Deeptig9138/Advent-Of-Cyber-2025/blob/main/Images/Phishing.png)
