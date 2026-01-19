# Talk to the code

You can use Copilot in **Ask** mode, **Agent** mode, or run it in the background.

## Architecture

Prompt (generate solution-wide architecture diagram, ignore `docs/`):

```text
Generate a diagram in arch-pl.md using Mermaid for the entire solution. I want to understand it better. Do not use files from the docs folder; analyze the full source code.
```

![alt text](image.png)

If you get an error, paste it back in (LLMs are not deterministic).

![alt text](image-1.png)

Compare with a docs-based view:

```text
Generate a diagram in arch-pl-docs.md using Mermaid for the entire solution. I want to understand it better.
```

## Backend file documentation

```text
Generate backend-plik-pl.md with documentation for every backend source file. Include:
- file path
- short (one-sentence) purpose
- a longer paragraph describing behavior
- every class and function with a one-sentence role summary
```

## How "chunking" works

```text
Explain how chunks are generated for the vector database. Is it done online (on demand) or as a one-time batch? How are new documents added?
```

## Entra ID auth: where and how

```text
Where is Entra ID authentication implemented in this solution, and what needs to be done to enable it?
Also explain how Entra-based ACL works and what is required to turn it on (for Auto!).
```

## Add Content Safety / grounding checks

```text
Where should I add Content Safety checks in this solution to validate responses? (Hint: partially added already.)
Also: where should I add a groundedness check? (Hint: partially added already.)
```
