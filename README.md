# APIDOC

## 概要
[Stoplight Studio](https://stoplight.io/studio)でAPIを作成して、
その仕様書をvercelに自動デプロイする

## 事前準備
- gitのインストール
- githubのインストール
- vercelのインストール
- npmのインストール

## 使用手順
### 1. [Stoplight Studio](https://github.com/stoplightio/studio/releases)をインストールする(githubからインストール)

|  ダウンロード  |  機種  |
| ---- | ---- |
|  Mac Download  |  インテルmac  |
|  Mac ARM64 Download  |  M1,M2 mac  |
|  Windows Download  |  Windows  |
|  Linux Download  |  Linux  |

### 2. 一通り、登録を終えたら、ローカルプロジェクトを作成する

![local_project](https://user-images.githubusercontent.com/73378197/211131599-ceee5bdc-c05a-46ea-bebf-3ebce48cce3c.png)

### 3. Stoplight StudioのGUIでAPI仕様書を作成する

![stoplight_studio_api](https://user-images.githubusercontent.com/73378197/211131603-dbb8704c-6fbe-4fd0-b4d0-7e522d927035.png)

⇨ finderのどこかにStoplight Studioファイルが作成される

### 4. githubで新しいリポジトリを作成する

作成の仕方は[こちら](https://docs.github.com/ja/get-started/quickstart/create-a-repo)を参照


### 5. vercelの紐付け
紐付け方法は[こちら](https://kikiblog-jp.com/vercel-deploy/)を参照

### 6. 任意のディレクトリにプロジェクトをクローンする

```
$　git clone git@github.com:masato5579/api_docs.git
```

### 7. プッシュ先を変更する(自分のプロジェクトにプッシュするように変更)

```
$ git remote set-url origin ${手順4のプロジェクトのSSHURL}

// 下記コマンドでpush先を確認する
$ git remote -v
```

※ まだpushしない

SSHURL↓
![ssh_url](https://user-images.githubusercontent.com/73378197/211134959-322eac76-3ce1-4cd6-a752-ad0e36ebc28e.png)

### 8. シンボリックリンクを作成する
```
$ ln -s ${手順3のStoplight Studioの相対パス}
```


### 9. scriptを実行する
シンボリックリンクをそのままコミッtできないので、通常のファイルに変換している
```
$ npm run delReference & npm run cpReference
```

### 10. コミットする
```
$ git add .

$ git commit -m "yamlファイル修正"
```

### 11. pushする
```
$ git push origin main
```
※ pushすることでvercelに自動デプロイされる

デプロイパス
```
https://${vercelデプロイ先URL}/current_refernce/${yamlファイル名}.html
```

API仕様書を修正するごとに手順9 ~ 11を実行するとvercelに反映される。