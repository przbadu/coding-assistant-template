# Three important folders

Get more examples of what contents to put inside these directories from:

https://github.com/przbadu/pocket-pick

## 1. ai-docs

This is your AI coding tools persistent memory. A knowledge repository your ai tools can instantly access.

`ai-docs` contains all the ai documentations, third party documentation that are helpful for the AI tools like [claude code](https://docs.anthropic.com/en/docs/claude-code/overview), [cline](https://cline.bot/), [aider](https://aider.chat/), [codex](https://github.com/openai/codex) etc.

It can contains:

- API docs & integrations
- Architecture docs / design docs
- Hidden non-code business logic
- Project-specific patterns

## 2. ai-specs (Specifications / Plan)

These are your specifications. Also known as `PRDs`, feature documents, or in simple words plans. This is where you detail the work you want done before handing it off to your ai tools.

> PLAN == PROMPT
>
> GREAT PLANNING == GREAT PROMPTING

## 3. .claude (or .llm)

Reusable prompts you can use with your ai tools. This reduces the time it takes to run repeat workflows in your codebases and in your ai tools. Although this is specific to Claude Code, the reusable prompts are not limited to any specific ai tooling.

```
.claude
  | - commands
  |   - context_prime.md
  settings.json
```

** `context_prime.md` example prompt

```md
READ README.md, THEN run git ls-files to understand the context of the project.
```

This simple prompt if given to ai coding assistent will have context of your entire project.

> NOTE: if you use .claude directory you can directly access context_prime by typing `/` in claude code.

### Example ultra diff review
**Not limited to context prime**: You can create `ultra-diff-review` and any other context as you like.

```markdown
# Ultra Diff Review
> Execute each task in the order given to conduct a thorough code review.

## Task 1: Create diff.txt

## Task 2: git diff and append

Then run git diff and append the output to the file.

## Task 3: just-prompt multi-llm tool call

Then use that file as the input to this just-prompt tool call.

prompts_from_file_to_file(
  from_file = diff.md,
  models = "openai:03-mini, anthropic:claude-3-7-sonnet-20250219:4k, gemini:gemini-2.0-flash-thinking-exp",
  output_dif= ultra_diff_review/
)

## Task 4: Read the output files and synthesize

Then read the output files and think hard to synthesize the results into a new single file called `ultra_diff_review/fusion_ultra_diff_review.md` following the original instructions plus any additional instructions or callouts you think are needed to create the best possible review.
```

