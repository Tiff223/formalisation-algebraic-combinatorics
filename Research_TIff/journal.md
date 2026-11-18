# MA395 Research Journal

**Supervisor:** Christian Ikenmeyer  
**Last updated:** 18 November 2026

This journal records daily progress, decisions and next steps.

The [research notebook](notebook.md) contains detailed observations, mathematical examples, source references and open questions.

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
