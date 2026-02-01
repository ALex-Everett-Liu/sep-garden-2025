---
{"dg-publish":true,"permalink":"/src/site/notes/interpretable-dimensions-framework-1/"}
---



## Current State of Interpretable Dimensions in the LLM Era:

### 1. **Shift from Fixed to Learned Interpretability**
- **Old approach**: Manually mapping dimensions (like your SPECTER example) was always limited and brittle
- **New approach**: Models like **SPECTER2** (2023) and modern embedding models use **concept activation vectors (CAVs)** or **probing classifiers** to discover interpretable directions post-hoc
- **Example**: Instead of "dimension 0 = academic," we now train linear probes to find the direction that maximizes separation between academic vs. non-academic documents

### 2. **Active Research Areas**
- **Concept Bottleneck Models**: Force specific dimensions to correspond to human-interpretable concepts
- **Disentangled Representations**: Research on making embeddings more factorized and interpretable
- **Contrastive Learning with Concepts**: Training objectives that encourage alignment with known semantic axes

### 3. **Industry Applications**
- **Search/Retrieval**: Companies use concept-aware embeddings for better filtering (e.g., "find technical documents about finance")
- **Content Moderation**: Identifying specific content types along interpretable dimensions
- **Personalization**: Mapping user preferences to concept vectors

### 4. **Why It's Not Dead**

```python
# Modern approach example (conceptual)
from sklearn.linear_model import LogisticRegression

# Instead of fixed mapping, learn interpretable directions
concept_probes = {
    "technical_depth": LogisticRegression().fit(embeddings, technical_labels),
    "formality": LogisticRegression().fit(embeddings, formality_labels),
    # ... other concepts
}

# Use learned directions for interpretable operations
def add_formality(text_embedding, amount):
    formality_direction = concept_probes["formality"].coef_[0]
    return text_embedding + amount * formality_direction
```

### 5. **LLM-Era Enhancements**
- **LLMs as Labelers**: Use GPT-4 to generate concept labels at scale
- **Multimodal Concepts**: Aligning text embeddings with visual concepts
- **Dynamic Concept Discovery**: Automatically discovering relevant concept dimensions for specific domains

## Key Papers/Projects (2023-2024):
- **SPECTER2**: Uses task-specific adapters rather than fixed dimensions
- **InstructOR**: Instruction-tuned embeddings that respond to concept-like instructions
- **E5** and **BGE Models**: While not explicitly dimension-mapped, their training encourages interpretable separation
- **ConceptX** and **DISSECT**: Tools for analyzing what dimensions in LLMs represent

## The Reality Check:
The naive "dimension 0 = topic X" approach **is** largely abandoned because:
1. It doesn't scale (768+ dimensions can't be manually mapped)
2. Real semantic concepts are rarely orthogonal in embedding space
3. Different layers represent different types of information

**But** the **goal** of interpretable dimensions is very much alive—it's just implemented through:
- Probing studies
- Concept activation vectors
- Disentanglement objectives
- Task-specific adapters