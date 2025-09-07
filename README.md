# Python Coin Collection

## 事前準備

Pygame Zeroのインストール(Windows環境)<br>

1. コマンドプロンプトを開く<br>
2. パッケージマネージャーをインストールする<br>
```
python -m pip install -U pip
```
4. pygameのインストール<br>
   パッケージマネージャーをインストールしたら下記の<br>
   命令文を入力しENTERキーを押すこれでPygameがインストールされます。<br>
   ```
   pip install pygame
   ```
5. Pygame Zeroのインストール<br>
   最後に下記の命令文を入力しENTERキーを押す。<br>
   これでPygame Zeroがインストールされる。<br>
   ```
   pip install pgzero
   ```

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
![タイトルなし](https://github.com/user-attachments/assets/d51bce33-e915-4340-a28e-f117e39332b9)




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
**実行方法**
1. コマンドプロント/PowerShell(どちらかを実行)<br>
2. コマンド
```
 pgzrun ディレクトリ\coin.py
```
![タイトルなし](https://github.com/user-attachments/assets/1fa3ae4e-39ff-4a3d-ba11-078917d99228)
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

    game_over = True
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

**17. ゲームを終わらせる** <br>
ゲームを開始して7秒経過すると、``clock.scgedule``が``time_up()``関数を呼び出してゲームを終わらせる。<br>
でもプレイヤーの最終スコアを表示しなければならない、その為に``draw()``関数に少しソースコードを書き足します。<br>
```
    if game_over:
        screen.fill("pink")
        screen.draw.text("Final Score: " + str(score), topleft=(10, 10), fontsize=60)
```
> [!NOTE]
> 変数**game_over**がTrueなら画面の背景色をピンクに設定<br>
> ``str(score)``最終スコアを画面に表示する。<br>
> ``fontsize=60``この命令は画面に表示する文字の大きさを決めている。<br>

**18. update()を使う** <br>
``update()``関数を定義していきます。<br>
この関数は**Pygame Zero**に用意されていて、他の関数とは違い<br>
いつ呼び出すかプログラマーが心配しなくてもいい。<br>
定義さえしておけば、**Pygame Zero**が1秒間に60回も自動的に呼び出してくます。<br>
``def update()``の下に下記のソースコード書き入れる。<br>
```
    if keyboard.left:
        hedgehog.x = hedgehog.x - 2
```
これでキーボードの左向き矢印キーを押したとき、キャラクターが左に動くようになる。<br>

> [!NOTE]
> ``hedgehog.x = hedgehog.x - 2``左向き矢印キーが押されたときキャラクターが<br>
> 左に2ピクセル動きます。

<br>

**19. 上下左右に動かす** <br>
ソースコードをテストし、キャラクターを動かし他の方向にも動くように設定。<br>
```
    elif keyboard.right:
        hedgehog.x = hedgehog.x + 2
        
    elif keyboard.up:
        hedgehog.y = hedgehog.y - 2

    elif keyboard.down:
        hedgehog.y = hedgehog.y + 2
```
> [!NOTE]
> どの``elif(else-if)``で分岐するかは、<br>
> どの矢印キーが押されたかで決まる。<br>

**20. コインを集める** <br>
最後にキャラクターがコインにタッチしたときに<br>
スコアを変えるためのソースコードを書いておきます。<br>
``update()``関数に書き加えます。<br>

```
    global score
```
関数を定義しているソースコードの最初に書きます。

```
    coin_collected = hedgehog.colliderect(coin)
```
キャラクターがコインにタッチしたらこの変数がTrueになります。

```
    if coin_collected:

        score = score +10

        place_coin()
```

ここでスコアに10を足しています。

**21. ゲーム完成** <br>
ゲームをプレイしてゲームオーバーまで何枚のコインを集められるか<br>
挑戦してみましょう。<br>
<br>
プレイ方法ファイルをDLして
1. コマンドプロント/PowerShell(どちらかを実行)<br>
2. コマンド
```
 pgzrun ディレクトリ\coin.py
```
**※Pygame Zeroがインストールされている環境**



