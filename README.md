# ゲームプログラミング1年生
2017年度 デジタルアーツ東京 ゲームプログラミング１年生用リポジトリー

# 講義予定
- [シラバス](syllabus.md)

# 参考URL
- [GitHubにUnityのプロジェクトを新規に作成する手順(VisualStudioも同様)](http://am1tanaka.hatenablog.com/entry/2016/02/05/102508)
- [GitHub Desktopで.gitignoreが作られなかった場合の対処](http://am1tanaka.hatenablog.com/entry/2017/06/09/234448)

# 13回目(7/21)
- [今回(13回目)の講義の動画目次](./docs/13-live.md)
- [前回(12回目)の講義の動画目次](./docs/12-live.md)
- 前回の金曜日欠席の人
  - https://github.com/dat17/yoketoru を開く
  - 右の[Clone or Download]ボタンをクリックして、[Download ZIP]をクリックしてダウンロード
  - ダウンロードが完了したら、ファイルを開く
  - スタートメニューから、コンピュータを開いて、[ライブラリ]>[ドキュメント]>[パブリックのドキュメント]>[Unity17]フォルダーを開いておく
  - フォルダーが開くので、[yoketoru-master]フォルダーをドラッグして、上で開いた[Unity17]フォルダーにドロップしてコピー

## 今日の提出
- \\LANDISK-A601\disk\2017年\学生用フォルダー\GP_1\gameprograming13 フォルダー内に、半角英数で、苗字のフォルダーを作って、その中に、キャラクターの差し替えと、BGM/SEが入ったUnityのプロジェクトフォルダーをコピーして提出
- 以上が完了したら、夏休みの課題の作業を開始する
  - yoketoruに新しい要素を入れる or 別のプロジェクトを探す or オリジナルの企画を考える etc...

## 予定：よけとる開発仕上げ
- [今回のデスクトップ動画のライブ配信](https://www.youtube.com/watch?v=nZip5_dVoTI)
- キャラクタープレハブの作成
- AssetStoreで、キャラクターと背景をインポート
  - プレイヤー
  - アイテム
  - 敵
  - 背景
- BGMと効果音の再生
  - 鳴らすタイミング
    - タイトル画面でスタートした時の効果音
    - ゲーム中のBGM。ループ再生する
    - アイテムを取ったときの効果音
    - 敵にぶつかった時の効果音
    - ゲームオーバージングル
    - クリア曲
    - タイトルは無音
  - 手順
    - リソースを探す
    - 著作者名とURLをGitHubのREADME.mdに書く
    - 再生方法をWebで検索して、実装する
## フリー素材音楽サイト
- [魔法魂](http://maoudamashii.jokersounds.com/)
- [効果音ラボ](http://soundeffect-lab.info/)
- [甘茶の音楽工房](http://amachamusic.chagasi.com/)
- [PANICPUMPKIN ファミコン風オリジナル音楽](http://pansound.com/panicpumpkin/)

## 参考プロジェクト
- [Unityの簡易シーン切り替え例2017年度版](https://github.com/tanakaedu/SimpleScene17)

## メモ
- プレイヤーのアセット
  - https://www.assetstore.unity3d.com/jp/#!/content/18880
- アイテムのアセット
  - https://www.assetstore.unity3d.com/jp/#!/content/73764
- 敵のアセット
  - http://u3d.as/F02
- 背景のアセット
  - https://www.assetstore.unity3d.com/jp/#!/content/18880

## 夏休みの課題：ミニゲームの開発
Unity、Phaser、その他の環境でも可。<b>ミニ</b>ゲームを開発する。

- 完全なオリジナルでなくてもよい
  - 講義で作成したyoketoruを改造したもの
  - Webで見つけたチュートリアルを改造したもの
  - AssetStoreのプロジェクトを改造したもの
  - 書籍のサンプルを改造したもの
- yoketoruの場合、以下のような要素を追加してみよう
  - 障害物を作る
  - 弾を撃つ
  - 敵の動きのバリエーションを増やす
  - 演出(パーティクル)
  - 画面を綺麗にする
- チュートリアルの例
  - ひよこのたまご http://hiyotama.hatenablog.com/
  - Unityの公式 https://unity3d.com/jp/learn/tutorials
  - AssetStore https://www.assetstore.unity3d.com/jp/#!/search/page=1/sortby=popularity/query=price:0&category:98
  - 本棚の書籍

### 夏休み明け
夏休み明けに、以下の要領で発表会を行う。

- 一人5分～10分程度で発表
- 作品をネットドライブにコピーしておいて、教卓PCで実行して、解説
- 発表内容は以下の通り
  - 作品名
  - 作品の概要
  - 操作方法
  - ゲームのルール
  - どこを自分で開発したか
  - 利用したアセットやチュートリアルを、全て紹介
- 各内容については、 https://unityroom.com/ の作品を何本か確認して、どのように書けば分かりやすいかを研究して、工夫すること


## 以下、水曜日に実施済み
- [暗くなるのを解決する](./docs/13-shiage.md)
- ゲームオーバー、クリア時に処理を止める
- ボールや敵の出現を、`Spawner`オブジェクトにする(`Awake`にする必要がなくなる)


---

## 前回の修正
- MoveBall.cs の `Start`の処理は、`Awake`にした方がよい
  - ゲームオブジェクトのインスタンシエイトを実行してから、`Start`が動くまでに時間差があり、その間に当たり判定が動いてしまうと、不測の事態になる
  - そこで、インスタンシエイト直後に呼び出される`Awake`に座標の設定を変更することで、このような不具合を防ぐ
  - ただ、今回、出現処理を変更するため上記の不具合は自然に解消する


# 12回目(7/14)
- [前回(11回目)の講義の動画目次](./docs/11-live.md)

## 話題
- [Unity3D Japan 【Unite 2017 Tokyo】Unityで楽しむノンフォトリアルな絵づくり講座：トゥーンシェーダー・マニアクス](https://www.youtube.com/watch?v=6aNB9LhSx7g)
- [【第13回】東ゲ部もくもく会](https://togebu.doorkeeper.jp/events/62478)
  - 2017-07-16（日）10:30 - 18:00
  - 1,000円 会場払い
  - 申込締切 7月16日 17:00 
- ゲーム業界の声

## 内容：よけとる開発(2)
- [今回のデスクトップ動画のライブ配信](https://www.youtube.com/watch?v=LahKaump9pQ)
- スコアの実装
- hanekaeri から移植

# 11回目(7/7)
- [前回(10回目)の講義の動画目次](./docs/10-live.md)

## 内容：よけとる開発(1)
- [今回のデスクトップ動画のライブ配信](https://www.youtube.com/watch?v=fx5Tohe7FyI)
- 新しいUnityプロジェクトを作成
- GitHubに登録
- [状態遷移についてスライド](docs/unity-scene-1706.pptx)
- [状態遷移を作る](docs/10-scene.md)
- プレイヤー用のアセットを読み込む

# 10回目(6/30)
## 9回目の内容
- [成果物](https://github.com/tanakaedu/move-labels/)
- [前回(9回目)の講義の動画目次](./docs/09-live.md)

## 内容
- [今日のデスクトップ動画](https://www.youtube.com/watch?v=XTjNKwH1hvs)
- 前回やったことの復習
- Unityの乱数
- ボールの数を数える(static)
- マウス移動
- ベクトルについて
- 移動速度に上限を設定
- キャラクターを見分ける(Tag)

# 9回目(6/23)
## 8回目にやったこと
- [1コマ目 C#](https://www.youtube.com/embed/kkYjFjGVsdY)
  - C# 違う変数型への代入方法
  - switch文
  - マウス入力
  - オフセットとピボット
  - コミットとSync
  - ifその2。複合で当たり判定
- [2コマ目 Unity](https://www.youtube.com/embed/E3OvAjHDvso)
  - 同じプレハブから作成したオブジェクトの共通の振る舞いを設定するには、プレハブで作業する
  - OnMouseEnter()を使う
  - Debug.Logで表示
  - Destory()でオブジェクトの削除
  - SetActive()で有効・無効の切り替え
  - 文字表示
  - ゲームマネージャー
  - 空のゲームオブジェクト(Empty)
  - Inspectorで、Hierarchyのオブジェクトを渡す方法
    - public変数
  - 物理エンジンの時間を止める

## 内容
- [今日のライブストリーミング](https://www.youtube.com/embed/ZpBuUYDRLMg)
- 乱数
- for文
- 配列
- 以上、[成果物](https://github.com/tanakaedu/move-labels/)

# 8回目
## 7回目にUnityでやったこと
- [2017/6/9 GP1-8 Unityでボールを画面内で跳ね返らせる](https://www.youtube.com/embed/lVaOYDGzNk8?cc_load_policy=1&fs=1&rel=0&autoplay=1)
- [2017/6/9 GP1-8 Unityの描画のオンオフ](https://www.youtube.com/embed/vaPkJTphaWY?cc_load_policy=1&fs=1&rel=0&autoplay=1)

## 休んだ人は・・・
- Google Chrome を起動して、 https://github.com を表示
- 右上の Sign in をクリックして、サインインする(すでに自分のアカウントでサインインしていたらこの手順は不要。他人のものだったら、右上のアイコンをクリックして、[Sign out]を選択してサインアウトしてから、改めて Sign in する)
- 自分のアカウントの csharp-manual [リポジトリーを削除](http://qiita.com/PlanetMeron/items/4d164eff7bff2243cf06)
- https://github.com/dat17/csharp-manual を右クリックして、新しいウィンドウで開く
- 開いたウィンドウの画面右上の[Fork]をクリック
- https://github.com/tanakaedu/move-labels を右クリックして、新しいウィンドウで開く
- 開いたウィンドウの画面右上の[Fork]をクリック
- GitHub Desktopを起動
- [自分のアカウントでログインしているか確認](http://am1tanaka.hatenablog.com/entry/2016/02/05/102508#%E3%83%AD%E3%82%B0%E3%82%A4%E3%83%B3%E3%81%97%E3%81%A6%E3%81%84%E3%82%8B%E3%81%8B%E7%A2%BA%E8%AA%8D)
- 画面左上の[+]をクリック
- [Clone]をクリック
- move-labelsをクリックして、Clone
- クローン先は、そのままの場所で良いので、そのまま[OK]

以上。

## 話題
- [gamesindustry 本格的モーションキャプチャスタジオやVR機器などを無償で提供，リクルートテクノロジーズがオープンイノベーションスペースを開設](http://jp.gamesindustry.biz/article/1706/17061501/)

## 内容
- [今日のライブストリーミング](https://www.youtube.com/embed/lgiQHRjEmBw)
- switch文と変数の型変換の表を完成させる
- マウス操作
- if文その2　マウスと重なったら停止
- Unityのhanekaeriを読み込んで、同じ動きをUnityで実装して、違いを比較する

# 7回目
## 内容
- 前回の復習
  - [演習8-1](https://github.com/dat17/csharp-manual/blob/master/08.md#%E6%BC%94%E7%BF%928-1)から、一通り手順に従って進めて、ラベルが画面内を跳ね返るプログラムを完成させよう
  - 跳ね返り座標を計算するためのイメージ
- GitHubに、move-labelsでプッシュ済み
![](./images/img0800.png)
- Unityのhanekaeriを読み込んで、同じ動きをUnityで実装して、違いを比較する
- GitHubに、hanekaeriでコミット。プッシュはしてない

# 6回目
## 準備
- github を開いて、 sign in する
- Visual Studio 2013 を起動して、 if-rensyu というプロジェクトを作成しておく

## 内容
- 前回の復習
  - ifというプロジェクトを作成して、ボタンをタイマーで動かして、クリックすると移動方向が逆になるプログラムの作成
- 変数からifまで
  - 画面端での跳ね返りについて考察して、次回までに検討
- Unityでボールを動かす

# 5回目
## 内容
- コントロールの続きから
  - 画像、タイマーなどを確認
- 変数について導入

# 4回目
## 内容
- 前回の復習
  - 新しいプロジェクトを move-button という名前で作成
  - 1つのボタン+十字に配置した4つのボタンで思いつくことをやってみる
- 計算の続きから、プロパティーの確認まで
- Paiza LearningでC#の #2 の5つの演習

# 3回目
## 2回目の成果物
- [C# 書く教科書 Visual C#の基本操作](https://github.com/dat17/csharp-manual/blob/master/01.md)

## 内容
- 前回やったことの復習(day170512)
- C# 書く教科書のプログラミングの肝
- エラーとデバッグ(error)
- プロパティの確認
  - ボタンをクリックしたら、表示内容を変更したり、消えるボタンを作る(error)
- 計算
  - ボタンをクリックしたら、右に移動したり、右下に移動したり、左上に移動させる(calc)

# 2回目
- [C# 書く教科書 はじめ方](02.md)
- [Tyrano Script](https://github.com/dat17/design/blob/master/02_tyrano.md)
- e-typing練習
  - [タイピング練習サービス e-typing](https://www.e-typing.ne.jp/)

# 1回目
- SMSの設定確認
  - [docomoのSMS設定](https://www.nttdocomo.co.jp/info/spam_mail/sms/)
  - [auのSMS設定](https://www.au.com/mobile/service/mail/sms/)
  - [SoftbankのSMS設定](http://faq.mb.softbank.jp/detail.aspx?cid=78827&id=78827)
- ガイダンス-プログラミングとは
- ユーザー登録
  - Unity / Paiza
- Visual Studioを試す
- Unityを試す
- ドットインストールでの学び方
  - [ドットインストール Unity(4.2)入門](http://dotinstall.com/lessons/basic_unity)
- Paizaでの学び方
  - [Paizaラーニング C#](https://paiza.jp/works/cs/primer)


# 参考URL
- [Unity](http://japan.unity3d.com/)
- [ドットインストール](http://dotinstall.com/)
  - [ドットインストール Unity(4.2)入門](http://dotinstall.com/lessons/basic_unity)
- [Paizaラーニング](https://paiza.jp/works)
  - [Paizaラーニング C#](https://paiza.jp/works/cs/primer)
- [タイピング練習サービス e-typing](https://www.e-typing.ne.jp/)
- [Phaserをサンドボックスで試すチュートリアル](http://am1tanaka.hatenablog.com/entry/2017/04/19/211234)
- [C# 書く教科書](https://github.com/tanakaedu/csharp-man)

