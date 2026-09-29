# HPE（Human Pose Estimation）

動画・画像から人物の骨格（23点の関節座標）を推定する Windows 用デスクトップアプリです。
Python は不要で、インストールするだけで最新の姿勢推定モデル（ViTPose-H など）を使えます。

A free Windows desktop application for human pose estimation (23 keypoints) from video and images. No Python required.

**[⬇ 最新版をダウンロード（Releases）](https://github.com/SBM-Labo/HPE/releases/latest)**

## できること

- 画像・動画から人体 23 点（手先・足部・頭頂などを含む）を推定。多人数にも対応します。
- 人物追跡：ByteTrack（原著実装の忠実な移植）と、すれ違い時の ID の付け替わりを直す ID 補修。
- 補正・平滑化：左右の取り違えの補正（脚・腕・足部）、外れ値の補正、欠損の補間、平滑化（Butterworthフィルタ。遮断周波数は Winter の残差分析で自動決定）。
- 身体重心（COM）の算出・表示（阿江・岡田・横井の身体部分慣性係数）。
- 骨格のオーバーレイ表示、グラフでの時系列確認と手動修正、現在フレームの再推定。
- CSV・骨格付き動画（MP4）・画像（PNG）の書き出し、複数ファイルのバッチ処理。

### 計測プリセット

| プリセット | 人物検出 | 姿勢推定 | 特徴 |
|---|---|---|---|
| 高精度（既定） | RF-DETR-L | ViTPose-H Wholebody（fp16） | 研究用の標準。手動デジタイズとの誤差 6.2px |
| 高速 | RF-DETR-L | RTMPose-M ＋ 手指モデル | 高精度より高速 |
| カスタム | 任意 | 任意 | 同梱モデルから組み合わせを選択 |

解剖学的マーカー 52 点の SynthPose などは、追加モデルパック（別配布）で使えます。

## 動作環境

- 64 ビット版 Windows 10 / 11
- GPU（DirectML 対応）があれば自動で使います。使えない場合は CPU で動きます（時間はかかります）。
- インストールには 2.5GB 以上の空き容量が必要です（姿勢推定モデル約 1.8GB を含みます）。

## インストール

1. [Releases](https://github.com/SBM-Labo/HPE/releases/latest) から、次の **2 つのファイルを両方** ダウンロードし、同じフォルダに置きます。
   - `HPE-Setup-<版>.exe`（インストーラー本体）
   - `HPE-Setup-<版>.nsisbin`（モデルなどのデータ。サイズが大きいため別ファイルになっています）
2. `HPE-Setup-<版>.exe` を実行し、利用規約に同意してインストールします。
3. 「Windows によって PC が保護されました」と表示された場合は、**詳細情報** → **実行** を押してください（本アプリはコード署名をしていないため、この表示が出ます）。

## 利用規約

本ソフトウェアは、**研究・教育・個人での利用に限り無償**で利用できます。営利目的での利用を希望する場合は、事前に作者へご連絡ください。
再配布・改変は禁止しています（このページへのリンクによる紹介は歓迎します）。詳しくは [LICENSE.txt](LICENSE.txt) をご覧ください。

同梱の第三者ソフトウェア・学習済みモデルには、それぞれのライセンスが適用されます（[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)、[モデルのライセンス](docs/MODEL_LICENSES.md)）。
全身姿勢推定モデルの学習データ（COCO-WholeBody など）は研究・非商用目的に限定されています。研究・教育以外の目的で利用する場合はご注意ください。

## 引用

本ソフトウェアを用いた研究成果を発表する際は、次のように引用してください（[CITATION.cff](CITATION.cff)）。

> Murata, K. HPE: Human Pose Estimation (Version 1.4.0) [Computer software]. SBM_Labo. https://github.com/SBM-Labo/HPE

## 不具合の報告・問い合わせ

- 不具合の報告・要望：[Issues](https://github.com/SBM-Labo/HPE/issues)
- 連絡先：村田 和隆（桃山学院大学 人間教育学部）k-murata@andrew.ac.jp

© 2026 Kazutaka Murata (SBM_Labo)
