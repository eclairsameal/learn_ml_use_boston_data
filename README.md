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

## BostonHousing.csv

:Attribute Information (in order):
- CRIM     
	per capita crime rate by town

  各城鎮人均犯罪率
- ZN       
	proportion of residential land zoned for lots over 25,000 sq.ft.

  面積超過 25,000 平方英尺的住宅用地比例
- INDUS    
	proportion of non-retail business acres per town

  每個城鎮非零售商業面積的比例
- CHAS     
	Charles River dummy variable (= 1 if tract bounds river; 0 otherwise)

  查爾斯河虛擬變數（如果區域邊界為河流，則 = 1；否則為 0）
- NOX
  nitric oxides concentration (parts per 10 million)
  
	一氧化氮濃度（千萬分之一）
- RM
  average number of rooms per dwelling
  
	每套住宅的平均房間數
- AGE
  proportion of owner-occupied units built prior to 1940
  
	1940 年之前建造的自住單位的比例
- DIS
  weighted distances to five Boston employment centres
  
	到五個波士頓就業中心的加權距離
- RAD
  index of accessibility to radial highways
  
	放射狀公路可達性指數
- TAX
  full-value property-tax rate per $10,000
  
	每 10,000 美元的全額財產稅稅率
- PTRATIO
  pupil-teacher ratio by town

按城鎮劃分的師生比
- B
  1000(Bk - 0.63)^2 where Bk is the proportion of blacks by town
  
	1000(Bk - 0.63)^2 其中 Bk 是按城鎮劃分的黑人比例
- LSTAT
  % lower status of the population
  
	人口地位較低的百分比
- MEDV
  Median value of owner-occupied homes in $1000's
  
	自住房屋的中位數價值為 1000 美元
