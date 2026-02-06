---
title: The Bond-Electron (BE) Matrix&#58; A Compact Way to Encode Molecular Structure
description: Struggling with determining the major product of a ring-closing reaction? Wanna know if the cyclization reaction you design for your project is feasible? You may want to learn Baldwin's rules.
date: 2026-02-05 17:00:00 -0500
author: Danger
categories: [Machine learning, molecular representation]
tags: [molecular representation]
---

When chemists describe molecules, we instinctively rely on **Lewis structures**, **bond orders**, and **electron counting**. In computational chemistry and cheminformatics, however, molecular structures must be translated into mathematical objects, such as adjacency matrices, Coulomb matrices, fingerprints, or graphs.

The **bond-electron (BE) matrix** occupies a special niche among these representations. It encodes *both bonding topology and valence electrons* in a single matrix, preserving classical chemical intuition while remaining mathematically tractable.

This post introduces what the BE matrix is, how it is constructed, and why it remains a useful conceptual and computational tool.

## What Is a Bond-Electron (BE) Matrix?

Think of a BE matrix as a molecular "accounting ledger" that keeps track of where all the electrons are in a molecule. Introduced by chemist Ivar Ugi in the 1970s, it's a mathematical way to represent the electronic structure of molecules that's both human-readable and computer-friendly.

Unlike traditional molecular representations (like SMILES strings or structural formulas), BE matrices explicitly track every valence electron in your system—both the ones forming bonds between atoms and the lone pairs sitting on individual atoms. This makes them particularly useful for understanding and predicting chemical reactions, which are fundamentally about electron redistribution.

A **bond-electron (BE) matrix** is a square matrix representation of a molecule that explicitly tracks:

- **Bonding electrons** between atoms (off-diagonal elements)
- **Nonbonding (lone-pair) electrons** on atoms (diagonal elements)

For a molecule with *N* atoms, the BE matrix is an *N × N* matrix:

$$
B =
\begin{bmatrix}
e_1 & b_{12} & \cdots & b_{1N} \\ 
b_{21} & e_2 & \cdots & b_{2N} \\ 
\vdots & \vdots & \ddots & \vdots \\ 
b_{N1} & b_{N2} & \cdots & e_N 
\end{bmatrix}
$$

where:

- Off-diagonal elements *b<sub>ij</sub>* represents the number of **bonding electron pairs** shared between atoms *i* and *j* (i.e., bonds)
- Diagonal elements *e<sub>i</sub>* represents the number of **nonbonding valence electrons** on atom *i* (i.e., lone-pair electrons)

This structure makes the BE matrix closely analogous to a Lewis structure—but written in linear algebra form.

## **How the BE Matrix Is Constructed**

Constructing a BE matrix typically follows these steps:

**Step 1: Define the Atom Ordering**

Choose an ordering of atoms (e.g., C<sup>1</sup>, C<sup>2</sup>, O<sup>3</sup>, H<sup>4</sup>…). The BE matrix depends on this ordering, though different orderings are related by permutation.

**Step 2: Assign Bonding Electron pairs**

Each covalent bond contributes **one electron pair**:

| Bond type | Electron pairs |
| :-------: | :-------: |
|  Single   |     1     |
|  Double   |     2     |
|  Triple   |     3     |

These electrons are split symmetrically:

$$
b_{ij} = b_{ji}
$$

**Step 3: Assign Nonbonding Electrons**

Lone pairs are placed on the **diagonal elements**:

- Each lone pair contributes 2 electrons
- Formal charges can be reflected by adjusting diagonal values

Let's have some examples for better understanding.

Consider water with atoms ordered as O<sup>1</sup>, H<sup>1</sup>, and H<sup>2</sup>.

- Two O–H single bonds → 2 electrons each
- Oxygen has two lone pairs → 4 nonbonding electrons

The BE matrix becomes:

$$
B_{H_2O} =
\begin{bmatrix}
4 & 1 & 1 \\
1 & 0 & 0 \\
1 & 0 & 0 
\end{bmatrix}
$$

This single matrix encodes:

- Connectivity (O bonded to both H atoms)
- Bond order (single bonds)
- Electron localization (oxygen lone pairs)

Consider ethylene (C<sub>2</sub>H<sub>4</sub>) as another example, with atoms ordered as H<sup>1</sup>, H<sup>2</sup>, C<sup>3</sup>, C<sup>4</sup>, H<sup>5</sup>, and H<sup>6</sup>. The BE matrix of ethylene is:

$$
B_{ethylene} =
\begin{bmatrix}
0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0 \\
1 & 1 & 0 & 2 & 0 & 0 \\
0 & 0 & 2 & 0 & 1 & 1 \\
0 & 0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0
\end{bmatrix}
$$

