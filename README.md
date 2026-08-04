# EXODUS Ansible Lab

A hands-on learning lab for Ansible, built alongside the **EXODUS** enterprise
engineering project. This repository is where each Ansible concept is learned
and drilled **before** it is used in the real project.

## Purpose

- Learn one Ansible concept at a time, with many small worked examples.
- Every line is commented — what the keyword is, what it does.
- Examples are built up incrementally: run one, add the next, run again.
- A **training ground**, kept separate from the main EXODUS project so
  experiments never affect production.

## How it is organised

One folder per concept, in teaching order:

- `01-architecture/` — how Ansible works (control node, managed nodes, push model)
- `02-inventory/` — static inventory, groups, host/group vars
- `03-ad-hoc/` — one-off commands (`ansible ... -m ...`)
- `04-modules/` — modules and idempotency, one at a time
- `05-playbooks/` — play, tasks, the play keywords
- `06-variables/` — vars, group_vars/host_vars, precedence
- `07-loops/` — loop over lists
- `08-conditionals/` — `when:`
- `09-handlers/` — notify + handlers
- `10-templates/` — Jinja2 templates
- `11-roles/` — role structure and reuse
- `12-collections/` — installing and using collections
- `13-vault/` — encrypting secrets (ansible-vault)
- `14-dynamic-inventory/` — inventory from a script/cloud source
- `15-error-handling/` — block / rescue / always
- `16-performance/` — async, pipelining, fact caching, strategy, tags
- `17-quality/` — ansible-lint, Molecule
- `18-custom-modules/` — writing your own module
- `19-git-ci/` — Git and CI-triggered execution
- `KEEPERS/` — clean, reusable snippets promoted from the lab
- `inventory/` — the hosts the lab runs against

## KEEPERS

When a lab example turns out to be genuinely reusable (for example a real
server-onboarding configuration), the clean version is **promoted** out of the
lab into `KEEPERS/`. That folder is the curated, reusable output of the lab.

## Governance

This lab is intentionally **outside** the EXODUS V2 governance — no Change
Requests, no ceremony. The goal here is to learn fast. The disciplined,
governed work happens in the main EXODUS repositories.

## Author

Abiola — self-directed EXODUS enterprise engineering project.