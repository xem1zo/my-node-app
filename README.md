# my-go-app

Учебный проект с CI на GitHub Actions для Go-приложения.

## 📌 Цель работы

Настроить CI для Go-проекта с линтингом, тестами, покрытием и сборкой Docker-образа.

## 🎯 Что делает CI

При каждом push/PR автоматически:

- **Линтинг** (golangci-lint)
- **Тесты** (`go test` с покрытием)
- **Сохранение coverage-отчёта** как артефакта
- **Сборка Docker-образа** (без публикации)

## 📂 Структура проекта

```
my-go-app/
├── .github/
│   └── workflows/
│       └── ci.yml
├── main.go
├── sum.go
├── sum_test.go
├── Dockerfile
├── go.mod
├── go.sum
└── README.md
```

## 🟦 Основной код

**`sum.go`:**
```go
package main

func Sum(a, b int) int {
    return a + b
}
```

**`main.go`:**
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello from Go app!")
    fmt.Println("2 + 3 =", Sum(2, 3))
}
```

## 🚀 Запуск локально

### Через Docker

```bash
docker build -t my-go-app:latest .
docker run --rm my-go-app:latest
```

Ожидаемый вывод:
```
Hello from Go app!
2 + 3 = 5
```

### Тесты через Docker

```bash
docker run --rm -v "$(pwd):/app" -w /app golang:1.22-alpine go test ./...
```

## 📸 Результат запуска

![Вывод приложения](terminal.png)

## ✅ Результат

При каждом push в `main` запускается CI.
На вкладке **Actions** отображаются 🟢 зелёные галочки.

**Ссылка на Actions:**  
https://github.com/xem1zo/my-go-app/actions

## 📝 Вывод

В ходе работы я освоил:

- Настройку CI для Go-проектов в GitHub Actions
- Линтинг через golangci-lint
- Тестирование с покрытием (coverage)
- Сохранение артефактов (upload-artifact)
- Сборку Docker-образа в CI
- Работу с Go-модулями через Docker без установки Go