# SafetyVision — PPE Compliance System

A computer vision proof of concept that detects Personal Protective Equipment (PPE) in images
and reports whether the required safety gear is present. Built for ITAI 1378 (Computer Vision and AI).

**Author:** Hnin Aung  |  **Tier:** 2  |  **Course:** ITAI 1378

## Demo Video
[Paste your YouTube (Unlisted) or Google Drive link here]

## What It Does
SafetyVision takes an image of a work area, uses a fine-tuned YOLO11 detector to find PPE items
(hard hat, vest, and others), then a compliance component checks each image against the required
gear and reports **COMPLIANT** or **VIOLATION**, listing anything missing.

## How It Works (as built)
- **Technique:** object detection + a rule-based compliance component
- **Model:** YOLO11 (nano), fine-tuned with transfer learning
- **Framework:** PyTorch + Ultralytics
- **Architecture:** convolutional neural network (CNN)
- **Compliance rule:** required items are hard hat and vest; the system flags any that are missing

## Data
- **Source:** public PPE dataset on Roboflow Universe (CC BY 4.0)
- **Classes:** Hard_hat, Vest, Gloves, Mask, Person, Safety_boots
- **Splits:** train / validation / test (the test split is used for the honest accuracy check)

## Results (measured on the unseen test split)
| Metric | Blueprint target | Achieved |
|---|---|---|
| Detection quality (mAP@0.5) | >= 0.80 | **0.862** (target met) |
| Speed per image | < 1 second | **~5 ms** (0.005 s) |
| Compliance decision | flags missing PPE | working end to end |

Measured on the unseen **test split**: mAP@0.5 = **0.862**, precision 0.792, recall 0.905, ~5 ms per image. Both Blueprint targets were exceeded.

## What Changed From the Blueprint
- Used a ready-made public Roboflow PPE dataset instead of collecting my own, to focus on the working system.
- Scoped compliance to **per image** for the proof of concept; per-person association is the next step.
- Kept YOLO11 nano for speed on free Colab; a larger model is an easy upgrade.

## How to Run
1. Open the notebook in Google Colab.
2. Set the runtime to a T4 GPU (Runtime -> Change runtime type -> T4 GPU).
3. Add your free Roboflow API key in the dataset cell.
4. Run all cells. Training, evaluation, inference, and the compliance report run end to end.

## Next Steps
- Associate each PPE item with a specific person.
- Run on live video with per-worker tracking and alerts.
- Add more classes and a larger model for higher accuracy.
