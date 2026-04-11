<p align="right">
  日本語 | <a href="README.en.md">English</a>
</p>

# 🎨 Mug Advanced Halftone

<p align="left">
  <a href="https://github.com/mug-lab-3/mug-advanced-halftone/releases"><img src="https://img.shields.io/github/v/release/mug-lab-3/mug-advanced-halftone?label=version&color=orange" alt="Latest Version"></a> <a href="https://github.com/mug-lab-3/mug-advanced-halftone/blob/main/LICENSE"><img src="https://img.shields.io/github/license/mug-lab-3/mug-advanced-halftone?color=blue" alt="License"></a> <a href="https://github.com/mug-lab-3/mug-advanced-halftone/releases"><img src="https://img.shields.io/github/downloads/mug-lab-3/mug-advanced-halftone/total?label=downloads&color=green" alt="Downloads"></a> <a href="https://github.com/mug-lab-3/mug-advanced-halftone/releases/latest"><img src="https://img.shields.io/badge/Release--Notes-latest-blue?logo=github" alt="Release Notes"></a>
</p>
<p align="center">
  <img src="images/sample.jpg" alt="MugAdvancedHalftone sample" width="600">
</p>

## 📝 概要
`MugAdvancedHalftone` は、DaVinci Resolve / Fusion 向けのハーフトーン生成プラグインです
網点、コミック風、ドット絵、レトロPC、サーマルカメラなどの質感をシミュレートします

### ✨ 主な機能
- **グリッド**: 六角形（ハニカム）配置による自然な網点
- **ドット形状**: 円形、四角形、ひし形、線、クロスハッチ
- **揺らぎ（Jitter）**: 位置・サイズ・縦横比・アングルの個別のランダム化
- **カラー**: 16色パレット等の制限、版ズレ（RGB Shift）の再現
- **描画制御**: アンチエイリアス、輝度反転、ドットゲイン調整

---

## 📦 インストール

本エフェクトを使用するには、以下のファイルをOSごとの所定フォルダに配置してください

