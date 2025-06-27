# 🧠 Интерфейсы и типы (Interfaces и Type Aliases)

## 🎯 Цель

Научиться создавать и использовать интерфейсы и типы в TypeScript для структурирования данных. 

---

## 📦 Задание: Расширение функциональности budget-tracker-cli

В рамках проекта budget-tracker-cli реализуйте интерфейсы и типы для управления данными о бюджетах, расходах и доходах.

1. Создайте файл `src/types.ts`.

2. Определите следующие интерфейсы и типы:

### 1. Тип `TransactionType`

Создайте тип для перечисления типов транзакций. Он должен включать "income" и "expense".

### 2. Интерфейс `ITransaction`

Создайте интерфейс для представления транзакции, который содержит следующие свойства:

- `id`: уникальный идентификатор транзакции (число)
- `amount`: сумма транзакции (число)
- `type`: тип транзакции (строка типа `TransactionType`)
- `date`: дата транзакции (строка в формате ISO)
- `description`: описание транзакции (строка)

### 3. Интерфейс `IAccount`

Создайте интерфейс для представления счёта, который содержит следующие свойства:

- `id`: уникальный идентификатор счёта (число)
- `name`: название счёта (строка)
- `addTransaction(account: ITransaction): void` — добавление новой транзакции
- `removeTransactionById(accountId: number): boolean` - удаление транзакции по идентификатору. Возвращает успешность удаления
- `getTransactions(): ITransaction[]` - получение всех транзакций

### 4. Интерфейс `ISummary`

Создайте интерфейс для сводной информации о счёте, который содержит следующие свойства:

- `income`: общая сумма доходов (число)
- `expenses`: общая сумма расходов (число)
- `balance`: текущий баланс (число)

### 5. Интерфейс `IAccountManager`

Создайте интерфейс для управления счетами с методами:
- `addAccount(account: IAccount): void` — добавление нового счёта
- `removeAccountById(accountId: number): boolean` - удаление счёта по идентификатору. Возвращает успешность удаления
- `getAccounts(): IAccount[]` — получение массива всех счетов
- `getAccountById(id: number): Account | undefined` - получение счёта по идентификатору
- `getSummary(accountId: number): ISummary` — получение сводной информации о конкретном счёте

3. Проверка решения:

- Экспортируйте все типы и интерфейсы из файла `types.ts`
- В файле `index.ts` создайте объект контроля счёта (пока без использования классов), который будет реализовывать интерфейс `IAccountManager`.
- Создайте счёт и добавьте в него несколько транзакций. Счёт должен реализовывать интерфейс `Account`
- Добавьте счёт в объект управления счетов и проверьте работу всех методов


<details>
<summary>Готовый шаблон для ленивых</summary>

```ts
const accountManager: IAccountManager & { accounts: IAccount[] } = {
  accounts: [],
  addAccount(account: Account): void {
    // этот метод добавляет новый счёт в массив accounts
  },
  removeAccountById(accountId: number): boolean {
    // этот метод удаляет счёт по идентификатору
  },
  getAccounts(): Account[] {
    // этот метод возвращает массив всех счётов
  },
  getAccountById(id: number): IAccount | undefined {
    // этот метод возвращает счёт по идентификатору
  },
  getSummary(accountId: number): ISummary {
    // этот метод возвращает сводную информацию о конкретном счёт
  }
}

const account: IAccount & { transactions: ITransaction[] } = {
  id: 1,
  name: "Личный бюджет",
  transactions: [],
  addTransaction(transaction: ITransaction): void {
    // этот метод добавляет транзакцию
  },
  removeTransactionById(transactionId: number): boolean {
    // этот метод удаляет транзакцию по идентификатору
  },
  getTransactions() {
    // этот метод возвращает массив всех транзакций
  }
};

account.addTransaction({
  id: 1,
  amount: 1000,
  type: 'income',
  date: '2023-01-01T00:00:00Z',
  description: 'Зарплата за январь'
});

account.addTransaction({
  id: 2,
  amount: 200,
  type: 'expense',
  date: '2023-01-05T00:00:00Z',
  description: 'Покупка продуктов'
});

account.addTransaction({
  id: 3,
  amount: 150,
  type: 'expense',
  date: '2023-01-10T00:00:00Z',
  description: 'Оплата коммунальных услуг'
});

accountManager.addAccount(account);
console.log("Список всех бюджетов:", accountManager.getAccounts());
console.log("Сводная информация о бюджете:", accountManager.getSummary(1));
accountManager.removeAccountById(account.id);
console.log("Список всех бюджетов:", accountManager.getAccounts());
```

</details>

---

## 📁 Структура проекта

```
budget-tracker-cli/
├── src/
│   ├── index.ts
│   ├── calculation-demo.ts
│   ├── functions.ts
│   └── types.ts
├── dist/
├── package.json
├── tsconfig.json
└── README.md
```

---

## ✅ Критерии выполненного задания

- [ ] Все интерфейсы и типы реализованы в файле `src/types.ts`
- [ ] Все свойства и методы имеют правильные типы
- [ ] Код компилируется без ошибок
- [ ] Все интерфейсы и типы имеют понятные и логичные названия

---