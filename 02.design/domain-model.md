# ドメインモデル

```mermaid
classDiagram
  namespace ユーザー集約 {
    %% ユーザー
    class User {
      <<AggregateRoot>>
      Id: Guid
      Name: string
      Email: Email
      Role: SystemRoke
    }

    %% 値オブジェクト
    class Email {
      <<ValueObject>>
      Value: string
    }
    class SystemRole {
      <<ValueObject>>
      Value: RoleType
      ---
      RoleType
      - Admin
      - User
    }
  }

  namespace プロジェクト集約 {
    %% プロジェクト
    class Project {
      <<AggregateRoot>>
      Id: Guid
      Name: string
      Description: string?
    }

    %% 値オブジェクト
    class ProjectMember {
      <<ValueObject>>
      UserId: Guid
      Role: ProjectRole
    }
    class ProjectRole {
      <<ValueObject>>
      Value: RoleType
      RoleType
      - ProjectManager
      - Member
    }
  }

  namespace チケット集約 {
    %% チケット
    class Ticket {
      <<AggregateRoot>>
      Id: Guid
      ProjectId: Guid
      Title: TicketTitle
      Description: TicketDescription
      Schedule: TicketSchedule
      Status: TicketStatus
      AssigneeId: Guid?
      CompletionCriteria: string?
      Comments: List<Comment>
    }


    %% コメント
    class Comment {
      <<Entity>>
      Id: Guid
      TicketId: Guid
      AuthorId: Guid
      Content: string
    }

    %% チケット操作履歴
    class TicketHistory {
      <<Entity>>
      Id: Guid
      TicketId: Guid
      ActorId: Guid
      OccurredAt: DateTime
      Action: TicketHistoryAction
      ---
      TicketHistoryType
      - TicketCreated
      - TicketUpdated
      - TicketCommentAdded
    }

    %% チケット操作履歴内容
    class TicketHistoryChange {
      <<Abstract>>
    }

    class TitleChanged {
      Before: TicketTitle?
      After: TicketTitle
    }
    class DescriptionChanged {
      Before: TicketDescription?
      After: TicketDescription
    }
    class ScheduleChanged {
      Before: TicketSchedule?
      After: TicketSchedule?
    }
    class StatusChanged {
      Before: TicketStatus?
      After: TicketStatus
    }
    class AssigneeChanged {
      Before: Guid?
      After: Guid?
    }
    class CompletionCriteriaChanged {
      Before: string?
      After: string?
    }

    %% 値オブジェクト
    class TicketTitle {
      <<ValueObject>>
      Value: string
    }
    %% チケット説明
    class TicketDescription {
      <<ValueObject>>
      Value: string
    }
    %% チケットスケジュール
    class TicketSchedule {
      <<ValueObject>>
      StartDate: Date?
      EndDate: Date?
    }
    class TicketStatus {
      <<ValueObject>>
      Value: StatusType
      ---
      StatusType
      - Todo
      - InProgress
      - Resolved
      - Done
    }
  }

  namespace 通知集約 {
    %% 通知
    class Notification {
      <<AggregateRoute>>
      Id: Guid
      RecipientId: Guid
      Category: NotificationCategory
      Message: string
      IsRead: bool
      CreatedAt: DateTime
    }

    %% 値オブジェクト
    class NotificationCategory {
      <<ValueObject>>
      Value: Category
      ---
      Category
      - 各種イベント
    }
  }

  %% ドメインルール
  note for User "
  Email: xxx@yyy.com 形式
  "
  note for Ticket "
  Deadline: 過去日付不可
  TicketStats: 初期状態 Todo
  CompletionCriteria: チケット完了とみなす条件
  "
  note for Notification "
  SubjectId: 通知の参照元となるID
  "

  %% 関連
  Project "1" --> "many" Ticket : has
  User "1" --> "many" Ticket : assigned
  Ticket "1" *-- "many" Comment : contains
  User "1" --> "many" Comment : author
  Ticket "1" *-- "many" TicketHistory : has
  TicketHistory "1" *-- "many" TicketHistoryChange : contains
  User "1" --> "many" Notification : target
  TicketHistoryChange <|-- TitleChanged
  TicketHistoryChange <|-- DescriptionChanged
  TicketHistoryChange <|-- ScheduleChanged
  TicketHistoryChange <|-- StatusChanged
  TicketHistoryChange <|-- AssigneeChanged
  TicketHistoryChange <|-- CompletionCriteriaChanged

  %% 値オブジェクトの使用関係
  User --> Email
  User --> SystemRole
  Project --> ProjectMember
  ProjectMember --> ProjectRole
  Ticket --> TicketTitle
  Ticket --> TicketDescription
  Ticket --> TicketSchedule
  Ticket --> TicketStatus
  Notification --> NotificationCategory
```
