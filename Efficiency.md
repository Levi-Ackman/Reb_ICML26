
### Efficiency analysis on **APAVA** (***batch size = 128***), using runtime and peak GPU memory for training/inference. 

During training, ViRe uses vision features that are precomputed once offline and reused thereafter; therefore, this one-time preprocessing cost is excluded from per-iteration training overhead. Under this setting, ViRe is both more accurate and efficient than Medformer and FEDformer.

***For inference, to fairly reflect the deployment cost, we include the full online visual pipeline of ViRe, including deterministic visualization and vision feature extraction.***  ViRe remains comparable to FEDformer, but is slower and more memory-intensive than Medformer. 

| Metric |ViRe (Ours) | Medformer | FEDformer |
|-|-|-|-|
| F1-Score | **91.19±1.01** | 76.31±0.71 | 73.51±3.3 |
| Training Time (ms) | **211.9** | 313.1 | 677.7 |
| Training Memory (MB) | **698.2** | 838.4 | 1203.9 |
| Inference Time (ms) | 267.7 | **152.6** | 282.6 |
| Inference Memory (MB) | 740.8 | **408.5** | 491.6 |

**We will add these results to the revised manuscript so that the training/inference trade-off of ViRe is explicit.**