As you may already notice, a key insight is that ***The sum of any row (or column) equals the total number of valence electrons belonging to that atom***.

## Technical Deep Dive: The Reaction Matrix

As a molecular representation, BE matrix can also be employed for reaction representations. When a chemical reaction occurs, we can represent it mathematically as:

**P = R + A**

Where:

- **R** is the reactant BE matrix
- **P** is the product BE matrix
- **A** is the reaction matrix (sometimes called the transformation matrix)

The reaction matrix **A** captures the essence of what changes during the reaction:

- Positive off-diagonal values in **A** indicate bond formation or gain of lone pairs
- Negative off-diagonal values indicate bond breaking or loss of lone pairs
- Diagonal changes in **A** indicate electron redistribution
- **A** must sum to zero (electron conservation: ∑<sub>i,j</sub> a<sub>ij</sub> = 0)

For most elementary reactions, 

$$
|a<sub>ij</sub>| ≤ 2
$$

since changing by two electrons represents a significant chemical process (like forming/breaking a double bond).

Let's consider the following reaction as an example for better understanding (each atom in the reaction was numbered):

![**Scheme 1**. Example reaction](/assets/img/BE_matrix/Rxn.png)

So we have the reactant BE matrix **R** as (order same as the number in the reaction scheme):

$$
R =
\begin{bmatrix}
0 & 1 & 1 & 1 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
1 & 0 & 0 & 0 & 1 & 1 & 1 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
1 & 0 & 0 & 1 & 0 & 0 & 4 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 2 & 1 & 1 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 
\end{bmatrix}
$$

While the product BE matrix **P** is:

$$
P =
\begin{bmatrix}
0 & 1 & 1 & 1 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
1 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
1 & 0 & 0 & 0 & 0 & 0 & 4 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 2 & 1 & 1 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 
\end{bmatrix}
$$

Which means the transformation matrix **A** is:

$$
A =
\begin{bmatrix}
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & –1 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & –1 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & –1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & –1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 
\end{bmatrix}
$$

This indicates the bond between C<sup>4</sup> and O<sup>7</sup>, and the bond between N<sup>9</sup> and H<sup>8</sup> were broken, while a bond between O<sup>7</sup> and H<sup>8</sup>, and a bond between C<sup>4</sup> and N<sup>9</sup>, were built. 

A better illustration is shown below:

![**Scheme 2**. Reaction matrix](/assets/img/BE_matrix/rxn_matrix.png)

## **Why the BE Matrix Is Useful**

BE matrices solve several critical problems in computational chemistry:

1. **Mass Conservation**: By explicitly tracking all electrons and atoms, BE matrices prevent the computational "hallucinations" that plague many AI models—where products contain more or fewer atoms than reactants.
2. **Chemical Interpretability**: Unlike black-box representations, BE matrices map directly to how chemists think about reactions through arrow-pushing mechanisms. In other words, every element of a BE matrix has a clear chemical meaning.
3. **Automated Reaction Discovery**: Historically, BE matrices were used to track **electron flow during reactions**, identify bond breaking/forming events, and encode reaction mechanisms in a rule-based way. Since BE matrices are numerical, fixed-size, and interpretable, making them useful as reaction descriptors, as intermediate representations in ML workflows, and teaching tools bridging symbolic and numerical chemistry.  Computers can systematically generate plausible reaction pathways by exploring valid transformations of BE matrices.

Despite its elegance, the BE matrix is not a universal solution. For example, there is no direct encoding of 3D geometry in BE matrix, while current implementations struggle with transition metal catalysis and coordination chemistry. For resonance structures, it requires multiple matrices for representation. Moreover, for aromaticity and delocalization, the BE matrices are approximated. Representing delocalized electrons (like benzene's π-electrons) requires careful handling to avoid electron overcounting in polycyclic systems. Finally, atom ordering in BE matrix is not inherently invariant.

While less common than fingerprints or graph neural networks today, BE matrices remain conceptually important. Many modern representations implicitly rediscover ideas that the BE matrix made explicit decades ago:

- Conservation of electrons
- Valence-based constraints
- Local chemical environments

In that sense, the BE matrix is a reminder that **good molecular representations don’t have to be complicated—just chemically honest**.

## **Conclusion**

Bond-electron matrices represent a beautiful marriage of chemical intuition and mathematical rigor. They encode the fundamental reality that chemical reactions are about electron redistribution, not just molecular rearrangement. As machine learning continues to revolutionize chemistry, BE matrices provide the physical constraints and chemical interpretability that turn black boxes into powerful scientific tools.

Whether you're developing new drugs, designing materials, or building the next generation of reaction prediction models, understanding BE matrices gives you a framework for thinking about chemistry that's both computationally tractable and chemically meaningful.

