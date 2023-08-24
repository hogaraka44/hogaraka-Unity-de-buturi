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
タブ・ヒエラルキー・インスペクター・コンポーネント・アセット
タブとは
FileやEditが並んでいるところ

ヒエラルキーとは
画面左のDirectionnal LightやMain Cameraが並んでいるところ。GameObject型で定義されたゲームオブジェクトが並んでいる。

インスペクター
画面右のゲームオブジェクトの詳細にまつわるものが、コンポーネントやC#形式で記載されているところ。

コンポーネント
簡単に扱いやすくパッケージ化されたC#スクリプト。コンポーネントの定義自体を書き換えるのは簡単ではない。

アセット
画面下にあるファイルやコンポーネントの並んでいるところ

# 4.1　Unityを触ってみる
機構について参考 https://jp.misumi-ec.com/tech-info/categories/machine_design/md10/c1129.html

完成版のパッケージのインストール
kikou.unitypackageをアセットのところにもっていくと画面右側にImport Unity Pachageが出るので、Importを選択。
kikouをダブルクリックして選択し、画面上の右三角マークの再生ボタンをクリックするとスライダ・クランク機構が動き出す。

# 4.2　スライダ・クランク機構を作る　
GameObjectタブ→Create Empty、それをタップしてから再びGameObject→3DObject→Cylinderをタップ。Cylinderをタップした状態でコピペしてこれを７個用意。
GameObject→3DObject→Cubeを選択しキューブを５個用意。こうすることでGameObjectがローカル座標で定義される。

ワールド座標とローカル座標について
ワールド座標はUnityが定めた原点に対する座標。
ローカル座標はそのGameObjectを基準にした座標。GameObjectが回転していたら内部の座標もそれに応じて回転する。ポジションやスケールに対しても同様。
