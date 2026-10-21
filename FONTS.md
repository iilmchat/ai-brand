# Шрифты бренда IIRuChating

## Рекомендуемые шрифты (Google Fonts, бесплатно)

| Шрифт | Начертание | Применение | Подключение |
|-------|------------|------------|-------------|
| **Inter** | Bold 700 / SemiBold 600 | Основной шрифт логотипа, интерфейс, основной текст | `fonts.css` |
| **Manrope** | Bold 700 | Техно-заголовки, цифровой характер | `fonts.css` |
| **Montserrat** | ExtraBold 800 / Bold 700 | Выразительные заголовки, особенно `II` в начале | `fonts.css` |

## Подключение

Добавьте в `<head>` вашего HTML (путь зависит от структуры проекта):

```html
<link rel="stylesheet" href="images/fonts.css">
```

Или импортируйте в CSS:

```css
@import url('./fonts.css');
```

Использование:

```css
body { font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif; }
h1, h2 { font-family: 'Montserrat', system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif; }
.logo-text { font-family: 'Inter', system-ui, sans-serif; font-weight: 700; }
```

## Продакшен-рекомендация

Для производственных сред рекомендуется загружать шрифты локально (формат `.woff2`):

1. Скачайте шрифты с [Google Fonts](https://fonts.google.com/). Файлов `.woff2` в брендките сейчас нет.
2. Положите файлы в папку `fonts/` рядом с `fonts.css`.
3. Обновите `fonts.css`, заменив `@import` на локальные `@font-face`.

Пример локального подключения Inter (файл `Inter-Bold.woff2` вы кладёте сами):

```css
@font-face {
  font-family: 'Inter';
  src: url('./fonts/Inter-Bold.woff2') format('woff2');
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}
```

## В логотипе

Текст в логотипе (`logo-full.svg` и варианты) переведён в кривые по шрифту Inter Bold. Шрифт для отрисовки логотипа не нужен, и он выглядит одинаково везде. Не смешивайте шрифты внутри логотипа.
