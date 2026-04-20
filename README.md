# ❓ 疑問詞クイズ | Question Words Quiz

小〜中学生向けの疑問詞（Question Words）を瞬時に判断するPOPなクイズゲーム。

## 特徴

- **13種類の疑問詞に対応**: What / Who / Where / When / Why / How / How long / How much / How many / How often / How old / Which / Whose
- **全50問**（1セット10問をランダム出題）
- **2つのモード**
  - 📖 **疑問詞の導入**: 各疑問詞の意味と例文をネイティブ音声付きで学習
  - 🎮 **クイズ**: 画像＋答えから疑問詞を当てる
- **講師側で出題範囲を選択可能**（チェックボックス方式）
- **ネイティブ音声**（Web Speech API）で例文を読み上げ
- **POPなデザイン** - 明るいカラー、バウンス/シェイクアニメーション、大きな丸ボタン
- **モバイルファースト** - スマホ・タブレット最適化
- **単一ファイル構成** - 外部依存ゼロでVercelデプロイが安定

## デプロイ方法 (GitHub → Vercel)

1. このリポジトリをGitHubに push
2. Vercel ダッシュボードで「New Project」→ このリポジトリを選択
3. **Framework Preset**: `Other` を選択（フレームワーク指定不要）
4. **Root Directory**: そのまま（`/`）
5. **Build Command**: 空欄のまま
6. **Output Directory**: 空欄のまま
7. Deploy！

`index.html` はリポジトリルートに配置されているため、Vercelが自動で静的サイトとして配信します。

## ファイル構成

```
/
├── index.html      # アプリ本体（単一ファイル）
├── vercel.json     # Vercel設定
└── README.md       # このファイル
```

## ローカル確認

```bash
# 任意のローカルサーバーで
python3 -m http.server 8000
# または
npx serve .
```
ブラウザで `http://localhost:8000` を開く。

## カスタマイズ

### 問題を追加・編集

`index.html` 内の `QUESTIONS` 配列を編集：

```js
{ id: 51, answer: 'your answer', correct: 'what', emoji: '🎨',
  grad: ['#FFE66D', '#FF8AB0'], exQ: 'What is this?' }
```

- `correct`: 正解の疑問詞ID (`what`, `who`, `where`, ... `whose`)
- `emoji`: ビジュアルカードに表示する絵文字
- `grad`: カード背景のグラデーション2色
- `exQ`: 音声読み上げ時の例文質問

### 1セットの問題数を変更

`QUIZ_LENGTH` 定数を変更（デフォルト 10）。

### 写真を使いたい場合

現在のビジュアルは「絵文字 + POPなグラデーション背景」です。
実写写真に差し替えたい場合は、`visual-inner` の中に `<img>` タグを追加するか、
画像ファイルを `/images/` フォルダに置いて `background-image` で参照できます。

## 音声について

Web Speech API の SpeechSynthesis を使用。
- モバイル Safari / Chrome では初回タップ後から音声が有効化されます
- 使用可能な英語音声を自動選択（Google US English を優先）
- 音声が出ない場合は端末の TTS（テキスト読み上げ）設定を確認してください

## ライセンス

教室内での使用を前提とした私的利用 OK。
