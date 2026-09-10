# Portfolio_v2
You are acting as a senior IEEE research-paper author, computer-vision researcher, and academic editor.

I have attached my current research-paper draft and I want you to transform it into a complete, coherent, publication-ready IEEE-style research paper of approximately 7–8 pages.

The paper title is:

“Severity-Aware and Uncertainty-Guided Deep Learning Framework for Automated Solar Panel Defect Inspection”

Your job is NOT simply to rewrite the existing document.

You must critically examine the existing manuscript, integrate the experimental results I provide below, correct structural and logical problems, improve scientific clarity, and produce a complete IEEE-style research paper.

The final paper must read like a paper genuinely written by a human researcher.

Do NOT write in a generic AI-generated style.

Do NOT over-polish the language into unnatural academic prose.

Do NOT repeatedly use phrases such as:
“Furthermore,”
“Moreover,”
“In addition,”
“It is worth noting that,”
“This innovative framework,”
“This groundbreaking approach,”
“This state-of-the-art method,”
unless genuinely necessary.

Use varied sentence structures, natural transitions, technically precise wording, and moderate academic language.

Do not try to evade AI-detection systems or make false claims about human authorship. The goal is simply to produce natural, technically credible academic writing.

========================================================
1. CORE RESEARCH DIRECTION
========================================================

The research focuses on:

“Severity-Aware and Uncertainty-Guided Automated Solar Panel Inspection”

The proposed framework integrates:

1. Image acquisition
2. YOLO-based panel/cell localization
3. Candidate multi-frame acquisition
4. Image-quality assessment
5. Quality-gated frame selection
6. Image preprocessing
7. Deep-learning defect classification
8. Ordinal severity prediction
9. Uncertainty estimation
10. Selective prediction and human review
11. Maintenance-priority decision support

The central research contribution is NOT any individual existing algorithm.

Do NOT claim novelty for:
• YOLO
• CNNs
• EfficientNet
• MobileNetV2
• ResNet
• Random Forest
• MC Dropout
• Temperature scaling
• Grad-CAM
• ordinal loss
• image-quality metrics
• uncertainty estimation
• selective prediction

These are established techniques.

The contribution should instead be positioned as the integrated experimental framework that combines:

• quality-aware acquisition
• severity-aware prediction
• uncertainty estimation
• selective prediction
• robustness evaluation
• computational efficiency
• maintenance-priority decision support

The paper should emphasize the systematic evaluation of these components rather than claiming that each individual component is novel.

Do NOT use “first-ever”, “first of its kind”, “revolutionary”, or similar unsupported novelty claims.

========================================================
2. VERY IMPORTANT: DO NOT FABRICATE RESULTS
========================================================

The numerical results supplied below are the experimental values to be incorporated into the paper.

Treat them as the reported experimental results.

Do not invent additional:
• accuracy values
• precision values
• recall values
• F1 values
• standard deviations
• confidence intervals
• p-values
• training epochs
• learning rates
• hardware performance
• inference latency
• dataset samples
• ablation results
• statistical significance

unless explicitly provided or genuinely derivable from the supplied information.

If information is missing, write the paper without inventing it.

If a value appears inconsistent with another table, FLAG THE INCONSISTENCY.

Do not silently change the value.

========================================================
3. FIRST TASK: METRIC CONSISTENCY AUDIT
========================================================

Before rewriting the paper, perform a detailed:

“METRIC CONSISTENCY AUDIT”

Check every supplied table.

In particular, verify:

• Accuracy
• Macro-F1
• MAE
• QWK
• ECE
• Brier score
• NLL
• AUROC
• Precision
• Recall
• Confusion matrix
• Support counts
• FPS
• parameter counts
• memory size
• derived efficiency metrics

Check whether the confusion matrix agrees with the reported classification metrics.

IMPORTANT:

The currently supplied confusion matrix is:

Actual \ Predicted

Functional:
220  3  2  0

Moderate:
1  15  2  0

Mild:
1  2  40  2

Severe:
0  0  3  103

Total samples = 394

This matrix produces an accuracy of approximately 95.94%, whereas the reported overall accuracy is 95.6%.

The class-wise values in Table XI also do not perfectly correspond to this matrix.

Therefore:

DO NOT silently modify either the matrix or the class-wise metrics.

Instead:

1. Identify the inconsistency.
2. Show the derived values from the matrix.
3. Compare them with the supplied values.
4. State which values require verification from the original experiment.
5. In the final paper, use only a consistent set after explicitly identifying what needs to be verified.

If the original experiment cannot be verified, do NOT manufacture a correction.

The same principle applies to every table.

========================================================
4. DATASET: ELPV
========================================================

The primary classification dataset is the ELPV dataset:

“A Benchmark for Visual Identification of Defective Solar Cells in Electroluminescence Imagery”

Official repository:

https://github.com/zae-bayern/elpv-dataset

ELPV contains:

