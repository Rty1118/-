这是一份根据类图代码@startuml
class 用户接口UserInterface {
  - accountBook: AccountBook
  + displayMenu(): void
  + record(): void
  + count(): void
  + mine(): void
}

class 记账本AccountBook {
  - transactions: Transaction[]
  - int: liveTransactions[]
  - totalTransactions: int
  - nextTransactionId: int
  + addTransaction(amount, type, keyword, note, time): void
  + deleteTransaction(id): void
  + changeTransaction(id): void
  + displayAllTransactions(): void
  + calculateTotalIncome(): double
  + calculateTotalExpense(): double
  + displayStatistics(): void
  + search_by_keyword(keyword): void
  + search_by_time(time): void
  + search_by_type(type): void
  + search_by_amount(amount): void
  + search_by_note(string): void
  + check(): void
}

class 交易Transaction {
  - id: int
  - amount: double
  - type: TransactionType
  - keyword: KeyType
  - date: string
  - note: string
  - deadtime: string
  + getId(): int
  + getAmount(): double
  + getType(): TransactionType
  + getKeyword(): KeyType
  + getDate(): string
  + getNote(): string
  + display(): void
}

class 用户界面UI{
}

enum TransactionType {
  INCOME
  EXPENSE
}

enum KeyType{
  TRAVEL
  FOOD
  STUDY
  RENT
  WAGES
  MEDICINE
  TRANSPORTATION
  OTHERS
}

note right of 交易Transaction::type
  表示是收入还是支出
end note

note left of 交易Transaction::keyword
  表示交易分类的关键词
end note

note left of 记账本AccountBook::check
  把存在时间超过deadtime的记录都消除
end note


用户接口UserInterface --> 记账本AccountBook : depends on
记账本AccountBook o--> "many" 交易Transaction : contains
交易Transaction --> TransactionType : uses
交易Transaction --> KeyType : uses
@enduml
用大模型生成的智能记账本系统的代码，没有实现UI界面，通过命令行展示交易信息和操作结果
