# CI-CD

Frontend-проект на `React 18` и `TypeScript` с ручной настройкой `webpack 5`, линтеров и GitHub Actions.

## Стек

- React 18
- TypeScript
- Webpack 5
- Babel
- Sass / SCSS
- ESLint
- Stylelint
- GitHub Actions

## Запуск

```bash
npm install
npm start
```

Dev server поднимается на `http://localhost:3000`.

## Доступные команды

```bash
npm start             # запуск dev-server
npm run dev           # dev build
npm run build         # production build + проверки
npm run bundle:analyzer
npm run ts:check
npm run lint
npm run lint:styles
npm run all-checks
```

## Структура проекта

```text
.
├── config/webpack     # ручная конфигурация webpack, разбитая на части
├── public/            # html-шаблон и favicon
├── src/
│   ├── components/    # примеры компонентов
│   └── styles/        # глобальные стили, normalize, fonts
└── .github/workflows/ # CI для main и future/**
```

## Что здесь настроено

- алиас `$components` для импортов компонентов
- загрузка изображений и шрифтов через `asset/resource`
- `React Refresh` в dev-режиме
- отдельная production-сборка CSS
- `splitChunks` для оптимизации бандла
- проверки `TypeScript`, `ESLint` и `Stylelint` в CI

## CI

В репозитории есть два workflow:

- `dev.yml` запускается при пуше в ветки `future/**`
- `prod.yml` запускается при пуше в `main`

Оба workflow выполняют одинаковые проверки:

- `npm run ts:check`
- `npm run lint`
- `npm run lint:styles`

CI в GitHub Actions зафиксирован на `Node.js 16.15.1`.

## Зачем этот репозиторий

Проект подходит как демонстрация базовой frontend-инфраструктуры:

- сборка приложения без готовых шаблонов
- организация webpack-конфига по частям
- подключение статических ассетов и стилей
- автоматическая проверка качества кода при пуше
