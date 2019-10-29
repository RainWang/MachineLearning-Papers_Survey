# ■ 論文
- 論文タイトル："Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks"
- 論文リンク：https://arxiv.org/abs/1703.03400
- 論文投稿日付：
- 被引用数（記事作成時点）：xxx 件
- 著者（組織）：
- categories：

# ■ 概要（何をしたか？）

## Abstract


# ■ イントロダクション（何をしたいか？）

## x. Introduction

- xxx

---

- The key idea underlying our method is to train the model’s initial parameters such that the model has maximal performance on a new task after the parameters have been up- dated through one or more gradient steps computed with a small amount of data from that new task.
    - この方法の基本的な考え方は、新しいタスクからの少量のデータを使用して計算された1つ以上の勾配ステップによってパラメーターが更新された後、モデルが新しいタスクで最大のパフォーマンスを発揮するようにモデルの初期パラメーターをトレーニングすることです。

- Unlike prior meta-learning methods that learn an update function or learning rule (Schmidhuber, 1987; Bengio et al., 1992; Andrychowicz et al., 2016; Ravi & Larochelle, 2017), our algorithm does not expand the number of learned parameters nor place constraints on the model architecture (e.g. by requiring a recurrent model (Santoro et al., 2016) or a Siamese network (Koch, 2015)), and it can be readily combined with fully connected, convolutional, or recurrent neural networks. It can also be used with a variety of loss functions, including differentiable supervised losses and non- differentiable reinforcement learning objectives.
    - 更新関数または学習ルールを学習する従来のメタ学習方法（Schmidhuber、1987; Bengio et al。、1992; Andrychowicz et al。、2016; Ravi＆Larochelle、2017）とは異なり、アルゴリズムは学習したパラメーターの数を拡張しません また、モデルアーキテクチャに制約を課す（たとえば、リカレントモデル（Santoro et al。、2016）またはSiameseネットワーク（Koch、2015）を必要とする）。また、完全に接続された、畳み込み、またはリカレントニューラルネットワークと容易に組み合わせることができます。 また、微分可能な教師あり損失や微分不可能な強化学習目標など、さまざまな損失関数とともに使用できます。

---

- The process of training a model’s parameters such that a few gradient steps, or even a single gradient step, can produce good results on a new task can be viewed from a feature learning standpoint as building an internal representation that is broadly suitable for many tasks.
    - いくつかの勾配ステップまたは単一の勾配ステップでも新しいタスクで良い結果が得られるようにモデルのパラメーターをトレーニングするプロセスは、多くのタスクに広く適した内部表現の構築として機能学習の観点から見ることができます。

- If the internal representation is suitable to many tasks, simply fine-tuning the parameters slightly (e.g. by primarily modifying the top layer weights in a feedforward model) can produce good results. In effect, our procedure optimizes for models that are easy and fast to fine-tune, allowing the adaptation to happen in the right space for fast learning.
    - 内部表現が多くのタスクに適している場合、パラメーターをわずかに微調整するだけで（たとえば、フィードフォワードモデルで主にトップレイヤーの重みを変更することで）良い結果が得られます。 実際、この手順は、簡単かつ迅速に微調整できるモデル向けに最適化されており、迅速な学習のために適切なスペースで適応を行うことができます。

- From a dynamical systems standpoint, our learning process can be viewed as maximizing the sensitivity of the loss functions of new tasks with respect to the parameters: when the sensitivity is high, small local changes to the parameters can lead to large improvements in the task loss.
    - 動的システムの観点から、学習プロセスは、パラメータに関する新しいタスクの損失関数の感度を最大化するものと見なすことができます。感度が高い場合、パラメータの小さな局所的変更はタスク損失の大幅な改善につながる可能性があります 。

---



# ■ 結論

## x. Conclusion


# ■ 何をしたか？詳細

## 2. Model-Agnostic Meta-Learning

- xxx

### 2.1. Meta-Learning Problem Set-Up

- xxx

---

