# README

## group_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## userテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unique: true|
|mail|string|null: false|

### Association

- has_many :groups, through: members
- has_many :messages
- has_many :members

## groupテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true, index|

### Association

- has_many :messages
- has_many :group_users
- has_many :users through::group_users

## messageテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|
|group_id|references|null: false, foreign_key: true|
|user_id|references|null: false, foreign_key: true|


### Association

- belongs_to :user
- belongs_to :group