# BriDigitalCo upstream-PR bot (STAGING ONLY)

DO NOT MERGE THESE BOT FILES INTO THE GO-HYBRID FORK'S MAIN BRANCH.
That would contaminate future upstream contributions with unrelated workflow files.

This is a proposed *separate* GitHub Actions automation repository:
  BriDigitalCo/UpstreamPRBot

One-time account-owner setup:
1. Create the above public repository; enable GitHub Actions.
2. Copy .github/scripts/submit_reviewed.py and .github/workflows/submit-reviewed-pr.yml to its default branch.
3. Create a GitHub Actions secret BRI_UPSTREAM_PR_TOKEN with an authorized
   public-repository credential (classic PAT with public_repo, not repo, if
   appropriate; use a dedicated low-privilege bot identity if practical).
   NEVER paste credentials into chat, commits, logs, or PRs.
4. Manually run the workflow first and inspect its output.

Requirements for each future auto-submitted fix:
- Branch submit/<safe-slug> in BriDigitalCo/Go-Hybrid, based on a clean upstream branch.
- Latest commit message contains: Upstream-Ready: true
  Tests-Verified: true; AI-Assistance: permitted;
  Payment-Eligibility: verified; Tests-Run: <real test evidence>.
- These are human/AI attestations, not independent proof; check before marking.

At most one upstream PR is submitted per scheduled run and existing PRs are skipped.
No token -> no upstream PR. No merge, payout, or contract is authorized.
Existing PR #4379 was manually submitted and must not be duplicated.

After deployment, GitHub Actions can be delayed; a cron trigger is not a
guarantee of uninterrupted 24/7 coding work. The separate Earnings Work
automation still performs discovery, coding and preliminary review.

WHY: The connected ChatGPT GitHub App's fork installation returns HTTP 403
for the upstream PR creation API. A user-authorized credential is needed
for upstream submission. ChatGPT plugin permissions alone cannot fix that.
