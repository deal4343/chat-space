# chat-space DB設計
## users テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index: true|
|email|string|null: false, unique: true|
|password|string|null: false, unique: true|
|password confirmation|string|null: false, unique: true|
### Association
- has_many :groups, through: :groups_users
- has_many :messages
- has_many :groups_users

## groups テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :users, through: :groups_users
- has_many :messages
- has_many :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false,foreign_key: true
|group_id|references|null: false,foreign_key: true
### Association
- belongs_to :group
- belongs_to :user

## messages テーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|references|null: false,foreign_key:true|
|user_id|references|null: false,foreign_key:true|
### Association
- belongs_to :user
- belongs_to :group
