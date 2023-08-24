# unityで物理
# 1.導入(windows)版の場合
はこちらを参考https://forpro.unity3d.jp/tutorial/unity-install-windows/
そしたらhttps://unity.com/ja/downloadに飛んでソフトをダウンロード
windows版をダウンロードをクリックしたらあとは同意していく。
# 2.注意点のまとめ
・初回unity　hub起動時には画面左上の人型アイコンをクリックし、ドロップダウンメニューから「サインイン」を選択し
サインインしておくことをお勧めする
・ライセンスはPersonalでいい
・Microsoft Visual Studio Community 2019をインストール
vs codeでインテリンスできるらしいが手順が多いため
・今回はunity 2021.3.29で解説するが基本的な操作に変わりはない
# 3.Unityの画面と用語
タブ・ヒエラルキー・インスペクター・コンポーネント
タブとは
FileやEditが並んでいるところ

ヒエラルキーとは
画面左のDirectionnal LightやMain Cameraが並んでいるところ。GameObject型で定義されたゲームオブジェクトが並んでいる。

インスペクター
画面右のゲームオブジェクトの詳細にまつわるものが、コンポーネントやC#形式で記載されているところ。

コンポーネント
簡単に扱いやすくパッケージ化されたC#スクリプト。コンポーネント自体を書き換えるのは容易ではない。

# 4.スライダ・クランク機構を作る
機構について参考 https://jp.misumi-ec.com/tech-info/categories/machine_design/md10/c1129.html

