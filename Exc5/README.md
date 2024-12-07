# GraphQL Схема

---

## Описание схемы

### Типы

#### **Client**

```graphql
type Client {
  id: String!
  name: String
  age: Int
  documents: [Document]
  relatives: [Relative]
}
```

#### **Document**

```graphql
type Document {
  id: String!
  type: String
  number: String
  issueDate: String
  expiryDate: String
}
```

#### **Relative**

```graphql
type Relative {
  id: String!
  relationType: String
  name: String
  age: Int
}
```

---

### Запросы

#### **Получение клиента по ID**

```graphql
query {
  client(id: "123") {
    id
    name
    age
  }
}
```

#### **Получение документов клиента**

```graphql
query {
  clientDocuments(id: "123") {
    id
    type
    number
  }
}
```

#### **Получение родственников клиента**

```graphql
query {
  clientRelatives(id: "123") {
    id
    name
    relationType
  }
}
```

#### **Комбинированный запрос**
Получение информации о клиенте вместе с его документами и родственниками в одном запросе.

```graphql
query {
  client(id: "123") {
    id
    name
    documents {
      id
      type
    }
    relatives {
      name
      relationType
    }
  }
}
```

---

## Преимущества использования GraphQL

1. **Гибкость**: клиенты могут запрашивать только необходимые данные, что снижает объем передаваемой информации и нет необходимости запрашивать избыточные данные.
2. **Снижение нагрузки**: Уменьшается RPS при помощи комбинированных запросов.

---
