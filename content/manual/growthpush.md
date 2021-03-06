---
categories: 'manual'
date: 2016-03-11T12:05:16+09:00
description: 'GrowthPush'
draft: false
title: GrowthPush
---

# はじめに

## 新規登録 / ログイン
Growth Pushの管理画面にログインするためには、会員登録（無料）をする必要があります。
Growth Pushのアカウントはシロクが提供するグロースハックツールのプラットフォームであるGrowthbeat(https://growthbeat.com/ )で管理されます。

https://growthbeat.com/ より、会員登録を行うことができます。右上の【会員登録（無料）】をクリックしていただきますと、以下の画像に示されている画面に遷移してアカウント作成が行えます。メールアドレス・パスワード・お客様の属性を選択された後に、利用規約をご覧下さい。利用規約とお知らせメールの受信に同意していただける場合にはチェックしていただきまして、【無料登録】をクリックしていただけますと新規登録は完了です。

<img src="/img/push/push_login.png" alt="" title="" width="100%"/>

アカウントを既にお持ちの場合には、【会員登録（無料）】の隣にあります。【ログイン】をクリックして頂けますと、以下のような画面に遷移しログインすることができます。
万が一パスワードを忘れてしまった場合は、【ログイン】の下にございます、【パスワード再発行】より、パスワードの再発行を行って下さい。

ログイン画面

<img src="/img/push/push_create_account.png" alt="" title="" width="100%"/>

ログインをすると、Growthbeatのトップ画面にたどり着きます。そこでGrowthPushを選択して下さい。

<img src="/img/push/push_select_servce.png" alt="" title="" width="100%"/>

## アプリの追加
上記の操作を完了すると、管理画面が表示されます。この時アプリはDefault Appが選択された状態になっています。

Growth Pushを適用したいアプリを追加するには、メインメニューの【アプリ】のプルダウンメニューから、
【アプリ追加】を選択し、アプリケーション作成画面へ遷移します。適用したいアアプリの名前を入力し、作成
ボタンをクリックして完了となります。

<img src="/img/push/push_add_application.png" alt="" title="" width="100%"/>

アプリの詳細情報に関しましてはGrowthbeat管理画面にて設定してください。設定方法は[Growthbeat管理画面操作方法](http://support.growthbeat.com/manual/growthbeat/#アプリ情報の確認)をご参照ください。

<img src="/img/push/push_create_application.png" alt="" title="" width="100%"/>

プッシュ通知を送信するためには、メインメニューから対象のアプリを選択する必要があります。

# 配信作成

## セグメントの作成
イベントとタグという2つのデータをもちいて、ユーザーをセグメント化し、配信をすることができます。

例えば、タグの場合はiOSユーザーとAndroidユーザーに別の配信を送る際に使用できます。イベントの場合は初回起動ユーザーや、課金ユーザーに配信を送る際に使用できます。NOTを追加すると、否定条件を入れることができます。

詳細に関しましてはサポートページの[セグメントとは](http://faq.growthbeat.com/article/18-article)をご参照ください。

**セグメントの作成事例は下記を御覧ください。**

* [【セグメント】Androidのバージョン指定のセグメント作成](http://faq.growthbeat.com/article/22-android)
* [【よくあるセグメントの作成方法】性別（男性/女性）](http://faq.growthbeat.com/article/98-article)
* [【よくあるセグメントの作成方法】課金経験あり](http://faq.growthbeat.com/article/94-article)
* [【よくあるセグメントの作成方法】N日間起動していないユーザー](http://faq.growthbeat.com/article/90-n)


## 文字パターン/設定
メニューから【プッシュ送信】を選択し、文字パターンに送信したいテキストを入力してください。（例、【本日初日！】週末限定タイムセール！）
プッシュ配信の最大文字数は80文字です。

<img src="/img/push/push_create_notification_pattern.png" alt="" title="" width="100%"/>

## 配信時間の設定
配信時間を追加で、日付け・時間を設定してください。
プッシュ通知の配信時間を複数にわけることが可能です。

<img src="/img/push/push_create_notification_time.png" alt="" title="" width="100%"/>

## カスタムフィールド
あるプッシュ通知から起動した際にアプリに追加情報を伝えたい時があると思います。その際にこちらのカスタムフィールドをお使い下さい。記述フォーマットはJSONです。

具体的な実装方法は下記をご参照ください。

* [カスタムフィールドを受け取る実装](http://faq.growthbeat.com/article/48-article)

<img src="/img/push/push_create_notification_customfield.png" alt="" title="" width="100%"/>

## 1パターンの配信

<img src="/img/push/push_pattern.png" alt="" title="" width="100%"/>

### サウンド
プッシュ通知を受け取った際に音が鳴ります。

### バッジ
プッシュ通知を受け取った際に赤色の数値をアプリのアイコンに表示させます。

### カスタムフィールドに通知IDを追加
Growth Pushの送信画面で「通知IDを追加」のオプションを設定いただくと、プッシュ通知のペイロードに、growthpushというキーのオブジェクトが追加されます。
 `{"growthpush":{"notificationId":10000}}`

**例えば下記のような時に使用します。**

* 独自のプッシュ通知機構を既に実装されている場合、Growth Pushから配信されたプッシュ通知を区別したい場合
* クライアントSDK側でどの通知が開かれたかを計測したい場合

## 秒間配信数
秒間配信数は、配信速度は、「1秒間に何通を送信するか」の数字で設定していただくことが可能です。 たとえば、100を設定した場合、1秒あたり100通程度の送信となるように配信間隔を調整します。

# 自動配信設定
配信作成の設定に加えて自動配信設定の項目で、配信開始、配信終了、配信間隔を設定します。

<img src="/img/push/push_automation.png" alt="" title="" width="100%"/>

## 重複解除
管理画面の「重複排除」にチェックをすると、一度自動配信が配信されたユーザーには同一の自動配信からプッシュ通知が配信されなくなります。この設定をしている場合、ある日に「1週間起動をしていないユーザー」に該当したユーザーは、翌日に「1週間起動をしていないユーザー」に該当したとしてもプッシュ通知は配信されません。

<img src="/img/push/pusn_ignore_duplicate.png" alt="" title="" width="100%"/>

## 配信時間設定
配信時間を追加で、日付け、時間を設定できます。

## 配信間隔
自動配信設定の際に、いつからいつまでを何時間間隔で設定することが可能です。

# 送信履歴
配信設定した文言とレポートを確認することができます。

**プッシュ通知の配信状況を確認する**

「完了(Completed)」となっている送信は、配信処理が終了していますが、その他のステータスのものは送信処理の途中です。配信が完了するまでお待ちください。

<img src="/img/push/push_notification_status.png" alt="" title="" width="100%"/>

**プッシュ通知の配信の詳細を確認する**

配信が完了している場合は、配信の詳細を確認してください。「送信履歴」からプッシュ通知のメッセージ部分のリンクをクリックしていただくと詳細をご覧いただくことができます。

<img src="/img/push/push_notification_detail.png" alt="" title="" width="100%"/>

ここで実際に配信されている数が確認できるので、配信数がゼロとなっている場合は、デバイスが正しく登録されていない状況が考えられます。配信ステータスが「失敗(Failure)」となっている場合は、以下の方法でログを確認してください。

**プッシュ通知の配信のログを確認する**

ログを確認するには、配信の行をクリックしてください。（リンクになっていませんが、しばらくするとポップアップが出現します。）

<img src="/img/push/push_show_log.png" alt="" title="" width="100%"/>

証明書などに問題がある場合は、ここに失敗のエラーメッセージが出ます。エラーを確認して、対応をおこなってください。

## レポート
配信総人数、イベント発生人数、割合を見ることができます。配信時間から最大24時間経過してから正常な値がご確認いただけます。
また、イベントが未設定の場合はこちらの画面は「There is no event.」となります。

<img src="/img/push/push_report.png" alt="" title="" width="100%"/>

## CSVエクスポート
指定した期間の配信データを一括でダウンロードすることができます。

<img src="/img/push/push_csv_export.png" alt="" title="" width="100%"/>

## Excelインポート
配信予約をExcelで入稿することが可能です。「こちら」の部分をクリックしてフォーマットをダウンロードして頂き、項目を入力してから「ファイルを選択」でExcelをインポートして配信設定が完了します。こちらの機能は**β版**となります。配信内容に誤りがある場合は手動で停止して頂く必要があります。

<img src="/img/push/push_excel_import.png" alt="" title="" width="100%"/>

# デバイス
デバイスではデバイストークンの状況を確認することができます。デバイストークンのインポート機能もあり、CSVで一度に20万件まで送ることができます。端末のステータスは下記のように管理されており、実際に配信されるのは active の端末となります。また、**一度 inactive になった端末は、手動にて更新ボタンを押さないかぎり active に変化することはありません。**

* unknown：未検証状態
* validating：検証処理中
* active：検証済み
* invalid：正しくないデバイストークン
* inactive：プッシュ通知送信後、アプリをアンインストールもしくはプッシュ通知をオフにしているしていると分かったデバイス

<img src="/img/push/push_device_list.png" alt="" title="" width="100%"/>

**各ステータスに関するトラブルシューティングは下記FAQを御覧ください**

* [デバイストークンが「invalid(不正)」になる](http://faq.growthbeat.com/article/101-invalid)
* [（ステータス）active時にプッシュ送信すると、inactiveに変わる状況とは？](http://faq.growthbeat.com/article/76-activeinactive)
* [Push通知が届かない場合のトラブルシューティング](http://faq.growthbeat.com/article/60-push)

# イベント
GrowthPushに登録されているイベントを一覧で表示する画面です。一覧項目は以下の3つになっており、レポートボタンをクリックするとそれぞれのイベントを起こしたユーザーのログを確認することができます。詳細に関しましてはサポートページの[イベントとは](http://faq.growthbeat.com/article/17-article)をご参照ください。

<img src="/img/push/push_event_list.png" alt="" title="" width="100%"/>

# タグ
GrowthPushに登録されているタグを一覧で表示する画面です。一覧項目は以下の3つになっており、詳細ボタンをクリックするとそれぞれのタグを取得したユーザーのログを確認することができます。詳細に関しましてはサポートページの[タグとは](http://faq.growthbeat.com/article/16-article)をご参照ください。

<img src="/img/push/push_tag_list.png" alt="" title="" width="100%"/>

# セグメント
作成したセグメント一覧の人数を見ることができます。更新ボタンを押すと、リアルタイムの人数が表示されます。セグメントの人数として表示される人数は概算となっており、配信されるのは、この人数のうち、**実際に配信が可能と判定されている端末のみ**となります。

詳細に関しましてはサポートページの[セグメントとは](http://faq.growthbeat.com/article/18-article)をご参照ください。

<img src="/img/push/push_segment_list.png" alt="" title="" width="100%"/>

<!--more-->