• 2,624 samples
• 300 × 300 pixel images
• 8-bit grayscale electroluminescence images
• samples extracted from 44 photovoltaic modules
• defect probability annotations
• probability values:
  p = 0
  p = 1/3
  p = 2/3
  p = 1

The dataset should be described as a publicly available benchmark.

Also cite the Forschungszentrum Jülich Data archive:

“EL Dataset of PV modules”

DOI:

10.26165/JUELICH-DATA/GCBNMA

Original references include:

Buerhop-Lutz et al.,
“A Benchmark for Visual Identification of Defective Solar Cells in Electroluminescence Imagery,”
EU PVSEC, 2018,
DOI: 10.4229/35thEUPVSEC20182018-5CV.3.15.

Deitsch et al.,
“Automatic classification of defective photovoltaic module cells in electroluminescence images,”
Solar Energy, vol. 185, pp. 455–468, 2019,
DOI: 10.1016/j.solener.2019.02.067.

Clearly distinguish:

• original dataset creators
• original publication
• official repository
• archival record
• use of the dataset in this study

Do NOT say that the authors personally collected ELPV.

Do NOT describe ELPV as drone imagery.

Do NOT describe ELPV as RGB outdoor imagery.

Do NOT claim ELPV contains YOLO bounding boxes.

========================================================
5. ELPV CLASS DISTRIBUTION
========================================================

Use the following experimental class distribution:

Functional: 1502
Moderate: 123
Mild: 298
Severe: 701

Total: 2624

Calculate the exact percentages.

Create a publication-quality table containing:

Class
Original Defect Probability
Number of Samples
Percentage
Ordinal Severity Level

IMPORTANT:

The four severity names are the research formulation.

Do not incorrectly state that ELPV originally contained these exact four semantic class names unless the source explicitly supports that statement.

Explain that the study reformulates the probability-based labels into an ordinal severity framework.

The ordering must be explicitly defined and logically consistent.

If the current draft's mapping is ambiguous or semantically questionable, flag it for correction rather than silently changing it.

========================================================
6. DATA SPLITTING
========================================================

The intended classification split is approximately:

70% training
15% validation
15% testing

The manuscript should describe:

• stratification
• fixed random seed
• splitting before augmentation
• prevention of direct train/test duplication

However, DO NOT claim module-level separation unless it was actually implemented.

ELPV contains samples originating from 44 modules, so discuss possible source-module correlation and leakage.

If the experiment used image-level stratification rather than module-disjoint splitting, state this honestly and identify module-level splitting as a stronger protocol for future validation.

Do not invent a module-disjoint split.

========================================================
7. IMPORTANT DATASET LIMITATION
========================================================

ELPV is NOT a genuine multi-frame camera/video dataset.

Therefore, the paper must NOT claim:

• real camera bursts from ELPV
• consecutive frames from a drone
• real-time video acquisition from ELPV
• field-acquired multi-frame sequences
• outdoor deployment validation

If multi-frame candidate pools were generated using transformations or simulated variations, call them:

“synthetically constructed candidate frame pools”

or

“simulated multi-frame acquisition”

and clearly distinguish them from genuine field acquisition.

This distinction must appear in:

• Dataset section
• Methodology
• Experimental Design
• Limitations

========================================================
8. YOLO DATASET
========================================================

The YOLO localization dataset must be treated as a SEPARATE dataset from ELPV.

This distinction is mandatory.

ELPV is used for:

• cell-level defect classification
• severity prediction
• uncertainty estimation

The YOLO dataset is used for:

• panel/cell localization

DO NOT state:

“The YOLO model was trained using the ELPV dataset”

unless actual bounding-box annotations were created and used.

ELPV itself does not provide the required YOLO bounding-box annotations.

If the actual YOLO dataset used is the “Solar Panel Bounding Boxes 621” dataset, describe it only if it matches the actual experiment.

Reported characteristics:

• 621 images
• solar-panel object detection
• bounding-box annotations
• YOLO-format annotations
• outdoor/in-the-wild imagery
• manually annotated bounding boxes

Do not claim the license permits unrestricted use unless verified.

If the actual YOLO dataset differs, use the actual dataset instead.

Never invent a dataset source.

========================================================
9. YOLO DATASET PROVENANCE
========================================================

Create a dedicated subsection:

“YOLO Localization Dataset and Acquisition”

Include, where available:

• dataset name
• source URL
• acquisition/source
• image count
• object classes
• annotation format
• bounding-box format
• preprocessing
• train/validation/test split
• annotation method
• license
• dataset limitations

Explain the standard YOLO annotation representation when applicable:

class_id
x_center
y_center
width
height

with normalized coordinates.

Only state the exact object class if supported by the actual dataset.

Clearly distinguish:

panel localization

from

cell defect classification.

========================================================
10. DATASET ROLE TABLE
========================================================

Create a table comparing the datasets.

Suggested columns:

