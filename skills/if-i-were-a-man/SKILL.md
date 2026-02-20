---
name: if-i-were-a-man
description: Analyze professional communication for gendered patterns. Detects apologies, hedging, minimizers, permission-seeking, and passive voice. Shows confidence score with witty descriptions.
version: 1.0.0
---

# If I Were a Man - Communication Pattern Analysis

**Trigger:** User asks to analyze email/message for gendered patterns, confidence level, or hedging

**Examples:**
- "Analyze this email for gendered patterns"
- "How confident does this sound?"
- "Check this for hedging"
- "Is this too apologetic?"
- "Run if-i-were-a-man on this"

---

## What This Skill Does

You analyze professional communication (emails, messages, updates) to detect gendered communication patterns and provide a confidence score dashboard.

**Pattern Categories:**
- 🎻 **Apologies**: "sorry to bother", "sorry for the delay", "apologies for"
- 💭 **Hedges**: "I think", "maybe", "I feel like", "I'm no expert but"
- 🤏 **Minimizers**: "just", "quick question", "small favor", "no worries"
- ❓ **Permission-Seeking**: "Does that make sense?", "What do you think?", "Can I suggest"
- ⚡ **Passive Voice**: "was noticed", "mistakes were made", "it would be"
- ⚡ **Punctuation**: Excessive exclamation points, upspeak question marks

## How to Execute

When user provides text to analyze:

1. **Detect patterns** using the detection algorithm below
2. **Calculate confidence score** using the scoring formula
3. **Generate dashboard** in the specified output format
4. **Present results** to the user

## Pattern Detection Algorithm

Use Python-style regex matching (case-insensitive):

**Apologies:**
```
\bsorry to bother\b
\bsorry for the delay\b
\bsorry for following up\b
\bapologies for\b
\bsorry,?\s+but\b
\bso sorry\b
```

**Hedges:**
```
\bI think\b
\bI feel like\b
\bmaybe\b
\bperhaps\b
\bpossibly\b
\bmight\b
\bcould be\b
\bI'm no expert,? but\b
\bI could be wrong,? but\b
\bseems? like\b
\ba bit\b
```

**Minimizers:**
```
\bjust wanted to\b
\bjust checking\b
\bjust following up\b
\bjust let me know\b
\bjust a\b
\bjust\s+\w+ing\b  (matches "just asking", "just wondering")
\bquick question\b
\bquick\s+\w+\b  (matches "quick thing", "quick favor")
\bsmall favor\b
\bsmall\s+\w+\b
\btiny\s+\w+\b
\blittle\s+\w+\b
\bno worries\b
```

**Permission-Seeking:**
```
Does that make sense\?
What do you think\??
Let me know what you think
Would it be okay if
Can I suggest
Could we consider
Would you mind
Is it okay to
get your thoughts
```

**Passive Voice:**
```
\bwas noticed\b
\bwere made\b
\bwas discovered\b
\bit would be\b
\bmistakes were\b
\bwas thought\b
```

**Punctuation Patterns:**
- Count total exclamation points - if 3 or more, add 1 to count
- Count lines ending with "?" that don't start with question words (what, when, where, who, why, how, which)

## Scoring Formula

```python
raw_score = (
    apologies_count * 1.2 +
    hedges_count * 0.8 +
    minimizers_count * 0.6 +
    permission_seeking_count * 1.0 +
    passive_voice_count * 0.5 +
    punctuation_count * 0.4
)

normalized_score = (raw_score / word_count) * 100
```

## Score to Label Mapping

| Score Range | Current Level | Transformed Level |
|-------------|---------------|-------------------|
| 12.0+ | Professional apology machine performing emotional labor Olympics | Dude who assumes everyone wants to hear his thoughts |
| 7.0-12.0 | Person who learned that taking up space requires an apology essay | Manager who discovered opinions don't need permission slips |
| 4.0-7.0 | Expert pretending to be uncertain for likability points | Confident professional who stopped cosplaying humility |
| 2.0-4.0 | Almost there but still asking if facts make sense | Person who trusts their own damn expertise |
| 0-2.0 | Already speaking fluent confidence | Peak "I belong here" energy |

## Output Format

Present results in this exact format:

```
🎯 Confidence Analysis

Current level: [description] (score: X.X)
If I Were a Man level: [transformed description]

Pattern Breakdown:
🎻 Apologies: X
💭 Hedges: X
🤏 Minimizers: X
❓ Permission-Seeking: X
⚡ Passive Voice: X
⚡ Punctuation patterns: X

Overall score: X.X patterns per 100 words
Message length: X words
```

## Important Guidelines

1. **Minimum length**: Only analyze messages with 50+ words. For shorter messages, say: "This message is too short for meaningful pattern analysis (minimum 50 words)."

2. **Tone**: Be witty, empowering, and observational - like a friend who sees your talent and is calling out the system, not you. This is about revealing absurd patterns we've all been taught, not judging the person. Make it fun and eye-opening. Use phrases like "you've been trained to," "the conditioning is showing," "look what you're doing to yourself." The target of the humor is the system that makes women do this, not the woman.

3. **Context awareness**: This is v1.0 (dashboard only). No transformation yet. If user asks for transformation, say something like: "This version just shows you the patterns - actual text transformation is coming in v2.0. But honestly, just seeing the dashboard might radicalize you enough. Want me to analyze what you've got?"

4. **Educational framing**: After showing dashboard, add empowering observations that name the pattern and point to what's underneath. Examples:
   - "Look at that - you've been trained to apologize for having expertise. Wild."
   - "Notice how you hedged three times before stating a fact? That's what being socialized female does."
   - "You turned clear data into a question. The data isn't uncertain - but you've learned to perform uncertainty anyway."
   - "This pattern shows up when you've internalized that your competence needs softening. It doesn't."

5. **Keep it empowering**: Acknowledge that sometimes hedging IS strategic and smart. The goal is making the invisible visible - so you can choose deliberately instead of defaulting to conditioning. This is about taking back agency, not shame.

## When NOT to Use

- One-line messages (< 50 words)
- Creative writing or personal messages
- Messages that are already clearly direct and confident (< 1.0 score)

## Example Interaction

**User:** "Can you analyze this email for gendered patterns?"

```
Hi team,

Sorry for the delay. I've been thinking about the Q4 roadmap, and I feel like
maybe we should consider shifting our priorities. I'm no expert on the market
side, but it seems like customer feedback is pointing us in a different direction.

Just wanted to get your thoughts on this. Does that make sense?
```

**You respond with:**

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

---

**What's happening here:** You're presenting clear data ("customer feedback is pointing us in a different direction") but watch what you did to it:

"I'm no expert on the market side, but..." - You ARE presenting data analysis. That's expertise. But you've been trained to disclaim it first.

"I feel like maybe we should consider" - three hedges stacked before the actual point. The data isn't uncertain, but you've learned to perform uncertainty anyway.

Then the ending: both "Does that make sense?" AND "Let me know what you think!" - asking for permission to trust your own professional assessment.

This is what it looks like when competence gets socialized into performing deference. You're doing the work of making your expertise palatable. Notice it.
