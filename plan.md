# Chore Bot Scope

## Goal and users

A Telegram bot that keeps a shared, always-current chore list so nothing is forgotten or done twice.

- **Users:** 2 parents in one family group chat.
- **Kids:** 2 small children who don't use the tool; their chores are items the parents manage.

## In-scope features

| Area | Decision |
| --- | --- |
| Chore types | One-off tasks and recurring chores |
| Repeats | Fixed interval ("every 3 days") or since last done ("3 days after last done") |
| Ownership | Unassigned, claimed by a parent, or assigned to one; either parent can reassign |
| Input | Natural language in the group chat, parsed by an LLM |
| Proactive messages | Daily morning digest: what's due, what's overdue, who owns it |
| Overdue recurring chores | Shown in the digest; a parent decides to skip or keep |
| History | Undo of the last action, plus a full log of who added, claimed, or finished what, and when |

## Tech choices

- **Platform:** Telegram bot in the family group chat.
- **Parsing:** LLM (e.g. the Claude API); needs an API key.
- **Runtime:** runs locally on a laptop.
- **Storage:** SQLite.

## Out of scope and risks

**Out of scope**

- Kids' features (accounts, rewards, visuals)
- Fairness stats (who did how much)
- Multiple households
- Always-on hosting (stretch goal)

**Risks**

- The LLM may misread an input, and there is no confirmation step; undo is the safety net.
- The morning digest only goes out while the laptop is on.
