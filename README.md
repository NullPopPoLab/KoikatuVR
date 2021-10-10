# NullPopPo-Custom
[詳細](https://github.com/NullPopPoLab/KoikatuVR/blob/master/!NullPopPo-Custom.md)

以下、fork元
---
# Ooetksh 追記

当 KoikatuVR は BepInEx 用のプラグインです（*IPAは不要*）。

[Releases](https://github.com/Ooetksh/KoikatuVR/releases) ページをご覧ください。

---

obtdai様版の[VRGIN.Template](https://github.com/obtdai/VRGIN.Template)を触ってなんとかコイカツ本編をVRで操作できるように**したい**もの

極めて実験的なバージョンです。いろいろと不便ですし、不具合が起こる可能性も高いですので、そういったことをご理解いただいた上で自己責任でお願いします。

# 導入方法
1. [release](https://github.com/vrhth/KoikatuVR/releases)から最新のzip（full）を落とす
1. 中身を全てインストールフォルダにコピーする（Koikatu.exeとIPA.exeを同じ階層になるように）
1. Koikatu.exeをIPA.exeにドラッグ&ドロップ
1. Koikatu_Data/globalgamemanagersを修正する
    1. [UABE](https://github.com/DerPopo/UABE/releases)でglobalgamemanagersを開く（確認時のバージョンは2.2 beta2）
    1. Path ID列が11のTypeがBuild Settingsとなっている行を選択しExport Dumpする
    1. 作成されたダンプファイルをテキストエディタで開き下の囲みの通り修正する
    1. 修正したものをImport Dumpする
    1. 保存する (上書きしようとすると失敗するので他の名前か場所で保存してUAB閉じてから移動、このとき、保存先をデスクトップにするとファイルが壊れるという報告あり)
    ~~~
    修正前
    0 vector enabledVRDevices
    0 Array Array (0 items)
    0 int size = 0

    修正後
    0 vector enabledVRDevices
    0 Array Array (2 items)
    0 int size = 2
    [0]
    1 string data = "None"
    [1]
    1 string data = "OpenVR"
    ~~~
    
1. --vrをつけて起動するか、SteamVRが起動している状態で起動する（--novrをつけて起動するとSteamVRが起動していても通常モードになる）

<br />
必要ならfork元も参考にして下さい

obtdai様版（ベースにさせて頂いています）

[VRGIN](https://github.com/obtdai/VRGIN)

[VRGIN.Template](https://github.com/obtdai/VRGIN.Template)

Eusth様版（更に元、オリジナルです）

[VRGIN](https://github.com/Eusth/VRGIN)

[VRGIN.Template](https://github.com/Eusth/VRGIN.Template)

# 操作方法
新たに学校のアイコンのツールが追加されています

このツールの状態での操作（oculusでやってるのでviveでの確認してません）

※ポインターが浮いてるウィンドウにあたってるときはこれらの操作はできないので注意

* トリガー

HMDが向いている方向に移動（カメラも追従）

VRSettings.xmlで目線の高さを変更できます

UsingHeadPosがtrueのときはキャラクターの目線の高さ、
falseのときはStandingCameraPosとCrouchingCameraPosの値による高さになります

オマケ：しゃがむとその高さになるので実際にしゃがみながらやると楽しい

※ダッシュだと酔いやすい＆操作しにくかったので、歩き（Shift押し）にしてます。

※酔い注意（特にキャラクターの目線の高さを使うと歩くとき上下に揺れるので酔いやすい）

* HMDの高さによる立ちしゃがみの切り替え

HMDの高さが一定を下回る（上回る）としゃがみ（立ち）ます
VRSettings.xmlのCrouchByHMDPosで有効無効、
CrouchThrethouldとStandUpThrethouldでどの高さで実行するかを設定できます
※値はHMDの基準位置とHMDの現在位置の差

* グリップ

カメラの位置にプレイヤーキャラを移動

押しっぱなしで現実で動くと仮想空間でも動き回れる

* スティック（タッチパッド）

上 F3

下 F4

左 左回転

右 右回転

中央 右クリック

※全て倒すだけでなく押し込む必要あり

VRSettings.xmlを書き換えることで割り当てを変えることができます。

* 歩く WALK
* 走る DASH
* ファンクションキー そのまま ex) F3
* マウスボタン LBUTTON / RBUTTON / MBUTTON
* その他のキー VK_をつける ex) VK_A
* 回転(45度) LROTATION / RROTATION
* 押している間しゃがむ CROUCH
* カメラの位置にプレイヤーキャラを移動 PL2CAM
* キー配置の切り替え NEXT

<details><summary>設定例</summary><div>
(トリガーで歩き、グリップしている間しゃがむ、↑設定/→マップ移動/←ステータス/・右クリ)と
(トリガーでダッシュ、グリップしている間HMDの位置にキャラを移動、↑左クリ/←→左右回転/・中央クリ)を↓を押すたびに切り替える
    
~~~
  <KeySets>
    <KeySet>
      <Trigger>WALK</Trigger>
      <Grip>CROUCH</Grip>
      <Up>F1</Up>
      <Down>NEXT</Down>
      <Right>F3</Right>
      <Left>F4</Left>
      <Center>RBUTTON</Center>
    </KeySet>
    <KeySet>
      <Trigger>DASH</Trigger>
      <Grip>PL2CAM</Grip>
      <Up>LBUTTON</Up>
      <Down>NEXT</Down>
      <Right>RROTATION</Right>
      <Left>LROTATION</Left>
      <Center>MBUTTON</Center>
    </KeySet>
  </KeySets>
~~~
</div></details>
<br />

* ぱいタッチなど、3Dモデルをクリックする操作について

会話時は、VR上で真正面にアップで表示されている状態にしてウィンドウの真ん中らへんをクリックでなんとか（ようはHMDじゃなくて通常のディスプレイのほうでの表示をクリックする）

H時は不可能ではないもののウィンドウ内でのマウスの位置と対応する3D空間での位置がわかりにくすぎるので、困難
（本編で愛撫で絶頂させる必要がある場合はマクロの使用を推奨）

* リモコン操作

以前の通りマウス左クリック（MenuToolのトリガー）でリモコン操作できるので、場面によってはそのほうが便利かも

# その他改善点
開始時にStandingModeで始まるように（Ctrl+C, Ctrl+C不要）

自動でApplyEffectsするように（VRSettings.xmlでOFFにできます）

ApplyEffects時（Ctrl+F5）に同時にHDRを許可するように（ピンクや緑の変な色になるの対策）

# 既知の不具合など
* ウィンドウが真っ白になったままフリーズすることがある（例えば、F3を開いたままゲームを進めるなど本来不可能な操作をした場合？）
* キャラクターのレイヤーのライティングがおかしくなることがある（光があたっていない状態になる、HMDの向き→ActionCameraの向き→DirectionalLightの向きと影響してるせいでたまたま影になる方向になるだけ？）
* マウスがきかなくなるときがある（非VRでポインタ表示されない状態のときの処理を無効化してるのが戻ってしまうときがある）。メニュー出すなど非VR環境でポインタ表示される状態にすれば一応操作はできる（もちろんその際は移動できない）。
* 向きの対応がおかしくなることがある（ワープツールで方向転換した後など？）
* 頭消しやカメラコントロールがうまくいかない場合がある（学校ツールに切り替えるタイミングや、そのときのカメラとプレイヤーの位置などによる？）
* 移動時障害物にひっかかるとカメラとの対応がおかしくなる
* KeySetが複数ある場合に、現在どれになっているのか確認できない
* 設定できるようになりました ~~ホイールクリックが未割当（WindowsInput.InputSimulator.Mouseになかったんだもん）~~
* 作者様が対応版を出してくださいました ~~GOLのCameraCtrlOffと競合するのでgolconfig.iniから抜くとかして下さい~~
* たぶん治った ~~近づいたときにキャラが消える（ゲーム側で、固定キャラ以外はカメラとかさなると消えるようになってる模様）~~
* 自動適用のタイミングで起こらないのでひとまず問題なし ~~Ctrl + F5をするタイミングによって色がおかしくなる（夜の家でやるとダメなのでロード直後注意、他ダメなシーンあるかは不明。大丈夫なところで一回適用してしまえば、後は大丈夫）~~
* たぶん治った ~~自動でFPSモードになる場面（トイレやシャワーなど）でプレイヤーキャラが消える（以後戻らない）~~~

