# Characteristic Analysis of Auditory Perception and Aesthetics in Sound Composition Optimization Using Revised Interactive Differential Evolution

**link:** https://dl.acm.org/doi/abs/10.1145/3377929.3398077?casa_token=MWSp4UqMb9wAAAAA:_qILfut1TOhzI1_80ZEfYEdYb6J2cmCM6XG_GkIpKismArTtWXiZTzcvbZ1otuq7DqmJcbfzlEGLEw

## 0. ABSTRACT

対話的差分進化アルゴリズムを用いて設計・実装された音構成最適化システムを用いて、聴覚の知覚と音の美的特性を解析している。  
従来の対話的差分進化アルゴリズムの母集団の初期化と交叉操作を修正したものである。  
従来の対話的差分進化アルゴリズムの交叉は、探索空間を実現可能な範囲内に維持するために修正されている。  
これは音色領域に新しいタイプの音を作り出すことを可能にする。  

この研究での主観的な評価では、被験者の好みを可能な限り満足させる音の構成に繋がる。  
5名の被験者に実験評価を行ってもらい、被験者の好みに合わせた音作りを行ってもらうことを目的としている。  
最適化過程で選択された音データを用いて、主成分分析とk-meansクラスタリング法を用いて5人の被験者の音の美的特性を分析する。  
選択された音の特性は、最適化プロセスとアルゴリズムいの収束性を説明するのに役立ち、各被験者の美的判断をよりよく理解するのに役立つ。  

この研究で生成したシステムでは、被験者の好みを満足させる音を生成でき、被験者の聴覚の特徴や音の美的感覚を分析するための効率的な手法を編み出した。

## 1. INTRODUCTION

進化計算(Evolution Computation: EC)とは、データ構造を変換・合成・選択して望む性能を実現する生物学的な進化のメカニズムを模倣した計算手法である。  
ECは、確率論の基礎をもつ最適化アルゴリズムの一つである。  
ECは最適解への収束は保証できないが、帯域的な最適値を任意に近似できる。  
主要な進化的計算アルゴリズムは以下のものがあげられる。

- 遺伝的アルゴリズム
- 進化的計算法
- 進化的戦略法
- 遺伝的計画法

ECはシステムの構造を解釈し、データを生物学的遺伝子として設計し、それを解読して生物の一個体として扱うシステムである。  
これらの個体は、与えられた基準にしたがって評価される。  
評価の高い個体のみが生き残り、個体間で遺伝子を掛け合わせて次世代の遺伝子をえるために突然変異操作を行う。  
このような操作を繰り返すのが遺伝的アルゴリズムの最適化プロセスである。  

ECの特徴は、特定の問題に依存することなく、最適化または近似最適化された解が得られることです。  
また、ECの問題点は、常に最適解が得られないことである。  
しかし、最適解ではないが実用的な範囲内の解を求めるのにかなり有効である。  

ECアルゴリズムにはいくつかの実装例があるが、対話的進化計算(Interactive Evolution Computation: IEC)もその一つである。  
IECは、ECを実際の人間の主観的な評価を加えた最適化手法である。  
IECの目的は、人とコンピュータとの間のコミュニケーションにおいて、実在の人間の嗜好や感性に適した解を作り出すことである。  
人の感情評価のようにコンピュータで推定できない問題に適用される。  
例えば、以下の分野でIECは使われる。  

- 服のコーディネート
- 部屋のデザインや配色
- ゲーム内のオリジナルキャラクターの顔のデザイン
- 3次元空間での音楽やカメラワークの映像など、人間の主観的な評価による最適化ツール

機械学習手法との連携や人間の知覚の分析はIEC研究でのパースペクティブ科目である。  
この研究では、個人の好みを満足させるための音の構成が動機となっている。  
音を構成する要素

- ラウドネス(大きさ)：振幅
- ピッチ(高さ)：周波数
- 音色：形状

ラウドネスとピッチは、単純に音信号の物理的な測定によって決定されるが、音色は単一の物理的な測定によって記述・表現することが困難である。  
なので、人の音響的嗜好を満足させる音の構成は、難しい最適化問題である。  
この研究ではKomoriによるLet's play for free sound effects!のよく設計された5つの自然音を初期化母集団として用いて対話的差分進化アルゴリズムの微分機構を用いて、人間の主観的評価のための混合音を合成する。  
改良版IDEは既存の音から初期母集団に当たる混合音を生成する。 
対話的アルゴリズムは評価プロセスにおけるユーザの疲労を軽減するためにペア比較を行っている。  
この研究では、5名の被験者に対して自分の主観的な評価と好みの音を合成するための評価を行った。  
選定された音声信号を主成分分析とk-meansクラスタリング法を用いて分析した。  
これらの比較分析から、評価参加者の聴覚と音の美的特性を調査した。  