| ファイル | 必須 | 用途 | 配置先フォルダ |
| :--- | :---: | :--- | :--- |
| [**MugAdvancedHalftone.fuse**](https://github.com/mug-lab-3/mug-advanced-halftone/releases/latest/download/MugAdvancedHalftone.fuse) | **必須** | プラグイン本体 (Fusion用) | `Fuses` |
| [**MugAdvancedHalftone.setting**](https://github.com/mug-lab-3/mug-advanced-halftone/releases/latest/download/MugAdvancedHalftone.setting) | **必須** | Editページ表示用プリセット | `Templates/Edit/Effects` |
| [**MugAdvancedHalftone.png**](https://github.com/mug-lab-3/mug-advanced-halftone/releases/latest/download/MugAdvancedHalftone.png) | 任意 | アイコン画像 | `Templates/Edit/Effects` |

### 配置フォルダのパス

#### 📂 Fuses フォルダ (`.fuse` を配置)

**Windows**
```text
%AppData%\Blackmagic Design\DaVinci Resolve\Support\Fusion\Fuses\
```

**macOS**
```text
~/Library/Application Support/Blackmagic Design/DaVinci Resolve/Fusion/Fuses/
```

**Linux**
```text
~/.local/share/BlackmagicDesign/DaVinciResolve/Fusion/Fuses/
```

#### 📂 Templates/Edit/Effects フォルダ (`.setting` と `.png` を配置)

**Windows**
```text
%AppData%\Blackmagic Design\DaVinci Resolve\Support\Fusion\Templates\Edit\Effects\
```

**macOS**
```text
~/Library/Application Support/Blackmagic Design/DaVinci Resolve/Fusion/Templates/Edit/Effects/
```

**Linux**
```text
~/.local/share/BlackmagicDesign/DaVinciResolve/Fusion/Templates/Edit/Effects/
```

---

## ⚙️ パラメータ

<details>
<summary><b>クリックしてパラメータ詳細を表示 / Click to expand Parameter Reference</b></summary>

| セクション | パラメータ | 説明 |
| :--- | :--- | :--- |
| **Global** | Screen Density | ドットの細かさ |
| | Contrast | 元画像のコントラスト調整 |
| | Invert Brightness | 明暗の反転（Subtractive Mode） |
| | Margin X | ドットの横方向の間隔調整 |
| | Margin Y | ドットの縦方向の間隔調整 |
| | Screen Aspect Ratio | スクリーンの縦横比（パターン全体の歪み） |
| **Dot Shape** | Dot Shape | ドットの形状 |
| | Staggered Grid | 千鳥配置（オフでストレート配置） |
| | Line Angle | 線・網線の角度 |
| | Dot Gain | ドットの太り |
| | Dot Size Curve | サイズの成長曲線 |
| | Cutoff Dot Radius | 描画する最小の半径 |
| | Clip Dot Radius | 最大サイズの制限 |
| | Enable Antialias | 境界のぼかし処理 |
| **Dot Jitter** | Jitter Noise Phase| アニメーションの位相 |
| | Position Jitter | 位置のランダムなズレ |
| | Size Jitter | サイズのランダムなムラ |
| | Aspect Jitter | 縦横比のランダムな歪み |
| | Angle Jitter | 角度のランダムな回転 |
| **Dot Color** | Use Original Color| 元画像の色をドットに使用 |
| | Color Reduction | カラーパレットの制限 |
| | RGB Shift | 版ズレ・色収差の強さ |
| | Dot Color | 指定色の設定 |
| **Background** | Blend With Input | 元の画像に直接合成 |
| | Paper Color | 背景色（紙の色） |

</details>

---

## ⚖️ ライセンス
本プロジェクトは **MITライセンス** のもとで公開されています
詳細は [LICENSE](./LICENSE) ファイルをご確認ください

> [!NOTE]
> **映像制作者の方へ / Note for Video Creators:**
> 本ソフトウェアを使用して制作された映像作品（ビデオコンテンツ）において、著作権表示やクレジットの記載は任意であり、必須ではありません。商用・非商用問わず、自由にお使いください！
> You do NOT need to include copyright notices or credits in your video works (rendered outputs) created using this Fuse. Feel free to use it for both commercial and non-commercial projects!

### ✅ やっていいこと（OK）
- **商用利用**: Youtube動画や広告、映画などの制作に自由に使用できます
- **改変**: Fuseファイルの中身を書き換えて自分好みに調整できます
- **再配布**: 規約を守れば、自分のサイトなどで紹介・配布できます（ただし、著作権表示が必要です）

### ❌ やってはいけないこと（NG）
- **無保証**: このプラグインの使用によって生じたいかなる損害についても、作者は責任を負いません
- **著作権表示の削除**: ソースコード内にある作者名やライセンス条項を消してはいけません

---
 
## 📜 更新履歴

### v2.33 (2026/04/06)
- **縁（エッジ）の描画安定化**: 画像の端や、透過背景上の文字の周りに不自然なドット（縁取り）が出る現象を修正しました。
- **サンプリング精度の向上**: より正確に画素の色を拾うように内部処理を改善し、端部まで安定した描画が行われるようになりました。

### v2.30 (2026/04/05)
- **UI構成の再編**: `AspectRatio` パラメータを `Dot Shape` から `Global` セクションへ移動し、`Screen Aspect Ratio` に改名しました。これにより、スクリーン全体の密度バランスとしてのアスペクト比調整がより直感的になりました。

### v2.21 (2026/04/05)
- **パフォーマンス最適化**: GPUカーネルの分岐を排除（`_mix`活用）し、数学演算（`_fmaf`等）を組み込み関数へ置き換えることで実行効率を向上。
- **保守性向上**: 各カーネルを論理的なステップ（Step 1〜4）に構造化し、コメントによる解説を拡充しました。
- **安定性改修**: ホスト側(Fuse)との互換性を確保しつつ、内部演算をベクトル化する最適なバランスへ調整しました。

### v2.10 (2026/04/02)

---

## 🔗 リンク
- [<img src="https://cdn.simpleicons.org/youtube" width="16" height="16"> **YouTube: Mug Lab**](https://www.youtube.com/@MugLab3)
- [<picture><source media="(prefers-color-scheme: dark)" srcset="https://cdn.simpleicons.org/github/white"><img src="https://cdn.simpleicons.org/github/black" width="16" height="16"></picture> **GitHub: Mug Advanced Halftone**](https://github.com/mug-lab-3/mug-advanced-halftone)
- [<picture><source media="(prefers-color-scheme: dark)" srcset="https://cdn.simpleicons.org/x/white"><img src="https://cdn.simpleicons.org/x/black" width="16" height="16"></picture> **X: @MugLab3**](https://x.com/MugLab3)
