# What has already moved

This file exists because the matrix it sits next to is about a platform that is actively
changing, and a reader arriving later needs to know how fast the rows move. Each section is
dated by when the state was read from Microsoft Learn, not by when Microsoft shipped anything.

## Read 2026-10-30

**Three harnesses, and the third one is new.** The overview now compares the **GitHub Copilot
harness**, the **Customer Conversation harness** (preview) and the **standard harness**.

The Customer Conversation harness arrived with roughly 45 pages. It builds a **Customer Assist
Agent** for voice and chat: a multi-agent architecture of sub-agents that each carry their own
escalation path to a human representative, prebuilt **Escalate** and **Biometric
Authentication** tools, a **Foundry IQ** knowledge connection, and a Build / Preview / Evaluate
/ Deploy / Monitor tab surface. It publishes to a website chat or a phone number. It bills in
Copilot Credits.

**The Copilot chat harness is no longer the third harness in the overview.** Earlier in 2026 the
overview's third harness was the Copilot chat harness, described as extending Microsoft 365
Copilot Chat. Its rows were removed from the overview's comparison tables when the Customer
Conversation harness was added. Anything written against the earlier three-harness lineup names
a harness that the overview no longer lists.

**A documented upgrade path appeared, and guidance appeared telling you how to think about it.**
[Upgrade agents to the GitHub Copilot harness](https://learn.microsoft.com/en-us/microsoft-copilot-studio/upgrade-to-github-copilot-from-standard-harness)
is in preview: ask Copilot Studio in natural language, get an "(Upgraded)" copy. Alongside it,
[Compare Copilot Studio agent harnesses](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/choose-harness)
is new long-form guidance that says to treat migration as re-architecture rather than component
conversion, and that migration should be a business-case decision rather than a default upgrade.

**The Power Automate connector constraint is unchanged.** Re-read on this date:
[Call Microsoft Copilot Studio agents from Power Automate](https://learn.microsoft.com/en-us/power-automate/call-copilot-studio-agent)
still carries a two-row table. A standard harness agent is callable from a cloud flow through
the Microsoft Copilot Studio connector; a GitHub Copilot harness agent is not, and is reached
through an agent node inside a Copilot Studio workflow instead.

## Read 2026-09-21 (for contrast)

The overview listed three harnesses: GitHub Copilot, standard, and **Copilot chat**. The
Power Automate connector table had the same two rows it has today. The capability boundaries
documented at that point were the connector split, the agent-level telemetry split
(standard-harness only), and coding-agent skills being GitHub Copilot harness only. No upgrade
path between harnesses was documented.
