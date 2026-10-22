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

- **SIFT** - Extracts local descriptors invariant to scale and rotation for matching objects or scenes across images; robustness to viewpoint and illumination changes is empirical, not unlimited invariance. [Lowe 2004](<https://link.springer.com/article/10.1023/B:VISI.0000029664.99615.94> "Distinctive Image Features from Scale-Invariant Keypoints; IJCV").
- **Histograms of oriented gradients** - Pools local gradient orientations with overlapping block normalization. The human-detection study isolates how spatial binning, orientation resolution, and contrast normalization affect recognition. [Dalal and Triggs 2005](<https://lear.inrialpes.fr/people/triggs/pubs/Dalal-cvpr05.pdf> "Histograms of Oriented Gradients for Human Detection; CVPR").
- **SuperPoint** - Jointly predicts interest points and descriptors from full images; Homographic Adaptation supplies self-supervision for repeatable matching across transformed views. [DeTone et al. 2018](<https://arxiv.org/abs/1712.07629> "SuperPoint: Self-Supervised Interest Point Detection and Description; CVPR DL4VSLAM Workshop").
- **SuperGlue** - Uses attention and a graph neural network to predict matching costs, then differentiable optimal transport to assign local features and reject unmatched points. [Sarlin et al. 2020](<https://arxiv.org/abs/1911.11763> "SuperGlue: Learning Feature Matching with Graph Neural Networks; CVPR").
- **LoFTR** - Matches images without a separate keypoint detector: cross-image attention establishes coarse correspondences, then refines selected matches at higher resolution. [Sun et al. 2021](<https://arxiv.org/abs/2104.00680> "LoFTR: Detector-Free Local Feature Matching with Transformers; CVPR").

## Classification backbones

- **AlexNet** - Trains a deep convolutional classifier on ImageNet using GPU computation, non-saturating neurons, and regularization; a reference for large-scale supervised visual learning. [Krizhevsky et al. 2012](<https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks> "ImageNet Classification with Deep Convolutional Neural Networks; NeurIPS").
- **VGG** - Studies depth using stacks of small 3×3 convolution filters; provides classification networks whose learned representations transfer to other image datasets. [Simonyan and Zisserman 2014](<https://arxiv.org/abs/1409.1556> "Very Deep Convolutional Networks for Large-Scale Image Recognition; arXiv").
- **ResNet** - Learns residual functions relative to layer inputs, easing optimization of deep networks. The paper evaluates recognition and transfers the backbone to detection. [He et al. 2015](<https://arxiv.org/abs/1512.03385> "Deep Residual Learning for Image Recognition; arXiv").
- **DenseNet** - Feeds each layer the feature maps of preceding layers within densely connected blocks, promoting feature reuse and short paths for information and gradients. [Huang et al. 2017](<https://arxiv.org/abs/1608.06993> "Densely Connected Convolutional Networks; CVPR").
- **EfficientNet** - Scales network depth, width, and input resolution together using a compound coefficient; combines this scaling rule with a searched convolutional baseline. [Tan and Le 2019](<https://arxiv.org/abs/1905.11946> "EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks; ICML").
- **Vision Transformer** - Applies a Transformer to image-patch sequences. The study emphasizes large-scale pretraining and transfer rather than assuming attention needs less data than convolutions. [Dosovitskiy et al. 2020](<https://arxiv.org/abs/2010.11929> "An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale; arXiv").
- **DeiT** - Trains image Transformers on ImageNet without external training data; an attention-based distillation token transfers knowledge from a teacher, including a convolutional teacher. [Touvron et al. 2020](<https://arxiv.org/abs/2012.12877> "Training data-efficient image transformers &amp; distillation through attention; arXiv").
- **Swin Transformer** - Builds hierarchical image features using local attention windows shifted between layers. Cross-window connections retain spatial interaction while limiting attention cost. [Liu et al. 2021](<https://arxiv.org/abs/2103.14030> "Swin Transformer: Hierarchical Vision Transformer using Shifted Windows; ICCV").
- **ConvNeXt** - Revisits convolutional design by progressively modifying a ResNet toward choices used in visual Transformers; supplies convolutional backbones for classification and dense prediction. [Liu et al. 2022](<https://arxiv.org/abs/2201.03545> "A ConvNet for the 2020s; CVPR").

## Learning reusable visual features

- **SimCLR** - Learns representations through contrastive prediction between augmented image views. The study isolates augmentation composition, a nonlinear projection head, and batch size as consequential choices. [Chen et al. 2020](<https://arxiv.org/abs/2002.05709> "A Simple Framework for Contrastive Learning of Visual Representations; ICML").
- **BYOL** - Trains an online network to predict a moving-average target network's representation of another augmented view, without explicit negative pairs. [Grill et al. 2020](<https://arxiv.org/abs/2006.07733> "Bootstrap your own latent: A new approach to self-supervised Learning; NeurIPS").
- **DINO** - Uses self-distillation without labels, a momentum encoder, and multiple crops. Studies semantic structure in Transformer features and evaluates them with nearest-neighbor and linear classifiers. [Caron et al. 2021](<https://arxiv.org/abs/2104.14294> "Emerging Properties in Self-Supervised Vision Transformers; ICCV").
- **Masked autoencoders** - Encodes only visible image patches and uses a lightweight decoder to reconstruct missing pixels; separates representation learning from the full reconstruction network. [He et al. 2022](<https://arxiv.org/abs/2111.06377> "Masked Autoencoders Are Scalable Vision Learners; CVPR").
- **DINOv2** - Combines curated image data, scaled self-supervised training, and model distillation to produce reusable features evaluated at image and pixel levels. [Oquab et al. 2023](<https://arxiv.org/abs/2304.07193> "DINOv2: Learning Robust Visual Features without Supervision; arXiv").
- **DINOv3** - Introduces Gram anchoring to address deterioration of dense features during long self-supervised training; studies scaling and post-training adaptation of visual representations. [Siméoni et al. 2025](<https://arxiv.org/abs/2508.10104> "DINOv3; arXiv").
- **CLIP** - Learns from paired images and text by predicting which captions match which images. Text descriptions specify classes for zero-shot transfer without fitting a task-specific classifier. [Radford et al. 2021](<https://arxiv.org/abs/2103.00020> "Learning Transferable Visual Models From Natural Language Supervision; ICML").

## Object detection

- **R-CNN** - Applies convolutional features to bottom-up region proposals; transfers supervised pretraining to detection through domain-specific fine-tuning. [Girshick et al. 2014](<https://arxiv.org/abs/1311.2524> "Rich feature hierarchies for accurate object detection and semantic segmentation; CVPR").
- **Fast R-CNN** - Builds on region-based convolutional detection to classify object proposals more efficiently; studies training and inference improvements over R-CNN and SPPnet. [Girshick 2015](<https://arxiv.org/abs/1504.08083> "Fast R-CNN; ICCV").
- **Faster R-CNN** - Learns region proposals with a network that shares image features with the detector, replacing a separate proposal-generation algorithm. [Ren et al. 2015](<https://arxiv.org/abs/1506.01497> "Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks; NeurIPS").
- **YOLO** - Predicts bounding boxes and class probabilities directly from a full image in one network evaluation, framing detection as joint regression rather than proposal classification. [Redmon et al. 2015](<https://arxiv.org/abs/1506.02640> "You Only Look Once: Unified, Real-Time Object Detection; arXiv").
- **SSD** - Predicts class scores and offsets for default boxes at multiple feature-map resolutions, handling different object scales without a separate proposal stage. [Liu et al. 2016](<https://arxiv.org/abs/1512.02325> "SSD: Single Shot MultiBox Detector; LNCS").
- **Feature pyramid networks** - Combines a top-down pathway with lateral connections to construct semantically rich features at multiple resolutions for detecting objects at different scales. [Lin et al. 2017](<https://arxiv.org/abs/1612.03144> "Feature Pyramid Networks for Object Detection; CVPR").
- **RetinaNet and focal loss** - Downweights well-classified examples in cross-entropy training so abundant easy background examples do not dominate a dense detector's loss. [Lin et al. 2017](<https://arxiv.org/abs/1708.02002> "Focal Loss for Dense Object Detection; ICCV").
- **DETR** - Treats detection as set prediction: learned object queries and bipartite matching produce unique predictions without anchor generation or non-maximum suppression. [Carion et al. 2020](<https://arxiv.org/abs/2005.12872> "End-to-End Object Detection with Transformers; arXiv").
- **Deformable DETR** - Restricts attention to a small set of sampling points around each reference point, addressing DETR's training convergence and high-resolution feature limitations. [Zhu et al. 2021](<https://arxiv.org/abs/2010.04159> "Deformable DETR: Deformable Transformers for End-to-End Object Detection; ICLR").
- **Grounding DINO** - Combines a DINO object detector with language-guided queries and cross-modal fusion to detect objects specified by category names or referring expressions. [Liu et al. 2023](<https://arxiv.org/abs/2303.05499> "Grounding DINO: Marrying DINO with Grounded Pre-Training for Open-Set Object Detection; arXiv").

## Semantic, instance, and prompted segmentation

- **Fully convolutional networks** - Adapts classification networks to pixelwise prediction; combines deep coarse semantics with shallower spatial detail to produce segmentation maps for variable-sized images. [Long et al. 2015](<https://arxiv.org/abs/1411.4038> "Fully Convolutional Networks for Semantic Segmentation; CVPR").
- **U-Net** - Combines a contracting context path with a symmetric expanding localization path. The biomedical study uses strong augmentation to train from limited annotated images. [Ronneberger et al. 2015](<https://arxiv.org/abs/1505.04597> "U-Net: Convolutional Networks for Biomedical Image Segmentation; arXiv").
- **DeepLab** - Uses atrous convolution and spatial pyramid pooling for multiscale semantic segmentation; a fully connected conditional random field refines object boundaries. [Chen et al. 2016](<https://arxiv.org/abs/1606.00915> "DeepLab: Semantic Image Segmentation with Deep Convolutional Nets, Atrous Convolution, and Fully Connected CRFs; arXiv").
- **Mask R-CNN** - Adds a parallel mask-prediction branch to Faster R-CNN, producing a separate segmentation mask for each detected object instance. [He et al. 2017](<https://arxiv.org/abs/1703.06870> "Mask R-CNN; ICCV").
- **Mask2Former** - Constrains cross-attention to predicted mask regions. A shared architecture supports semantic, instance, and panoptic segmentation through their different grouping targets. [Cheng et al. 2022](<https://arxiv.org/abs/2112.01527> "Masked-attention Mask Transformer for Universal Image Segmentation; CVPR").
- **Segment Anything** - Trains a promptable segmentation model alongside a model-assisted mask collection process; evaluates transfer to new distributions and tasks without task-specific training. [Kirillov et al. 2023](<https://arxiv.org/abs/2304.02643> "Segment Anything; ICCV").
- **SAM 2** - Extends promptable segmentation to images and videos with a Transformer using streaming memory; couples model development with interactive video-mask collection. [Ravi et al. 2024](<https://arxiv.org/abs/2408.00714> "SAM 2: Segment Anything in Images and Videos; arXiv").

## Video and motion

- **Two-stream networks** - Combines spatial appearance and temporal motion networks for action recognition; the temporal stream learns from stacked dense optical-flow fields. [Simonyan and Zisserman 2014](<https://arxiv.org/abs/1406.2199> "Two-Stream Convolutional Networks for Action Recognition in Videos; NeurIPS").
- **I3D** - Inflates 2D convolution and pooling kernels into 3D to learn video features while reusing image-model designs and parameters; introduces the Kinetics action dataset. [Carreira and Zisserman 2017](<https://arxiv.org/abs/1705.07750> "Quo Vadis, Action Recognition? A New Model and the Kinetics Dataset; CVPR").
- **SlowFast** - Pairs a low-frame-rate pathway for spatial semantics with a lightweight high-frame-rate pathway for motion, separating temporal resolution from channel capacity. [Feichtenhofer et al. 2018](<https://arxiv.org/abs/1812.03982> "SlowFast Networks for Video Recognition; arXiv").
- **RAFT** - Builds multiscale all-pairs pixel correlation volumes and recurrently updates an optical-flow field by querying those correlations. [Teed and Deng 2020](<https://arxiv.org/abs/2003.12039> "RAFT: Recurrent All-Pairs Field Transforms for Optical Flow; arXiv").
- **CoTracker** - Jointly tracks multiple 2D points with a transformer that models dependencies between tracks, using windowed inference to extend trajectories through video and occlusions. [Karaev et al. 2023](<https://arxiv.org/abs/2307.07635> "CoTracker: It is Better to Track Together; arXiv").

## Geometry and scene representations

- **Structure-from-Motion revisited** - Develops an incremental reconstruction pipeline for unordered image collections, addressing robustness, accuracy, completeness, and scalability; releases the pipeline as open-source software. [Schonberger and Frahm 2016](<https://openaccess.thecvf.com/content_cvpr_2016/html/Schonberger_Structure-From-Motion_Revisited_CVPR_2016_paper.html> "Structure-From-Motion Revisited; CVPR").
- **PointNet** - Processes point clouds directly while respecting invariance to input-point ordering; supports object classification, part segmentation, and scene labeling without voxelizing the input. [Qi et al. 2017](<https://arxiv.org/abs/1612.00593> "PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation; CVPR").
- **NeRF** - Fits a continuous field of volume density and view-dependent radiance to posed images; differentiable volume rendering synthesizes new views of the fitted scene. [Mildenhall et al. 2020](<https://arxiv.org/abs/2003.08934> "NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis; ECCV").
- **Instant neural graphics primitives** - Augments a small neural network with trainable multiresolution hash-table features; optimized GPU kernels support efficient fitting and evaluation of neural graphics representations. [Müller et al. 2022](<https://arxiv.org/abs/2201.05989> "Instant Neural Graphics Primitives with a Multiresolution Hash Encoding; ACM Trans. Graph.").
- **3D Gaussian splatting** - Represents a scene with optimized anisotropic Gaussians, interleaves parameter fitting with density control, and renders through visibility-aware splatting. [Kerbl et al. 2023](<https://arxiv.org/abs/2308.04079> "3D Gaussian Splatting for Real-Time Radiance Field Rendering; arXiv").
- **2D Gaussian splatting** - Represents surfaces with oriented planar Gaussian disks; ray-splat intersections and depth/normal regularization address geometry inconsistency in volumetric Gaussian representations. [Huang et al. 2024](<https://arxiv.org/abs/2403.17888> "2D Gaussian Splatting for Geometrically Accurate Radiance Fields; SIGGRAPH").
- **DUSt3R** - Predicts paired pointmaps without supplied camera calibration or poses; aligns these maps into a common frame for reconstruction from multiple images. [Wang et al. 2024](<https://arxiv.org/abs/2312.14132> "DUSt3R: Geometric 3D Vision Made Easy; CVPR").
- **VGGT** - Uses a feed-forward network to infer camera parameters, depth, pointmaps, and point tracks from scene views, combining several geometric prediction tasks in one model. [Wang et al. 2025](<https://arxiv.org/abs/2503.11651> "VGGT: Visual Geometry Grounded Transformer; CVPR").
- **Depth Anything V2** - Trains a depth teacher on synthetic labels, then students on pseudo-labeled real images. Produces relative monocular depth; metric-depth models require separate fine-tuning. [Yang et al. 2024](<https://arxiv.org/abs/2406.09414> "Depth Anything V2; NeurIPS").

## Evaluation and dataset shift

- **COCO** - Introduces everyday scenes with object-instance segmentation annotations and detection baselines, moving recognition evaluation toward objects in context. [Lin et al. 2014](<https://arxiv.org/abs/1405.0312> "Microsoft COCO: Common Objects in Context; arXiv").
- **LVIS** - Evaluates large-vocabulary instance segmentation with a long tail of rare categories. Category frequency exposes failures hidden by aggregate accuracy; the original paper motivates evaluation where many categories have few labeled instances. [Gupta et al. 2019](<https://arxiv.org/abs/1908.03195> "LVIS: A Dataset for Large Vocabulary Instance Segmentation; arXiv").
- **TIDE detection diagnostics** - Separates six detection/segmentation error types and estimates their effects on average precision. Classification, localization and missed detections can yield the same headline score; the decomposition uses counterfactual error corrections. [Bolya et al. 2020](<https://arxiv.org/abs/2008.08115> "TIDE: A General Toolbox for Identifying Object Detection Errors; arXiv").
- **Perceptual similarity and LPIPS** - Evaluates deep-feature distances against human judgments of image similarity. Results concern the studied perceptual comparisons; classification accuracy alone is not the evaluation target. [Zhang et al. 2018](<https://arxiv.org/abs/1801.03924> "The Unreasonable Effectiveness of Deep Features as a Perceptual Metric; CVPR").
- **ImageNet-C and ImageNet-P** - Benchmark image classifiers under common corruptions and perturbations. These tests measure a different robustness setting from worst-case adversarial attacks. [Hendrycks and Dietterich 2019](<https://arxiv.org/abs/1903.12261> "Benchmarking Neural Network Robustness to Common Corruptions and Perturbations; ICLR").
- **ImageNet replication** - Recreates CIFAR-10 and ImageNet test sets and observes accuracy drops despite similar collection procedures; probes generalization beyond repeatedly reused benchmark images. [Recht et al. 2019](<https://arxiv.org/abs/1902.10811> "Do ImageNet Classifiers Generalize to ImageNet?; arXiv").
- **Dynamic view synthesis evaluation** - Shows how monocular-video protocols can contain effective multiview signals; proposes co-visibility-aware image metrics and correspondence evaluation to expose this dependence. [Gao et al. 2022](<https://arxiv.org/abs/2210.13445> "Monocular Dynamic View Synthesis: A Reality Check; NeurIPS").

## Related topics

- [Neural Networks](https://mlpapers.org/neural-nets/)
- [Generative Models](https://mlpapers.org/generative-models/)
- [NLP](https://mlpapers.org/nlp/)
