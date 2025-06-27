# 🧠 Модули и пространства имён в TypeScript

## 🎯 Цель

Научиться организовывать код в модули, использовать экспорт и импорт, а также понять отличие модулей от пространств имён (namespace). Научиться структурировать проект так, чтобы каждый интерфейс и класс находился в отдельном файле с использованием модулей ES.

---

## 📦 Задание: Организация проекта budget-tracker-cli с использованием модулей

В рамках проекта budget-tracker-cli реорганизуйте код, связанный с управлением бюджетом, расходами и доходами, используя модули ES. Каждый интерфейс и класс должен находиться в отдельном файле, а взаимодействие между ними должно осуществляться через экспорт и импорт.

---

### 1. Структура проекта

Приведите к виду следующую структуру в папке `src`:

```md
src/
├── interfaces/
│   ├── TransactionType.ts
│   ├── ITransaction.ts
│   ├── IAccount.ts
│   ├── ISummary.ts
│   └── IAccountManager.ts
├── classes/
│   ├── Transaction.ts
│   ├── Account.ts
│   └── AccountManager.ts
├── index.ts
```

---

### 2. Интерфейсы

В папке `src/interfaces/` создайте файлы с определениями интерфейсов:

```ts
namespace BudgetTracker {
  export interface ИмяИнтерфейса {
    // описание интерфейса
  }
}
```

---

### 3. Классы

В папке `src/classes/` создайте файлы с реализацией классов:

```ts
namespace BudgetTracker {
  export class ИмяКласса {
    // реализация класса
  }
}
```

---

### 4. Главный файл `index.ts`

В файле `src/index.ts` импортируйте классы и создайте пример использования:

```ts
import { Account } from './classes/Account';
import { Transaction } from './classes/Transaction';
import { AccountManager } from './classes/AccountManager';

const personalAccount = new Account(1, 'Личный бюджет');
personalAccount.addTransaction(new Transaction(1, 1000, 'income', '2023-01-01T00:00:00Z', 'Зарплата'));
personalAccount.addTransaction(new Transaction(2, 200, 'expense', '2023-01-05T00:00:00Z', 'Продукты'));
personalAccount.addTransaction(new Transaction(3, 150, 'expense', '2023-01-10T00:00:00Z', 'Коммунальные услуги'));

const manager = new AccountManager();
manager.addAccount(personalAccount);

console.log(String(personalAccount));
console.log(`Общий баланс всех бюджетов: ${manager.balance} ₽`);

console.log('\nТранзакции личного бюджета:');
personalAccount.getTransactions().forEach(t => console.log(t.toString()));
```

## ℹ️ Дополнительно

- Обратите внимание, что использование namespace (пространств имён) в современных TypeScript-проектах часто заменяется на модули ES.
- Для корректной работы модулей убедитесь, что в `tsconfig.json` стоит `"module": "none"`, `"moduleResolution": "node"` и `"outFile": "./dist/budget-tracker.js"`.
- Так как файлы `types.ts` и `classes.ts` теперь не используются, их стоит удалить.

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
│   │   └── IAccountManager.ts
│   ├── classes/
│   │   ├── Transaction.ts
│   │   ├── Account.ts
│   │   └── AccountManager.ts
│   └── index.ts
├── dist/
├── package.json
├── tsconfig.json
└── README.md
```

---

## ✅ Критерии выполненного задания

- [ ] Все интерфейсы и классы должны быть объявлены внутри одного общего `namespace BudgetTracker`
- [ ] Каждый интерфейс и класс должен находиться в отдельном файле
- [ ] В каждом файле должен быть объявлен тот же namespace `BudgetTracker`
- [ ] Для доступа к сущностям внутри namespace не использовать `import`/`export`, а полагаться на объединение деклараций namespace
- [ ] В главном файле (`index.ts`) использовать сущности через пространство имён, например: `BudgetTracker.Account`, `BudgetTracker.Transaction` и т.п
- [ ] Использовать компиляцию TypeScript с поддержкой namespace (без модулей ES)

---