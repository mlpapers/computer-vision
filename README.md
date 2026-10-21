---
title: "Computer Vision"
aliases: ["CV", "Image Recognition", "Visual Computing"]
tags:
  - computer-vision
  - deep-learning
  - image-processing
---
# Computer Vision

## Descriptors and correspondence

- **[SIFT](https://link.springer.com/article/10.1023/B:VISI.0000029664.99615.94)** — 2004. Extracts local descriptors invariant to scale and rotation for matching objects or scenes across images; robustness to viewpoint and illumination changes is empirical, not unlimited invariance.
- **[Histograms of oriented gradients](https://lear.inrialpes.fr/people/triggs/pubs/Dalal-cvpr05.pdf)** — 2005. Pools local gradient orientations with overlapping block normalization. The human-detection study isolates how spatial binning, orientation resolution, and contrast normalization affect recognition.
- **[SuperPoint](https://arxiv.org/abs/1712.07629)** — 2017. Jointly predicts interest points and descriptors from full images; Homographic Adaptation supplies self-supervision for repeatable matching across transformed views.
- **[SuperGlue](https://arxiv.org/abs/1911.11763)** — 2019. Uses attention and a graph neural network to predict matching costs, then differentiable optimal transport to assign local features and reject unmatched points.
- **[LoFTR](https://arxiv.org/abs/2104.00680)** — 2021. Matches images without a separate keypoint detector: cross-image attention establishes coarse correspondences, then refines selected matches at higher resolution.

## Classification backbones

- **[AlexNet](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks)** — 2012. Trains a deep convolutional classifier on ImageNet using GPU computation, non-saturating neurons, and regularization; a reference for large-scale supervised visual learning.
- **[VGG](https://arxiv.org/abs/1409.1556)** — 2014. Studies depth using stacks of small 3×3 convolution filters; provides classification networks whose learned representations transfer to other image datasets.
- **[ResNet](https://arxiv.org/abs/1512.03385)** — 2015. Learns residual functions relative to layer inputs, easing optimization of deep networks. The paper evaluates recognition and transfers the backbone to detection.
- **[DenseNet](https://arxiv.org/abs/1608.06993)** — 2016. Feeds each layer the feature maps of preceding layers within densely connected blocks, promoting feature reuse and short paths for information and gradients.
- **[EfficientNet](https://arxiv.org/abs/1905.11946)** — 2019. Scales network depth, width, and input resolution together using a compound coefficient; combines this scaling rule with a searched convolutional baseline.
- **[Vision Transformer](https://arxiv.org/abs/2010.11929)** — 2020. Applies a Transformer to image-patch sequences. The study emphasizes large-scale pretraining and transfer rather than assuming attention needs less data than convolutions.
- **[DeiT](https://arxiv.org/abs/2012.12877)** — 2020. Trains image Transformers on ImageNet without external training data; an attention-based distillation token transfers knowledge from a teacher, including a convolutional teacher.
- **[Swin Transformer](https://arxiv.org/abs/2103.14030)** — 2021. Builds hierarchical image features using local attention windows shifted between layers. Cross-window connections retain spatial interaction while limiting attention cost.
- **[ConvNeXt](https://arxiv.org/abs/2201.03545)** — 2022. Revisits convolutional design by progressively modifying a ResNet toward choices used in visual Transformers; supplies convolutional backbones for classification and dense prediction.

## Learning reusable visual features

- **[SimCLR](https://arxiv.org/abs/2002.05709)** — 2020. Learns representations through contrastive prediction between augmented image views. The study isolates augmentation composition, a nonlinear projection head, and batch size as consequential choices.
- **[BYOL](https://arxiv.org/abs/2006.07733)** — 2020. Trains an online network to predict a moving-average target network's representation of another augmented view, without explicit negative pairs.
- **[DINO](https://arxiv.org/abs/2104.14294)** — 2021. Uses self-distillation without labels, a momentum encoder, and multiple crops. Studies semantic structure in Transformer features and evaluates them with nearest-neighbor and linear classifiers.
- **[Masked autoencoders](https://arxiv.org/abs/2111.06377)** — 2021. Encodes only visible image patches and uses a lightweight decoder to reconstruct missing pixels; separates representation learning from the full reconstruction network.
- **[DINOv2](https://arxiv.org/abs/2304.07193)** — 2023. Combines curated image data, scaled self-supervised training, and model distillation to produce reusable features evaluated at image and pixel levels.
- **[DINOv3](https://arxiv.org/abs/2508.10104)** — 2025. Introduces Gram anchoring to address deterioration of dense features during long self-supervised training; studies scaling and post-training adaptation of visual representations.
- **[CLIP](https://arxiv.org/abs/2103.00020)** — 2021. Learns from paired images and text by predicting which captions match which images. Text descriptions specify classes for zero-shot transfer without fitting a task-specific classifier.

## Object detection

- **[R-CNN](https://arxiv.org/abs/1311.2524)** — 2013. Applies convolutional features to bottom-up region proposals; transfers supervised pretraining to detection through domain-specific fine-tuning.
- **[Fast R-CNN](https://arxiv.org/abs/1504.08083)** — 2015. Builds on region-based convolutional detection to classify object proposals more efficiently; studies training and inference improvements over R-CNN and SPPnet.
- **[Faster R-CNN](https://arxiv.org/abs/1506.01497)** — 2015. Learns region proposals with a network that shares image features with the detector, replacing a separate proposal-generation algorithm.
- **[YOLO](https://arxiv.org/abs/1506.02640)** — 2015. Predicts bounding boxes and class probabilities directly from a full image in one network evaluation, framing detection as joint regression rather than proposal classification.
- **[SSD](https://arxiv.org/abs/1512.02325)** — 2015. Predicts class scores and offsets for default boxes at multiple feature-map resolutions, handling different object scales without a separate proposal stage.
- **[Feature pyramid networks](https://arxiv.org/abs/1612.03144)** — 2016. Combines a top-down pathway with lateral connections to construct semantically rich features at multiple resolutions for detecting objects at different scales.
- **[RetinaNet and focal loss](https://arxiv.org/abs/1708.02002)** — 2017. Downweights well-classified examples in cross-entropy training so abundant easy background examples do not dominate a dense detector's loss.
- **[DETR](https://arxiv.org/abs/2005.12872)** — 2020. Treats detection as set prediction: learned object queries and bipartite matching produce unique predictions without anchor generation or non-maximum suppression.
- **[Deformable DETR](https://arxiv.org/abs/2010.04159)** — 2020. Restricts attention to a small set of sampling points around each reference point, addressing DETR's training convergence and high-resolution feature limitations.
- **[Grounding DINO](https://arxiv.org/abs/2303.05499)** — 2023. Combines a DINO object detector with language-guided queries and cross-modal fusion to detect objects specified by category names or referring expressions.

## Semantic, instance, and prompted segmentation

- **[Fully convolutional networks](https://arxiv.org/abs/1411.4038)** — 2014. Adapts classification networks to pixelwise prediction; combines deep coarse semantics with shallower spatial detail to produce segmentation maps for variable-sized images.
- **[U-Net](https://arxiv.org/abs/1505.04597)** — 2015. Combines a contracting context path with a symmetric expanding localization path. The biomedical study uses strong augmentation to train from limited annotated images.
- **[DeepLab](https://arxiv.org/abs/1606.00915)** — 2016. Uses atrous convolution and spatial pyramid pooling for multiscale semantic segmentation; a fully connected conditional random field refines object boundaries.
- **[Mask R-CNN](https://arxiv.org/abs/1703.06870)** — 2017. Adds a parallel mask-prediction branch to Faster R-CNN, producing a separate segmentation mask for each detected object instance.
- **[Mask2Former](https://arxiv.org/abs/2112.01527)** — 2021. Constrains cross-attention to predicted mask regions. A shared architecture supports semantic, instance, and panoptic segmentation through their different grouping targets.
- **[Segment Anything](https://arxiv.org/abs/2304.02643)** — 2023. Trains a promptable segmentation model alongside a model-assisted mask collection process; evaluates transfer to new distributions and tasks without task-specific training.
- **[SAM 2](https://arxiv.org/abs/2408.00714)** — 2024. Extends promptable segmentation to images and videos with a Transformer using streaming memory; couples model development with interactive video-mask collection.

## Video and motion

- **[Two-stream networks](https://arxiv.org/abs/1406.2199)** — 2014. Combines spatial appearance and temporal motion networks for action recognition; the temporal stream learns from stacked dense optical-flow fields.
- **[I3D](https://arxiv.org/abs/1705.07750)** — 2017. Inflates 2D convolution and pooling kernels into 3D to learn video features while reusing image-model designs and parameters; introduces the Kinetics action dataset.
- **[SlowFast](https://arxiv.org/abs/1812.03982)** — 2018. Pairs a low-frame-rate pathway for spatial semantics with a lightweight high-frame-rate pathway for motion, separating temporal resolution from channel capacity.
- **[RAFT](https://arxiv.org/abs/2003.12039)** — 2020. Builds multiscale all-pairs pixel correlation volumes and recurrently updates an optical-flow field by querying those correlations.
- **[CoTracker](https://arxiv.org/abs/2307.07635)** — 2023. Jointly tracks multiple 2D points with a transformer that models dependencies between tracks, using windowed inference to extend trajectories through video and occlusions.

## Geometry and scene representations

- **[Structure-from-Motion revisited](https://openaccess.thecvf.com/content_cvpr_2016/html/Schonberger_Structure-From-Motion_Revisited_CVPR_2016_paper.html)** — 2016. Develops an incremental reconstruction pipeline for unordered image collections, addressing robustness, accuracy, completeness, and scalability; releases the pipeline as open-source software.
- **[PointNet](https://arxiv.org/abs/1612.00593)** — 2016. Processes point clouds directly while respecting invariance to input-point ordering; supports object classification, part segmentation, and scene labeling without voxelizing the input.
- **[NeRF](https://arxiv.org/abs/2003.08934)** — 2020. Fits a continuous field of volume density and view-dependent radiance to posed images; differentiable volume rendering synthesizes new views of the fitted scene.
- **[Instant neural graphics primitives](https://arxiv.org/abs/2201.05989)** — 2022. Augments a small neural network with trainable multiresolution hash-table features; optimized GPU kernels support efficient fitting and evaluation of neural graphics representations.
- **[3D Gaussian splatting](https://arxiv.org/abs/2308.04079)** — 2023. Represents a scene with optimized anisotropic Gaussians, interleaves parameter fitting with density control, and renders through visibility-aware splatting.
- **[2D Gaussian splatting](https://arxiv.org/abs/2403.17888)** — 2024. Represents surfaces with oriented planar Gaussian disks; ray-splat intersections and depth/normal regularization address geometry inconsistency in volumetric Gaussian representations.
- **[DUSt3R](https://arxiv.org/abs/2312.14132)** — 2023. Predicts paired pointmaps without supplied camera calibration or poses; aligns these maps into a common frame for reconstruction from multiple images.
- **[VGGT](https://arxiv.org/abs/2503.11651)** — 2025. Uses a feed-forward network to infer camera parameters, depth, pointmaps, and point tracks from scene views, combining several geometric prediction tasks in one model.
- **[Depth Anything V2](https://arxiv.org/abs/2406.09414)** — 2024. Trains a depth teacher on synthetic labels, then students on pseudo-labeled real images. Produces relative monocular depth; metric-depth models require separate fine-tuning.

## Evaluation and dataset shift

- **[COCO](https://arxiv.org/abs/1405.0312)** — 2014. Introduces everyday scenes with object-instance segmentation annotations and detection baselines, moving recognition evaluation toward objects in context.
- **[LVIS](https://arxiv.org/abs/1908.03195)** — 2019. Evaluates large-vocabulary instance segmentation with a long tail of rare categories. Category frequency exposes failures hidden by aggregate accuracy; the original paper motivates evaluation where many categories have few labeled instances.
- **[TIDE detection diagnostics](https://arxiv.org/abs/2008.08115)** — 2020. Separates six detection/segmentation error types and estimates their effects on average precision. Classification, localization and missed detections can yield the same headline score; the decomposition uses counterfactual error corrections.
- **[Perceptual similarity and LPIPS](https://arxiv.org/abs/1801.03924)** — 2018. Evaluates deep-feature distances against human judgments of image similarity. Results concern the studied perceptual comparisons; classification accuracy alone is not the evaluation target.
- **[ImageNet-C and ImageNet-P](https://arxiv.org/abs/1903.12261)** — 2019. Benchmark image classifiers under common corruptions and perturbations. These tests measure a different robustness setting from worst-case adversarial attacks.
- **[ImageNet replication](https://arxiv.org/abs/1902.10811)** — 2019. Recreates CIFAR-10 and ImageNet test sets and observes accuracy drops despite similar collection procedures; probes generalization beyond repeatedly reused benchmark images.
- **[Dynamic view synthesis evaluation](https://arxiv.org/abs/2210.13445)** — 2022. Shows how monocular-video protocols can contain effective multiview signals; proposes co-visibility-aware image metrics and correspondence evaluation to expose this dependence.

## Related Topics

- [Neural Networks](https://mlpapers.org/neural-nets/)
- [Generative Models](https://mlpapers.org/generative-models/)
- [NLP](https://mlpapers.org/nlp/)
