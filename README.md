# UE5_NewAnimSystemsSample
UE5のアニメーションに関する新機能をかんたんに確認・検証するために用意したサンプルです。  
各機能のON/OFF・プロパティを制御するUIを使って、標準のアニメーションに新機能を適用した際の効果を見ることができます。また、サンプルにあるAnim Blueprint（ABP_UE5AnimSystemSample）を見ることで、各新機能の使用方法についても確認できます。

現時点では、下記機能を試す・確認することができます。
- Pose Warping
  - Stride Warping
  - Orientation Warping
  - Slope Warping
  - Foot Placement
- Distance Matching
- Blueprint Thread Safe Update Animation
- Anim Node Functions
- Property Access

各機能の概要に関しては公式ドキュメント、または下記スライドをご確認ください。  
[猫でも分かる UE5.0, 5.1 におけるアニメーションの新機能について【CEDEC+KYUSHU 2022】](https://www.docswell.com/s/EpicGamesJapan/ZY3PDK-UE_CEDECKYUSHU2022_UE5Animation)

# 動作環境
UE5.1

# 注意：サンプルを動かす前に
EULAによりエンジン標準のTemplate以外のアセットをサンプルに含めることができないため、本サンプルにてDistanceMatchingを試すには外部から「移動からの停止」アニメーションを別途用意する必要があります。

RootMotionなアニメーションであれば何でもよいのですが、本サンプルでは下記無料アセットを使用することを想定しています。  
[MCO Mocap Basics
](https://www.unrealengine.com/marketplace/ja/product/28fc3cc4332541e3b0037d67a65e5d6d?sessionInvalidated=true)

## DistanceMatching用アセットのセットアップ手順

1. [MCO Mocap Basics
](https://www.unrealengine.com/marketplace/ja/product/28fc3cc4332541e3b0037d67a65e5d6d?sessionInvalidated=true)をプロジェクトに追加
2. Content/MCO_Mocap_Basics/Animation/Mobility_Pro/Root_Motion/MOB1_Jog_F_to_Stand_Relaxed_RU に対してリターゲットを実行  

<img src="https://user-images.githubusercontent.com/8957600/206977489-0322ffdf-f3aa-4f33-9000-38f88b4ae94a.png" width="50%">　
<img src="https://user-images.githubusercontent.com/8957600/206977661-aaa0567f-25ad-473c-9219-d6f0ca3cbc5b.png" width="50%">

3. 2で生成したAnimationSequence を MM_Stop にリネーム  
4. MM_Stopを開き、EnableRootMotion と Force Root Lockを有効に

![image](https://user-images.githubusercontent.com/8957600/206978077-eebd2207-2af7-4ba1-a5f4-e38beca109a8.png)  
5. DistanceCurveModifierを適用し、Rootボーンの移動量からAnimCurveを生成
6. 
<img src="https://user-images.githubusercontent.com/8957600/206978830-a3654861-22f2-4aea-901f-81fd42607b7e.gif" width="50%">

