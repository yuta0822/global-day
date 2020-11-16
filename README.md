# GlobalDay
SNS上の語学学校をイメージとした英語学習に特化したアプリケーション

![toppage](https://user-images.githubusercontent.com/71579504/99182917-86be2100-277b-11eb-8dc9-153ae2103757.PNG)


# 💬　概要

### 日記を書くことは語学の定着に優れているという。
### 英語力の向上を目的としたSNSである。

自身の英語学習のアウトプットを「日記投稿」と言う形で行うことのできるSNS
投稿した日記に対して他者が文法・単語の使い方をコメントし、指摘し合う
指摘されたものはメモを残すことができ復習ができる

# 🌐 App URL
### **https://global-day.herokuapp.com/** 


# 💻 利用方法
① トップページから新規登録・ログイン

② 一覧画面へ遷移する
③ 新規投稿は右上アバター写真をクリック → 「New diary」を選択
　 投稿完了後は一覧画面へ戻る
  ![post-to-show](post-to-show.gif)
  ![7c5df226a30881a330dfdc2143ce0065]()
  ![post-to-index](https://user-images.githubusercontent.com/71579504/99178958-13f17d80-275c-11eb-9430-a386d6e78b6f.gif)

  
④ 一覧画面から１つの投稿を選択 → 投稿詳細画面へ遷移する
　 投稿者本人であれば投稿の編集・削除が投稿詳細画面から可能になる
  ![post-to-show](https://user-images.githubusercontent.com/71579504/99179105-a8a8ab00-275d-11eb-9cec-6c3e2facdb6d.gif)

  
⑤ 投稿詳細画面からコメントができる
　 （コメントは投稿に対しての英語の使い方を指摘するものが望ましいが、交流のために使っても良い）
 '![demo](https://raw.githubusercontent.com/wiki/liz539z/global-day/gif/comment.gif)'


⑥ コメントから得た学びや他者の投稿から得た学びを「My memo」へコピペして管理することができる
 　右上アバター写真をクリック → 「My memo」を選択
  ![to-memo](https://user-images.githubusercontent.com/71579504/99179203-a5fa8580-275e-11eb-9106-357e9031efaa.gif)
 ![how_to_memo](https://user-images.githubusercontent.com/71579504/99182317-a7847780-2777-11eb-828c-b17e8119de1f.gif)
 
⑦ Memoした履歴のタイトルをクリックするとメモ内容が表示される仕組みとなっている。
　 タイトルにはわかりやすい記述がおすすめである
  ![memo-show](https://user-images.githubusercontent.com/71579504/99179456-4ce02100-2761-11eb-83c2-c18731e8ac72.gif)

# ✅ 課題解決
| ユーザーストーリーから考える課題                                                        | 課題解決                                         |
| ------------------------------------------------------------------------------- | ------------------------------------------------- |
| 自身文法があっているのかわからないという日常の課題                                          | コメント機能をつけ各自のアウトプットのため投稿へ助言ができるようにする |
| 単語の使い方が合っているのかわからないという課題                                            | 自分の苦手箇所や単語の使い方を復習できるよう個人のメモ機能をマイページとして使用できるようにする |
| 従来のSNSを利用しても目的の一致した人と関わりづらいという課題                                  | 語学を学ぶことに特化するSNSとすることで同じ目的の人同士が関わることができるようにする |
| 語学勉強のためのアプリケーションは他もあるが、有料のものが多い                                  | 同じ目的を持つ人たちによる勉強型SNSにすることで無料のアプリケーションとすることができる |
| アウトプットの仕方がわからないという課題                                                    | 日記は語学のアウトプットに良いとされているため、SNSの仕組みで気軽に投稿できるものとする |



# 機能

## メモ機能
| 特徴            | 概要             |
| -------------- | -----------------|
| SNSにメモ機能　| 従来のSNSにはない機能。学習に特化したSNSのためメモを活用して自身だけの「辞書」のような役割を果たすことが可能である。　|
| 非同期通信を活用 | 通信量の削減が可能となり、パフォーマンスの向上 |
| アコーディオン形式を使ってのメモ表示 | メモを見やすく管理する為、タイトルをクリックするとメモ内容が見れる仕組みとなっている |

## LIKE機能

| 特徴            | 概要             |
| -------------- | -----------------|
| LIKEした数ではなくユーザーの名前表示 | 数に意識されず利用者がより自分を表現しやすいようにする為　数値での評価は避ける為 |
| 非同期通信を活用 | 通信量の削減が可能となり、パフォーマンスの向上、そしてアイコンが即座に変わる使用にする為 |

## コメント機能
| 特徴            | 概要             |
| -------------- | ---------------- |
| 投稿とコメント欄の位置関係 | 投稿とコメントブラウザ半々の表示にすることで、投稿内容に対してのコメント（助言）がスムーズに行えるようにした |
| 非同期通信活用 | 通信量の削減が可能となり、パフォーマンスの向上 |
| ユーザーアイコンの表示とリンク | コメントしたユーザー情報がわかることで、交流にもつなげていける仕様とする為 |



# 追加予定機能




# DB設計

## Userテーブル
| Column        | Type       | Options     |
| ------------- | ---------- | ----------- |
| name          | string     | null: false |
| email         | string     | null: false |
| password      | string     | null: false |
| country_id    | integer    | null: false |
| profile       | text       |             |
| birthday      | date       | null: false |

### Associate
- has_many :comments
- has_many :posts
- has_many :likes
- has_many :likes_posts, through: :likes, source: :post
- belongs_to :user



## Postテーブル
| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| title         | string     | null: false                    |
| text          | text       | null: false                    |
| place         | string     | null :false                    |
| user_id       | references | null: false, foreign_key: true |

### Associate
- belongs_to :user
- has_many :likes
- has_many :users, through: :likes
- has_many :comments



## Likes
| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| user_id | references | null: false, foreign_key: true |
| post_id | references | null: false, foreign_key: true |

### Associate
- belongs_to :user
- belongs_to :post





## Commentsテーブル
| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| text    | text       | null: false                    |
| user_id | references | null: false, foreign_key: true |
| post_id | references | null: false, foreign_key: true |

### Associate
- belongs_to :user
- belongs_to :post


## Memosテーブル
| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| title   | string     | null: false                    |
| text    | text       | null: false                    |
| user_id | references | null: false, foreign_key: true |

### Associate
- belongs_to :user
