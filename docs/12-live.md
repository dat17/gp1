# 12回目 デスクトップ動画目次
## 話題
- https://youtu.be/LahKaump9pQ?t=2m32s

## 前回までの確認
- https://youtu.be/LahKaump9pQ?t=15m54s
  - シーンを切り替える
  - シーン管理について復習 https://youtu.be/LahKaump9pQ?t=18m20s
  - スコアは`static`でやる
  - `TitleManager`と`GameManager`に同じスクリプト`GameParams.cs`をアタッチ https://youtu.be/LahKaump9pQ?t=22m59s

## スコアの実装
- Gameシーンの`GameManager`に、新しいスクリプト`GameParams.cs`を新規に追加してアタッチ https://youtu.be/LahKaump9pQ?t=25m37s
- 自分のインスタンス`_instance`を宣言 https://youtu.be/LahKaump9pQ?t=29m19s
- `Awake()`とは、インスタンスが作られた直後に呼ばれる。`Start（）`より前に初期化が必要なものはここで初期化 https://youtu.be/LahKaump9pQ?t=30m58s
- スコアを表示する`Text`のインスタンスを受け取る場所を宣言 https://youtu.be/LahKaump9pQ?t=33m
  - 最初の宣言は間違えているので注意！
- 点数を記録するための`static`変数を宣言 https://youtu.be/LahKaump9pQ?t=34m34s
- ここで、事前に宣言した`instance`を`_instance`に変更
- 使わない`Start`と`Update`を削除 https://youtu.be/LahKaump9pQ?t=43m58s
- スコアを設定するパブリックメソッド`SetScore`を作成 https://youtu.be/LahKaump9pQ?t=44m26s
- スコアを描画するパブリックメソッド`DrawScore`を作成 https://youtu.be/LahKaump9pQ?t=45m24s
- `static`メソッド内では、インスタンスプロパティである`scoreText`が参照できない、という説明  https://youtu.be/LahKaump9pQ?t=46m50s
  - `_instance`プロパティに記録した`this`のインスタンスから呼び出せばOK https://youtu.be/LahKaump9pQ?t=48m45s
- `GameManager`オブジェクトに追加された`Score Text`スロットに、スコアを表示するテキストをドラッグ＆ドロップ https://youtu.be/LahKaump9pQ?t=51m6s
- `GameManager`スクリプトの`Start`メソッドに、スコアの初期化を追加する https://youtu.be/LahKaump9pQ?t=56m19s
  - ゲームが始まるときに実行する場所なので、ゲームが開始するときにスコアが`0`点になる
- このままだとスコアが描画されないので、`SetScore`内に`DrawScore`の呼び出しを追加 https://youtu.be/LahKaump9pQ?t=58m55s
- スコアを0埋めする https://youtu.be/LahKaump9pQ?t=1h2m58s
  - `ToString()`に文字列でフォーマット文字列(`D6`で、6桁の10進数値)を渡す
- 点数を加算するメソッド`AddScore`を追加する https://youtu.be/LahKaump9pQ?t=1h4m7s
  - スコアが上限をオーバーしないように、チェック用のif文を作っておく
- スコアの加算を試すために、`A`キーを押すと点数を加算する処理を追加 https://youtu.be/LahKaump9pQ?t=1h7m14s
- コミット https://youtu.be/LahKaump9pQ?t=1h11m38s
- タイトル時のスコア描画が抜けていたので、追加 https://youtu.be/LahKaump9pQ?t=1h14m9s
- 今度こそ、雛形完成 https://youtu.be/LahKaump9pQ?t=1h16m49s

---

休憩

---

## 作成済みの`hanekaeri`を移植する
### hanekaeri をパッケージ化
- Unityをもう一つ起動して、`hanekaeri`を起動 https://youtu.be/LahKaump9pQ?t=1h40m5s
- すべての要素を`hanekaeri`フォルダーに入れる https://youtu.be/LahKaump9pQ?t=1h45m17s
- シーンを右クリックして、エクスポート https://youtu.be/LahKaump9pQ?t=1h48m57s
- `yoketoru`に切り替えて、エクスポートしたパッケージを[Project]ビューにドラッグ＆ドロップ https://youtu.be/LahKaump9pQ?t=1h50m40s

