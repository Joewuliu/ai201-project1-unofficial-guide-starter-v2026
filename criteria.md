# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
I chose 4 out of 5 because my questions cover several different topics in the
corpus, and I want retrieval to work reliably without assuming it will be
perfect on every question.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
I chose every answer because source attribution is a core part of this RAG
system. If the system gives an answer without a source, I would not be able to
verify that the answer actually came from the retrieved documents.

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

**Why this target:**
I chose 4 out of 5 because I want the system to reject almost all clearly
unrelated questions while allowing for one borderline case where a retrieved
chunk may appear somewhat similar even though it does not actually answer the
question.

---

## 4. Chunks are complete and usable

At least 4 of 5 sampled chunks should contain a complete thought that could be
understood without needing to read the chunk before or after it.

**Why this target:**
I chose 4 out of 5 because the goal of chunking is to preserve enough context
for retrieval, but I expect that an occasional chunk may still split
information in an awkward place. Requiring most sampled chunks to stand on
their own gives me a clear way to judge whether my chunking strategy is working.

---

## 5. Answers include the expected key information

For at least 4 of my 5 test questions, the generated answer should contain the
expected word or phrase listed in the `expects` field in `questions.py`.

**Why this target:**
I chose 4 out of 5 because the five questions cover different parts of the
corpus, and I want the system to correctly answer most of them without
requiring perfect performance. The `expects` phrases give me a consistent way
to check whether each answer includes the key fact I decided was important
before testing.


---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