Dataset
Modality
Number of Images
Annotation Type
Task
Model
Role in Framework

The table must make the following conceptual separation obvious:

ELPV:
EL grayscale
2624
defect probability
classification/severity
CNN backbones
defect analysis

YOLO dataset:
actual modality
actual image count
bounding boxes
object detection
YOLO
localization

Do not merge the two datasets.

========================================================
11. REPORTED EXPERIMENTAL RESULTS
========================================================

Use the following values in the paper.

--------------------------------------------------------
TABLE IV. PER-BACKBONE CLASSIFICATION RESULTS
--------------------------------------------------------

Custom CNN:
4-Class Accuracy = 89.8%
Binary Accuracy = 94.1%
Macro-F1 = 85.7%
MAE = 0.284
QWK = 0.842

MobileNetV2:
4-Class Accuracy = 93.7%
Binary Accuracy = 96.6%
Macro-F1 = 90.8%
MAE = 0.214
QWK = 0.901

EfficientNet-B0:
4-Class Accuracy = 95.6%
Binary Accuracy = 97.7%
Macro-F1 = 93.5%
MAE = 0.164
QWK = 0.934

ResNet-18:
4-Class Accuracy = 94.4%
Binary Accuracy = 97.1%
Macro-F1 = 92.1%
MAE = 0.186
QWK = 0.919

ResNet-50:
4-Class Accuracy = 95.1%
Binary Accuracy = 97.5%
Macro-F1 = 93.0%
MAE = 0.171
QWK = 0.929

--------------------------------------------------------
TABLE V-A. CATEGORICAL VS ORDINAL SEVERITY LEARNING
--------------------------------------------------------

EfficientNet-B0 + Cross-Entropy:
Accuracy = 94.7%
Macro-F1 = 92.1%
MAE = 0.213
QWK = 0.912

EfficientNet-B0 + Ordinal Loss:
Accuracy = 95.6%
Macro-F1 = 93.5%
MAE = 0.164
QWK = 0.934

Interpretation must emphasize that ordinal learning is particularly beneficial for severity-aware metrics such as MAE and QWK.

Do not claim statistical significance unless statistical testing exists.

--------------------------------------------------------
TABLE V-B. ABLATION OF PROPOSED COMPONENTS
--------------------------------------------------------

Single-frame + Softmax:
Accuracy = 92.8%
Macro-F1 = 89.7%
MAE = 0.287
QWK = 0.871
ECE = 8.9%

+ Quality Gating:
Accuracy = 94.1%
Macro-F1 = 91.4%
MAE = 0.241
QWK = 0.901
ECE = 6.6%

+ Multi-frame Selection:
Accuracy = 94.6%
Macro-F1 = 92.0%
MAE = 0.218
QWK = 0.914
ECE = 5.9%

+ Ordinal Severity:
Accuracy = 95.2%
Macro-F1 = 93.0%
MAE = 0.177
QWK = 0.928
ECE = 4.7%

+ MC Dropout:
Accuracy = 95.3%
Macro-F1 = 93.2%
MAE = 0.173
QWK = 0.930
ECE = 3.8%

Full Proposed Framework:
Accuracy = 95.6%
Macro-F1 = 93.5%
MAE = 0.164
QWK = 0.934
ECE = 2.9%

Interpret the ablation incrementally.

Do not attribute the entire performance gain to a single component.

--------------------------------------------------------
TABLE VI. ROBUSTNESS UNDER SIMULATED DEGRADATION
--------------------------------------------------------

Gaussian Blur:
Severity 1 = 94.7%
Severity 3 = 90.1%
Severity 5 = 80.4%

Additive Gaussian Noise:
Severity 1 = 95.0%
Severity 3 = 91.8%
Severity 5 = 84.1%

Brightness/Contrast Shift:
Severity 1 = 95.2%
Severity 3 = 92.8%
Severity 5 = 87.0%

JPEG Compression:
Severity 1 = 95.3%
Severity 3 = 93.2%
Severity 5 = 88.5%

Clearly state these are simulated degradations.

Do not describe them as actual field conditions.

--------------------------------------------------------
TABLE VI-B. ROBUSTNESS: BASELINE VS PROPOSED
--------------------------------------------------------

Gaussian Blur:
Severity 1:
Baseline 92.4%
Proposed 94.7%
Improvement +2.3%

Severity 3:
Baseline 82.6%
Proposed 90.1%
Improvement +7.5%

Severity 5:
Baseline 66.8%
Proposed 80.4%
Improvement +13.6%

Noise:
Severity 1:
93.0 → 95.0 (+2.0)

Severity 3:
85.7 → 91.8 (+6.1)

Severity 5:
73.9 → 84.1 (+10.2)

Brightness/Contrast:
Severity 1:
93.6 → 95.2 (+1.6)

Severity 3:
88.1 → 92.8 (+4.7)

Severity 5:
78.4 → 87.0 (+8.6)

