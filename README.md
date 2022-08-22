# README

# テーブル設計

## users テーブル

| Column             | Type   | Options                    |
| ------------------ | ------ | -------------------------- |
| name               | string | null: false                |
| email              | string | null: false, unique: true  |
| encrypted_password | string | null: false                |
| profile            | string | null: false                |
| occupation         | string | null: false                |
| position           | string | null: false                |

### Association

- has_many :prototypes
- has_many :prototypes, through: :comments

## prototypes テーブル

| Column     | Type       | Options                         |
| ---------- | ---------- | ------------------------------- |
| title      | string     | null: false                     |
| catch_copy | text       | null: false                     |
| concept    | text       | null: false                     |
| user       | references | null: false, foreign_key: true  |

### Association

- belongs_to :users
- has_many  :users, through: :comments

## comments テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| user        | references | null: false, foreign_key: true |
| prototype   | references | null: false, foreign_key: true |
| content     | text       | null: false                    | 

### Association

- belongs_to :prototypes
- belongs_to :user

