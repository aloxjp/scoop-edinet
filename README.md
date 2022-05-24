# scoop-edinet
Eclipse環境(jdk8, gradle4, spring boot 2.0) 保全のためのscoop bucket

## scoopをインストール

PowerShellでインストールします。

1. 管理者権限でPowerShellを起動

	セキュリティ上の理由から、デフォルトでスクリプトの実行が無効に設定されています。

		PS > Set-ExecutionPolicy RemoteSigned

	管理者権限のPowerShellを閉じます。
	以降、ユーザー権限でPowerShellを起動して続行してください。

1. 実行ポリシーを緩和

		PS > set-executionpolicy remotesigned -scope currentuser

1. TLS認証を緩和

		PS > [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls11
		PS > [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
		PS > [System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}

1. インストール

		PS > iex (new-object net.webclient).downloadstring('https://get.scoop.sh')

## gitをインストール

scoopもbucketをgitでバージョン管理しています。
これもscoopでインストールできます。

	PS > scoop install git