### 移植する
- `GameManager`が2つあってエラーが出ているので、`hanekaeri`の方の`GameManager`スクリプトの機能を確認して、削除 https://youtu.be/LahKaump9pQ?t=1h54m
- エラー場所は、シーンの切り替えタイミングなので、`NextScene`に移行する先の文字列を代入する https://youtu.be/LahKaump9pQ?t=1h56m5s

### ゲームオーバーとクリアが同時に設定される場合、クリアを優先する
- セッターとゲッターで、プロパティの読み出しと書き込みをスクリプトにできる https://youtu.be/LahKaump9pQ?t=2h4m20s
- `NextScene`を書き換える https://youtu.be/LahKaump9pQ?t=2h7m41s
- 動作を確認する。CLEARを設定したあとにGAMEOVERを設定しても、クリアするかをチェック https://youtu.be/LahKaump9pQ?t=2h15m21s

### hanekaeriのシーンを、yoketoruのゲームシーンに移植
- https://youtu.be/LahKaump9pQ?t=2h19m12s
- 枠とプレイヤーをゲームに移動したら、`hanekaeri`のシーンは不要なので、`RemoveScene`する。保存は不要 https://youtu.be/LahKaump9pQ?t=2h21m34s
- `Game`シーンは保存
- これで、プレイヤーの移植完了

### 敵とアイテムをスクリプトで自動生成
- 必要なプロパティーを追加 https://youtu.be/LahKaump9pQ?t=2h22m59s
- `GameManager`の`Start`に、敵とアイテムを出現させるスクリプトを追加 https://youtu.be/LahKaump9pQ?t=2h27m8s
- 出現するようになったが、エラーが発生 https://youtu.be/LahKaump9pQ?t=2h31m
- 残りボールの個数の表示が不要になったので、コードをコメントアウトする https://youtu.be/LahKaump9pQ?t=2h31m28s

### ゲームオーバー時にクリアになってしまう
- 原因が分からないので、アイテムを取ったときに100点加算するようにする https://youtu.be/LahKaump9pQ?t=2h31m28s
- ゲームオーバーになったあとに、アイテムが全て取ったことになってしまっている(1000点になるので) https://youtu.be/LahKaump9pQ?t=2h39m16s
  - 原因：`OnDestroy`は、シーンが切り替わる時にも呼ばれるため、`OnDestroy`に入れた処理は、取った時とは限らない。当たり判定の場所を調整する
- `MoveBall.cs`に`OnTriggerEnter`を追加して、そっちにボールを取った処理を移動する https://youtu.be/LahKaump9pQ?t=2h51m30s
- 念のため、ぶつかった相手が`Player`タグであるチェックを入れたので、プレイヤーオブジェクトのTagを`Player`に設定する https://youtu.be/LahKaump9pQ?t=2h55m8s

### 一度ゲームオーバーになると、次からクリアできなくなる
- 原因：`static`で数えていたボールの数が残ってしまうため
- `ClearBallCount()`メソッドを作成して、それを`GameManager`のスタートから呼び出す https://youtu.be/LahKaump9pQ?t=3h1m9s

### ボールをとっても消えない
- ボールと接触した処理に`Destroy(gameObject);`がなかったので、追加 https://youtu.be/LahKaump9pQ?t=3h9m13s

## 完成 
- https://youtu.be/LahKaump9pQ?t=3h12m13s

# まとめ
- スコアは、`static`で実装
- スコアなどのゲーム内で常に利用するものは、専用のクラスを定義して、`static`で管理するとよい
- `static`を活用する場合、自分のインスタンス`this`を記録する`_instance`などを利用すると便利
- セッターとゲッターを使うと、プロパティへの代入や読み出しに対して、スクリプトを入れてエラーチェックをしたり、公開レベルを読み書きで変えたりできる
- 状態遷移を作らないでゲームを作ると、相当大変。最初に状態遷移を実装してから、本体を実装した方が楽
- エラーの追い方を参考にして欲しい。エラーが表示されるエラーは大したエラーではない
- ボールや敵の座標設定は、`Start`だと動作が不安定になる。`Awake`に移動すべき(さらにいうと、本来は`Instantiate()`で座標を設定した方がよい

## 次回
- ボールや敵の出現を、`Spawner`オブジェクトにする(`Awake`にする必要がなくなる)
- 暗くなるのを解決する
- キャラクターを差し替える
- BGMや効果音を鳴らす
- リソースの集め方のレクチャー
- 完成

