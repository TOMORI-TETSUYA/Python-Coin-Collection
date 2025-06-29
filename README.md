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
