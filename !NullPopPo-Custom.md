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

- 派生元版はBepIn5と相性が悪い
  - ~~例外吐いてプラグイン強制終了の刑~~ (修正)
  - BepIn4時代に動作していたことは確認済
- Resources.GetBuiltinResource<Material>("Sprites-Default.mat") が失敗している
- ~~VRGIN.Modes.ControlMode:InitializeScreenCapture() で例外落ち~~ (回避)
- コイカツはUnity 5.6.2で動いてるのに UNITY_5_3 とか怪しそうだけど…
  - 派生元これでも動いてたので、この点はひとまず放置
  - というか先日、参照を5.6.2に置き換えてみたら余計悪化したらしいので戻し
