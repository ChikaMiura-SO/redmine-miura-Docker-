# redmine-miura-Docker-
## Redmine に Agile プラグイン( Light 版)を追加する方法  
### コンテナを起動  
<<<<<<< HEAD
コンテナ「redmine-miura-Docker-」を起動します。
=======
コンテナ「redmine-miura-Docker-を起動します。
>>>>>>> master

### コンテナにプラグインファイルのコピー
1.コンテナ内のdocker-compose.ymlの親ディレクトリに、ローカル環境で配置したredmine_agile-1_5_4-light.zipをコピーします。  
`
$ sudo docker cp redmine_agile-1_5_4-l <コンテナID>:/etc/redmine_agile-1_5_4-l
`   
2.コンテナの中に入ります。  
`
$ sudo docker exec -i -t コンテナ名またはコンテナID /bin/bash
`   

### ファイルの解凍と実行
redmine コンテナ上で下記コマンドを実行します。  
`
apt update
`
`  
apt install -y unzip
`
`  
cp /etc/redmine_agile-1_5_4-light.zip plugins/ &&
`
`  
cd plugins &&
`  
`
unzip redmine_agile-1_5_4-light.zip &&
`
`  
cd .. &&
`
`  
bundle install --without development test --no-deployment &&
`
`  
bundle exec rake redmine:plugins NAME=redmine_agile RAILS_ENV=production  
`  

### 確認
Redmineにログインし、「管理」→ 「プラグイン」からAgileが反映されていることを確認します。

### 参考URL
下記URLを参考にしました。  
<https://qiita.com/ping-pong/items/78ae62e17219a3c1e26e>

