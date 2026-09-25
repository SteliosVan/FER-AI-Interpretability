# Questioning Representational Optimism in Deep Learning: The Fractured Entangled Representation Hypothesis

**Authors:** Alexandra Karali, Magdalini Maria Pliatsika, Georgios Kouseris, Georgios Oikonomou, Stylianos Vantarakis

## Overview

This project empirically investigates the **Fractured Entangled Representation (FER) hypothesis** — the idea that models trained via conventional Stochastic Gradient Descent (SGD) often achieve high output performance while relying on disorganized, heuristic-based internal structures, rather than the **Unified Factored Representations (UFR)** observed in open-ended evolutionary systems.

We extend the original FER analysis through a series of novel experiments that probe the mechanisms behind representational formation, using **Compositional Pattern Producing Networks (CPPNs)** as a transparent "toy model" for internal representation analysis — contrasting CPPNs trained via SGD with CPPNs evolved through **Picbreeder**.

## Background

- **CPPNs** map 2D pixel coordinates `(x, y)` to color values, allowing every hidden neuron's behavior to be visualized directly as an image — unlike black-box models such as modern LLMs.
- **Picbreeder** is a platform where humans evolved images through open-ended search rather than training toward a fixed target, producing images (e.g., a symmetrical skull) with clean, modular internal structure.
- **FER** (Fractured Entangled Representation): concepts are split into disconnected pieces and inappropriately mixed with unrelated functions — analogous to "spaghetti code."
- **UFR** (Unified Factored Representation): concepts are distinct, modular, and reused effectively — analogous to clean software design.
- **Imposter Intelligence**: models that appear flawless at the output level while relying on FER internally, lacking true generalizable understanding (e.g., a model that draws a perfect skull without any internal notion of "symmetry").

## Experiments

### 1. Loss Function Regularization
We added **orthogonality regularization** (decorrelating feature maps via a correlation-matrix penalty) and **activation sparsity regularization** (L1 penalty) to the training objective. This produced a measurably more interpretable latent space than baseline SGD, with individual weights corresponding to more localized, semantically meaningful visual effects.

### 2. Transfer Learning and Feature Complexity
Using a pre-trained CPPN with the first 80% of layers frozen, we fine-tuned only the remaining 20% via SGD. This produced higher-level, semantically meaningful controls (e.g., a single weight controlling jaw inclination or eye symmetry).

### 3. Low-Dimensional Structure in CPPN Evolution
We layerized a Picbreeder evolutionary lineage into a fixed-parameter representation and applied PCA. The **first principal component explained ~84% of variance**, and traversing it produced a smooth, monotonic change in mirror symmetry — evidence that open-ended evolution organizes variation around a low-dimensional, structurally meaningful axis.

### 4. Symmetry-Preserving Directions in Weight Space
By sampling random weight perturbations and filtering for those that preserved global mirror symmetry, we identified a dominant axis controlling image sharpness/contrast while leaving symmetry intact — showing that evolved networks contain organized subspaces for controlled, non-destructive variation.

### 5. Emergence of Rotational Symmetry Across Layers
Activation sweeps on rotation-invariant neurons showed a clear layer-dependent progression:
- **Early layers (e.g., layer 3):** symmetry is fragile and easily disrupted.
- **Intermediate layers (e.g., layer 8):** symmetry is preserved; modulation smoothly changes ring radius.
- **Late layers (e.g., layer 15):** symmetry is fully stabilized as a causally controllable, structurally distinct factor.

### 6. Dataset Generation and Scaling
We trained a conditional CPPN (`(x, y, d, z) → (h, s, v)`) jointly on datasets of 60 and 120 structurally similar skull images to test whether data scale alone resolves FER.

**Results:** Increasing dataset size did **not** eliminate FER — most neurons remained visually chaotic and entangled. However, scaling introduced a **mild stabilizing pressure**: certain weight IDs (e.g., controlling brightness or global scale) developed consistent, semi-localized semantic roles across images and remained stable even under larger perturbation ranges (R = 2) that would collapse single-image or smaller-dataset models. Despite this, the representations never approached the clean, hierarchical modularity of evolved (UFR) networks.

## Discussion

We connect FER to mechanistic interpretability research in large language models, particularly work on **Sparse Autoencoders (SAEs)**, superposition, and attribution graphs. Key limitations identified:
- Entanglement/fracture metrics depend heavily on the quality of SAE-based feature dictionaries.
- Many metrics rely on the **Linear Representation Hypothesis**, which may not capture curved manifolds or higher-order feature interactions present in real models.

We argue FER is best understood as a **structural hypothesis** motivating further methodological development, rather than a single standardized metric.

## Conclusion

- Standard SGD naturally drifts toward FER, but targeted interventions (orthogonality/sparsity regularization) measurably mitigate this.
- UFR in evolved networks relies on early establishment of low-dimensional structural axes (e.g., symmetry) that are preserved and modulated throughout network depth — something SGD training does not reliably internalize even with matching output.
- **Scaling data alone does not resolve FER.** It reduces catastrophic instability and yields more semi-stable semantic weights, but does not induce true unified, factored representations.
- These findings suggest that benchmark/output performance alone is insufficient to detect "imposter" representations in larger foundation models, motivating future work using nonlinear and geometric representation analysis.

## References

- [Toy Models of Superposition](https://transformer-circuits.pub/2022/toy_model/index.html)
- [Towards Monosemanticity](https://transformer-circuits.pub/2023/monosemantic-features/index.html)
- [Scaling Monosemanticity](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html)
- [Attribution Graphs: Methods](https://transformer-circuits.pub/2025/attribution-graphs/methods.html)
- [Towards Measuring Superposition (Bereska)](https://static1.squarespace.com/static/669758ca11526478ba0619b2/t/67ecbb6b72cdcc5d88e531/1743569557450/bereska-towards-measuring-superposition.pdf)
- [arXiv:2409.14507v6](https://arxiv.org/pdf/2409.14507v6)
- [arXiv:2311.03658v2](https://arxiv.org/pdf/2311.03658v2)
- [arXiv:2405.14860](https://arxiv.org/pdf/2405.14860)
- [arXiv:2301.05062](https://arxiv.org/pdf/2301.05062)
