ant migrate tool
=====

directory
----
* `./source/`: deploy資源のdirectory
* `./source/package.xml`: deploy資源の定義ファイル
* `./package.xml`: retrieve資源の定義ファイル（すべて資源をretrieveできるように定義されています）
* `./build.properties`: ログイン情報を設定するファイル（gitで管理しないように注意してください）
```
sf.username = yourname@example.com
sf.password = password_and_security_token
sf.serverurl = https://test.salesforce.com
```

how to
----
* `./package.xml`に設定しているメタデータをSF環境から`./retrieveUnpackaged`に取り込む
```
$ ant retrieveUnpackaged
```
* `./source/`のメタデータをデプロイ
```
$ ant deploy
```

ant install/setup 
----
(one time only)
* brew install ant
* 設定→開発→ツール→「Force.com ツールおよびツールキット」→「Force.com Migration Tool」→ 「Force.com Migration Tool Download」から「version 38.0版」をダウンロード, `ant-salesforce.jar`は`~/.ant/lib/ant-salesforce.jar`に置く
* “java” command-line tool を使うので、JDKが必要です。 http://www.oracle.com/technetwork/java/javase/downloads