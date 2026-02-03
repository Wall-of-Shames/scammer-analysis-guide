---
name: Scam Report
about: Report a fraudulent repository or social media account
title: '[SCAM] '
labels: 'investigation-needed'
assignees: ''
---

## 🚨 Scam Report

### Basic Information

**Target Repository/Account:**
- **URL:** https://github.com/username/repo
- **Platform:** [ ] GitHub [ ] YouTube [ ] Telegram [ ] Facebook [ ] TikTok [ ] Other: _______
- **Discovery Date:** YYYY-MM-DD
- **Current Status:** [ ] Active [ ] Deleted [ ] Private [ ] Suspended

---

### Scam Classification

**Primary Scam Type:**
- [ ] API Wrapper Fraud (fake custom AI model)
- [ ] Telegram Payment Funnel
- [ ] Fake Hacker Aesthetics (all UI, no logic)
- [ ] Stolen/Cloned Code
- [ ] Credential Harvesting
- [ ] Malware Distribution
- [ ] Fake Star/Fork Farming
- [ ] Other: ___________

**Severity:**
- [ ] 🔴 Critical (active payment fraud, malware)
- [ ] 🟠 High (payment requests, data collection)
- [ ] 🟡 Medium (misleading but no immediate harm)
- [ ] 🟢 Low (exaggerated claims only)

---

### Technical Evidence

#### Code Analysis

**1. Suspicious Files:**

```
File: src/main.py
Lines: 23-45

[Paste relevant code snippet showing the scam evidence]
```

**2. Dependencies Check:**

```bash
# Run this in the repository:
cat requirements.txt
```

**Output:**
```
[Paste requirements.txt or package.json content]
```

**3. API Calls Found:**

- [ ] Calls to `openai.com`
- [ ] Calls to `openrouter.ai`
- [ ] Calls to `deepseek.com`
- [ ] Calls to other LLM APIs: _______
- [ ] Hardcoded API keys in commits

**Specific Evidence:**
```python
# Example:
openai.api_key = "sk-proj-xxxxx"  # Found in commit abc123
```

---

#### README Analysis

**Suspicious Claims:**
- [ ] "Uncensored AI"
- [ ] "Jailbroken GPT"
- [ ] "100% undetectable"
- [ ] "Custom trained model"
- [ ] "Zero restrictions"

**Payment Requests:**
- [ ] Telegram link for "premium"
- [ ] Discord link for "VIP access"
- [ ] Direct payment request (Amount: ______ Currency: ______)
- [ ] Cryptocurrency wallet address

**Quote from README:**
```markdown
[Paste the suspicious section of their README]
```

---

#### Commit History Analysis

**Red Flags:**
- [ ] Hardcoded secrets in commit history
- [ ] Suspicious commit message patterns
- [ ] Mass commits with no real changes
- [ ] .env files not gitignored

**Specific Commits:**
- Commit SHA: `abc123def456`
  - Issue: Exposed API key
  - Link: https://github.com/user/repo/commit/abc123def456

---

#### Engagement Metrics

**Star Pattern:**
- Stars when first discovered: _____
- Current stars: _____
- Star gain rate: _____ stars/day

**Fork Pattern:**
- Total forks: _____
- Forks with actual changes: _____

**Contributor Pattern:**
- Total contributors: _____
- Open Pull Requests: _____
- Closed Issues: _____

**Suspicious Activity:**
- [ ] 100+ stars in first 48 hours
- [ ] All forks have zero modifications
- [ ] Only 1 contributor despite 50+ commits
- [ ] Regular "urgent update" commits

---

### Social Media Evidence

**Promotional Channels:**

1. **YouTube:**
   - Video URL: _______
   - Views: _______
   - Upload Date: _______
   - Key Claims: _______

2. **Telegram:**
   - Channel: t.me/_______
   - Members: _______
   - Payment Method: _______
   - Screenshot: [link]

3. **Other Platforms:**
   - Platform: _______
   - URL: _______
   - Description: _______

---

### Archive Links

**REQUIRED:** Please archive the evidence before submitting.

- **Archive.today:** https://archive.ph/xxxxx
- **GitHub Archive:** https://github.com/user/repo/tree/commit-sha
- **Screenshots:** [Upload to Imgur/GitHub Issues]
  - [ ] Repository README
  - [ ] Suspicious code sections
  - [ ] Payment requests
  - [ ] Social media posts

---

### Victim Reports

**If you or someone you know was affected:**

- Number of known victims: _____
- Financial loss reported: $_____
- Contact method used by scammer: _______
- Screenshot of scam interaction: [link]

*Note: Do NOT include personal information of victims.*

---

### Additional Context

**Scammer's Pattern:**
- [ ] This appears to be part of a network (list similar repos)
- [ ] Scammer has created multiple accounts
- [ ] Related repositories: _______

**Your Relationship:**
- [ ] I discovered this independently
- [ ] I am a victim
- [ ] I saw this promoted on social media
- [ ] Other: _______

**Additional Notes:**
```
[Any other relevant information, observations, or context]
```

---

### Pre-Submission Checklist

Before submitting, please verify:

- [ ] I have archived the evidence (Archive.today link included)
- [ ] I have included specific code examples or screenshots
- [ ] I have checked that this isn't already reported (search existing issues)
- [ ] I have not included personal information or doxxing material
- [ ] I understand this is for documentation, not personal revenge
- [ ] I have evidence this is fraud, not just poor coding

---

### Suggested Actions

**What should happen to this repository?**
- [ ] Document in Hall of Shame
- [ ] Report to GitHub for ToS violation
- [ ] Report to payment processor (if applicable)
- [ ] Warn on social media platforms
- [ ] Contact victims if possible
- [ ] Other: _______

---

**Reporter's Statement:**

I confirm that the information provided above is accurate to the best of my knowledge and that I am submitting this report in good faith to protect the community from fraudulent activities.

---

*Thank you for helping protect the community! We will review your submission within 48 hours.*
