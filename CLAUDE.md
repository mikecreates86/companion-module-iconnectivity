# Claude Code handoff

Read [AGENTS.md](AGENTS.md), [PROJECT_CONTEXT.md](PROJECT_CONTEXT.md), [README_AI.md](README_AI.md), and [STATUS.md](STATUS.md) before editing. These files are the shared handoff for any AI; do not assume access to previous chats. Follow AGENTS.md throughout the session.

## Project and editable code

Bitfocus Companion module for iConnectivity devices. Edit `src/` and `tests/`; legacy/TNG codecs are in `src/protocol/` and AppleMIDI/RTP-MIDI transport is in `src/network/`. Read [docs/README.md](docs/README.md) and the capability matrix before changing supported operations.

## Install and verify

Use Node `^22.20` and the pinned Yarn 4 version through Corepack:

```sh
corepack yarn install --immutable
corepack yarn test
corepack yarn lint
```

The AppleMIDI integration test requires loopback UDP. For packaging or release-readiness changes, also run `corepack yarn package` and `corepack yarn package:verify`.

## Current work and constraints

STATUS.md records release state and blockers; [docs/IMPLEMENTATION_PLAN.md](docs/IMPLEMENTATION_PLAN.md) records the work queue. Preserve capability-aware controls, reconnect behavior, MIDI queues, multiple-instance port isolation, and Auracle access. Distinguish implemented behavior from hardware validation.

Use a focused `codex/` branch as required by AGENTS.md. Do not replace Yarn with npm, edit generated artifacts as source, or commit personal exports, device identifiers, private network layouts, or unsanitized captures. Change CI, manifest, or user help only when the task requires it.

Follow [releases/README.md](releases/README.md) for packaging and retain archive history. Production promotion requires hardware validation and explicit user approval. At handoff, update STATUS.md within its existing four sections and report checks actually run and the next action.
