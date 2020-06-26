# health_care_app(健康管理アプリ　）

# アプリ概要

毎日の健康管理が出来る会計簿の様なもの。

・今日は何本タバコを吸ったか？
・今日は何本お酒を飲んだか？
・今日の体温は？
・何時に寝て何時に寝たか？
・今日の食事は？

# 制作背景

あまりJavaScriptが得意では無いため、ページ遷移が少ない家計簿を選びました。
また自分が使いたいと思うアプリを作った方が気持ちが籠ると思いました。
加えてチーム開発のフリマアプリ実装において、自分が対応しなかったタスクに関してもしっかりと理解をし、
このアプリで表現していきたいと思っています。

# DEMO(gifで動画や写真を貼って、ビューのイメージを掴んでもらいます)
　⇒できている範囲で貼り付けましょう。
# 実装予定の内容
# DB設計　

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|id               |integer   |null:false,unique:true|  
|password         |string    |null:false|
|email            |string    |null:false, unique:true|
|first_name       |string    |null:false|
|last_name        |string    |null:false|
|first_name_kana  |string    |null:false|
|last_name_kana   |string    |null:false|
|birthday         |string    |null:false|
|age              |integer   |null:false|

### Association
- has_many :posts ,dependent: :destroy

## postsテーブル

|Column|Type|Options|
|------|----|-------|
|id                  |integer      |null:false,unique:true|  
|text                |string       |null:false|
|date                |date         |null:false|

### Association
- has_one :cigarette,        dependent: :destroy
- has_one :alchol,           dependent: :destroy
- has_one :body_temperature, dependent: :destroy
- has_one :meal ,            dependent: :destroy
- has_one :sleep,            dependent: :destroy

### cigarettesテーブル

|Column|Type|Options|
|------|----|-------|
|id      |integer      |null:false,unique:true| 
|name    |string       |null:false|
|number  |integer      |null:false|
|post_id |references   |null:false, foreign_key: true|

### Asociation
- belongs_to :post

### alcholsテーブル

|Column|Type|Options|
|------|----|-------|
|id      |integer      |null:false,unique:true| 
|name    |string       |null:false|
|number  |integer      |null:false|
|post_id |references   |null:false, foreign_key: true|


### Asociation
- belongs_to :post

### body_temperaturesテーブル

|Column|Type|Options|
|------|----|-------|
|id             |integer      |null:false,unique:true| 
|thermometer    |integer      |null:false|
|post_id |references   |null:false, foreign_key: true|


### Asociation
- belongs_to :post

### mealsテーブル

|Column|Type|Options|
|------|----|-------|
|id             |integer   |null:false,unique:true| 
|breakfast      |string    |null:false|
|lunch          |string    |null:false|
|dinner         |string    |null:false|
|post_id |references   |null:false, foreign_key: true|

### Asociation
- belongs_to :post

### sleepsテーブル

|Column|Type|Options|
|------|----|-------|
|id               |integer   |null:false,unique:true| 
|wake_up_time     |date      |null:false|
|bedtime          |date      |null:false|
|time_of_sleeping |integer   |null:false|
|post_id |references   |null:false, foreign_key: true|

### Asociation
- belongs_to :post