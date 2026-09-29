# モデルライセンス一覧 / Model Licenses

本アプリ（HPE 1.4）が同梱・使用する機械学習モデルのライセンス一覧です。
モデルの**コード**はすべて Apache-2.0 系で構成しています。ただし学習データの利用条件は別で、後述の注意事項を参照してください。
利用者向けの表記は `THIRD_PARTY_NOTICES.md` にまとめています。

最終確認日: 2026-09-27

## 標準同梱モデル（インストーラに含む）

| 役割 | モデル | 由来 | ライセンス |
|---|---|---|---|
| 人物検出（既定） | `rfdetr-large.onnx` | [RF-DETR (Roboflow)](https://github.com/roboflow/rf-detr) | **Apache-2.0** |
| 人物検出（軽量） | `rtmdet_m.onnx` | [RTMDet / MMDetection](https://github.com/open-mmlab/mmdetection)（person特化weights は [facebook/sapiens-pose-bbox-detector](https://huggingface.co/facebook/sapiens-pose-bbox-detector) ミラー経由, mmdeployでONNX化） | **Apache-2.0** |
| 姿勢推定（高精度） | `vitpose-h-wholebody-fp16.onnx` | [ViTPose](https://github.com/ViTAE-Transformer/ViTPose)（fp32版を fp16 に変換） | **Apache-2.0**（コード） |
| 姿勢推定（標準） | `vitpose-b-wholebody-fp16.onnx` | [ViTPose](https://github.com/ViTAE-Transformer/ViTPose)（fp32版を fp16 に変換） | **Apache-2.0**（コード） |
| 姿勢推定（高速・body） | `rtmpose-m.onnx` | [RTMPose / MMPose](https://github.com/open-mmlab/mmpose) | **Apache-2.0** |
| 手指推定（高速・hand） | `rtmpose-m_hand.onnx` | [RTMPose / MMPose](https://github.com/open-mmlab/mmpose) | **Apache-2.0** |

## 追加モデルパック（別配布・任意）

| モデル | 由来 | ライセンス |
|---|---|---|
| `vitpose-l-*.onnx` / `vitpose-b-wholebody.onnx`（fp32） | ViTPose | Apache-2.0（コード） |
| `rtmw-x.onnx` / `rtmpose-x.onnx` | RTMW・RTMPose / MMPose | Apache-2.0 |
| `yolox_x.onnx` / `yolox_m.onnx` | [YOLOX (Megvii)](https://github.com/Megvii-BaseDetection/YOLOX) | Apache-2.0 |
| `rfdetr-medium.onnx` | RF-DETR (Roboflow) | Apache-2.0 |
| `synthpose-vitpose-huge-hf.onnx` | SynthPose（ViTPoseベース, HuggingFace） | ViTPoseベース（※上流の重み配布条件は要確認） |

## 除外したモデル（ライセンス上の理由）

| モデル | 由来 | ライセンス | 除外理由 |
|---|---|---|---|
| `yolo26x` / `yolo26m`（旧採用） | [Ultralytics YOLO](https://github.com/ultralytics/ultralytics) | **AGPL-3.0** | 配布・ネット公開で**アプリ全体のソース公開義務**が発生。回避には有償 Enterprise License が必要。公開アプリに不適のため **2026-06-06 に除外**。 |

> Ultralytics 系（YOLOv8/v11/「yolo26」等）は AGPL-3.0。研究内部利用は可能でも、**クローズドソースのまま配布・SaaS提供はできません**。本アプリの検出器は Apache-2.0 の RF-DETR・RTMDet（追加パックで YOLOX）のみです。

## 注意事項

- **学習データの利用条件**：全身（Wholebody）モデル（ViTPose Wholebody・RTMW）は COCO-WholeBody アノテーションで学習されており、COCO-WholeBody は研究・非商用目的に限られます。RTMPose（Halpe26）の学習データにも研究目的に限定されたデータセットが含まれます。アプリ本体の利用規約（研究・教育・個人は無償、商用は要連絡）はこれを踏まえたものです。
- 上表は各リポジトリの **コード**ライセンスです。**学習済み重み**の再配布条件はコードと異なる場合があるため、配布元（GitHub Releases / HuggingFace 等）の利用条件も確認してください。
- Apache-2.0 の義務: 配布物に **ライセンス全文の同梱**と**著作権・変更点の表示（NOTICE）**が必要です。本アプリは `licenses/Apache-2.0.txt` と `THIRD_PARTY_NOTICES.md` で対応しています（fp16 変換・ONNX 化を変更点として記載）。
- 推論基盤 [onnxruntime](https://github.com/microsoft/onnxruntime)（MIT）、[Electron](https://github.com/electron/electron)（MIT）、FFmpeg（ffmpeg-static, GPL-3.0）等の依存にも別途ライセンスがあります（`THIRD_PARTY_NOTICES.md`）。
