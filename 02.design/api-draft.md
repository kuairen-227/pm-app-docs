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
| GET | /projects/{id} | プロジェクト詳細取得 |
| POST | /projects | プロジェクト作成 |
| PATCH | /projects/{id} | プロジェクト編集 |
| DELETE | /projects/{id} | プロジェクト削除 |

## チケット

| メソッド | パス | 機能 |
|-----------|------|------|
| GET | /projects/{projectId}/tickets | プロジェクト内チケット一覧取得 |
| PATCH | /projects/{projectId}/tickets/{ticketId} | チケット詳細取得 |
| POST | /projects/{projectId}/tickets | チケット作成 |
| PATCH | /projects/{projectId}/tickets/{ticketId} | チケット編集 |
| DELETE | /projects/{projectId}/tickets/{ticketId} | チケット削除 |

## ユーザー

| メソッド | パス | 機能 |
|-----------|------|------|
| GET | /users | ユーザー一覧取得 |
| GET | /users/{id} | ユーザー詳細取得 |
| POST | /users | ユーザー作成 |
| PATCH | /users/{id} | ユーザー編集 |
| DELETE | /users/{id} | ユーザー削除 |

## 通知

| メソッド | パス | 機能 |
|-----------|------|------|
| GET | /notifications | ログインユーザー宛の通知一覧取得 |
| PATCH | /notifications/{id}/read | 通知既読更新 |
