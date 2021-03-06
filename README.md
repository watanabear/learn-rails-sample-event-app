# learn-rails-sample-event-app
## Overview
Rails学習のためにサンプルとしてイベント告知アプリを作成する

## 実装する主な仕様
- ユーザは作成されたイベント情報を閲覧することができる
    - デフォルトで開始時間が現在時刻以降のイベントが開始時間の昇順で表示される
    - 10件毎にページネーション
    - イベント名および開始時間でイベントを検索し、絞り込むことができる
- Twitterでログインできる
- ログインしたユーザーはイベントを作成できる
    - イベントの情報として作成者、イベントの名前、イベントの画像、開催場所、開始時間、終了時間、イベント詳細、参加者一覧があり、すべてのユーザーが閲覧することができる
- ユーザーは自分が作成したイベントであれば削除することができる
    - イベントに参加するときに短いコメントを付けることができる
    - ログインしたユーザーはイベントの参加をキャンセルすることができる
- ログインしたユーザーは退会することができる
    - ただし、関連する未開催のイベントが存在しないときに限る
- 退会したユーザーの情報は削除される
- 退会したユーザーが作成したイベントはそのまま残る
- イベントを作成したユーザーが退会している場合、作成したユーザーの情報として「退会したユーザーです」と表示される
- イベントに参加したユーザーが退会している場合、参加したユーザーの情報として「退会したユーザーです」と表示される

## ルーティング仕様
|path|method|description|
|---|---|---|
|/|get|イベント一覧表示|
|/auth/:provider/callback|get|ログイン/ユーザー作成処理を実行|
|/logout|get|ログアウト|
|/events/new|get|イベント作成用のフォームを表示|
|/events|post|イベント作成処理を実行|
|/events/:id|get|イベント詳細ページを表示|
|/events/:id/edit|get|イベント編集用のフォームを表示|
|/events/:id|patch|イベント編集処理を実行する|
|/events/:id|delete|イベント削除処理を実行する|
|/events/:event_id/tickets|post|イベント参加処理を実行する|
|/events/:event_id/tickets/:id|delete|イベント参加キャンセルを実行する|
|/user/retire|get|退会用画面を表示する|
|/user|delete|退会処理を実行する|

### Twitterアカウントでログインする機能
- ヘッダーに「Twitter」でログインのリンクを追加する
- 「Twitterでログイン」をクリックするとTwitterのアプリケーション認証画面に遷移する
- Twitterアプリケーション認証画面で適切なユーザー名とパスワードを入力するとログインできる
- ログインした状態だと「Twiterでログイン」の代わりに「ログアウト」というリンクが表示される
- 「ログアウト」をクリックするとログアウトできる

### イベントの閲覧機能
- イベントを登録したときに、イベント詳細ページに遷移する
- トップページに、未開催のイベント一覧が表示される
- イベント一覧からイベント詳細ページに遷移できる

### イベント編集・削除機能
- イベント詳細ページに「イベントを編集する」リンクを追加する
    - イベントを作成したユーザーがアクセスしたときだけ表示する
- 「イベントを編集する」をクリックすると、イベント編集フォームに遷移する
- イベント編集フォームで間違った入力をするとエラーメッセージが表示される
- イベント編集ふぉむで正しく入力するとイベントが更新される
- イベント詳細ページに「イベントを削除する」リンクを追加する
    - イベントを作成したユーザーがアクセスしたときだけ表示する
- 「イベントを削除する」をクリックすると確認ダイアログが表示され、OKするとイベントが削除される

### 登録されたイベントへの参加機能・参加キャンセル機能
- イベント詳細ページに「参加する」リンクを作成する
- ログイン状態で「参加する」をクリックすると、コメント入力用のモーダルウィンドウが表示される
- コメントを正しく入力すると参加が完了する
- イベント詳細ページに参加者一覧を表示する
- 未ログイン状態で「参加する」をクリックすると、トップページにリダイレクトされる



























