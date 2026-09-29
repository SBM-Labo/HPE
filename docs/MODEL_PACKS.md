# HPE 1.4 モデル構成（標準同梱／追加モデルパック）

## 標準同梱（インストーラに含む・約1.8GB）

| ファイル | 用途 | 使うプリセット |
|---|---|---|
| rfdetr-large.onnx | 人物検出（追従が安定） | 高精度・高速 |
| vitpose-h-wholebody-fp16.onnx | 全身姿勢（最高精度） | 高精度 |
| vitpose-b-wholebody-fp16.onnx | 全身姿勢（ViTPose-H より約5倍速い） | カスタム（ViTPose-H が無い環境では高精度の代わり） |
| rtmpose-m.onnx / rtmpose-m_hand.onnx | 身体姿勢＋手指（高速） | 高速 |
| rtmdet_m.onnx | 人物検出（CPU向け・軽量） | カスタム／SynthPose |

ViTPose-H・ViTPose-B の fp16 版は fp32 版を onnxconverter-common で変換（keep_io_types=True）。
ViTPose-B の fp32 との座標差：平均 0.004px・最大 0.027px（sample.mp4 の3コマ・198点, 2026-09-27）。

## 追加モデルパック（GitHub Releases に別ファイルで配布・任意）

入手したファイルを「ヘルプ → 追加モデルのフォルダを開く」で開いたフォルダ（インストール先の `resources\Models`）に置くと、
カスタム設定・該当プリセットで選べるようになる。

| パック | ファイル | 容量 | 内容 |
|---|---|---|---|
| SynthPose | synthpose-vitpose-huge-hf.onnx | 約1.2GB | 解剖学的マーカー52点（下肢長等の研究用） |
| ViTPose-L | vitpose-l-wholebody.onnx / vitpose-l-coco.onnx / vitpose-l-coco_25.onnx | 各約1.2GB | 比較・検証用 |
| その他 | rtmw-x.onnx, rtmpose-x.onnx, vitpose-b-wholebody.onnx(fp32), yolox_x.onnx, yolox_m.onnx, rfdetr-medium.onnx | 0.1〜0.4GB | 比較・検証用 |

GitHub Releases の上限（1ファイル2GB）以内なので、各ファイルをそのまま、または ZIP にしてリリースに添付できる。
