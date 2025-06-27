# 🧠 Утилитные типы TypeScript в проекте budget-tracker-cli

## 🎯 Цель

Научиться применять утилитные типы TypeScript (`Partial`, `Required`, `Pick`, `Omit`, `Record`, `NonNullable`, `ReturnType`, `Parameters` и др.) для повышения гибкости и безопасности типов в проекте учёта бюджета.

---

## 📦 Задание: Улучшение типизации и работы с данными в budget-tracker-cli

В рамках проекта budget-tracker-cli, используя интерфейсы и типы из `src/interfaces`, выполните следующие задачи с применением утилитных типов в файле `utility-types.ts` (`src/interfaces/utility-types.ts`).

---

### 1. Частичное обновление транзакций и аккаунтов

- Создайте тип `TransactionUpdate`, который допускает частичное обновление свойств транзакции (`ITransaction`), используя `Partial<ITransaction>`.
- Создайте тип `AccountUpdate`, аналогично для обновления аккаунта (`IAccount`).

- Напишите метод класса `Transaction` для обновления транзакции `update(update: TransactionUpdate): void`, который обновляет переданные поля транзакции
- Напишите метод класса `Account` для обновления счёта `update(update: AccountUpdate): void`, который обновляет переданные поля счёта
- Удалите модификаторы `readonly` (только не идентификатор, так как его нельзя менять), чтобы свойства можно было обновлять

---

### 2. Обязательные поля и исключения

- Создайте тип `CompleteTransaction`, где все поля интерфейса `ITransaction` обязательны (`Required<ITransaction>`).
- Создайте тип `TransactionWithoutDescription`, который содержит все поля `ITransaction`, кроме `description` (`Omit<ITransaction, 'description'>`).

---

### 3. Выборка ключевых полей

- Создайте тип `TransactionPreview`, который содержит только `id`, `amount`, `type` и `date` (`Pick<ITransaction, 'id' | 'amount' | 'type' | 'date'>`).
- Создайте тип `AccountInfo`, который содержит только `id` и `name` из `IAccount`.

---

### 4. Словарь лимитов по категориям транзакций

- В `TransactionType` добавьте категории транзакций (`income`, `expense`).
- Создайте тип `CategoryLimits` с помощью `Record<TransactionType, number>`, где ключ — тип транзакции, а значение — лимит суммы.

```ts
const limits: CategoryLimits = {
  income: 10000,
  expense: 5000,
};
```

---

### 5. Работа с типами функций

- Используя функцию-конструктор класса `Transaction` из `src/classes.ts`, создайте тип `TransactionConstructorParams`, который представляет параметры конструктора (`ConstructorParameters<typeof Transaction>`).
- Создайте тип `TransactionInstance`, который представляет возвращаемый тип конструктора (`InstanceType<typeof Transaction>`).

---

### 6. Работа с необязательными и nullable полями

- Создайте тип `NullableDescription`, который допускает, что поле `description` в `ITransaction` может быть `string` или `null`.

### 7. Практика использования созданных типов

- Отредактируйте файл `index.ts` с использованием реализованных методов и типов.

<details>
<summary>Пример использования</summary>

```ts
const personalAccount = new Account('Личный бюджет');
const transaction: Transaction = new Transaction(1000, 'income', '2023-01-01T00:00:00Z', 'Зарплата');

transaction.update({ amount: 1200 });
console.log('Обновлённая транзакция:');
console.log(transaction);

personalAccount.addTransaction(transaction);
personalAccount.addTransaction(new Transaction(200, 'expense', '2023-01-05T00:00:00Z', 'Продукты'));
personalAccount.addTransaction(new Transaction(150, 'expense', '2023-01-09T00:00:00Z', 'Коммунальные услуги'));

personalAccount.update({ name: 'Основной счёт' });
console.log('Обновлённый счёт:');
console.log(personalAccount);

const manager = new AccountManager();
manager.addAccount(personalAccount);

console.log(String(personalAccount));
console.log(`Общий баланс всех бюджетов: ${manager.balance} ₽`);

console.log('\nТранзакции основного счёта:');
personalAccount.getTransactions().forEach(t => console.log(t.toString()));

console.log('Лимит пополнений:', limits.income);
console.log('Лимит трат:', limits.expense);

const transactionParams: TransactionConstructorParams = [500, 'expense', '2023-02-01T00:00:00Z', 'Покупка'];
const newTransaction: TransactionInstance = new Transaction(...transactionParams);
console.log(newTransaction.toString());
```

</details>

---

## 📁 Структура проекта 

```
budget-tracker-cli/
├── src/
│   ├── interfaces/
│   │   ├── TransactionType.ts
│   │   ├── ITransaction.ts
│   │   ├── IAccount.ts
│   │   ├── ISummary.ts
│   │   ├── IAccountManager.ts
│   │   └── utility-types.ts
│   ├── classes/
│   │   ├── Transaction.ts
│   │   ├── Account.ts
│   │   └── AccountManager.ts
│   ├── lib/
│   │   ├── budget-utils.js
│   │   └── budget-utils.d.ts
│   └── index.ts
├── dist/
├── package.json
├── tsconfig.json
└── README.md
```

---

## ✅ Критерии выполненного задания

- [ ] Все новые типы созданы с использованием утилитных типов TypeScript.
- [ ] Функции типизированы корректно и возвращают ожидаемые типы.
- [ ] Код компилируется без ошибок.
- [ ] Типы и функции логично интегрированы с существующими интерфейсами и классами проекта.

---