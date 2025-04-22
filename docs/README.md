# Документация по проектной практике

## Best practices, которые используется в проекте

- [Конвенция названия коммитов](https://www.conventionalcommits.org/en/v1.0.0/)
- [Ведение документации в формате Markdown](https://ru.wikipedia.org/wiki/Markdown)
- [Методология BEM](https://ru.bem.info/methodology/css/)

## Этапы разработки

### 1. Клонирование репозитория и добавления Документация

```bash
git clone https://github.com/askerdev/practice-2025-1.git
cd practice-2025-1
# ... редактирование и добавление документации
git add .
git commit -m "feat(docs): added project documentation"
```

### 2. Добавление Домашней страницы проекта

Была добавлены следующие файлы:

- [`index.html`](https://github.com/askerdev/practice-2025-1/blob/master/site/index.html)
- `styles.css`

### 3. Добавление страницы "О проекте"

Была добавлена страница `project.html`. Так же вынесены общие стили страниц в `base.css`. И использование отдельного файла стилей для каждой страницы: `home.css`, `project.css`

### 4. Добавлена страница "Журнал"

Была добавлена страница `journal.html` и аналогично прошлому пункту стили для неё `journal.css`. Так же были добавлены нужные посты на страницу

### 5. Добавлена страница "Ресурсы"

Была добавлена страница `resources.html` и аналогично прошлому пункту стили для неё `resources.css`. Так же были добавлены нужные ссылки на внешние ресурсы

### 6. Настройка Github CI/CD для хостинга сайта на Github Pages

Был создан файл `.github/workflows/static.yml`, который описывает CI/CD для деплоя в Github Pages на каждый push в ветку `master`

## Технологический стек

- Hosting: `Github Pages`
- HTML, CSS, BEM