JPEG:
Severity 1:
94.0 → 95.3 (+1.3)

Severity 3:
89.7 → 93.2 (+3.5)

Severity 5:
81.9 → 88.5 (+6.6)

Explain that the performance gap becomes larger under stronger degradation.

Do not overgeneralize this to real-world conditions.

--------------------------------------------------------
TABLE VII. QUALITY-GATED MULTI-FRAME ACQUISITION
--------------------------------------------------------

Random single frame:
Accepted frames = 1
Accuracy = 89.9%
Macro-F1 = 85.8%
MAE = 0.301

Best of 3, no quality gate:
Accepted frames = 3
Accuracy = 93.5%
Macro-F1 = 90.4%
MAE = 0.231

Best of 5, no quality gate:
Accepted frames = 5
Accuracy = 94.0%
Macro-F1 = 91.1%
MAE = 0.218

Quality-gated N=3:
Accepted frames = 3
Accuracy = 94.4%
Macro-F1 = 91.8%
MAE = 0.207

Quality-gated N=5:
Accepted frames = 5
Accuracy = 95.6%
Macro-F1 = 93.5%
MAE = 0.164

Clearly explain that these candidate frames are simulated/constructed if they are not genuine sequential captures.

--------------------------------------------------------
TABLE VIII. IMAGE QUALITY GATING PERFORMANCE
--------------------------------------------------------

Quality-score vs human-rating Spearman rho = 0.87
Quality classification accuracy = 91.8%
Precision for usable frames = 93.1%
Recall for usable frames = 90.6%
F1 = 91.8%
Rejection rate = 18.4%
Retained-frame classification accuracy = 95.6%
Non-gated classification accuracy = 92.8%

Interpret the quality-gating results carefully.

Do not claim that the quality score is a clinically or universally validated quality standard.

--------------------------------------------------------
TABLE IX. UNCERTAINTY ESTIMATION AND CALIBRATION
--------------------------------------------------------

Softmax baseline:
Accuracy = 92.8%
ECE = 8.9%
Brier = 0.142
NLL = 0.318
Error Detection AUROC = 0.71

MC Dropout:
Accuracy = 95.3%
ECE = 5.1%
Brier = 0.109
NLL = 0.241
Error Detection AUROC = 0.84

MC Dropout + Temperature Scaling:
Accuracy = 95.3%
ECE = 2.9%
Brier = 0.096
NLL = 0.198
Error Detection AUROC = 0.88

Deep Ensemble:
Accuracy = 95.8%
ECE = 2.5%
Brier = 0.091
NLL = 0.187
Error Detection AUROC = 0.90

IMPORTANT:

The main proposed framework uses MC Dropout unless the experimental record explicitly states otherwise.

Deep Ensemble should be presented as an alternative uncertainty/calibration experiment, NOT automatically as a component of the main framework.

--------------------------------------------------------
TABLE X. ACCURACY VS SELECTIVE PREDICTION
--------------------------------------------------------

100% coverage:
0% rejected
Accuracy = 95.3%

95% coverage:
5% rejected
Accuracy = 96.8%

90% coverage:
10% rejected
Accuracy = 97.7%

85% coverage:
15% rejected
Accuracy = 98.4%

80% coverage:
20% rejected
Accuracy = 99.0%

75% coverage:
25% rejected
Accuracy = 99.3%

CRITICAL:

These are retained-subset accuracies.

Do NOT call 99.3% the overall model accuracy.

Use terminology such as:

“accuracy at 75% coverage”

or

“retained-set accuracy under 25% rejection.”

Explain the accuracy-coverage trade-off.

--------------------------------------------------------
TABLE XI. CLASS-WISE SEVERITY PERFORMANCE
--------------------------------------------------------

Functional:
Precision = 97.4%
Recall = 98.0%
F1 = 97.7%
Support = 225

Moderate:
Precision = 84.2%
Recall = 78.9%
F1 = 81.5%
Support = 18

Mild:
Precision = 91.6%
Recall = 89.7%
F1 = 90.6%
Support = 45

Severe:
Precision = 96.0%
Recall = 96.7%
F1 = 96.3%
Support = 106

Macro Average:
Precision = 92.3%
Recall = 90.8%
F1 = 91.5%
Support = 394

These values must be checked against the confusion matrix.

Do not silently alter them.

--------------------------------------------------------
TABLE XII. CONFUSION MATRIX
--------------------------------------------------------

Functional:
220  3  2  0

Moderate:
1  15  2  0

Mild:
1  2  40  2

Severe:
0  0  3  103

Total = 394

Perform an explicit consistency check before using this table.

--------------------------------------------------------
TABLE XIII. PANEL/CELL LOCALIZATION
--------------------------------------------------------

YOLO-based localizer:

Precision = 94.2%
Recall = 93.1%
F1 = 93.6%
mAP@0.50 = 96.1%
mAP@0.50:0.95 = 84.7%
Inference FPS = 32
Localization failure rate = 4.3%

