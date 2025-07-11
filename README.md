# ハイライト検出

本プロジェクトでは、**自然画像におけるハイライト領域のセグメンテーション**を目的として、U-Net アーキテクチャを用いた二値マスク予測モデルを実装しています。

---

## 🔧 モデル構造

使用している U-Net の構成は以下の通りです：

### エンコーダー（Downsampling）
- Conv2D → ReLU → MaxPooling
- 段数：4段（チャンネル数は段階的に増加）

### ボトルネック
- Conv2D（1層）

### デコーダー（Upsampling）
- ConvTranspose2D（アップサンプリング）
- Concat（スキップ接続）
- Conv2D
- 段数：4段（チャンネル数は段階的に減少）

### 出力層
- 1x1 Conv → Sigmoid による二値マスク出力

---

## ⚙️ 損失関数・最適化

- **損失関数**：`nn.BCELoss()`  
- **最適化手法**：`Adam`  
  - 学習率：`1e-4`

---

## 📈 評価指標

以下の2つの指標でモデル性能を評価しています：

- **IoU（Intersection over Union）**  
- **Dice Coefficient（F1スコア）**

---

## ✅ 結果

予測結果の可視化例を以下に示します：

<p align="center">
  <img width="1142" height="397" alt="Prediction 1" src="https://github.com/user-attachments/assets/243d2c21-83e9-44e8-8e9e-3eb373474182" />
</p>

<p align="center">
  <img width="1142" height="397" alt="download" src="https://github.com/user-attachments/assets/e4fe1a29-65ce-45b3-b9ec-af3865b174b7" />
</p>

<p align="center">
  <img width="1142" height="397" alt="download" src="https://github.com/user-attachments/assets/206c88d8-b474-4bc2-8487-90449e6bf6b5" />
</p>

---
