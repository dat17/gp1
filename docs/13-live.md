# 13回目 デスクトップ動画目次
- https://www.youtube.com/watch?v=nZip5_dVoTI

## 概要
- 水曜日の復習
- キャラクターの差し替え
- BGM,SEを探す
- 自分で調べて、BGMとSEを実装してみる

## BGMや効果音の実装
- 情報を探す https://youtu.be/nZip5_dVoTI?t=2h50m23s
  - AudioSourceコンポーネントを鳴らす
  - 効果音は、`PlayOneShot(AudioClip)`で鳴らす
- 音データを[Project]ビューにドラッグ＆ドロップして読み込む https://youtu.be/nZip5_dVoTI?t=2h53m27s
- コードを追加する場所を探す https://youtu.be/nZip5_dVoTI?t=2h54m42s
  - アイテムを取った時なら、Playerかアイテムのいずれか。双方のコードを確認して、それらしい場所を探す
  - `Player.cs`は敵との判定のみなので、ここではない
  - `MoveBall.cs`の当たり判定にアイテムの取得場所があるので、ここにコードを追加

### 失敗した手順
- Ballにアイテムを取った時の音をアタッチ
- そのまま再生すると、ゲーム開始と同時に一斉に音が鳴る。これは、`Play On Awake`にチェックが入っていたから https://youtu.be/nZip5_dVoTI?t=3h18s
  - この動作は不要なので、チェックを外す
- 音は、`AudioSource`インスタンスの`Play()`を呼び出せばよい https://youtu.be/nZip5_dVoTI?t=3h2m36s
- 実装 https://youtu.be/nZip5_dVoTI?t=3h3m12s
  - `AudioSource`を記録する変数を定義
  - `Start()`内で、設定されている`AudioSource`を取得(GetComponent)
  - アイテムを取った場所で、`audioSource.Play();`を呼び出す
- 試すと、音が鳴らない！ 
  - 原因は、アイテムを取って、音を鳴らした直後に、そのアイテムを消してしまったこと。音源であるアイテムが消えてしまったので、音は鳴らない。

つまり、ここまでやった方法では効果音は鳴らない！

効果音は、`GameManager`で鳴らすことにする。

### 正解の手順
- https://youtu.be/nZip5_dVoTI?t=3h11m13s
- BGMもGameManagerに加える。これは、`Play On Awake`で自動再生にしておいて、`Loop`にチェックをしておけば、自動的に再生が始まって、ループする

効果音のための仕組みを作る。

https://youtu.be/nZip5_dVoTI?t=3h12m21s

- 効果音を設定する配列`SE`を定義
- `static`の`PlaySE()`メソッドを作る
- 仕組みができたら、`PlaySE(効果音番号);`で、`_instance.SEAudio.PlayOneShot(効果音番号);`として、効果音を再生する
- `static`なので、インスタンス変数の`SEAudio`や`SE`を参照できない。そこで、`_instance`という`static`変数を定義して、そこに`Start()`で`this`を記録して、そこから呼び出すようにする。 https://youtu.be/nZip5_dVoTI?t=3h16m59s
- アイテムを取った場所の再生コードを、`PlaySE()`の呼び出しに変更 https://youtu.be/nZip5_dVoTI?t=3h18m15s
- 設定 https://youtu.be/nZip5_dVoTI?t=3h18m47s
  - `SEAudio`に、効果音を鳴らすために追加した`Audio Source`をドラッグ＆ドロップ
  - 使いたい効果音の数を設定 https://youtu.be/nZip5_dVoTI?t=3h19m3s
  - Elementに効果音をドラッグ＆ドロップ

以上でできあがり。

# まとめ
ゲームオーバーやクリアの時にBGMを停止したい場合は、BGMを鳴らしているゲームオブジェクトのスクリプトに、`PlaySE()`と同じように、BGMを停止するメソッドを追加する。例の場合、`GameManager`。

メソッドができたら、前回、時間を停止したのと同じ場所に、BGMを停止するメソッドの呼び出しを加えればよい。

基本的には、これまで学んできたUnityの使い方の応用である。インターネットで情報を探し、試行錯誤をして、理解を深めて欲しい。
