# Third-Party Notices — HPE (Human Pose Estimation)

HPE（以下「本ソフトウェア」）には、以下の第三者ソフトウェアおよび学習済みモデルが含まれています。
各コンポーネントには、本ソフトウェアの利用規約（LICENSE.txt）ではなく、それぞれのライセンスが適用されます。
ライセンス全文は同梱の `licenses/` フォルダ（Apache-2.0 / GPL-3.0）および各コンポーネント付属のファイルを参照してください。

## 1. 学習済みモデル（標準同梱）

| モデル | 用途 | 出典 | ライセンス |
|---|---|---|---|
| RF-DETR-Large | 人物検出 | Roboflow RF-DETR | Apache-2.0 |
| RTMDet-M（person） | 人物検出 | OpenMMLab MMDetection | Apache-2.0 |
| ViTPose-H Wholebody（fp16 に変換） | 全身姿勢推定（高精度プリセット） | ViTAE-Transformer ViTPose | Apache-2.0（コード） |
| ViTPose-B Wholebody（fp16 に変換） | 全身姿勢推定 | ViTAE-Transformer ViTPose | Apache-2.0（コード） |
| RTMPose-M（Halpe26） | 身体姿勢推定 | OpenMMLab MMPose | Apache-2.0 |
| RTMPose-M hand | 手指推定 | OpenMMLab MMPose | Apache-2.0 |
| SynthPose-Huge（fp16 に変換） | 解剖学的マーカー52点（SynthPose プリセット） | Stanford MIMI SynthPose / OpenCapBench | Apache-2.0 |

各モデルは ONNX 形式への変換（ViTPose-H・ViTPose-B・SynthPose-Huge は fp16 化）を行っています。

**学習データについての注意**：全身（Wholebody）モデルは COCO-WholeBody アノテーションで学習されています。
COCO-WholeBody のアノテーションは「研究・非商用目的に限る」とされており、商用利用には権利者への連絡が必要です
（https://github.com/jin-s13/COCO-WholeBody）。RTMPose（Halpe26）の学習データにも研究目的に限定された
データセットが含まれます。SynthPose-Huge は ViTPose を合成データ（BEDLAM など）で追加学習したモデルで、
学習データの利用条件は各データセットに従います。本ソフトウェアを研究・教育以外の目的で利用する場合はご注意ください。

## 2. 追加モデルパック（別配布・任意）

ViTPose-L、RTMW-X、YOLOX 等は標準インストールに含まれません。追加モデルパックに同梱の説明に従ってください
（いずれも Apache-2.0 のモデルですが、上記と同様に学習データの利用条件にご注意ください）。

## 3. 実行ファイル（別プロセスとして起動）

| コンポーネント | ライセンス | ソースコード |
|---|---|---|
| FFmpeg 6.0（npm `ffmpeg-static` 5.2.0 経由） | GPL-3.0-or-later | https://github.com/FFmpeg/FFmpeg/commit/ea3d24bbe3 |
| FFprobe（npm `ffprobe-static` 3.1.0 経由） | GPL（FFmpeg プロジェクト） | https://ffmpeg.org/download.html#get-sources |

FFmpeg / FFprobe は本ソフトウェアとは独立したプログラムとして同梱され、別プロセスとして呼び出されます。
GPL-3.0 の全文は `licenses/GPL-3.0.txt` にあります。ソースコードの入手に問題がある場合は作者（k-murata[at]andrew.ac.jp）までご連絡ください。配布日から3年間、対応するソースコードを提供します。

## 4. アプリケーション基盤・ライブラリ

| コンポーネント | ライセンス |
|---|---|
| Electron（Chromium, Node.js を含む） | MIT（Chromium の各ライセンスは `LICENSES.chromium.html`） |
| ONNX Runtime（onnxruntime-node 1.23.2） | MIT |
| DirectML（Windows 版の GPU 推論） | Microsoft DirectML 再配布ライセンス |
| @napi-rs/canvas 1.0.0（Skia を含む） | MIT（Skia: BSD-3-Clause） |
| jpeg-js 0.4.4 | BSD-3-Clause |

Apache-2.0 の全文は `licenses/Apache-2.0.txt` にあります。
