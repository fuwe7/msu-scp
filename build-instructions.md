# build-instructions.md — Инструкция по сборке сайта
**Роль:** site_architect

## Процедура статической сборки (Вариант A)
1. **Подготовка структуры:** Создать папку `dist/` и подпапки `dist/pages/`, `dist/css/`, `dist/assets/`.
2. **Копирование стилей:** Скопировать `css/style.css` в `dist/css/style.css`.
3. **Подготовка компонентов:** Прочитать `templates/header.html` и `templates/footer.html`, исправить в них ссылки навигации на готовые HTML (вместо `/templates/...`).
4. **Сборка страниц (pages):** 
   - Прочитать каждый `.md` файл из `pages/` со статусом approved.
   - Заменить `{{INCLUDE_HEADER}}` и `{{INCLUDE_FOOTER}}`.
   - Исправить `href="/css/style.css"` на `href="../css/style.css"`.
   - Сохранить как `dist/pages/[имя].html`.
5. **Сборка главной страницы:**
   - Обработать `index.html`.
   - Заменить `{{INTRO_TALE}}`, `{{NEW_OBJECTS_LIST}}`, `{{NEW_DOCS_LIST}}` на реальные HTML-ссылки.
   - Заменить header/footer.
   - Исправить CSS на `css/style.css`.
   - Сохранить в `dist/index.html`.
6. **Нормализация исходников:** Переместить рабочие `.md` файлы в `/project/sources/`, а отчеты ревью в `/project/reviews/`.