- In the K-shot learning setting, the model is trained to learn a new task Ti drawn from p(T ) from only K samples drawn from qi and feedback LTi generated by Ti.
    - Kショット学習設定では、モデルは、qiから描画されたKサンプルとTiによって生成されたフィードバックLTiからのみp（T）から描画された新しいタスクTiを学習するようにトレーニングされます。

- During meta-training, a task Ti is sampled from p(T ), the model is trained with K samples and feedback from the corresponding loss LTi from Ti, and then tested on new samples from Ti.
    - メタトレーニング中に、タスクTiはp（T）からサンプリングされ、モデルはKサンプルとTiからの対応する損失LTiからのフィードバックでトレーニングされ、Tiの新しいサンプルでテストされます。

- The model f is then improved by considering how the test error on new data from qi changes with respect to the parameters. In effect, the test error on sampled tasks Ti serves as the training error of the meta-learning process. At the end of meta-training, new tasks are sampled from p(T ), and meta-performance is measured by the model’s performance after learning from K samples. Generally, tasks used for meta-testing are held out during meta-training.
    - その後、モデルfは、qiからの新しいデータのテストエラーがパラメーターに関してどのように変化するかを考慮することによって改善されます。 実際、サンプリングされたタスクTiのテストエラーは、メタ学習プロセスのトレーニングエラーとして機能します。 メタトレーニングの最後に、p（T）から新しいタスクがサンプリングされ、Kサンプルから学習した後のモデルのパフォーマンスによってメタパフォーマンスが測定されます。 一般的に、メタテストに使用されるタスクは、メタトレーニング中に保留されます。

### 2.2. A Model-Agnostic Meta-Learning Algorithm

- In contrast to prior work, which has sought to train recurrent neural networks that ingest entire datasets (Santoro et al., 2016; Duan et al., 2016b) or feature embeddings that can be combined with nonparametric methods at test time (Vinyals et al., 2016; Koch, 2015), we propose a method that can learn the parameters of any standard model via meta-learning in such a way as to prepare that model for fast adaptation. The intuition behind this approach is that some internal representations are more transferrable than others.
    - テスト時にノンパラメトリックメソッドと組み合わせることができるデータセット全体または特徴の埋め込みを取り込むリカレントニューラルネットワークをトレーニングしようとした従来の作業とは対照的に、メタ学習によって標準モデルのパラメーターを学習できる方法を提案します そのモデルを迅速な適応のために準備する方法。 このアプローチの背後にある直観は、一部の内部表現は他の表現よりも譲渡可能であるということです。

- For example, a neural network might learn internal features that are broadly applicable to all tasks in p(T ), rather than a single individual task. How can we encourage the emergence of such general-purpose representations? We take an explicit approach to this problem: since the model will be fine-tuned using a gradient-based learning rule on a new task, we will aim to learn a model in such a way that this gradient-based learning rule can make rapid progress on new tasks drawn from p(T ), without overfitting.
    - たとえば、ニューラルネットワークは、単一の個々のタスクではなく、p（T）のすべてのタスクに広く適用可能な内部機能を学習する場合があります。 このような汎用表現の出現をどのように奨励できますか？ この問題への明示的なアプローチを取ります。モデルは新しいタスクで勾配ベースの学習ルールを使用して微調整されるため、この勾配ベースの学習ルールが迅速になるようにモデルを学習することを目指します。 オーバーフィッティングなしでp（T）から描画された新しいタスクの進捗。

- In effect, we will aim to find model parameters that are sensitive to changes in the task, such that small changes in the parameters will produce large improvements on the loss function of any task drawn from p(T), when altered in the direction of the gradient of that loss (see Figure 1). We make no assumption on the form of the model, other than to assume that it is parametrized by some parameter vector θ, and that the loss function is smooth enough in θ that we can use gradient-based learning techniques.
    - 実際、タスクの変化に敏感なモデルパラメーターを見つけることを目指します。パラメーターの小さな変化は、p（T）から引き出されたタスクの損失関数に大きな改善をもたらします。 その損失の勾配（図1を参照）。 モデルの形式については、何らかのパラメーターベクトルθによってパラメーター化されていること、および損失関数がθで十分に滑らかであり、勾配ベースの学習手法を使用できることを前提としています。

