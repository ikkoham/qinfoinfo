+++
title = "量子コンピュータのオープンソース・ソフトウェア"
date = 2018-12-23T23:34:23+09:00
+++

## まえがき

[量子コンピュータ Advent Calendar 2018](https://qiita.com/advent-calendar/2018/quantum)の23日目の記事です。

OpenQLのなかの人の一人として記事を書いています。この記事を執筆する機会をいただけて感謝しております。

2014年から始まる第二次量子コンピュータブームでは、オープンソース・ソフトウェア(OSS)がたくさん生み出されています。この記事では、量子コンピュータに関するオープンソース・ソフトウェアがあるのかをまとめたいと思います。
このアドベントカレンダーの[1日目の記事](https://qiita.com/gyu-don/items/52e5341e459535045127#%E9%87%8F%E5%AD%90%E3%82%A2%E3%83%8B%E3%83%BC%E3%83%AA%E3%83%B3%E3%82%B0%E6%96%B9%E5%BC%8F%E3%81%A8%E9%87%8F%E5%AD%90%E3%82%B2%E3%83%BC%E3%83%88%E6%96%B9%E5%BC%8F)にある通り、量子コンピュータには汎用的な「ゲート型(と言われるがゲート操作をするとは限らない)」量子コンピュータと、イジングモデルに特化した「量子アニーリング型」と呼ばれているものがあります。この記事では色々と煩わしい「量子コンピュータ」の定義問題には立ち入らず、すべての量子コンピュータに関わるOSSをまとめようと思います。

OSSというのは、[Wikipedia](https://ja.wikipedia.org/wiki/%E3%82%AA%E3%83%BC%E3%83%97%E3%83%B3%E3%82%BD%E3%83%BC%E3%82%B9%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2)的に言うと、「利用者の目的を問わずソースコードを使用、調査、再利用、修正、拡張、再配布が可能なソフトウェアの総称である」です。量子コンピュータにおいても、多くのOSSがあります。これらはGitHub上で公開されていることが多いので、スターの数やコントリビュータの数など多くの情報がわかります。OSSにおいてはライセンスも重要です。現在どんなOSSがあって、それぞれどんな感じなのか、個人的にも気になるのでまとめてみました。著者の不理解により、誤りなどがあるかもしれませんが、その場合は編集リクエストをお送りいただければ幸いです。

この記事の情報は2018年12月23日のものとします。
順番はアルファベット順です。

## D-Wave Systems

世界で最初の商用量子アニーリングマシンを開発した、カナダのD-WaveのOSSを見ていきます。
本アドベントカレンダーにおいても、[9日目](https://qiita.com/abenben/items/1ccc51cd5d9ba18b30c1)にはOceanを使った足し算、Hybridについては　[１１日目](http://blog.mdrft.com/post/814)、[13日目](https://qiita.com/piyo7/items/5e2cf2a92ddbe016572b)にはピクロス(お絵かきロジック)を解いています。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [dwave-ocean-sdk](https://github.com/dwavesystems/dwave-ocean-sdk) | Apache-2.0 | Python |4|67|12|
| [D-Wave Hybrid](https://github.com/dwavesystems/dwave-hybrid) | Apache-2.0 | Python |3|15|10|
| [Qbsolv](https://github.com/dwavesystems/qbsolv) | Apache-2.0 | C++ |20|833|192|

正直に言って、D-Waveを使用したことがないので、各ライブラリの位置付けがいまいちわからないです。どなたか詳細を加筆して編集リクエストをいただけると嬉しいです。

## Google

72量子ビットの量子プロセッサ「Bristlecone」を開発中のGoogleですが、OSSもリリースしています。
ここで紹介するものは　Googleの公式のプロダクトではないので、Googleと書くのも微妙な気がしますが、quantumlibとかいてもピンと来ないので、Googleにしておきます。

[Cirq](https://github.com/quantumlib/Cirq)はアドベントカレンダーの[10日目](https://qiita.com/s_zh/items/bb5c14d21f4dcbcf5426)で紹介されています。[OpenFermion](https://github.com/quantumlib/OpenFermion)は量子化学で出てくるフェルミオンを量子コンピュータで扱うためのライブラリです。
[OpenFermion-Cirq](https://github.com/quantumlib/OpenFermion-Cirq)ではOpenFermionで生成したハミルトニアンをCirq向けにコンパイルすることが出来ます。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [Cirq](https://github.com/quantumlib/Cirq) | Apache-2.0 | Python |35|1272|185|
| [OpenFermion](https://github.com/quantumlib/OpenFermion) | Apache-2.0 | Python |29|682|160|
| [OpenFermion-Cirq](https://github.com/quantumlib/OpenFermion-Cirq) | Apache-2.0 | Python |8|144|27|

## IBM

クラウド上の量子コンピュータを公開しているIBMは多くのOSSをリリースしています。Quantum Information Science KitことQiskitは[4つの要素](https://medium.com/qiskit/qiskit-and-its-fundamental-elements-bcd7ead80492)に分かれます(現在リリースされているのは3つです。)

Qiskit TerraはQiskitの基礎を担うもので、量子回路をコンパイルしたり、量子回路や計算結果を可視化したりする機能があります。Qiskit Aquaは応用向けのライブラリで量子化学・最適化・機械学習をターゲットにしています。Qiskit Aerはつい先日リリースされたばかりのライブラリで、量子計算の高速なシミュレータです。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [Qiskit Terra](https://github.com/Qiskit/qiskit-terra) | Apache-2.0 | Python |75|2276|686|
| [Qiskit Aqua](https://github.com/Qiskit/qiskit-aqua) | Apache-2.0 | Python |20|130|63|
| [Qiskit Aer](https://github.com/Qiskit/qiskit-aer) | Apache-2.0 | Python, C++ |5|13|10|

その他にも、[Qiskit Tutorials](https://github.com/Qiskit/qiskit-tutorials)というチュートリアルがあります。Qiskit Tutorialsについては、このアドベントカレンダーの[5日目の記事](https://nbviewer.jupyter.org/github/ikkoham/qinfo.tech/blob/master/public/notebook/qiskit2018.ipynb)で紹介されています。
また、[JavaScript](https://github.com/Qiskit/qiskit-js)や[Swift](https://github.com/Qiskit/qiskit-swift)向けのライブラリや[VSCode用のExtension](https://github.com/Qiskit/qiskit-vscode)もあるようです。

## MDR

MDRは量子コンピュータの研究・開発をしている企業で、[磁束量子ビット](https://mdrft.com/2018/12/13/qubit/)を作ったりしています。
ゲート型もアニーリング型も両方やっている会社で、OSSも両方に対応しているものがあります。

[Blueqat](https://mdrft.com/blueqat/)は量子回路のシミュレータです。
最近流行りのVQE(Variational Quantum Eigensolver)というアルゴリズムにも対応しているようです。
[Wildqat](https://mdrft.com/wildqat/)は量子アニーリング・量子イジング型向けのライブラリです。
アドベントカレンダーの[19日目](https://qiita.com/s_zh/items/bb5c14d21f4dcbcf5426)ではWildqatを用いて、ビンパッキング問題を解いています。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [Blueqat](https://github.com/mdrft/Blueqat) | Apache-2.0 | Python |4|9|2|
| [Wildqat](https://github.com/mdrft/Wildqat) | Apache-2.0 | Python |7|20|8|

## Microsoft

Q#はとても人気があり、このアドベントカレンダーでも何度か目にする機会がありました。
[3日目](https://tech.tanaka733.net/entry/2018/12/running-qsharp-in-ibmq)では「Q#からIBM Qを操作する」方法について取り上げられていますし、[4日目](https://qiita.com/stwhabout/items/04105d054b739914d478)ではQ#を学ぶことが出来る問題集であるQuantum Katasが解説されています。

しかしながら、Q#はOSSではありません。

その[ライブラリ](https://github.com/Microsoft/QuantumLibraries)と[例](https://github.com/Microsoft/Quantum)はOSSになっています。また、問題集である[Quantum Katas](https://github.com/Microsoft/QuantumKatas)もOSSです。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [Quantum Development Kit Samples](https://github.com/Microsoft/Quantum) | MIT | C# |12|1688|319|
| [Microsoft Quantum Development Kit Libraries](https://github.com/Microsoft/QuantumLibraries) | MIT | C# |17|10|5|
| [Quantum Katas](https://github.com/Microsoft/QuantumKatas) | MIT | C# |22|1257|195|

ファイルの拡張子が、`.cs`なのでGitHub上でみてみるとC#になっています。

## OpenQL

OpenQL Projectは、量子コンピューターでオープンソースのライブラリを開発している人や、それを利用したい人が集まるコミュニティです。 勉強会を開催したり、Slack上で情報交換をしたりしています。

[QuantPy](https://github.com/openql-org/quantpy/)は、フロントエンドに SymPy の数式や量子計算の表現を利用できるようにして、量子計算を行うバックエンドに各種の量子回路シミュレータが利用できるようにした量子回路モデルのシミュレータです。バックエンドには、QuantPy が標準で提供している python実装のシミュレータのほかに、プラグインを追加することで様々なバックエンドを使えるような設計をとっています。IBMの Qiskit（今はquantpyに内包）、cupy 対応された GPU版（quantpycupyパッケージ）、C言語実装版（quantpycythonパッケージ）があります。バックエンドとして、Cirq、Rigetti、Qulacs、Blueqat などの各種シミュレータおよび実サービスの対応も計画されていますが、開発者が少なく、開発自体は盛んではありません。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [QuantPy](https://github.com/openql-org/quantpy) | BSD 3-Clause | Python |1|5|8|

また、OpenQLでは、様々な言語で量子計算のライブラリ開発の取り組みを目標に掲げており、Elixir 実装の quantex、nodeJS 実装の quantjs、Julia 実装の quantjl、C/C++言語実装の libopenql、Haskell 実装の haskell-openql の開発者も募っています。これ以外の言語対応やライブラリの追加も、コミュニティ・メンバーの興味に応じて立ち上げていきます。

## ProjectQ

[ProjectQ](https://projectq.ch)はETH Zurichの研究者によるプロジェクトです。

[ProjectQ](https://github.com/ProjectQ-Framework/ProjectQ)では量子回路を作ったり、シミュレーションをしたりできます。
また、IBM Quantum Experienceで実行することも出来ます。
[FermiLib](https://github.com/ProjectQ-Framework/FermiLib)はOpenFermionのフォーク元で、ProjectQ上で動くフェルミオンのシミュレーション用ライブラリです。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [ProjectQ](https://github.com/ProjectQ-Framework/ProjectQ) | Apache-2.0 | Python |11|398|119|
| [FermiLib](https://github.com/ProjectQ-Framework/FermiLib) | Apache-2.0 | Python |10|47|31|

## QunaSys

QunaSysは日本の量子コンピュータ技術を研究・開発しているベンチャー企業です。
OSSについては、[Qulacs](http://qulacs.org/)という高速に量子回路のシミュレーションをすることが出来るライブラリを公開しています。
GitHub上の他のライブラリとの比較をみると、確かに速いです。
速さは正義ですね。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [Qulacs](https://github.com/qulacs/qulacs) | MIT | C++ |6|15|13|

## QuTiP

Quantum Toolbox in Python、略して[QuTiP](http://qutip.org/)はこれまで紹介したものとは少し異なりますが、数値計算向けのライブラリです。日本学術振興会も支援しています。
アドベントカレンダー2の[18日目](https://qiita.com/masaphys/items/38aeaee5313f81e15414)の記事で[QuTiP](http://qutip.org/)を使用しています。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [QuTiP](https://github.com/qutip/qutip) | 3条項BSDライセンス | Python |44|543|229|

## Rigetti

Rigettiはアメリカのスタートアップ企業で、IBMと同様に量子コンピュータをクラウドで公開しています。

[pyQuil](https://github.com/rigetti/pyquil)はRigettiのクラウド量子コンピュータForestで実行するためのQuilを生成するためのPythonライブラリです。
量子回路をコンパイルし、クラウドでの実機・シミュレータ両方による計算をサポートしています。
[Grove](https://github.com/rigetti/grove)は量子アルゴリズム用のライブラリです。
量子フーリエ変換や位相推定などの基本的な量子アルゴリズムから、Variational　Quantum　Eigensolver (VQE)、Quantum Approximate Optimization Algorithm (QAOA)といったNISQ向けのアルゴリズムもサポートしています。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [pyQuil](https://github.com/rigetti/pyquil) | Apache-2.0 | Python |54|684|184|
| [Grove](https://github.com/rigetti/grove) | Apache-2.0 | Python |25|227|79|

## Xanadu

Xanaduは光を用いた量子
コンピュータを作っているカナダの企業です。光を用いたアーキテクチャ向けのオープンソース・ソフトウェアを公開しています。
連続量を用いた量子計算向けのライブラリは今回紹介する中ではこれだけです。

[Strawberry Fields](https://strawberryfields.readthedocs.io/)は量子回路のデザイン・シミュレーションなどを行ないます。`tensorflow-gpu`を用いてGPUで計算することも出来ます。いずれは実機で計算することも可能になるようです。

| 名前       |   ライセンス   |プログラミング言語 | Contributor |   スター   | フォーク |
|:----------|:----------:|:------:|------:|------:|------:|
| [Strawberry Fields](https://github.com/XanaduAI/strawberryfields) | Apache-2.0 | Python |7|200|31|

## あとがき

ちょっと時間がなくて急いで書いてしまいました。後日加筆する予定です。
取り上げてほしいOSSがあればコメントください。
加筆・訂正したときには[Twitter](https://twitter.com/ikkoham)で告知します。
