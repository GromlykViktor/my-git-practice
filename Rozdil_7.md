РОЗДІЛ 7. МОДЕЛЬ ДАНИХ ІНФОРМАЦІЙНОЇ СИСТЕМИ
7.1. Загальна характеристика моделі даних

Модель даних реалізується у вигляді реляційної бази даних.
Основними сутностями є:

Користувач (User)

Роль (Role)

Книга (Book)

Видача (Loan)

Автор (Author)

7.2. Опис сутностей
1️⃣ User (Користувач) 
| Поле    | Тип      | Опис                     |
| ------- | -------- | ------------------------ |
| id      | INT (PK) | Унікальний ідентифікатор |
| name    | VARCHAR  | ПІБ                      |
| email   | VARCHAR  | Електронна пошта         |
| role_id | INT (FK) | Роль користувача         | 
2️⃣ Role (Роль) 
| Поле      | Тип      |
| --------- | -------- |
| id        | INT (PK) |
| role_name | VARCHAR  | 
3️⃣ Book (Книга) 
| Поле             | Тип      |
| ---------------- | -------- |
| id               | INT (PK) |
| title            | VARCHAR  |
| author_id        | INT (FK) |
| year             | INT      |
| genre            | VARCHAR  |
| available_copies | INT      | 
4️⃣ Author (Автор) 
| Поле      | Тип      |
| --------- | -------- |
| id        | INT (PK) |
| full_name | VARCHAR  |
5️⃣ Loan (Видача) 
| Поле        | Тип      |
| ----------- | -------- |
| id          | INT (PK) |
| user_id     | INT (FK) |
| book_id     | INT (FK) |
| issue_date  | DATE     |
| return_date | DATE     |
| status      | VARCHAR  |
7.3. Зв’язки між сутностями

Один Role → багато Users (1:M)

Один Author → багато Books (1:M)

Один User → багато Loans (1:M)

Одна Book → багато Loans (1:M) 
7.4. UML-діаграма класів (PlantUML) 
@startuml

class User {
  id : int
  name : string
  email : string
}

class Role {
  id : int
  role_name : string
}

class Book {
  id : int
  title : string
  year : int
  genre : string
  available_copies : int
}

class Author {
  id : int
  full_name : string
}

class Loan {
  id : int
  issue_date : date
  return_date : date
  status : string
}

User "1" -- "0..*" Loan
Book "1" -- "0..*" Loan
Author "1" -- "0..*" Book
Role "1" -- "0..*" User

@enduml


