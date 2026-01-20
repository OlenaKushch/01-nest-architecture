## Description
[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Project setup

```bash
$ npm install
```

## Compile and run the project

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Run tests

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```


## ARCHITECTURE

Структура проєкту

## Структура проєкту

```text
01-NEST-ARCHITECTURE/
├── dist/                    # Згенеровані файли після збірки
├── node_modules/            # Залежності проєкту
├── src/
│   ├── config/              # Налаштування середовища
│   │   └── configuration.ts
│   ├── users/               # Модуль Users
│   │   ├── users.controller.ts
│   │   ├── users.module.ts
│   │   └── users.service.ts
│   ├── app.controller.ts    # Базовий контролер
│   ├── app.module.ts        # Головний модуль
│   ├── app.service.ts       # Базовий сервіс
│   └── main.ts              # Точка входу в додаток
├── test/                    # Тести
├── .env                     # Змінні середовища (локальні)
├── .env.example             # Шаблон змінних середовища
├── .gitignore
├── .prettierrc
├── eslint.config.mjs
├── nest-cli.json
├── package-lock.json
├── package.json
├── README.md
├── tsconfig.build.json
└── tsconfig.json



Наш проект побудований за принципом модульної архітектури.
Тобто кожна доменна область винесена в окремий модуль,
що дозволяє чітко розділити відповідальності та спростити масштабування застосунку.

Модулі(@Module) є блоками з яких складається проект Nest.
В нашому проекті є кореневий модуль у файлі app.module.ts та створений нами feature-модуль Users.

Кореневий модуль відповідає за підключення feature-модулів, ініціалізацію глобальних залежностей
та налаштування конфігурацій.

Users-module відповідальний за роботу з користувачами.
Users-модуль, як і кожен модуль у Nest,  містить:
- файл module, який описує зв'язки між контролером і сервісом та визначає, що цей модуль
експортує до інших частин системи
- контролер для обробки запитів, який приймає запити та повертає відповідь клієнту
- файл із бізнес-логікою(service.ts).

Файл configuration.ts виконує роль централізованого сховища, яке збирає дані зі змінних середовища(.env)
та групує їх в один об'єкт для уникнення помилок та спрощення масштабування. 

Файл main.ts відповідає за ініціалізацію екземпляра додатка (NestFactory.create).
Тут налаштовуються глобальні параметри, такі як префікси маршрутів, пайпи валідації або CORS, що
забезпечує чистоту коду на рівні окремих модулів.




