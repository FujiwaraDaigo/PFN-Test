2019年度PFNインターンシップ選考にて書いたGNNのフルスクラッチ実装です．(問題参考：https://github.com/pfnet/intern-coding-tasks/tree/master/2019/machine_learning)


添付のEigenを同じ階層に置くかパスを指定し，includeしてください.
以下コード，課題に対する簡単な説明です．

課題１
pfn_assignment1.cpp
main上で指定した行列形式のグラフGと重み行列Wに対し，集約を行い特徴量ベクトルhgをコンソール上に出力します．
グラフクラスGraphはG,Wを引数に持ち，Graph::concentration(int T)によりT回集約した後のhgを返します．
手計算で計算した結果，コードに載せた例ではノード1,2,3の特徴量は
(1,1),(1,1),(1,1) -> (3,0.4),(1.5,0.2),(1.5,0,2) -> (1.9,1.38),(1.9,1.38),(1.9,1.38)

と推移し，hgは(1.9,1.38)+(1.9,1.38)+(1.9,1.38)=(5.7,4.14）となり，実行結果と一致します．


課題２
pfn_assignment2.cpp
適当なグラフGとラベルyに対して損失を減らすようにパラメータのチューニングを行います．損失が0.01より小さくなるまで更新を続け，コンソールにランダムに生成された入力グラフG，更新により減少していく損失の値，チューニング後のパラメータW,A,bを表示します．損失を計算する処理はParameterUpdate ::LossFunction()になります．


課題３
pfn_assignment3_SGD.cpp / pfn_assignment3_mSGD.cpp
SGD,MomentumSGDにより，実データセットから学習を行い，学習結果W,A,bをコンソールに出力します.実質二つはほぼ一緒で，SGDではモーメンタム法のモーメント係数を０にしてあります．

pfn_assignment3_validation.cpp
MomentumSGDにより学習を行ったあと検定を行います．検定結果と損失の下がる様子がコンソールに表示されます．今回は学習時間がかかるのでクロスバリデーションなどは採用せず，ホールドアウト法を用います．引数となっているdataNで学習に用いるデータ数を決めれるので，今回は0~1599の1600個を学習に用いました．

課題４
pfn_assigment4_sigmoid.cpp
pfn_assignment3_validation.cppの活性化関数をReLUからsigmoidに変えたプログラムです．