---

- xxx

---

- Note that the meta-optimization is performed over the model parameters θ, whereas the objective is computed using the updated model parameters θ′. In effect, our proposed method aims to optimize the model parameters such that one or a small number of gradient steps on a new task will produce maximally effective behavior on that task.
    - メタ最適化はモデルパラメーターθに対して実行されるのに対し、目的は更新されたモデルパラメーターθ 'を使用して計算されることに注意してください。 実際、提案された方法は、新しいタスクの1つまたは少数の勾配ステップがそのタスクで最大限効果的な動作を生成するように、モデルパラメーターを最適化することを目的としています。

---

- xxx

---

- The MAML meta-gradient update involves a gradient through a gradient. Computationally, this requires an additional backward pass through f to compute Hessian-vector products, which is supported by standard deep learning libraries such as TensorFlow (Abadi et al., 2016). In our experiments, we also include a comparison to dropping this backward pass and using a first-order approximation, which we discuss in Section 5.2.
    - MAMLメタグラデーション更新には、グラデーションを介したグラデーションが含まれます。 計算上、これにはヘッセ行列ベクトル積を計算するためにfを介した追加の後方パスが必要です。これは、TensorFlowなどの標準の深層学習ライブラリでサポートされています（Abadi et al。、2016）。 私たちの実験では、この逆方向パスを削除し、1次近似を使用することとの比較も含めています。




# ■ 実験結果（主張の証明）・議論（手法の良し悪し）・メソッド（実験方法）

## 5. Experimental Evaluation

### 5.1. Regression

- xxx

- The qualitative results, shown in Figure 2 and further expanded on in Appendix B show that the learned model is able to quickly adapt with only 5 datapoints, shown as purple triangles, whereas the model that is pretrained using standard supervised learning on all tasks is unable to adequately adapt with so few datapoints without catastrophic overfitting. 
    - 図2に示され、さらに付録Bに拡張された定性的結果は、学習されたモデルが紫色の三角形で示された5つのデータポイントのみで迅速に適応できるのに対し、すべてのタスクで標準的な教師あり学習を使用して事前学習されたモデルは不可能であることを示しています 壊滅的なオーバーフィッティングなしで非常に少ないデータポイントで適切に適応する。

- Crucially, when the K datapoints are all in one half of the input range, the model trained with MAML can still infer the amplitude and phase in the other half of the range, demonstrating that the MAML trained model f has learned to model the periodic nature of the sine wave.
    - 重要なのは、Kデータポイントがすべて入力範囲の半分にある場合、MAMLでトレーニングされたモデルは範囲の残りの半分で振幅と位相を推測できるため、MAMLトレーニングモデルfが周期的性質のモデル化を学習したことを示しています 正弦波の。

- Furthermore, we observe both in the qualitative and quantitative results (Figure 3 and Appendix B) that the model learned with MAML continues to improve with additional gradient steps, despite being trained for maximal performance after one gradient step.
    - さらに、定性的および定量的な結果（図3および付録B）の両方で、MAMLで学習されたモデルは、1つの勾配ステップ後の最大のパフォーマンスのためにトレーニングされているにもかかわらず、追加の勾配ステップで改善し続けていることがわかります

- This improvement suggests that MAML optimizes the parameters such that they lie in a region that is amenable to fast adaptation and is sensitive to loss functions from p(T ), as discussed in Section 2.2, rather than overfitting to parameters θ that only improve after one step.
    - この改善は、セクション2.2で説明したように、MAMLがパラメーターを最適化して、高速適応に適し、pからの損失関数に敏感な領域にあるようにパラメーターを最適化することを示しています。


# ■ 関連研究（他の手法との違い）

## x. Related Work

