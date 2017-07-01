# 10回目 デスクトップ動画目次
## 前回までの確認
- https://youtu.be/XTjNKwH1hvs?t=45s

## Unityの乱数
- https://youtu.be/XTjNKwH1hvs?t=3m44s
- `Random.Range(最小値, 最大値);`に、intを渡すとintで、floatを渡すとfloatで返す
- intは最大値を含まず、floatは最大値を含む。Phaserと逆なので注意
- その他、球体内や球体の表面上、円内、円周上などの乱数も得られる

### staticについて～オブジェクト指向の概要～
- https://youtu.be/XTjNKwH1hvs?t=6m48s

### コンピューターの乱数の特徴
- https://youtu.be/XTjNKwH1hvs?t=18m32s
- シードを使うことで、再現できる
- デバッグに有効

## 座標を乱数で設定
- 出現範囲を確認する https://youtu.be/XTjNKwH1hvs?t=21m4s
- スクリプトを作成する https://youtu.be/XTjNKwH1hvs?t=25m50s
  - 座標を設定する https://youtu.be/XTjNKwH1hvs?t=28m17s

## ボールの数を管理する
- ボールの数を表示するためのテキストを追加する https://youtu.be/XTjNKwH1hvs?t=35m28s
  - 折り返しが不要な場合、Horizontal OverflowとVertical Overflowを、どちらもOverflowにしておく
  - フォントサイズや色、配置など、好みに応じて設定
- ボールを管理するのは誰か https://youtu.be/XTjNKwH1hvs?t=38m21s
- スクリプトの実装 https://youtu.be/XTjNKwH1hvs?t=42m52s
  - 変数を定義
  - `Start`で定義した変数を1増やす
  - `Debug.Log()`で表示してみる https://youtu.be/XTjNKwH1hvs?t=45m23s
    - 増えない！　→　それぞれのボールが個別にデータを持っているから　→ staticにする！
  - staticを変数宣言に追加するだけ https://youtu.be/XTjNKwH1hvs?t=46m27s
    - 正しく動いた！ https://youtu.be/XTjNKwH1hvs?t=47m27s
