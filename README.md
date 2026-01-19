# The Computational Prometheus: Evolutionary Genre Analysis via Structural Topic Modeling (STM)
## Project Overview
This project applies Natural Language Processing (NLP) to a centuries-old literary debate: Is Mary Shelley (Frankenstein, The Last Man) a Gothic Horror author, or the progenitor of Science Fiction?

Using a corpus of 44 novels from the Romantic, Victorian, and Modern eras, this study utilizes Structural Topic Modeling (STM) and Principal Component Analysis (PCA) to quantify the evolution of literary genres. The analysis proves that Shelley functions as an "Evolutionary Bridge, her syntactic fingerprint remains rooted in Gothic tradition, while her thematic vocabulary pioneers the narrative structures of Science Fiction.

## Key Features

- Structural Topic Modeling (STM): Unlike standard LDA, this model incorporates document-level covariates (Genre and Era) to estimate how metadata influences topic prevalence.
- Stylometric Profiling (PCA): utilized Principal Component Analysis on the top 150 function words to map the high-dimensional "stylistic distance" between authors.
- The "Bridge" Discovery: Quantitative evidence showing Shelley’s work acts as a connector—using the atmospheric tension of Gothic horror to prototype the speculative inquiries (e.g., "Naval Exploration") that would define Sci-Fi.
- Network Analysis: Constructed a Topic Correlation Network to visualize the thematic fracture between Romanticism and Modern Speculative Fiction.

## Technical Stack

- Language: R (v4.5.1) 
- Libraries: stm (Structural Topic Model), tidyverse (Data Manipulation), gutenbergr (Data Acquisition), tidytext (Tokenization), ggplot2 (Visualization) .
- Data Source: Project Gutenberg (via API).

## Project Context
Developed as a Graduate Project for CSCI E-89b: Introduction to Natural Language Processing at Harvard Extension School (Harvard DCE).

Focus: Advanced NLP, Unsupervised Learning, and Digital Humanities.

## Engineering Challenges & Trade-offs
A critical part of this analysis was identifying where the models failed to capture nuance:

The "Technology Gap" (Bag-of-Words Limitation):

- Challenge: The model identified "Naval Exploration" (Shelley) and "Space Travel" (Wells) as distinct, unrelated topics.

- Insight: Qualitatively, these serve the same narrative purpose (the vessel of exploration). The model failed to recognize that for Shelley, the boat was the rocket. This highlights the limitation of lexical frequency models in capturing historical context.

STM vs. LDA (Bias vs. Clarity):

- Decision: Chose STM to explicitly model the effect of "Era" on vocabulary.

- Trade-off: While this sharpened the distinction between genres, it introduced a "priming" effect where the model was encouraged to find differences, potentially overstating the divide between Gothic and Sci-Fi.

Reproducibility & Latent Space Volatility:

- Issue: Minor changes to metadata labels caused significant shifts in topic formation.
- Solution: Implemented a strict random seed (42) and model checkpointing to ensure the interpretative analysis remained consistent with the generated data.
