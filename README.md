# splatnet2statink-heroku

## 概要

[heroku](https://jp.heroku.com/home)上で[splatnet2statink](https://github.com/frozenpandaman/splatnet2statink)を定期実行してSplatoon 2の戦績を[stat.ink](https://stat.ink/)へ自動送信します

## 特徴

* ✅ 無料
* ✅ 完全自動

## herokuについて

* [herokuとは？](https://jp.heroku.com/what)を参照
* Freeプランでは小さなアプリケーションを[Free Dyno Hours](https://devcenter.heroku.com/articles/free-dyno-hours)の間使用可能
  * splatnet2statink-herokuを動かしているだけであればFree Dyno Hoursを超えないはず

## splatnet2statinkやstat.inkについて

* [splatnet2statink](https://github.com/frozenpandaman/splatnet2statink)を参照

## 使用方法

### splatnet2statinkに必要な情報を取得する

* [Setup instructions](https://github.com/frozenpandaman/splatnet2statink#setup-instructions)を参考に、一度ローカルでsplatnet2statinkを動かす
* `config.txt` が出力されるので、その中の `api_key` , `cookie` , `session_token` の内容を控えておく

### herokuを使用する

* このリポジトリをForkする
* herokuアカウントを作成する
* [Create new app](https://dashboard.heroku.com/new-app)から名前を付けてherokuアプリを作成する
* `Connect to GitHub` から先程Forkしたリポジトリを指定する
* `Settings` タブから
  * `Config Vars` に先程控えておいた3つの内容をそれぞれ `API_KEY` , `COOKIE` , `SESSION_TOKEN` として登録する
  * `Buildpacks` に `https://github.com/grauwoelfchen/heroku-buildpack-gettext.git` を追加する
* `Resources` タブから
  * `Find more add-ons` より `Heroku Scheduler` を探して追加する
* `Heroku Scheduler` の設定から
  * `Schedule` に `Every 10 minutes` を指定
  * `Run Command` に `./main` を指定

