# Keras版SSDモデルの利用

有名なSSDのKeras実装をTensorflow2対応してみる

## 仮想環境の準備

```
pyenv virtualenv 3.8.9 keras
pyenv local keras
pip install --upgrade pip setuptools

# pythonモジュールのインストール
pip install opencv-python
pip install tensorflow
pip install matplotlib
pip install imageio
```

## リポジトリのクローン
```
git clone https://github.com/rykov8/ssd_keras.git
# まだcdしない
```

## モデルファイルのダウンロード
ブラウザで以下にアクセスし、weights_SSD300.hdf5をダウンロード  
(ファイルを選択して、下の方にあるダウンロードボタン(↓)をクリック)  
    - <https://mega.nz/#F!7RowVLCL!q3cEVRK9jyOSB9el3SssIA>  
ダウンロード後、``weights``ディレクトリにコピーしておく。  

## テスト用画像をダウンロード
これでなくてもいいけど、とりあえずいつもの奴。  
ファイル名はテストプログラム中で固定してあるので、ファイル変更した場合はよしなに...  
```
wget https://raw.githubusercontent.com/PINTO0309/MobileNet-SSD-RealSense/master/data/input/testvideo3.mp4 -O images/testvideo3.mp4
```

## リポジトリにパッチを当てる
```
cd ssd_keras/
patch -p1 < ../ssd_keras.patch 
patch -p1 < ../ssd_keras_2.patch 
```

## テストプログラムを実行する

```
cd testing_utils/
python videotest_example.py 
```
ESCキー入力で実行中断できるように改造してあるので、途中でやめたくなったらESCを押してください。  

