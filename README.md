# CakePHP on Docker
このDockerファイルは、CakePHPをDockerで動かすものである。  
CakePHP v3.8を対象としているが、v4でも問題なく動作するはずです。

## 接続先
 - Cake php Top : [http://127.0.0.1/](http://127.0.0.1/)
 - phpMyAdmin : [http://127.0.0.1:8080/](http://127.0.0.1:8080/)
   - username : root
   - password : passw@rd

## Create Project
 1. appディレクトリの.gitkeepを削除 
 2. 以下のコマンドを実行し、質問に答える(基本Yで問題なし)
```bash
docker-compose run --rm app composer create-project --prefer-dist cakephp/app:^3.8 .
```

### Error情報
以下のエラーが発生するが問題なし。  
[詳細ドキュメント](https://tt-computing.com/cake4-remove-post-autoload-dump)
```bash
> Cake\Composer\Installer\PluginInstaller::postAutoloadDump
     Action required!

     The CakePHP plugin installer v1.3+ no longer requires the
     "post-autoload-dump" hook. Please update your app's composer.json
     file and remove usage of                                                   
     Cake\Composer\Installer\PluginInstaller::postAutoloadDump
```

対策として、インストール完了後に[この処理](https://qiita.com/H-Toshi/items/7efa294e1597152cec32)を行うと良い  
`composer.json`の以下(40行目付近)を削除
```json
"post-autoload-dump": "Cake\\Composer\\Installer\\PluginInstaller::postAutoloadDump",
```