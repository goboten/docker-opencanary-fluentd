Opencanaryと連携するためのfluentdを構築するためのDockerfileです。

dockerイメージ構築サンプルはパブリックイメージを参考にしています。https://hub.docker.com/r/fluent/fluentd/   

イメージを作成するために適当な名前でディレクトリを作成します。(ここではfluentとします)  
以下の様にファイルを配置します

 fluent/  
 ├── Dockerfile  
 ├── fluent.conf <- ダミーファイルなので0byteの空ファイルを作成しています。  
 └── plugins/  

fluentフォルダのfluent.confとpluginsフォルダはパブリックイメージから作成するときに必要となるため作成だけします。  
Dockerfileについてもパブリックページに書かれている内容のプラグインに fluent-plugin-elasticsearch と fluent-plugin-record-reformer を追加しているだけです。  
あとは、起動オプションで空のfluent.confを設定済みのfluent.confに差し替えるだけです。  
差し替えるための fluent.conf を保存するディレクトリを用意します。  
差し替え用のfluent.confはdistディレクトリのfluent.confとなります。  
 
 /fluentd/  
 └── etc/    
       └── fluent.conf  

これは、起動時に読み込むfluent.confの送信先を変更するために使用しています。  
そのため、実際に動かすためのfluent.confを配置してください。  

そして、dockerファイルからイメージを作成するのは以下のコマンドで作成しています。  
$ sudo docker build -t fluentd ./  

起動は以下のコマンドとなります。  
$ sudo docker run --name fluentd -d -p 1514:1514 -v /fluentd/etc:/fluentd/etc fluentd

