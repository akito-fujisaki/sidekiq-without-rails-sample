# sidekiq-without-rails-sample

「SidekiqをRailsなしで使う」ことを目的としたリポジトリです。

詳細は下記ブログを参照してください。

https://tech.itandi.co.jp/entry/2023/01/27/180000

### 1. Gemのインストール

```
$ bundle install
```

### 2. Redisサーバを建てる

```
$ docker compose up
```

### 3. Sidekiqサーバを建てる

```
$ bundle exec sidekiq -r ./application.rb
```

### 4. ジョブを実行する

```
$ bundle exec irb -r ./application.rb

irb(main)> SampleJob.perform_async({ 'name' => 'hoge'})

=> "664a8c2dcd13c616a126ffe4"
```

実行すると、3で建てたSidekiqサーバのログに出力されます。

### 5. Sidekiqダッシュボードを建てる

```
$ bundle exec rackup
```

`http://localhost:9292`にアクセスすることで、ダッシュボードを確認できます。
