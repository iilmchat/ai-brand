# Брендкит IIRuChating

Набор фирменных материалов: логотип, палитра Material 3, шрифты, favicon и PWA-манифест.
Версия **1.1** · октябрь 2026.

Полное описание правил — в [брендбуке](BRAND_BOOK_IIRuChating.md).

---

## Быстрый старт

```bash
git clone https://github.com/iilmchat/ai-brand.git
cp ai-brand/{logo-icon.svg,logo-full.svg,favicon.svg,favicon.ico,apple-touch-icon.png} public/images/
cp ai-brand/web-app-manifest*.{json,png} public/images/
```

В `<head>`:

```html
<link rel="icon" type="image/svg+xml" href="/images/favicon.svg" />
<link rel="icon" href="/images/favicon.ico" sizes="32x32" />
<link rel="apple-touch-icon" href="/images/apple-touch-icon.png" />
<link rel="manifest" href="/images/web-app-manifest.json" />
```

Цвета и шрифты — по [INSTALL.md](INSTALL.md). Коротко:

```html
<link rel="stylesheet" href="/images/fonts.css" />
```

```css
:root {
  --iiru-brand-black: #000000;
  --iiru-brand-white: #FFFFFF;
  --iiru-accent-violet: #8B5CF6;
  --iiru-accent-blue: #0EA5E9;
  --iiru-accent-emerald: #10B981;
}
```

---

## Состав

### Логотип

| Файл | Назначение |
|---|---|
| `logo_new.svg` | мастер-эмблема (452 × 453), исходная геометрия |
| `logo-full.svg` | полный логотип с текстом (240 × 96) |
| `logo-icon.svg` | иконка 64 × 64, `fill="currentColor"` |
| `logo-variant-A-icon.svg`, `logo-variant-A-full.svg` | вариант А: градиентная заливка |
| `logo-variant-B-icon.svg`, `logo-variant-B-full.svg` | вариант Б: разрывы линий |
| `logo-variant-C-icon.svg`, `logo-variant-C-full.svg` | вариант В: цветные акценты |

Текст логотипа переведён в кривые — шрифт для отрисовки не нужен.

### Иконки и PWA

| Файл | Назначение |
|---|---|
| `favicon.svg` | favicon, сам переключается между светлой и тёмной темой |
| `favicon.ico` | старые браузеры, Windows |
| `favicon-96x96.png` | растровый favicon |
| `apple-touch-icon.png` | иконка iOS (180 × 180) |
| `web-app-manifest.json` | PWA-манифест |
| `web-app-manifest-192x192.png`, `web-app-manifest-512x512.png` | иконки PWA |
| `logo-icon-128.png`, `logo-icon-256.png`, `logo-icon-512.png` | растровые логотипы с прозрачным фоном |

### Цвет и тема

| Файл | Назначение |
|---|---|
| `theme-m3.css` | роли Material 3: светлая и тёмная схемы, тональные палитры |
| `color-palette.svg` | визуальная шпаргалка по палитре бренда |
| `color-palette-m3.svg` | тональные палитры и роли обеих схем |

Палитра построена по алгоритму **Material 3** (Material Color Utilities, схема **Fidelity**):

- **Primary** — `#8B5CF6` (электрический фиолет, сохраняет тон бренда);
- **Tertiary** — `#0EA5E9` (неоновый синий), построен из собственного seed-цвета, а не стандартного сдвига M3, — чтобы акцент оставался брендовым;
- **Secondary**, **neutral**, **neutral-variant** — производные от primary; **error** — стандартный M3.

В компонентах используются роли (`var(--md-sys-color-primary)`), а не сырые HEX: тогда светлая и тёмная темы переключаются сами.

### Шрифты

| Файл | Назначение |
|---|---|
| `fonts.css` | подключение шрифтов из Google Fonts |
| `FONTS.md` | подробная инструкция |

Рекомендуемые шрифты: **Inter** (интерфейс и логотип), **Manrope** (техно-заголовки), **Montserrat** (выразительные заголовки). Для продакшена загружайте `.woff2` локально — см. `FONTS.md`.

### Шпаргалки

| Файл | Назначение |
|---|---|
| `clear-zone.svg` | схема чистого пространства вокруг логотипа |
| `anti-examples.svg` | типичные ошибки при использовании логотипа |

### Документы

| Файл | Назначение |
|---|---|
| `BRAND_BOOK_IIRuChating.md` | брендбук: логотип, палитра, типографика, правила |
| `INSTALL.md` | быстрое подключение к проекту |
| `FONTS.md` | шрифты |
| `LICENSE.md` | условия использования бренда |
| `CHANGELOG.md` | история версий кита |
| `sources/README.md` | исходники макета (`.fig` / `.ai`) и что можно править самостоятельно |

---

## Пересчёт палитры под свой акцент

Схема — обычный Material 3, поэтому её можно пересчитать в рантайме по любому seed-цвету.
В приложении `AI Ru Chating` это работает так: генератор на
[Material Color Utilities](https://github.com/material-foundation/material-color-utilities)
воспроизводит все 49 ролей `theme-m3.css` без единого расхождения, а третичные роли
остаются зафиксированными брендовыми.

```js
import { DynamicScheme, Hct, Variant, argbFromHex, hexFromArgb } from '@material/material-color-utilities'

const scheme = new DynamicScheme({
  sourceColorHct: Hct.fromInt(argbFromHex('#8B5CF6')), // seed
  variant: Variant.FIDELITY,
  contrastLevel: 0,
  isDark: false,
})

const primary = hexFromArgb(scheme.colors.primary().getArgb(scheme)) // #6B38D4
```

Готовые роли для подстановки в CSS собираются в том же порядке, что и в `theme-m3.css`:
`:root, [data-theme='light']` → `[data-theme='dark']` → медиазапрос для системной темы.

---

## Правила использования — коротко

- базовая версия логотипа — **чёрная на светлом** или **белая на тёмном**; градиенты и цветные заливки допустимы только в вариантах А/Б/В;
- минимальный размер: иконка 16 × 16 px, полный логотип 120 px по ширине;
- чистое пространство вокруг логотипа — не меньше высоты одной буквы текста;
- запрещены наклон, неравномерное растяжение, тени, обводки и свечение;
- акцентные варианты не заменяют базовый логотип на официальных носителях.

Полный список — [брендбук, раздел 6](BRAND_BOOK_IIRuChating.md).

---

## Где используется

| Репозиторий | Как |
|---|---|
| [`iilmchat/ai-ruchating`](https://github.com/iilmchat/ai-ruchating) | ассеты в `client/public/brand/`, роли M3 в `client/src/styles/theme-m3.css`, мост в Tailwind — `client/src/styles/brand.css` |

При обновлении бренда: скопировать новые файлы в `client/public/brand/`, обновить
`client/src/styles/theme-m3.css` и `fonts.css`.

---

## Лицензия

Условия использования бренда, логотипа и палитры — в [LICENSE.md](LICENSE.md).
Исходные файлы макета (`.fig` / `.ai`) не входят в публичный брендкит и выдаются
по запросу владельца бренда — порядок описан в [sources/README.md](sources/README.md).

---

© 2026 IIRuChating. Все права защищены.
