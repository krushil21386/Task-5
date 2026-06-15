# Social Engineering Attacks: Research Report

**Prepared by:** Alian  
**Institution:** Charotar University of Science and Technology (CHARUSAT)  
**Program:** B.Tech Information Technology  
**Internship Task:** Task 5 — Social Engineering Attacks  
**Date:** June 2026

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Introduction](#2-introduction)
3. [Types of Social Engineering Attacks](#3-types-of-social-engineering-attacks)
   - 3.1 Phishing
   - 3.2 Spear Phishing and Vishing
   - 3.3 Pretexting
   - 3.4 Baiting
   - 3.5 Business Email Compromise (BEC)
   - 3.6 Quid Pro Quo and Tailgating
4. [Psychological Triggers Attackers Rely On](#4-psychological-triggers-attackers-rely-on)
5. [Real-World Case Studies](#5-real-world-case-studies)
   - 5.1 Twitter Account Hijacking (2020)
   - 5.2 MGM Resorts and Caesars Entertainment (2023)
   - 5.3 Arup Deepfake Fraud (2024)
   - 5.4 Stuxnet and the USB Drop (2010)
   - 5.5 Microsoft 365 AiTM Phishing (2023)
6. [Key Statistics](#6-key-statistics)
7. [Organizational Impact](#7-organizational-impact)
8. [Prevention Strategies](#8-prevention-strategies)
9. [Framework Alignment](#9-framework-alignment)
10. [Conclusion](#10-conclusion)
11. [References](#11-references)

---

## 1. Executive Summary

When most people think about cyberattacks, they picture hackers breaking through firewalls or exploiting zero-day vulnerabilities. The reality is far less cinematic. A huge chunk of successful breaches happen because someone picked up a phone call, clicked a link in an email, or plugged in a USB drive they found on the floor. That's social engineering — and it's consistently one of the top causes of data breaches globally.

This report covers the main types of social engineering attacks: phishing, pretexting, and baiting, along with several related variants. Five documented incidents are analyzed to understand how these attacks actually played out, what went wrong, and what organizations learned. The report ends with practical prevention measures mapped against NIST CSF 2.0, ISO/IEC 27001, and CIS Controls v8.

A few numbers worth keeping in mind:
- Phishing was behind **44% of social engineering breaches in 2024** according to the Verizon DBIR.
- Pretexting actually surpassed phishing for the first time, making up **over 50% of social engineering incidents**.
- Business Email Compromise alone caused **$2.77 billion in losses** in 2024 (FBI IC3).
- Vishing — phone-based social engineering — shot up by **442%** in the second half of 2024.
- More than **80% of phishing emails** are now written or assisted by AI tools.

These are not small numbers. They make the case that the human side of security deserves at least as much attention as the technical side.

---

## 2. Introduction

There's a quote from Kevin Mitnick, one of the most well-known hackers in history, that stuck with me when I first read it during this internship: "Companies spend millions of dollars on firewalls, encryption, and secure access devices, and it's money wasted because none of these measures address the weakest link in the security chain — the people." He spent years breaking into organizations not by cracking code, but by talking his way in.

Social engineering is basically that — manipulating people rather than systems. It doesn't require technical skill at the level of writing exploits. What it requires is understanding how people think, what they're likely to trust, and how to create a situation where the target makes a decision they wouldn't normally make.

What makes this especially concerning right now is that AI tools have made it easier than ever to pull off convincing attacks. Phishing emails used to be easy to spot — bad grammar, weird sender addresses, generic greetings. Today, attackers can generate a personalized, grammatically perfect email in seconds. They can clone someone's voice from a few seconds of audio. They can create deepfake video of a CEO giving instructions. The technical barrier is gone; the psychological barrier is what matters.

This report is an attempt to understand these attacks properly — not just define them, but look at how they've been used in real incidents, what damage they caused, and what we can do about it.

---

## 3. Types of Social Engineering Attacks

### 3.1 Phishing

Phishing is probably the most well-known social engineering attack, and for good reason — it's everywhere. The basic idea is simple: an attacker sends an email that looks like it's from a trusted source (your bank, your IT department, a delivery service), and tries to get you to either click a link, open an attachment, or hand over your credentials.

What makes phishing effective isn't that it fools experts. It's that it's sent to thousands or millions of people at once, and only a small percentage need to fall for it. Even a 1% success rate on a campaign targeting 100,000 inboxes is 1,000 compromised accounts.

**A typical phishing flow:**

1. Attacker registers a domain that looks like the real thing — `paypa1.com` instead of `paypal.com`, or `security-microsoft-support.com`.
2. They send an email with a sense of urgency: "Your account has been locked. Verify immediately."
3. The link goes to a cloned login page. The victim enters credentials.
4. Those credentials are captured and used — either directly or sold.

**Variants worth knowing:**
- **Clone Phishing** — The attacker takes a legitimate email you received before and resends it with links swapped out for malicious ones.
- **Whaling** — Phishing that targets executives specifically, because they have more access and their approval carries more weight.
- **Smishing** — Same concept but via SMS. Fake toll payment scams using this method grew by 2,900% between 2023 and 2024.
- **Quishing** — QR codes that redirect to phishing pages. These are tricky because most people don't scrutinize QR codes the way they do URLs.

### 3.2 Spear Phishing and Vishing

Regular phishing is a numbers game. Spear phishing is the opposite — it's targeted, researched, and often frighteningly personal. The attacker spends time on LinkedIn, the company website, and social media to learn the target's name, role, manager, current projects, and even their communication style. Then they craft a message that references something real. "Hi Rahul, following up on the procurement discussion from last Tuesday's call" hits very differently than "Dear Customer."

Vishing takes this to the phone. The attacker calls and impersonates someone — IT support, a bank's fraud department, a colleague. Voice-based attacks are harder for people to evaluate in the moment because there's social pressure to respond in real time. You can re-read an email and spot something suspicious. On a call, you're expected to respond immediately.

Vishing detections increased 442% in the second half of 2024. Part of that is because email filters have gotten better, so attackers are moving to channels that are harder to filter automatically. And AI voice synthesis means they don't even need to be good actors anymore — they can clone a real person's voice.

### 3.3 Pretexting

Pretexting is about building a believable story. The attacker doesn't just say "I'm from IT" — they have answers ready for follow-up questions, they know the company's internal terminology, they've done their homework. The "pretext" is the fictional backstory that makes the request seem legitimate.

What's notable is that in the 2024 Verizon DBIR, pretexting overtook phishing as the most common social engineering method — accounting for more than 50% of incidents. That's a significant shift. It suggests that as email-based attacks get filtered more aggressively, attackers are investing more in human-to-human deception.

Some common pretexting scenarios:

| Who the attacker pretends to be | What they ask for | What they're really after |
|---|---|---|
| IT helpdesk | "Can you confirm your password so we can fix the VPN?" | Login credentials |
| HR or payroll | "We need to update your direct deposit information" | Banking details |
| Vendor or supplier | "Please confirm your account number for the next payment" | Financial account data |
| External auditor | "I need access to the server room for a compliance check" | Physical access to systems |

The attacks in the MGM and Caesars case studies (covered in Section 5) are textbook pretexting — and they worked against two multi-billion dollar companies.

### 3.4 Baiting

Baiting works by dangling something people want — free software, confidential files, a prize — and hiding a payload inside it. The name comes from fishing. You put something tempting on the hook, wait for someone to bite, and reel them in.

**Physical baiting — USB drives:**  
This is the most well-documented physical form. An attacker leaves infected USB drives somewhere employees will find them — parking lots, lobbies, bathrooms, desks. Labels like "HR Salaries Q3 - Confidential" make people even more likely to plug them in out of curiosity.

A 2016 study at the University of Illinois dropped 297 USB drives around a campus. 98% were picked up. Around 45% led to file openings that would have triggered a malware payload. That's not a small number — nearly half of people who found these drives did exactly what an attacker would want.

**Digital baiting:**  
This includes fake software downloads ("Get Adobe Premiere Pro for free!"), fake antivirus popups, fraudulent update notifications, and malicious ads on legitimate websites. The mechanism is the same — make the target take an action by offering something they want.

**Notable baiting incidents:**
- In 2010, Stuxnet malware was delivered to Iranian nuclear facilities via infected USB drives — one of the most consequential cyberattacks in history (covered in Section 5.4).
- In 2017, scammers mailed USB drives to Australian small businesses claiming they contained tax documents from the Australian Taxation Office. Plugging them in installed credential-stealing malware.

### 3.5 Business Email Compromise (BEC)

BEC is worth treating separately because of the financial damage involved. The basic setup: an attacker either hacks into a real corporate email account or creates a convincing spoofed version, then uses it to impersonate someone trusted — a CEO, CFO, or vendor — and request a wire transfer or sensitive data.

The FBI IC3 recorded 21,442 BEC complaints in 2024, with total losses of $2.77 billion. That's an average of around $129,000 per complaint. What makes BEC particularly dangerous is that the emails often come from a real account, so technical email filters don't catch them. The defense has to be procedural.

AI has made BEC significantly worse. Attackers can now generate convincing impersonation emails instantly, and deepfake audio/video means the follow-up "confirmation call" can also be faked (see the Arup case in Section 5.3).

### 3.6 Quid Pro Quo and Tailgating

**Quid pro quo** is basically a social engineering trade offer. The attacker contacts someone — often cold-calling IT staff or regular employees — and offers to help with something. "I noticed your computer has been slow, let me run a quick diagnostic." Once the victim agrees to the help, they're led to install remote access software or hand over credentials.

**Tailgating** is physical. The attacker follows an authorized person through a secured door by acting like they belong — hands full with boxes, looking busy, holding the door conversation. It's remarkably effective because most people are too polite to challenge someone who looks like they should be there.

---

## 4. Psychological Triggers Attackers Rely On

Social engineering attacks don't work because victims are stupid. They work because humans have predictable psychological responses that evolved in contexts where they were useful. Attackers exploit those responses deliberately.

Robert Cialdini's research on influence identified six principles that social engineers consistently weaponize:

| Principle | What it looks like in an attack |
|---|---|
| **Authority** | "This is your CEO. I need that wire done today." |
| **Urgency** | "Your account gets deleted in 2 hours if you don't verify." |
| **Social Proof** | "Everyone else in your department has already submitted their info." |
| **Liking/Trust** | The attacker builds rapport over several calls before making the actual request. |
| **Reciprocity** | Offering something free first — fake software, a fake IT fix — so the target feels obligated. |
| **Commitment** | Getting small agreements early, then escalating to the actual harmful request. |

There's also **cognitive load** to consider. Attackers often time their attempts during stressful moments — system outages, end of quarter, right before a deadline. When people are overwhelmed, they cut corners on verification. That's exactly when attackers strike.

Understanding these triggers isn't just interesting — it's essential for training. People who know what manipulation looks like can recognize it in the moment.

---

## 5. Real-World Case Studies

### 5.1 Twitter Account Hijacking (2020)

**Attack type:** Vishing + Pretexting  
**Date:** July 15, 2020  
**Impact:** 130 high-profile accounts compromised; roughly $110,000 in Bitcoin scammed from followers

On the afternoon of July 14, 2020, attackers started calling Twitter employees. They claimed to be from Twitter's internal IT helpdesk, and said they were following up on a VPN issue — which was completely believable since Twitter had recently moved to remote work due to COVID-19. VPN problems were genuinely common at the time.

The attackers directed employees to a phishing website that looked exactly like Twitter's internal VPN portal. As employees typed in their credentials, the attackers captured them in real time and simultaneously submitted them to the real Twitter login — triggering an MFA push notification on the employee's phone. The employee, thinking they were logging in normally, approved it. The attacker's session was now authenticated.

What's important here is that the MFA didn't fail technically. It was bypassed because the victim was deceived into approving a legitimate-looking prompt that was actually generated by the attacker's relay. This technique is called Adversary-in-the-Middle (AiTM), and it's now one of the most common ways to get around MFA.

Once inside, the attackers moved laterally through Twitter's internal systems, escalating access until they reached admin tools that could control any account on the platform. They used those tools to post Bitcoin scam tweets from accounts belonging to Barack Obama, Elon Musk, Joe Biden, Bill Gates, Apple, and others. The scam collected around $110,000 in Bitcoin before Twitter shut it down.

The person primarily responsible turned out to be a 17-year-old from Florida.

**What this tells us:** MFA is not a complete solution on its own. Real-time credential relay can bypass it. The better solution is phishing-resistant MFA like FIDO2 hardware keys, which are cryptographically tied to the actual website domain and cannot be relayed. Helpdesk agents also need stricter verification protocols before making any account changes.

---

### 5.2 MGM Resorts and Caesars Entertainment (2023)

**Attack type:** Pretexting (IT helpdesk impersonation via LinkedIn OSINT)  
**Date:** September 2023  
**Impact:** MGM — estimated $100M+ in losses from operational outage; Caesars — ~$15M ransom paid

This is probably the most striking example of how dangerous pretexting can be at scale, because the entire attack started with a LinkedIn search.

The threat actor group Scattered Spider looked up MGM employees on LinkedIn, identified someone in IT, and then called MGM's helpdesk impersonating that employee. They had just enough personal information — name, job title, rough tenure — to pass the identity check. The helpdesk agent reset credentials and provided access. From there, the attackers deployed ransomware across MGM's infrastructure.

The fallout was severe. Slot machines across Las Vegas MGM properties went offline. Hotel check-in systems stopped working. Digital room keys failed. The MGM website went dark. Guests were checking in manually with pen and paper. The outage lasted for days and the estimated financial hit exceeded $100 million.

Caesars was hit by the same group using the same method around the same time. Their response was different — they reportedly paid approximately $15 million in ransom (reduced from a $30M initial demand) to get their systems back.

What's sobering is how simple this was. No zero-day exploits. No sophisticated malware to start with. Just a phone call, some publicly available information, and a helpdesk agent doing their job without adequate verification procedures.

**What this tells us:** Helpdesk verification procedures cannot rely on information the caller provides. Name and job title are not secrets — they're on LinkedIn. Proper verification should involve callbacks to known numbers, manager approval, or identity confirmation through a separate channel entirely. Privileged actions like password resets need a higher bar.

---

### 5.3 Arup Deepfake Fraud (2024)

**Attack type:** Deepfake video BEC  
**Date:** Early 2024  
**Impact:** HKD 200 million (~USD $25 million) transferred to attackers

This one is genuinely alarming because it removes what most people consider the last line of defense: seeing and hearing the person you're talking to.

A finance employee at Arup's Hong Kong office received an email requesting an urgent wire transfer. They were suspicious — the email came from an unfamiliar address. But then they were invited to a video conference call that appeared to include the company's CFO and several other senior colleagues. On that call, they saw familiar faces, heard familiar voices, and received direct instructions to execute 15 wire transfers totaling HKD 200 million.

Every person on that call was a deepfake. The attackers had synthesized video and audio of Arup executives from publicly available recordings — company presentations, media coverage, LinkedIn videos. The employee had no way to tell. They followed the instructions and transferred the money.

The fraud came to light only when the employee later followed up with the real CFO through internal channels.

**What this tells us:** Video calls are no longer reliable verification. Organizations dealing with large financial transactions need out-of-band verification that doesn't rely on seeing or hearing someone. Some organizations are implementing "safe word" protocols for executive payment instructions — a pre-agreed verbal code that deepfakes wouldn't know. Large transfers should always require dual authorization and a separate confirmation call to a known, pre-registered number.

---

### 5.4 Stuxnet and the USB Drop (2010)

**Attack type:** Physical baiting (USB drive)  
**Date:** Discovered 2010, operation likely started around 2007  
**Impact:** Estimated 20% reduction in operational centrifuges at Iran's Natanz nuclear facility

Stuxnet is worth understanding because it shows that baiting isn't just a trick for credential theft — in the right context, it can cause physical destruction.

Iran's Natanz uranium enrichment facility was air-gapped. That means it had no connection to the internet, which is supposed to make network-based attacks impossible. The attackers (widely attributed to a US-Israeli intelligence operation, though never officially confirmed) got around this by ensuring infected USB drives found their way to contractors and employees connected to the facility.

Once a drive was plugged into a machine that had any connection to the facility's industrial network — even temporarily — Stuxnet propagated silently. It specifically targeted Siemens STEP 7 software used to control the centrifuges. The malware subtly altered centrifuge rotation speeds to cause physical damage, while reporting completely normal readings to operators. The facility's staff thought everything was fine while their equipment was destroying itself.

By the time the attack was discovered, Iran's centrifuge program had been significantly set back. Stuxnet is widely considered the first known cyberweapon to cause physical infrastructure damage.

**What this tells us:** Air-gapped systems are only as secure as the physical media policies around them. USB AutoRun should be disabled by default on every enterprise machine. Devices connected to industrial control systems (OT/ICS networks) need especially strict physical media controls and device whitelisting.

---

### 5.5 Microsoft 365 AiTM Phishing (2023)

**Attack type:** Adversary-in-the-Middle (AiTM) phishing  
**Date:** 2023  
**Impact:** Multiple corporate Microsoft 365 accounts compromised despite MFA being enabled

This campaign is technically interesting because of how it handled MFA. Attackers sent phishing emails with HTML attachments disguised as Excel files. When opened, they launched a browser session pointing to a fake Microsoft 365 login page — but this wasn't a simple credential harvester. It was a real-time proxy.

As the victim typed in their credentials, the proxy relayed them to the actual Microsoft server. Microsoft sent back an MFA prompt to the victim's phone. The victim approved it — thinking it was a normal login. Microsoft then issued a session token, which the proxy captured. The attacker now had an authenticated session without ever needing the victim's password or their MFA device.

The victim didn't notice anything unusual. Their login "worked." But behind the scenes, the attacker now had full access to their Microsoft 365 account.

**What this tells us:** Standard TOTP or push-based MFA can be relayed. The solution is FIDO2/WebAuthn hardware security keys, where authentication is cryptographically bound to the exact domain the user is visiting. A relay attack breaks immediately because the key refuses to authenticate to the proxy domain. Conditional access policies that enforce device compliance before granting access also help significantly.

---

## 6. Key Statistics

| Metric | Number | Source |
|---|---|---|
| Phishing's share of social engineering breaches (2024) | 44% | Verizon DBIR 2024 |
| Pretexting's share of social engineering incidents | >50% | Verizon DBIR 2024 |
| FBI phishing complaints (2024) | 300,000+ | FBI IC3 2024 |
| Phishing-related losses (2024) | >$3 billion | FBI IC3 2024 |
| BEC losses (2024) | $2.77 billion | FBI IC3 2024 |
| BEC complaints (2024) | 21,442 | FBI IC3 2024 |
| Vishing growth H1 to H2 2024 | +442% | DeepStrike 2025 |
| Smishing growth 2023–2024 (toll scams) | +2,900% | DeepStrike 2025 |
| AI-generated phishing emails | >80% | ENISA 2025 |
| Average cost per social engineering attack | $130,000 | Secureframe 2026 |
| USB drives picked up in university study (2016) | 98% of 297 dropped | Univ. of Illinois |

---

## 7. Organizational Impact

### Financial

The most obvious impact is money. Wire fraud from BEC, ransom payments, regulatory fines, and incident response costs add up fast. MGM's 2023 breach exceeded $100 million. Caesars paid $15 million in ransom. The Arup deepfake fraud cost $25 million in a single incident. These are headline numbers, but even smaller incidents carry significant costs — the average is $130,000 per attack.

### Operational

When ransomware follows a social engineering intrusion, operations can grind to a halt. MGM couldn't process card payments or issue digital room keys for days. Hospitals hit by ransomware after phishing attacks have had to divert emergency patients. Industrial facilities hit by baiting-delivered malware (like Natanz) can suffer physical equipment damage.

### Reputational

The harder thing to quantify is trust. After a breach, customers question whether their data is safe. Employees lose confidence in leadership. Partners start reassessing their relationships. Twitter's 2020 breach happened at a moment when the platform could least afford a credibility crisis. Rebuilding trust takes much longer than rebuilding systems.

### Regulatory

Depending on the sector and region, breaches that expose personal or financial data trigger compliance obligations. GDPR fines can run to 4% of global annual turnover. HIPAA violations carry penalties up to $1.9 million per violation category annually. The NYDFS published a formal investigation report on the Twitter breach. Regulators are paying closer attention to social engineering incidents, and boards are being held accountable.

---

## 8. Prevention Strategies

There's no single fix for social engineering. What works is layering controls so that even if one fails, others catch the attack.

### 8.1 Security Awareness Training

This is the most important investment. Employees who know what social engineering looks like can stop attacks that no technical control would catch. Training needs to be:
- **Regular** — at least quarterly, not an annual checkbox
- **Practical** — simulated phishing campaigns teach better than slide decks
- **Specific** — show employees real examples of the attacks their organization is likely to face
- **Non-punitive** — people who report suspicious things should be praised, not embarrassed

The "hang up and call back" principle is worth teaching explicitly: if someone calls asking for sensitive information or action, hang up and call the organization back through a number you look up yourself — not one the caller gave you.

### 8.2 Phishing-Resistant MFA

Standard MFA (push notifications, SMS codes, TOTP apps) can be relayed in AiTM attacks. The solution is moving to phishing-resistant MFA:

- **FIDO2/WebAuthn hardware keys** (like YubiKey) — authentication is cryptographically bound to the actual website domain. AiTM relays fail because the key sees the wrong domain.
- **Certificate-based authentication** — used in enterprise PKI environments.
- Avoid SMS OTP where possible — SIM-swapping attacks can defeat it.

### 8.3 Strict Helpdesk Verification

Based on what happened at MGM and Caesars, this is critical. Helpdesk agents should not make any privileged changes based on information the caller provides:

- Callback to a number registered in the HR system — not one the caller gives.
- Manager approval via a separate channel for password resets and MFA bypass.
- In-person verification for the highest-risk changes.
- Privileged access changes should be logged and reviewed.

### 8.4 Email Authentication (SPF, DKIM, DMARC)

These three protocols together make it much harder to spoof email domains:
- **SPF** — specifies which mail servers are allowed to send email for your domain.
- **DKIM** — cryptographically signs outgoing emails so receivers can verify they weren't tampered with.
- **DMARC** — tells receiving servers what to do when SPF/DKIM checks fail. Set to `p=reject` to block spoofed emails outright.

Combined with a Secure Email Gateway (SEG), these controls significantly reduce the volume of phishing that reaches employee inboxes.

### 8.5 Financial Authorization Controls

For BEC and deepfake fraud:
- Wire transfers above a threshold (e.g., $5,000–$10,000) require dual authorization.
- Requests from executives for urgent payment must be verified through a separate channel — a known phone number, not email or video call.
- Consider establishing a verbal "safe word" for executive financial instructions that deepfakes wouldn't know.
- Any change to vendor payment details requires verification directly with the vendor via a known contact.

### 8.6 USB and Physical Media Controls

- Disable USB AutoRun/AutoPlay via Group Policy on all endpoints — this alone stops many USB-based attacks.
- Implement device whitelisting through endpoint management tools (Intune, CrowdStrike, etc.) to block unauthorized USB devices.
- Train employees to never plug in found drives and to hand them to the security team instead.
- For OT/ICS environments, USB ports should be physically blocked or disabled at firmware level.

### 8.7 Zero Trust Principles

Zero Trust means treating every access request as untrusted until verified — including those from inside the network. Practically, this means:
- Verify every login with identity, device health, and context checks.
- Enforce least privilege: users get access only to what they need for their role.
- Segment the network so that compromising one account doesn't mean compromising everything.

### 8.8 Incident Response Readiness

Prevention won't be perfect. When an attack does get through:
- Have a documented incident response plan that includes social engineering scenarios.
- Run tabletop exercises so that IT, finance, and HR teams know what to do.
- Make sure employees know how to report suspicious calls and emails without feeling like they'll get in trouble for it.

### Controls Summary

| Control | What it stops | Priority |
|---|---|---|
| Phishing-resistant MFA (FIDO2) | Phishing, AiTM, vishing | Critical |
| DMARC/DKIM/SPF | Email spoofing, BEC | Critical |
| Security awareness training + phishing simulations | All vectors | Critical |
| Helpdesk callback verification | Pretexting, credential theft | Critical |
| Dual authorization for wire transfers | BEC, deepfake fraud | High |
| Least privilege access / RBAC | Lateral movement after compromise | High |
| USB device control + AutoRun disabled | USB baiting | High |
| EDR (Endpoint Detection and Response) | Malware from phishing or baiting | High |
| Zero Trust network segmentation | Limiting blast radius | High |
| Deepfake detection tools | Deepfake BEC and vishing | Medium |
| Physical access controls (badges, CCTV) | Tailgating | Medium |

---

## 9. Framework Alignment

### NIST Cybersecurity Framework 2.0 (CSF 2.0)

| Function | Relevant Controls |
|---|---|
| **Govern (GV)** | Helpdesk verification policy, financial authorization procedures, acceptable use policy |
| **Identify (ID)** | OSINT exposure assessment, employee data risk mapping, asset inventory |
| **Protect (PR)** | Security awareness training, MFA, DMARC/DKIM/SPF, USB controls |
| **Detect (DE)** | Phishing simulation metrics, SIEM alerts on login anomalies, EDR behavioral detection |
| **Respond (RS)** | Incident response plan, BEC reporting procedure, compromised credential response |
| **Recover (RC)** | Backup and restoration, post-incident review, customer communication |

### ISO/IEC 27001:2022

Controls most relevant to social engineering defense:
- **A.6.3 — Information Security Awareness, Education and Training:** Regular training and awareness programs for all employees.
- **A.8.5 — Secure Authentication:** MFA requirements for privileged and remote access.
- **A.5.14 — Information Transfer:** Protecting sensitive data in all forms of communication.
- **A.8.7 — Protection Against Malware:** Coverage for malware delivered through phishing and baiting.

### CIS Controls v8

- **Control 14 — Security Awareness and Skills Training:** Mandates phishing simulations and social engineering awareness as core practices.
- **Control 6 — Access Control Management:** Least privilege enforcement and MFA.
- **Control 9 — Email and Web Browser Protections:** DMARC, email filtering, anti-phishing.
- **Control 10 — Malware Defenses:** Endpoint protection covering payloads delivered through social engineering.

---

## 10. Conclusion

One thing that stands out after researching this topic is how consistent the pattern is across incidents. Whether it's a teenager social engineering Twitter's helpdesk in 2020, a ransomware gang pretexting their way into MGM's network in 2023, or attackers using deepfake video to steal $25 million from a Hong Kong company in 2024 — the core mechanism is always the same. Someone trusted something they shouldn't have.

The sophistication varies. The target varies. The damage varies. But the fundamental exploit is human psychology, not technical vulnerability.

What's changing is the tools available to attackers. AI-generated phishing emails are already indistinguishable from legitimate communication for most people. Voice cloning is accessible and cheap. Deepfake video quality is improving rapidly. The 2024 Arup incident — where every person on a video call was a fabricated deepfake — shows that even seeing and hearing someone is no longer sufficient verification.

This is uncomfortable because it means that defenses built around "verify by calling back" or "check that it looks like the real website" are becoming less reliable. The industry needs to move toward verification methods that are cryptographically binding — FIDO2 keys, PKI-based authentication — because those can't be fooled by a convincing fake.

At the same time, training still matters enormously. A well-trained employee who knows that no legitimate IT department will ever ask for their password, who follows callback procedures before approving a wire transfer, and who reports a suspicious USB drive they found in the parking lot — that employee is a genuine defense layer. Not foolproof, but meaningful.

The goal isn't to eliminate social engineering attacks entirely. That's probably not achievable. The goal is to make them fail more often, detect them faster when they don't fail, and recover quickly when they succeed. A combination of the right technology, clear procedures, and genuinely trained employees gets organizations a lot closer to that goal than technical controls alone.

---

## 11. References

1. Verizon. (2024). *Data Breach Investigations Report (DBIR) 2024*. Verizon Business.
2. FBI Internet Crime Complaint Center (IC3). (2024). *2024 Internet Crime Report*. Federal Bureau of Investigation.
3. ENISA. (2025). *Threat Landscape 2025: Social Engineering*. European Union Agency for Cybersecurity.
4. New York Department of Financial Services (NYDFS). (2020). *Twitter Investigation Report*. https://www.dfs.ny.gov/Twitter_Report
5. Mitnick, K. D., & Simon, W. L. (2002). *The Art of Deception: Controlling the Human Element of Security*. Wiley.
6. Cialdini, R. B. (2007). *Influence: The Psychology of Persuasion* (Revised Ed.). HarperCollins.
7. Krombholz, K., Hobel, H., Huber, M., & Weippl, E. (2015). Advanced social engineering attacks. *Journal of Information Security and Applications*, 22, 113–122.
8. Witman, P. D., & Mackelprang, S. (2022). The 2020 Twitter Hack — So Many Lessons to Be Learned. *Journal of Cybersecurity Education, Research and Practice*, Vol. 2021, No. 2.
9. Secureframe. (2026). *85+ Social Engineering Statistics to Know for 2026*. https://secureframe.com/blog/social-engineering-statistics
10. Spacelift. (2026). *70 Social Engineering Statistics for 2026*. https://spacelift.io/blog/social-engineering-statistics
11. Adaptive Security. (2026). *Social Engineering Threats: 6 Common Attack Examples*. https://www.adaptivesecurity.com/blog
12. DeepStrike. (2025). *Social Engineering Statistics 2025: The Human Hack*. https://deepstrike.io/blog/social-engineering-statistics-2025
13. Bitwarden. (2025). *Baiting Attacks Explained: How to Recognize and Prevent Them*. https://bitwarden.com/resources/baiting-attacks-explained/
14. University of Illinois. (2016). *Beware of Abandoned Flash Drives*. USB drop study. https://dl.acm.org/doi/10.1145/2976749.2978446
15. NIST. (2024). *Cybersecurity Framework 2.0*. https://doi.org/10.6028/NIST.CSWP.29
16. ISO/IEC. (2022). *ISO/IEC 27001:2022 — Information Security Management Systems*. International Organization for Standardization.
17. CIS. (2021). *CIS Controls Version 8*. Center for Internet Security. https://www.cisecurity.org/controls/v8
18. InformationWeek. (2024). *Social Engineering Ploys Popular with Scammers in 2024*. https://www.informationweek.com
19. Proofpoint. (2024). *State of the Phish Report 2024*. Proofpoint, Inc.
20. KnowBe4. (2020). *The Recent Massive Twitter Social Engineering Hack Was Tried And True Pretexting*. https://blog.knowbe4.com
21. Hong Kong Police Force. (2024). *Press Release: Deepfake Video Conference Fraud*. Hong Kong Police.
22. Langner, R. (2011). Stuxnet: Dissecting a Cyberwarfare Weapon. *IEEE Security & Privacy*, 9(3), 49–51.
23. Valimail. (2025). *What Is a Baiting Attack in Social Engineering Tactics?* https://www.valimail.com/blog/what-is-baiting-attack/
24. IT GOAT. (2025). *Social Engineering: Preventing Baiting Attacks & Scams*. https://www.itgoat.com/blog/social-engineering-preventing-baiting-attacks-scams/
25. Rahalkar, C. (2021). *A Diamond Model Analysis on Twitter's Biggest Hack*. arXiv:2306.15878.

---

*Prepared as part of an internship in cybersecurity. All referenced incidents are sourced from publicly available documentation. Statistics and recommendations reflect the threat landscape as of June 2026.*
