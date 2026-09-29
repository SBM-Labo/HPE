# HPE 1.4 model files (standard installation / additional model packs)

## Standard installation (about 3.1 GB)

SynthPose (`synthpose-vitpose-huge-hf.onnx`) is distributed as a separate file from the installer because GitHub limits each file to 2 GB. If it is placed in the same folder as the installer, it is copied automatically during installation. All other models are included in the installer.

| File | Purpose | Used by preset |
|---|---|---|
| rfdetr-large.onnx | Person detection (stable tracking) | High accuracy, Fast |
| vitpose-h-wholebody-fp16.onnx | Whole-body pose (highest accuracy) | High accuracy |
| vitpose-b-wholebody-fp16.onnx | Whole-body pose (about 5 times faster than ViTPose-H) | Custom (replaces High accuracy where ViTPose-H is unavailable) |
| rtmpose-m.onnx / rtmpose-m_hand.onnx | Body pose + hands (fast) | Fast |
| rtmdet_m.onnx | Person detection (lightweight, for CPU) | Custom / SynthPose |
| synthpose-vitpose-huge-hf.onnx | 52 anatomical markers (for research such as segment lengths; weights converted to fp16) | SynthPose |

The fp16 versions of ViTPose-H and ViTPose-B were converted from the fp32 versions with onnxconverter-common (keep_io_types=True).
Coordinate difference of ViTPose-B from fp32: mean 0.004 px, max 0.027 px (3 frames / 198 points of sample.mp4, 2026-09-27).

## Additional model packs (distributed separately on GitHub Releases, optional)

Place the downloaded files in the folder opened by Help → "Open additional models folder" (`resources\Models` in the installation folder);
they can then be selected in the custom settings and the corresponding presets.

| Pack | Files | Size | Contents |
|---|---|---|---|
| ViTPose-L | vitpose-l-wholebody.onnx / vitpose-l-coco.onnx / vitpose-l-coco_25.onnx | about 1.2 GB each | For comparison and validation |
| Others | rtmw-x.onnx, rtmpose-x.onnx, vitpose-b-wholebody.onnx (fp32), yolox_x.onnx, yolox_m.onnx, rfdetr-medium.onnx | 0.1–0.4 GB | For comparison and validation |

Each file is within the GitHub Releases limit (2 GB per file), so it can be attached to a release as is or as a ZIP.
