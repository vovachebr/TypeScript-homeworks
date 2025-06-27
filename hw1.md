# 🧠 Введение в TypeScript

## 🎯 Цель

Ознакомиться с TypeScript, установить и настроить окружение, скомпилировать и запустить простой TypeScript-код.

---

## 📦 Задание: Инициализация проекта Budget Tracker CLI

### 1. Установка окружения

- Установите Node.js (если ещё не установлен): https://nodejs.org
- Установите TypeScript глобально:

```bash
npm install -g typescript
```

- Проверьте установился ли TypeScript:

```bash
tsc --version
```

- Сформируйте файл `.gitignore` со следующим содержимым:

```
node_modules
package-lock.json
dist
```

---

### 2. Инициализация проекта

- Создайте новую папку проекта:

```bash
mkdir budget-tracker-cli
cd budget-tracker-cli
```

- Инициализируйте npm-проект:

```bash
npm init
```

Установите TypeScript в проект:

```bash
npm i typescript --save-dev
```

- Инициализируйте TypeScript-конфигурацию:

```bash
npx tsc --init
```

- Обновите `tsconfig.json`, чтобы он содержал следующие параметры:

```json
{
  "compilerOptions": {
      "target": "ES2020",
      "module": "commonjs",
      "rootDir": "./src",
      "outDir": "./dist",
      "strict": true,
      "esModuleInterop": true
    }
}
```

---

### 3. Создание первого TypeScript-файла

- Создай папку `src` и файл `index.ts`:

- Добавьте в файл следующий код:

```ts
console.log("🚀 Budget Tracker CLI");
```

---

### 4. Компиляция и запуск

- Скомпилируйте проект:

```bash
npx tsc
```

- Убедитесь, что в папке `dist` появился файл `index.js`
- Запустите его через Node.js:

```bash
node dist/index.js
```

- В терминале должно появиться сообщение:

```
🚀 Budget Tracker CLI
```

---

### 5. Добавьте npm-скрипты

- В файл `package.json` добавьте раздел `scripts`:

```json
"scripts": {
  "build": "tsc",
  "start": "node dist/index.js",
  "dev": "tsc --watch"
}
```

Теперь можно запускать проект с помощью:

- 🔨 Сборка: `npm run build`
- ▶️ Запуск: `npm start`
- 👀 Режим разработки: `npm run dev`

---

### 6. (Дополнительно) Добавьте описание проекта

- Создайте файл `README.md` с описанием будущего проекта

## 📁 Структура проекта после выполнения

```
budget-tracker-cli/
├── node_modules/
├── src/
│   └── index.ts
├── dist/
│   └── index.js
├── package.json
├── tsconfig.json
└── README.md (по желанию)
```

---

## ✅ Критерии выполненного задания

- [ ] Установлен TypeScript и инициализирован tsconfig.json
- [ ] Создан файл index.ts с выводом приветственного сообщения
- [ ] Код успешно компилируется в папку dist
- [ ] Программа запускается через Node.js и выводит сообщение
- [ ] Добавлены npm-скрипты для сборки и запуска
