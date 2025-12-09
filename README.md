# Лабораторно-практична робота №2
## Робота з package.json, залежностями, змінними оточення, семантичним версіонуванням, базовими можливостями TypeScript (type, interface, class).

Мета  
- Ознайомитися зі структурою package.json та призначенням основних полів.
- Навчитися відрізняти робочі залежності (dependencies) від залежностей для розробки (devDependencies).
- Розібратися з принципами семантичного версіонування (SemVer) і навчитися оновлювати версії коректно.
- Дослідити використання змінних оточення через .env файли та підключення їх у коді.
- Освоїти базові конструкції TypeScript: типи, інтерфейси, класи, generics.
- Налаштувати інструменти перевірки коду: ESLint, Prettier, Husky, Commitlint.
- Закріпити практику роботи з Git та GitHub (ініціалізація репозиторію, коміти, теги версій).

В ході цієї роботи був розглянутий фреймворк TypeScript, за допомогою якого в звичайний JS додана типізація й багато інших корисних речей, які спрощують розробку та дебаг.

Короткий опис призначення

Бібліотека надає невеликі утиліти та конфігурацію для прикладних TypeScript‑проєктів: прості функції для роботи зі строками та числами, типізований логер та централізована конфігурація через .env із валідацією zod. Мета — швидко підключити набір корисних допоміжних функцій у demo/пакетах.

Інструкції з запуску

Встановити залежності: npm i
Запустити демо: npm run demo
Зібрати пакет: npm run build

Огляд кроків еволюції

v0.1.0 — basic utils
- Додав базові утиліти (наприклад add, capitalize) з типом any.
- Швидке прототипування функціональності.

v0.2.0 — basic types for utils
- Додавання простих типів для утиліт (number/string) — перехід від any до перших типів.

v0.3.0 — formatNumber
- Реалізація formatNumber з підтримкою NumberFormatOptions — поліпшення роботи з числами/локалізацією.

v0.4.0 — User interface & groupBy
- Додав інтерфейс User.
- Додав універсальну (generic) groupBy — робота над реюзабельністю і типобезпекою колекцій.

v0.5.0 — Logger & env config via zod
- Додав клас Logger.
- Конфігурація оточення через zod (валидація env).
- formatNumber тепер використовує APP_PRECISION — централізація налаштувань.

v1.0.0 — stabilize public API; forbid any; package exports
- Стабілізація публічного API — проєкт прагне гарантій сумісності.
- Заборона any — суворіші типи.
- Налаштовані package exports (контроль того, що експортується з пакета).

v2.0.0 — breaking change: add signature accepts number[]
- Зміна сигнатури add — тепер приймає number[]. Це є зламаною сумісністю (major release).
- Документація/реліз має вказувати, як мігрувати з попередніх версій.

Приклади використання (TypeScript)

```ts
// Просте підсумування масиву
import { add } from './src/utils/add';
console.log(add([1, 2, 3])); // 6
```

```ts
// Капіталізація рядка
import { capitalize } from './src/utils/capitalize';
console.log(capitalize('hello')); // "Hello"
```

```ts
// Форматування числа (використовує APP_PRECISION із config)
import { formatNumber } from './src/format/number';
console.log(formatNumber(123.456)); // наприклад "123.46" якщо APP_PRECISION=2
```

```
// Логгер
import { Logger, type LogLevel } from './src/logger';
import { config } from './src/config';

const logger = new Logger(config.LOG_LEVEL as LogLevel);
logger.info('Application started');
logger.debug('Detailed debug info'); // виведеться тільки якщо LOG_LEVEL === 'debug'
```

Нотатка про .env

APP_PRECISION — очікується ціле число 0..10 (default: 2). Впливає на точність formatNumber.  
LOG_LEVEL — один із: silent | info | debug (default: info). Керує поведінкою Logger.

Посилання на теги релізів
Tags: https://github.com/MarryBye/TSLab2/tags
Releases: https://github.com/MarryBye/TSLab2/releases
