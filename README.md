# Rails6 + MySQL + Webpacker + Vue on docker の開発環境構築

1. リポジトリをクローンして、新規 rails プロジェクトを作成

```sh
mkdir your_app_name
cd your_app_name
git clone this repository
docker-compose run web rails new . --force --database=mysql --webpack=vue --skip-coffee --skip-test
docker-compose build
```

2. 該当部分の database.yml を変更

```database.yml
default: &default
  adapter: mysql2
  encoding: utf8
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: password
  host: db
```

3. DB を作成して、コンテナを起動後、接続確認

```sh
docker-compose up
docker-compose stop
docker-compose run web rake db:create
docker-compose up
```
