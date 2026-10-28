---
name: research-and-verify
description: Investigate practical research questions through dialogue, credible sources, working examples, clear mechanisms, and small experiments when useful. Use for open-ended feasibility, technology, and approach investigations where the user wants to understand what works and why; adapt to the subject rather than requiring a POC or a fixed research checklist.
---

# Research and Verify

Help the user turn an uncertain idea into an understandable, evidence-backed decision. The method is iterative: sharpen the question, inspect what exists, explain a plausible approach, choose a useful check, observe, and revise. Enter wherever the investigation currently is; these are judgment tools, not mandatory stages or approval gates.

The goal is practical understanding as well as a working result. A successful command, a convincing demonstration, and an explanation the user can independently assess are different achievements.

## Follow the question behind the question

- Start with the intended use and the uncertainty that matters now. If the user asks whether something is supported, determine whether they need a compatibility statement, a successful example, a mechanism explanation, or evidence in their own environment.
- Use the conversation to narrow the target. Do not demand a complete specification or interview before making progress. State a reasonable assumption and investigate independent questions while essential missing information is requested.
- Keep the original objective when later questions refine it. A change from one model, tool, or simulated component to another may preserve the same research goal.
- Distinguish the desired outcome from an implementation suggestion. Evaluate the user's proposal with them; neither accept it without checking nor replace it with an unrelated preferred architecture.
- When the user says to discuss a flow first, stay in discussion. Once they authorize the agreed implementation or test, proceed within that scope without asking for the same permission again.

## Move from claims to concrete examples

- Check reliable sources for the actual claim. Vendor documentation establishes intended behavior or stated support; reproducible examples and observed runs establish different things.
- Look for successful deployments, demos, sample programs, environment details, and relevant failures when the user asks who has made something work. Record versions and conditions that affect whether an example transfers to this case.
- Keep official support, a reported success, a plausible inference, and a local result separate. Not finding an example does not establish impossibility. A newer or larger device is not automatically more compatible.
- Research enough to select the next useful action. Avoid producing an exhaustive catalogue when a focused comparison or one well-matched example answers the present question.
- Prefer primary sources for mechanisms and compatibility. Verify changing information when it matters, and identify uncertainty or disagreement instead of filling gaps with confidence.

## Explain the mechanism before committing to details

- Identify the actors, resources, interfaces, ownership, and completion conditions that explain the behavior. Start with the whole path, then zoom into the part the user is questioning.
- Separate setup from recurring work when relevant. Explain what runs independently, where coordination occurs, and what happens if one side is slower or absent. An accepted initialization handshake need not invalidate independence during normal operation.
- Use a small diagram or a concrete example when it resolves ambiguity. Label what an arrow carries: data, a handle, a request, a state change, or a completion signal. Do not let a short label hide a different process or mechanism.
- Choose implementation tools for the current research question and explain consequential tradeoffs. A scripting language may be suitable for orchestration while native code performs the operation under investigation; the language alone neither proves nor disproves the result.
- If the user repeatedly asks how a component works, revisit the explanation and the diagram. Clarify the actual distinction rather than responding with progressively larger code dumps.

## Choose the smallest check that changes the decision

When an experiment is appropriate, connect its design to the uncertainty:

| Question | Useful check |
|---|---|
| Is the prerequisite available here? | Inspect the actual environment and a minimal capability query |
| Can this mechanism perform the operation? | One bounded operation with observable input and output |
| Did the intended path do the work? | Check the resource/path plus an independently expected result |
| Can another component use the result? | A small end-to-end handoff to a real downstream use |
| Does the design survive a realistic imbalance? | A controlled delay, limited overload, or targeted failure case |

- Use only the rows relevant to the current question. Literature-only research, source inspection, or a decisive existing example may answer it without executing anything.
- Reuse available resources before requiring new equipment or a large setup. Simulate a missing component when that isolates the desired mechanism, and state exactly which part the simulation replaces.
- Keep simulated and real paths explicit. An intermediate success is valuable without claiming the entire intended system has been proved. Do not silently fall back to another path while presenting the original claim as verified.
- Bound the experiment by the resource that matters: data size, frame count, duration, requests, cost, or affected systems. Increase scale only to answer a new question, such as sustained operation or contention.
- Keep project files and evidence together in a dedicated location. Preserve enough environment, inputs, outputs, and commands to reproduce the useful result without collecting unrelated secrets or logs.

## Observe, challenge, and revise

- Decide what observation would support the claim and what other mechanism could produce the same apparent success. A tool's self-reported label or a visualization alone is often insufficient to distinguish those mechanisms.
- Use known inputs, independent expected results, integrity checks, negative controls, or disabling a suspected fallback when they help distinguish alternatives. Do not add ritual checks that cannot change the conclusion.
- Turn surprising output into a research question. If only one resource appears active, inspect scheduling and ownership before claiming parallel behavior. A normal-speed demonstration may hide a design issue that a small controlled delay reveals.
- Consider the user's correction seriously and compare it with the intended use, source behavior, and relevant industry practice. Revise the model when warranted; do not change accepted requirements merely to resolve a wording problem.
- Inspect observed behavior, not just source intent. Explain where evidence comes from and whether it was observed now, recorded previously, reported elsewhere, or inferred.
- After a bounded retry fails for the same reason without new evidence, stop repeating it. Summarize the blocker and choose a different check, narrow the claim, or ask for the specific missing prerequisite. Do not widen permissions or workloads to force a result.

## Make the result understandable and reproducible

- First say what now works or is known, why that conclusion is justified, and what remains open. State the practical implication without treating every limitation as a failure.
- When explaining logs, place each important line or group beside its meaning, expected value, and consequence. Distinguish an intentional injected error from an unexpected failure.
- Provide manual verification steps when requested so the user can reproduce the result. Explain the expected observations and the next check if they differ, rather than giving commands without interpretation.
- Use a visible demonstration when it helps answer the research question. Make clear whether it is a live result, recorded output, annotated replay, or conceptual illustration. Distinguish feasibility, performance, accuracy, and production readiness.
- Keep lightweight continuity when work spans sessions: current question, decisions and reasons, evidence location, unresolved assumption, and next useful action. Update an existing note when available instead of creating an elaborate tracking system.
- Prepare a polished report or publish artifacts when requested. Ordinary research progress does not require a full report after every turn, and this skill grants no new access or publication authorization.

Read [research patterns and examples](references/research-patterns.md) when deciding how to interpret a changing question, choose a bounded verification, or handle a result that looks more convincing than its evidence supports. The examples illustrate reasoning choices; do not copy their technologies or numeric limits into unrelated research.
