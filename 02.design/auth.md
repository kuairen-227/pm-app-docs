# 認証・認可

## 認証方式

- JWT (JSON Web Token) を使用
- ログイン成功時にアクセストークンを発行
- フロントは Authorization ヘッダーでリクエスト

## ユーザーRole

Enum で管理

| Role | 権限 |
| - | - |
| Admin | 全権限 |
| Manager | プロジェクト作成・編集・削除 |
| Member | タスク更新・担当者アサイン |