Clearly state whether the reported metrics refer to panel localization or cell localization.

Do not interchange the two terms.

--------------------------------------------------------
TABLE XIV. COMPUTATIONAL EFFICIENCY
--------------------------------------------------------

Custom CNN:
Parameters = 2.1M
Model Size = 8.4 MB
Accuracy = 89.8%
FPS = 92
Accuracy/M parameters = 42.76

MobileNetV2:
Parameters = 3.5M
Model Size = 14.0 MB
Accuracy = 93.7%
FPS = 80
Accuracy/M parameters = 26.77

EfficientNet-B0:
Parameters = 5.3M
Model Size = 21.2 MB
Accuracy = 95.6%
FPS = 68
Accuracy/M parameters = 18.04

ResNet-18:
Parameters = 11.7M
Model Size = 46.8 MB
Accuracy = 94.4%
FPS = 58
Accuracy/M parameters = 8.07

ResNet-50:
Parameters = 25.6M
Model Size = 102.4 MB
Accuracy = 95.1%
FPS = 38
Accuracy/M parameters = 3.71

Verify the formula used for accuracy/M parameters.

If the metric is not standard, label it clearly as a study-specific efficiency indicator.

Do not present it as a standard benchmark metric.

--------------------------------------------------------
TABLE XV. MAINTENANCE-PRIORITY DECISION
--------------------------------------------------------

No Action:
Precision = 97.8%
Recall = 98.5%
F1 = 98.1%
Interpretation = functional/negligible defect

Monitor:
Precision = 89.6%
Recall = 87.2%
F1 = 88.4%
Interpretation = low-risk degradation

Inspect:
Precision = 86.4%
Recall = 84.7%
F1 = 85.5%
Interpretation = uncertain/moderate-risk

High Priority:
Precision = 93.2%
Recall = 91.5%
F1 = 92.3%
Interpretation = severe + reliable prediction

Macro Average:
Precision = 91.8%
Recall = 90.5%
F1 = 91.1%

IMPORTANT:

Maintenance priority is a decision-support formulation proposed in this study.

Do NOT present these categories as an established industry standard.

Clearly explain that the priority mapping is illustrative and would require validation with domain experts and maintenance records before operational deployment.

--------------------------------------------------------
TABLE XVI. OVERALL PERFORMANCE
--------------------------------------------------------

4-class accuracy = 95.6%
Binary accuracy = 97.7%
Macro-F1 = 93.5%
Severity MAE = 0.164
QWK = 0.934
ECE = 2.9%
Error Detection AUROC = 0.88
Accuracy @ 80% coverage = 99.0%
Quality-gating Spearman rho = 0.87
Localization mAP@0.50 = 96.1%
Blur severity 5 accuracy = 80.4%
EfficientNet-B0 = 68 FPS

Again, verify consistency before final publication.

========================================================
12. REQUIRED PAPER STRUCTURE
========================================================

Produce a complete IEEE-style manuscript using approximately the following structure:

TITLE

ABSTRACT

INDEX TERMS

I. INTRODUCTION

A. Background and Motivation
B. Problem Statement
C. Limitations of Existing Approaches
D. Research Gap
E. Research Questions
F. Contributions

II. RELATED WORK

A. Conventional PV Inspection
B. Deep-Learning-Based EL Classification
C. Object Detection and Localization
D. Severity-Aware Classification
E. Uncertainty and Selective Prediction
F. Robustness and Image Quality
G. Summary of Research Gap

III. DATASET AND PROBLEM FORMULATION

A. ELPV Dataset
B. Dataset Source and Provenance
C. Class Distribution
D. Severity Formulation
E. YOLO Localization Dataset
F. Dataset Acquisition and Annotation
G. Data Preprocessing
H. Data Splitting and Leakage Prevention
I. Problem Definition

IV. PROPOSED METHODOLOGY

A. Overall Framework
B. Image Acquisition
C. YOLO-Based Localization
D. Quality-Aware Candidate Frame Selection
E. Image Quality Scoring
F. Preprocessing
G. Deep-Learning Classification
H. Ordinal Severity Prediction
I. Uncertainty Estimation
J. Selective Prediction
K. Maintenance-Priority Decision

V. EXPERIMENTAL SETUP

A. Hardware and Software
B. Dataset Split
C. Training Configuration
D. Backbone Models
E. Evaluation Metrics
F. Experimental Protocol

VI. EXPERIMENTAL DESIGN

A. Backbone Comparison
B. Categorical vs Ordinal Learning
C. Quality-Gating Ablation
D. Multi-Frame Selection
E. Robustness Evaluation
F. Uncertainty and Calibration
G. Selective Prediction
H. Computational Efficiency
I. Maintenance-Priority Evaluation

VII. RESULTS

