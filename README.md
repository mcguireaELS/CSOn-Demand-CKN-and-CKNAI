# Onboarding and Enablement Hub, nursing

ClinicalKey for Nursing and ClinicalKey Nursing AI.

**Status:** Draft 0.1, 22 September 2026. Internal review copy, not for customer distribution.

Single self-contained HTML file, hosted on GitHub Pages, intended to embed into
WordPress on elsevierresources.com. Forked from the ClinicalKey AI hub at draft
0.11.1. The shell is unchanged; everything below the shell is new.

Customer facing name is **Onboarding and Enablement Hub**, subtitle **Customer Hub**.
Eyebrow reads "Customer Success, Your Digital Experience." Internally these builds
are Learning Experiences, or LeX. People who use them are learners, never users.

---

## Structure

Role at the top, product sequence underneath. Two paths, one shared wrap up.
Nurse runs 11 content steps, administrator 13.

```
Gate
  |
Landing: I am an administrator   |   I am a nurse
  |
  ClinicalKey for Nursing steps
  ---- product break ----
  ClinicalKey Nursing AI steps
  |
Wrap up
```

**Nurse, 11 steps, about 55 minutes.** Welcome video, get started, access and your
account, on mobile, clinical calculators, earn CE credit. Break. Introducing Nursing
AI, get started with Nursing AI, writing better questions, what Nursing AI draws on,
questions and limits.

**Administrator, 13 steps, about 55 minutes.** Implementation overview and what has
changed, access and authentication, usage reporting through E-PIC, link resolver and
Open URL linking, discovery and library systems, institutional branding, content and
the master content lists, training and support. Break. Introducing Nursing AI,
Conversation Sharing, link resolver setup, what your nurses will ask, driving
adoption.

The AI block is contiguous in both paths by design, so an institution without the AI
bundle can be served a build with that block removed. That is the per instance
approach already agreed in place of entitlement checking.

---

## Why sequence rather than fork

John described two shapes in the same conversation: role at the top with the two
products blended inside each path, and a ClinicalKey for Nursing path that extends
into a Nursing AI path. This build takes the second shape and puts it under the
first, for three reasons.

A fork will not balance, though it is closer than it was. The Nursing AI
administrator block now carries four real steps rather than two, after the
Conversation Sharing and link resolver setup guides arrived on 22 September. It is
still eight CKN steps to five AI steps, and the AI half depends on the base platform
being understood first.

A blend recreates the problem John was warning about with the Disney and Hulu
analogy. A nurse working through remote access does not want a prompt writing step in
the middle of it. The break does what keeping the two apps separate does, without
needing two hubs.

The product itself says sequence. The Nursing AI introduction video states that
ClinicalKey for Nursing AI is now part of ClinicalKey for Nursing, and John observed
that most nurses arrive at the AI layer through a link inside the base platform. The
bridge copy on the first AI step is quoted from that video.

---

## What is new in the shell

Four additions to the ClinicalKey AI shell. Everything else is untouched.

- **Product break in the rail.** A label, not a target, emitted when the product
  changes between steps. Not a step, not counted toward progress, not navigable.
- **Bridge block.** Shown once, on the first step of the AI block, above the step
  heading.
- **Transcripts.** Collapsible, inline, on the two narrated videos. Converted from
  the supplied WebVTT files. Requested independently by Laura, Andrew and Matt
  Wilcox. The three Master the Moment clips are silent with on-screen text and need
  no transcript for parity.
- **Asset block.** Downloads and outbound links carried on a step, used by the
  administrator steps whose source is a resource centre page rather than one guide.

Removed: the ClinicalKey AI resources and clinician contact screens, which were
specific to that product.

---

## Videos

All five are unlisted, so the hash is required on the player URL. `texttrack` can be
appended at the same place for the language toggle.

| Video | ID | Hash |
|---|---|---|
| Welcome to ClinicalKey for Nursing | 1229297245 | f419dc046a |
| ClinicalKey for Nursing AI Introduction | 1222128849 | 26a5ffa46c |
| Master the Moment, Books | 1229294307 | c0bfabd8a9 |
| Master the Moment, Clinical Skills | 1229294229 | 563b3a6efa |
| Master the Moment, Journals | 1229294104 | aecc7248cc |

---

## Before this goes anywhere

- **`assets/` is empty.** Copy the folder across from the ClinicalKey AI repo: the
  Elsevier logo, the favicons, and the five landing layer images. Missing layers hide
  themselves rather than showing a broken image, so the landing screen degrades
  quietly, but it will not look right until they are there.
- **`SHARE_BASE`** reads `PENDING-NURSING-HUB-PATH`. Per step share links are
  composed from it, because script inside the iframe cannot read the parent URL. It
  needs the real address once hosting is settled.
- **`ACT_BASE`** is set to this repository's Pages URL, which gives nursing its own
  reporting namespace, separate from the ClinicalKey AI hub. Changing it after real
  data starts flowing splits reporting across two namespaces permanently.
- **LRS credentials** are labelled placeholders and stay that way. They are the open
  technical risk and the reason for the Lambda and API Gateway conversation.
- **Adoption kit deep link** is not supplied, so that step renders a pending block
  rather than a broken link. Sourcing: John Grooms.
- **Download links point at `/docs`.** Replace them with `media.ffycdn.net` direct
  URLs once the nursing assets are located in Frontify, which also reduces the
  copyright surface of this repository. Most of these PDFs carry a no-reproduction
  line, and public repo clearance is an open item.

---

## Content flags carried over from the comparison

- **Six of the nurse-facing CKN quick sheets predate 2022** and at least one is
  contradicted by a 2026 product change. The QA pass with Laura and Jan is a
  prerequisite, not a nice to have.
- **What's New for ClinicalKey for Nursing was cut**, not refreshed. It describes a
  2021 homepage that has changed twice since.
- **The Gen AI Academy for Nursing is not in the build.** Five modules, eighteen
  lessons, already promoted above the fold on the Nursing AI resource centre. It is
  the obvious destination from the wrap up, and it competes with the nurse path if it
  is not. Held until we know who owns it.
- **The Welcome video is 6 minutes 33 seconds** and opens the nurse path. Segmenting
  it, with the transcript searchable, was raised independently three times.
- **Nursing AI support routes to the ClinicalKey AI support centre**, not a nursing
  specific one. Confirm that is intended.
- **Promotional Resources for ClinicalKey for Nursing** has not been reviewed and is
  not represented. It is probably the administrator counterpart to the Nursing AI
  adoption kit.

---

## Build conventions

No network access in the sandbox. All assets are uploaded and all commits are manual
through the GitHub web interface.

Every edit to this file is an exact string replacement with a one occurrence
assertion, failing loudly on zero or multiple matches. JavaScript is extracted and
checked with `node --check`, CSS is checked for brace balance, and the path logic is
exercised through a DOM stub simulation in Node before anything is staged.

Current validation: JavaScript parses, 324 CSS braces balanced, 47 simulation checks
pass across both paths, every referenced local asset present, no em dashes or en
dashes.
