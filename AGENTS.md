# Repository collaboration instructions

## Continuity across computers

- Treat `origin/main` as the source of truth.
- At the beginning of a work session, fetch and integrate the latest `origin/main` before editing.
- Keep `WORKLOG.md` current when work changes the active status, test results, next steps, or open questions.
- When the user says they are going home, will continue on the other computer, or otherwise asks to hand off the work:
  1. Review the working tree and summarize the changes.
  2. Run relevant validation that is available and safe.
  3. Update `WORKLOG.md` with the handoff state.
  4. Commit all intended repository changes with a descriptive message.
  5. Pull/rebase if the remote advanced, resolve only well-understood conflicts, then push to `origin/main`.
  6. Report the pushed commit hash and any remaining uncommitted or untracked files.
- Never commit personal or private travel screenshots unless the user explicitly approves them.
- Do not install the skill merely to edit or review it; installation requires a separate user request.

