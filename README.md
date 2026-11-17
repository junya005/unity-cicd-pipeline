# GitHub&GameCI&Unity設定ファイルテンプレート

| 更新日       | 更新内容                      |
| --------- | ------------------------- |
| 2026/2/9  | 初版                        |
| 2026/2/9  | ライセンス返却のバージョンをv2に変更       |
| 2026/2/9  | dirtyでもビルドする設定を追加         |
| 2026/5/26 | ProjectPathを一般的なファイル命名に変更 |

## 補足
- Geminiを用いて作成
- 開始時と終了時にディスク開放とライセンスの返却を行い、キャッシュをすることでコスト(無料枠の時間消費量)を抑えた動作を可能にしている

## 構築手順

### Unityリポジトリの作成
- Unityのリポジトリを作成。
- Unityのフォルダをrootに置かない場合は後で`projectPath: ~`を用いてパスを指定する必要がある

### Job用の変数を作成
- Actions seacrets(SettingsのSeacret and Variablesにある)で以下のSeacret Repositoryを追加する
	- UNITY_LICENSE -> 下のコードブロックのpathに存在する`.ulf`ファイルの中身をコピーし貼り付け
	- UNITY_EMAIL -> 自分のUnityアカウントのメールアドレス
	- UNITY_PASSWORD -> 自分のUnityアカウントのパスワード

```
Windows: C:\ProgramData\Unity\Unity_lic.ulf
Mac: /Library/Application Support/Unity/Unity_lic.ulf
Linux: ~/.local/share/unity3d/Unity/Unity_lic.ulf
```

### ビルドの指示ファイルを追加
- このリポジトリの`.github/workflows/unity-cicd.yml`をディレクトリごとコピーし、リポジトリルートに配置

### テスト結果投稿のため、Actionsの権限を変更する
- `Settings->Actions->General->Workflow permissions`を`Read and write permissions`に変更

### まとめ
- 上記手順でUnityの自動テスト、ビルドの環境が整う。
