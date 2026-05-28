# AI-assisted contributions

This policy applies to any contribution produced with the assistance of large language models (LLMs), code generation tools, or similar AI systems. It does not introduce new standards. It restates existing expectations that have always applied to all contributions, regardless of how they were produced.

## You are responsible for what you submit

A contribution is yours the moment you open a pull request. You must be able to explain every line: why it exists, what it replaces, and what breaks if it is removed. If you cannot defend a change under review, it will be closed. This was true before AI tools existed.

## Change the minimum necessary

Every diff should contain exactly the changes required to solve the stated problem and nothing else. Do not refactor adjacent code, rename unrelated variables, reformat files, or "improve" things that were not broken. Unrelated changes obscure review, introduce risk, and waste maintainer time.

## You are operating in a social environment

The hapi ecosystem serves thousands of applications in production. A change to a public API, a shifted default, or a modified behavior can break things for a lot of people. Treat every modification with the gravity it deserves. Consider downstream consumers. Consider the humans who will debug the next issue.

## Tests are not optional

Nothing will be accepted without tests. Contributions must include tests that demonstrate the change works and that document the intended behavior. If you are fixing a bug, include a test that fails without the fix. If you are adding a feature, include tests that cover its contract.

## Document what you change

If a contribution affects the public API, introduces side effects, or has implications for users, those must be addressed in the documentation. API changes without corresponding documentation updates will not be merged.

## What this means in practice

- Do not submit AI-generated code you have not read, understood, and verified.
- Do not use AI tools to generate large speculative refactors and submit them as contributions.
- Using AI for commit messages, PR titles, and PR descriptions is fine. But you must read the result before submitting. If it contains fluff, hyperbole, marketing language, or walls of text that are difficult to get through — rewrite it. Keep it clear, intentional, and concise. If you cannot get through your own PR description, we are not going to get through it either.
- You must still be able to defend and explain your changes in review. The description can be AI-written; the understanding cannot be.
- Do not submit bulk formatting, linting, or style changes produced by AI unless explicitly requested by a maintainer.

The tool you use is your business. The quality, correctness, and minimal scope of what you submit is ours.
