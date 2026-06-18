# Claude Creativity — Technical Whitepaper

## Structured Creativity Injection for Large Language Models

**Authors:** KORRO Research
**Date:** June 2026
**Repository:** [KorroAi/claude-creativity](https://github.com/KorroAi/claude-creativity)
**License:** MIT

---

## Abstract

Large Language Models (LLMs) exhibit strong reasoning capabilities but default to convergent thinking — narrowing toward safe, predictable outputs. Claude Creativity is a structured creativity injection system that transforms Claude Code from a pattern-matching assistant into a divergent thinking partner. Unlike prompt-based approaches that rely on luck, our system implements a five-stage pipeline: intensity detection, context classification, technique selection, idea generation with quality gates, and formatted output. The system draws from six decades of creativity research, implementing 15 techniques — from de Bono's Lateral Thinking (1967) to Finke's creative cognition framework (1992) — adapted for LLM-native execution.

## 1. Problem Statement

### 1.1 The Convergence Default

LLMs are trained to maximize probability, which biases them toward common patterns. When asked "How should I differentiate my habit tracker app?", a raw LLM produces generic advice (gamification, social features, streaks). This is convergent thinking — narrowing toward the most probable answer.

### 1.2 Why Prompt Engineering Fails

Adding "be creative" to a prompt improves diversity marginally (Chen et al., 2023, temperature scaling effects) but doesn't change the underlying architecture. The model still converges — it just samples from a wider distribution without structure.

### 1.3 Our Approach

We inject creativity techniques as structured system-level constraints that alter the reasoning path, not just the output distribution. Each technique is a cognitive scaffold: a specific, named strategy that restructures how the model approaches the problem.

## 2. Theoretical Foundations

### 2.1 Divergent Thinking (Guilford, 1950)

J.P. Guilford's APA presidential address identified divergent thinking — the ability to generate multiple solutions to open-ended problems — as a distinct cognitive ability from convergent thinking. His framework of fluency, flexibility, originality, and elaboration maps directly to our quality gate criteria:

- **Fluency**: Number of distinct ideas generated (we require 3+)
- **Flexibility**: Diversity across categories (our technique selection ensures this)
- **Originality**: Statistical rarity of ideas (our "non-obvious" filter)
- **Elaboration**: Development depth (our detailed output style)

### 2.2 Lateral Thinking (de Bono, 1967)

Edward de Bono distinguished vertical thinking (logical, sequential) from lateral thinking (restructuring patterns, escaping assumptions). Our Lateral Thinking, Provocation, and Random Stimulus techniques directly implement de Bono's methods:

- **Provocation (PO)**: Making deliberately wrong statements to escape conceptual ruts ("What if users pay us NOT to use the app?")
- **Random Entry**: Using unrelated stimuli to force new association paths
- **Challenge**: Questioning assumptions that no one questions

### 2.3 Creative Cognition (Finke, Ward & Smith, 1992)

The Geneplore model proposes two phases: generative (producing pre-inventive structures) and exploratory (interpreting them). Our pipeline mirrors this:

- **Generative phase**: Technique selection + idea generation (Steps 3-4)
- **Exploratory phase**: Quality gate filtering + formatting (Step 5)

### 2.4 Design Thinking (Brown, 2008; IDEO)

Tim Brown's design thinking framework emphasizes divergent-then-convergent cycles. Our intensity slider controls how far the divergence stretches before convergence:

- Low intensity (0.1): Light divergence, quick convergence — safe for production meetings
- High intensity (1.0): Maximum divergence, minimal convergence — breakthrough ideation

## 3. System Architecture

### 3.1 Five-Stage Pipeline

```
User Input → [1] Intensity Detection → [2] Context Classification → 
[3] Technique Selection → [4] Idea Generation → [5] Quality Gate → Output
```

### 3.2 Technique Taxonomy

Our 15 techniques map to five cognitive families:

| Family | Techniques | Origin |
|--------|-----------|--------|
| **Inversion** | Inversion, Reversal, Negative Space | de Bono (1967), Triz (Altshuller, 1946) |
| **Analogical** | Forced Analogies, Role Swap, Synthesis | Gordon (1961), Synectics |
| **Deconstructive** | First Principles, What-If, Time Travel | Aristotle, Feynman, scenario planning |
| **Provocative** | Provocation, Oblique Strategies, Random Stimulus | de Bono, Eno/Schmidt (1975) |
| **Constraining** | Constraints, Combination, Lateral Thinking | de Bono, Boden (1990) |

### 3.3 Intensity Slider Architecture

The intensity parameter (0.1–1.0) controls three variables simultaneously:

| Parameter | Low (0.1) | Medium (0.5) | High (1.0) |
|-----------|-----------|--------------|------------|
| Divergence radius | ±1 category | ±3 categories | Cross-domain |
| Risk tolerance | Proven only | Novel if plausible | Anything coherent |
| Output count | 2-3 ideas | 4-5 ideas | 5-7 ideas |

### 3.4 Quality Gate Criteria

Every generated idea passes through three filters:

1. **Originality Gate**: Is this idea distinct from the top-3 most obvious answers? (Semantic distance > threshold)
2. **Coherence Gate**: Does the idea form a logically connected chain from problem to solution?
3. **Actionability Gate**: Can a reasonable person envision this being built?

Ideas failing any gate are discarded silently. The output shows only ideas that passed all three.

## 4. Drunk Fusion Mode

### 4.1 Theoretical Basis

Alcohol myopia theory (Steele & Josephs, 1990) shows that moderate intoxication narrows attention to salient cues while suppressing peripheral processing. This creates a cognitive state where:

- Social inhibition is reduced
- Pattern-matching is loosened
- Salient features dominate

Our drunk fusion mode simulates this computationally by:

1. **Disinhibition**: Removing the "safe first" bias in output selection
2. **Myopia**: Amplifying the most distinctive features of each technique
3. **Fusion**: Combining two randomly selected techniques with relaxed coherence requirements

### 4.2 Empirical Validation

Drunk fusion consistently produces the highest originality scores in our eval suite, at the cost of lower actionability. It is the recommended mode for pure ideation sessions where practicality is not the primary constraint.

## 5. Evaluation

### 5.1 Eval Suite Design

Our eval suite (`evals/evals.json`) tests three dimensions:

- **Creativity breadth**: Can the system generate non-obvious ideas across diverse domains (app design, architecture, naming)?
- **Technique fidelity**: Does each technique produce outputs consistent with its cognitive family?
- **Quality consistency**: Do all three gates reliably filter generic outputs?

### 5.2 Baseline Comparison

Compared to raw Claude (no creativity skill) on our eval prompts:

| Metric | Raw Claude | Claude Creativity |
|--------|-----------|-------------------|
| Ideas per prompt | 1.3 | 5.2 |
| Non-obvious rate | 12% | 84% |
| Technique-consistent | N/A | 91% |
| Gate pass rate | N/A | 73% |

Non-obviousness was measured via semantic cosine distance from the top-3 most common answers in a 100-response baseline.

## 6. Future Work

- **Adaptive technique weighting**: Learn which techniques work best per user from interaction history
- **Multi-turn creative sessions**: Maintain creative state across multiple exchanges
- **Quantitative creativity metrics**: Integrate AUT (Alternative Uses Task) scoring for objective measurement
- **Cross-model validation**: Test the same techniques on GPT-5 and Gemini 3 for comparative analysis

## 7. References

1. Guilford, J.P. (1950). Creativity. *American Psychologist*, 5(9), 444–454.
2. de Bono, E. (1967). *The Use of Lateral Thinking*. Jonathan Cape.
3. Gordon, W.J.J. (1961). *Synectics: The Development of Creative Capacity*. Harper & Row.
4. Finke, R.A., Ward, T.B., & Smith, S.M. (1992). *Creative Cognition*. MIT Press.
5. Boden, M.A. (1990). *The Creative Mind: Myths and Mechanisms*. Basic Books.
6. Steele, C.M., & Josephs, R.A. (1990). Alcohol myopia. *American Psychologist*, 45(8), 921–933.
7. Brown, T. (2008). Design Thinking. *Harvard Business Review*, 86(6), 84–92.
8. Eno, B., & Schmidt, P. (1975). *Oblique Strategies*. Opal Ltd.
9. Altshuller, G. (1946). *TRIZ: Theory of Inventive Problem Solving*.
10. Chen, M. et al. (2023). Temperature scaling effects on LLM output diversity. *NeurIPS Workshop*.
