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

step by step (for beginer)
----
1. `./build.properties` に、供給元Salesforce 組織のログイン情報と接続情報を入力します
2. `./build.xml` でターゲットを作成します → 設定済
3. `./package.xml` でプロジェクトマニフェストを作成します → 設定済が、必要メタデータのみを取得したい時は変更してください
4. Ant 移行ツールを実行して、Salesforce からメタデータファイルを取得します → `$ ant retrieveUnpackaged`
5. `./build.properties` にコピー先 Salesforce 組織のログイン情報と接続情報を入力します
6. `./retrieveUnpackaged/`フォルダを参考して、必要メタデータファイルを`./deploy/`フォルダにCopyして、`./deploy/package.xml`を変更
7. Ant 移行ツールを実行して、メタデータファイルを Salesforce にリリースします → `$ ant deploy`

参考リンク: https://developer.salesforce.com/docs/atlas.ja-jp.216.0.daas.meta/daas/forcemigrationtool.htm

ant install/setup 
----
(one time only)
* brew install ant
* 設定→開発→ツール→「Force.com ツールおよびツールキット」→「Force.com Migration Tool」→ 「Force.com Migration Tool Download」から「version 38.0版」をダウンロード, `ant-salesforce.jar`は`~/.ant/lib/ant-salesforce.jar`に置く
* “java” command-line tool を使うので、JDKが必要です。 http://www.oracle.com/technetwork/java/javase/downloads
