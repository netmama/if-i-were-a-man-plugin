# If I Were a Man

A [Claude Code](https://claude.ai/claude-code) skill that analyzes professional communication for gendered patterns.

Paste an email, Slack message, or any professional text and get a confidence analysis dashboard that reveals the invisible patterns: the apologies, the hedging, the minimizers, the permission-seeking — all the ways women have been socialized to soften their expertise.

## What It Detects

| Pattern | Example |
|---------|---------|
| 🎻 **Apologies** | "Sorry to bother you", "Sorry for the delay" |
| 💭 **Hedges** | "I think", "maybe", "I feel like", "I'm no expert but" |
| 🤏 **Minimizers** | "just wanted to", "quick question", "no worries" |
| ❓ **Permission-Seeking** | "Does that make sense?", "What do you think?" |
| ⚡ **Passive Voice** | "was noticed", "mistakes were made" |
| ⚡ **Punctuation** | Excessive exclamation points, upspeak question marks |

## Example Output

```
🎯 Confidence Analysis

Current level: Person who learned that taking up space requires an apology essay (score: 11.0)
If I Were a Man level: Manager who discovered opinions don't need permission slips

Pattern Breakdown:
🎻 Apologies: 1
💭 Hedges: 4
🤏 Minimizers: 1
❓ Permission-Seeking: 3
⚡ Passive Voice: 0
⚡ Punctuation patterns: 0

Overall score: 11.0 patterns per 100 words
Message length: 73 words
```

## Install

### Manual install

Copy `skills/if-i-were-a-man/SKILL.md` into your `~/.claude/skills/if-i-were-a-man/` directory.

## Usage

In Claude Code, use the `/if-i-were-a-man` command or just ask:

- "Analyze this email for gendered patterns"
- "How confident does this sound?"
- "Check this for hedging"
- "Is this too apologetic?"

Then paste your text.

## Philosophy

This isn't about judging anyone's communication style. It's about making the invisible visible — so you can choose deliberately instead of defaulting to conditioning. Sometimes hedging IS strategic and smart. The goal is agency, not shame.

## License

MIT
