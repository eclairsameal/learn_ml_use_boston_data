# Learn ML using boston data

## 前準備
1. ボストン住宅データセットを読み込み、欠損地の有無、要約統計量を確認してください。
2. データセットの目的変数である「MEDV」について、データの分布を可視化し、確認してください。
3. 目的変数MEDVと相関が強い変数を確認するために、ヒートマップを作成し相関が高い2つの変数を選択してください。
4. 上記で選択した2つの変数と、MEDVについてペアプロットを描画してください。

Code : 

[Pretreatment.ipynb](https://github.com/eclairsameal/learn_ml_use_boston_data/blob/main/Pretreatment.ipynb)

## 重回帰
1. 全ての特徴量（13個）と目的変数MEDVで、重回帰モデルを作成してください。
2. なお、データセットはホールドアウト法で分割し、trainデータ、testデータとすること。なお、train:testは8:2としてください。
3. ランダムシードは0で固定してください。(以降、全て同様)
4. 精度評価はRMSEとしてください。

Code : 

### 標準化（standardization）:
  
[linear_regressio_stand.ipynb](https://github.com/eclairsameal/learn_ml_use_boston_data/blob/main/linear_regressio_stand.ipynb)

看了其他人的文章表示標準化後，結果差異不大，所以編寫一個沒有標準化的程式做實驗

他の人の記事を読んだところ、標準化しても結果にほとんど差がなかったので、標準化せずにプログラムを書いて実験する

### 沒有標準化（no standardization）:

[linear_regression.ipynb](https://github.com/eclairsameal/learn_ml_use_boston_data/blob/main/linear_regression.ipynb)

### 篩選特徵（Filter features）：

利用前處理中高度相關的特徵來執行（`['LSTAT','RN']`）

前処理で関連性の高い特徴を使用して実行する

[linear_regression_filter_features.ipynb](https://github.com/eclairsameal/learn_ml_use_boston_data/blob/main/linear_regression_filter_features.ipynb)

標準化的結果確實沒有太大的差異(確かに標準化された結果には大きな違いはありません)

篩選特徵雖然正確度下降，但沒有下降太多，為了提升速度可以考慮

フィルタリング機能の精度は低下しましたが、それほど精度が低下していないため、速度を向上させるためにフィルタリング機能を検討できます。

## 回帰木（決定木）

https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeRegressor.html#sklearn.tree.DecisionTreeRegressor

1. 全ての特徴量（13個）と目的変数MEDVで、回帰木モデルを作成してください。
2. データセットは、重回帰同様、ホールドアウト方で分割し、train, testデータとしてください。
3. 以下のハイパーパラメータを(明示的に)設定し、モデルを作成すること。なお、以下のハイパーパラメータは何か確認してください。
    - criterion: 'squared_error'
    - max_depth: 4
    - min_samples_leaf: 10
    - ccp_alpha: 5
4. 精度評価をRMSEで計算してください。
5. 今回作成したモデルの回帰木を可視化してください。
6. 特徴量重要度を可視化してください。

Code : 

### 標準化（standardization）:

[decision_tree_stand.ipynb](https://github.com/eclairsameal/learn_ml_use_boston_data/blob/main/decision_tree_stand.ipynb)

### 沒有標準化（no standardization）:

[decision_tree.ipynb](https://github.com/eclairsameal/learn_ml_use_boston_data/blob/main/decision_tree.ipynb)

## 勾配ブースティング（LightGBM）
https://lightgbm.readthedocs.io/en/stable/

（0. 勾配ブースティングについて簡単に調べてください。）
1. 全ての特徴量（13個）と目的変数MEDVとし、LigthGBMの回帰モデルを作成してください。
2. データセットは、重回帰同様、ホールドアウト方で分割し、train, testデータとしてください。
3. 以下のハイパーパラメータを(明示的に)設定し、モデルを作成すること。なお、以下のハイパーパラメータは何か確認してください。
    - objective: 'mse'
    - num_leaves: 5
4. ブーステイングの回数は50としてください。
5. 精度評価はRMSEとしてください。
6. 特徴量重要度を可視化してください。
↓以下は余裕があれば↓
(7. 1本目の木と50本目の木を可視化してください。)
(8. SHAP(SHapley Additive exPlanations)とは何か調べて確認してください。)

Code : 

### 標準化（standardization）:

[LigthGBM_stand.ipynb](https://github.com/eclairsameal/learn_ml_use_boston_data/blob/main/LigthGBM_stand.ipynb)

### 沒有標準化（no standardization）:

[LigthGBM.ipynb](https://github.com/eclairsameal/learn_ml_use_boston_data/blob/main/LigthGBM.ipynb)
