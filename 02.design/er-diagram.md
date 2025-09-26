# ER図

```mermaid
erDiagram
    users {
        GUID id PK
        string name
        string email
        string role
        GUID created_by
        datetime created_at
        GUID updated_by
        datetime updated_at
    }
    projects {
        GUID id PK
        string name
        string description
        GUID created_by
        datetime created_at
        GUID updated_by
        datetime updated_at
    }
    project_members {
        Guid id PK
        Guid project_id FK
        Guid user_id FK
        string role
    }
    tickets {
        GUID id PK
        GUID project_id FK
        string title
        date deadline
        string status
        GUID assignee_id FK
        string completion_criteria
        GUID created_by
        datetime created_at
        GUID updated_by
        datetime updated_at
    }
    comments {
        GUID id PK
        GUID ticket_id FK
        GUID author_id FK
        string content
        datetime created_at
        datetime updated_at
    }
    assignment_history {
        GUID id PK
        GUID ticket_id FK
        GUID assignee_id FK
        GUID previous_assignee_id FK
        string change_type
        datetime changed_at
        GUID created_by
        datetime created_at
        GUID updated_by
        datetime updated_at
    }
    notifications {
        GUID id PK
        GUID user_id FK
        string category
        string message
        bool is_read
        GUID created_by
        datetime created_at
        GUID updated_by
        datetime updated_at
    }

    users ||--o{ project_members : "1:n"
    projects ||--o{ project_members : "1:n"
    projects ||--o{ tickets : "1:n"
    users ||--o{ tickets : "1:n"
    tickets ||--o{ assignment_history : "1:n"
    users ||--o{ notifications : "1:n"
    tickets ||--o{ comments : "1:n"
    users ||--o{ comments : "1:n"
```