この導入部に続いて、第2節では差分進化アルゴリズムの概要を説明し、改定されたIECについて紹介する。  
第3節では、改定されたIECを用いた音構成最適化の問題と開放を提示し、設計を行う。  
第4節では評価実験を行い、実験の設計、実験パラメータの設定、実験データの解析方法など実験結果を分析する。  
第5節では、主成分分析とk-meansクラスタリング法を用いて音の選択、聴覚知覚、美的特性のユーザ嗜好を調査し、考察する。  
評価における被験者の分析、被験者毎の聴感の発見、最適化プロセスの説明にこのような方法を用いたことは、この研究の独自性を示すものである。  
最後に第6節でこの研究の結論と今後の課題を記している。  

## 2. INTERACTIVE DIFFERENTIAL EVOLUTION

### 2.1. Differential Evolution

差分進化(DE)は、与えられた評価規模で候補解を改良し、問題を最適化するECアルゴリズムの一つである。  
アルゴリズムが比較的単純であり、強力な探索能力により収束が早いのが特徴である。  
母集団の分布規模に関する間接的な情報を持つ個体間の差分情報を用いてベースとなる個体を中心に探索することで、一つの親こたいから一つの子孫個体が生成される。  
子孫個体が親個体を超えた場合のみ、親個体を子孫個体に置き換える。  
最適化の過程で個体分布が徐々に狭くなるため、グローバルな探索と局所的な搾取を自動的にバランスさせることができる。  
差分進化アルゴリズムのステップは以下の通りである。  

1. 母集団を初期化する
1. 一個の個体を取り出し、それを基底ベクトルとする
1. 残りの個体からランダムに二つの個体を取り出し、差分ベクトルを生成する
1. その中からランダムまたは最良の個体を一つ取り出す
1. 基底ベクトルに加重微分ベクトルを加えて変異体ベクトルを生成する
1. 基底ベクトルと変異ベクトルを比較し交叉させてトライアルベクトルを生成する
1. 基底ベクトルと試験ベクトルの的合成を比較しより良い方を次の世代に存続させる
1. (2)に戻りループ

(2)から(5)を数式に表すと、  
**mutant vector = base vector + F * differential vector**  
となる。  

式中のFは、差分ベクトルの大きさを調整するための0から2までの重み定数であるスケールファクターである。

## 6. CONCLUSION

この研究では、改訂された対話型差分進化を用いて、利用者の主観的な評価を反映した音作りの手法を提案した。  

実験では、5個体それぞれに10秒の音源を初期化した。  
5人の被験者が各個体をペア比較によって8世代に渡って評価を行った。  
その結果から被験者の好みに近い音を作り出すことができた。  

実験データを主成分分析を用いて解析し、選択した音の特徴を可視化した。  
最終世代の各個体を主成分の1点のみでグラフで単純に表すことが可能である。  
さらに、選択された音をk-means法でグループに分類し、それらのグループを分析することで、被験者が選択した音の特徴や被験者間の関係性を見ることができるようになった。  

また、改訂IDEを用いて、被験者の聴覚の美学的特徴を調査・分析した。  
主成分分析やk-meansなどの機械学習法は、実験対象者の美的洗濯を分析・可視化することができる。  

改訂IDEで被験者の好みに近い音を出せるようにするには、被験者の数が必要である。  
そして、実験後に、被験者に好みの音を出すことができたかどうかを問う内容をさらに精査する必要がある。  
実験に使用したシステムについては、作成した音の何がよくて何が悪かったのかを被験者に詳しく聞き、より明確にすることで分析していく。  
さらに参加者を増やして実験を続け、提案した方法でシステムの妥当性を検証していく。  

被験者には1回の評価に10秒以上の音を聞いてもらう必要があるため、1回の実験に費やす時間がやや長くなってしまう(一人の被験者に対して20~30分程度)。  
さらに、DEアルゴリズムを適用した後、必ず1個体をペア比較で評価している。  
これにより、実験終了まで少なくとも40回は評価を繰り返すことになる。  
そのため、必然的に被験者の疲労が増大する。  
よって、被験者の疲労を軽減することは、IECを実用化するための用件の一つである。  

今後は、より短い音源を用いて1回の実験時間を短縮し、評価回数を少なくして、ユーザの好みに近い音を実現する方法を検討していく。  
