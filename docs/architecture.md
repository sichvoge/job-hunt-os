# Architecture

Job Hunt OS uses two repositories.

## job-hunt-os

Public.

Contains the reusable system:
- schemas
- workflows
- evaluation logic
- methodology
- documentation
- bootstrap tooling
- synthetic/example data

It must never depend on the author's personal data being present.

## job-hunt-os-data

Private.

Contains one person's instance of the system:
- career evidence
- career stories
- positioning
- search preferences
- target companies
- jobs
- contacts
- applications
- interviews
- work products
- search history and outcomes

## Core rule

A complete Job Hunt OS installation requires both repositories.

The public repository defines how the system works.
The private repository contains the state it works on.

The public repository must contain everything necessary to bootstrap
a new private data repository without exposing any real user's data.