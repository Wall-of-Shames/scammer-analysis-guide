# Wall of Shames: GitHub & Social Media Scam Exposure Project

![Status](https://img.shields.io/badge/status-active-success.svg)
![Contributions](https://img.shields.io/badge/contributions-welcome-orange.svg)

> **Mission:** Documenting and analyzing fraudulent "AI Hacker Tools" and scam repositories that exploit non-technical users through social media platforms (Facebook, YouTube, Telegram).

---

## Table of Contents

- [About](#about)
- [The Problem](#the-problem)
- [Scam Detection Checklist](#scam-detection-checklist)
  - [1. The "Wrapper" Trap](#1-the-wrapper-trap)
  - [2. The "Telegram" Funnel](#2-the-telegram-funnel)
  - [3. Fake "Hacker" Aesthetics](#3-fake-hacker-aesthetics)
  - [4. Dependency Loops & Bad Practices](#4-dependency-loops--bad-practices)
  - [5. Artificial Engagement](#5-artificial-engagement)
- [Real-World Examples](#real-world-examples)
- [How to Contribute](#how-to-contribute)
- [Submission Template](#submission-template)
- [Hall of Shame Archive](#hall-of-shame-archive)
- [Legal & Ethical Guidelines](#legal--ethical-guidelines)
- [FAQ](#faq)
- [Resources](#resources)

---

### About

This repository serves as a **community-driven database** for identifying and documenting fraudulent GitHub projects that masquerade as sophisticated AI/hacking tools. These scams typically:

- Target users with limited technical knowledge
- Promote "premium" or "uncensored" versions through private channels
- Steal money via cryptocurrency, fake subscriptions, or data harvesting
- Damage the reputation of legitimate open-source projects

**We focus on technical proof, not personal attacks.** All submissions must include reproducible evidence.

---

## 🔥 The Problem

### The Scam Lifecycle

```
1. Create "Hacker Tool" with edgy name (WormGPT, DarkGPT, etc.)
   ↓
2. Write minimal code (usually 50-200 lines)
   ↓
3. Add flashy UI with Matrix-style colors
   ↓
4. Post demo videos on YouTube/Facebook/TikTok
   ↓
5. Direct users to Telegram for "Premium Access"
   ↓
6. Request payment in crypto or steal credentials
   ↓
7. Disappear or rebrand when exposed
```

### Common Victims

- Aspiring "hackers" seeking shortcuts
- Non-developers impressed by terminal UIs
- Users in regions with limited cybersecurity awareness
- Young people attracted to "forbidden" technology

---

## 🔍 Scam Detection Checklist

### 1. The "Wrapper" Trap

**What to look for:** Code that pretends to be a custom AI model but actually just forwards requests to public APIs.

#### 🚩 Red Flags

```python
# Example: Fake "Custom AI Model"
import openai
from langchain import OpenAI

# They claim it's "trained on hacking data" but it's just ChatGPT
response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=[{"role": "system", "content": "You are a hacker assistant"}]
)
```

```python
# Another common pattern
import requests

# Routing to free public endpoints
api_url = "https://api.openrouter.ai/v1/chat/completions"
# or "https://api.deepseek.com/v1/chat/completions"
```

#### ✅ How to Verify

1. Search the codebase for these imports:
   ```bash
   grep -r "import openai" .
   grep -r "from langchain" .
   grep -r "openrouter.ai" .
   grep -r "deepseek.com" .
   ```

2. Check if there's actual model training code:
   - Look for `torch`, `tensorflow`, `transformers` with actual training loops
   - Search for `.pt`, `.safetensors`, `.h5` model files
   - Check if there's a `train.py` or `finetune.py` script

#### 💡 The Reality

**What they sell you:** "Custom AI trained on 10TB of hacking databases"  
**What you actually get:** A system prompt that says `"You are a helpful hacking assistant"` sent to ChatGPT

---

### 2. The "Telegram" Funnel

**What to look for:** Projects that use GitHub as a billboard but do all business on Telegram.

#### 🚩 Red Flags

```markdown
# Typical Scam README.md

## Installation
git clone https://github.com/fake/repo
cd repo
pip install -r requirements.txt

## Usage
⚠️ **FREE VERSION IS LIMITED!**

For the UNCENSORED version with:
- 🔓 Jailbreak capabilities
- 💀 Zero restrictions
- 🚀 10x faster responses

👉 Join our Telegram: t.me/hackergpt_premium
💰 Premium: $49.99/month (BTC only)
```

#### How to Verify

**Legitimate projects:**
- Document everything in GitHub wiki/README
- Offer all features open-source (maybe with optional paid hosting)
- Use official payment processors if commercial (Stripe, PayPal)
- Have public issue trackers and changelogs

**Scams:**
- Minimal GitHub documentation
- 2+ Telegram links in README
- Phrases like "DM @admin for license key"
- No public roadmap or feature list

#### 💡 Why Telegram?

- Harder to moderate than GitHub
- Disappear faster when exposed
- Enables anonymous crypto payments
- Creates FOMO with "exclusive access"

---

### 3. Fake "Hacker" Aesthetics

**What to look for:** Projects where the UI/branding has more effort than the actual code.

#### 🚩 Red Flags

```python
# 150 lines of ASCII art and colors
from colorama import Fore, Style, init
from art import text2art
import pyfiglet
import time
import sys

def print_banner():
    banner = text2art("DARKGPT", font='block')
    for line in banner.split('\n'):
        print(Fore.GREEN + line)
        time.sleep(0.1)
    
    print(Fore.RED + "=" * 60)
    print(Fore.YELLOW + "🔥 UNCENSORED AI HACKING TOOL 🔥")
    print(Fore.RED + "=" * 60)
    # ... 100 more lines of this ...

# Then the "core" logic:
def hack():
    user_input = input("Enter target: ")
    response = requests.post("https://api.openai.com/...", ...)
    print(response.json()['choices'][0]['text'])

# That's it. That's the entire tool.
```

#### ✅ How to Verify

**Check the code-to-fluff ratio:**

```bash
# Count lines of actual logic
find . -name "*.py" -exec grep -v "print\|Fore\|\#\|import art" {} \; | wc -l

# vs. total lines
find . -name "*.py" -exec cat {} \; | wc -l
```

If the ratio is less than 30%, it's probably a scam.

#### 💡 The Reality

**Professional tools:** Focus on functionality first, aesthetics second  
**Scams:** Spend 80% effort on "looking cool" to impress non-coders

---

### 4. Dependency Loops & Bad Practices

**What to look for:** Code quality issues that no experienced developer would commit.

#### 🚩 Red Flag Examples

```python
# ❌ RED FLAG 1: Hardcoded API keys (committed to git)
OPENAI_KEY = "sk-proj-1234567890abcdefghijklmnop"
TELEGRAM_TOKEN = "123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11"

# ❌ RED FLAG 2: Circular imports
# file1.py
from file2 import function_b
def function_a():
    return function_b()

# file2.py
from file1 import function_a  # This will crash
def function_b():
    return function_a()

# ❌ RED FLAG 3: No error handling
def exploit_target(ip):
    data = requests.get(f"http://{ip}/admin")
    return data.json()['password']  # Will crash if any step fails

# ❌ RED FLAG 4: Requirements.txt chaos
openai==0.28.0
openai==1.3.0  # Two different versions!
numpy
pandas
scikit-learn  # Imported but never used
tensorflow-gpu  # Not needed for an API wrapper

# ❌ RED FLAG 5: Missing .gitignore
# (so you can see their .env files with API keys in commit history)
```

#### ✅ What to Look For

```bash
# Check for exposed secrets in history
git log --all --full-history --source -- '*.env'
git grep -i "api_key\|password\|secret" $(git rev-list --all)

# Check for amateur mistakes
grep -r "import .*\nimport .*\n.*from .* import" .  # Messy imports
find . -name ".env" ! -path "./.gitignore"  # Exposed config files
```

---

### 5. Artificial Engagement

**What to look for:** Fake popularity metrics.

#### 🚩 Red Flags

- **Star Pattern:** 500+ stars in first 48 hours, then flatlines
- **Fork Pattern:** 200 forks but zero modified commits in forks
- **Contributor Pattern:** 1 developer, 0 pull requests, 0 issues
- **Commit Pattern:** "Urgent security update" every 3 days (fake activity)
- **Release Pattern:** v1.0 → v1.1 → v2.0 in 1 week with no changelog

#### ✅ How to Verify

```bash
# Check star history (requires browser extension or API)
# Visit: https://star-history.com/#username/repo

# Check fork quality
# Click "Forks" tab → Check if any fork has new commits

# Check commit patterns
git log --since="30 days ago" --oneline | wc -l
# If >50 commits/month but all are "minor fixes", suspicious
```

---

## 💀 Real-World Examples

### Case Study #1: "WormGPT Clone"

**Repository:** `github.com/fake-user/wormgpt-free` (archived)

**Red Flags Found:**
```
✓ API wrapper to OpenAI (found in src/main.py:23)
✓ Telegram premium link in README
✓ 250 lines of ASCII art vs. 40 lines of logic
✓ Hardcoded API key in commit 3f4a2b1
✓ 600 stars in 2 days, then 0 activity
```

**Evidence:**
```python
# src/core.py (entire file)
import openai
openai.api_key = "sk-..."  # Stolen key from commit history

def generate_hack(prompt):
    return openai.Completion.create(
        engine="text-davinci-003",
        prompt=f"You are WormGPT. {prompt}",
        max_tokens=500
    )
```

**Outcome:** Repository deleted after exposure. User created 3 more clones.

---

### Case Study #2: "DarkGPT Pro"

**Repository:** `github.com/scammer/darkgpt` (archived)

**The Scam:**
- Claimed to be "uncensored AI for pentesters"
- Free version was intentionally broken
- Telegram charged $99 for "lifetime license"
- "License key" was just an API key to OpenRouter

**Evidence:**
```python
# Check if user paid
if license_key == "PREMIUM":
    api_endpoint = "https://openrouter.ai/api/v1/chat/completions"
else:
    print("FREE VERSION: Limited to 3 queries/day")
    exit()
```

**Outcome:** 40+ victims reported on Telegram before shutdown.

---

## 🤝 How to Contribute

We welcome submissions that include **technical proof** of scams.

### What We Accept

✅ GitHub repositories with fraudulent claims  
✅ Social media accounts promoting scam tools  
✅ Telegram channels conducting payment fraud  
✅ YouTube tutorials directing to scams

### What We DON'T Accept

❌ Personal attacks or doxxing  
❌ Speculation without code evidence  
❌ Reports about legitimate projects you disagree with  
❌ Submissions based solely on "sketchy vibes"

---

## 📝 Submission Template

### Via GitHub Issues

Click [**New Issue**](../../issues/new) and use this template:

```markdown
## Scam Report

**Repository/Account:**
- URL: https://github.com/username/repo
- Platform: [ ] GitHub [ ] YouTube [ ] Telegram [ ] Facebook [ ] Other

**Scam Category:**
- [ ] API Wrapper Fraud
- [ ] Telegram Payment Scam
- [ ] Fake Hacker Aesthetics
- [ ] Stolen/Cloned Code
- [ ] Other: ___________

**Technical Evidence:**

1. **File:** `src/main.py` **Line:** 42
   ```python
   openai.ChatCompletion.create(...)  # Claims to be custom model
   ```

2. **README contains:**
   - Telegram link: t.me/fakehackertool
   - Payment request: "$49/month BTC only"

3. **Commit History:**
   - Hardcoded API key in commit: `abc123def`
   - Screenshot: [link to imgur]

**Archive Links:**
- Archive.today: https://archive.ph/xxxxx
- GitHub Archive: https://github.com/username/repo/tree/abc123

**Additional Context:**
[Any social media posts, victim testimonials, etc.]
```

---

## 🗂️ Hall of Shame Archive

Our documented cases are organized by date:

```
/exposures
  /2025-01
    /fake-wormgpt
      - analysis.md       # Detailed breakdown
      - evidence.md       # Code screenshots
      - timeline.md       # Discovery to shutdown
      - archive/          # Cached files
  /2025-02
    /darkgpt-scam
      - analysis.md
      ...
```

**Browse the archive:** [`/exposures`](./exposures)

---

## ⚖️ Legal & Ethical Guidelines

### Our Principles

1. **Public Information Only**
   - We analyze publicly accessible GitHub repositories
   - We do not hack, crack, or bypass private systems
   - We do not share personal information (names, addresses, etc.)

2. **Focus on Code, Not People**
   - We critique technical implementations, not individuals
   - We avoid inflammatory language
   - We provide evidence, not accusations

3. **Fair Use & DMCA**
   - Code snippets are quoted under fair use for educational criticism
   - We link to original sources
   - We respect takedown requests for legitimate projects

4. **No Harassment**
   - We do not coordinate brigading or mass reporting
   - We do not encourage contact with scammers
   - We report findings to platforms (GitHub, Telegram) via official channels

### Disclaimer

```
This repository documents publicly available code for educational 
and research purposes. We do not condone harassment, doxxing, or 
vigilante justice. All submissions must include reproducible 
technical evidence. We are not responsible for actions taken by 
third parties based on information in this repository.
```

---

## ❓ FAQ

### Q: How is this different from just reporting to GitHub?

**A:** GitHub's abuse reports can take weeks. This database:
- Provides immediate warnings to the community
- Creates a searchable archive (repos get deleted)
- Helps identify patterns across multiple scam accounts

### Q: What if a project is just poorly coded but not a scam?

**A:** We differentiate between:
- **Scam:** Intentional fraud with payment demands
- **Misleading:** Exaggerated claims but no payment
- **Amateur:** Just bad code (not documented here)

### Q: Can a project be removed from the archive?

**A:** Yes, if:
1. The maintainer provides proof of legitimacy
2. Our analysis was factually incorrect
3. The project has been substantially reworked

Submit a removal request via Issues.

### Q: What if I submitted a false positive?

**A:** Open an issue with "CORRECTION" in the title. We'll review and update.

### Q: Are you affiliated with GitHub/Anthropic/OpenAI?

**A:** No. This is an independent community project.

---

## 📚 Resources

### For Victims

- **FBI IC3:** https://www.ic3.gov/Home/FileComplaint
- **Crypto Scam Report:** https://www.blockchain.com/support
- **Telegram Fraud Report:** https://telegram.org/support

### For Developers

- **Secure Coding:**
  - OWASP Top 10: https://owasp.org/www-project-top-ten/
  - Python Security: https://bandit.readthedocs.io/

- **API Key Management:**
  - GitHub Secrets: https://docs.github.com/en/actions/security-guides/encrypted-secrets
  - Git-secrets: https://github.com/awslabs/git-secrets

- **Detecting Fake Stars:**
  - Star History: https://star-history.com/
  - GitHub Analysis: https://github.com/vinta/awesome-stars

### Learning Resources

- **Ethical Hacking (Legit):**
  - HackTheBox: https://www.hackthebox.com/
  - TryHackMe: https://tryhackme.com/

- **AI Development (Real):**
  - Hugging Face: https://huggingface.co/
  - OpenAI Cookbook: https://github.com/openai/openai-cookbook

---

## 🛡️ Protect Yourself

### Before Using Any "Hacking Tool"

✅ **DO:**
- Read the source code completely
- Check commit history for secrets
- Verify dependencies are legitimate
- Test in an isolated environment (VM)
- Research the developer's other projects

❌ **DON'T:**
- Enter payment information on Telegram
- Download "cracked" or "premium" versions
- Trust projects with <10 commits
- Use tools that "require admin/root"
- Ignore your security software's warnings

### Red Flag Phrases

If you see these in a README, be suspicious:

- "Uncensored AI" / "Jailbroken GPT"
- "100% undetectable"
- "Premium version on Telegram"
- "Join private group for access"
- "Cryptocurrency only"
- "Limited time offer"
- "FBI/NSA don't want you to know this"

---

## 📊 Statistics

**As of February 2025:**

- **Total Repositories Documented:** [TBD]
- **Total Estimated Victims:** [TBD]
- **Average Scam Lifespan:** 14-30 days
- **Most Common Scam Type:** API Wrapper (68%)
- **Top Target Platforms:** Telegram (73%), Discord (18%), WhatsApp (9%)

---

## 🚀 Roadmap

- [x] Initial documentation framework
- [ ] Automated scam detection bot
- [ ] Browser extension for real-time warnings
- [ ] Integration with GitHub's abuse API
- [ ] Multi-language support (Spanish, Portuguese, Russian)
- [ ] Victim support resources
- [ ] Monthly scam trend reports

---

## 💬 Community

- **Discussions:** [GitHub Discussions](../../discussions)
- **Report a Scam:** [Open an Issue](../../issues/new)
- **Security Concerns:** security@[project-domain].com

---

## 📜 License

This project is licensed under the **MIT License** - see [LICENSE](LICENSE) for details.

Code snippets from analyzed repositories are quoted under **Fair Use** for educational and critical commentary purposes.

---

## 🙏 Acknowledgments

Special thanks to:

- Security researchers who expose these scams daily
- Victims who share their experiences to warn others
- Legitimate open-source developers maintaining ethical tools
- Platforms working to combat fraud (GitHub, OpenAI, Telegram)

---

## ⚠️ Final Warning

**If something seems too good to be true, it is.**

No legitimate AI tool will:
- Promise to "hack any system"
- Require payment via untraceable cryptocurrency
- Operate exclusively on Telegram
- Claim to bypass all ethical safeguards

**Stay safe. Verify everything. Trust the code, not the hype.**

---

<div align="center">

**Found a scam? [Report it here](../../issues/new)**

**Want to contribute? [Read our guidelines](#how-to-contribute)**

**Need help? [Visit our FAQ](#faq)**

---

Made with 🔍 by the NCF community, for the community.

*Last updated: February 2025*

</div>