- テキストに残りの数を表示 https://youtu.be/XTjNKwH1hvs?t=48m27s
  - `using UnityEngine.UI;`を追加
  - `public Text CountText;`でTextのインスタンスをもらう場所を追加
  - `CountText.text = ""+BallCount;`で表示できる
  - Unityで、Canvasの下のボールの数を表示するためのテキストをドラッグして、ボールのインスタンスへ追加 https://youtu.be/XTjNKwH1hvs?t=51m22s
    - 実は、このやり方はよくなく、後ほど、実行後のエラーの原因になっている
    - なぜ良くないのか？
      - テキストの表示は、テキストの仕事。それをボールが行っているから(主語が異なる）
    - 良い方法
      - テキストに更新のための命令を持たせるか、ゲームのパラメーターを管理するスクリプトが行う
    - 今回やらなかったのは
      - まだゲームシステムの設計前で、ゲームを管理する構造がない。ここでは、単純に文字を表示する方法だけ説明したかったので、シンプルな実装方法を選択した
- 消えるときに、ボールの数を減らす https://youtu.be/XTjNKwH1hvs?t=57m14s
  - `OnDestroy()`はUnityが提供しているサービスで、そのオブジェクトが消えるときに呼び出してくれる。ここにボールを減らす処理を書けば、ボールを消した時に減らしてくれる https://youtu.be/XTjNKwH1hvs?t=59m51s
  - このように、何かが起きた時に処理するプログラムを仕込んで、構築するのを**イベントドリブン(イベント駆動)**という
- 文字を右揃えにする https://youtu.be/XTjNKwH1hvs?t=1h1m22s
  - 数字は、右端が揃っていた方が読みやすいので、一般的に右揃えにする

## プレイヤーを作る
### プレイヤーオブジェクトの作成
- https://youtu.be/XTjNKwH1hvs?t=1h4m17s
- 入れ物のゲームオブジェクトを作成する(今回はCube)
- 移動して、当たり判定をRigidbodyで行いたい場合は、RigidbodyかCharacterControllerのいずれかをアタッチする
  - CharacterControllerは、傾斜の地面や段差を登ったりするアクションがある場合に利用。通常は、Rigidbodyでよい
- 重力が不要な場合は、`Use Gravity`のチェックを外す
- 停止時に発生しているエラー https://youtu.be/XTjNKwH1hvs?t=1h8m46s
  - 原因は、ボールの消滅時に、残りのボール数をテキストに表示しようとする処理。ゲームを停止する時にもボールが消滅するので、この処理が呼ばれるが、その際にボールの残り数を表示するためのテキストが先に削除されてしまうと、表示先がなくなるため、このようなエラーが発生する
  - 対策としては、描画前に、テキストが有効化のチェックを入れる方法がある。今回は仮のプログラムなので対処しなかった
- 跳ね返りが不要な場合は、`IsTrigger`にチェックを入れる https://youtu.be/XTjNKwH1hvs?t=1h11m59s
  - シューティングゲームなど
  - 物理シミュレーションの動きは予想外のことが起きる場合があり、プレイヤーや敵など、重要なキャラクターを動かすには邪魔になる場合が少なくない

### プレイヤーをマウスで操作
- https://youtu.be/XTjNKwH1hvs?t=1h14m45s
- スクリプト`Player`を作成 https://youtu.be/XTjNKwH1hvs?t=1h14m57s
- マウスの座標を確認 https://youtu.be/XTjNKwH1hvs?t=1h15m50s
  - Input.mousePosition
- マウスの座標にそのままプレイヤーを移動させてみる https://youtu.be/XTjNKwH1hvs?t=1h17m54s
  - 表示されない https://youtu.be/XTjNKwH1hvs?t=1h18m58s
  - 画面左下の方にマウスカーソルを移動させると見える https://youtu.be/XTjNKwH1hvs?t=1h19m26s
  - 座標系の違い!
- スクリーン座標系からワールド座標系へ https://youtu.be/XTjNKwH1hvs?t=1h33m44s
　　- ビューポートは(0,0)が画面の左下、(1,1)が右上。講義中、-1～1としてしまったが、0～1の誤り
- 変換するスクリプト https://youtu.be/XTjNKwH1hvs?t=1h38m27s

### マウスを追いかけるようにプレイヤーの動作を変更
- https://youtu.be/XTjNKwH1hvs?t=1h48m41s
- 最大速度を決める

### ベクトルの足し算と引き算
- https://youtu.be/XTjNKwH1hvs?t=1h50m2s
- ベクトルの足し算 https://youtu.be/XTjNKwH1hvs?t=1h53m54s
- ベクトルの引き算 https://youtu.be/XTjNKwH1hvs?t=1h59m40s
- 自分からマウスカーソルへのベクトル https://youtu.be/XTjNKwH1hvs?t=2h59s

### コードに戻る
- 自分からマウスカーソル位置へのベクトル https://youtu.be/XTjNKwH1hvs?t=2h4m7s
- やりたい処理をまとめる https://youtu.be/XTjNKwH1hvs?t=2h5m44s
- MoveTowards()を使った移動 https://youtu.be/XTjNKwH1hvs?t=2h6m9s
  - 現在座標、目的の座標、最大速度だけ設定すればよいので、ベクトルを算出する手順は不要だった・・・
  - 最大移動速度は、秒速ではなく、1フレーム分の移動量なので、注意　https://youtu.be/XTjNKwH1hvs?t=2h8m40s
    - Time.deltaTimeを速度にかける必要がある
 
### キャラクターがぶつかった時の処理 OnTriggerEnter
- https://youtu.be/XTjNKwH1hvs?t=2h15m54s
- スクリプト https://youtu.be/XTjNKwH1hvs?t=2h18m2s

## キャラクターを増やす
これまでは、触ったら取れるキャラクターだった。次は、ぶつかったらゲームが終わるキャラクターを作る。

### 見た目を変える Material
- https://youtu.be/XTjNKwH1hvs?t=2h22m11s
- [Project]ビュー>[Create]>[Material]でマテリアルを作成
- 作成したマテリアルをボールにドラッグ＆ドロップしてアタッチ
- 色を設定
- もう一つMaterialを作って、違う色を設定
- 別キャラにするボールにアタッチ
- そのボールを、[Project]ビューにドラッグ＆ドロップして、新しいプレハブにする

### ぶつかった相手は何者か？ Tag
- https://youtu.be/XTjNKwH1hvs?t=2h31m6s
- 必要なタグを追加(Add)
- キャラクターに作成したTagを設定する(プレハブに行えば、Hierarchyの全てに反映するので楽) https://youtu.be/XTjNKwH1hvs?t=2h32m44s
- 処理を分けたいところに`if`文で、`CompareTag("タグ名")`を使って、自分や相手が何者かを判別する https://youtu.be/XTjNKwH1hvs?t=2h33m39s

### クリアとゲームオーバー
- 残りの作業 https://youtu.be/XTjNKwH1hvs?t=2h44m57s
- ゲームオーバーの実装 https://youtu.be/XTjNKwH1hvs?t=2h45m40s
- ゲームが進行中かを表す変数 https://youtu.be/XTjNKwH1hvs?t=2h49m41s
- 敵にぶつかった時に、ゲームを停止する https://youtu.be/XTjNKwH1hvs?t=2h52m27s
- アイテムを全て取った時に、ゲームを停止する https://youtu.be/XTjNKwH1hvs?t=2h53m44s
  - ボールの個数が0になったら停止
  - 本来は`==0`でよい。ただ、何らかの不具合でチェックをすり抜けた時に、停止しない症状を避けるため、`<=0`にしている
    - 参考：ロボットなどのハードウェアを含めた構成でのプログラミングでは、センサーの状態がぴったりになることは期待できない。ぴったりの状態で判定するのではなく、大小比較などのおおまかな判定ができるようであれば、そちらで処理した方が安全な場合がある
  
## アセットストアで、キャラクターや背景を探す
- https://youtu.be/XTjNKwH1hvs?t=2h58m3s
- [無料のみ]をクリックしておけば、無料のアセットだけ探せる
- 本格的にやるなら、購入も検討して欲しい
- 次回までにやること https://youtu.be/XTjNKwH1hvs?t=3h2m33s

次回から、ゲームの構造を勉強して、今回の内容をゲームとして完成させる。丸と四角でやるのは味気ないので、各自、気に入ったキャラクターや背景を見つけてくること。