A. Backbone Classification Results
B. Ordinal Severity Results
C. Component Ablation
D. Quality-Gated Multi-Frame Results
E. Robustness Results
F. Uncertainty and Calibration
G. Selective Prediction
H. Class-Wise Severity Results
I. YOLO Localization Results
J. Computational Efficiency
K. Maintenance-Priority Results
L. Overall Results

VIII. DISCUSSION

A. Main Findings
B. Effect of Quality Gating
C. Effect of Ordinal Learning
D. Effect of Uncertainty Estimation
E. Robustness
F. Accuracy-Efficiency Trade-Off
G. Practical Interpretation

IX. EXPLAINABILITY ANALYSIS

Include Grad-CAM or other explainability analysis ONLY if it actually exists in the experimental work.

Do not fabricate heatmaps or numerical explainability results.

If explainability was not quantitatively evaluated, describe it as qualitative analysis.

X. LIMITATIONS

Discuss:

• ELPV dataset size
• class imbalance
• grayscale EL modality
• absence of genuine multi-frame sequences
• simulated frame acquisition
• synthetic degradation
• possible module-level correlation
• YOLO/ELPV domain difference
• lack of field deployment
• lack of drone validation
• lack of maintenance-record validation
• illustrative maintenance-priority mapping

XI. CONCLUSION AND FUTURE WORK

========================================================
13. ARCHITECTURE DIAGRAM
========================================================

CRITICAL:

I WILL MANUALLY ADD THE ARCHITECTURE DIAGRAM.

DO NOT generate an image.

DO NOT create an artificial figure.

DO NOT provide a generated diagram.

Instead, insert a clear placeholder at the appropriate location:

[FIGURE 1 ABOUT HERE: OVERALL ARCHITECTURE OF THE PROPOSED SEVERITY-AWARE AND UNCERTAINTY-GUIDED SOLAR PANEL INSPECTION FRAMEWORK]

Then provide:

Figure 1. Overall architecture of the proposed framework.

The text surrounding the figure should explain the architecture so that I can manually insert my diagram.

The architecture should conceptually contain:

Image Acquisition
↓
YOLO Localization
↓
Candidate Frame Generation/Acquisition
↓
Image Quality Assessment
↓
Quality Gating
↓
Best Frame Selection
↓
Preprocessing
↓
EfficientNet-B0 / Backbone
↓
Ordinal Severity Prediction
↓
MC Dropout Uncertainty
↓
Selective Prediction
↓
Maintenance Priority

Clearly separate the localization and classification stages.

========================================================
14. TABLE AND FIGURE PLACEMENT
========================================================

Use proper IEEE-style references to tables and figures.

Examples:

“Table IV shows that EfficientNet-B0 achieves the highest four-class accuracy among the evaluated backbones.”

“Fig. 1 illustrates the overall processing pipeline.”

Do not place tables randomly.

Every table must be introduced and interpreted in the surrounding text.

Do not create tables that have no discussion.

Avoid repeating the entire table in prose.

========================================================
15. RESEARCH QUESTIONS
========================================================

Use these research questions unless the existing manuscript contains a stronger, internally consistent version:

RQ1:
Can automated localization and quality-aware acquisition improve downstream classification reliability?

RQ2:
Does ordinal severity formulation improve severity prediction compared with conventional categorical classification?

RQ3:
Can uncertainty estimation identify predictions that should be referred for human review?

RQ4:
How robust are candidate backbones under realistic image degradation?

RQ5:
What is the trade-off between predictive performance and computational cost?

Each RQ must be answered explicitly in the Results/Discussion sections.

========================================================
16. CONTRIBUTIONS
========================================================

Frame the contributions carefully.

Potential contributions:

1. An integrated solar-cell inspection framework combining localization, quality-aware candidate selection, severity-aware classification, uncertainty estimation, selective prediction, and maintenance-priority decision support.

2. An experimental evaluation of ordinal severity learning against conventional categorical classification using ELPV defect-probability labels.

3. A quality-aware candidate-frame selection strategy evaluated under simulated multi-frame conditions.

4. A systematic robustness analysis under blur, noise, brightness/contrast shifts, and JPEG compression.

5. An uncertainty and selective-prediction analysis examining calibration and accuracy-coverage trade-offs.

6. An accuracy-efficiency comparison across multiple CNN backbones.

Do not claim that any individual component is newly invented.

========================================================
17. RELATED WORK AND REFERENCES
========================================================

Use at least 20 credible references.

Prefer recent research from approximately 2022–2026 where relevant, while retaining foundational references for:

• ELPV
• CNNs
• EfficientNet
• MobileNetV2
• ResNet
• YOLO
• MC Dropout
• temperature scaling
• uncertainty estimation
• Grad-CAM
• ordinal classification

Do not fabricate citations.

Every reference must correspond to a real publication.

Verify:

• authors
• paper title
• journal/conference
• year
• volume/pages where applicable
• DOI where available

Do not cite random websites as scientific references.

For datasets, cite the original dataset publication plus the official repository/archive where appropriate.

