# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

以下DB設計を書く

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|email|string|null: false, unique: true|
|last_name|string|null: false|
|first_name|string|null: false|
|last_name_kana|string|null: false|
|first_name_kana|string|null: false|
### Association
- has_one :profile
- has_many :creditcards
- has_many :items
- has_many :comments
- has_many :likes
- has_many :solditems

## profilesテーブル
|Column|Type|Options|
|------|----|-------|
|birthday|integer|-------|
|profile|text|-------|
|postcode|string|-------|
|prefecture|string|-------|
|municipality|string|-------|
|address|string|-------|
|room_number|string|-------|
|phone|integer|-------|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user

## creditcardsテーブル
|Column|Type|Options|
|------|----|-------|
|cardnumber|integer|null: false, unique: true|
|expirationdata|integer|null: false|
|securitycode|integer|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user

## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|explanation|text|null: false|
|category1|integer|null: false, foreign_key: true|
|category2|integer|null: false, foreign_key: true|
|category3|integer|null: false, foreign_key: true|
|brand|string|-------|
|condition|string|null: false|
|postage|integer|null: false|
|area|string|null: false|
|days|integer|null: false|
|price|integer|null: false|
|user_id|integer|null: false, foreign_key: true|
|status|integer|null: false|
### Association
- belongs_to :user
- belongs_to :category1
- belongs_to :category2
- belongs_to :category3
- has_one :solditems
- has_many :item-images
- has_many :comments
- has_many : likes

## item-imagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|string|null: false|
|item_id|string|null: false, foreign_key: true|
### Association
- belongs_to :item

## solditemsテーブル
|Column|Type|Options|
|------|----|-------|
|item_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :item
- belongs_to :user

## categories1テーブル
|Column|Type|Options|
|------|----|-------|
|category1|string|null: false,|
### Association
- has_many :items

## categories2テーブル
|Column|Type|Options|
|------|----|-------|
|category2|string|null: false|
### Association
- has_many :items

## categories3テーブル
|Column|Type|Options|
|------|----|-------|
|category3|string|null: false|
### Association
- has_many :items

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|items_id|integer|null: false, foreign_key: true|
|users_id|integer|null: false, foreign_key: true|
|comment_id|text|null: false|
### Association
- belongs_to :group
- belongs_to :user

## likesテーブル
|Column|Type|Options|
|------|----|-------|
|items_id|integer|null: false, foreign_key: true|
|users_id|integer|null: false, foreign_key: true|
|like|boolean|null: false|
### Association
- belongs_to :group
- belongs_to :user