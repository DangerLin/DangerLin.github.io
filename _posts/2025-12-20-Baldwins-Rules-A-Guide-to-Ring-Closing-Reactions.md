---
Title: Baldwin's Rules: A Guide to Ring-Closing Reactions
Date: 2025-12-20 00:00:00 -0500
Categories: organic chemistry, cyclization
Tags: baldwin's rule
---

# Baldwin's Rules: A Guide to Ring-Closing Reactions

*In memory of Professor Jack Baldwin (1938-2020)*

## Introduction: A Puzzling Selectivity

If you're studying organic chemistry, you've probably encountered puzzling questions about cyclization reactions. Consider this: when the same molecule undergoes intramolecular ring closure, and both possible products would form five-membered rings, why does one pathway give 100% yield while the other gives essentially 0%?

This selectivity isn't random—it follows a set of elegant guidelines known as **Baldwin's rules**, which help us predict and understand the feasibility of ring-closing reactions.

## The Origin of Baldwin's Rules

In 1976, British chemist Sir Jack Edward Baldwin systematically analyzed cyclization patterns in acyclic compounds and formulated what we now call Baldwin's rules. His framework uses three key parameters to describe any ring-closing reaction:

### 1. **Ring Size (n)**

A number indicating the size of the ring being formed:

- **5-endo-trig** → forming a 5-membered ring
- **6-exo-dig** → forming a 6-membered ring

### 2. **Bond-Breaking Mode**

The position of the breaking bond relative to the forming ring:

- **Exo** (exocyclic): The bond being broken lies outside the ring being formed. This ultimately produces a smaller ring.
- **Endo** (endocyclic): The bond being broken lies inside the ring being formed. This ultimately produces a larger ring.

### 3. **Hybridization of the Attacked Atom**

- **Tet**: The atom being attacked is sp³ hybridized (tetrahedral)
- **Trig**: The atom being attacked is sp² hybridized (trigonal)
- **Dig**: The atom being attacked is sp hybridized (digonal)

## The Rules in Detail

### Rule 1: Tetrahedral (Tet) Systems

**Favorable:**

- 3- to 7-membered rings via **exo-tet** cyclization

**Unfavorable:**

- 5- to 6-membered rings via **endo-tet** cyclization

**Key takeaway:** For tetrahedral centers, attack from outside the forming ring (exo) is generally favored.

### Rule 2: Trigonal (Trig) Systems

**Favorable:**

- 3- to 7-membered rings via **exo-trig** cyclization
- 6- to 7-membered rings via **endo-trig** cyclization

**Unfavorable:**

- 3- to 5-membered rings via **endo-trig** cyclization

**Key takeaway:** Larger rings (6-7 membered) can accommodate endo-trig closures, but smaller rings cannot.

### Rule 3: Digonal (Dig) Systems

**Favorable:**

- 5- to 7-membered rings via **exo-dig** cyclization
- 3- to 7-membered rings via **endo-dig** cyclization

**Unfavorable:**

- 3- to 4-membered rings via **exo-dig** cyclization

**Key takeaway:** Digonal systems show different selectivity—endo closures are broadly favorable, while small exo closures are disfavored.

## Summary Table

| Ring Size     | 3    | 4    | 5    | 6    | 7    |
| ------------- | ---- | ---- | ---- | ---- | ---- |
| **exo-tet**   | ✓    | ✓    | ✓    | ✓    | ✓    |
| **endo-tet**  | —    | —    | ✗    | ✗    | —    |
| **exo-trig**  | ✓    | ✓    | ✓    | ✓    | ✓    |
| **endo-trig** | ✗    | ✗    | ✗    | ✓    | ✓    |
| **exo-dig**   | ✗    | ✗    | ✓    | ✓    | ✓    |
| **endo-dig**  | ✓    | ✓    | ✓    | ✓    | ✓    |

*(✓ = favored, ✗ = disfavored, — = not commonly observed)*

## Solving the Opening Puzzle

Now we can understand the selectivity shown in the opening example. The molecule can cyclize via two pathways:

- **Path A**: 5-endo-trig → **Disfavored** (yields ~0%)
- **Path B**: 5-exo-trig → **Favored** (yields ~100%)

