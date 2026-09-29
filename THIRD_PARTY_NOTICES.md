# Third-Party Notices — HPE (Human Pose Estimation)

HPE (the "Software") includes the third-party software and trained models listed below.
Each component is governed by its own license, not by the terms of use of the Software (LICENSE.txt).
For the full license texts, see the bundled `licenses/` folder (Apache-2.0 / GPL-3.0) and the files provided with each component.

## 1. Trained models (standard installation)

| Model | Purpose | Source | License |
|---|---|---|---|
| RF-DETR-Large | Person detection | Roboflow RF-DETR | Apache-2.0 |
| RTMDet-M (person) | Person detection | OpenMMLab MMDetection | Apache-2.0 |
| ViTPose-H WholeBody (converted to fp16) | Whole-body pose estimation (High accuracy preset) | ViTAE-Transformer ViTPose | Apache-2.0 (code) |
| ViTPose-B WholeBody (converted to fp16) | Whole-body pose estimation | ViTAE-Transformer ViTPose | Apache-2.0 (code) |
| RTMPose-M (Halpe26) | Body pose estimation | OpenMMLab MMPose | Apache-2.0 |
| RTMPose-M hand | Hand pose estimation | OpenMMLab MMPose | Apache-2.0 |
| SynthPose-Huge (converted to fp16) | 52 anatomical markers (SynthPose preset) | Stanford MIMI SynthPose / OpenCapBench | Apache-2.0 |

All models have been converted to the ONNX format (ViTPose-H, ViTPose-B and SynthPose-Huge were also converted to fp16).

**Note on training data**: the whole-body models were trained on the COCO-WholeBody annotations.
The COCO-WholeBody annotations are provided "for research and non-commercial purposes only", and commercial use requires contacting the rights holders
(https://github.com/jin-s13/COCO-WholeBody). The training data of RTMPose (Halpe26) also includes datasets restricted to research use.
SynthPose-Huge is ViTPose fine-tuned on synthetic data (e.g., BEDLAM); the terms of each dataset apply to its training data.
Please take care when using the Software for purposes other than research and education.

## 2. Additional model packs (distributed separately, optional)

ViTPose-L, RTMW-X, YOLOX and others are not included in the standard installation. Follow the instructions provided with each additional model pack
(all are Apache-2.0 models, but the same caution about training data applies).

## 3. Executables (launched as separate processes)

| Component | License | Source code |
|---|---|---|
| FFmpeg 6.0 (via npm `ffmpeg-static` 5.2.0) | GPL-3.0-or-later | https://github.com/FFmpeg/FFmpeg/commit/ea3d24bbe3 |
| FFprobe (via npm `ffprobe-static` 3.1.0) | GPL (FFmpeg project) | https://ffmpeg.org/download.html#get-sources |

FFmpeg / FFprobe are bundled as programs independent of the Software and are invoked as separate processes.
The full text of GPL-3.0 is in `licenses/GPL-3.0.txt`. If you have trouble obtaining the source code, please contact the author (k-murata[at]andrew.ac.jp). The corresponding source code will be provided for three years from the date of distribution.

## 4. Application framework and libraries

| Component | License |
|---|---|
| Electron (including Chromium and Node.js) | MIT (Chromium licenses: `LICENSES.chromium.html`) |
| ONNX Runtime (onnxruntime-node 1.23.2) | MIT |
| DirectML (GPU inference on Windows) | Microsoft DirectML redistribution license |
| @napi-rs/canvas 1.0.0 (including Skia) | MIT (Skia: BSD-3-Clause) |
| jpeg-js 0.4.4 | BSD-3-Clause |

The full text of Apache-2.0 is in `licenses/Apache-2.0.txt`.
