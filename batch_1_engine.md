# batch_1_engine.md — БАТЧ 1: все Engine-шаблоны

Используй профили: `planner`, `site_architect`, `reviewer`, `gap_analyzer`.

## Задача
Создать HTML/CSS-шаблоны и базовую структуру сайта MSU-SCP, воспроизводящую структуру и визуальный язык scpfoundation.net, но без реального лорного контента. Результат — файлы в `/templates/` и `index.html` в корне.

## Источники
- `msu-scp-lore.md`
- `site-map.md`
- `codex.md`
- `reference.md` (должен быть создан в Батче 0)
- `progress_log.md`
- `STATE.md`

## ПРЕДУСЛОВИЕ
Перед стартом проверь, что `reference.md` существует и не пуст. Если `reference.md` отсутствует — остановись, обнови `STATE.md` со статусом `stopped_on_error` и причиной «reference.md не создан — требуется Батч 0 сначала, жди человека.

## РЕЖИМ
Автономный батч. Работай по списку target_pages последовательно, без остановки между страницами внутри батча.

## ЖЁСТКОЕ ПРАВИЛО ОШИБОК
Если `delegate_task` к любой роли падает с ошибкой после 3 повторных попыток:
- не создавай и не редактируй файлы напрямую в обход роли;
- не одобряй страницу без reviewer;
- не переходи к следующей странице;
- обнови `STATE.md`: `Статус последней сессии: stopped_on_error`;
- укажи страницу, роль, этап и текст ошибки;
- выполни HUMAN_CHECKPOINT вне очереди и остановись.

## target_pages (Батч 1, все Engine, порядок обязателен)

1. `Engine: header.html`
2. `Engine: footer.html`
3. `Engine: article-template.html`
4. `Engine: dossier-location-template.html`
5. `Engine: theory-doc-template.html`
6. `Engine: incident-report-template.html`
7. `Engine: tale-template.html`
8. `Engine: dossier-personnel-template.html`
9. `Engine: hub-template.html`
10. `Engine: tales-hub.html`
11. `Engine: index.html` (использует header/footer + плейсхолдер под вступительный Tale вместо "Статья дня")
12. `Engine: about-template.html` (только скелет/плейсхолдеры — `{{ORG_NAME}}`, `{{DEPARTMENTS}}`, `{{ACCESS_LEVELS}}`, `{{WARNING_TEXT}}`. Реальный текст пишет content_executor в Батче 2 — это ЧИСТО ВЁРСТКА без лорного текста внутри)

## Алгоритм на каждую target_page

1. `planner` проверяет статус страницы и её зависимости в `site-map.md`.
2. Делегируй задачу:
   - `Engine-page` → `site_architect`.
3. Дождись черновика.
4. Запусти проверяющие роли:
   - `Engine-page` → `gap_analyzer` (сверка со структурой `reference.md`).
5. Передай все замечания `reviewer`.
6. `reviewer` запускает собственный чек-лист:
   - структура блоков соответствует `reference.md`;
   - все плейсхолдеры для контента промаркированы и задокументированы;
   - CSS-классы согласованы с уже одобренными шаблонами;
   - базовая адаптивность не ломается;
   - навигация (header/footer/hub-ссылки) логически корректна.
7. `reviewer` делит замечания на `BLOCKING` и `NICE-TO-HAVE`, `round_counter += 1`.
8. Если есть `BLOCKING` и `round_counter < 3`:
   - верни единый список замечаний `site_architect`;
   - исправляй только затронутые разделы;
   - повтори проверку (шаги 4–7).
9. Если `round_counter == 3` и `BLOCKING` остались:
   - `reviewer` переводит их в `known limitations`;
   - фиксирует список в конце страницы или в `progress_log.md`;
   - одобряет страницу.
10. После одобрения:
    - обнови `site-map.md` (статус страницы → `approved`);
    - обнови `codex.md` (список плейсхолдеров шаблона);
    - добавь строку в `progress_log.md`:
      `Engine: [имя] — round_counter: X — known limitations: [список или "нет"] — статус: одобрено`.
11. Перейди к следующей `target_page` без ожидания человека.

## Финальный HUMAN_CHECKPOINT

Только после `about-template.html`:
- обнови `STATE.md`:
  - Батч: `1`;
  - Статус последней сессии: `completed`;
  - Следующий промпт: `batch_2_content_core.md`;
  - В список файлов следующей сессии добавь `reference.md`;
  - кратко напиши, что все Engine-шаблоны одобрены, сайт готов к наполнению контентом.
- выведи сводку по `progress_log.md` за весь батч (сколько страниц одобрено, сколько с known limitations, краткий список ограничений);
- остановись. Не начинай Content-страницы.

## Формат вывода
- файлы в `/templates/` (включая `about-template.html`);
- `index.html` в корне;
- обновлённые `site-map.md`, `codex.md`, `progress_log.md`, `STATE.md`.