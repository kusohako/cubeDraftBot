# Introduction
This is a tool for online TCG players.

# Usage

coming soon...

# 要件メモ

## 前提
キューブドラフトをできるようにする
そのために必要な機能
  - プレイヤーの登録
    - public なチャンネルで bot に対してリプライなどで参加を表明するとプレイヤー登録できる
    - 1チャンネル1ゲーム
    - 以後botとプレイヤーはDMでやり取りする
  - カードリストの登録
    - 一人がすべて登録する場合
      - プレイヤーではなくGMとして参加し、botにカードリストをDMする
    - 各プレイヤーが持ち寄る場合
      - 各プレイヤーは必要枚数のカードリストをbotにDMする
      - 集まったカードリストは単純に混ぜ合わされる
  - パック作成
    - カードリストからランダムにパックをプレイヤー人数*ドラフト回数分抽出して作成
    - とりあえず今は抽選はこれだけだが後々拡張するかも
  - ドラフト
    - ランダムに席順を決める
    - ピックしたら残りを次の人に回す
    - 1パックすべてピック終了したら逆順にもう一度ドラフト開始
    - パックをすべてなくすまで繰り返す
  - 対戦表作成
    - 席順から対戦表を作って見せてくれる
    - 勝敗管理もできると嬉しいね

## やり取りのイメージ
  - !create 4 3 15
    - 4人 3パック 15枚入りで開始
    - 「ドラフトの参加募集を開始しました」
  - !join
    - 「参加を受け付けました」
    - 集まったらDMで「カードリストを提出してください」
  - !leave
    - 「参加を取り消しました」
  - 平文でカードリスト提出
    - 提出内訳をDMで表示
    - 再提出で上書き
  - !draftstart
    - 足りてなかったら「カードリストがまだ完成していません」
    - 足りてたらピックの席順発表、DMでpick開始
  - !pick 4
    - 表示されてるうち4つ目をpick
    - 全員pickするまで変更可能？要検討
    - ラスト1pickは自動

## 拡張（願望）
  - 多言語化
    - bot のメッセージを日本語以外も対応する
  - カードにタグ付けして抽選をアレコレする（レアリティとか）
  - 並列化
    - 適当にサーバー借りて動かすと色んな人が利用するだろうからいい感じにスレッドを使って並列化したりしなかったりする