# KoikatuVR 改良実験

## 第1目標

- BepIn5 というか HF Patch との共存

## 第2目標

- インタフェイス改善

## 最終目標

- この延長で自作VRゲームを作る(妄想)

# 改善済

(まだ)

# 現状わかっている問題点 

- ~~派生元版はBepIn5と相性が悪い~~ (濡れ衣の可能性)
  - ~~例外吐いてプラグイン強制終了の刑~~ (修正)
  - ~~BepIn4時代に動作していたことは確認済~~
  - ここでひとつ驚愕の事実、BepIn外して元のIPA版MODを改めて確認してみたら、同様に画面表示されなくなってる
  - 当時のOpenVR APIが今のSteamVRに適応できない疑い
- Resources.GetBuiltinResource<Material>("Sprites-Default.mat") が失敗している
- ~~VRGIN.Modes.ControlMode:InitializeScreenCapture() で例外落ち~~ (回避)
- コイカツはUnity 5.6.2で動いてるのに UNITY_5_3 とか怪しそうだけど…
  - 派生元これでも動いてたので、この点はひとまず放置
  - というか先日、参照を5.6.2に置き換えてみたら余計悪化したらしいので戻し
  
## というわけで、第0目標

- ~~今のSteamVRで動くOpenVRフレームワークを新規に組む~~
  - ここで悲しいお知らせです。Unity 5.6.2でSteamVR 1.2.3のサンプルシーンが動作しませんでした。
  - SteamVR2系はいろいろめんどいので保留
- 当時使ってたOculus APIが一応動作するみたいなので、ひとまずこっちで試す
- これをMOD経由で起動
