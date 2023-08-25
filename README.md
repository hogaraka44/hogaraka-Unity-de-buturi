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

ワールド座標とローカル座標とは
ワールド座標はUnityが定めた原点に対する座標。
ローカル座標はそのGameObjectを基準にした座標。GameObjectが回転していたら内部の座標もそれに応じて回転する。ポジションやスケールに対しても同様。

続き
ヒエラルキーのCylinderを選択(左クリック)してから右クリックしてRenameを押して名前をRollerに変更。Cylinder(5),Cylinder(6)をWire,Wire1に変更。Cube(4)をpistonに変更。

ヒエラルキーからRollerを選択してインスペクターのtransformを選択してPositionを(x,y,z)=(0,3.25,0)に、Wire、Wire1のPositionを(2.5,2.7,1.2),(6.5,2.7,1.6)に
Cylinder(1),(2),(3),(4)のPositionを(0.5,2.7,1.2),(4.5,2.7,1.2),(4.5,2.7,1.6),(8.4,2.7,1.6)に変更。Cube,Cube(1),(2),(3)のPositionを(8.4,2.7,1.1),(7.1.6,1.4),(8.5,2.6,2.4),(8.5,2.6,0.3)に変更。PistonのPositionを(10,2.7,1.4)に変更。

GameObjectを選択したのちShiftやCtrlを押しながら選択すると同時選択ができる。
Rollerを選択したのちTransformのScaleを(2,1,2)にWire,Wire(1)のScaleを(0
1,2,0.1)にCylinder(1)~(4)のを(0.4,0.2,0.4)に変更。
Scaleは左のクリップマークを押すと３方向同時に変更可能。CubeのScaleを(0.6，0.6，0.6)に変更。Cube(1)は(1,9,1),(2),(3)は(1,6,1),Pistonは(1,2.7,1)に変更。

Transformから、Roller,Cylinder(1)～(4)のRotationを(90，0，0)に変更。Wire,Wire(1),
Cube(1)～(3),PistonのRotaltionを(0,0,90)に変更。

いままでは出来合いコンポーネントを使ってきたので
ここからはコンポーネントを追加していきます。

追加したGameObjectすべてを選択した状態でインスペクタ－の一番下のAddComponetをクリックし、Rigidbodyを追加する。これで剛体の性質を持つようになった。Wire,Wire(1),PistonにFixedJointを追加、Wire,Wire(1)にもう一回FixedJointを追加する。WireのそれぞれのConnectedBodyにはCylinder(1),(2)を追加する。Wire(1)のConnectedBodyにはCylinder(3),(4)を追加する。PistonのConnectedBodyにはCubeを追加する。Cylinder(1),(3),(4)にはHingeJointを追加し、ConnectedBodyはそれぞれ、Roller,Cylinder(2),Cubeを追加、Axisは(0,1,0),Ancerは(0,-1,0)にする。

MainCameraのPositionを(10,4,15)にし、Rotationは(0,180,15)に、Cube(2)
のmeshRenderの隣のチェックを押してメッシュを非表示にする。Cylinder (1)～(4)にアセットにあるRedを追加する。追加はそれぞれのGameObjectのインスペクターかSceneビュー(画面中央部にある)にドラッグアンドドロップ


右三角の再生ボタンをクリックすると、機構が動き出す。

# 4.2　簡易的な車をスクリプトで操作する
car.unitypackageをインポートする。Car_Sampleにはサンプルが入っているため、実行ボタンから動かすことができる。

では実際に作ってみよう。car_Createに途中まで作ったものがあるためこれを使う。Body_L_Eはコピペできるので、１回コピペした後、名前をCar_Rに変更し、Rotationを(0,180,0)にする。前後が分かるようにマテリアルをタイヤかなんかに着ける。今アセットにあるBlackを使ってもいいが今回は新規でマテリアルを作る方法を紹介する。アセットのところで右クリック→Create→Material→MainMapのAlbedを変更する。それをタイヤとかに着けて前後の目印にするといい。

2つあるbodyの内片方にFixesJointを追加してもう片方のBodyとくっつける。Car_Lの子要素のCylinderどちらか一つと、Car_Rの子要素のCylinderどちらか一つにMotor.csをつけ、Car_Rの子要素のCylinderのMotor.csのLeftのチェックボックスを外す。実行時にＴキーを押すと左のモーターが前進、Ｆキーで後進,Uキーで右モータが前進、Jキーで後進する。

# 4.3 馬を走らせる
horse.unitypachageをimportするとumatyakusyokuがあるのでそれを開くと馬を走らせることができるようになる。
 
乗馬する。
MainCameraを選択し、インスペクターからAddComponentを押して入力フォームにCameraScrを入力し、NewScriptを押す。CameraScrの内容を書いたらMainCameraにとりついているCameraScr.csのhorseにbodyを入れる。再び実行すると左クリックしたとき、乗馬できるようになる。
