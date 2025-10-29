# Root.io AI Engineer - Home Assignment

**Time Limit: 3 hours maximum**

## Overview

This assignment evaluates your ability to build and assess AI agents that can analyze code, understand vulnerabilities, and apply fixes autonomously.

You'll research **CWE-22 (Path Traversal)** vulnerability online, then build an AI agent that analyzes vulnerable code, determines the appropriate fix, and applies it.

## What You're Given

1. **Vulnerability**: **CWE-22: Path Traversal** (Improper Limitation of a Pathname)
   - **Research online**: [CWE-22 Details](https://cwe.mitre.org/data/definitions/22.html) | [OWASP Path Traversal](https://owasp.org/www-community/attacks/Path_Traversal)
   - Understand what path traversal is and how to prevent it
2. **Vulnerable Code**: `file_reader.py` (has the vulnerability)
3. **Test Suite**: `test_file_reader.py` (2 tests currently FAIL due to the vulnerability)

## Your Goal

**Build an agent (`agent.py`) that:**
1. Analyzes `file_reader.py` to understand the vulnerability (CWE-22)
2. Determines the appropriate fix
3. Applies the fix to `file_reader.py`
4. Makes all tests pass ✅

## Getting Started

### 1. Research the Vulnerability

**Start by researching CWE-22 (Path Traversal) online:**
- Read about it on [CWE-22](https://cwe.mitre.org/data/definitions/22.html) or [OWASP](https://owasp.org/www-community/attacks/Path_Traversal)
- Understand what path traversal attacks are
- Learn about common fixes and mitigations
- This research will inform how you build your agent

### 2. Setup Environment

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Verify the Vulnerability

```bash
pytest test_file_reader.py -v
```

You should see 2 tests **FAIL** (path_traversal_blocked and absolute_path_blocked).

### 4. Build Your Agent

Create `agent.py` that:
- Analyzes the vulnerable code in `file_reader.py`
- Uses your understanding of CWE-22 to determine the fix
- Applies the fix to `file_reader.py`

### 5. Run and Verify

```bash
python agent.py
pytest test_file_reader.py -v  # All tests should now PASS
```

## Success Criteria

**Before your agent runs:**
- ❌ test_path_traversal_blocked FAILS
- ❌ test_absolute_path_blocked FAILS

**After your agent runs:**
- ✅ test_path_traversal_blocked PASSES
- ✅ test_absolute_path_blocked PASSES
- ✅ test_safe_extraction PASSES
- ✅ test_nonexistent_file PASSES

## Deliverables

Submit these three files:

### 1. `agent.py` - Your AI Agent Implementation

Your agent must:
- Read and analyze `file_reader.py` and `test_file_reader.py`
- Understand CWE-22 (Path Traversal vulnerability)
- Determine the appropriate fix
- Modify `file_reader.py` to apply the fix
- Be runnable via: `python agent.py`

**Important**: The agent should autonomously analyze and fix the code, not have the fix hardcoded.

### 2. `REPORT.md` - Evaluation Report (1-2 pages)

Include:
- **Architecture**: Brief description of your agent's design and approach
- **Research Summary**: What you learned about CWE-22 from your online research
- **Analysis Strategy**: How the agent analyzed the code and determined the fix
- **Findings**: Summary of the vulnerability and the fix applied
- **Performance Metrics**: Time taken, iterations, success rate
- **Evaluation**: What worked well, what didn't, limitations
- **Improvements**: What you'd do differently with more time

See `REPORT_TEMPLATE.md` for a detailed template.

### 3. `requirements.txt` - Dependencies

Add any libraries your agent needs (APIs, LLM clients, web scraping, etc.)

## Rules & Guidelines

- ✅ **Use any AI tools/APIs**: OpenAI, Anthropic, Claude, etc. to build your agent
- ✅ **Agent must be autonomous**: Don't hardcode the fix - the agent should analyze and determine it
- ✅ **Any Python libraries**: Use whatever you need
- ✅ **Partial submissions OK**: If you run out of time, submit what you have
- ⏱️ **Time limit**: Maximum 3 hours (we respect your time!)
- 🚫 **Don't modify tests**: Fix the vulnerable code, not the test file

## Evaluation Criteria

Your submission will be evaluated on:

| Criteria | Weight | Description |
|----------|--------|-------------|
| **Functionality** | 40% | Does the agent successfully fix the vulnerability? Do all tests pass? |
| **Agent Quality** | 30% | Clear architecture, effective analysis approach, autonomous operation |
| **Evaluation** | 20% | Thoughtful analysis, honest assessment, good metrics |
| **Code Quality** | 10% | Clean, readable, well-structured code |

**Total**: 100 points

## Tips for Success

- **Research first**: Start by reading about CWE-22 (Path Traversal) online - understanding the vulnerability is key
- **Start simple**: A basic working agent is better than a complex incomplete one
- **Well-documented issue**: Use CWE, OWASP, and other sources to understand path traversal
- **Multiple valid fixes**: There are several correct ways to fix path traversal vulnerabilities
- **Test frequently**: Run the tests often to verify your fix works
- **Use the tests**: The failing tests show exactly what the vulnerability is
- **Document assumptions**: If something is unclear, write down your assumptions
- **Focus on the goal**: The agent should analyze, understand, fix, and validate

## FAQ

**Q: Can I use ChatGPT/Claude/other AI tools to help build my agent?**
A: Yes! This assignment is about building an AI agent - using AI/LLM APIs is expected and encouraged.

**Q: Should I research CWE-22 online?**
A: Yes! Start by researching CWE-22 (Path Traversal) online using the provided links (CWE, OWASP) and any other sources. Understanding the vulnerability is crucial for building your agent.

**Q: Should my agent search the web at runtime?**
A: No. You research online first, then your agent should analyze the code and use LLM capabilities (with CWE-22 context in prompts) to determine and apply the fix.

**Q: What if I can't finish in 3 hours?**
A: Submit what you have with notes on what's incomplete. We value honesty and want to see your approach.

**Q: Can I modify the test file?**
A: No - the tests demonstrate the vulnerability. Your agent should fix `file_reader.py`, not the tests.

**Q: How detailed should my REPORT.md be?**
A: 1-2 pages is sufficient. Focus on your agent's approach, what worked, and honest evaluation.

---

**Questions?** If anything is unclear, document your assumptions in REPORT.md.

Good luck! 🚀
