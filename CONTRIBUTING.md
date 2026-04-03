Contributing to Web Data Extractor
Thank you for your interest in contributing! This document explains how to get set up, our conventions, and the process for submitting changes.

Table of Contents
Code of Conduct
Getting Started
Development Workflow
Commit Conventions
Pull Request Process
Reporting Bugs
Requesting Features
Code of Conduct
This project follows the Contributor Covenant Code of Conduct. By participating, you agree to uphold it.

Getting Started
Prerequisites
Node.js v24+
pnpm v10+
Setup
git clone https://github.com/your-org/web-data-extractor.git
cd web-data-extractor
pnpm install
Running the project locally
# Terminal 1: API server
pnpm --filter @workspace/api-server run dev
# Terminal 2: Frontend
pnpm --filter @workspace/web-extractor run dev
After changing the OpenAPI spec
pnpm --filter @workspace/api-spec run codegen
Development Workflow
Fork the repository and create a branch from main:

git checkout -b feat/your-feature-name
Make your changes. Keep each PR focused on a single concern.

Typecheck before pushing:

pnpm run typecheck
Build to confirm there are no build-time errors:

pnpm run build
Push your branch and open a Pull Request.

Commit Conventions
We use Conventional Commits:

<type>(<scope>): <short summary>
Types:

Type	When to use
feat	A new feature
fix	A bug fix
docs	Documentation changes only
style	Formatting, whitespace (no logic change)
refactor	Code restructuring (no feature/fix)
perf	Performance improvements
test	Adding or updating tests
chore	Build process, dependency updates
Examples:

feat(extractor): add support for nested table extraction
fix(api): handle 429 rate-limit responses correctly
docs: update API reference in README
Pull Request Process
Ensure pnpm run typecheck and pnpm run build pass.
Fill out the PR template completely.
Link any related issues using Closes #<issue-number>.
Request a review from a maintainer.
Address all review comments before merging.
PRs are merged using squash merge to keep the history clean.
Reporting Bugs
Use the Bug Report issue template. Include:

A clear description of what happened vs. what you expected
Steps to reproduce (URL you tried, options you used)
Any error messages shown in the UI or browser console
Requesting Features
Use the Feature Request issue template. Describe:

The problem you're trying to solve
Your proposed solution
Any alternatives you've considered
