# API一覧

## 認証

| メソッド | パス | 機能 |
|-----------|------|------|
| POST | /auth/login | ユーザーログイン（JWT発行） |
| POST | /auth/logout | ログアウト（トークン無効化） |

## プロジェクト

| メソッド | パス | 機能 |
|-----------|------|------|
| GET | /projects | プロジェクト一覧取得 |
| GET | /projects/{projectId} | プロジェクト詳細取得 |
| POST | /projects | プロジェクト作成 |
| PATCH | /projects/{projectId} | プロジェクト編集 |
| DELETE | /projects/{projectId} | プロジェクト削除 |

## チケット

| メソッド | パス | 機能 |
|-----------|------|------|
| GET | /projects/{projectId}/tickets | プロジェクト内チケット一覧取得 |
| GET | /projects/{projectId}/tickets/{ticketId} | チケット詳細取得 |
| POST | /projects/{projectId}/tickets | チケット作成 |
| PATCH | /projects/{projectId}/tickets/{ticketId} | チケット編集 |
| DELETE | /projects/{projectId}/tickets/{ticketId} | チケット削除 |
| GET | /projects/{projectId}/tickets/{ticketId}/comments | チケットのコメント一覧取得 |
| POST | /projects/{projectId}/tickets/{ticketId}/comments | チケットにコメント投稿 |
| PATCH | /projects/{projectId}/tickets/{ticketId}/comments | チケットコメント編集 |
| DELETE | /projects/{projectId}/tickets/{ticketId}/comments/{commentId} | チケットコメント削除 |

## ユーザー

| メソッド | パス | 機能 |
|-----------|------|------|
| GET | /users | ユーザー一覧取得 |
| GET | /users/{userId} | ユーザー詳細取得 |
| POST | /users | ユーザー作成 |
| PATCH | /users/{userId} | ユーザー編集 |
| DELETE | /users/{userId} | ユーザー削除 |

## 通知

| メソッド | パス | 機能 |
|-----------|------|------|
| GET | /notifications | ログインユーザー宛の通知一覧取得 |
| PATCH | /notifications/{notificationId}/read | 通知既読更新 |
