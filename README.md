# Jarvis Preview for macOS

A local source workspace for browsing, searching and discussing source material.
The interface presents source nodes, searchable excerpts and an optional chat
panel, with English and Hebrew text support.

**Early preview · 0.1.0 preview 1 · Apple Silicon · macOS 13 or later.**
This is a preview of the source workspace, not a finished autonomous assistant.

## Download and install

Download the DMG from [Releases](https://github.com/WEBServices-ORG/jarvis/releases/tag/v0.1.0-preview.1),
open it and drag **Jarvis Preview.app** to Applications. Open the app, then select
**Open sample**. A small authored sample workspace opens in your default browser.
Keep the launcher running while using the workspace. **Stop** or quitting the
launcher stops its local server; browser tabs are left open.

The Python runtime is included. You do not need Python, Node, Homebrew or a model
for sample browsing and search. This package does not install background services.
Intel Macs are not supported by this build. The minimum OS is a build target;
execution was checked on the release Mac, not every supported macOS version.

## Use your own sources

Choose **Choose workspace…** and select a folder with this layout:

```text
my-workspace/
  sandbox/downloads/jarvis/*.srt
  sandbox/downloads/herdr/*.srt
  projects/audio-lab/docs/catalog/resources.yaml   # optional JSON-format catalog
  projects/jarvis/references.json                 # optional repository manifest
```

This preview uses the existing Jarvis workspace layout, not arbitrary document
import. UTF-8 SRT files are supported. A matching `.corrected.srt` is preferred
when present. Files outside the chosen folder are not followed through source
symlinks. Source IDs and excerpts are derived from source paths and locations;
reopen the workspace after changing files. A future document-import interface is
not included in this preview.

## Optional local AI

Before opening a workspace, enter an **already running** OpenAI-compatible local
endpoint, for example `http://127.0.0.1:8000/v1`, and an existing model ID. The
browser queries that server's model list and permits selecting an available model.
Only literal loopback HTTP endpoints are accepted. Jarvis does not start, download,
or configure a model, bypass its memory safeguards, or fall back to a cloud API.
No endpoint is contacted until you explicitly configure one.

Source browsing and word search work without AI. Chat requires a compatible local
server with enough memory. Generated answers may be wrong or cite irrelevant
sources: inspect the excerpts. A citation's presence is not evidence of correctness.
Stopping browser waiting does not guarantee that the model server stops generation.

## Scope and privacy

- The bundled sample is authored fictional material, not anyone's personal memory.
- This app does not automatically scan your home folder or connect to live memory.
- Sources remain read-only. Persistent memory and experimental correction editing
  are not included in the distributed app. Memory controls in the browser report
  that memory is not configured.
- No automatic actions, DAW control, continuous recording or speech model is bundled.
  Browser-dependent dictation is experimental and may be unavailable; no speech
  download or capture was tested for this release.
- No application telemetry, cloud fallback, account sign-in or automatic updater.
  If you configure a model server, it receives prompts and selected source context;
  that server's own logging and network behavior are outside Jarvis's control.
- The browser communicates with a token-protected server bound to `127.0.0.1` on
  an automatically assigned port. Do not share the active local page.
- Chat is held in the current page. The browser may retain its own session state.

The source repository is private. This public repository contains the README and
release downloads. Public binaries necessarily contain runtime code and browser
assets; private repository visibility is not binary obfuscation.

## Preview verification

Release checks cover the bundled runtime, sample source retrieval, authenticated
HTTP behavior, disabled persistent memory, launcher lifecycle and disk-image
integrity. Existing automated application checks do not establish model grounding,
human usability acceptance, speech quality or production readiness.

Report reproducible preview issues through this repository's Issues tab. Include
macOS version, chip, steps and observed behavior; do not include personal sources,
model logs, credentials or active browser tokens.

Bundled CPython and dependency notices are included in the application resources.
