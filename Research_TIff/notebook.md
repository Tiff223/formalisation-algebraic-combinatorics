# MA395 Research Notebook — Current Essay Material

**Topic:** Representing textbook permutations in Lean  
**Supervisor:** Christian Ikenmeyer  
**Last updated:** 18 November 2026  
**Audience:** Mathematicians familiar with sets, functions and groups, but new to Lean.

This is the working reference for the **current final-essay plan**. It contains present conclusions, supporting examples, source locations, and clearly marked sections still to develop. It follows writing order, not discovery order.

The [research journal](journal.md) records the development of the ideas, superseded interpretations, unused drafts and editorial decisions. Historical material is not an additional list of current essay claims.

## Essay argument and writing map

**Central question:** How do the choices made when formalising textbook mathematics affect the representation, assumptions and interpretation of the resulting Lean statements?

**Working argument:** The examples distinguish transparent names for the same objects, broader constructions with explicit conditions for their textbook interpretation, and a graph simplification preserving a selected property. Evaluate definitions, hypotheses and connecting theorems, rather than names alone.

| Order | Topic | What to explain | Current position |
|---|---|---|---|
| 1 | [Permutations and symmetric groups](#1-permutations-and-symmetric-groups-a-shared-underlying-type) | Shared underlying type and retrieval of group structure | Developed; in local essay |
| 2 | [Definitions and notation](#2-choosing-def-abbrev-notation-infix-or-macro) | When to use def, abbrev, notation, infix and macro; benefits and limits | Planned expansion; examples need compilation |
| 3 | [Transpositions](#3-transpositions-generalising-the-input-domain) | Which textbook restriction can be omitted while some results remain true | Developed; in local essay |
| 4 | [Cycle graphs](#4-cycle-graphs-preserving-orbits-after-forgetting-information) | What is lost, what survives, and how the directed formulation is connected | Developed; in local essay |
| 5 | [Cycles](#5-cycles-construction-and-certification) | General construction versus proof of the intended property | Developed; in local essay |
| 6 | [Synthesis](#6-synthesis-what-the-examples-support) | Distinguish generalisation, representation reduction and certification | Current interpretation; conclusion to draft |
| 7 | [Prompting guidance](#7-practical-guidance-for-ai-assisted-formalisation) | Practical recommendations tied to the examples | Planned ending; effectiveness not tested |

“Developed” means explained for the essay, not newly verified by a Lean run. Verification is recorded separately below.

## Sources and evidence

All project lines refer to the fork snapshot at commit [8ec0305ea7c8e191c26ce5f51c4a91affdf9f912](https://github.com/Tiff223/formalisation-algebraic-combinatorics/commit/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912).

| Short name | Exact path | Blob SHA |
|---|---|---|
| Basics.lean | AlgebraicCombinatorics/Permutations/Basics.lean | 51d68e8b5b0edacc00c3af5a95c035bf09d77ed1 |
| Basics.tex | AlgebraicCombinatorics/tex/Permutations/Basics.tex | 0982a062b4c7a0f7e6952ca3dac9df1d0a81ac3a |

These are files in Tiffany's fork. The annotated Permutaions_Tiff copy has different lines and is not the reference for the quotations below.

| Evidence | What has actually been done |
|---|---|
| Fork Lean and textbook TeX sources | Inspected and compared |
| Repeated-entry cycle counterexample | Calculated mathematically; adjacent-swap product evaluated in Python on every input |
| Standalone Lean check of the counterexample | Started, then interrupted without a result: **not Lean-verified** |
| Local essay | XeLaTeX compilation and page inspection; artifact validation, not new Lean proof verification |
| Proposed language examples and prompt guidance | Not compiled or experimentally evaluated |
| Group instance and selected permutation laws | Standalone Lean 4.28.0 check passed. See section 1 for scope and Mathlib revision. |
| Directed/simple-graph correspondence | Explained mathematically; no newly compiled bridge theorem |
| Restricted cycle wrapper | Proposed design; not implemented |

Theorems displayed with **sorry** have complete statements but proofs omitted for exposition. The source supplies proofs. These displays are not claims of completed new Lean verification.

## 1. Permutations and symmetric groups: a shared underlying type

### Claim

Permutation X and SymmetricGroup X name the same type of permutation elements. The group interpretation additionally uses Mathlib's registered operations and laws. An individual permutation remains an element, not a group.

### Mathematical explanation

| Role | Familiar mathematics | Lean representation |
|---|---|---|
| Individual permutation | A bijection σ:X→X | A term σ : Equiv.Perm X |
| Underlying collection | All bijections X→X | The type Equiv.Perm X |
| Group structure | Composition, identity, inverse and laws | The registered group structure on that type |

A type specifies the kind of objects under consideration. A term is an object of that type. Typing is distinct from set membership, although these presentations have corresponding roles.

An element of Equiv.Perm X records a function, an inverse and inverse laws. The group structure **on the type of those equivalences** is supplied separately.

### Source evidence

| Source | Context |
|---|---|
| [Basics.lean, 97 and 103](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L97-L103) | Two abbreviations |
| [Basics.lean, 5](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L5) | Imports Mathlib |
| [Basics.lean, 182–183](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L182-L183) | Multiplication is composition |
| [Basics.lean, 220](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L219-L223) | A general inverse law applied to a permutation |

~~~lean
abbrev Permutation (X : Type*) := Equiv.Perm X
abbrev SymmetricGroup (X : Type*) := Equiv.Perm X
~~~

Complete inverse-law statement; variable renamed, inverse written as Inv.inv a, proof omitted:

~~~lean
theorem perm_mul_inv {X : Type*} (a : Equiv.Perm X) :
    a * Inv.inv a = 1 := by
  sorry
~~~

### Where the structure is requested

The file explicitly asks Lean to supply the group structure at line 137. [Basics.lean, lines 136–137](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L136-L137)

~~~lean
example {X : Type*} : Group (Equiv.Perm X) := inferInstance
~~~

The type after the colon describes what Lean must supply. The imported Mathlib instance `Equiv.Perm.permGroup` gives composition, the identity, inversion and the laws. Either abbreviation unfolds to `Equiv.Perm X`, so a request for `Group (SymmetricGroup X)` can use the same instance. This example checks availability. Lean makes independent instance requests when elaborating later expressions and theorem applications. [Mathlib instance definitions](https://github.com/leanprover-community/mathlib4/blob/8f9d9cff6bd728b17a24e163c9402775d9e6a365/Mathlib/Algebra/Group/End.lean#L66-L81) · [Lean reference on instance synthesis](https://lean-lang.org/doc/reference/latest/Type-Classes/Instance-Synthesis/)

### An operation and its laws make different demands

| Example | What Lean uses | Source |
|---|---|---|
| Composition at a point, `(α * β) x = α (β x)` | The definition of permutation multiplication. `rfl` checks that both sides agree after unfolding. The right-hand permutation acts first. | [182–183](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L182-L183) |
| Associativity, `mul_assoc α β γ` | An instance of `Semigroup`, which supplies associative multiplication. Lean obtains it from the permutation group instance. | [186–187](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L186-L187) |
| Identity laws, `one_mul α` and `mul_one α` | An instance of `MulOneClass`, which supplies multiplication, the identity and the two identity laws. | [190–193](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L190-L193) |
| Inverse law, `mul_inv_cancel α` | An instance of `Group`. Lean infers the type from `α` and supplies the registered permutation group. | [219–223](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L219-L223) |

Using the same two permutations in a composition formula and an algebraic argument is legitimate because they already belong to a collection with established laws under that operation. The ability to compose maps alone is insufficient. All functions from a set to itself can be composed and satisfy associativity and the identity laws, but a constant map on a two-element set has no inverse. For a permutation, the pointwise inverse identity can also be obtained directly from its inverse laws. The file chooses to reuse the general group theorem for the identity of permutations.

### Proposition 5.1.3 checks compatibility with multiplication

For a bijection `f : X ≃ Y`, the file uses the ordinary equivalence `f.permCongr` to exhibit the transported permutation on `Y`. The main construction at lines 248–249 uses `f.permCongrHom`, whose result type uses `≃*`. It gives a bijection of the two types of permutations together with a proof that the map preserves their multiplication. The notation `≃*` requires multiplication structures. With the known group structures on these types, the result is a group isomorphism. The preservation claim at lines 275–277 uses the already supplied proof via `.map_mul`. When `X = Y` and `f` is itself a permutation, lines 297–300 express the same map as the group product `f * σ * f⁻¹`. [Construction](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L248-L261) · [Multiplication preservation](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L274-L277) · [Same-type case](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L295-L300) · [Mathlib construction and its preservation proof](https://github.com/leanprover-community/mathlib4/blob/8f9d9cff6bd728b17a24e163c9402775d9e6a365/Mathlib/Algebra/Group/End.lean#L290-L297)

**Verification.** A standalone check with Lean 4.28.0 and the local Mathlib checkout at `8f9d9cff6bd728b17a24e163c9402775d9e6a365` compiled successfully. It inspected the signatures of `mul_assoc` and `mul_inv_cancel`, synthesised the group through both names, and synthesised `Equiv.Perm.permGroup.toSemigroup` for the associativity case. It also checked the composition equation, the whole-permutation and pointwise inverse identities, and preservation of multiplication by `permCongrHom`. This verification covers the standalone examples.

### Paragraph sequence to write

1. Pose the puzzle using the two abbreviations.
2. Distinguish an element, its collection and the group structure.
3. Explain terms, types and equivalences.
4. Show the explicit `inferInstance` example at line 137 and explain the meaning of its requested type.
5. Contrast computation by unfolding with use of algebraic laws. Use the inverse law as the main example and Proposition 5.1.3 as a short follow-up about preserving multiplication.
6. Conclude why shared naming preserves the distinctions.

**Limit:** availability of a structure alone does not establish that its operations match the textbook. Here the composition formula supplies the intended connection.

## 2. Choosing def, abbrev, notation, infix or macro

**Purpose:** Add a concise comparison to explain what a naming or notation choice does and does not change. This is planned essay material, with examples still to test.

| Mechanism | When useful | Advantage | Cost or limitation |
|---|---|---|---|
| def | Name a function or construction, e.g. cyc | Reusable declaration with a type and associated lemmas | The name guarantees no extra property; unfolding behaviour matters |
| abbrev | A transparent alternative name, e.g. Permutation | Existing results/instances are accessible through unfolding | No new mathematical kind or stronger guarantee; weaker abstraction boundary |
| notation | A familiar way to write an expression | Matches textbook formulas; local/scoped control | Can hide the expression; scope and ambiguity need care |
| infix / infixl / infixr | Operator notation for a binary operation | Concise formulas with explicit parsing conventions | Parsing associativity is not a proof of mathematical associativity |
| macro | Translate a syntax pattern into other syntax | Flexible syntactic abstraction | Expansion must elaborate and type-check; extra syntax/debugging complexity |

Ordinary def is semireducible by default; abbrev is reducible. Both can unfold under appropriate conditions. Avoid an absolute claim that def cannot unfold automatically.

### Project examples

| Source | Example |
|---|---|
| [Basics.lean, 97](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L97) | abbrev Permutation |
| [Basics.lean, 1004](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1004) | def cyc |
| [Basics.lean, 781](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L781) | Simple-transposition notation |

~~~lean
scoped notation "s[" i "]" => simpleTransposition i
~~~

The notation gives an existing construction a spelling; it does not construct a different mathematical object or prove its properties.

**Present evaluation:** textbook-style names can help textbook readers; standard library names can help Lean users recognise and reuse objects. Choose by audience and explain the correspondence.

### Illustrative experiments to prepare

These are drafts, not source quotations and not compiled examples:

~~~lean
def identityMap (X : Type*) : X → X := fun x => x
abbrev PermAlias (X : Type*) := Equiv.Perm X
local notation "P[" X "]" => Equiv.Perm X
local infixl:65 " +++ " => Nat.add
macro "twiceNat " t:term : term => `(Nat.add $t $t)
~~~

They respectively name an identity function, alias the permutation type, provide local notation, introduce an addition operator and expand syntax to addition of an expression twice.

**Before final drafting:** compile against the project's pinned toolchain; inspect types, expansions, instance retrieval, scope and parsing; retain only examples serving the essay. No performance comparison is established.

**References:** [Definitions](https://lean-lang.org/doc/reference/latest/Definitions/Definitions/), [notation/macros](https://lean-lang.org/doc/reference/latest/Notations-and-Macros/), [operators](https://lean-lang.org/doc/reference/latest/Notations-and-Macros/Custom-Operators/), [macros](https://lean-lang.org/doc/reference/latest/Notations-and-Macros/Macros/).

## 3. Transpositions: generalising the input domain

### Claim

The formal swap construction accepts equal arguments, unlike the textbook's definition of a genuine transposition. Some identities remain valid on that broader domain.

| Source | Context |
|---|---|
| [Basics.lean, 600](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L600) | Abbreviation |
| [Basics.lean, 620–633](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L620-L633) | Symmetry, inversion and squaring |

~~~lean
abbrev transposition {X : Type*} [DecidableEq X]
    (i j : X) : Equiv.Perm X := Equiv.swap i j
~~~

DecidableEq supplies equality decisions. There is no hypothesis requiring i ≠ j.

Complete selected statement, proof omitted:

~~~lean
theorem transposition_sq_eq_one {X : Type*} [DecidableEq X]
    (i j : X) :
    transposition i j * transposition i j = 1 := by
  sorry
~~~

When i=j, the construction returns the identity and the theorem remains true. For distinct inputs it gives the usual transposition identity.

### Interpretation and paragraph plan

1. Give the textbook distinctness assumption.
2. Display the broader construction and full identity theorem.
3. Evaluate equal inputs.
4. Explain uniform treatment of that boundary case.
5. Identify conditions still needed for genuine-transposition results.

Support size two and nontriviality require distinct inputs. The counting theorem uses IsSwap, excluding the equal-input identity. Do not infer that every transposition theorem can omit distinctness.

**Evidence:** source interpretation and elementary mathematical check; no new compiled experiment. This is a broader domain, not an established false theorem.

## 4. Cycle graphs: preserving orbits after forgetting information

### Claim

The formal graph is an undirected loopless representation, not the complete textbook directed graph. It retains the orbit components needed by a particular theorem.

| Textbook | Formal graph |
|---|---|
| Arrows i→σ(i), including fixed-point loops | Undirected edges between distinct i,j when σ(i)=j or σ(j)=i |
| Keeps orientation | Forgets orientation |
| Shows fixed-point loops | Retains fixed vertices without loops |

| Source | Context |
|---|---|
| [Basics.lean, 482–488](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L482-L488) | SimpleGraph construction |
| [Basics.lean, 510–511](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L510-L511) | Reachability–orbit theorem |

Adjacency, meaning an undirected edge, is defined by:

~~~lean
i ≠ j ∧ (σ i = j ∨ σ j = i)
~~~

The symbols ∧ and ∨ mean “and” and “or”. Distinctness removes loops.

Complete theorem statement, proof omitted:

~~~lean
theorem cycleDigraph_connected_iff {n : ℕ}
    (σ : Sn n) (i j : Fin n) :
    (cycleDigraph σ).Reachable i j ↔
      ∃ k : ℤ, (σ ^ k) i = j := by
  sorry
~~~

Reachable means connected by a path, including length zero. Integer powers allow forward and inverse applications. An orbit consists of elements related by these applications.

### Examples

- The identity's directed graph has a loop at every vertex; its simple graph has no edges but retains singleton components.
- (0 1 2) and (0 2 1) have opposite directions but the same undirected triangle.

The simple graph does not determine the original permutation. It nevertheless retains its partition into orbits.

### Transfer to a directed statement

For **weak connectivity**, compare the directed graph's underlying undirected graph with the simplification; deleting loops does not affect components.

For **directed reachability** in the finite permutation graph, every orbit is a finite directed cycle. Forward paths can run around that cycle, so strong components also match orbits. This uses the finite-permutation setting, not an arbitrary directed graph.

A Lean theorem about the directed representation still needs that representation and the relevant correspondence. No new bridge theorem has been compiled here.

### Paragraph sequence

1. Explain the representation change.
2. Give examples showing what is lost.
3. Display the orbit theorem and explain what survives.
4. State the directed correspondence needed.
5. Assess adequacy for this property rather than equivalence of complete graph representations.

**Evidence:** source comparison and mathematical examples. Downstream uses and a compiled bridge remain to be investigated.

## 5. Cycles: construction and certification

### Claim

The construction cyc determines a permutation but does not guarantee a single nontrivial cycle. Separate conditions certify that property, which later theorems can explicitly require.

### 5.1 Construction and counterexample

| Source | Context |
|---|---|
| [Basics.lean, 1004](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1004) | General list construction |

~~~lean
def cyc {X : Type*} [DecidableEq X]
    (l : List X) : Equiv.Perm X := l.formPerm
~~~

List X is an ordered finite list. The definition neither requires distinct entries nor imposes a minimum length.

On X={0,1,2,3},

$$
\operatorname{cyc}[0,1,2,0,3]
=(0\,1)(1\,2)(2\,0)(0\,3)
=(1\,2)(0\,3).
$$

Mathlib's formPerm multiplies consecutive-entry swaps, acting right to left. The output sends 0↔3 and 1↔2, so it has two nontrivial cycles. Repeated 0 has conflicting proposed successors 1 and 3 under the textbook rule, but the swap-product construction is well defined.

**Evidence:** mathematical calculation plus Python evaluation on all four inputs. Not a quoted project theorem or a completed Lean test.

### 5.2 Advantages and costs

**Advantages:** direct Mathlib reuse; construction before list proofs; uniform empty/singleton cases; identities applicable to lists whose outputs are not single cycles.

**Costs:** the name can suggest guarantees absent from the type. Readers must identify the hypotheses that recover the textbook meaning. Lean checks formal proof requirements, not whether a name or comment communicates them accurately.

A permutation is **constructed by** cyc. IsCycle is a **predicate**, a property that may be asserted and proved of the permutation.

### 5.3 A theorem not requiring a cycle proof

| Source | Context |
|---|---|
| [Basics.lean, 1022–1024](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1022-L1024) | Outside-list elements are fixed |

Complete statement, proof omitted:

~~~lean
theorem cyc_apply_of_not_mem {X : Type*} [DecidableEq X]
    {l : List X} {x : X} (h : x ∉ l) :
    cyc l x = x := by
  sorry
~~~

The proof h says that x is outside the list. All construction swaps use listed elements, so x is fixed even when the output has several cycles. No IsCycle proof is needed.

### 5.4 Certification and a theorem requiring it

| Source | Context |
|---|---|
| [Basics.lean, 1032–1034](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1032-L1034) | Certifies the construction under list conditions |
| [Basics.lean, 1099–1113](https://github.com/Tiff223/formalisation-algebraic-combinatorics/blob/8ec0305ea7c8e191c26ce5f51c4a91affdf9f912/AlgebraicCombinatorics/Permutations/Basics.lean#L1099-L1113) | Later theorem takes a cycle proof |

Complete statements, proofs omitted; variables in the second statement renamed:

~~~lean
theorem cyc_isCycle {X : Type*} [DecidableEq X]
    {l : List X} (hl : l.Nodup) (hn : 2 ≤ l.length) :
    (cyc l).IsCycle := by
  sorry

theorem cycle_eq_transposition {X : Type*}
    [DecidableEq X] [Fintype X] {a : Equiv.Perm X}
    (h : a.IsCycle) (hcard : a.support.card = 2) :
    ∃ i j : X, i ≠ j ∧ a = Equiv.swap i j := by
  sorry
~~~

Nodup means “no duplicates”. The proofs hl and hn establish distinctness and minimum length. Fintype supplies a finite enumeration. The support is the collection of moved elements.

The second theorem receives a permutation, its cycle proof h, and proof hcard that it moves exactly two elements. Its conclusion identifies a swap of distinct elements.

At line 1103, the source uses hσ.orderOf: a nontrivial cycle's order equals the size of its support. Order is the least positive number of repetitions giving the identity, when such a number exists. The counterexample above moves four elements but has order two; being an output of cyc alone cannot justify that equality.

This explains a cycle-specific step in the selected proof. It does not claim that IsCycle is a logically minimal assumption for every proof that a support-two permutation is a swap.

### 5.5 What must be supplied

1. Supply a list of distinct entries with length at least two.
2. Prove those conditions.
3. Apply cyc_isCycle to obtain the property proof.
4. Supply it to results that require a nontrivial cycle.

The permutation was already fully defined by cyc. Certification establishes a property; it does not complete the definition. These are explicit mathematical hypotheses, unlike automatically retrieved group instances.

### 5.6 Textbook definition and brief alternatives

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

### Paragraph sequence

1. General construction and repeated-entry counterexample.
2. Advantages and costs.
3. A property of all constructed permutations versus a cycle-specific result.
4. Full certification/later statements and explanations of proof parameters.
5. Brief textbook definition, alternative interface and singleton convention.

## 6. Synthesis: what the examples support

The present conclusion distinguishes four choices:

| Case | Choice | Evaluation question |
|---|---|---|
| Permutation/group names | Transparent aliases of one type | Are element/type/structure roles and operations clear? |
| Swaps | Broader input domain | Which claims survive equal inputs, and where is distinctness needed? |
| Graphs | Simpler representation | Which information is lost, which property survives, and what bridge is needed? |
| Cycles | Construction separated from certification | Which conditions establish the intended property, and where is it used? |

These are local source-based findings. A general AI tendency toward greater generality is a hypothesis, not a statistical result. Generation traces have not been examined to establish an agent's reasoning.

Distinguish **semantic fidelity**, preserving mathematical meaning, from **expository fidelity**, following the textbook presentation. Library reuse can establish a result without displaying its argument locally. Compare with the project's stated purpose; the paper's objectives still need focused review.

### What the essay may conclude

- Names, notation and comments do not certify mathematical properties.
- Correctness of a formal proof and fidelity of its statement to the source are separate evaluations.
- Generality, representation changes and mathematical errors are distinct categories.
- Greater local proof detail alone does not imply greater fidelity.
- Broad constructions and restricted interfaces serve different purposes and audiences.

## 7. Practical guidance for AI-assisted formalisation

**Purpose:** Finish with concise recommendations tied to the cases. These are proposed practices, not tested prompt-improvement results.

| Ask the AI to specify | Why |
|---|---|
| Audience and intended purpose | Textbook exposition and library reuse may favour different interfaces |
| Source assumptions and boundary conventions | Distinctness and singleton cases affect meaning |
| Why def, abbrev or notation is chosen | Naming/syntax and certified properties play different roles |
| Broader domains or changed representations | Explain swap edge cases and discarded graph information |
| Required property proofs or certified outputs | A name cannot supply IsCycle |
| A bridge for representation changes | Recover the intended graph statement precisely |
| The complete intended statement before its proof | Assess translation independently of proof completion |
| Imported constructions and their hypotheses | Make reuse and remaining obligations visible |
| Boundary examples, compilation and source versions | Make the evidence reproducible |

### Draft prompt fragment

> Formalise the supplied definition and theorem for a reader who knows the mathematics but is new to Lean. First state the intended objects, assumptions and boundary cases. If you reuse a broader library construction or change representation, explain the difference and state the conditions or correspondence needed for the textbook interpretation. Identify imported results, explain naming and notation choices, and show the complete theorem statement before proving it. Test small boundary cases, compile the final code, and report only checks actually completed.

Refine the final recommendations after the language examples and graph passage are developed. Measuring prompt effectiveness would be a separate experiment requiring recorded prompts, outputs and criteria.

## Final-essay preparation checklist

- [ ] Compile the repeated-entry counterexample as a standalone Lean example.
- [ ] Compile and compare language examples against the pinned toolchain.
- [x] Draft source-labelled transposition and graph passages.
- [ ] Specify the directed-connectivity bridge; compile if implemented.
- [ ] Compare the analysis with the paper's stated objectives.
- [ ] Keep full relevant theorem statements before explanations.
- [ ] Keep construction alternatives brief.
- [ ] Finalise guidance without implying unperformed experiments.
- [ ] Verify cited lines against the pinned version before submission.

**Working artifact:** /Users/liuaitian/Desktop/MA395/essay.tex and essay.pdf. The current compiled draft has seven pages and includes the shared-type, transposition, graph and cycle observations. They are not published to GitHub by this notebook update.

**Writing conventions:** explain Lean notation for beginners; use compact file/line/context tables; label adapted code and omitted proofs. Show substantive proposed essay wording for approval before editing; a direct requested edit is already authorised.

**Maintenance rule:** keep only current essay material and its necessary evidence here. Put revised beliefs, unused drafts and deferred investigations in the journal. Planned essay sections stay here with clear status labels; unadopted leads do not.
