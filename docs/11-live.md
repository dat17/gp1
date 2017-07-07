# 11回目 デスクトップ動画目次
## 前回までの確認
- https://youtu.be/fx5Tohe7FyI?t=35s
  - 乱数で座標と速度を設定
  - マウスを追う
  - タグで相手を判定
  - ボールの数を把握して、クリアを検出

## シーン管理について講義
- https://youtu.be/fx5Tohe7FyI?t=4m14s

## 新しいプロジェクト yoketoru の作成
- https://youtu.be/fx5Tohe7FyI?t=28m52s
- Titleシーンを保存して、プロジェクトを保存 https://youtu.be/fx5Tohe7FyI?t=33m19s
- GitHubに登録 https://youtu.be/fx5Tohe7FyI?t=34m43s

### `.gitignore`が作られなかった時の対処
- https://youtu.be/fx5Tohe7FyI?t=38m54s
- GitHubのgitignoreを検索 https://youtu.be/fx5Tohe7FyI?t=41m53s
- 一つ上のフォルダーに移動 https://youtu.be/fx5Tohe7FyI?t=42m1s
- ファイルを右クリックして保存を選択して、`.gitignore`にファイル名を変更して保存 https://youtu.be/fx5Tohe7FyI?t=42m11s
- Atomなどのテキストエディターを起動して、`.gitignore`をドラッグ＆ドロップで開く https://youtu.be/fx5Tohe7FyI?t=44m9s
- 無効な中身なので、全て選択して削除 https://youtu.be/fx5Tohe7FyI?t=44m19s
- `Unity.gitignore`を開いて、[Raw]をクリックして、全て選択してコピー https://youtu.be/fx5Tohe7FyI?t=44m26s
  - Atomに貼り付けて保存 

`.gitignore`の取得は、 https://www.gitignore.io でできる。ただ、ダウンロードはできないので、何らかの方法で`.gitignore`ファイルを作る必要がある。

### GitHubへの登録の続き
- 問題なくなったら、コミットして、[Publish]をする https://youtu.be/fx5Tohe7FyI?t=54m31s


## シーンを作る方針
- https://youtu.be/fx5Tohe7FyI?t=55m18s

## タイトルシーンのテキストを扱う
- タイトルを表示するためのテキストユーザーインターフェースを作成する https://youtu.be/fx5Tohe7FyI?t=57m57s
- スコアを表示するためのテキストを作成 https://youtu.be/fx5Tohe7FyI?t=1h

### テキストの調整(Canvas)
- 画面の大きさが変わっても、文字の大きさが変わらない https://youtu.be/fx5Tohe7FyI?t=1h48s
- Canvas Scalerを調整する https://youtu.be/fx5Tohe7FyI?t=1h2m14s
  - ターゲットとなる解像度を決めておいて、それを幅と高さに設定するとよい

### テキストの調整(Text)
- 折り返しがない場合は、`Overflow`の設定が必要 https://youtu.be/fx5Tohe7FyI?t=1h6m10s
- サイズを調整
- outlineやshadowコンポーネントを使うとテキストを飾ることができる https://youtu.be/fx5Tohe7FyI?t=1h7m6s
- アスペクト比の変更に対応させる https://youtu.be/fx5Tohe7FyI?t=1h11m6s
  - AnchorとPivotとAlignmentを調整する
- タイトルは画面の中央に配置されるように調整 https://youtu.be/fx5Tohe7FyI?t=1h14m57s

## ゲームシーンを作る
- https://youtu.be/fx5Tohe7FyI?t=1h21m24s
- タイトルからユーザーインターフェースをコピーする https://youtu.be/fx5Tohe7FyI?t=1h23m20s
- タイトルの文字は要らないので削除 https://youtu.be/fx5Tohe7FyI?t=1h24m57s

## ゲームオーバーとクリアの作成
- 同様にして、ゲームオーバーとクリアを作成 https://youtu.be/fx5Tohe7FyI?t=1h25m42s

---

## シーンを切り替える
### タイトルシーン
- https://youtu.be/fx5Tohe7FyI?t=1h38m48s
- シーンをコントロールする`TitleManager`オブジェクトとスクリプトを作る https://youtu.be/fx5Tohe7FyI?t=1h42m8s
- スクリプトを作成 https://youtu.be/fx5Tohe7FyI?t=1h51m22s
- キー操作について確認 https://youtu.be/fx5Tohe7FyI?t=1h51m40s
- `Fire1`キーを押したかを判定 https://youtu.be/fx5Tohe7FyI?t=1h53m31s
- シーンの読み替えのスクリプト https://youtu.be/fx5Tohe7FyI?t=1h55m16s
  - `using`を追加
  - `SceneManager.LoadSceneAsync()`を追加
- このままだとエラーになる https://youtu.be/fx5Tohe7FyI?t=1h58m41s
- シーンをビルドターゲットに設定する https://youtu.be/fx5Tohe7FyI?t=1h59m23s
- 動作確認 https://youtu.be/fx5Tohe7FyI?t=2h6m14s

### ゲームシーン
- https://youtu.be/fx5Tohe7FyI?t=2h7m24s
- 次のシーンを入れる変数を定義 https://youtu.be/fx5Tohe7FyI?t=2h10m40s
- キーを押した時に、次のシーンを設定 https://youtu.be/fx5Tohe7FyI?t=2h12m21s
  - シーンの切り替え処理 https://youtu.be/fx5Tohe7FyI?t=2h16m30s
- 動作確認 https://youtu.be/fx5Tohe7FyI?t=2h19m45s
  - スコアが消えてしまう
- ゲームオーバーとクリアは追加読み込み https://youtu.be/fx5Tohe7FyI?t=2h20m47s
- 動作確認 https://youtu.be/fx5Tohe7FyI?t=2h22m12s
  - クリアとゲームオーバーが同時に発生
- 切り替えたら、ゲームの管理を無効にする https://youtu.be/fx5Tohe7FyI?t=2h23m10s
- 動作確認 https://youtu.be/fx5Tohe7FyI?t=2h25m47s

### 残りのシーンにタイトルへの移動
- https://youtu.be/fx5Tohe7FyI?t=2h25m47s
- コミット https://youtu.be/fx5Tohe7FyI?t=2h53m2s
- ゲームオーバーとクリア時に警告が大量に表示される　https://youtu.be/fx5Tohe7FyI?t=2h54m
　　- カメラや不要な光を無効にする https://youtu.be/fx5Tohe7FyI?t=2h55m33s
- 動作確認 https://youtu.be/fx5Tohe7FyI?t=2h56m45s

## アセットの読み込み
- 探してきたアセットをよみこむ https://youtu.be/fx5Tohe7FyI?t=3h34s


# まとめ
- Unityでシーンを切り替えるスクリプトを作成した
- 画面サイズが変更されても、レイアウトが崩れにくいテキストの設定をした
- アセットの読み込み

次回、スコアの実装、アセットの読み込み、ゲーム本体の実装。
