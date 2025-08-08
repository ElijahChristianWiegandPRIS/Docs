\# PRIS Bug Workflow



\# 🛠️ Improving Bug Resolution: Examples from Past Work



According to research, we've analyzed several recently resolved bugs to highlight how applying four core paradigms — \*\*Reproducibility\*\*, \*\*Expected Behavior\*\*, \*\*Production Examples\*\*, and \*\*Workflows Impacted\*\* — can streamline our triage, reduce investigation cycles, and help prevent future edge cases.



The following three cases illustrate where greater clarity and consistency in these areas would have directly accelerated delivery and supported stronger QA/Product collaboration.



---



\## 🐞 GW-1747 – Claims Pulled Midterm



\*\*Summary:\*\*  

Claims were incorrectly added midterm via an endorsement, making the driver unacceptable. Business rule dictates claims only appear at renewal.



\### 🔁 Reproducibility

\- No reproduction steps were included in QA notes.

\- Developer could not reproduce in environment but deduced logic issue from related tickets (GW-3627, GW-2712).



> 💡 \*Adding QA steps showing how the claim appeared midterm (or how to attempt it) would improve clarity and validate the issue sooner.\*



\### ✅ Expected Behavior

\- Acceptance Criteria (AC) vaguely stated: \*“Verify claim does not appear midterm.”\*

\- No explicit workflow coverage — left open questions like:

&nbsp;   - Is this for all claim types?

&nbsp;   - What about reinstatements?



> 💡 \*AC should detail how loss history is built during endorsements vs renewals.\*



\### 🖼️ Production Examples

\- Two screenshots were provided, but no query logs or step-by-step walkthrough of when claim appeared.



> 💡 \*Including a production policy timeline (endorsement → claims → validation) would help pattern detection and prevent future occurrences.\*



\### 🔄 Workflows Impacted

\- \*\*Policyholders\*\* and \*\*Underwriting\*\* were impacted — but that was only listed, not described.



> 💡 \*This logic error could have led to unfair rejections or missed opportunities. Clearer workflow implications help Product triage urgency.\*



---



\## 🐞 GW-2298 – IVANS Export 401 Failure



\*\*Summary:\*\*  

AZ producers failed to export IVANS files due to a 401 error. This broke the \*\*Format Daily IVANS File\*\* job in TRAIN. Issue appeared environment-specific and inconsistent.



\### 🔁 Reproducibility {id="reproducibility\_2"}

\- No QA or AC steps to recreate.

\- Dev noted hunch that it may be token-related but couldn’t confirm without logs.



> 💡 \*QA/Business needs to document: what policy types, timing, or triggers caused the job to run and fail?\*



\### ✅ Expected Behavior {id="expected-behavior\_2"}

\- No documented behavior to compare against. Is a retry mechanism expected? Should the job fail silently?



> 💡 \*Expected job behavior (fail fast vs retry vs queue) needs clear ownership and business validation.\*



\### 🖼️ Production Examples {id="production-examples\_2"}

\- Logs provided late in cycle. Early PROD/UAT logs could have clarified if this was a coverage issue or bad actor.



> 💡 \*Linking past IVANS job tickets or documenting successful runs would have made this fix faster.\*



\### 🔄 Workflows Impacted {id="workflows-impacted\_2"}

\- \*\*Marketing\*\*, \*\*Producers\*\*, and \*\*IVANS integration\*\* affected — but unclear how often or in what regions/states.



> 💡 \*Mapping producers by state and their IVANS usage frequency helps prioritize fixes and regression coverage.\*



---



\## 🐞 GW-1592 – Out-of-Sequence (OOS) Reapply Failures



\*\*Summary:\*\*  

OOS endorsements sometimes failed silently due to missing beans or validation conflicts, requiring manual reapply processing. This led to double AP charges or missing coverage.



\### 🔁 Reproducibility {id="reproducibility\_1"}

\- Mahesh and others documented good step-by-step flows late in the cycle.

\- Multiple environments lacked a testable example for weeks — delays slowed triage.



> 💡 \*Upfront test case reproduction with sample data would've caught risk bean loss much earlier.\*



\### ✅ Expected Behavior {id="expected-behavior\_1"}

\- Initial AC only required manual task creation. But broader system expectations were unclear:

&nbsp;   - Should reapply auto-process?

&nbsp;   - When is manual intervention expected?



> 💡 \*Clarifying “when to fail and alert” vs “when to silently retry” is critical in workflows with financial risk.\*



\### 🖼️ Production Examples {id="production-examples\_1"}

\- Eventually one policy (`PA0116946-05`) became the linchpin — but that came weeks after initial ticket creation.



> 💡 \*Business should prioritize sharing at least 1 complete example early to enable root cause analysis.\*



\### 🔄 Workflows Impacted {id="workflows-impacted\_1"}

\- \*\*Billing\*\*, \*\*Underwriting\*\*, and \*\*Validation logic\*\* were impacted.

\- Validation rules weren’t faulty — they were correct — but system behavior after failure needed better definition.



> 💡 \*Clearer mapping of when manual review tasks should generate, route, and close helped refine behavior.\*



---



\## 📌 Final Takeaways



To improve turnaround time and reduce repeat bugs:



| Paradigm           | Opportunity for Improvement |

|--------------------|-----------------------------|

| \*\*Reproducibility\*\* | Always include explicit steps or reference policies where bug occurred. |

| \*\*Expected Behavior\*\* | AC should describe not only what’s wrong, but what \*should\* happen instead, in business terms. |

| \*\*Production Examples\*\* | Even one confirmed policy speeds up developer triage dramatically. |

| \*\*Workflows\*\* | Document who is impacted and how — Underwriting? Billing? Agents? QA needs this for regression. |



---



\## ✅ Recommendations for Future Tickets



1\. \*\*QA Team\*\*

&nbsp;   - Add minimal steps to recreate issue from UI or job runner.

&nbsp;   - If applicable, include an expected result vs observed behavior.



2\. \*\*Product Owners\*\*

&nbsp;   - Clarify business rules driving expected behavior.

&nbsp;   - Include affected states, workflows, and priorities.



3\. \*\*Business SMEs\*\*

&nbsp;   - Provide at least one production policy or account where issue was observed.

&nbsp;   - Document any existing workarounds.



4\. \*\*Developers\*\*

&nbsp;   - Cross-reference similar bugs (e.g., clones, spikes) early on.

&nbsp;   - Log assumptions and questions in ticket early to drive alignment.



---





