# Research patterns and examples

## What this first version captures

This method was distilled from a user-led investigation that moved from compatibility questions to a small hardware/software experiment, a usable demonstration, a design correction, and an explanation the user could independently assess. The transferable pattern is how the questions evolve, not the original device, code, or benchmark.

| User behavior | How to support it |
|---|---|
| Asks which products support a feature, then asks who actually succeeded | Move from advertised capability to a concrete example with environment details |
| Offers equipment already available and permits a simulated missing part | Investigate the actual environment and isolate the desired mechanism before expanding the setup |
| Says the immediate goal is only to verify one connection | Choose the smallest test of that connection; preserve the larger intended use as the next question |
| Asks how the result proves the feature was really used | Build evidence that distinguishes the intended path from a plausible substitute |
| Wants a downstream program to consume the output | Add one real end-to-end use after the primitive operation works |
| Requests manual steps, explanation beside logs, and reasons for library choices | Make the investigation reproducible and intelligible, not dependent on the assistant's assurances |
| Stops a code walkthrough to discuss the flow | Follow the current conceptual question rather than continuing the abandoned presentation |
| Notices that only one buffer changes in a demo | Treat the observation as a scheduling/design question and inspect it |
| Proposes queues and protected ownership based on a familiar industry model | Check the proposal against the intended behavior and reference practice, then update the design when justified |
| Accepts initial communication but expects independent operation afterward | Preserve that boundary; do not add late-connect or recovery requirements without a reason |
| Requests a report once the mechanism and results are understood | Consolidate the evidence at the end without making report production the purpose of every research step |

These patterns express a preference for concrete progress and explanations that survive follow-up questions. They do not require this exact sequence or every type of deliverable.

## Example: hardware data path

**Initial question:** Can a custom acquisition path write data where a GPU application can use it?

A useful investigation might evolve as follows:

1. Check the stated capability and successful examples, including hardware, driver, and operating-system conditions.
2. Inspect the available machine rather than assuming a model name proves compatibility.
3. Use a tiny write/read experiment to verify the memory-access primitive. If a driver writes through a CPU mapping, name that path explicitly.
4. Have a separate application consume the same allocation and perform a computation whose expected result can be checked independently.
5. Add a short image-processing demonstration only after the basic path works. The demonstration answers usability questions beyond memory access.
6. Slow the consumer in a bounded run to reveal ownership, queueing, overwrite, and drop behavior.
7. Compare the resulting behavior with the intended design and revise it when the evidence exposes a mismatch.

In this example, CPU writes through a GPU mapping do not establish physical device peer DMA. Correct inference does not by itself prove how the input arrived. A video is useful evidence of behavior but cannot replace a check of the claimed data path. Keep these as separate research conclusions.

There is no requirement to repeat all seven activities if the user's question is already resolved. A research step is useful because it closes an uncertainty, not because it completes a prescribed ladder.

## Example: software service or alternative platform

**Initial question:** Could another service replace the current one?

Start with the behavior the user needs, such as an API contract, a deployment restriction, or a supported input format. Read relevant documentation and one well-matched integration example. A small request using a known input may establish API compatibility without migrating the application.

If the question becomes whether the existing application can use the response, add a bounded handoff to that application. If the question becomes speed, cost, or error recovery, design a check for that specific property. A successful request alone does not establish sustained throughput or a successful migration.

When the user asks only to compare documentation or approaches, stop at the supported comparison; do not install a service or run a paid workload simply to follow the hardware example.

## Choosing evidence that distinguishes alternatives

Use a combination that addresses the actual uncertainty:

- **Known or random challenge input:** helps rule out a fixed demonstration result.
- **Independent expected output:** checks content rather than relying on the tested component's own success message.
- **Resource or execution-path inspection:** distinguishes where the work occurred, when location matters.
- **A targeted negative control:** establishes that a damaged input or unavailable mechanism produces a detectable difference.
- **Timing, ownership, or state traces:** reveal behavior that a final screenshot cannot show.
- **A manual replay:** lets the user verify the mechanism, while clearly distinguishing replay of saved evidence from a fresh experiment.

Avoid claiming that any one technique proves every property. Select enough evidence to distinguish the plausible alternatives without building an unnecessarily large test system.

## Keeping direction without creating a rigid process

For long investigations, a short working note can record:

> We are trying to determine ___. The current evidence supports ___. We chose ___ because ___. It does not yet establish ___. The next useful check is ___. Evidence is saved at ___.

Use this only where continuity helps. The user may ask a simple question that needs a short answer rather than a new note, plan, diagram, or experiment.

Keep factual confidence separate from a design preference. A correction such as accepting a startup handshake changes the interpretation of independence; it need not require rewriting the program. A correction revealing unintended overwrites may require a real design change. Check which kind of problem has actually been identified.
