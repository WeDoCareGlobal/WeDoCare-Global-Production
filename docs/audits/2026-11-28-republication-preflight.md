# We Do Care Global republication preflight — 2026-11-28

## Decision

**Production deployment: BLOCKED / not approved.** This branch and its pull request are review-only. No DNS, Vercel domain, production alias, or production deployment changes are authorized by this preflight.

## Verified state

- `https://wedocare-global.com/` returned HTTP 200 during this inspection.
- The supplied candidate preview `https://wedocare-globalcom-next.vercel.app/` returned HTTP 404 with `DEPLOYMENT_NOT_FOUND`. Its visual design could not be inspected, so this preflight does not claim a pixel-accurate implementation of that preview.
- The Vercel project named `we-do-care-global` is currently linked in project context to `WeDoCareGlobal/WeDoCare-Global-Production`.
- The latest production deployment record for that project reports commit `595ad0610baedb2ee5ffd2765828d1cff64d3d01`, but its deployment metadata identifies source `we-do-care-global/we-do-care-global`. This does not match the currently linked GitHub repository.
- The project-domain listing returned only `we-do-care-global.vercel.app`; it did not list `wedocare-global.com` or `www.wedocare-global.com`.
- The repository README describes production as `we-do-care-global/we-do-care-global`, `main:/docs`. The repository's `WEBSITE_AUDIT_FIXES.md` describes the production source as this repository's `docs/`. Meanwhile, `scripts/build-vercel.mjs` builds the root-level site and excludes `docs/`. These statements need reconciliation before any production cutover.

## Production repository index

The following repository identities and visibility were verified in the WeDoCareGlobal organization. Existence and visibility do not, by themselves, certify that a repository is the best, latest, secure, or production-ready implementation.

| System | Production repository | Visibility |
|---|---|---|
| AgentGuard | [AgentGuard-Production](https://github.com/WeDoCareGlobal/AgentGuard-Production) | Public |
| AgentVault | [AgentVault-Production](https://github.com/WeDoCareGlobal/AgentVault-Production) | Public |
| Enterprise Hybrid-RAG | [Enterprise-Hybrid-Rag-Production](https://github.com/WeDoCareGlobal/Enterprise-Hybrid-Rag-Production) | Public |
| Agent Eval | [AgentEval-Production](https://github.com/WeDoCareGlobal/AgentEval-Production) | Public |
| FoundationCentar | [FoundationCentar-Production](https://github.com/WeDoCareGlobal/FoundationCentar-Production) | Public |
| Pharma Intelligence OS | [Pharma-Intelligence-Os-Production](https://github.com/WeDoCareGlobal/Pharma-Intelligence-Os-Production) | Public |
| OmniGuard | [OmniGuard-Production](https://github.com/WeDoCareGlobal/OmniGuard-Production) | Private — access restricted |

The public portfolio must not imply that anonymous visitors can read the private OmniGuard repository. Its page labels the source as private and provides a source-access request route.

## P0 and correctness findings addressed in this branch

1. The root homepage lacked the canonical link required by `scripts/check_site.py`, while the `validate.yml` and `site-preflight.yml` workflows run that validator. The homepage now declares `https://wedocare-global.com/` as canonical.
2. Six system-card opening tags had malformed `data-group` attributes. They are corrected so the existing Control / Knowledge / Assurance filters can read the intended group values.
3. The six system cards now link their titles to the local system detail pages and their GitHub action to the matching `-Production` repository.
4. The OmniGuard preflight now asserts the private `OmniGuard-Production` repository link, private-source disclosure, source-access route, and development-preview disclosure rather than asserting only the old `OmniGuard-Next` link.

## Backups and review branch

Backup branches were created from `main` in these candidate source repositories:

- `WeDoCareGlobal/WeDoCare-Global-Production:backup/pre-republish-2026-11-28`
- `WeDoCareGlobal/wedocare-global-live:backup/pre-republish-2026-11-28`
- `WeDoCareGlobal/we-do-care-global:backup/pre-republish-2026-11-28`

Working branch:

- `WeDoCareGlobal/WeDoCare-Global-Production:work/portfolio-links-and-p0-2026-11-28`

## Remaining blockers before production

- Restore or provide a working candidate-preview URL so the intended design can be inspected and compared.
- Reconcile the canonical production source, Vercel Git connection, deployment provenance, and root-versus-`docs/` build path.
- Attach and verify apex and `www` domains to the intended Vercel project only after a separately approved cutover plan.
- Run the pull-request workflows and resolve every failing check.
- Audit each `-Production` repository against its corresponding development repository, tests, releases, security configuration, and evidence before describing any as the definitive "best" version.

## Safety boundary

This report records inspection evidence and proposed review changes only. No branch was merged. No production deployment, domain mutation, DNS mutation, secret change, or repository deletion was performed.
