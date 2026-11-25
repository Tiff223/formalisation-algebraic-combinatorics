# MA395 Research Journal

**Supervisor:** Christian Ikenmeyer  
**Last updated:** 25 November 2026

This journal records daily progress, decisions and next steps.

The [research notebook](notebook.md) contains detailed observations, mathematical examples, source references and open questions.


## How to use this journal

- **Writing the final essay:** start with the [current research notebook](notebook.md), which contains only the active argument, examples, sources and planned sections.
- **Understanding how a view changed:** use the dated entries and the “Changes of view and scope” table below.
- **Recovering an old draft or source record:** open the collapsed notebook archive at the end. It is historical evidence, not the current essay plan.

Entries below preserve what was understood or planned at their recorded time. Old deadlines, code drafts and descriptions of notebook policy are historical. **The current policy, agreed 18 November, is: notebook = current essay material; journal = research history, revisions and deferred work.**

## Current position — 25 November 2026

| Topic | Current use |
|---|---|
| Shared permutation/symmetric-group type | Explain terms, types and separately retrieved group structure |
| def, abbrev, notation, infix, macro | Three-command guide added to the local essay; infix and macro remain further work |
| Transpositions | Show broader swap inputs and identities valid in the identity case |
| Directed cycle graphs | Explain information loss and preservation of orbit components; specify the required bridge |
| Cycles | Main construction-versus-certification case, including repeated-entry counterexample |
| Generality and fidelity | Synthesise the distinct choices without claiming a universal AI tendency |
| Prompting guidance | Planned conclusion grounded in those examples; no measured improvement claimed |

The local essay develops the shared-type, transposition, cycle-graph and cycle-construction cases and synthesises the latter three. The essay also includes the guide to abbrev, def and notation. Prompting guidance remains planned material.


## 18 October 2026 — Goals and next steps

### Completed today

Set the project goals and agreed to follow the *2026–2028 Mathematics Research & PhD Application Timeline*.

No mathematical investigation, error checking or Lean coding was completed today.

### Target: 31 October 2026

Carry out initial checks of reported errors in autoformalised mathematics and record the evidence and unresolved questions.

Choose a manageable MA395 experiment and establish a GitHub repository and research notebook, in line with the October timeline milestone.

### Candidate cases

**Bender–Knuth definitions**

Check the reported omission of matching conditions and the selection of rightmost rather than leftmost excess entries.

These are candidate translation errors, not findings we have independently verified.

**N-partition definitions**

Examine duplicated, mathematically equivalent definitions and their interoperability.

This is a coherence problem, rather than necessarily a mathematical error.

### Next steps

1. Read the relevant textbook definitions and the paper’s discussion in §4.1.
2. Locate the corresponding Lean definitions and, where available, the original faulty versions and repairs.
3. Compare the informal and formal definitions; use small examples to check the reported errors.
4. Record source references, declaration names, commit IDs, findings and remaining uncertainty.
5. Distinguish reported claims from independently verified results.

### Following milestones

- **15 November:** Complete initial Lean examples and document a meaningful translation difficulty.
- **30 November:** Produce a 3–5-page technical note with working Lean code and clear findings.

### Reference documents

- *2026–2028 Mathematics Research & PhD Application Timeline*
- *Autoformalisation in Lean: Two Coherence Failures — Research Notes*

## 19 October 2026 — Paper overview and essay scope

### Completed today

Confirmed that the source textbook is Darij Grinberg’s *An Introduction to Algebraic Combinatorics*.

Discussed the approach in *Automatic Textbook Formalization*:

- Sketcher and prover agents.
- Mathematical and engineering review.
- Lean checks.
- Coordination through Git and an issue tracker (§§2.4–2.6).

Reviewed the coverage overview (Figure 3) and the reported 340 completed targets (§3.3).

Examined the repository screenshot listing four unfinished exercises and five `sorry` placeholders.

Distinguished proof-completion blockers from errors in translating mathematical meaning.

No Lean code or reported translation error was independently verified today.

### Decisions

Begin by reading one chapter chosen for mathematical interest, then evaluate selected definitions and theorem statements in its formalisation.

Decide whether to include further chapters only after assessing the first chapter’s workload and the depth of the analysis.

Symmetric functions remains a candidate because of the N-partition and Bender–Knuth cases. No chapter has been selected yet.

Consider solving and formalising one unfinished exercise as a possible later extension or separate URSS project.

This is a tentative direction, subject to:

- Interest.
- Feasibility.
- Current repository status.
- Discussion with the supervisor.

### Next session — 20 October

Compare candidate chapters by interest, prerequisites, length and opportunities for evaluating the formalisation.

Choose the first chapter and a manageable initial reading section.

Continue working toward the 31 October target.

## 20 October 2026 — Chapter 5 selected

### Completed today

Compared the textbook topics using the repository’s contents index and discussed their mathematical appeal and possible relevance to the essay.

Selected **Chapter 5: Permutations** as the first chapter to read, based on personal interest.

### Current status

Beginning independent reading of Chapter 5, covering:

- Basic definitions.
- Transpositions.
- Cycles.
- Involutions.
- Inversions.
- Lehmer codes.
- Signs.
- Cycle decomposition.

Reading is not yet complete.

No formalisation evaluation or Lean coding has been completed today.

### Next steps

Read and understand Chapter 5, then return to discuss its formalisation and select definitions and theorem statements for detailed comparison with Lean.

Decide whether to include additional chapters after assessing the workload and findings from this first chapter.

## 26 October 2026 — First Lean source inspection

### Completed today

Began looking at the Chapter 5 Lean file:

```text
AlgebraicCombinatorics/Permutations/Basics.lean
```

Developed a targeted inspection guide covering:

- Representations.
- Composition.
- Hypotheses.
- Boundary cases.
- Counting statements.
- Coherence between definitions.

Saved the guide in the new research notebook.

Source comparison identified a difference between the textbook’s directed cycle diagram and `cycleDigraph`, which constructs an undirected graph without loops.

Recorded the identity and opposite three-cycles as distinguishing examples.

This is an assistant-led source observation. No Lean test or downstream investigation has been completed.

### Decisions

Maintain two complementary documents:

- **Journal:** Daily progress, decisions and next steps.
- **Notebook:** Lasting discoveries, comments, examples, references and open questions.

Update the relevant dated entry on each day we work in this chat, consolidating multiple sessions on the same day.

Record only work actually completed and keep observations distinct from tested results.

### Current status

Lean is new to the student.

The code in the guide has not yet been explained or understood in detail.

Completion of Chapter 5 reading has not been confirmed.

No new Lean proof, repair or compiled experiment was produced today.

### Next steps

Explain the guide slowly, beginning with:

1. `Sn`.
2. `symmetricGroup_conj_iso`.
3. `cycleDigraph`.

Translate each definition into ordinary mathematics before discussing proof tactics.

Reproduce the cycle-diagram examples in Lean once the necessary basics are understood.

Inspect downstream uses before assessing the wider impact.

Continue toward the 31 October initial-check milestone.

### Research notebook

