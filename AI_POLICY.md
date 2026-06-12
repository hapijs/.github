# AI-assisted contributions

This policy applies to any contribution produced with the assistance of large language models (LLMs), code generation tools, or similar AI systems. It restates expectations that have always applied to all contributions, and adds rules that exist to protect the time and motivation of the humans who review them.

Reviewing a change takes longer than writing one, and AI tools have made writing nearly free while review remains expensive. These rules rebalance that. They are written so that a maintainer can apply them without debating quality or guessing intent.

## Rules for outside contributions

### 1. Disclose all AI use

If AI assisted your contribution in any form, say so. State the tool and the extent of the assistance in the pull request description, and add an `Assisted-by:` trailer to your commit messages:

```
Assisted-by: Claude Code:claude-sonnet-4-6
```

Do not use `Co-authored-by:` for AI tools; that trailer is reserved for humans.

Trivial mechanical assistance is out of scope and needs no disclosure: spelling and grammar fixes, identifier completion, and formatting.

If you do not disclose AI use and a maintainer suspects it, the contribution will be closed. We will not argue about whether the suspicion is correct. Disclosure costs you one line; non-disclosure costs you the contribution.

### 2. AI-assisted pull requests require an accepted issue

A pull request produced with AI assistance must reference an accepted issue: one a maintainer has labeled `help wanted` or confirmed in a comment as ready for work. Drive-by pull requests will be closed without review, regardless of their quality.

This is the rule that protects reviewers. An accepted issue means the problem is real, the approach has been discussed, and a human on the team has already decided the work is worth doing. If you believe you have found a real problem, open an issue first. That is a contribution too, and often a more valuable one.

### 3. You must be able to defend every line

A contribution is yours the moment you open a pull request. You must be able to explain every line: why it exists, what it replaces, and what breaks if it is removed. Reviewers will ask, and your answers must be your own. If you cannot defend a change under review, or your responses read like they were generated for you, the contribution will be closed. This was true before AI tools existed.

### 4. Verify before you submit

Do not submit code you have not run. AI tools produce plausible code that has never been executed; running the tests yourself is the minimum bar. Do not use AI to write code for platforms or environments you cannot test on.

### 5. Issues and discussions: AI assistance is welcome, with a human in the loop

You may use AI to investigate, translate, or draft issues and discussion posts. Everything you submit must have been read, verified, and trimmed by you first. If you report a bug, you must be able to reproduce it yourself, not merely relay what a tool told you. AI output is verbose by default; cutting it down is your job, not the reader's.

### 6. Repeated violations result in a ban

We want to help contributors learn. But repeated or intentional violations of this policy shift work onto maintainers and erode the trust this project runs on, and will result in being banned from contributing.

## Standing expectations (all contributions, AI or not)

- **Change the minimum necessary.** Every diff should contain exactly the changes required to solve the stated problem and nothing else. Do not refactor adjacent code, rename unrelated variables, reformat files, or "improve" things that were not broken.
- **Tests are not optional, and they must have a purpose.** All code must be tested, and every test must prove something real: a bug-fix test fails without the fix; a feature test demonstrates the promised behavior. Test functionality and outcomes, not implementation details. Tests written for the sake of having tests will be treated the same as no tests at all.
- **Document what you change.** API changes without corresponding documentation updates will not be merged.
- **Respect the reader.** This applies to everything you write: PR descriptions, issues, comments, replies, and comments in code. AI output tends toward walls of text — long, jargon-heavy, and padded with restatements of what the code already says. If you use AI to write, fixing that is your job before you submit. Keep it short and plain enough that a human can read it once and understand it. Say what the code cannot say for itself — the why, not a narration of the diff. If you cannot get through your own PR description, we are not going to get through it either.
- **You are operating in a social environment.** The hapi ecosystem serves thousands of applications in production. Consider downstream consumers. Consider the humans who will debug the next issue.

## Maintainers

These rules apply to outside contributions. Core maintainers may use AI tools at their discretion: they have demonstrated judgment, they own the consequences, and they will live with the code long after a drive-by contributor has moved on.

Maintainer discretion is not maintainer exemption from quality. AI-assisted maintainer work goes through the same peer review as any other change, and maintainers hold each other to the same bar this policy holds contributors to.

## Why this policy is not a ban

Parts of the hapi ecosystem are built with AI assistance, and some maintainers use these tools daily. We are not anti-AI. We are against unverified work being handed to reviewers as if verification were their job. It is the people driving the tools, not the tools, that determine quality, and most unsolicited AI-generated contributions we receive do not clear the bar.

A full ban would be honest only if we stopped using these tools ourselves, and it would still be unenforceable: there is no reliable way to detect AI-generated code. What can be enforced is everything above: disclosure, an accepted issue, and a contributor who can stand behind their work. We would rather state rules we can apply than a principle we would quietly violate.

The tool you use is your business. The quality, correctness, and minimal scope of what you submit is ours.
