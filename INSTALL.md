# Быстрое подключение бренда IIRuChating к проекту

## 1. Скопируйте файлы

Скопируйте файлы брендкита (без папки `sources/` и исходного `BRAND_BOOK_IIRuChating.md`, если он не нужен в проекте) в директорию статических файлов вашего проекта, например `wwwroot/images/` или `public/images/`:

```
images/
├── logo-full.svg               # Полный логотип (240 × 96)
├── logo-icon.svg               # Иконка (64 × 64)
├── favicon.svg                 # Фавикон со светлой/тёмной темой
├── favicon.ico                 # Фавикон для старых браузеров
├── favicon-96x96.png           # Иконка 96 × 96
├── web-app-manifest-192x192.png
├── web-app-manifest-512x512.png
├── apple-touch-icon.png        # Иконка для iOS (180 × 180)
├── web-app-manifest.json       # Манифест PWA
├── fonts.css                   # Подключение шрифтов
├── logo-icon-128.png           # Иконка в растре (с прозрачным фоном)
├── logo-icon-256.png
├── logo-icon-512.png
├── logo-variant-A-icon.svg     # Вариант А: градиентная заливка
├── logo-variant-A-full.svg
├── logo-variant-B-icon.svg     # Вариант Б: разрывы линий
├── logo-variant-B-full.svg
├── logo-variant-C-icon.svg     # Вариант В: цветные акценты
├── logo-variant-C-full.svg
└── theme-m3.css                # Material 3 роли цветов (светлая и тёмная тема)
```

Файл `logo_new.svg` (мастер-эмблема) можно положить рядом для справки; для сайта он не нужен.

## 2. Подключите фавикон и манифест

В `<head>` вашего HTML:

```html
<!-- Фавикон: favicon.svg сам переключается между светлой и тёмной темой -->
<link rel="icon" type="image/svg+xml" href="images/favicon.svg" />
<link rel="icon" href="images/favicon.ico" sizes="32x32" />

<!-- PWA манифест и иконка для iOS -->
<link rel="manifest" href="images/web-app-manifest.json" />
<link rel="apple-touch-icon" href="images/apple-touch-icon.png" />
```

## 3. Подключите логотип

```html
<!-- Полный логотип (сайт, презентации, документы) -->
<img src="images/logo-full.svg" alt="IIRuChating" width="240" height="96" />

<!-- Иконка (аватарки, навигация, мобильные приложения) -->
<img src="images/logo-icon.svg" alt="IIRuChating" width="64" height="64" />
```

Логотип залит `currentColor`. Через `<img>` CSS-цвет его не меняет, поэтому для тёмной темы используйте `filter: invert(1)`. Если нужно управлять цветом через CSS, встраивайте SVG прямо в HTML (inline).

## 4. CSS переменные цветов

Добавьте в глобальные стили (`:root`):

```css
:root {
  --iiru-brand-black: #000000;
  --iiru-brand-white: #FFFFFF;
  --iiru-accent-violet: #8B5CF6;
  --iiru-accent-blue: #0EA5E9;
  --iiru-accent-emerald: #10B981;
  --iiru-bg-dark: #1E293B;
  --iiru-text-on-dark: #FFFFFF;
}
```

## 5. Шрифты

Подключите шрифты бренда (Inter, Manrope, Montserrat через Google Fonts):

```html
<link rel="stylesheet" href="images/fonts.css">
```

Или импортируйте в CSS:

```css
@import url('./fonts.css');
```

Подробнее — в файле `FONTS.md`. Для продакшена рекомендуется загружать шрифты локально (`.woff2`).

## 6. Правила использования (кратко)

- Логотип только чёрный на светлом или белый на тёмном фоне (базовая версия).
- Не наклоняйте, не растягивайте неравномерно, не добавляйте тени и свечение.
- Минимальный размер иконки: 16 × 16 px; полного логотипа: 120 px по ширине.
- Свободное место вокруг логотипа (clear zone) не меньше высоты одной буквы.
- Для выделения используйте акцентные варианты А, Б или В (раздел 5 брендбука), а не искажения базового логотипа.

## 7. Лицензия

Перед использованием бренда в проектах ознакомьтесь с файлом `LICENSE.md`.

Подробнее — в файле `BRAND_BOOK_IIRuChating.md`.