========================================================
18. SCIENTIFIC INTERPRETATION RULES
========================================================

Use conservative interpretation.

For example:

GOOD:
“EfficientNet-B0 achieved the highest four-class accuracy among the evaluated backbones.”

BAD:
“EfficientNet-B0 is unquestionably the best model for all solar inspection applications.”

GOOD:
“The ordinal formulation reduced severity MAE from 0.213 to 0.164.”

BAD:
“The ordinal formulation solves severity prediction.”

GOOD:
“The results suggest that uncertainty-based rejection can improve accuracy on the retained subset.”

BAD:
“The system guarantees reliable predictions.”

GOOD:
“Performance degraded as synthetic corruption severity increased.”

BAD:
“The framework is robust to all real-world environmental conditions.”

========================================================
19. HUMAN ACADEMIC WRITING REQUIREMENTS
========================================================

The final manuscript must sound like a competent undergraduate/final-year research team working under academic supervision, not like a marketing document or an AI-generated survey.

Use:

• natural academic phrasing
• technically specific explanations
• moderate sentence lengths
• occasional concise sentences
• logical transitions
• direct explanations
• appropriate caution
• terminology consistent with computer-vision literature

Avoid:

• excessive buzzwords
• exaggerated claims
• repetitive paragraph structures
• unnecessarily complicated vocabulary
• generic filler
• repeated conclusions
• overly polished corporate language
• “This groundbreaking framework”
• “revolutionary”
• “highly innovative”
• “seamlessly integrates”
• “leverages cutting-edge technology”
• “unprecedented performance”

Do not artificially insert grammar mistakes.

“Humanized” means natural and credible academic writing, not deliberately poor writing.

========================================================
20. PAGE-LENGTH REQUIREMENT
========================================================

Target approximately 7–8 IEEE conference pages.

The paper must contain enough technical detail to fill the required length naturally.

Do NOT inflate the paper using:

• unnecessary repetition
• generic background
• excessive bullet points
• meaningless discussion
• repeated descriptions of tables

Prioritize space for:

• methodology
• dataset
• experimental design
• results
• discussion
• limitations

The final paper should be suitable for conversion into the IEEE two-column format.

========================================================
21. ABSTRACT REQUIREMENTS
========================================================

Write a concise IEEE-style abstract.

Include:

• problem
• limitation of conventional approaches
• proposed integrated framework
• ELPV dataset
• YOLO localization
• severity-aware classification
• uncertainty estimation
• key measured results
• significance of findings

Use actual reported results.

Do not claim field deployment.

Do not say “real-time” unless the relevant measured component supports that claim.

========================================================
22. RESULTS DISCUSSION
========================================================

The Results section must not simply reproduce tables.

For every major experiment:

1. State the main observation.
2. Give the important numerical evidence.
3. Explain what the result means.
4. Relate it to the research question.
5. Avoid overclaiming.

For example:

EfficientNet-B0 should be discussed as the strongest classification backbone in the reported experiments, achieving 95.6% four-class accuracy and 93.5% Macro-F1.

Ordinal learning should be discussed using the comparison:

Cross-Entropy:
94.7% accuracy, 92.1% Macro-F1, MAE 0.213, QWK 0.912

Ordinal:
95.6% accuracy, 93.5% Macro-F1, MAE 0.164, QWK 0.934

The improvement in MAE and QWK should be emphasized because they are directly relevant to ordered severity.

========================================================
23. UNCERTAINTY INTERPRETATION
========================================================

Explain:

Softmax baseline:
ECE 8.9%, AUROC 0.71

MC Dropout:
ECE 5.1%, AUROC 0.84

MC Dropout + Temperature Scaling:
ECE 2.9%, AUROC 0.88

Deep Ensemble:
ECE 2.5%, AUROC 0.90

Explain that uncertainty is useful for identifying cases that may require review.

Do not claim that uncertainty equals actual clinical/physical defect probability.

Do not claim perfect error detection.

========================================================
24. SELECTIVE PREDICTION INTERPRETATION
========================================================

The selective prediction experiment must be explained carefully.

The key result is:

At 80% coverage:
99.0% retained-set accuracy

At 75% coverage:
99.3% retained-set accuracy

Explain the trade-off:

Higher rejection
→ fewer predictions retained
→ higher accuracy among retained predictions

But:

Higher rejection also means fewer cases are automatically resolved.

Therefore the result demonstrates a selective-prediction trade-off rather than simply “99.3% accuracy.”

========================================================
25. ROBUSTNESS INTERPRETATION
========================================================

Discuss the degradation results progressively.

The strongest degradation effects should be noted.

For example:

Gaussian blur at severity 5:
80.4%

Noise at severity 5:
84.1%

Brightness/contrast shift at severity 5:
87.0%

JPEG compression at severity 5:
88.5%

Explain that blur has the strongest impact among these simulated conditions.

