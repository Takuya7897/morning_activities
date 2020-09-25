# テーブル設計

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many :tweets
- has_many :tasks 

## tweets テーブル

| Column | Type       | Options     |
| ------ | ------     | ----------- |
| text   | string     | null: false |
| user   | references | null: false, foreign_key: true |

### Association

- has_one  :tasks
- belongs_to :user

## tasks テーブル

| Column        | Type       | Options                        |
| ------        | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| tweets        | references | null: false, foreign_key: true |
| long_term     | string     | null: false |
| medium_term   | string     | null: false |
| short_term    | string     | null: false |

### Association

- belongs_to :tweets
- belongs_to :user