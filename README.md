# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many  :groups,  through:  :groups_users
- has_many  :tweets,  through:  :tweets_users
- has_many  :groups_users

## tweets_usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|text|string|null: false|
### Association
- belongs_to :group
- belongs_to :user

## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|image|text||
### Association
-  has_many  :tweets,  through:  :tweets_users
- belongs_to  :group


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
||integer|null: false, foreign_key: true|
||integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :groups_users
- has_many  :users,  through:  :groups_users
- has_many :tweets



