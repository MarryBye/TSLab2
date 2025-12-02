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

v1.0.0 — Початковий реліз: базові утиліти (add, capitalize) та початкова структура пакета.
v1.1.0 — Додано конфігурацію з dotenv + валідація zod; додано formatNumber для уніфікованого форматування чисел.
v2.0.0 — Рефакторинг типів і збірки (tsup, dts), оновлено експорти для зручнішого імпорту; піднято major через зміни API експорту.

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

// Logger з конфігурацією із .env (з авторизованою валідацією zod)
```
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
