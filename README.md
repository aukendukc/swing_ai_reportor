# 指導報告書自動生成ツール

Google Gemini APIを使用した保護者向け指導報告書の自動生成ツールです。

## 特徴

- 🎯 **完全ブラウザベース**: サーバー不要でブラウザ上で動作
- 🤖 **AI駆動**: Google Gemini 2.5 Flashによる高品質な文章生成
- 📱 **レスポンシブデザイン**: スマートフォン・タブレット対応
- 🔒 **セキュア**: APIキーはローカルストレージに安全保存
- 📋 **履歴機能**: 最新5件の生成履歴を保存
- 🖨️ **印刷対応**: 印刷用スタイル設定済み
- ☁️ **Vercel対応**: ワンクリックでデプロイ可能

## デプロイ方法

### Netlifyへのデプロイ（推奨）

1. **GitHubにプッシュ**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/swing-report-generator.git
   git push -u origin main
   ```

2. **Netlifyでデプロイ**
   - [Netlify](https://netlify.com) にアクセス
   - GitHubアカウントでログイン
   - 「New site from Git」をクリック
   - GitHubを選択してリポジトリを接続
   - Build settings:
     - Build command: 空欄
     - Publish directory: `.`
   - 「Deploy site」をクリック

3. **カスタムドメイン設定（オプション）**
   - Netlifyダッシュボードで「Domain settings」
   - カスタムドメインを追加

### Vercelへのデプロイ

1. **GitHubにプッシュ**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/swing-report-generator.git
   git push -u origin main
   ```

2. **Vercelでデプロイ**
   - [Vercel](https://vercel.com) にアクセス
   - GitHubアカウントでログイン
   - 「New Project」をクリック
   - リポジトリを選択
   - デプロイ設定を確認して「Deploy」をクリック

3. **カスタムドメイン設定（オプション）**
   - Vercelダッシュボードで「Settings」→「Domains」
   - カスタムドメインを追加

### ローカル開発

```bash
# 依存関係のインストール
npm install

# ローカルサーバーの起動
npm run dev
```

## セットアップ手順

### 1. Google Gemini APIキーの取得

1. [Google AI Studio](https://makersuite.google.com/app/apikey) にアクセス
2. Googleアカウントでログイン
3. 「Create API Key」をクリック
4. APIキーをコピーして保存

### 2. アプリケーションの起動

1. デプロイされたURLにアクセス、または `index.html` ファイルをダブルクリック
2. 初回起動時にAPIキーを入力
3. 進捗内容を入力して「報告書を生成」ボタンをクリック

## 使用方法

### 基本操作

1. **APIキー設定**（初回のみ）
   - APIキー入力欄にGoogle Gemini APIキーを入力
   - 自動的にローカルストレージに保存されます

2. **進捗内容入力**
   - テキストエリアに生徒の進捗状況を入力
   - 例：「教科書p.12-14、計算ミス多い、理解度良好」

3. **報告書生成**
   - 「報告書を生成」ボタンをクリック
   - AIが保護者向けの丁寧な報告書を自動生成

4. **結果の活用**
   - 生成された報告書をコピーまたは印刷
   - 履歴から過去の報告書を参照可能

### 入力例

```
教科書p.12-14、計算ミス多い、理解度良好
```
↓
```
【学習内容の報告】
本日は教科書12ページから14ページの内容を学習いたしました。基本的な計算問題に取り組み、新しい概念の理解を深めました。

【評価とコメント】
計算の過程でいくつかのミスが見られましたが、概念の理解度は良好です。集中して学習に取り組む姿勢が見られ、積極的に質問もしてくれました。

【今後の方針】
計算ミスを減らすため、基礎計算の練習を継続いたします。理解できている部分を活かしながら、正確性を向上させていきたいと思います。
```

## 機能詳細

### エラーハンドリング

- **APIキー未設定**: 適切な案内メッセージを表示
- **入力内容未記入**: 警告メッセージを表示
- **API呼び出し失敗**: 詳細なエラーメッセージを表示
- **ネットワークエラー**: 接続問題の案内を表示

### セキュリティ機能

- APIキーはローカルストレージのみに保存
- 外部サーバーへの送信はGoogle Gemini APIのみ
- 入力内容のサニタイズ処理
- Vercelのセキュリティヘッダー設定

### 追加機能

- **生成履歴**: 最新5件の報告書を保存・参照可能
- **キーボードショートカット**: Ctrl+Enterで報告書生成
- **印刷対応**: 印刷時に不要な要素を非表示
- **コピー機能**: ワンクリックでクリップボードにコピー

## 技術仕様

### 使用技術

- **フロントエンド**: HTML5, CSS3, JavaScript (ES6+)
- **AI API**: Google Gemini 2.5 Flash
- **ストレージ**: LocalStorage
- **デザイン**: レスポンシブCSS、グラデーション
- **ホスティング**: Vercel

### API仕様

- **エンドポイント**: `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash:generateContent`
- **リクエスト形式**: JSON POST
- **認証**: API Key認証

### ブラウザ対応

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## トラブルシューティング

### よくある問題

**Q: APIキーが無効と表示される**
A: Google AI Studioで正しいAPIキーを取得し、再度入力してください。

**Q: 報告書が生成されない**
A: インターネット接続を確認し、API利用制限に達していないか確認してください。

**Q: 履歴が表示されない**
A: ブラウザのローカルストレージが有効になっているか確認してください。

**Q: 印刷時にレイアウトが崩れる**
A: ブラウザの印刷設定で「背景のグラフィック」を有効にしてください。

**Q: Vercelデプロイでエラーが発生する**
A: `vercel.json`の設定を確認し、リポジトリのルートディレクトリに配置されているか確認してください。

## ライセンス

このプロジェクトはMITライセンスの下で公開されています。

## サポート

問題や質問がある場合は、GitHubのIssuesページでお知らせください。

---

**注意**: このツールは教育目的で作成されています。生成された報告書は必ず内容を確認してから使用してください。
