# MA395 — Evaluating Autoformalisation in Algebraic Combinatorics

This repository contains my annotated copy of the Lean formalisation of Darij Grinberg’s *An Introduction to Algebraic Combinatorics*.

It supports my third-year mathematics essay at the University of Warwick, supervised by Christian Ikenmeyer.

## Research aim

The project examines how faithfully formal definitions and theorem statements in Lean represent the mathematics in the textbook.

The initial focus is Chapter 5: Permutations. I am reading the mathematics alongside the Lean code, recording explanations, differences in representation, and questions requiring further investigation.

## My contributions
This repository is a fork repository from 
https://github.com/facebookresearch/algebraic-combinatorics
I have added files and folders of my own, with _Tiff at end of the folder/file name as identification.
UPSTREAM_README.md is my readme for my contribution.


## What I am looking at

- Whether formal definitions preserve the textbook’s intended meaning.
- Whether hypotheses and conclusions match the original statements.
- How indexing conventions and boundary cases are handled.
- How existing library definitions and results are reused.
- How naming and documentation affect readability.

A successful Lean check establishes the formal statement that was written. It does not, by itself, establish that the statement faithfully translates the textbook.

## Current progress

- Began reading and annotating `AlgebraicCombinatorics/Permutations/Basics.lean`.
- Studied the definitions of `Permutation`, `SymmetricGroup`, `bracketN`, and `Sn`.
- Discussed finite cardinalities, the empty permutation, and finite-type instances.
- Recorded a readability observation about textbook-style abbreviations and standard library names.

This is an ongoing learning and research project. Annotations may contain questions or provisional interpretations rather than established findings.

## Reading the annotations

My explanatory comments are marked with `MA395` where practical.

Observations distinguish between:

- explanations of Lean syntax;
- equivalent choices of mathematical representation;
- readability and organisation;
- possible differences in mathematical meaning.

A possible issue should be checked against the textbook and tested where appropriate before being treated as a confirmed formalisation error.

## Next steps

Continue reading Chapter 5 and comparing selected definitions and statements with their Lean counterparts. Develop small examples to investigate possible discrepancies.

The scope may expand after assessing the workload and findings from this chapter. Attempting an unfinished exercise is a possible later extension.

## Sources and attribution

- [Original formalisation repository](https://github.com/facebookresearch/algebraic-combinatorics)
- [Formalisation contents and coverage](https://github.com/facebookresearch/algebraic-combinatorics/blob/main/CONTENTS.md)
- [Darij Grinberg — An Introduction to Algebraic Combinatorics](https://arxiv.org/abs/2506.00738)

The original formalisation is the work of its upstream authors and contributors. My contribution is the accompanying annotations, analysis, and any explicitly identified experiments or changes.

The upstream licence and attribution notices are retained in this repository.
