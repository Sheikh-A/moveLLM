# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Repository overview

This repository is a small, metadata-only project describing Movement Labs in multiple machine- and human-readable formats for use with LLMs or other tooling. There is currently no executable code, build system, or tests in this repo.

## Files and structure

Top-level files:

- `movellm.yaml` – YAML representation of the Movement Labs profile. Fields include `name`, `description`, `core_mission`, `voice_tone`, `key_highlights`, and `contacts`.
- `movellm.json` – JSON representation of the same profile, with an equivalent set of fields, structured for direct consumption by JSON-based tools.
- `movellm.txt` – Human-readable, Markdown-like/text representation of the profile with similar content and an additional `github` contact entry.

The three files are intended to describe the same underlying entity (Movement Labs) for different consumers:

- YAML / JSON: structured data for programmatic use.
- TXT: readable reference and prompt-style context.

When updating the Movement Labs profile, be aware that changes may need to be reflected across all three files to keep them logically consistent.

## Development and tooling

Because this repository currently contains only data files and no code:

- There are **no project-specific build, lint, or test commands** defined.
- There is no `README.md`, package manifest (`package.json`, `pyproject.toml`, etc.), or CI configuration to drive a standard build/test workflow.

Useful ad-hoc commands when working here:

- Pretty-print and validate the JSON profile:
  - `python -m json.tool movellm.json`
- Quickly inspect the YAML profile (if `yq` is installed):
  - `yq . movellm.yaml`

If new code, scripts, or configuration are added to this repository in the future (for example, generators that produce these files or tests that validate them), update this `WARP.md` to document:

- How to run the generator(s).
- How to run any linters or schema validators for the profile formats.
- How to run tests (including how to target a single test or suite).

## Guidance for future changes

- Keep the semantics of the Movement Labs profile aligned across `movellm.yaml`, `movellm.json`, and `movellm.txt`. If one format gains new fields (e.g., additional contact links), consider whether they should be added to the others.
- Maintain clear, concise descriptions and highlights that match the intended voice/tone fields in these files.
- If you introduce a schema (e.g., JSON Schema for `movellm.json` or a YAML schema), document how to validate against it in this file.
