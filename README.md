# Copilot Studio harness matrix

A dated capability matrix for the three Microsoft Copilot Studio agent harnesses, with the
source page linked beside every row.

**Start here: [MATRIX.md](MATRIX.md).** What has already changed is in
[HISTORY.md](HISTORY.md).

## Why this repository exists

Copilot Studio asks you to pick a harness before you build anything, and that pick decides how
the agent reasons, how it is billed, what can call it, and what you can observe about it. The
answers are spread across the harness overview, the Power Automate connector article, the
telemetry articles, a guidance article, and the pages for each harness. Nobody wants to re-read
six pages to answer "can a flow call this one."

So this is the one page, with the date and the source on every claim.

It accompanies [The Workbench](https://www.theworkbench.blog), and specifically
[The Agent Your Flow Can't Call](https://www.theworkbench.blog/2026/09/copilot-studio-agent-your-flow-cant-call.html)
(2026-09-21), which argued that the harness is an architectural decision wearing the costume of
a product setting, and sketched this matrix as the file that would make such a repository worth
cloning. This is that file, built.

## How it was produced, and how to check it

Every row was read from Microsoft Learn on **2026-10-30** and carries a link to the page it came
from. Nothing here was measured in a tenant, and the matrix says so at the top rather than
leaving you to assume otherwise.

To check any row, open its linked page. That is the whole verification procedure, and it is
deliberately the only one, because a matrix you cannot re-derive is a matrix you have to trust.

Two rules the cells follow:

- A cell reads **Not stated** when the documentation does not answer the question for that
  harness. Not stated is not the same as unsupported, and conflating the two is the fastest way
  to publish something false.
- Quoted phrasings such as "Not a focus" are Microsoft's words from the comparison table, kept
  verbatim rather than translated into a yes or a no.

## Scope

In scope: what the documentation says about each harness, with dates and sources.

Out of scope: tenant measurements, exported solutions, and anything that needs a licensed
environment to produce. Those belong in a lab repository, and this is not one.

## Contributing

This repository is a publishing surface for the blog rather than a community project, so it does
not accept pull requests. If a row no longer matches what Microsoft Learn says, the comments on
the related blog post are the right place, and that is where corrections come from.

## License

MIT. See [LICENSE](LICENSE).
