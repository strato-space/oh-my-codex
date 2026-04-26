---
name: ontology-check
description: "[OMX] Optional Greek-scholastic review of a deep-interview spec"
argument-hint: "[<spec-path or text>]"
---

<Purpose>
Ontology-check is an optional post-interview quality pass. It reviews a deep-interview spec or supplied text before the user chooses a downstream planning or execution skill.
</Purpose>

<Use_When>
- A deep-interview spec has just been produced and the user wants an ontology-first sanity check before handoff
- The user asks for `$ontology-check`, `ontology check`, Greek/scholastic review, ambiguity review, category-mistake detection, hidden-assumption review, modality separation, or minimal repair
- A spec, plan, requirement, or argument may contain term drift, category mistakes, inconsistent logic, or untested claims
</Use_When>

<Do_Not_Use_When>
- The user explicitly wants to skip review and proceed to planning/execution
- The request is a normal implementation task with no spec or conceptual framing to review
- The user wants broad code review or security review instead
</Do_Not_Use_When>

<Execution_Policy>
- This is advisory and optional; do not launch `$ralplan`, `$autopilot`, `$ralph`, or `$team` from inside this skill.
- Prefer an explicit spec path or supplied text. If omitted, use the current/latest relevant `.omx/specs/deep-interview-*.md` artifact when available.
- Return a verdict: `APPROVE`, `ITERATE`, or `REJECT`.
- If the verdict is `ITERATE` or `REJECT`, report the minimal repair before handoff; do not rewrite the spec unless the user asks.
</Execution_Policy>

<Checklist>
1. Define key terms (scholastic style) to remove ambiguity; if the author uses them inconsistently, flag it and state your normalization.
2. Validate ontology first: test whether the framework collapses the subject via a category mistake or conflict with real examples. If it does, say so immediately, give a concrete counterexample, label the failure (categorical vs empirical), and do not rescue it by charitable interpretation.
3. Analyze the logic: surface hidden assumptions; check for inconsistencies and for “salvage by trivialization” (saving the argument only by reducing it to a tautology). State this explicitly when it occurs.
4. Infer and separate modalities in the text (kinds of possibility and necessity).
5. Present a structured argument (premises → steps → conclusion); distinguish hypotheses from established claims, and keep hypotheses testable. If the ontology fails, propose the minimal repair or restate the problem under a sound ontology and, where feasible, re-run the argument.
</Checklist>

<Output>
- Verdict: `APPROVE`, `ITERATE`, or `REJECT`
- Key term normalization
- Ontology finding
- Logic/modality finding
- Minimal repair, if needed
- Ready for handoff: yes/no
</Output>

<Final_Checklist>
- [ ] Reviewed the intended spec/text, not unrelated context
- [ ] Verdict is explicit: `APPROVE`, `ITERATE`, or `REJECT`
- [ ] Key term, ontology, logic, modality, and argument-chain issues are covered
- [ ] Minimal repair is stated when needed
- [ ] No downstream execution skill was launched from inside ontology-check
</Final_Checklist>
