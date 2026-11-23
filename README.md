# software-testing-qa-assignment-41378-nikita
## Contents
- Module assignments
- Week assignments

## Tools
Selenium, TestNG, Maven, Java, Python, SQL

## How to use this repository
Each assignment is submitted on its own branch and merged through a pull request.

run the tests..

## Fork-and-PR Contribution Evidence

### Fork
- Original repository: https://github.com/nikita1908-AT/software-testing-qa-assignment-41378-nikita
- Fork (in my organization): https://github.com/nikita-test-lab/software-testing-qa-assignment-41378-nikita
- Contribution branch in the fork: `docs/improve-readme`

### Documentation improvement
The original README had only a title and one line, so there was no typo to fix.
I improved the documentation instead:

- Before: title and a single description line.
- After: added **Contents**, **Tools**, **How to use this repository** and
  **Running tests** sections (commits `da15717`, `b1d0834`).

### Pull request
- PR #1: https://github.com/nikita1908-AT/software-testing-qa-assignment-41378-nikita/pull/1
  (from `nikita-test-lab:docs/improve-readme` into `main`)

PR description:

> **Summary:** Expands the README, which only had a title and one line,
> with a contents list, the tools used and a short usage note.
>
> **Testing notes:** Previewed the README on GitHub; headings and lists
> render correctly. Docs-only change, so no code or tests are affected.

### Review comment and response
- Review comment: "Please also add a line about how to run the tests."
- My response: added a "Running tests" section (`mvn test`) in commit
  `b1d0834`, replied "Added in latest commit" in the thread and resolved it.

### Branch protection
A ruleset on `main` requires a pull request before merging, so direct pushes
are blocked (see the Branch Protection section above).
