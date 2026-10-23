# Evidence — `python-bug-triage`

> User-provided observations only. No additional terminal logs were created or reconstructed for this contribution.

**Tested on:** Windows · Python 3.12 · **Date:** 2026-10-23

---

## 1. It fired when it should

**What the user typed:**

```text
Triage this Python bug: AttributeError NoneType object has no attribute get. My AI agent crashes when processing a JSON response. Classify the severity and identify missing information.
```

**User-provided routing and tool trace:**

```text
Routed to: python-bug-triage
Tool trace: read_resource(resources/triage-rules.md), run_script(triage_bug.py), save_output(triage-agent.md)
```

**User-provided answer:**

```text
Severity SEV1; likely component agent; missing expected result, actual result, reproduction steps, version/environment.
```

**Did it activate on its own?** Yes. The user-provided evidence states that it was routed to `python-bug-triage` without naming the skill explicitly in the request.

---

## 2. It stayed quiet when it should

**A near-miss the user typed:**

```text
Explain this Python repository to a newcomer and show how to run it.
```

**User-provided routing result:**

```text
Routed to: repo-onboarder, NOT python-bug-triage
Tool trace included: run_script(scan_repo.py) and save_output(onboarding-skill-runner.md)
```

**Did it stay dormant?** Yes.

**Why this one is a real test:** It is close to a Python/agent troubleshooting prompt but asks for repository explanation and onboarding, not bug triage or severity classification.

---

## 3. What it cost

| | Tokens (approx.) |
|---|---|
| Description in the menu (always loaded) | ~291 |
| Body, once it fired | ~1885 |
| What stayed on disk because it did not fire | ~404 |
| Saved by progressive disclosure | ~1481 |

**User-provided progressive disclosure figures:**

```text
4 skills on disk; menu ~291 tokens; all bodies ~1885 tokens; loaded ~404 tokens; saved ~1481 tokens.
```

**Near-miss disclosure:**

```text
loaded ~427 tokens; saved ~1458 tokens.
```

---

## 4. Anything a reviewer should know

- Known limitation: this is a narrowly scoped triage skill for Python and agent bug reports; it intentionally does not claim root causes or invent missing evidence.
- Needs an API key / network: yes for the JHF runner to auto-route, but the deterministic script itself does not require a network call.
- Missing evidence note: the exact raw runner transcript and full model output beyond the user-provided observations are not in this workspace. The template asks for a real transcript, but the available evidence set is limited to the exact user observations above; no additional logs were invented.
