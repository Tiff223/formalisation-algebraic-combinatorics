# MA395 Research Journal

**Supervisor:** Christian Ikenmeyer  
**Last updated:** 28 October 2026

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

Tiffany reported further edits to the Lean file today. The supplied link returned blob `34b391a01fad9094bf8eb23e735377e2d7e07407`, unchanged from the previously reviewed version. The older conjugation annotation and existence-statement comment are still present in that retrieved version.

The revised wording is therefore recorded as prepared in discussion, with publication of the latest Lean edits not yet verified. No new compilation or proof implementation was verified today.

### Next steps

1. Save and commit the revised Lean annotations, then confirm that GitHub shows the intended version.
2. Compile the edited module and record the result.
3. Continue after the conjugation section at the student's pace.
4. Keep statement fidelity, proof reuse and readability distinct in the essay analysis.
