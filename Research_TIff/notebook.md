# MA395 Research Notebook

**Topic:** Permutations and autoformalisation  
**Supervisor:** Christian Ikenmeyer  
**Established:** 26 October 2026  
**Last updated:** 28 October 2026

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

## Next reading session

- Publication of today's revised conjugation annotation is confirmed; record compilation results next.
- Compile the edited module in the project environment.
- Compare the explicit construction in P5-007 with the library construction, checking both the formula and proof obligations.
- Keep a pinned upstream baseline.
- Decide how to avoid importing duplicate declarations.
- Resume at the permutation-notations section (line 493 in the 28 October version) at Tiffany’s pace.
- Continue distinguishing explanatory improvements from semantic errors.

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
