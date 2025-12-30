# CloudTrail（操作ログ）

## CloudTrail とは？

「誰が・いつ・何をしたか」を記録する操作ログ。

【 記録される例 】

・S3バケットを作成した。

・バケットポリシーを変更した。

・EC2を起動・停止した。

【 記録されない例（重要） 】

・HTMLの中身。

・Webページを誰が見たか。

⇒ これは CloudTrailの仕事じゃない。

## CloudTrailは操作ログ（監査ログ）

・AWS上で実行された すべてのAPI操作を記録する仕組み。

・「誰が・いつ・どのサービスに・何をしたか」を追跡できる。

・セキュリティ監査・不正調査・事故原因特定の基盤。

## AWSはすべてAPIで動いている

・コンソール操作も内部的にはAPI呼び出し。

・EC2起動 = RunInstances

・S3アップロード = PutObject

・つまり「操作＝ログに残る」

## CloudTrailが記録するもの

・管理イベント（デフォルト）

・S3：CreateBucket / PutObject / PutBucketPolicy

・EC2：RunInstances / StopInstances

・実行主体（IAMユーザー / ロール）

・リクエスト内容（JSON）

## CloudTrailが記録しないもの

・Webサイトへのアクセス履歴。

・ファイルの中身。

・誰がHTMLを閲覧したか ⇒ アクセスログ（S3 / ALB / CloudFront）の役割。

## イベント履歴と証跡（Trail）の違い

【 イベント履歴 】

・追加設定なしで見られる。

・90日間のみ保持。

【 証跡（Trail） 】

・ログをS3に保存。

・長期保存・監査対応が可能。

## セキュリティ視点での重要性

・「誰がやったか分からない」を防ぐ。

・変更履歴の証拠になる。

・IAM・S3・EC2すべてと連動する中核サービス。

# 実践

・CloudTrailのイベント履歴を確認。

・S3操作（PutObject / PutBucketPolicy）のログを確認。

・EC2操作（RunInstances 等）のログを確認。

・イベント詳細（eventName / userIdentity）を確認。

・証跡（Trail）を作成し、S3保存を有効化。
