# **Lab 01 – 準備**

## ***Step 1（ログイン）***

[VANTIQ の開発環境](https://dev.vantiq.co.jp) にログインします。


## ***Step 2（作成する Namespace の解説）***

講師がいる場合と講師がいない場合で作成する Namespace が異なります。  

<details>
<summary>講師がいる場合</summary>

講師がいる場合は下記の Namespace を作成してください。  

- [ポンプ故障検知システム用のNamespace（例：PumpFailureDetectionNS）](#ポンプ故障検知システム用の-namespace-の作成)
</details>

<details>
<summary>講師がいない場合</summary>

講師がいない場合は下記の Namespace を作成してください。

- [ポンプ故障検知システム用のNamespace（例：PumpFailureDetectionNS）](#ポンプ故障検知システム用の-namespace-の作成)
- [データジェネレーター用のNamespace（例：TrainingDataGenNS）](#データジェネレーター用の-namespace-の作成)
</details>


## ***Step 3（Namespace の作成）***

### ポンプ故障検知システム用の Namespace の作成
1. 「新規 Project」ウィンドウが表示されるので、「新規 Vantiq Namespace」を選択し、Name に **ポンプ故障検知システム** 用の Namespace 名を入力して、「_続行_」をクリックします。  
（例：PumpFailureDetectionNS）  
  <img src="../../imgs/Lab01/image0.png" width=70%>

1. 「新規 Project」ウィンドウが表示されるので「空の Project」を選択し、「_続行_」をクリックします。  
   ＊ 既に Project が存在する場合は表示されません。  

   <img src="../../imgs/Lab01/image2.png" width=58%>

   ＊ ウィンドウが表示されない場合は、ナビゲーション バーにある以下の入力欄に「**PumpFailureDetection**」と入力し、隣の **保存** ボタンをクリックしてください。また次の手順をスキップしてください。  

    <img src="../../imgs/Lab01/image3.png" width=80%>

1. 「Project Name」に 「**PumpFailureDetection**」と入力し、「_終了_」をクリックします。  

    <img src="../../imgs/Lab01/image4.png" width=68%>

1. Project 名に「`PumpFailureDetection`」と表示されていることを確認します。  

    <img src="../../imgs/Lab01/image5.png" width=90%>


### データジェネレーター用の Namespace の作成
※講師がいない場合のみ実施してください。

<details>
<summary>講師がいない場合</summary>

1. 現在の Namespace が データジェネレーター用の Namespace になっていることを確認します。  

1. 「管理」 > 「Namespace」を開き、_+ 新規_ ボタンをクリックして、「新規 Namespace」ウィンドウを開きます。  

1. Namespace に **データジェネレーター** 用の Namespace 名を入力して、「_変更の保存_」をクリックします。  
（例：TrainingDataGenNS）  
  <img src="../../imgs/Lab01/image01.png" width=70%>

1. ナビゲーション バーで、現在の Namespace 名をクリックし、「Namespace の変更」ダイアログを表示します。  
上記の手順で作成した データジェネレーター用の Namespace を選択して、Namespace を切り替えます。  

1. 「新規 Project」ウィンドウが表示されるので「キャンセル」をクリックします。  
   ＊ 既に Project が存在する場合は表示されません。  
</details>

#### 参考
  - [2.3: リソースの整理](https://community.vantiq.com/courses/vantiq%e3%82%a2%e3%83%97%e3%83%aa%e3%82%b1%e3%83%bc%e3%82%b7%e3%83%a7%e3%83%b3%e9%96%8b%e7%99%ba%e3%82%b3%e3%83%bc%e3%82%b9%ef%bc%86%e3%83%ac%e3%83%99%e3%83%ab1%e8%aa%8d%e5%ae%9a%e8%a9%a6%e9%a8%93v1-2/lessons/2-vantiq%e3%83%97%e3%83%a9%e3%83%83%e3%83%88%e3%83%95%e3%82%a9%e3%83%bc%e3%83%a0%e3%81%ae%e7%b4%b9%e4%bb%8b/topic/2-3-%e3%83%aa%e3%82%bd%e3%83%bc%e3%82%b9%e3%81%ae%e6%95%b4%e7%90%86/)


## ***Step 4（データジェネレーターのインポート）***
複数台のポンプにそれぞれ取り付けられた温度センサーと回転数センサーからのデータを擬似的に発生させるデータジェネレーターを準備します。  

※講師がいない場合のみ実施してください。  

<details>
<summary>講師がいない場合</summary>

1. 現在の Namespace が データジェネレーター用の Namespace になっていることを確認します。  

1. 「Projects」 > 「インポート...」 を開き、「Project またはデータのインポート」ウィンドウを開きます。  
   事前に配布したデータジェネレーターの zip ファイル 「[`TrainingDataGen.zip`](https://github.com/fujitake/vantiq-related/raw/main/vantiq-apps-development/1-day-workshop/conf/TrainingDataGen.zip)」をドラッグ&ドロップします。  

   <img src="../../imgs/Lab01/image006.png" width=70%>

1. 「_インポート_」をクリックします。

1. インポートすると確認ダイアログが表示されるので「_リロード_」をクリックします。
</details>

## ***Step 5（MQTT Broker の設定）***<a id="mqtt_broker_setting"></a>

サンプルデータを生成するためのサーバーの設定を MQTT Broker に設定します。  

※講師がいない場合のみ実施してください。  

<details>
<summary>講師がいない場合</summary>

1. 現在の Namespace が データジェネレーター用の Namespace になっていることを確認します。  

1. 「追加」 > 「Source...」 を開き、「Sources」ウィンドウを開きます。

1. `TrainingDataGenMQTT` をクリックし、「Source」ウィンドウを開きます。

1. 「Server URI」タブをクリックします。

1. 「編集」(小さい鉛筆) アイコンをクリックし、「Server URI の編集」ダイアログを開きます。  

   <img src="../../imgs/Lab01/image02.png" width=60%>

1. 「Server URI:」には、仮の値が設定されているので、ご自身で準備された MQTT Broker サーバーの URI に設定し直してください。「OK」をクリックします。  
   （例：mqtt://public.vantiq.com:1883）  
   | <img src="../../imgs/Lab01/image03.png" width=60%> |
   | ----- |

1. タイトルバーの右上にある _アクティブ状態オンに_ アイコンをクリックして、Source をアクティブにします。

   <img src="../../imgs/Lab01/image002.png" width=60%>

1. 隣にある _変更の保存_ アイコンをクリックして、保存します。

</details>




## ***Step 6（データジェネレーターの設定）***<a id="data_generator_setting"></a>

本ワークショップでは複数台存在するポンプそれぞれに温度センサーと回転数センサーが設置されており、データが送信されるという状況を前提にアプリケーションの作成を進めます。  
データジェネレーターを使用して、その状況を擬似的に再現します。  

<img src="../../imgs/Lab01/image7.png" width=80%>  

※講師がいない場合のみ実施してください。  

<details>
<summary>講師がいない場合</summary>

1. 現在の Namespace が データジェネレーター用の Namespace になっていることを確認します。  

1. 「TrainingDataGeneratorClient」の「起動」 > 「_現在保存されているClientをClient Launcher(RTC)で実行_」をクリックし、データジェネレーターをブラウザーで開きます。  

   ＊ 今回のように VANTIQ で開発された Client は「**VANTIQ Client Launcher**」というアプリケーションで起動できます。

    ![RTC](../../imgs/Lab01/RTC.gif)  


1. データジェネレーターを開いたら、上部にある _Setup_ をクリックします。

   ![Setup button](../../imgs/Lab01/image9.png)  

1. テキストボックスに「_5_」と入力します。（＊ 半角で入力してください。）

    <img src="../../imgs/Lab01/image010.png" width=25%>

1. _Update Number Pumps_ ボタンをクリックします。

1. 表に PumpNo 1\~5 が表示されていることを確認します。

1. MQTT の Topic 名を以下のように入力します。  

   RPMSSensor Topic： "_/***unique name***/pump/RPMS_"

   TempSensor Topic： "_/***unique name***/pump/Temp_"

   ＊ **_unique name_** の箇所には **会社名+お名前** など **他人と重複しない** 任意の値を入力してください。また、topic 名に**ダブルクォーテーションは含みません**。topic 名の**前後に半角スペースが入らないよう**にしてください。  

1. _Update Topics_ ボタンをクリックします。

   <img src="../../imgs/Lab01/image11.png" width=78%>

1. 上部にある _Date Generator_ をクリックし、画面を切り替えます。

   ![Data Generator](../../imgs/Lab01/image12.png)

1. _Start Generator_ ボタンをクリックし、約 6秒後に 「Last Message」 ウインドウにデータが表示されることを確認します。
</details>

## ***Step 7（開発画面に戻る）***

Namespace を **ポンプ故障検知システム** 用の Namespace に切り替えます。  

※講師がいない場合のみ実施してください。  

<details>
<summary>講師がいない場合</summary>

1. データジェネレーター画面から、予め開いていたタブの **VANTIQ の開発環境画面（https://dev.vantiq.co.jp）** に戻ります。

1. ナビゲーション バーで、現在の Namespace 名をクリックし、「Namespace の変更」ダイアログを表示して、 **ポンプ故障検知システム** 用の Namespace に切り替えます。

1. Project 名に「`PumpFailureDetection`」と表示されていることを確認します。

   <img src="../../imgs/Lab01/image5.png" width=90%>
</details>

## このセッションのまとめ

ここまでの手順で、 VANTIQ で開発を行う準備が整いました。  

最後に作成した Namespace と Project を確認しましょう。  

<details>
<summary>講師がいる場合</summary>

1つの Namespace に 1つの Project が存在しているはずです。  
- Namespace：PumpFailureDetectionNS（例）
  - Project：PumpFailureDetection
</details>

<details>
<summary>講師がいない場合</summary>

2つの Namespace が存在しており、それぞれに1つの Project が存在しているはずです。  
- Namespace：PumpFailureDetectionNS（例）
  - Project：PumpFailureDetection
- Namespace：TrainingDataGenNS（例）
  - Project：TrainingDataGen
</details>

＊ `PumpFailureDetection` Project を表示してください。

＊ 以上で、ワークショップの準備は終了です。

## ***▷確認ポイント***

各 Lab の最後には「**確認ポイント**」のステップが設けられています。ミスしやすい、または理解を深めるためのポイントが記載されておりますので、必ず目を通して理解するようにしてください。

<details>
<summary>講師がいる場合</summary>

- 開いている Project が正しいか
  - 皆様の環境には、1つの開発用 Namespace があるはずです。
  - **ポンプ故障検知システム** 用の Namespace には、 **ポンプ故障検知システム** を構築するために使用する Resource を追加していく `PumpFailureDetection` Project (今はまだ空の状態) が存在しています。
  - 次の Lab から `PumpFailureDetection` Project で作業を行います。
</details>

<details>
<summary>講師がいない場合</summary>

- 開いている Project が正しいか
  - 皆様の環境には、2つの開発用 Namespace があるはずです。
  - **ポンプ故障検知システム** 用の Namespace には、 **ポンプ故障検知システム** を構築するために使用する Resource を追加していく `PumpFailureDetection` Project (今はまだ空の状態) が存在しています。
  - **データジェネレーター** 用の Namespace には、データジェネレーターで使用している Resource を確認できる `TrainingDataGen` Project が存在しています。
  - 次の Lab から `PumpFailureDetection` Project で作業を行います。

- データジェネレーターに設定している Topic が正しいか
  - 温度の Topic として回転数の Topic を設定してしまうなどの間違いがあると、この後開発していくシステムが正しく動作しません。改めて正しく設定されていることを確認しましょう。  
  ✔︎   **RPMS** SensorTopic： /***unique name***/pump/**RPMS**  
  ✔︎   **Temp** SensorTopic： /***unique name***/pump/**Temp**
</details>

## Vantiq 1-day Workshop 次のセッション  
|Session #|Session      | Type  |Contents Description       |Duration (m)|Material               |
|:-----:|--------------|:------:|---------------------------|:-:|--------------------------------|
| 3 | Vantiq の基本リソース | Lecture | Vantiqアプリケーションを構成する最も基本なリソース | 15 | [00_BasicResources](0-10_BasicResources.md) |
