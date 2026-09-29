# Model Licenses

Licenses of the machine learning models bundled with or used by this application (HPE 1.4).
The model **code** is all under Apache-2.0-type licenses. The terms of the training data are separate; see the notes below.
The notice for users is in `THIRD_PARTY_NOTICES.md`.

Last checked: 2026-09-27

## Standard models (included in the installation)

| Role | Model | Origin | License |
|---|---|---|---|
| Person detection (default) | `rfdetr-large.onnx` | [RF-DETR (Roboflow)](https://github.com/roboflow/rf-detr) | **Apache-2.0** |
| Person detection (lightweight) | `rtmdet_m.onnx` | [RTMDet / MMDetection](https://github.com/open-mmlab/mmdetection) (person-specific weights via the [facebook/sapiens-pose-bbox-detector](https://huggingface.co/facebook/sapiens-pose-bbox-detector) mirror, converted to ONNX with mmdeploy) | **Apache-2.0** |
| Pose estimation (high accuracy) | `vitpose-h-wholebody-fp16.onnx` | [ViTPose](https://github.com/ViTAE-Transformer/ViTPose) (fp32 converted to fp16) | **Apache-2.0** (code) |
| Pose estimation (standard) | `vitpose-b-wholebody-fp16.onnx` | [ViTPose](https://github.com/ViTAE-Transformer/ViTPose) (fp32 converted to fp16) | **Apache-2.0** (code) |
| Pose estimation (fast, body) | `rtmpose-m.onnx` | [RTMPose / MMPose](https://github.com/open-mmlab/mmpose) | **Apache-2.0** |
| Hand pose (fast, hand) | `rtmpose-m_hand.onnx` | [RTMPose / MMPose](https://github.com/open-mmlab/mmpose) | **Apache-2.0** |
| Pose estimation (52 anatomical markers) | `synthpose-vitpose-huge-hf.onnx` | [SynthPose / OpenCapBench (Stanford MIMI)](https://huggingface.co/stanfordmimi/synthpose-vitpose-huge-hf) (based on ViTPose-Huge; converted to ONNX with fp16 weights) | **Apache-2.0** (weights; fine-tuned on synthetic data such as BEDLAM; the terms of each dataset apply to the training data) |

## Additional model packs (distributed separately, optional)

| Model | Origin | License |
|---|---|---|
| `vitpose-l-*.onnx` / `vitpose-b-wholebody.onnx` (fp32) | ViTPose | Apache-2.0 (code) |
| `rtmw-x.onnx` / `rtmpose-x.onnx` | RTMW, RTMPose / MMPose | Apache-2.0 |
| `yolox_x.onnx` / `yolox_m.onnx` | [YOLOX (Megvii)](https://github.com/Megvii-BaseDetection/YOLOX) | Apache-2.0 |
| `rfdetr-medium.onnx` | RF-DETR (Roboflow) | Apache-2.0 |

## Excluded models (for license reasons)

| Model | Origin | License | Reason |
|---|---|---|---|
| `yolo26x` / `yolo26m` (previously used) | [Ultralytics YOLO](https://github.com/ultralytics/ultralytics) | **AGPL-3.0** | Distribution or network use creates an **obligation to publish the source code of the whole application**; avoiding it requires a paid Enterprise License. Unsuitable for a published application, so **excluded on 2026-06-06**. |

> The Ultralytics models (YOLOv8/v11, "yolo26", etc.) are AGPL-3.0. They may be used internally for research, but **cannot be distributed or offered as SaaS as closed source**. The detectors of this application are only the Apache-2.0 RF-DETR and RTMDet (and YOLOX in an additional pack).

## Notes

- **Terms of the training data**: the whole-body models (ViTPose WholeBody, RTMW) were trained on the COCO-WholeBody annotations, which are limited to research and non-commercial purposes. The training data of RTMPose (Halpe26) also includes datasets restricted to research use. The terms of use of the application itself (free for research, education and personal use; contact the author for commercial use) reflect this.
- The table above lists the **code** licenses of each repository. Redistribution terms of the **trained weights** may differ from the code, so also check the terms of the distributor (GitHub Releases, Hugging Face, etc.).
- Apache-2.0 obligations: distributions must **include the full license text** and **state copyright and changes (NOTICE)**. This application does so with `licenses/Apache-2.0.txt` and `THIRD_PARTY_NOTICES.md` (fp16 conversion and ONNX conversion are stated as changes).
- Dependencies such as the inference runtime [onnxruntime](https://github.com/microsoft/onnxruntime) (MIT), [Electron](https://github.com/electron/electron) (MIT) and FFmpeg (ffmpeg-static, GPL-3.0) have their own licenses (`THIRD_PARTY_NOTICES.md`).