[Research notebook — Google Docs](https://docs.google.com/document/d/18wzFPSxEs81265IJNlBlrQ83XyhNifCrfr5rRAc1NNw)

## 27 October 2026 — Annotated source and explicit conjugation proof

### Completed today

Worked through the opening definitions, cardinality results, finite-type and decidable-equality instances, composition, natural and integer powers, and conjugation in Chapter 5.

Explained Lean notation and prepared annotations at the student’s chosen pace.

Published an annotated copy in:

```text
AlgebraicCombinatorics/Permutaions_Tiff/Basics.lean
```

This is separate from the fork’s `Permutations` folder for comparison.

Reviewed the annotations and edits through **line 470** against the fork copy, with an upstream check for the original opening definitions and conjugation construction.

A README draft was discussed earlier; its publication was not checked in this review.

Developed separate multiplication-preservation, injectivity and surjectivity lemmas for the conjugation map, followed by an explicit bundled isomorphism construction at lines 420–470.

### Observations and revised assessment

**P5-005 — Naming and readability**

Updated the notebook with verified source evidence: the upstream conjugation signature uses `Equiv.Perm`, while the annotated copy uses `SymmetricGroup`.

Retained the counterargument that standard library names can aid recognition and reuse.

Readability depends on the audience; renaming is not a mathematical correction.

**P5-006 — Bundled constructions and proof reuse**

Recorded that the library construction already carries the required proofs, so reusing it is not circular.

Distinguished an equivalence from a bundled multiplicative equivalence and identified comments that need correction.

**P5-007 — Explicit conjugation proof**

Recorded that the new proof development makes the mathematical obligations more visible.

The hypothesis specifies the conjugation formula without assuming its isomorphism properties.

The final construction uses the homomorphism lemma and proves inverse identities directly.

**Other points**

Recorded that the existence theorem alone does not identify the particular conjugation map.

Retained the proposed derivation of `sn_zero_card` from `sn_card 0` as untested. The published code still uses `native_decide`.

### Documentation organisation

Discussed keeping the research notebook and journal in the GitHub fork, alongside the annotated Lean source.

Prepared complete Markdown versions for:

```text
research/notebook.md
research/journal.md
```

The notebook version uses Lean code blocks, mathematical notation and source links.

Prepared the text for copying into GitHub. Committing these Markdown files has not yet been verified.

### Decisions and current status

Keep research findings separate from syntax-learning notes and unverified conjectures.

No new semantic error in the original formalisation was established by this review.

The source edits and proof text were inspected on GitHub, but the edited module was not compiled during the review.

The fork’s comparison copy already contains annotations; upstream is needed as the clean baseline.

The notebook records file-content hashes and the need for commit permalinks.

### Next steps

1. Correct the comments about `permCongr`, circularity and the strength of the existence statement.
2. Compile the exact edited module and resolve any reported errors.
3. Check how the two copies will be used without importing duplicate declarations.
4. Compare the explicit construction with the library construction.
5. Resume reading after line 470.
6. Commit the Markdown notebook and journal after reviewing their previews.

Continue checking the textbook meaning as well as Lean’s acceptance of the code.

## 28 October 2026 — Clarifying proof reuse and revising annotations

### Completed today

Revisited the conjugation section of Proposition 5.1.3. Clarified that `f.permCongrHom` provides a group isomorphism, as indicated by its `≃*` type. Discussed checking the type by hovering or using `#check Equiv.permCongrHom`.

Distinguished the role of the later lemmas: unfolding the formula, retrieving properties of the bundled isomorphism, applying general group results, and identifying the inverse or special cases.

Rewrote the main annotation in discussion around Tiffany's concern about the visibility of the mathematical argument. The revised wording explains the library construction and then motivates the step-by-step alternative proof.

Stated `symmetricGroup_iso_of_equiv` precisely in English: given a bijection between X and Y, their symmetric groups are isomorphic. Distinguished this existence conclusion from a statement specifying the conjugation map.

Confirmed that the notebook and journal are populated in `Research_TIff` on GitHub, and updated both with today's discussion and verification status.

### Observations

The original construction reuses an existing isomorphism and its proofs. Its short subsequent lemmas expose the formula and properties for readers and later proofs.

The alternative development makes the reasoning more visible locally. This supports an observation about mathematical exposition; it does not establish a new semantic error or greater fidelity merely from having more proof steps.

### Source and validation status

The first check returned the previously reviewed source. A subsequent check confirmed today's edits on GitHub, with blob `d7e32c83b0e2e4c86ba27b808e8ec569248c866b`.

Verified the revised conjugation annotation, the added `#check Equiv.permCongrHom`, removal of the “trivial/useful” labels, and the revised explanation of the existence conclusion. Updated the notebook to reflect confirmed publication.

No compilation result was independently verified. The alternative construction now ends at line 490, and the permutation-notations section starts at line 493.

### Next steps

1. Publication of the revised annotations is confirmed; retain the source version reference for the essay.
2. Compile the edited module and record the result.
3. Continue after the conjugation section at the student's pace.
4. Keep statement fidelity, proof reuse and readability distinct in the essay analysis.

## 3 November 2026 — Statement fidelity and preliminary notation review

### Completed today

Resumed reading around the permutation-notations section and screened two-line notation, one-line notation and the cycle digraph. Tiffany's initial impression was that the definitions were handled reasonably well; she noticed no major problems in this preliminary pass. The process felt tedious, so detailed inspection is deferred.

Discussed how the purpose of textbook formalisation affects its evaluation. Distinguished mathematical fidelity, explanatory presentation and library reuse.

Read Proposition 5.1.3 in the extracted text of textbook page 271 and confirmed its two claims: conjugation produces a permutation of Y, and the resulting map between symmetric groups is an isomorphism.

Prepared a revised annotation and a combined Lean statement with an explicit definition of group isomorphism. The draft keeps both claims together and leaves the proofs open with two `sorry` placeholders.

### Decisions and status

Prioritise accurate theorem statements over completing proofs. Supporting proof lemmas can be added later; the immediate aim is to assess whether an AI-generated statement captures the source.

Added P5-008 to the notebook to preserve this methodological direction and the draft statement. Today's screening is not a completed verification, and the earlier cycle-digraph lead remains open.

No compilation or publication of today's Lean draft was checked. No new mathematical error was established.

### Next session — 4 November

Reread the three notations in detail, comparing the definitions with the textbook and testing small examples. Revisit the open cycle-digraph question without treating the preliminary impression as a final assessment. Proof completion for Proposition 5.1.3 remains optional.

## 18 November 2026 — Essay development and cycle-construction analysis

### Scope of this entry

Retrospective consolidation of the research discussions and local essay work on 14–18 November, recorded on 18 November. This entry does not imply that all activities occurred today.

### Completed since the previous journal update

- Explained why `Permutation X` and `SymmetricGroup X` can both abbreviate `Equiv.Perm X`: distinguish a permutation term, its underlying type, and the separately registered group structure.
- Inspected actual source examples of composition and inverse laws. Explained how imported instances supply the algebraic structure needed by general theorems.
- Compared the annotated `Permutaions_Tiff/Basics.lean` copy with `Permutations/Basics.lean`. The illustrative `inferInstance` check in the annotated copy is absent from the comparison file; the essay now uses actual theorem examples from the latter.
- Reviewed notation, cycle graphs, transpositions, and simple transpositions. Retained the cycle-graph lead without claiming a downstream error.
- Inspected the cycle discussion at lines 983–1113 and counting subsection at 1115–1180 of the selected `Permutations/Basics.lean` version. Involutions start at line 1182; earlier references to line 1394 as the end of cycles were corrected.
- Developed a repeated-entry counterexample: `cyc [0,1,2,0,3]` acts as `(1 2)(0 3)`, so the construction need not produce a single nontrivial cycle.
- Distinguished properties of the general construction from results requiring a proof of `IsCycle`. Discussed `cyc_isCycle`, `cyc_apply_of_not_mem`, and `cycle_eq_transposition`.
- Compared the construction with the textbook's distinct-entry definition, including its equivalent piecewise formula and its one-cycle convention.
- Revised the local essay through user-approved changes, adding source/context tables and complete selected theorem statements with proofs replaced by `sorry` for exposition.
- Set up VS Code with LaTeX Workshop. Corrected the unavailable code font, logical-symbol rendering, and compiler configuration; the document now builds with XeLaTeX.

### Current essay

The working master is the local file `/Users/liuaitian/Desktop/MA395/essay.tex`, with `essay.pdf` beside it. The latest compiled version has six pages. These files have not been published to GitHub as part of this update.

The essay's two current themes are:
1. The shared underlying type of permutations and symmetric groups, and retrieval of group structure.
2. What a definition's name does not guarantee: general cycle construction, additional hypotheses, and textbook-facing alternatives.

The paragraph introducing an “intermediate level of assumptions” was removed at Tiffany's request because it interrupted the section's main argument. The counting theorem was also replaced as the main example by a theorem explicitly taking a cycle proof.

### Evidence and limits

- The fork's Lean and textbook TeX sources were inspected. The source baseline is commit [`8ec0305`](https://github.com/Tiff223/formalisation-algebraic-combinatorics/commit/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912).
- The repeated-entry example was checked mathematically and by evaluating the adjacent-swap product in Python on all four inputs: 0→3, 1→2, 2→1, 3→0.
- A standalone Lean check of that example was started but interrupted before producing a result. No successful Lean compilation of the counterexample or the edited project module is claimed.
- Successful XeLaTeX compilation and rendered-page inspection verify the essay artifact, not the validity of new Lean proof code.
- No new semantic error in the source theorems was established. The cycle observation concerns the domain of a general construction, its naming, and the hypotheses needed for intended interpretations.

### Decisions and collaboration

- Maintain these GitHub Markdown files as the research records.
- Update the journal on research days, consolidating multiple sessions on the same day; put lasting observations and evidence in the notebook.
- Explain code in ordinary mathematics, define unfamiliar Lean terms, and record file paths, source lines, and context.
- Show substantive proposed essay wording in chat and wait for Tiffany's approval before editing the essay. Directly requested edits, such as removing a paragraph, are already authorised.
- Record completed work separately from proposals, mathematical calculations separately from Lean-checked results, and source observations separately from claims of translation errors.

### Next steps

1. Complete a reproducible Lean check of the repeated-entry counterexample and record the exact command, dependency version, and result.
2. Keep the cycle section focused on construction versus certification; avoid accumulating tangential examples.
3. Retain commit-based source links for cited lines and distinguish the fork, annotated copy, and upstream baseline.
4. Continue source inspection at Tiffany's chosen pace; do not infer that all of Chapter 5 or the involution section has been reviewed.
5. Revisit the cycle-graph representation and its downstream uses before assessing impact.

See notebook findings P5-009–P5-011 for the detailed record.

### Meeting summary and agreed research direction — 18 November

Tiffany supplied a meeting summary and asked that it be included in the research records.

**Agreed direction**

1. Compare `notation`, `abbrev`, `def`, and, where useful, `macro` and `infix`. Use examples to explain when each is appropriate, what it changes, and its advantages, disadvantages and limitations.
2. Develop the transposition and cycle-graph observations alongside the cycle-construction case.
3. Investigate a working theme: the inspected formalisation often uses a general construction or a fact with fewer hypotheses, then supplies the conditions needed for a specific mathematical interpretation.
4. End the eventual essay with practical guidance for people using AI to formalise mathematics, including what to specify in prompts.

**Examples and qualifications**

- The swap construction accepts equal arguments. Basic swap identities hold in that identity case as well as for distinct arguments. This is genuine generalisation of the domain; it does not mean that every theorem about genuine transpositions can omit distinctness.
- The graph construction forgets direction and self-loops while retaining orbit components. This is a representation reduction whose adequacy depends on the property being studied, not automatically a stronger theorem about every graph.
- The cycle construction can return a permutation with more than one nontrivial cycle. Later cycle-specific results explicitly require `IsCycle`; the file provides a theorem supplying that property under suitable list assumptions.

The phrase “AI tends to prove more general facts” is retained as a research hypothesis suggested by these examples, not a measured general conclusion. The source shows separation of construction and property, but does not by itself establish what an AI agent understood or intended.

For directed graphs, specify the notion of connectivity. Weak components correspond to components of the underlying undirected graph. In a finite permutation graph, directed reachability also follows the finite cycles, but a formal transfer requires an explicit correspondence; an arbitrary directed graph does not have the same strong and weak components.

**Work completed in recording this meeting**

Rechecked the relevant fork declarations at the existing commit baseline and consulted Lean's official reference on definitions, notation, custom operators and macros. Added notebook P5-012 with a comparison agenda, preliminary examples, a careful synthesis of the three cases, and draft prompting guidance. No new Lean experiment or essay edit was performed for this meeting update.

**Next research tasks**

Prepare and compile small comparison examples for the five mechanisms; document their types, expansions, scope and usability with existing instances. Clarify and, if needed, formalise the graph correspondence. Develop the proposed guidance from the evidence rather than claiming prompt improvements have already been tested. Present new essay wording for approval before applying it.

### Reorganisation of the research records — 18 November

Tiffany clarified the roles of the documents: the notebook should contain what she currently intends to use in the final essay. Views she no longer accepts belong in the journal, recording what was considered and why the position changed.

Reorganised the notebook in essay order, with a writing map and a repeated format: claim, mathematical explanation, source evidence, example, paragraph plan and verification limits. Consolidated overlapping observations into seven active topics. Kept planned material visibly separate from already developed essay sections.

#### Changes of view and scope

The table distinguishes a corrected interpretation from a valid topic that is simply outside the current essay. It does not imply that Tiffany endorsed every early assistant suggestion.

| Earlier concern, formulation or draft | Present position | Reason and destination |
|---|---|---|
| Concern that using an existing conjugation isomorphism assumes what must be proved | It reuses a library construction carrying the required proofs | The bundled type includes the evidence. Earlier concern and explicit alternative development remain historical below |
| Question whether the suffix “Hom” implies only a homomorphism | Read the actual result type: the relevant construction is a multiplicative equivalence | The name is not a replacement for inspecting the type; historical discussion retained |
| Preference for replacing standard library names with textbook aliases as if inherently better | Naming is audience-dependent; the underlying type is unchanged | Relevant current evaluation retained in notebook section 2; before/after history archived |
| The cycle construction described as “not fully defining a cycle” | It fully defines a permutation; a separate proof certifies the nontrivial-cycle property | More precise separation of construction and certification, retained in notebook section 5 |
| Counting theorem as the main cycle example | Use a later theorem explicitly taking an IsCycle proof instead | Tiffany redirected the section toward why property certification is required; counting discussion archived |
| Intermediate-assumptions paragraph about successor and rotation results | Mathematically useful nuance, but not part of the current essay explanation | Removed at Tiffany's request because it interrupted the main argument; retained only as history |
| Long list of implementation difficulties for a direct cycle construction | Brief comparison plus the textbook definition itself | Tiffany asked for a short view; extended discussion preserved in archive |
| Cycle-graph simplification as a possible mismatch | Evaluate information loss separately from preservation of orbit components | The current essay direction is a property-specific analysis, not a demonstrated false theorem |
| “The directed theorem follows” without specifying connectivity | Distinguish weak connectivity, directed reachability and the finite-permutation setting | The intended bridge needs to be explicit; current qualified conclusion in notebook section 4 |
| “AI tends to prove more general facts” as an unrestricted conclusion | A working interpretation of selected examples | No systematic sample or generation evidence supports a general claim about AI; qualified synthesis in notebook section 6 |

#### Material moved out of the active notebook

- Chronological syntax-learning notes, dated source-comparison logs and superseded formulations.
- The old conjugation proof discussion and uncompiled combined statement draft.
- Unselected leads about integer indexing, duplicate simple-transposition definitions, involution coverage, Bender–Knuth and N-partitions.
- Proposed replacement of native_decide for small-cardinality results.
- Editorial history of rejected examples and removed paragraphs.
- Earlier notebook IDs and their detailed historical records.

These items were not all mathematically rejected. Some are corrected interpretations, some are unused drafts, and some remain deferred questions. They are no longer mixed with material intended for the final essay.

#### Traceability of previous observation labels

| Earlier labels | Current location |
|---|---|
| P5-001 | Notebook section 4: active graph observation; older wording archived |
| P5-002–P5-004 | Deferred leads, journal archive |
| P5-005 | Notebook section 2: current audience-dependent naming evaluation; history archived |
| P5-006–P5-007 | Historical conjugation development; general proof-reuse lesson in notebook section 6 |
| P5-008 | Current statement-fidelity principle in notebook sections 6–7; old statement draft archived |
| P5-009 | Notebook section 1 |
| P5-010 | Notebook section 5 |
| P5-011 | Source/evidence and writing conventions consolidated in notebook |
| P5-012 | Meeting plan distributed into notebook sections 2–7; full meeting record archived |

#### Validation and next action

No new Lean execution or mathematical experiment was performed in this reorganisation. Evidence statuses remain explicit. The local essay was read to check which material is already developed; it was not edited.

Next, develop only the planned sections in the notebook's writing map, verify examples before making stronger claims, and present substantive essay wording for approval. Future reconsidered views should move here, while the notebook presents the latest accepted interpretation.




### Essay update — transpositions and cycle graphs, 18 November

At Tiffany's request, added the two observations from the current notebook to the local essay.

- **Transpositions:** included the construction and complete squaring-theorem statement with an exposition-only proof placeholder. Explained decidable equality, the equal-input identity case, the advantage of a broader domain, and where genuine-transposition conditions remain necessary.
- **Cycle graphs:** included the adjacency condition, full reachability–orbit statement with its proof omitted, and the identity and opposite-three-cycle examples. Explained which information is lost, what orbit information survives, weak versus directed connectivity, and the correspondence still needed for a formal directed formulation.
- Kept these as different design choices: input-domain extension versus information-forgetting representation.
- Converted the raw meeting-summary prose at the end of the local LaTeX file into actual sections and retained the unimplemented notation-comparison and prompting tasks as nonprinting comments.
- Pinned the essay's source convention and Lean source link to the inspected commit rather than relying on changing main-branch line numbers.
- Compiled with XeLaTeX and inspected the new and reflowed pages. The current local PDF has eight pages. No new Lean proof, counterexample test or graph bridge was compiled.

The notebook writing map now marks the transposition and graph sections as developed in the local essay. Remaining writing work is the language-mechanism comparison, synthesis and final prompting guidance. The local essay remains unpublished on GitHub.

### Follow-up on permutation operations and group laws — 18 November

Tiffany asked for a clearer account of when the formalisation uses composition directly, when it retrieves group structure, and whether the ability to compose functions justifies group laws. Read the pinned `AlgebraicCombinatorics/Permutations/Basics.lean` from the beginning through the conjugation material for Proposition 5.1.3 (lines 1–300). Cross-checked the local textbook statement and the local Mathlib definitions.

The earlier description that the comparison file lacked an explicit group instance check was too broad. The annotated copy requests `Group (SymmetricGroup X)`, while the comparison file explicitly requests `Group (Equiv.Perm X)` at line 137. Both names refer to the same underlying type. [Comparison file, lines 136–137](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L136-L137)

The relevant progression is the definition of multiplication (182–183), the associativity theorem with a semigroup requirement (186–187), and the inverse theorem with a group requirement (220). The conjugation construction also exhibits the distinction between a bijection of permutation types and a multiplication-preserving bijection (248–249 and 275–277). When the source and target coincide, the file expresses conjugation using group multiplication (297–300).

Ran a standalone check with Lean 4.28.0 and the local Mathlib checkout at `8f9d9cff6bd728b17a24e163c9402775d9e6a365`. Both group requests yielded `Equiv.Perm.permGroup` and the semigroup request yielded its semigroup structure. The composition, inverse and conjugation examples compiled successfully. The project module was inspected at the pinned source revision and the check ran against the local Mathlib build.

Updated notebook section 1 with the precise source evidence and verification. Proposed wording for the essay in chat for review.

### Essay revision on when group structure enters — 18 November

Replaced the passage Tiffany supplied after she asked when the symmetric group structure enters the construction. The new text leads with the Mathlib import and the explicit instance check at lines 136–137. It contrasts the pointwise composition formula with the semigroup requirement for associativity and the group requirement for the inverse law. A constant self-map gives a contrast with invertible permutations. A short paragraph on Proposition 5.1.3 explains the role of multiplication preservation.

The revised essay compiled with XeLaTeX and has seven pages. The graph source table and code excerpt were kept together after pagination changed. The Lean evidence remains the source inspection and standalone checks recorded in the preceding entry.

## 24 November 2026 — From the three examples to a common argument

Replaced the standalone textbook-definition and alternative-constructions passage with “Generality and the link to the textbook.” The earlier passage described direct cycle construction and a restricted wrapper in detail. The synthesis retains brief textbook comparisons and develops two advantages raised in discussion. A single theorem can cover boundary inputs, and a general result can be reused to establish a textbook specialisation.

The essay distinguishes three routes. The swap law applies immediately to distinct inputs. The cycle construction has an explicit certification theorem, `cyc_isCycle`. The graph theorem establishes the orbit partition for the undirected simple graph. Recovering the directed result requires relating connectivity and reachability, a correspondence the inspected Lean section leaves implicit. Forward iteration around a finite orbit justifies the link mathematically.

The local essay rebuilt successfully with XeLaTeX and renders as seven pages. This revision added no Lean implementation or compilation check.

<details>
<summary>Earlier notebook material on textbook cycles and alternative constructions</summary>

#### 5.6 Textbook definition and brief alternatives

| Source | Context |
|---|---|
| [Basics.tex, 310–341](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/tex/Permutations/Basics.tex#L310-L341) | Cycle definition |
| [Basics.tex, 391–395](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/tex/Permutations/Basics.tex#L391-L395) | One-cycle convention |

For distinct i₁,…,iₖ in X, the permutation sends i₁→i₂→…→iₖ→i₁ and fixes all others. Equivalently, with iₖ₊₁=i₁,

$$
\operatorname{cyc}_{i_1,\ldots,i_k}(p)=
\begin{cases}
i_{j+1},&p=i_j\text{ for some }1\le j\le k,\\
p,&p\notin\{i_1,\ldots,i_k\}.
\end{cases}
$$

These are equivalent presentations of one definition.

A direct construction could implement the formula and prove bijectivity and, for k≥2, IsCycle. A simpler alternative is a restricted wrapper around formPerm requiring input proofs and returning the permutation with its cycle proof. Neither alternative has been implemented in this research. Restrictions move proof obligations rather than removing them.

The textbook recognises the identity as a one-cycle on a nonempty set; IsCycle excludes it. Empty/singleton input lists produce the identity. A formulation including those cases must state the convention; retain a list or specified set if singleton labels matter, since the permutation alone cannot distinguish [a] from [b].

</details>

## 25 November 2026 — Choosing abbreviations, definitions and notation

The supervisor asked for practical guidance on choosing `abbrev`, `def` or `notation`. Inspected the pinned source declarations for `Sn` (line 134), `oneLineNotation` (lines 396–397), `simpleTransposition` (lines 776–778), and `s[i]` (line 781). The adjacent-swap definition and its bracket notation demonstrate two different choices for the same mathematical operation. The group lookup gives an observable comparison between an abbreviation and an ordinary definition of the same permutation type.

A standalone check compiled with Lean 4.28.0 and local Mathlib at `8f9d9cff6bd728b17a24e163c9402775d9e6a365`, using the individual Mathlib imports needed by these excerpts. It confirmed that Lean finds the group structure through `Sn`, that automatic lookup fails for the same-body `def` until the underlying type is exposed, and that `s[i]` gives the same permutation as `simpleTransposition i` once the notation is in scope. Both ways of writing the four-position adjacent swap gave the one-line list [0, 2, 1, 3].

The earlier experiment plan used unrelated toy examples and included infix operators and macros. The proposed section focuses on the three commands requested and uses the permutation file throughout. The toy examples were planning notes and were not compiled. The essay wording was shown for review before the local source was changed.

After approval, added the guide after the shared-type section, with compact source tables for the three code excerpts. XeLaTeX rebuilt the local draft successfully. The guide is on page 3 of the eight-page PDF.

The follow-up asked how to choose between an abbreviation and notation when either could express the same thing. Prepared two side-by-side examples for the guide. A standalone Lean 4.28.0 check confirmed that the name `Perms 4` and the bracket form `P[4]` produce the same permutation type with the same group structure available, and that an illustrative alias `adjacentSwap i` agrees with the existing notation `s[i]` for permutations of four positions. The proposed LaTeX addition compiled in a temporary copy. A follow-up asked whether the two forms have any practical differences. A second Lean check verified equality of the inferred group structures by `rfl`; with notation display disabled, the printed definitions retained `Perms 4` for the abbreviation and showed `Equiv.Perm (Fin 4)` for the bracket form. The expanded proposal explains the difference between the retained name and the written shorthand. The master awaits wording review.

## Archive — Research notebook before the 18 November reorganisation

This preserves the complete previous notebook, including its historical drafts, corrections, source records and earlier IDs. It is retained to avoid losing the reasoning behind revisions. **The current notebook supersedes it as the writing reference.** Statements inside reflect their earlier context and verification status.

<details>
<summary>Open the complete historical notebook snapshot</summary>

# MA395 Research Notebook

**Topic:** Permutations and autoformalisation  
**Supervisor:** Christian Ikenmeyer  
**Established:** 26 October 2026  
**Last updated:** 18 November 2026

## Purpose and working scope

This notebook collects mathematical observations, useful comments, inspection methods, examples and open questions.

The research journal separately records dated progress, decisions and next steps. Substantive findings belong here. Corrections and their reasons should be retained so that the evidence remains traceable.

The initial scope is Chapter 5 (Permutations) of Darij Grinberg’s *An Introduction to Algebraic Combinatorics*, using the selected reading range pp. 270–312.

The working plan is to:

1. Understand the mathematics.
2. Compare selected definitions and theorem statements with their Lean formalisation.
3. Decide whether to include more chapters after assessing the workload.

Solving an unfinished exercise remains a possible extension or separate URSS direction, not a commitment.

### Finding labels

Labels such as **P5-005** are internal notebook references:

- **P5:** Chapter 5 — Permutations.
- **005:** the fifth recorded observation.

These are not theorem numbers from the textbook or Lean.

## Lean inspection guide — 26 October 2026

**Central question: does the Lean statement express the mathematics intended by the textbook?**

A checked proof establishes the formal statement that was written. It does not, by itself, establish that this statement is a faithful translation.

Begin with definitions and theorem statements. Detailed proof scripts can wait.

### 1. Identify the objects and their representation

Look first at:

- `Permutation`
- `SymmetricGroup`
- `bracketN`
- `Sn`

The file uses `Equiv.Perm X` for permutations of `X` and `Equiv.Perm (Fin n)` for `Sn`. Record what the objects mean before reading proofs.

The textbook labels $[n]$ by $1,\ldots,n$, whereas `Fin n` uses $0,\ldots,n-1$. This can be a harmless relabelling, provided every construction is translated consistently.

Separately, the textbook’s bracket notation permits integer $n$, while the Lean abbreviation uses natural $n$. Check whether excluding negative inputs changes the scope of a particular statement.

A representation change and a restriction of scope are different questions.

Starting declaration:

```lean
abbrev Sn (n : ℕ) := Equiv.Perm (Fin n)
```

### 2. Check composition and relabelling

Read permutation products as function composition:

```lean
(α * β) x = α (β x)
```

Thus, `β` acts first. Use a small example to check the order rather than relying on how the symbols look.

Inspect `symmetricGroup_conj_iso` alongside Proposition 5.1.3.

A bijection `f : X ≃ Y` should transport a permutation $\sigma$ of $X$ to

$$
f \circ \sigma \circ f^{-1}
$$

on $Y$.

Check that the construction is bijective and preserves multiplication.

The Lean result uses `≃*`, which here denotes a group isomorphism, and is implemented using `f.permCongrHom`.

### 3. Compare assumptions as well as conclusions

For each theorem, list:

- The variables.
- Their types.
- Every hypothesis.
- The conclusion in ordinary mathematics.

Look for added assumptions that make the result weaker, omitted hypotheses, and conclusions that assert only one direction of the textbook’s claim.

Examples worth checking:

- Finiteness assumptions in `symmetricGroup_card`.
- The distinctness requirement `l.Nodup` in cycle statements.
- The conditions `1 < k` and `k ≤ n` in `num_kCycles_formula`.

Some Lean assumptions concern how objects are represented or computed. Do not classify an unfamiliar assumption as a mathematical restriction before understanding it.

### 4. Test boundary cases

Use small inputs:

- $n=0$.
- $n=1$.
- The identity permutation.
- Fixed points.
- Equal swap arguments.
- An empty cycle list.
- A singleton cycle list.

These cases often expose differences hidden in familiar examples.

For `cyc`, inspect the empty and singleton cases and the use of `l.formPerm`.

For `IsCycle`, check the convention that excludes the identity.

For `simpleTransposition`, examine the index type `Fin (n - 1)`, which selects adjacent positions. Check indexing carefully when translating back to the textbook.

### 5. Inspect what representations retain or forget

For `oneLineNotation`, ask:

- Does every entry appear exactly once?
- Does the notation determine the permutation?

Compare this with the corresponding uniqueness and no-duplicate results.

A representation should retain the information needed by the textbook’s use of it.

The `cycleDigraph` definition is especially worth investigating: see **P5-001** below. A familiar name is not sufficient evidence that the formal object has the intended meaning.

### 6. Check counting statements describe exactly the intended set

In `num_kCycles_formula`, inspect both membership directions for the finite set `S`:

1. Every member of `S` must be a $k$-cycle.
2. Every relevant $k$-cycle must belong to `S`.

A set of the claimed size containing only some examples would not establish the intended counting theorem.

Also check the range of $k$ and conventions for one-cycles.

### 7. Notice duplicated definitions and bridges

The file notes another simple-transposition definition in `Inversions2` and supplies `simpleTransposition_eq_canonical`.

This raises a useful coherence question:

> Are the two definitions mathematically equivalent, and is that equivalence available to later proofs?

Duplication alone is not a mathematical error.

For `IsInvolution`, the file starts with a permutation `σ` and defines:

```lean
σ * σ = 1
```

The textbook can start with an arbitrary function $f:X\to X$ satisfying

$$
f \circ f = \operatorname{id}
$$

and derive bijectivity.

Check whether the formalisation also provides that bridge. Starting with a permutation is not itself a false definition, but may omit part of the textbook’s development.

### 8. Record evidence before drawing conclusions

Use this order for each inspected item:

1. Textbook meaning.
2. Lean meaning.
3. Difference or agreement.
4. Small example.
5. Conclusion.

Record the declaration name, source location, repository version, hypotheses and unresolved questions.

Keep proof-completion issues separate from semantic translation issues.

Possible evidence-status labels:

- **Reported elsewhere**
- **Observed by source comparison**
- **Checked by a worked mathematical example**
- **Tested in Lean**
- **Resolved**

A finding can move through these stages. Do not describe source inspection as a completed Lean experiment.

## AI-suggested leads — P5-001 to P5-004

> **Authorship and verification note:** The following leads were suggested by ChatGPT and recorded because I consider them worth investigating. I have not personally inspected these observations. References to source comparison below describe the assistant’s reported inspection, not my independent verification.
>
> My own observations begin at **P5-005**.

### P5-001 — Cycle diagram loses direction and loops

**Recorded:** 26 October 2026  
**Status:** Observed by assistant source comparison; mathematical distinguishing examples identified; no Lean execution or downstream impact assessment completed.

#### Evidence and mathematical interpretation

The textbook’s cycle diagram has directed arcs

$$
i \longrightarrow \sigma(i),
$$

including loops at fixed points.

The repository’s corresponding TeX definition is `def.perm.notations`, part (c).

The Lean definition `cycleDigraph` returns `SimpleGraph (Fin n)`, with adjacency:

```lean
i ≠ j ∧ (σ i = j ∨ σ j = i)
```

This makes adjacency symmetric and excludes loops.

Consequently, it describes the underlying undirected graph with loops removed, rather than the full directed cycle diagram.

#### Distinguishing examples

**Identity permutation**

The textbook diagram contains one loop at every vertex.

The Lean graph has no edges; `cycleDigraph_one` states that it is the bottom graph.

**Opposite three-cycles**

On three vertices, the cycles $(0\ 1\ 2)$ and $(0\ 2\ 1)$ have opposite directions.

The Lean construction gives the same undirected triangle for both. The representation therefore does not determine the direction of a cycle.

#### Significance and limits

This is a concrete difference in the represented object.

It does not show that every theorem using this graph is wrong: forgetting orientation and loops still preserves the orbit components.

The theorem `cycleDigraph_connected_iff` relates reachability to integer powers of the permutation.

#### Next checks

- Reproduce the examples in Lean.
- Inspect uses of `cycleDigraph`.
- Determine whether the intended object is explicitly documented as an undirected simplification.
- Decide whether a renamed auxiliary graph or a directed representation would better match the source.

No repair has been implemented.

### P5-002 — Indexing and domain

Compare $[n]$ with `Fin n`, separating relabelling from the integer-to-natural domain restriction.

**Status:** Inspection question; no error established.

### P5-003 — Duplicate simple transpositions

Inspect `simpleTransposition_eq_canonical` and whether later proofs can move between definitions conveniently.

**Status:** Coherence question; duplication is not evidence of false mathematics.

### P5-004 — Involutions

Check the bridge between arbitrary self-inverse functions and bundled permutations.

**Status:** Coverage question; no missing theorem established.

### Earlier leads

The separate *Two Coherence Failures* notes discuss reported Bender–Knuth translation problems and duplicated N-partition definitions.

These remain background cases. Their historical faulty versions and repairs have not been independently verified in this project.

## P5-005 — Textbook-style abbreviations are not reused in Sn

**Recorded:** 27 October 2026  
**Status:** Readability observation from the definitions discussed; not a mathematical error.

**Location:** `AlgebraicCombinatorics/Permutations/Basics.lean`, declaration `Sn`, following the abbreviations `Permutation`, `SymmetricGroup` and `bracketN`.

### Observation

The authors introduce textbook-style abbreviations but do not consistently build later definitions using them.

Specifically, `Sn` is defined directly using `Equiv.Perm` and `Fin`:

```lean
abbrev Sn (n : ℕ) := Equiv.Perm (Fin n)
```

It could equivalently use the previously introduced abbreviations:

```lean
abbrev Sn (n : ℕ) := Permutation (bracketN n)
```

Unfolding `Permutation` and `bracketN` yields exactly the original expression. The two formulations are definitionally equal.

Reusing the abbreviations could make the connection to the textbook clearer; using library names directly exposes the underlying representation.

The authors’ reason for this choice is not established, and this local example does not establish a repository-wide pattern.

### Revision — 27 October 2026: readability and reuse

**Tiffany’s counterargument**

Using `Equiv.Perm` directly lets readers familiar with the library recognise the object without learning a project-specific alias.

Copying a statement written with `Permutation` into another project requires bringing that abbreviation too, or replacing it with the standard name.

Importing the original file makes its abbreviations available automatically.

**Revised assessment**

Textbook-style names may help readers following the textbook; standard library names may help library users recognise and reuse results.

Neither choice is automatically better.

This is an audience-dependent presentation choice, not a formalisation error or a general recommendation to replace library names.

The same question occurs in `symmetricGroup_card`.

Docstrings can explain the intended mathematics while retaining standard names, although Lean does not check that the prose matches the code.

**Source:** [Upstream Basics.lean](https://github.com/facebookresearch/algebraic-combinatorics/blob/main/AlgebraicCombinatorics/Permutations/Basics.lean)

### Example — Naming the groups in symmetricGroup_conj_iso

**Recorded:** 27 October 2026

**Location:** `symmetricGroup_conj_iso`, in the conjugation-isomorphism section labelled `prop.perm.Sf`.

Tiffany changed the formulation to use `SymmetricGroup` explicitly, to make it clearer which mathematical objects are isomorphic.

**Before — upstream formulation**

```lean
def symmetricGroup_conj_iso {X Y : Type*} (f : X ≃ Y) :
    Equiv.Perm X ≃* Equiv.Perm Y :=
  f.permCongrHom
```

**After — annotated copy**

```lean
def symmetricGroup_conj_iso {X Y : Type*} (f : X ≃ Y) :
    SymmetricGroup X ≃* SymmetricGroup Y :=
  f.permCongrHom
```

#### Readability rationale

`SymmetricGroup X` makes the group viewpoint explicit in the output type.

For a reader learning Lean alongside the textbook, this helps distinguish the groups being related from individual permutations.

`Equiv.Perm X` already denotes the type of all permutations, with its group structure supplied by the library. The original formulation does not claim that individual permutations are isomorphic.

#### Formal meaning

`SymmetricGroup X` and `Permutation X` both abbreviate `Equiv.Perm X`.

Replacing these aliases in the output type leaves its mathematical meaning unchanged. The construction `f.permCongrHom` is also unchanged.

This declaration is a definition of an isomorphism, rather than a theorem asserting only that some isomorphism exists.

#### Evidence and scope

Source comparison on 27 October verified that upstream uses:

```lean
Equiv.Perm X ≃* Equiv.Perm Y
```

The annotated copy uses:

```lean
SymmetricGroup X ≃* SymmetricGroup Y
```

at lines 308–309.

This replaces the earlier uncertainty about the starting spelling.

Both abbreviations unfold to the same underlying type. The published edit has been inspected, but its compilation has not been independently checked. Version evidence is recorded below.

#### Assessment

This is a concrete example supporting the textbook-reader side of P5-005.

Standard library names can still be more immediately recognisable to experienced Lean users.

The benefit depends on the reader and context; no mathematical error is alleged.

## P5-006 — Bundled constructions and proof reuse

**Recorded:** 27 October 2026  
**Location:** `AlgebraicCombinatorics/Permutaions_Tiff/Basics.lean`, lines 308–415.  
**Textbook reference:** Proposition 5.1.3.

### Observation

`symmetricGroup_conj_iso` returns a bundled group isomorphism, using `f.permCongrHom`.

Its result includes:

- The underlying equivalence.
- A proof that multiplication is preserved.

The definition therefore supplies a construction with the required evidence; it does not assume the proposition being proved.

The mathematical work is reused from Mathlib rather than reproduced step by step here.

The later lemmas expose:

- The formula.
- Bijectivity.
- Multiplication preservation.
- Identity preservation.
- The inverse.

Some extract existing evidence; others provide convenient rewrite statements.

Their short proofs do not make them useless or circular.

### Correction to comments at lines 310–346

`f.permCongr` is an equivalence whose underlying map also preserves multiplication.

It is not presented as a bundled multiplicative equivalence. This is different from saying that it is not a group homomorphism.

Mathlib explicitly proves `permCongr_mul` and packages this map as `permCongrHom`.

No claim that conjugation is the unique possible isomorphism is needed.

### Correction to the comment near line 404

The expression

```lean
Nonempty (Equiv.Perm X ≃* Equiv.Perm Y)
```

asserts that an isomorphism exists.

On its own, this is weaker than identifying the particular conjugation map and proving its properties.

The surrounding declarations provide that additional information.

### Research significance

Distinguish:

1. Semantic coverage.
2. Proof reuse.
3. Explanatory transparency.

A compact construction can formally establish the result while leaving its mathematical argument less visible to a beginner.

**Reference:** [Mathlib documentation: Algebra.Group.End](https://leanprover-community.github.io/mathlib4_docs/Mathlib/Algebra/Group/End.html)

The reference is to current documentation; the exact project dependency version has not been independently checked.

## P5-007 — Explicit development of the conjugation isomorphism

**Recorded:** 27 October 2026  
**Location:** `AlgebraicCombinatorics/Permutaions_Tiff/Basics.lean`, lines 420–470.  
**Textbook reference:** Proposition 5.1.3.

### New work

| Declaration | Purpose |
|---|---|
| `symmetricGroup_conj_isom_hom` | Proves multiplication preservation. |
| `symmetricGroup_conj_isom_injective` | Proves injectivity. |
| `symmetricGroup_conj_isom_surjective` | Proves surjectivity. |
| `symmetricGroup_conj_MulEquiv` | Constructs the bundled isomorphism. |

### Hypotheses and mathematical meaning

The hypotheses supply:

- A bijection `f`.
- A map `S_f` between symmetric groups.
- A hypothesis `h` specifying the conjugation formula.

The defining equation is:

```lean
S_f σ = (f.symm.trans σ).trans f
```

This formula sends `y` to:

```lean
f (σ (f.symm y))
```

In ordinary mathematical notation:

$$
S_f(\sigma)(y)=f\bigl(\sigma(f^{-1}(y))\bigr).
$$

The hypothesis specifies the map. It does not assume that `S_f` is injective, surjective or multiplicative.

### Inverse construction

The inverse candidate is:

```lean
(f.trans τ).trans f.symm
```

It sends `x` to:

```lean
f.symm (τ (f x))
```

In ordinary mathematical notation:

$$
S_f^{-1}(\tau)(x)=f^{-1}\bigl(\tau(f(x))\bigr).
$$

The final construction:

1. Supplies this inverse.
2. Proves both inverse identities.
3. Uses the multiplication-preservation lemma.

It does not invoke the separately named injectivity and surjectivity lemmas.

### Assessment

This makes the proof obligations more visible and is a useful pedagogical comparison with `f.permCongrHom`.

It still relies on equivalence constructions and simplification from the library.

Greater explanatory detail is not, by itself, evidence of greater semantic fidelity or a correction to the original mathematics.

### Validation

The published source was inspected through line 470.

No Lean compilation was performed during this review.

The mathematical strategy is coherent by inspection. Successful compilation of the exact edited module remains to be checked.

## Supporting learning notes and corrections

### Type-theoretic foundations — 6 November 2026

Lean uses dependent type theory as a foundation that brings mathematical objects, functions, propositions and proofs into a common framework. Through the propositions-as-types correspondence, a proof is represented by a term whose type is the proposition being proved, allowing Lean’s kernel to check it against the rules of the underlying theory ([Theorem Proving in Lean 4, §3.1](https://lean-lang.org/theorem_proving_in_lean4/Propositions-and-Proofs/); [Lean Language Reference, §2.3](https://lean-lang.org/doc/reference/latest/Elaboration-and-Compilation/)). Types also support inference and error detection, while dependent types express objects whose types depend on parameters, such as `Fin n`. Ordinary sets remain available within this framework: `s : Set X` denotes a set of elements of type `X`, and membership `x ∈ s` is distinct from the typing judgement `x : X` ([Mathematics in Lean, Chapter 4](https://leanprover-community.github.io/mathematics_in_lean/C04_Sets_and_Functions.html)). These features explain practical advantages of Lean’s foundation without implying that set theory is unsuitable for formalisation. For this project, the resulting distinction is important: translating the textbook’s set-based language into Lean requires choices of representation, whose faithfulness to the intended mathematics must be evaluated separately from whether the resulting proofs are accepted.

| Command | What it introduces | How Lean treats it | Typical use |
|---|---|---|---|
| `def` | A named definition. | Lean can replace the name with its definition, but procedures such as instance search do not normally do this automatically. | Define a function or mathematical object, such as `oneLineNotation`. |
| `abbrev` | A named definition marked for automatic unfolding. | Procedures such as instance search can replace the name with its definition automatically. | Give an existing type another name, such as `Permutation X := Equiv.Perm X`. |
| `notation` | A way to write an existing expression. | Lean interprets the notation as that expression; no new definition is introduced. | Write `𝔖₃` for `Equiv.Perm (Fin 3)`. |

### Naming choices

Lines 233–291 use `Permutation` in several signatures, while line 308 uses `SymmetricGroup` to emphasise the group-level construction.

These are presentation choices: the abbreviations unfold to `Equiv.Perm`.

Claims that one spelling is more machine-readable have not been measured.

### Natural and integer exponents

Natural and integer exponents use different exponent types.

In `perm_zpow_neg`:

```lean
(n : ℤ)
```

converts the natural number to an integer before negation.

This is a typing explanation, not a discovered mathematical discrepancy.

### A permutation witness and its pointwise formula

The witness `τ` in `symmetricGroup_conj_isPerm` is already a bundled permutation.

Its pointwise equation expresses agreement with the ordinary function:

```lean
fun y => f (σ (f.symm y))
```

Keep this application notation precise when annotating the composition.

### Small-cardinality proofs

The small-cardinality theorems still use `native_decide`.

Deriving `sn_zero_card` from `sn_card 0` remains a proposed alternative, not an implemented or tested edit.

## Comparison and version record — 27 October 2026

### Annotated source

[Annotated Basics.lean](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/main/AlgebraicCombinatorics/Permutaions_Tiff/Basics.lean)

**Reviewed range:** Lines 1–470.

**File blob SHA:**

```text
34b391a01fad9094bf8eb23e735377e2d7e07407
```

### Fork comparison copy

**Path:**

```text
AlgebraicCombinatorics/Permutations/Basics.lean
```

**File blob SHA:**

```text
de97b592253d2267fe2b7c694513966f94eed61f
```

This file already contains student annotations, so it is not a pristine upstream baseline.

### Upstream comparison

**Repository:** `facebookresearch/algebraic-combinatorics`

**Path:**

```text
AlgebraicCombinatorics/Permutations/Basics.lean
```

**File blob SHA:**

```text
59de10cf1249f982be44ac4e17768e38cf4510b9
```

The opening section was checked, including the conjugation construction.

### Version and organisation cautions

These are file-content identifiers, not commit IDs.

Capture commit permalinks before citing exact lines in the essay.

Separate folders aid comparison, but copies retaining the same namespace and declaration names may conflict if imported together. This has not been tested.

## Follow-up — 28 October 2026: understanding the conjugation construction

**Related findings:** P5-006 and P5-007.  
**Location:** `AlgebraicCombinatorics/Permutaions_Tiff/Basics.lean`, conjugation section, lines 308–470 in the retrieved version.

### Reading the type rather than the name

The suffix `Hom` in `permCongrHom` prompted a question about whether the construction gives only a homomorphism. The relevant distinction is in the type: for groups, `G →* H` denotes a homomorphism, while `G ≃* H` denotes an isomorphism.

To inspect the library declaration in Lean:

```lean
#check Equiv.permCongrHom
```

Hovering over the declaration also displays its type. These checks were explained in discussion; their execution by Tiffany has not been verified.

### Proof reuse and the reader's experience

Tiffany's initial impression was that the section first assumes conjugation is an isomorphism and then proves that it is one. The discussion clarified that `f.permCongrHom` supplies an already established construction, including the evidence required by its type.

This explains the short subsequent proofs:

| Declaration suffix | Role |
|---|---|
| `_apply` | Definitional equality, proved by `rfl`. |
| `_isPerm`, `_apply_val` | Explicit descriptions of the underlying conjugation map. |
| `_bijective`, `_mul` | Properties obtained from the bundled isomorphism. |
| `_one` | A general consequence of preserving the group operation. |
| `_symm`, `_self` | Identification of the inverse and the self-equivalence case. |
| `_iso_of_equiv` | An existence statement witnessed by the constructed isomorphism. |

The central presentation concern remains: a reader following the textbook may want to see why the conjugation formula preserves multiplication and is bijective. The original version reuses the library construction, whereas Tiffany's alternative makes more of that reasoning visible within this file.

### Revised annotation prepared in discussion

The annotation was rewritten to explain the construction first, then the role of subsequent lemmas, then the motivation for the alternative proof. It distinguishes `permCongr` and `permCongrHom` by the structure they package: the underlying map is the same, and multiplication preservation is included explicitly in the latter's bundled type.

The revised interpretation replaces the earlier conjecture about uniqueness of conjugation and the concern about circularity. The alternative proof is described as a more explicit mathematical presentation; greater semantic fidelity has not been established.

When polishing annotations, preserve Tiffany's viewpoint and develop the explanation for a future reader. Integrate necessary corrections into that explanation rather than writing a rebuttal to the original draft.

### The precise existence conclusion

```lean
theorem symmetricGroup_iso_of_equiv {X Y : Type*} (f : X ≃ Y) :
    Nonempty (SymmetricGroup X ≃* SymmetricGroup Y) :=
  ⟨symmetricGroup_conj_iso f⟩
```

In English: **Given a bijection between X and Y, there exists a group isomorphism between their symmetric groups.**

This states the existence conclusion of Proposition 5.1.3 without specifying the isomorphism's action. Its proof chooses the conjugation construction as the witness. This distinction concerns what the statement explicitly asserts, even though the proof uses the intended map.

### Publication and validation status

The first check on 28 October returned the previously reviewed version. A subsequent check confirmed the new published source, blob `d7e32c83b0e2e4c86ba27b808e8ec569248c866b`.

The revised main annotation is now present, along with `#check Equiv.permCongrHom` at line 310. The existence-conclusion annotation follows `symmetricGroup_iso_of_equiv` at line 416. The earlier “trivial/useful” labels have been removed from the surrounding lemmas. The alternative construction ends at line 490; the permutation-notations section now begins at line 493.

Publication of these edits is confirmed. The presence of a `#check` command is source evidence, not a recorded execution result; compilation has not been independently verified.

Both `Research_TIff/notebook.md` and `Research_TIff/journal.md` now contain the migrated documents. These GitHub files are the intended working copies for future updates.

## P5-008 — Purpose of formalisation and statement-first evaluation

**Recorded:** 3 November 2026.  
**Status:** Methodological observation and statement draft prepared in discussion; not a newly established translation error.  
**Related findings:** P5-006 and P5-007.  
**Source:** Darij Grinberg, *An Introduction to Algebraic Combinatorics*, p. 271, Proposition 5.1.3.

### Evaluation should reflect the intended purpose

Tiffany raised the question of what a textbook formalisation is meant to achieve. Preserving mathematical meaning, supporting readers, providing reusable library results and evaluating AI translation are related but distinct purposes.

Distinguish **semantic fidelity** (preserving the objects, assumptions, specified constructions and conclusions) from **expository fidelity** (following the textbook's presentation). Library reuse can supply a correct proof without displaying the argument locally. More proof detail alone does not establish a more faithful statement.

The next research question is to compare these criteria with the paper's stated objectives. Those objectives have not been re-examined in this session.

### Revised priority: translate the proposition before proving it

Tiffany's priority is now to state the source proposition explicitly, so its translation can be assessed independently of proof construction. Completing a proof is optional at this stage. For AI autoformalisation, a successful proof of a generated statement does not by itself establish agreement with the source.

The PDF's extracted text on page 271 was read in this session. Proposition 5.1.3 has two claims:

1. For a bijection f : X → Y and every permutation σ of X, the function f ∘ σ ∘ f⁻¹ : Y → Y is a permutation of Y.
2. The resulting map S_f : S_X → S_Y with that action is a group isomorphism, yielding S_X ≅ S_Y.

The proposed format keeps both claims in one theorem, with supporting proof lemmas available later. The first claim asserts bijectivity of an ordinary function, rather than starting with its output already bundled as a permutation. The second specifies the action of S_f and asserts that it is an isomorphism.

### Statement draft prepared in discussion

This uses the existing project abbreviations. It is not a standalone file, and the predicate should be declared only once in the relevant namespace.

```lean
def IsGroupIsomorphism
    {G H : Type*} [Group G] [Group H] (φ : G → H) : Prop :=
  Function.Bijective φ ∧
    ∀ a b : G, φ (a * b) = φ a * φ b

theorem symmetricGroup_conjugation_prop
    {X Y : Type*} (f : X ≃ Y) :
    (∀ σ : Permutation X,
      Function.Bijective
        (fun y : Y => f (σ (f.symm y)))) ∧
    (∃ S_f : SymmetricGroup X → SymmetricGroup Y,
      (∀ (σ : Permutation X) (y : Y),
        (S_f σ) y = f (σ (f.symm y))) ∧
      IsGroupIsomorphism S_f) := by
  constructor
  · sorry
  · sorry
```

**Validation:** This is an unproved, uncompiled draft prepared in chat. Its publication in the Lean source has not been checked in this session. The two `sorry` placeholders deliberately leave proof obligations open.

The conjunction records both claims but does not encode a sequential construction. A proof of the first goal is not automatically available in the second goal after `constructor`; a named lemma or a shared intermediate result can provide that dependency. The statement remains a candidate translation to assess, not a declaration that exact fidelity has already been established.

## Preliminary reading — 3 November 2026: three permutation notations

Tiffany screened the definitions of two-line notation, one-line notation and the cycle digraph, starting around the previously identified line 490. Her initial impression is that the definitions are handled reasonably well, and she noticed no major problems during this pass. She found the inspection tedious and plans a more detailed rereading on 4 November.

**Evidence status:** Student-reported preliminary screening, not a completed comparison or verification. The earlier assistant-suggested cycle-digraph issue in P5-001 remains open; today's impression neither confirms nor resolves it.


## P5-009 — Shared permutation type and separately supplied group structure

**Recorded:** 18 November 2026; consolidates discussions on 14–18 November.  
**Status:** Source-based explanation; no new semantic error established.  
**Related:** P5-005 and P5-006.

### Mathematical distinction

A permutation is one bijection. The underlying collection consists of all such bijections. The symmetric group is that collection equipped with composition, identity, inverse, and group laws.

In Lean, an individual permutation is a term `σ : Equiv.Perm X`; `Equiv.Perm X` names the type. The abbreviations `Permutation X` and `SymmetricGroup X` both name this underlying type. They do not identify a single transformation with an entire group.

The definition of the type packages invertible functions, not the external group structure on the type of those functions. Mathlib separately registers the operations and the group instance `Equiv.Perm.permGroup`. Once imported, the relevant instances can be retrieved through either abbreviation.

### Concrete source evidence

| Source | Lines | Role |
|---|---|---|
| [Basics.lean](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L5) | 5 | Imports Mathlib. |
| [Abbreviations](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L97-L103) | 97, 103 | Both names abbreviate `Equiv.Perm X`. |
| [Composition](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L182-L183) | 182–183 | `perm_mul_apply` identifies multiplication as function composition. |
| [Inverse law](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L219-L223) | 220–223 | General inverse laws are applied to permutation elements. |

Instance search supplies the algebraic structures required by the general theorem; no local `inferInstance` example is needed to activate them. General algebraic theorems may require less than the full group structure; describe the precise requirement where relevant rather than assuming every use of multiplication needs all group axioms.

The explicit `example ... : Group (SymmetricGroup X) := inferInstance` occurs in the annotated copy previously inspected. It is **not** in this version of `Permutations/Basics.lean`. Earlier essay wording attributing that example to the comparison file was corrected.

### Limits and significance

Check the operation as well as the type: instance availability does not by itself show correspondence with the textbook. Here `perm_mul_apply` confirms the intended composition order. Naming differences alone are not mathematical errors.

## P5-010 — A cycle construction does not certify the cycle property

**Recorded:** 18 November 2026; consolidates discussions on 15–18 November.  
**Status:** Source observation and independently calculated mathematical example; not yet a Lean-compiled experiment.  
**Scope:** Cycles, lines 983–1113; related counting subsection, lines 1115–1180.

### Construction, property, and counterexample

At [line 1004](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1004), `cyc l` is defined as `l.formPerm` for an arbitrary list with decidable equality. It returns a permutation. It does not require duplicate-free entries or minimum length, and does not return a proof of `IsCycle`.

A permutation is **constructed by** `cyc`; it does not “satisfy the definition cyc.” `IsCycle` is the property it may or may not satisfy.

Mathlib's `List.formPerm` multiplies swaps of consecutive list entries. For the list `[0,1,2,0,3]` on `Fin 4`,

$$
\operatorname{cyc}[0,1,2,0,3]
=(0\,1)(1\,2)(2\,0)(0\,3)
=(1\,2)(0\,3).
$$

It maps 0↔3 and 1↔2, hence has two nontrivial orbits and fails `IsCycle`. Products act right to left.

The repeated 0 would have two proposed successors under the textbook rule, so the distinctness hypothesis is essential to that interpretation. The library's swap-product construction remains well defined.

**Validation:** checked the swap product mathematically and with Python on all four points. A temporary Lean test was started and interrupted without a result. Do not describe this as Lean-verified.

### How the file controls later reasoning

| Source | Lines | Conditions and consequence |
|---|---|---|
| [Empty and singleton cases](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1011-L1018) | 1013–1018 | Both construct the identity. |
| [Certification](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1031-L1034) | 1032–1034 | `l.Nodup` and length at least two imply `(cyc l).IsCycle`. |
| [Outside-list behaviour](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1022-L1024) | 1022–1024 | An element outside the list is fixed; no cycle proof needed. |
| [Recursive identity](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1027-L1029) | 1027–1029 | Decomposes the general construction into a swap and the tail construction. |
| [Support](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1048-L1053) | 1048–1053 | Under distinctness and length assumptions, support equals the listed collection. |
| [Cycle theorem](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1099-L1113) | 1099–1113 | `cycle_eq_transposition` explicitly takes an `IsCycle` proof and support cardinality two. |

At line 1103, `hσ.orderOf` invokes equality between cycle order and support cardinality. The counterexample moves four elements but has order two, showing why that library equality is not available merely from being an output of `cyc`.

Do not claim that `IsCycle` is a logically minimal hypothesis for the *conclusion* that support size two implies a swap. The observation concerns the displayed theorem's interface and its chosen proof's use of a cycle-specific result.

A cycle proof does not finish defining a permutation; it certifies a property of an already defined permutation. `cyc_isCycle` supplies that certificate from suitable list conditions. These cycle proofs are explicit mathematical hypotheses, unlike automatically retrieved group structures.

### Intermediate assumptions — retained in notebook, omitted from essay

The successor formula (1038–1040) and rotation theorem (1058–1060) require duplicate-free lists but no minimum length. Their conclusions hold for singleton lists, whose permutations are identities. This illustrates different levels of generality, but Tiffany requested removal of the paragraph from the essay because it distracted from the main argument. Do not reinsert it without agreement.

### Textbook comparison and design alternatives

The [textbook definition](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/tex/Permutations/Basics.tex#L310-L341) assumes distinct entries and gives successive-image and piecewise descriptions of the **same** definition.

The textbook [explicitly treats the identity as the one-cycle](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/tex/Permutations/Basics.tex#L391-L395) on a nonempty set. Mathlib's `IsCycle` excludes it. Empty-list notation, singleton notation, and the resulting identity permutation should not be conflated with a nontrivial-cycle predicate.

The current broad construction supports uniform identities and direct library reuse. Its naming can obscure the distinction between constructing a permutation and establishing the cycle property. This is an expository/domain issue, not by itself a false theorem.

Two proposed alternatives, neither implemented:
1. A restricted wrapper around `List.formPerm`, requiring distinctness and, for nontrivial cycles, length at least two; return the permutation with its cycle proof.
2. A new construction from the textbook piecewise formula, with inverse laws or bijectivity, a cycle-property proof, and agreement with the library construction for reuse.

Restrictions move proof obligations into the inputs and correctness proofs; they do not eliminate them. State the singleton convention explicitly.

Mathlib's `IsCycleOn` is a broader property on a specified set, with empty and singleton cases; it does **not** require fixing all elements outside that set. Local library inspection found `List.Nodup.isCycleOn_formPerm` without a minimum-length assumption. This alternative was discussed, not implemented in the project.

### Counting theorem — inspected but not the current essay example

At [lines 1124–1133](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1124-L1133), the counted permutations are characterised directly by `σ.IsCycle ∧ σ.support.card = k`. Membership clauses give all and only those permutations; `cyc` is not used to specify the collection.

The comments describe the ordered-list/rotation argument; the actual proof identifies cycle type `{k}` and invokes a library counting theorem at lines 1149–1173. This illustrates result fidelity versus expository fidelity, not a demonstrated mathematical error.

Tiffany preferred `cycle_eq_transposition` as the essay's main example because it explicitly requires a cycle proof. Preserve that scope decision.

## P5-011 — Inspection follow-up and essay working conventions

**Recorded:** 18 November 2026.

### Source scope and representation observations

The earlier review of notation through simple transpositions included:
- Two-line notation chooses a fixed top-row ordering rather than every textbook column ordering.
- Equality theorems show that one-line and two-line lists determine the permutation; reconstruction checks the one-line round trip.
- `transposition i j` accepts equal arguments and then gives the identity; `IsSwap` and the counting theorem impose genuine distinctness where needed.
- `cycleSupport` at lines 1095–1096 accepts any permutation, despite its specialised name.
- The existing cycle-graph lead P5-001 remains a representation change, not a proved downstream error: direction/loops are forgotten, while reachability is related to orbits. No graph repair or compiled counterexample has been produced.

These are inspection observations. No exhaustive review of all of Chapter 5 is claimed.

### Working artifact and editorial preferences

- Master essay: local `/Users/liuaitian/Desktop/MA395/essay.tex`; compiled PDF beside it. It is not a GitHub-published essay as of this record.
- Use XeLaTeX (the document uses `fontspec`), the bundled `lmmono10-regular.otf` code font, and a mathematical font for logical symbols.
- The latest PDF has six pages, after shortening the textbook-construction discussion and adding the textbook's definition.
- Explain unfamiliar Lean notation and mathematical roles for mathematicians new to Lean.
- Use compact source tables with file, line range, context, and any display adaptations.
- Show the full relevant theorem statement before analysis. In the essay only, use `sorry` to omit proofs and say explicitly that the source contains a proof. Such exposition is not a new Lean verification.
- Prefer focused examples and brief construction comparisons. Explain why a theorem needs a property; avoid digressions that need their own explanation.
- Present substantive proposed wording in chat and obtain approval before applying it. A direct instruction to perform a specific edit already authorises that edit.
- Read the current file before editing because Tiffany also edits it directly.

### Source version record

Commit baseline for the inspected fork files: [`8ec0305ea7c8e191c26ce5f51c4a91affdf9f912`](https://github.com/Tiff223/formalisation-algebraic-combinatorics/commit/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912).

| File | Blob SHA |
|---|---|
| `AlgebraicCombinatorics/Permutations/Basics.lean` | `51d68e8b5b0edacc00c3af5a95c035bf09d77ed1` |
| `AlgebraicCombinatorics/tex/Permutations/Basics.tex` | `0982a062b4c7a0f7e6952ca3dac9df1d0a81ac3a` |

These paths are in Tiffany's fork. Do not label this snapshot as a newly checked upstream version. Earlier annotated-copy references use a different path, line numbering, and blob. The local Mathlib files inspected are source evidence; their dependency revision has not been pinned in this update.

### Open work

1. Compile a self-contained Lean counterexample and record the outcome.
2. Decide whether a restricted wrapper would be a useful future experiment; no implementation is authorised merely by discussing the design.
3. Inspect downstream graph uses before judging the impact of P5-001.
4. Keep statement fidelity, proof reuse, naming, and readability as distinct assessment criteria.
5. Update this notebook after substantive research findings and the journal on research days; consolidate rather than duplicate entries.



## P5-012 — Meeting synthesis: generality, representation, and formalisation guidance

**Recorded:** 18 November 2026.  
**Origin:** Tiffany's meeting summary.  
**Status:** Research direction supported by inspected examples; language-mechanism comparisons and prompting recommendations are preliminary, not completed experiments.  
**Related:** P5-001, P5-005, P5-009 and P5-010.

### Meeting objectives

- Include examples of `notation`, `abbrev`, `def`, and optionally `macro` and `infix`.
- Explain which circumstances favour each mechanism and compare advantages, costs and limitations.
- Bring the transposition and directed-graph representation observations into the research synthesis alongside cycles.
- Investigate how general constructions and results are specialised through hypotheses or separate property proofs.
- Plan an essay conclusion giving evidence-based guidance on prompting AI for formalisation.

This records the requested research plan. It does not authorise silently adding unreviewed essay sections or claim that every item has been experimentally evaluated.

### 1. Definitions versus syntax: preliminary comparison and examples

The distinction to investigate is between named mathematical definitions and ways of writing expressions. `def` and `abbrev` introduce named definitions; `abbrev` is reducible, while ordinary `def` is semireducible by default. Their bodies can be unfolded under appropriate transparency settings. Avoid saying that a `def` can never unfold automatically or that `abbrev` is a new mathematical type.

| Mechanism | Example to study | When useful | Advantages | Costs and limitations |
|---|---|---|---|---|
| `def` | The project's `cyc` or `oneLineNotation` | Give a function or construction a reusable name | A named declaration with a type; convenient target for lemmas | A name does not guarantee an intended property; unfolding behaviour matters in automation |
| `abbrev` | `Permutation X := Equiv.Perm X` | A transparent alternative name for an existing expression | Existing results and instances remain accessible through the alias | No new object kind or extra mathematical guarantees; weaker abstraction boundary |
| `notation` | The project's `scoped notation "s[" i "]" => simpleTransposition i` | Match a mathematical writing convention | Makes formulas familiar; scoped notation helps manage ambiguity | Does not itself add a certified property; scope, parsing and display may hide the underlying expression |
| `infix` / `infixl` / `infixr` | A small illustrative binary-operator notation for an existing function | Operator-shaped notation with chosen precedence/associativity | Concise expressions and controlled parsing | Associativity of parsing is not a proof of mathematical associativity; conflicting symbols or precedence can confuse |
| `macro` | A small syntax abbreviation expanding into an existing term | Syntax patterns needing translation beyond a simple named alias | Flexible, reusable syntax expansion | Expansion must still elaborate and type-check; introduces syntax/debugging complexity, not a proof of the expansion's intended meaning |

**Source examples in the fork:** [`abbrev Permutation`, line 97](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L97); [scoped simple-transposition notation, line 781](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L781); [`def cyc`, line 1004](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1004).

Illustrative comparison examples below are proposed for a small separate experiment. They are **not** quoted from the repository and have **not** been compiled in this update:

```lean
def identityMap (X : Type*) : X → X := fun x => x

abbrev PermAlias (X : Type*) := Equiv.Perm X

local notation "P[" X "]" => Equiv.Perm X

local infixl:65 " +++ " => Nat.add

macro "twiceNat " t:term : term => `(Nat.add $t $t)
```

Read these as: define an identity function; introduce a transparent permutation-type alias; give the permutation type a local spelling; write an existing addition function using a binary operator; expand a syntax form into addition of the same expression twice. The functions chosen are intentionally simple so syntax and unfolding can be investigated separately from new mathematics.

**Planned checks:** inspect elaborated expressions and inferred types; try instance retrieval for aliases; compare rewriting/unfolding; test local/scoped availability and ambiguous parses; examine macro expansion and error messages. These examples alone do not establish performance differences.

**Official documentation consulted 18 November:**
- [Definitions and abbreviations](https://lean-lang.org/doc/reference/latest/Definitions/Definitions/).
- [Notation and macro overview](https://lean-lang.org/doc/reference/latest/Notations-and-Macros/).
- [Custom operators](https://lean-lang.org/doc/reference/latest/Notations-and-Macros/Custom-Operators/).
- [Macros](https://lean-lang.org/doc/reference/latest/Notations-and-Macros/Macros/).

These are current manual references; check compatibility with the project's pinned Lean version before testing examples. This comparison refines the simplified earlier learning-note table without erasing the historical note.

### 2. Transpositions: a genuine extension of the allowed inputs

At [line 600](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L600), `transposition i j` abbreviates `Equiv.swap i j` without requiring `i ≠ j`. When the arguments are equal, the output is the identity.

The identities for exchanging the arguments, inversion and squaring (lines 620–633) remain valid in that case. Thus these statements cover more inputs than the textbook's definition of a genuine transposition.

This supports the observation that some boundary cases can be included uniformly. It does **not** support omitting distinctness from every transposition result: support-cardinality and nontriviality claims must distinguish the equal-input case. The counting theorem uses `IsSwap`, rather than counting every constructed swap expression as a distinct transposition.

**Essay task:** show the textbook assumption, the broader formal construction, and a theorem whose conclusion survives the added boundary case. Explain where genuine transposition conditions reappear.

### 3. Directed cycle graphs: preservation of a property after forgetting information

At [lines 482–488](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L482-L488), `cycleDigraph` is an undirected loopless `SimpleGraph`, despite the textbook's directed arcs and fixed-point loops.

At [lines 510–511](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L510-L511), `cycleDigraph_connected_iff` equates graph reachability with membership in the same permutation orbit, expressed by an integer power.

Removing direction and self-loops preserves the relevant orbit partition. It loses information about orientation and cannot distinguish a three-cycle from its inverse.

**Qualification to the meeting summary:** a theorem on the simplified graph is not automatically a theorem about every notion of directed connectivity. If the desired directed statement concerns **weak** components, the relation to the underlying undirected graph is the needed bridge. For the finite permutation graph, **directed** reachability also runs around each finite cycle, so its strongly connected components agree with the orbits. This is a mathematical explanation, not a newly completed Lean bridge proof. Arbitrary directed graphs need not have this property.

This is best classified as a representation reduction preserving a selected invariant, rather than a simple “more general theorem implies the specific theorem” argument. A formal result about the directed representation needs that representation and the transfer stated explicitly.

**Essay task:** distinguish the represented graph, the property retained, and the correspondence needed to recover the intended directed claim. Do not suggest that the entire directed graph has been faithfully encoded by the simple graph.

### 4. Cycles: general construction and explicit certification

At line 1004, `cyc` returns a permutation for any input list. P5-010's repeated-entry example produces two disjoint transpositions and fails `IsCycle`.

The theorem at lines 1032–1034 certifies `IsCycle` for distinct entries and length at least two. The later theorem at lines 1099–1100 explicitly takes a cycle proof; its chosen proof uses that hypothesis at line 1103.

The artifact therefore separates construction from property proof. Describe this as an observable feature of the source, not evidence about what the AI “realised.” We have not reconstructed generation traces or established the intent of the producing agent.

Construction identities need not first establish nontriviality. Cycle-specific theorems need the appropriate property proof, obtained from input conditions or other evidence. This remains the main cycle-section explanation; do not restore the removed intermediate-assumptions paragraph merely because the research notebook records the nuance.

### 5. Working synthesis and limits of the claim about AI

A useful working theme is **general constructions with explicit conditions for their intended interpretations**. The three examples are not identical:

| Case | What broadens or changes | What must be checked |
|---|---|---|
| Swaps | Input domain admits equal arguments | Which conclusions survive the identity case, and where distinctness is required |
| Cycle graph | Representation forgets orientation and loops | Which invariants survive and how the simplified result transfers |
| Cycles | List construction returns arbitrary permutation shapes | Conditions and proofs ensuring a single nontrivial cycle |

These cases motivate the hypothesis that the inspected formalisation favours reusable library constructions and facts that handle boundary cases uniformly. They do not establish a statistical tendency of AI systems, a universal strategy, or a semantic error. Compare with the paper's stated aims and, if claiming a general tendency, collect further cases and generation evidence.

### 6. Planned concluding guidance for AI-assisted formalisation

The eventual essay can turn these cases into practical prompting guidance. The following is a **draft agenda**, not a tested prompting intervention:

1. State the intended audience and purpose: textbook exposition, reusable library development, statement translation, or a combination.
2. Supply the source definition, all assumptions and boundary conventions, including distinctness, empty/singleton cases, indexing and allowed sizes.
3. Ask the AI to distinguish mathematical definitions from aliases and syntax, and explain the choice of `def`, `abbrev`, notation or macros.
4. If a construction is more general than the source, request an explicit explanation of the additional inputs, a source-compatible interface or theorem, and evidence connecting them.
5. Require the intended properties explicitly in theorem hypotheses or certified outputs; do not rely on descriptive names.
6. For representation changes, specify what information may be forgotten, what must be preserved, and what bridge theorem links the representations.
7. Ask for the exact intended theorem statement before its proof, including the action of a specified map where relevant.
8. Permit library reuse while requiring identification of imported constructions, preconditions, and whether the textbook argument remains visible.
9. Request small counterexamples and boundary checks, plus actual Lean compilation of the final code, with sources and version information.
10. Label explanation-only examples and proof placeholders; distinguish accepted code from source fidelity and from experiments not yet run.

**Possible prompt fragment for later refinement:**

> Formalise the supplied definition and theorem for a reader who knows the mathematics but is new to Lean. First state the intended objects, assumptions and boundary cases. If you reuse a more general library construction or change the representation, explain the difference, specify the conditions needed for the textbook interpretation, and state the connecting result. Use existing library proofs where appropriate, identify them, and keep the mathematical statement explicit. Explain naming and notation choices. Show the complete theorem statement before proving it, then compile the final code and report the actual checks performed.

Before putting this guidance in the essay, select concise recommendations tied to our examples and make clear that their effectiveness has not yet been measured.

### Immediate follow-up

- Create a minimal, version-pinned comparison file for the five language mechanisms and compile it.
- Prepare a focused transposition passage and graph passage with full source-labelled theorem statements.
- State the graph correspondence precisely before claiming a directed theorem has been recovered.
- Keep the current local essay unchanged until substantive proposed wording is approved.
- Test the proposed prompting guidance only if adopted as an experiment; preserve prompts, outputs and evaluation criteria.


## Next reading session — historical plan from 3 November

The current follow-up tasks are recorded in P5-011 above; the earlier plan is retained below as history.

- On 4 November, revisit two-line notation, one-line notation and the cycle digraph in detail, comparing each with the textbook.
- Check indexing, retained information and small examples; revisit P5-001 as an open lead.
- Evaluate the combined statement of Proposition 5.1.3 before spending time on its proof.
- Check the paper's stated purpose before adopting evaluation criteria for the essay.
- Record compilation or source-publication checks only when performed.

## Reusable finding record

### Finding ID — Short title

**Date:**

**Textbook section / definition / theorem:**

**Lean file and declaration:**

**Repository commit or other version evidence:**

**Textbook meaning:**

**Lean meaning and hypotheses:**

**Agreement or difference:**

**Small example:**

**Evidence status and tests performed:**

**Possible significance:**

**Remaining questions and next action:**

## Sources and version record

### Textbook

Darij Grinberg, *An Introduction to Algebraic Combinatorics*.

[Read the textbook](https://arxiv.org/pdf/2506.00738)

### Original Lean file

[Upstream Permutations/Basics.lean](https://github.com/facebookresearch/algebraic-combinatorics/blob/main/AlgebraicCombinatorics/Permutations/Basics.lean)

### Corresponding repository TeX

[Upstream tex/Permutations/Basics.tex](https://github.com/facebookresearch/algebraic-combinatorics/blob/main/AlgebraicCombinatorics/tex/Permutations/Basics.tex)

### Source inspection — 26 October 2026

**Lean file blob SHA:**

```text
59de10cf1249f982be44ac4e17768e38cf4510b9
```

**TeX file blob SHA:**

```text
0982a062b4c7a0f7e6952ca3dac9df1d0a81ac3a
```

These identify file contents, not a repository commit.

The main-branch links can change. Capture a commit permalink before citing this analysis in the essay.

### Related documents

- [Research journal](journal.md)
- [2026–2028 Mathematics Research & PhD Application Timeline](https://docs.google.com/document/d/1r4yN4jOON0d08nAcOmCthaBc9y8rD0ZH0N2gTO8XUsU/edit)
- [Earlier research notes — Two Coherence Failures](https://docs.google.com/document/d/1gVgsUDOLMvUlcc02AGaF4GSMI-gJ5MCndCk_M9tr2lg/edit)

</details>
