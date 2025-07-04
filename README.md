# Python-Coin-Collection

**1. セットアップ** <br>
``Python-Coin-Collection``というフォルダー新規に作成する。<br>
IDELEを開いて**File**メニューから**NewFile**を選びからのファイルを作成し<br>
同じメニューから**Save As**を選んで、ファイル名を``coin.py``という名前で<br>
**Python-Coin-Collection**のフォルダーにセーブ。<br>

**2. 画像用フォルダを作成する** <br>
このゲームはモグラとCoinの画像を使用<br>
Python-Coin-Collectionフォルダーの中に<br>
新しく``images``を作成しimagesフォルダーはCoin.pyと<br>
同じフォルダーに保存する。<br>
![スクリーンショット 2025-06-29 092033](https://github.com/user-attachments/assets/647a1c2e-d368-4b59-a70f-c4ff2cee2c27)

<br>

**3. 画像をフォルダー入れる** <br>
**Python-Coin-Collection**に使用する画像coin.pngとhedgehog.pngというファイルを<br>
使用しこの2つを``images``フォルダの中に入れます。<br>

**4. プログラミングを開始** <br>
最初にゲームで使うエリアを設定するために、ファイルの先頭に<br>
下記のプログラムを入力。
```
WIDTH = 400
HEIGHT = 400
```
> [!NOTE]
> ゲーム画面をたてと横とも400pxに設定。

<br>

**5. スコアをセット** <br>
ゲームの開始時にスコアを0にセットするようにする。<br>
変数``score``を設定する。
```
score = 0
```
> [!NOTE]
> この行で変数``score``を0に設定する。

<br>

**6. ゲームオーバー？** <br>
真理値（``True``か``False``のどちらかになる）が代入される<br>
ブール変数（論理変数とも呼ぶ）を使用し<br>
**Pygame Zero**にゲームが終わったかどうかを教える。<br>
今は``False``をセットする。
```
game_over = False
```

<br>

**7. アクターを設定する** <br>
このゲームにはアクターが2つでてくる。<br>
モグラ（hedgehog）とコイン（coin）。<br>
この2つのアクターを作ってからステージの位置を決める。
```
hedgehog = Actor("hedgehog")
hedgehog.pos = 100, 100

coin = Actor("coin")
coin.pos = 200, 200
```
> [!NOTE]
> ``hedgehog = Actor("hedgehog")``imagesフォルダーのhedgehog.pngを<br>
> 使ってモグラのアクターを作成。<br>
> ``coin = Actor("coin")``コインの位置は画面左上から右に<br>
> 200px、下に200pxの設定。

<br>

**8. 画像を画面に表示** <br>
``draw()``関数を使用しアクターを画面に表示。<br>
画面の背景色を変えて、スコアを表示。
```
def draw():
    screen.fill("green")
    hedgehog.draw()
    coin.draw()
    screen.draw.text("Score: " + str(score), color="black", topleft=(10, 10))
```
> [!TIP]
> ``hedgehog.draw()``と``coin.draw()``モグラとコインを画面に表示する。<br>
> ``screen.draw.text("Score: " + str(score), color="black", topleft=(10, 10))``スコアを画面の左上に表示。

<br>

**9. 試してみる** <br>
ここまで書いたソースコードを実行。<br>
コマンドプロント（またはターミナル）のウィンドウでコマンドラインを使用して実行。
```
pgzrun
```

<br>

**10. 動作確認** <br>
モグラとコインが画面に表示され、左上にはスコアも表示される。<br>
まだプレイはできないけれど、まめに実行しバグがないかチェック。<br>
![タイトルなし](https://github.com/user-attachments/assets/1fbdf2ea-648c-4b0e-ba4b-3c4922676bf3)

<br>

**11. 関数の場所を取っておく** <br>
ゲームを完成させるために、いくつかの関数を作成する。<br>
関数のための場所取りを行う。<br>
**pass**というキーワードを使えば、今すぐ関数を定義しなくても<br>
ソースコードに場所を取っておける。<br>
後ですぐに関数を定義できるようにソースコードを入力
```
def place_coin():
    pass

def time_up():
    pass

def update():
    pass
```
> [!TIP]
> ソースコード全体の構造（つくり）を考えやすくするため。<br>
> このように関数の場所だけ取っておき、後で関数を完成させるようにする。

<br>

**12. randint()を組み入れる** <br>
関数を定義していく。<br>
最初の関数はビルドイン関数``randint()``を利用する。<br>
``randint()``をプログラムに組み入れる。<br>
場所はソースコードの先頭に入力。
```
from random import randint
```

<br>

**13. コインを置く** <br>
``place_coin()``関数を書きかえる。<br>
この関数は画面のランダムな位置にコインを置く設定。<br>
``pass``を削除して命令を書いていく。
```
def place_coin():

    coin.x = randint(20, (WIDTH - 20))
    
    coin.y = randint(20, (HEIGHT - 20))
```
> [!TIP]
> コインの画面の端からすくなくとも20px離れた位置に置かれる

> [!NOTE]
> **Python**の場合、関数内部の処理がきちんと決められないうちは、<br>
> ``pass``というキーワードだけ書いておき、後で書き換えることができる。<br>
> クイズで正解が分からないとき、「パス！」と言う似ている。<br>

<br>

**14. 関数を呼び出す** <br>
関数を定義するだけでなく、呼び出さなければならないため。<br>
ソースコードの最後にソースコードを追加。
```
place_coin()
```
> [!TIP]
> place_coin()関数の中に書いたソースコードは、この行で実行される。

<br>

**15. 時間切れ！** <br>
``time_up()``関数を定義。<br>
この関数は呼び出されるとブール関数``game_over``に<br>
``Tuue``をセットして、プログラムにゲームを終えるように設定する。
```
def time_up():

    global game_over

    geme_over = True
```

> [!NOTE]
> キーワードの**pass**を削除し新しい行は**pass**を取り去ってから入力。

<br>

**16. タイマーをセットする** <br>
``time_up()``の定義が終わったら、プログラムで呼び出すように設定。<br>
ただしゲーム開始から７秒後に呼び出す必要がある。<br>
Pygame Zero用意してある``clock``というツールを利用する。<br>
ツールは決めておいた時間がたってから関数を呼び出すためのもの。
```
clock.schedule(time_up, 7.0)
```

> [!NOTE]
> 関数``time_up()``をゲーム開始から7秒後に呼び出す。

<br>

