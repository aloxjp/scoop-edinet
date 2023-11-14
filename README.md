# scoop-edinet
Eclipse環境(jdk8, gradle4, spring boot 2.0) 保全のためのscoop bucket

## scoopをインストール

PowerShellでインストールします。

1. 管理者権限でPowerShellを起動

	セキュリティ上の理由から、デフォルトでスクリプトの実行が無効に設定されています。

		Set-ExecutionPolicy RemoteSigned

	管理者権限のPowerShellを閉じます。
	以降、ユーザー権限でPowerShellを起動して続行してください。

1. 実行ポリシーを緩和

		set-executionpolicy remotesigned -scope currentuser

1. TLS認証を緩和

		[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls11
		[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
		[System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}

1. インストール

		iex (new-object net.webclient).downloadstring('https://get.scoop.sh')

## gitをインストール

scoopもbucketをgitでバージョン管理しています。
これもscoopでインストールできます。

	scoop install git

## このbucketをscoop参照先に追加

この設定をすることで、 `scoop install <app>` でこのリポジトリにあるアプリケーションをインストールすることができるようになります。

	scoop bucket add alox-edinet https://github.com/aloxjp/scoop-edinet

## このbucketを更新

このbucketのバージョン番号が更新されている場合、下記のコマンドで更新します。

	scoop update

さらに、`scoop update <app>` を実行することでインストールされているアプリケーションを更新することができます。

`<app>`に指定するアプリケーションは下記のとおりです。

`<app>`        | アプリケーション
-----------|---------------
alm        | ALM.exe
edinet     | EDINET.exe
gradle4    | gradle ver.4
ojdkbuild8 | openjdk8
pleiades   | 保全環境(Spring Boot 2.0)
uwsc       | UWSC

## このbucketをscoop参照先から削除

	scoop bucket rm alox-edinet

