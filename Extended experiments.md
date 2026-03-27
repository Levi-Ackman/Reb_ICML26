To evaluate ViRe on **multivariate time series forecasting**, we conduct additional experiments on the **M4** benchmark *[1]*. We compare ViRe with **iTransformer** *[2]* and **PatchTST** *[3]*, and report SMAPE, MASE, and OWA ***(the lower, the better)***.

| Task | Metric | ViRe (Ours) | iTransformer | PatchTST |
|-|-|-|-|-|
| Yearly | SMAPE | **13.201** | 14.141 | 16.463 |
|  | MASE | **2.972** | 3.179 | 3.967 |
|  | OWA | **0.787** | 0.833 | 1.003 |
| Quarterly | SMAPE | **1.064** | 10.739 | 10.644 |
|  | MASE | **1.181** | 1.282 | 1.278 |
|  | OWA | **0.911** | 0.955 | 0.949 |
| Monthly | SMAPE | **12.541** | 13.727 | 13.399 |
|  | MASE | **0.934** | 1.082 | 1.031 |
|  | OWA | **0.892** | 0.984 | 0.944 |

To further assess ViRe under **irregularly sampled time series**, we evaluate it on three datasets: **PhysioNet**, **MIMIC**, and **Human Activity**, following **t-PatchGNN** *[4]*. We compare ViRe against **t-PatchGNN** *[4]* and **Neural Flow** *[5]*, using MSE and MAE ***(the lower, the better)***.

| Dataset | Metric | ViRe (Ours) | t-PatchGNN | Neural Flow |
|-|-|-|-|-|
| PhysioNet | MSE $\times 10^{-3}$ | **4.86** | 4.98 | 7.20 |
|  | MAE $\times 10^{-2}$ | **3.58** | 3.72 | 4.67 |
| MIMIC | MSE $\times 10^{-3}$ | **1.62** | 1.69 | 1.87 |
|  | MAE $\times 10^{-2}$ | **6.92** | 7.22 | 8.03 |
| Human Activity | MSE $\times 10^{-3}$ | **2.55** | 2.66 | 4.05 |
|  | MAE $\times 10^{-2}$ | **3.09** | 3.15 | 4.46 |

We also conduct extended experiments using two representative *human activity recognition benchmarks*, **FLAAP** *[6]* and **UCI-HAR** *[7]*, to validate the effectiveness of ViRe in general **time series classification**. We choose **iTransformer** *[2]* and **PatchTST** *[3]* as baselines, using Accuracy and F1-score ***(the higher, the better)***.
| Task | Metric | ViRe (Ours) | iTransformer | PatchTST |
|-|-|-|-|-|
| FLAAP | Accuracy | **83.42** | 75.35 | 58.34 |
|  | F1-score | **83.28** | 74.88 | 57.58 |
| UCI-HAR | Accuracy | **93.72** | 92.41 | 87.67 |
|  | F1-score | **94.17** | 92.39 | 88.02 |

```
[1] N-BEATS: Neural basis expansion analysis for interpretable time series forecasting.

[2] iTransformer: Inverted Transformers Are Effective for Time Series Forecasting.

[3] A Time Series is Worth 64 Words: Long-term Forecasting with Transformers.

[4] Irregular Multivariate Time Series Forecasting: A Transformable Patching Graph Neural Networks Approach.

[5] Neural Flows: Efficient Alternative to Neural ODEs.

[6] FLAAP: An Open Human Activity Recognition (HAR) Dataset for Learning and Finding the Associated Activity Patterns.

[7] A Public Domain Dataset for Human Activity Recognition Using Smartphones.
```
