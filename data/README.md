# Data Plan — SafetyVision

## Where our data comes from
Our primary data source is Roboflow Universe, which hosts several public, free PPE
(personal protective equipment) detection datasets. We will start from one or more of these
and, if needed, add a small number of our own labeled photos to cover cases the public data misses.

## Details
- Source: Roboflow Universe (public PPE datasets), plus optional self-collected images
- Approximate size: 3,000 to 6,000 labeled images (free tier)
- Labels / classes: hard hat, safety vest, safety glasses, person, and negative cases (for example "no-helmet" and "no-vest")
- Format: images with bounding-box annotations (YOLO format)
- Cost: $0 — free tier and open source only

## How we will use it
1. Demo first: run a pretrained YOLO11 on a handful of sample images to confirm the pipeline works.
2. Fine-tune: use transfer learning to adapt YOLO11 to our PPE classes.
3. Augment if needed: apply flips, brightness, and similar augmentations to balance under-represented classes.
4. Hold-out split: keep a validation set to measure mAP@0.5 honestly.

## Notes
We are building an application, not just collecting a dataset. Data is one ingredient; the goal is a
working PPE compliance tool. We will not spend weeks on data before the pipeline runs.
