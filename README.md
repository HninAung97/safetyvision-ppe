# SafetyVision — PPE Compliance System

## Team Members
- Hnin Aung
- May Pang Kue

## Project Tier
Tier 2 (Advanced): a YOLO11 detection model feeds a compliance-reporting component, so two parts work together to turn raw detections into a per-worker violations report.

## Problem Statement
On construction and manufacturing sites, workers must wear personal protective equipment (PPE) such as hard hats, safety vests, and glasses. Compliance is checked manually by a safety officer who cannot watch everyone at once, so missing gear often goes unnoticed until an injury, lost work time, or a regulatory fine occurs. Safety managers and the companies they work for need a faster, more consistent way to catch violations.

## Solution Overview
SafetyVision takes a photo (or camera frame) of a work area, detects each worker and their PPE, checks each worker against the required gear, and produces a simple violations report. This lets one safety officer effectively monitor a whole site and catch problems before they become injuries.

## Technical Approach
- CV Technique: Object Detection (plus a rule-based compliance-reporting component)
- Model Architecture: Convolutional neural network (CNN)
- Model: YOLO11
- How we will use it: Transfer learning (fine-tune YOLO11 on PPE categories)
- Framework: PyTorch with the Ultralytics library
- Why this approach: YOLO11 is the current free, open-source, real-time detection standard, and transfer learning lets us teach it our PPE categories with a small dataset. The compliance component turns raw detections into the report a safety officer actually needs, which makes this a two-part Tier 2 system.

## Dataset
- Source: Public PPE datasets on Roboflow Universe, plus a small set of our own labeled photos
- Size: Roughly 3,000 to 6,000 labeled images (free tier)
- Labels: hard hat, safety vest, safety glasses, person (including "no-helmet" / "no-vest" negative cases)
- Link: Roboflow Universe PPE datasets (public, free to download)

## Success Metrics (what we will measure and expect)
- Primary: We will measure mean Average Precision at IoU 0.5 (mAP@0.5) and expect at least 0.80 on our validation set.
- Secondary: We will measure inference speed and expect under 1 second per image on free Colab hardware.

## Milestone Plan (10-week summer term)
| Phase | Goal | When |
|---|---|---|
| Blueprint | Plan approved, midterm submitted | Week 5 |
| First Working Demo | Pretrained YOLO11 runs end to end on a few sample images | Week 6 |
| Make It Yours | Fine-tune on PPE data; add compliance-report logic | Weeks 7-8 |
| Improve & Measure | Test, fix, and measure against our success metrics | Week 9 |
| Package & Present | Demo video, README, final slides | Week 10 |

## Resources
- Compute: Google Colab (free tier, T4 GPU)
- Cost: $0 (free tier and open source only)

## Risks and Mitigation
| Risk | Probability | Plan B |
|---|---|---|
| PPE data is limited or imbalanced | Medium | Combine several Roboflow PPE datasets and use data augmentation (flips, brightness) to expand and balance the classes. |
| Model misses small items such as glasses | Medium | Scope the core system to hard hats and vests first (larger, easier to detect), and add glasses only once the core works reliably. |

## Demo Video
[Link goes here at the Final]

## AI Usage Log
See docs/AI_usage_log.md

## Current Status
- [x] Repository created
- [ ] Proposal submitted
- [ ] First working demo
- [ ] System works on our data
- [ ] Metrics measured
- [ ] Final submitted
