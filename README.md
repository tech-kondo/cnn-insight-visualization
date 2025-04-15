# CNN Feature Evolution & Layer Visualization

![自動生成カーネルの畳み込み可視化](/assets/inu_tf_auto_kernel_c.png)

このリポジトリは、畳み込みニューラルネットワーク（CNN）の仕組みを視覚的に理解するために、
**各レイヤー（Conv, Pooling, Flatten, Dense）や学習前後の変化**を可視化・比較した学習用プロジェクトです。

---

## 🧠 学びの目的

01. 畳み込み層でのフィルターの働きを視覚的に理解する
-自作カーネルで畳み込みを行いカーネルの数値がどのように作用するかを視覚化
-TensorFlowのConv2Dの自動生成カーネルで畳み込みを行い1との特徴マップの違いを比較
-TensorFlowのConv2Dの自動生成カーネルの形状を可視化
（未）02. プーリング層での情報圧縮の様子を確認する
（未）03. Flatten → Dense層での構造変化を確認する
（未）04. CNNの学習によって**フィルターがどのように変化するか**を比較する

---

## 📁 ディレクトリ構成

cnn-insight-visualization/
├──────── README.md  # このファイル
├──────── assets/  # 可視化のピクチャフォルダ
├────── data/
│  ├─ input/ # 入力画像
│  │       ├──inu_color_256.jpg      # 入力画像（カラー画像）
│  │       └── inu_grayscale_256.jpg              # 入力画像（グレースケール画像）
│  ├────kernels/   # 3*3のカーネルを視覚化のため100倍に拡大した画像
│  │     ├─ self_made      # 自作カーネル画像
│  │     │     ├── my_kernel_ Vertical_Edge.png      # 左から右へ縦のエッジを強調カーネル
│  │     │     ├── my_kernel_ Horizontal_Edge.png    # 上から下へ横のエッジを強調カーネル
│  │     │     └── my_kernel_ Diagonal_Edge.png      # 左下から右上へ斜めのエッジを強調カーネル
│  │     └── TensorFlow_auto     # TF自動生成カーネル画像
│  │            ├── 01_auto_kernel_01_color.png & gray.png      # カラーとグレースケールそれぞれの自動生成カーネル
│  │            └── ..._auto_kernel_..._color.png & gray.png
│  └── outputs/
│  │       └── feature_map # 特徴マップの出力画像
│  │          ├── self_made_filters  # 自作カーネルを畳み込み後の特徴マップ
│  │          │ ├── 1_feature_map_my_kernel_Vertical_Edge_color.png & gray.png # カラー画像とグレースケール画像
│  │          │ ├── 2_feature_map_my_kernel_Horizontal_Edge_color.png & gray.png
│  │          │ └── 3_feature_map_my_kernel_Diagonal_Edge_color.png & gray.png
│  │          └── TensorFlow_auto_filters     # TFによる自動生成カーネルを畳み込み後の特徴マップ
│  │             ├── 01_feature_map_auto_filter_01_color.png & gray.png   # カラー画像とグレースケール画像
│  │             └── …_feature_map_auto_filter_..._color.png & gray.png
├──── notebooks/
│        ├──── 01_manual_filters.ipynb # 自作カーネル・Conv2D層それぞれの畳み込み処理の出力を可視化
│        ├──── （空）02_pooling__visualization.ipynb # プーリング層の出力可視化
│        ├──── （空）03_flatten_dense_layer.ipynb # Flatten → Dense構造の確認
│        ├──── （空）04_feature_map_evolution.ipynb # 学習前 と 学習後の特徴マップを比較
│        └── （空）05_summary.ipynb # 各ステップまとめ
└── scripts/  # ローカルから実行できるpythonスクリプト（を今後追加予定）
└── requirements.txt # 使用ライブラリ

---

## 🎨 含まれる可視化例（一部紹介）

- **自作エッジフィルター（垂直・水平・斜め）による特徴検出**
- **TensorFlow自動生成フィルターによる畳み込み出力**
（未）- **MaxPooling処理前後の比較**
（未）- **学習前後でのフィルター出力の進化（feature evolution）**

---

## 💬 メモ

このプロジェクトはCNNの処理の内容を具体的にイメージして説明できるよう学習のために始めました。
1層ずつ分解し実際に手を動かしながら実行して確認することで、出力の構造を知ることができました。
このプロジェクトにより、今まで自分にとってブラックボックスであった
「特徴量を認識していくメカニズム」について理解が深まってきたように感じています。

今後は、このプロジェクトで得た知見を土台として、
より複雑なネットワークへの応用や、モデルに応じた適切なチューニングが出来るように
可視化を重ねて理解を深めていきます🧩

---

## ▶️ 実行方法

1. `requirements.txt` に記載された環境を整える（TensorFlow, matplotlib, OpenCVなど）
2. 各ノートブック（`notebooks/`）をGoogle Colabなどで順番に実行してください
