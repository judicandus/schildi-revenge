# SDK fix assets (matrix-rust-sdk)

Patch files referenced from SchildiChat/schildi-revenge#53 and #47 comments. Nothing here is part of SchildiChat Revenge.

- `sdk-clear-hidden-remote-events.patch` — fix for duplicated/missing timeline items after a timeline `clear()` while
  local echoes are pending (follow-up to matrix-org/matrix-rust-sdk#6983/#6709). Includes a regression test
  (`timeline::tests::echo::test_clear_with_local_echo_removes_hidden_remote_events`). On upstream `main` `0614b846f`
  the test fails without the fix (`left: ["$2", "$2"]`, `right: ["$1", "$2"]`) and passes with it.
- `sdk-duplicate-event-id-invariant.patch` — optional separate PR: a `check_no_duplicate_event_ids` invariant that
  would have caught this class of bug.

Apply with `git am <patch>` on a checkout of matrix-org/matrix-rust-sdk `main`.

**Provenance:** these patches and their commit messages were produced with an AI assistant (Kilo) and are shared as a
draft. matrix-rust-sdk's CONTRIBUTING does not accept AI-assisted/agent-written contributions, so anyone filing them
upstream should rewrite the text and the code comments as their own.
