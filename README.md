# my-node-app

Учебный проект с CI на GitHub Actions для Node.js-приложения.

## 📌 Цель работы

Настроить CI для Node.js-проекта с автоматической проверкой кода, тестами и сборкой Docker-образа.

## 🎯 Что делает CI

При каждом push/PR автоматически:

- **Линтинг** (ESLint) — проверка кода на ошибки
- **Тесты** (Jest) — запуск unit-тестов
- **Сборка Docker-образа** — без публикации

## 📂 Структура проекта

```
my-node-app/
├── .github/
│   └── workflows/
│       └── ci.yml            # GitHub Actions workflow
├── src/
│   └── index.js              # основной код
├── tests/
│   └── index.test.js         # тесты (Jest)
├── package.json              # зависимости и скрипты
├── package-lock.json         # фиксация версий
├── .eslintrc.json            # конфигурация ESLint
├── Dockerfile
└── README.md
```

## 🟩 Основной код

```javascript
function add(a, b) {
    return a + b;
}
function main() {
    console.log("Hello from Node.js app!");
}
if (require.main === module) {
    main();
}
module.exports = { add };
```

## 🚀 Запуск локально

### Через Docker (рекомендуется)

```bash
docker build -t my-node-app:latest .
docker run --rm my-node-app:latest
```

### Без Docker (нужен Node.js 18+)

```bash
npm ci
npm run lint
npm test
node src/index.js
```

## 📸 Результат запуска

Ниже — вывод приложения в терминале после сборки и запуска Docker-контейнера:

![Вывод приложения в терминале](/img/terminal.png)

```
Hello from Node.js app!
```

## ⚙️ CI Workflow

Workflow запускается на **3 версиях Node.js** (18.x, 20.x, 22.x) параллельно:

- Node.js 18.x
- Node.js 20.x
- Node.js 22.x

После успешных тестов запускается job сборки Docker-образа.

## ✅ Результат

При каждом push в ветку `main` запускается CI.
На вкладке **Actions** отображаются 🟢 зелёные галочки — все проверки пройдены успешно.

**Ссылка на Actions:**  
https://github.com/xem1zo/my-node-app/actions

## 📝 Вывод

В ходе работы я освоил:

- Настройку CI для Node.js-проектов в GitHub Actions
- Использование matrix strategy для тестирования на нескольких версиях Node.js
- Линтинг кода через ESLint
- Тестирование через Jest
- Сборку Docker-образа в CI без публикации
- Генерацию `package-lock.json` через Docker без локальной установки Node.js