Do not generalize this result to every real-world imaging environment.

========================================================
26. COMPUTATIONAL EFFICIENCY
========================================================

Discuss the trade-off:

Custom CNN:
lowest parameter count and highest FPS, but lower accuracy.

EfficientNet-B0:
highest reported four-class accuracy while maintaining 68 FPS.

ResNet-50:
slightly lower accuracy than EfficientNet-B0 with substantially higher computational cost.

Do not claim EfficientNet-B0 is universally optimal.

Say it provides the best balance among the evaluated models in this experiment.

========================================================
27. MAINTENANCE PRIORITY
========================================================

Explain the decision-support layer carefully.

The mapping:

No Action
Monitor
Inspect
High Priority

is a research-level decision-support illustration.

It should be derived from:

• predicted severity
• uncertainty/reliability
• risk interpretation

Do not present it as an industry-standard maintenance protocol.

Clearly identify it as a framework-level decision layer that would require validation against expert inspection practices and maintenance records.

========================================================
28. LIMITATIONS MUST BE HONEST
========================================================

Do not hide limitations.

Include:

1. ELPV contains only 2,624 cell images.
2. Class imbalance exists.
3. ELPV is grayscale EL imagery.
4. ELPV does not provide genuine multi-frame inspection sequences.
5. Multi-frame experiments therefore use simulated candidate-frame construction if applicable.
6. Synthetic degradation cannot reproduce every field imaging condition.
7. Module-level correlation may affect generalization if image-level splitting was used.
8. YOLO and ELPV may come from different visual domains.
9. The study does not demonstrate complete field deployment.
10. No actual drone deployment should be claimed unless evidence exists.
11. Maintenance-priority categories require domain validation.
12. Further testing on larger, diverse, independently collected datasets is required.

These limitations should make the paper more credible, not weaker.

========================================================
29. CONCLUSION
========================================================

The conclusion should summarize:

• what was proposed
• what was experimentally evaluated
• strongest classification result
• severity result
• uncertainty result
• selective prediction result
• robustness result
• localization result
• efficiency result
• practical meaning
• limitations
• future work

Do not introduce new results in the conclusion.

Do not exaggerate.

========================================================
30. FUTURE WORK
========================================================

Recommended future directions:

• genuine multi-frame field acquisition
• module-disjoint evaluation
• larger and more diverse EL datasets
• RGB + EL multimodal inspection
• real UAV/drone validation
• domain adaptation
• expert-validated maintenance-priority rules
• calibrated uncertainty under distribution shift
• external test-set validation
• temporal consistency across video frames

Clearly label these as future work.

========================================================
31. FINAL QUALITY CONTROL
========================================================

After writing the paper, perform a final audit.

Return:

A. Metric consistency audit
B. Dataset consistency audit
C. Citation/reference audit
D. Methodology consistency audit
E. Claim-overstatement audit
F. Figure/table consistency audit
G. IEEE structure audit
H. Final paper

Check specifically:

• Does every reported number appear consistently?
• Does every table have a corresponding discussion?
• Does every figure have a caption?
• Is Figure 1 left as a manual placeholder?
• Are ELPV and YOLO datasets clearly separated?
• Is the ELPV provenance correct?
• Is the Jülich DOI correct?
• Are synthetic multi-frame experiments clearly identified?
• Are synthetic robustness transformations clearly identified?
• Is there any unsupported drone/field claim?
• Is there any unsupported “real-time” claim?
• Is the maintenance-priority layer correctly described as decision support?
• Is selective accuracy correctly described as retained-subset accuracy?
• Is MC Dropout distinguished from Deep Ensemble?
• Is the confusion matrix inconsistency explicitly identified?
• Are missing experimental details left uninvented?
• Are references real and traceable?
• Is the paper approximately 7–8 IEEE pages when formatted in two columns?

========================================================
32. FINAL OUTPUT
========================================================

Your response should contain:

PART 1
DATASET AND METRIC AUDIT

PART 2
LIST OF ISSUES THAT MUST BE RESOLVED

PART 3
RECOMMENDED CORRECTIONS

PART 4
COMPLETE FINAL IEEE PAPER

PART 5
FINAL TABLES

PART 6
FIGURE PLACEHOLDERS AND CAPTIONS

PART 7
FINAL REFERENCES

PART 8
FINAL PRE-SUBMISSION CHECKLIST

IMPORTANT:

Do not omit the complete paper because of the audit.

If there are unresolved inconsistencies, clearly mark them inside the audit and use [VERIFY] markers in the affected location of the manuscript rather than fabricating a solution.

The final manuscript must remain coherent even where verification is required.

The goal is a technically honest, natural, human-written IEEE research paper that accurately represents the experiments actually performed.

Do not fabricate.

Do not silently correct.

Do not exaggerate.

Do not merge datasets.

Do not invent field validation.

Do not generate the architecture diagram.

I will manually add the architecture diagram myself.
