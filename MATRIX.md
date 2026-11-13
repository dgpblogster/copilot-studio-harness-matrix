# Copilot Studio harness capability matrix

**Read from Microsoft Learn on 2026-11-13.** Every row links the page it came from.

**Naming, 2026-11-13.** What this matrix called the **GitHub Copilot harness** through
2026-10-30 is now the **Microsoft Copilot harness**. Microsoft renamed it; nothing in the
capability rows changed with the name. The upgrade article's URL still contains
`github-copilot` and still resolves, so the links below are unchanged. See
[HISTORY.md](HISTORY.md).

**What this is and is not.** This matrix is read out of documentation, not measured in a
tenant. A cell says what Microsoft publishes today, which is not always the same as what a
tenant does today. Where the documentation does not state an answer, the cell says
**Not stated** rather than guessing, because an inferred cell in a compatibility matrix is
indistinguishable from a measured one three months later.

**Why the date is at the top.** A harness matrix with no date ages into confident
misinformation. If you are reading this more than a few weeks after the date above, re-check
the linked pages before you rely on a row. [HISTORY.md](HISTORY.md) records what has already
moved.

## The three harnesses

Per [Harnesses in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview),
everything built in Copilot Studio runs on one of three harnesses:

| Harness | Built for | Billing |
|---|---|---|
| **Microsoft Copilot harness** | Reasoning-heavy, multi-step work | Copilot Credits (usage-based) |
| **Customer Conversation harness** (preview) | Customer questions and issues over voice and chat | Copilot Credits (usage-based) |
| **Standard harness** | Rule-based agents and agent flows | The Copilot Studio licensing model |

An agent built on the Customer Conversation harness is called a **Customer Assist Agent**.

## Integration: what can call the agent

| Capability | Microsoft Copilot | Customer Conversation | Standard | Source |
|---|---|---|---|---|
| Callable from a Power Automate cloud flow via the Microsoft Copilot Studio connector | **No**, stated explicitly | **Not stated** | **Yes** (Execute Agent, Execute Agent and wait) | [call-copilot-studio-agent](https://learn.microsoft.com/en-us/power-automate/call-copilot-studio-agent) |
| Callable from an agent node in a Copilot Studio workflow | **Yes** | **Not stated** | **Not stated** | [call-copilot-studio-agent](https://learn.microsoft.com/en-us/power-automate/call-copilot-studio-agent) |
| Publishing targets | Internal teams or external customers | Website chat, or a phone number | Internal teams or external customers | [harnesses-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview) |

The connector article's table still has exactly two rows, Standard and Microsoft Copilot. It does
not mention the Customer Conversation harness, which is why two cells above read Not stated.

## Observability

| Capability | Microsoft Copilot | Customer Conversation | Standard | Source |
|---|---|---|---|---|
| Agent-level Application Insights telemetry | **No** | **Not stated** | **Yes**, this scope is standard-harness only | [telemetry-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/telemetry-overview) |
| Environment-level Application Insights telemetry (preview) | **Yes** | **Not stated** | **Yes** | [telemetry-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/telemetry-overview) |

Environment-level telemetry is available only in managed environments, only in Microsoft public
cloud environments, and does not support unauthenticated or multi-tenant agent configurations.
It also does not capture TopicStart, TopicAction or TopicEnd events, and the duration value is
absent from traces of standard-harness agents. See
[advanced-environment-level-agent-telemetry](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-environment-level-agent-telemetry).

## Capabilities

| Capability | Microsoft Copilot | Customer Conversation | Standard | Source |
|---|---|---|---|---|
| Skills and memory | **Yes** | **Yes** | Not a focus | [harnesses-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview) |
| Creates, edits and reasons over Word, Excel, PowerPoint and PDF files | **Yes** | Not a focus | Not a focus | [harnesses-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview) |
| How it recovers when something fails | Retries and finds alternative paths automatically | Escalates to a human representative through a defined path | Follows the paths you built | [harnesses-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview) |
| Reasoning models and emerging agentic capabilities | **Yes** | **Not stated** | **No** | [guidance/choose-harness](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/choose-harness) |
| Tools across connectors, knowledge, MCP and connected agents | **Yes** | **Yes** | **Yes** | [harnesses-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview) |
| Escalate and Biometric Authentication tools | **Not stated** | **Yes** | **Not stated** | [overview-customer-conversation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/overview-customer-conversation) |

## Published runtime limits

These are Microsoft Copilot harness limits, and the page says Microsoft manages the values and can
change them. Source: [agents-experience/runtime-limits](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/runtime-limits).

| Limit | Default | What happens at the limit |
|---|---|---|
| Turn duration | 90 minutes | Steered to wrap up at about 60 minutes; the service stops the turn at 90 |
| Tool calls per turn | 200 | The agent stops calling tools and the turn ends |
| Tool call timeout | 120 seconds | Cancelled, error result returned to the agent |
| Workflow tool timeout | 660 seconds | Times out, the agent receives an error |
| Connected agent timeout | 5,400 seconds | Times out, the agent receives an error |
| External agent timeout | 300 seconds | Times out, the agent receives an error |
| Messages kept in the conversation window | 100 | Oldest messages dropped from working history |

Separately, files an agent creates during a turn are capped at 10 MB each, and MCP servers count
against an agent's total tool count with a cap on concurrent server instances per conversation.
Those two limits are documented as applying to **both** the Microsoft Copilot and Customer
Conversation harnesses. Source:
[agents-experience/tools-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/tools-overview).

## Changing harness after the fact

| Path | Status | Source |
|---|---|---|
| Standard harness to Microsoft Copilot harness | Documented, **preview** | [upgrade-to-github-copilot-from-standard-harness](https://learn.microsoft.com/en-us/microsoft-copilot-studio/upgrade-to-github-copilot-from-standard-harness) |
| Microsoft Copilot harness to standard harness | **No documented path** | n/a |
| Either direction, to or from the Customer Conversation harness | **No documented path** | n/a |

The documented upgrade creates a **copy** of the agent on the Microsoft Copilot harness, named with
an "(Upgraded)" suffix. It carries over instructions, tools and suggested prompts, can rebuild
custom topics as skills or workflows, reports what migrated and what needs attention, and
consumes Copilot Credits.

**What the upgrade does not migrate**, per the Limitations section of that page:

- Knowledge sources
- Power Fx expressions
- Child agents

Microsoft's own guidance on whether to use it is worth reading next to it.
[Compare Copilot Studio agent harnesses](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/choose-harness)
says to treat migration as re-architecture rather than component conversion, that it is complete
when the rebuilt agent performs its core journeys rather than when every old component is
mechanically reproduced, and that a functioning standard harness agent does not need to move
simply because another harness is available.

## Where the three-harness model has and has not landed

The overview article describes three harnesses. The pages that draw actual capability boundaries
are catching up unevenly, which is the single most useful thing to know when reading any harness
page right now.

| Page | Harnesses it treats |
|---|---|
| [harnesses-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview) | Three |
| [agents-experience/tools-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/tools-overview) | Names Microsoft Copilot and Customer Conversation together |
| [guidance/choose-harness](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/choose-harness) | Standard and Microsoft Copilot only, despite the title |
| [call-copilot-studio-agent](https://learn.microsoft.com/en-us/power-automate/call-copilot-studio-agent) | Standard and Microsoft Copilot only |
| [telemetry-overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/telemetry-overview) | Standard and Microsoft Copilot only |

This is a platform mid-move, not an error. It does mean that "the docs do not say X about the
Customer Conversation harness" is usually the honest reading, rather than "X is unsupported."
