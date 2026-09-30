=====================================================================
   NEURAL TELEMETRY CALIBRATION (NTC) EXPERIMENTAL SUITE EXECUTION   
=====================================================================

Dataset Split: Train=17500 | Validation=3750 | Test=3750
Training NTC Model (Coupled, Constrained, Multi-Objective Loss)...

[TABLE 1] Baseline Benchmark Comparison Results:
                       ROC-AUC  F1-Score (Opt)  Brier Score (Calib)  Temporal Jitter
Min-Max               0.881406        0.832653             0.012286         0.682226
Z-Score               0.867602        0.832653             0.012219         0.737947
Robust Scaler         0.870206        0.832653             0.012220         0.739493
Quantile Transformer  0.849616        0.789062             0.029448         0.082638
Isotonic Regression   0.419593        0.073465             0.036780         0.000093
Unconstrained NN      0.883957        0.819672             0.032085         0.008873
NTC (Proposed)        0.933246        0.806324             0.020800         0.134352

[TABLE 2] 5-Way Ablation Study Results:
                                     ROC-AUC  F1-Score (Opt)  Brier Score (Calib)  Temporal Jitter
Full NTC                            0.933246        0.806324             0.020800         0.134352
Ablation A (Unconstrained Weights)  0.879757        0.819672             0.032429         0.007540
Ablation B (Decoupled 1D Networks)  0.886954        0.484507             0.033264         0.059751
Ablation C (Static Normalization)   0.938388        0.808824             0.037323         0.000293
Ablation D (No Smoothness Penalty)  0.932393        0.806324             0.017530         0.224871

[TABLE 3] Empirical Monotonicity Verification Sweeps:

--- Latency Sweep (ms) ---
 Latency (ms)  Calibrated Score S
          500              4.9814
         1000              4.9396
         1500              4.8272
         2000              4.5949
         2500              4.2407
         3000              3.8362
         3500              3.4670

--- Drift Sweep (KS) ---
 Drift (KS)  Calibrated Score S
        0.0              4.9924
        0.2              4.9855
        0.4              4.9725
        0.6              4.9489
        0.8              4.9081
        1.0              4.8420

[TABLE 4] Cross-Metric Interaction Scenario Assessment:
                                        Calibrated Score S Failure Risk P(Y=1|X)
Scenario Alpha (Isolated High Latency)              4.5285                11.79%
Scenario Beta (Compound Degradation)                4.8236                 4.41%
Scenario Gamma (Optimal Infrastructure)             4.9938                 0.15%