According to Baldwin's rules, 5-endo-trig cyclizations are unfavorable, while 5-exo-trig are favored. This perfectly explains the observed selectivity!

## Extension to Enolate Anions

Baldwin's rules also apply to cyclizations involving enolate anions, with additional descriptors:

- **Enolendo**: The C-C bond of the enolate becomes part of the forming ring
- **Enolexo**: The C-C bond of the enolate lies outside the forming ring

**Simplified rules for enolates:**

1. **3- to 5-membered rings**: enolexo processes are favored; enolendo processes are disfavored
2. **6- to 7-membered rings**: enolendo processes become favored

This helps explain why certain ketone cyclizations favor one regioisomer over another based on ring size.

## Important Considerations

### 1. "Disfavored" ≠ "Forbidden"

Baldwin's "disfavored" classification doesn't mean the reaction is impossible—just that it's more difficult and may require special conditions or give lower yields.

### 2. Relative Reactivity Trends for Trig Systems

- **5-endo ≫ 4-exo**
- **5-exo > 6-endo**
- **6-exo ≫ 7-endo**

These trends help predict product distributions when multiple pathways are possible.

### 3. Third-Row Elements (S, P, etc.)

When sulfur or other third-row elements participate, normally disfavored processes like **5-endo-trig** can become feasible. This is attributed to:

- Longer C-S bond lengths providing geometric flexibility
- Empty 3d orbitals on sulfur that can interact with π bonds

### 4. Applicability to Cations and Radicals

Baldwin's rules apply equally well to cationic and radical cyclizations, not just anionic processes.

### 5. Exceptions Exist

Like all empirical rules in chemistry, violations of Baldwin's rules have been documented. Special structural features, electronic effects, or reaction conditions can override the general trends.

## Practice Problems

**Problem 1:** Are the following reactions feasible? Why or why not?

a) A 4-exo-trig cyclization
 b) A 6-endo-dig cyclization

**Problem 2:** Predict the major product when the following substrates undergo cyclization:

a) An alkoxide with a choice between 5-exo-tet and 6-enolendo-exo-tet pathways
 b) A nitrogen nucleophile with options for 5-endo-dig vs. 6-exo-dig attack on an alkyne

*(Think through these using the rules above before checking literature or computational predictions!)*

## A Tribute to Professor Baldwin

Professor Sir Jack Edward Baldwin passed away in January 2020 at the age of 81. His contributions to organic chemistry extended far beyond these rules—he made fundamental discoveries in natural product synthesis, enzymatic mechanisms, and stereoselective reactions.

Baldwin's rules remain one of the most practical and widely used guidelines in synthetic organic chemistry, helping chemists design more efficient syntheses and understand reaction selectivity. His legacy continues to guide researchers in academia and industry worldwide.

## Conclusion

Baldwin's rules provide a powerful framework for understanding and predicting the outcome of ring-closing reactions. By considering three simple parameters—ring size, bond-breaking mode, and hybridization—we can rationalize selectivity that might otherwise seem arbitrary.

Whether you're planning a total synthesis, analyzing a reaction mechanism, or simply studying for an exam, these rules are an indispensable tool in the organic chemist's toolkit.

------

## References

1. Baldwin, J. E. *J. Chem. Soc. Chem. Commun.* **1976**, 734-736.
2. Baldwin, J. E.; Thomas, R. C.; Kruse, L.; Silberman, L. *J. Org. Chem.* **1977**, *42*, 3846-3852.
3. Johnson, C. D. *Acc. Chem. Res.* **1993**, *26*, 476-482.
4. Baldwin, J. E.; Kruse, L. I. *J. Chem. Soc. Chem. Commun.* **1977**, 233-235.
5. Baldwin, J. E. *Tetrahedron* **1982**, *38*, 2939-2947.
6. Alabugin, I. V.; Gilmore, K. *Chem. Commun.* **2013**, *49*, 11246-11250.
7. Ferry, G. *Nature* **2020**, *578*, 212.

------

*Have questions or examples to share? Understanding these rules through practice is the best way to internalize them. Happy cyclizing!*