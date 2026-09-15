# Agent Access Setup

This repository is intended to be collaboratively worked on by ChatGPT, Claude Code, and Mistral Vibe.

## ChatGPT

The connected GitHub integration already has repository admin/push access for `NTinkicht/SecureMedRAG-Bench`.

## Claude Code

Recommended collaboration mode: install the official Claude GitHub App and use the repository workflow at `.github/workflows/claude.yml`.

### One-time setup

1. Install the official Claude GitHub App on **only** `NTinkicht/SecureMedRAG-Bench` unless broader access is intentionally desired.
2. If using a Claude Pro/Max subscription, generate a Claude Code OAuth token locally:

   ```bash
   claude setup-token
   ```

3. In GitHub, open:

   `SecureMedRAG-Bench -> Settings -> Secrets and variables -> Actions -> New repository secret`

4. Create a secret named exactly:

   `CLAUDE_CODE_OAUTH_TOKEN`

5. Paste the generated token as the value.

6. Test by opening an issue and commenting:

   `@claude Read AGENTS.md and CLAUDE.md, then review this issue.`

The committed workflow grants the job repository-content write, pull-request write, issue write, Actions read, and OIDC token permissions. Claude should work through branches/PRs rather than pushing research-changing work directly to `main`.

Alternative setup: run Claude Code locally in a clone of the repository. Local Git permissions then determine what Claude can push.

## Mistral Vibe Code Web

Recommended collaboration mode: Vibe Code Web with the official Mistral GitHub App.

### One-time setup

1. Open Vibe Code Web.
2. Start the GitHub connection flow.
3. Install/authorize the **Mistral GitHub App** for the GitHub account `NTinkicht`.
4. Choose **Selected repositories** and select only `SecureMedRAG-Bench`.
5. Create a Vibe Code project named `SecureMedRAG-Bench` and attach the repository.
6. Start the first session with:

   `Read AGENTS.md and the repository README completely. Treat this as a scientific research project. Work only through a dedicated branch and PR. Begin by auditing the current research plan for novelty, methodological weaknesses, dataset risks, and missing security threat classes. Record findings in the repository rather than inventing experimental results.`

Vibe Code Web uses the Mistral GitHub App to clone, create branches, commit, push, and open pull requests on the user's behalf. It cannot bypass GitHub branch protections or required reviews.

## Mistral Vibe CLI / VS Code

If using Vibe locally instead of Vibe Code Web:

1. Clone the repository.
2. Start `vibe` from the repository root.
3. Trust the repository when Vibe detects project-level instructions.
4. `AGENTS.md` is the shared project instruction file and must be followed.

Local Git credentials determine repository write access.

## Repository governance

Full agent capability does **not** mean unrestricted direct changes to the publication branch. The intended model is:

- agents may read the whole repository;
- agents may create/edit files on their own work branches;
- agents may run tests and experiments in their own environments;
- agents may push branches and open PRs;
- agents may review and comment on each other's PRs;
- final merges remain reviewable and auditable.

The human owner retains final authority over protocol freezes, experiment inclusion/exclusion, manuscript claims, and submission.

## Secret-handling rule

Never commit API keys, OAuth tokens, GitHub tokens, model-provider credentials, clinical private data, or licensed datasets. Use GitHub Actions secrets or provider-managed credentials.
