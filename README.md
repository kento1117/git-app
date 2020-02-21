# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :tweets
- has_many  :groups,  through:  :groups_users
- has_many  :groups_users

## tagsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
### Association
- has_many :tweets_tags
- has_many  :tweets,  through:  :tweets_tags


## tweets_tagsテーブル
|Column|Type|Options|
|------|----|-------|
|tweet_id|integer|null: false, foreign_key: true|
|tag_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :tag
- belongs_to :tweet

## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|image|text||
### Association
- has_many :tweets_tags
- has_many  :tags,  through:  :tweets_tags


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :groups_users
- has_many  :posts,  through:  :posts_tags



